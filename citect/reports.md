# Приклад онлайн звіту

При виборі устатковання з дереву викликається функція MyEquipSel, яка викликає спливаючу сторінку, куди передає назву обладнання та час для звіту: плинний час та плинний час мінус година. 

![image-20211205135312806](media/image-20211205135312806.png)

![image-20211205135403318](media/image-20211205135403318.png)

```c
FUNCTION MyEquipSel (STRING sEquipName)
	INT now = TimeCurrent();
	INT prewhr = TimeCurrent()-3600;
	STRING sNow = TimeToStr(now, 9) + " " + TimeToStr(now, 1);
	STRING sPrewhr  = TimeToStr(prewhr , 9) + " " + TimeToStr(prewhr , 1); 

	//GetTrnedTagsFromEquip (sEquipName);
	Ass(-2,"timestart", "'" + sPrewhr + "'", 0);
	Ass(-2,"timeend", "'" + sNow + "'", 0);
	Ass(-2,"equipname", "'" + sEquipName + "'", 0);
	PagePopUp ("!MyEquipPopup");
END
```

Сторінка popup має тренд та alarmtab. 

![image-20211205135034045](media/image-20211205135034045.png)

Налаштування alarmtab

![image-20211205135131399](media/image-20211205135131399.png)

AlarmTabInit фільтрує відображення тільки для вибраного устатковання та за вказаний час. 

```c
FUNCTION AlarmTabInit (STRING sTable)
	STRING sEquipment = AssInfo("equipname", 0);
	STRING sStartDate = AssInfo("timestart", 0);
	STRING sEndDate = AssInfo("timeend", 0);	
	
	// Set up columns
	LibTable_AddColumn(sTable, "ДатаЧас", 150, "LocalTimeDate");
	LibTable_AddColumn(sTable, "Tag", 150);
	LibTable_AddColumn(sTable, "Message", 150);
	LibTable_AddColumn(sTable, "State", 150);

	STRING sStartDate1 = StrMid (sStartDate,0,10);   
	STRING sStartTime1 =  StrMid (sStartDate,11,8);
	STRING sEndDate1 = StrMid (sEndDate,0,10);
	STRING sEndTime1 = StrMid (sEndDate,11,8);	
	STRING startDate = IntToStr (StrToDate(sStartDate1) + StrToTime(sStartTime1)); 
	STRING endDate = IntToStr (StrToDate(sEndDate1) + StrToTime(sEndTime1));
	STRING sFilter = "Equipment=" + sEquipment + "* AND LocalTimeDate>=" + startDate + " AND LocalTimeDate<" +  endDate + ";";
	tagstr = sStartDate1 + " " + sStartTime1 + " " + sEndDate1 + " " + sEndTime1 ; 
	// Set up filter
	INT nAN = LibAlmTable_GetAN(sTable);
	INT hEdit = AlarmFilterEditOpen(nAN);
	AlarmFilterEditSet(hEdit, sFilter);
	AlarmFilterEditCommit(hEdit);
	AlarmFilterEditClose(hEdit);
END
```

Налаштування запуску функцій при показу сторінки:

![image-20211205153344954](media/image-20211205153344954.png)

Функції шо викликаються:

```c
FUNCTION EquipPA (STRING NamePA, STRING sEquipName)
	ErrSet(1);

	OBJECT hAnalyst, hPanes, hPane, hPens, hPen;
	INT nPanes, nPens;
	STRING sTag;    
	STRING sFilter = "EQUIPMENT=" + sEquipName + "*";
    STRING sField = "NAME";
    INT iStatus = -1;
    INT hTagBrowse =  TrnBrowseOpen (sFilter,sField);
    IF (hTagBrowse <> -1) THEN
        iStatus = TrnBrowseFirst(hTagBrowse);
        WHILE iStatus = 0 DO
             sTag = TrnBrowseGetField(hTagBrowse,sField);
             ProcessAnalystSetPen(-1, sTag, NamePA)
             //tagstr = tagstr + sTag + ";" 
             iStatus = TrnBrowseNext(hTagBrowse);
             nError=IsError();
        END
        TrnBrowseClose(hTagBrowse);
    END  
    ErrSet(0);
END 
```

Встановлення часу для тренду:

```c
FUNCTION SetPensTime (STRING NamePA, STRING sStartDate = "11.10.2017 0:30:00", STRING sEndDate = "11.10.2017 23:30:00" )
	ErrSet(1);
	OBJECT hAnalyst, hPanes, hPane, hPens, hPen;
	INT nPanes, nPens;
	STRING sTag, sDesc;
	STRING sStartDate1, sStartTime1, sEndDate1, sEndTime1;

	sStartDate1 = StrMid (sStartDate,0,10);   
	sStartTime1 =  StrMid (sStartDate,11,8);
	sEndDate1 = StrMid (sEndDate,0,10);
	sEndTime1 = StrMid (sEndDate,11,8);
	
	              
	hAnalyst	= ObjectByName(NamePA);
	hPanes	= _ObjectGetProperty(hAnalyst, "Panes");
	nPanes = _ObjectGetProperty(hPanes, "Count");
	
	REAL startDate;
	REAL endDate;	
	startDate = StrToDate(sStartDate1) + StrToTime(sStartTime1); //StrToDate("11.10.2017") + StrToTime("0:30:00");
	endDate = StrToDate(sEndDate1) + StrToTime(sEndTime1); //StrToDate("11.10.2017") + StrToTime("23:00:00");
	startDate = TimeToOLEDate(startDate, 0); // Convert to UTC
	endDate = TimeToOLEDate(endDate, 0); // Convert to UTC
		
	INT i, j;
	FOR i = 1 TO nPanes DO
		hPane = _ObjectCallMethod(hPanes, "get_Item", i);
		hPens = _ObjectGetProperty(hPane, "Pens");
		nPens = _ObjectGetProperty(hPens, "Count");
		FOR j = 1 TO nPens DO
			hPen = _ObjectCallMethod(hPens, "get_Item", j);
			_ObjectcallMethod(hPen, "PutHorizontalAxisTimeSpan", startDate, 0, endDate, 0);
			_ObjectSetProperty(hPen, "HorizontalAxisScroll", 0);
			_ObjectCallMethod(hPen, "RefreshData");
			sTag = _ObjectGetProperty(hPen, "DataPoint");
			sDesc = TagGetProperty(sTag, "Description");
			
			//Message (sTag ,sDesc ,0);			
		END
	END	
	ErrSet(0);	
	

END
```

## Офлайн звіти

