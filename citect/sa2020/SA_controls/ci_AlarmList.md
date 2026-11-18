# AlarmList

Містить допоміжні функції Array View для керування списком тривог або табличним поданням, джерелом даних для якого є масив, створений за допомогою `ArrayCreateByAn()`.

Ці функції слід використовувати разом із Genie `sa_controls_common.arrayview_header`.

- AlarmList_SetFormat
- AlarmList_DspPrev
- AlarmList_DspNext
- AlarmList_SetSelectedRowFont
- AlarmList_SelectedRowFont
- AlarmList_Selected_Cluster
- AlarmList_Selected_AlarmTagName
- AlarmList_Selected_Area
- AlarmList_Selected_Privilege
- AlarmList_Selected_Type
- AlarmList_Selected_UserName
- AlarmList_Selected_Classification
- AlarmList_Selected_StateNumeric
- AlarmList_Selected_DisableEndDate
- AlarmList_Selected_DisableEndTime
- AlarmList_Selected_DisableComment
- AlarmList_Selected_Equipment
- AlarmList_Selected_Help
- AlarmList_Selected_Priority
- AlarmList_Selected_StateSummary
- AlarmList_Selected_Field
- AlarmList_Selected_HasNextResponse
- AlarmList_Selected_NextResponse
- AlarmList_Selected_HasPrevResponse
- AlarmList_Selected_PrevResponse
- AlarmList_Selected_ResponseIndex
- AlarmList_Selected_ResponseNum
- AlarmList_Selected_Cause
- AlarmList_Selected_Response
- AlarmList_Selected_RespTime
- AlarmList_Selected_Consequence



## AlarmList_SetFormat

Встановлення нового формату Array View

```
FUNCTION AlarmList_SetFormat(INT nBaseAn = -2, STRING sFormatName = "__AlarmListTemp", STRING sNewFormat = "")
```

Функція встановлює новий формат для масиву, пов'язаного з Genie `Array View`.

- Параметр `nBaseAn` задає AN базового об'єкта, який визначає область натискання заголовка стовпців.

- Параметр `sNewFormat` містить новий рядок формату, що визначає набір стовпців, їхні назви та ширину.

Функція не повертає значення (`Nil`).
