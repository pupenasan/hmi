# Опис програм з одного проекту



## Alarms.ci

```c
INT
FUNCTION AlrmFltrSet1(STRING Name1 = "1", STRING Equip = "2_Дфсат", STRING sNameFilter = "Produv") 
	ErrSet(1);
	INT iHndl, iErr; 
    STRING Fltr = TagRead ("MESSAGE1[9]") + "*";
    INT nAN = _LibControl_GetInt("_almtbl_" + Name1, "AN");
	TabAlmTable_InitDsp(Name1, nAN, sNameFilter);
    
    TagWrite ("MESSAGE1[0]", Fltr);
	iHndl = AlarmFilterEditOpen(nAN);
	iErr = AlarmFilterEditSet(iHndl, "Equipment=^""+Fltr+"^";");
	IF sNameFilter="LabLog" THEN
		AlarmFilterEditAppend(iHndl, " Category=11;")
	END
	iErr = AlarmFilterEditCommit(iHndl);
	iErr = AlarmFilterEditClose(iHndl);
	RETURN (TRUE) ;
	//WinFree();
END

FUNCTION ShowEquipAlm (STRING sTag)
	STRING sEqNm;
	sEqNm = TagGetProperty(sTag, "Equipment",3);
	Ass (-2, "EQUIP",sEqNm, 0);
	Ass (-2, "NAME", "'" + sEqNm + "'", 0);
	WinNewAt("!EquipAlm", 100, 200, 1+2+4+128);
END

FUNCTION AutoAck (STRING sCategory)
	INT Category = StrToInt (sCategory);
	INT Current;
	INT Next;
	STRING AlmTag;
	Current=AlarmFirstCatRec(Category,1);
	WHILE Current<>-1 DO
	   AlmTag = AlarmGetFieldRec(Current, "Tag");
	   //TagWrite ("MESSAGE1[3]", "222222222222222222222222222222");
	   IF StrToInt (TagRead (AlmTag + ".On")) = 0 THEN
	   		AlarmAckRec(Current); 
	   END	   
	   Next=AlarmNextCatRec(Current,Category,1);
	   Current=Next;
	END
END
```

## Controls.ci

```c
REAL 
FUNCTION TagRampR (REAL rTag, REAL rPrcnt, REAL rMin, REAL rMax)
	REAL val;
	val = rTag + rPrcnt*100.0/(rMax - rMin);
	IF val > rMax THEN val = rMax ; END
	IF val < rMin THEN val = rMin ; END
	RETURN val;
END
```

## PA.ci

```c
FUNCTION PA_withoutTool (STRING NamePA)	
	ErrSet(1);
	OBJECT hAnalyst		= ObjectByName(NamePA);
	OBJECT hToolbars	= _ObjectGetProperty(hAnalyst, "Toolbars");
	_ObjectSetProperty(hAnalyst, "BackgroundColor", 12566463);
	OBJECT hMainToolbar	= _ObjectCallMethod(hToolbars, "get_Item", 1);
	_ObjectSetProperty(hMainToolbar, "Visible", 0);
	
	//_ObjectCallMethod(hPen, "ResetToDefaultSpan");
	OBJECT hOV = _ObjectGetProperty(hAnalyst, "ObjectView");
		
		INT bVisible = _ObjectGetProperty(hOV, "Visible");
		IF (bVisible <> 0) THEN
			_ObjectSetProperty(hOV, "Visible", 0);
		END;
		//_ObjectCallMethod(hAnalyst, "BlockUpdates");	
	ErrSet(0);	
END

FUNCTION SetPenName (STRING NamePA)
	ErrSet(1);
	OBJECT hAnalyst, hPanes, hPane, hPens, hPen;
	INT nPanes, nPens;
	STRING sTag, sDesc;    
	hAnalyst	= ObjectByName(NamePA);
	hPanes	= _ObjectGetProperty(hAnalyst, "Panes");
	nPanes = _ObjectGetProperty(hPanes, "Count");
	INT i, j;
	FOR i = 0 TO nPanes DO
		hPane= _ObjectCallMethod(hPanes, "get_Item", i);
		hPens = _ObjectGetProperty(hPane, "Pens");
		nPens = _ObjectGetProperty(hPens, "Count");
		FOR j = 0 TO nPens DO
			hPen = _ObjectCallMethod(hPens, "get_Item", j);
			sTag = _ObjectGetProperty(hPen, "DataPoint");
			sDesc = TagGetProperty(sTag, "Description");
			_ObjectSetProperty(hPen, "Name", sDesc);
		END
	END	
	ErrSet(0);		
END
```

## Popupmenu.ci

```c
	INT iRoute [1000];
INT 
FUNCTION PopupMenus(STRING sTag, INT AN)    
	INT iSelection, X, Y;
	STRING sEqNm, sEqType, sEqItem, sTagPV, sEqLoop, sHelpFile;
	DspGetMouse(X, Y);
	INT xan, yan, xan1, yan1;
	DspGetAnExtent(AN, yan, xan, yan1 , xan1  );
	
	IF NOT (X>=xan AND X<=xan1 AND Y>=yan AND Y<=yan1) THEN RETURN (0); END 
	
	//!Item1 disables Item1; 
	// ~Item2 checks Item2; 
	// ,Item3 inserts a separator above Item3. 
	// insert a link from a menu item TO a sub menu, use the (>) symbol. 
	

	//msg = " " + IntToStr (AN) + "," + IntToStr (X) + "," + IntToStr (Y);
	//msg1 = "AN=" + IntToStr (AN) + ", X=" + IntToStr (X) + ", Y=" + IntToStr (Y) + ", xan=" + IntToStr (xan) + ", yan=" + IntToStr (yan)+ ", xan1=" + IntToStr (xan1)+ ", yan1=" + IntToStr (yan1) ;
	sEqNm = TagGetProperty(sTag, "Equipment",3);
	sEqItem = TagGetProperty(sTag, "Item", 3); 
	IF sEqNm = "" THEN RETURN (-1); END
	
	STRING sFilterCriteria = "Equipment=^""+ sEqNm + "*" + "^";";
	INT iAlmCount = AlarmCount(0, sFilterCriteria, 1 , 0);
	INT iAlmDisblCount = AlarmCount(3, sFilterCriteria);
	//Message("Title", IntToStr (iAlmCount) , 0);
		
	sEqType = EquipGetProperty (sEqNm, "Type",3);
	sEqLoop = EquipGetProperty (sEqNm, "Custom2",3);
	sHelpFile = EquipGetProperty (sEqNm, "Help",3);
	
	STRING sMenu0 = "";
	STRING sDis2 = "";
	IF GetPriv(2, 0)=0 THEN
		sDis2 = "!"; 
	END
	SELECT CASE sEqType
	CASE "PTr", "QTr"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1;iRoute [2] = 2;
		sMenu0 = sMenu0 + "," + sDis2 + "Налаштування параметру,";
		iRoute [3] = 3;
		sMenu0 = sMenu0 + sDis2 + "Налаштування регулятору,";
		iRoute [4] = 31;
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [5] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [6] = 5;
		//sMenu0 = sMenu0 + ",Допомога";
		//iRoute [7] = 7;
		sTagPV = TagInfoEx(sEqNm + ".PV", 0); // отримати імя тегу PV по назві обладнання
	CASE "PTc2", "QTc2", "TTprod"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1;iRoute [2] = 2;
		sMenu0 = sMenu0 + "," + sDis2 + "Налаштування параметру,";
		iRoute [3] = 3;
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [4] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [5] = 5;
		//sMenu0 = sMenu0 + ",Допомога";
		//iRoute [6] = 7;
		sTagPV = TagInfoEx(sEqNm + ".PV", 0); // отримати імя тегу PV по назві обладнання
	CASE "PTnet"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1;iRoute [2] = 2;
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [3] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [4] = 5;
		//sMenu0 = sMenu0 + ",Допомога";
		//iRoute [6] = 7;
		sTagPV = TagInfoEx(sEqNm + ".PV", 0); // отримати імя тегу PV по назві обладнання		
	CASE "LabVal"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1;iRoute [2] = 2;
		sMenu0 = sMenu0 + ",Введення значення,";
		iRoute [3] = 33;
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [4] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [5] = 5;
		//sMenu0 = sMenu0 + ",Допомога";
		//iRoute [6] = 7;
		sTagPV = TagInfoEx(sEqNm + ".PV", 0); // отримати імя тегу PV по назві обладнання	
	CASE "YAPID"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1; iRoute [2] = 2;
		sMenu0 =  sMenu0 + ",Дистанційне керування...,";
		iRoute [3] = 8;		
		sMenu0 = sMenu0 + sDis2 + "Налаштування регулятору,";
		iRoute [4] = 31;
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [5] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [6] = 5;
		//sMenu0 = sMenu0 + ",Допомога";
		//iRoute [7] = 7;
		sTagPV = TagInfoEx(sEqNm + ".OUT", 0); // отримати імя тегу OUT по назві обладнання	
	CASE "SYPID"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1; iRoute [2] = 2;
		sMenu0 =  sMenu0 + ",Дистанційне керування...,";
		iRoute [3] = 81;		
		sMenu0 = sMenu0 + sDis2 + "Налаштування регулятору,";
		iRoute [4] = 31;
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [5] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [6] = 5;
		//sMenu0 = sMenu0 + ",Допомога";
		//iRoute [7] = 7;
		sTagPV = TagInfoEx(sEqNm + ".OUT", 0); // отримати імя тегу OUT по назві обладнання			
	CASE "YAnet"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1; iRoute [2] = 2;
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [3] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [4] = 5;
	CASE "Motor1"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1;iRoute [2] = 2;
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [3] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [4] = 5;
		//sMenu0 = sMenu0 + ",Допомога";
		//iRoute [5] = 7;
	CASE "YD"
		sMenu0 =  "Графік,Графік в новому вікні,";
		iRoute [1] = 1;iRoute [2] = 2;
		sMenu0 =  sMenu0 + ",Дистанційн керування...,";
		iRoute [3] = 82;
		sMenu0 = sMenu0 + "Налаштування продувок,";
		iRoute [4] = 32;		
		sMenu0 = sMenu0 + ",Плинні тривоги (";
		IF iAlmCount > 0 THEN 
			sMenu0 = sMenu0 + IntToStr (iAlmCount); 
		ELSE
			sMenu0 = sMenu0 + "немає";
		END
		IF iAlmDisblCount > 0 THEN
			sMenu0 = sMenu0 + "/" + IntToStr (iAlmDisblCount) + " заблокованих";
		END  
		iRoute [5] = 4;
		sMenu0 = sMenu0 + "),Журнал тривог та подій,";
		iRoute [6] = 5;
		//sMenu0 = sMenu0 + ",Допомога";
		//iRoute [7] = 7;	
	CASE ELSE
		RETURN (-2);
	END SELECT

	DspPopupMenu(0,sMenu0);	
	iSelection = DspPopupMenu(-1, "");
	
	INT iWinNum;
	SELECT CASE iRoute[iSelection] 
	CASE 1 //Графік
		iWinNum = WinNumber("!ProcessAnalystPopup1");
		IF iWinNum < 0 THEN 
			ProcessAnalystPopup("!ProcessAnalystPopup1");
		ELSE
			//ProcessAnalystSelect(iWinNum , "TrensPopup1", "_templatePA2");
			WinSelect(iWinNum);
		END 
		ProcessAnalystSetPen(-1, sTag, "_templatePA2", 0, 0);
		SetPenName ("_templatePA2");	
	CASE 2 // Графік в новому вікні
 		ProcessAnalystPopup("!ProcessAnalystPopup"); 
		ProcessAnalystSetPen(-1, sTagPV, "", 0, 0);
		IF sEqType = "PTr" OR  sEqType = "QTr" THEN
			ProcessAnalystSetPen(-1, sTagPV + "_SP", "", 0, 0);
		END
		//PageProcessAnalystPens("!ProcessAnalystPopup", sTag);
		SetPenName ("_templatePA1");
	CASE 3 // Налаштування вимірювальних значень
		Ass (-2, 1, "'" + sTagPV + "'", 0);
		Ass (-2, "TAG", sTagPV, 0);
		Ass (-2 ,"MIN", "'" + TagGetProperty(sTagPV, "EngUnitsLow") + "'", 0);
		Ass (-2 ,"MAX", "'" + TagGetProperty(sTagPV, "EngUnitsHigh") + "'", 0);		
		Ass (-2, "SCALE6", "'0'", 0);		
		WinNewAt("!" + sEqType , 100, 200, 1+2+4);
	CASE 31 // Налаштування регулятору
		WinNewAt(sEqLoop, 100, 200, 1+2+4);
	CASE 32 // Налаштування продувок
		Ass (-2, "EQUIP", sEqLoop, 0);
		Ass (-2, "NAME", "'" + sEqLoop + "_DTSP'", 0);
		Ass (-2, "YD", "YD" + StrRight(sEqLoop, 2) , 0);
		//Message ("YD", "YD" + StrRight(sEqLoop, 2), 0); 
		WinNewAt("!KSProd", 100, 200, 1+2+4+128);
	CASE 33 // Введення лабораторного значення
		AssWin ("!EnterValueLab", 100, 200, 1+2+4+128, "'" + sTagPV + "'", 
				"'" + sTagPV +"_SPLOC'",
				sTagPV, sTagPV + "_SPLOC", 
				"'" + TagGetProperty(sTagPV + "_SPLOC", "EngUnitsLow") + "'", 
				"'" + TagGetProperty(sTagPV + "_SPLOC", "EngUnitsHigh") + "'" )
		//AssWin ("!EnterValueLab", 100, 200, 1+2+4+128, "'%TAG%'", 
		//"'%TAG%_SPLOC'",
		//"%TAG%",
		//"%TAG%_SPLOC", 
		//"'" + TagGetProperty("%TAG%_SPLOC", "EngUnitsLow") + "'", 
		//"'" + TagGetProperty("%TAG%_SPLOC", "EngUnitsHigh") + "'" )
	CASE 4 // Плинні тривоги
		Ass (-2, "EQUIP",sEqNm, 0);
		Ass (-2, "NAME", "'" + sEqNm + "'", 0);
		WinNewAt("!EquipAlm", 100, 200, 1+2+4+128);
	CASE 5 // Журнал тривог
		Ass (-2, "EQUIP",sEqNm, 0);
		Ass (-2, "NAME", "'" + sEqNm + "'", 0);
		WinNewAt("!EquipSOE", 100, 200, 1+2+4+128);
	CASE 6 // Зведені тривоги
		;
	CASE 7 // Допомога	 
		//sHelpFile = "C:/ProgramData/Schneider Electric/Vijeo Citect 7.50/User/Teosat/Help/index.html";
		Ass (-2, 1, "'" + sHelpFile + "'", 0);
		//TagWrite ("HelpFile", sHelpFile);  
		PageDisplay("HTML");
		//PageFile(sHelpFile);
	CASE 8 // Дистанційне керування YA	 
		Ass (-2, "TAG", sTag, 0);
		AssWin ("!YA1", 100, 200, 1+2+4+128, "'" + sTag + "'", "'" + sTag + "_OUTMAN'",sTag, sTag + "_OUTMAN", "'0'", "'100'");
	CASE 81 // Дистанційне керування SY
		Ass (-2, "TAG", sTag, 0);
		AssWin ("!SY1", 100, 200, 1+2+4+128, "'" + sTag + "'", "'" + sTag + "_OUTMAN'",sTag, sTag + "_OUTMAN", sTag + "_FREQ");		  
	CASE 82 // Дистанційне керування YD
		Ass (-2, "TAG", sTag, 0);
		Ass (-2, "NAME", "'" + sTag + "'", 0);
		WinNewAt("!YDSG1", 100, 200, 1+2+4+128);	  
			
	END SELECT					
END

FUNCTION WinSetpoint(STRING sTAG)
	AssWin ("!EnterValue", 100, 200, 1+2+4+128, "'" + sTAG + "_DMAX'", "'" + sTAG + "_DMAXLOC'", "" + sTAG + "_DMAX","" + sTAG + "_DMAXLOC", "'" + TagGetProperty(sTAG + "_DMAXLOC", "EngUnitsLow") + "'", "'"+ TagGetProperty(sTAG + "_DMAXLOC", "EngUnitsHigh") + "'")
END

FUNCTION WinDevSetpoint(STRING sTAG)
	AssWin ("!EnterValue", 100, 200, 1+2+4+128, "'" + sTAG + "'", "'" + sTAG + "LOC'", sTAG, sTAG + "LOC", "'" + TagGetProperty(sTAG + "LOC", "EngUnitsLow") + "'", "'"+ TagGetProperty(sTAG + "LOC", "EngUnitsHigh") + "'")
END
```

## Produv.ci

```c
REAL 
FUNCTION GetTMV (INT tmV, INT tmSP, INT tmtSP, INT perSP, INT STA)
	SELECT CASE STA 
	CASE 0
	    RETURN 0;
	CASE 1 
		RETURN tmV*100/perSP;
	CASE 2
		RETURN tmV*100/tmSP;
	CASE 3
		RETURN tmV*100/tmtSP;
	END SELECT;
END  
```

