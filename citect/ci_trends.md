# Trend Functions

You can control a trend's operation by using the trend functions. Citect SCADA has standard trend pages, so you would not normally use these low-level functions unless you want to define your own trend displays. You can  control the movement of the trend cursor, trend scaling, and the  definition of trend attributes (such as the trend starting time and  sampling period). You can also create, and subsequently delete trends.

Following are functions relating to Trends:

|                                                              |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [TrnAddHistory](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnAddHistory.html) | Restores an old history file to the trend system.            |
| [TrnBrowseClose](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnBrowseClose.html) | Closes a trend browse session.                               |
| [TrnBrowseFirst](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnBrowseFirst.html) | Gets the oldest trend entry.                                 |
| [TrnBrowseGetField](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnBrowseGetField.html) | Gets the field indicated by the cursor position in the browse session. |
| [TrnBrowseNext](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnBrowseNext.html) | Gets the next trend entry in the browse session.             |
| [TrnBrowseNumRecords](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnBrowseNumRecords.html) | Returns the number of records in the current browse session. |
| [TrnBrowseOpen](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnBrowseOpen.html) | Opens a trend browse session.                                |
| [TrnBrowsePrev](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnBrowsePrev.html) | Gets the previous trend entry in the browse session.         |
| [TrnClientInfo](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnClientInfo.html) | Gets information about the trend that is being displayed at the AN point. |
| [TrnComparePlot](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnComparePlot.html) | Prints two trends (one overlaid on the other), each with up to four trend tags. |
| [TrnDelete](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnDelete.html) | Deletes a trend created by the TrnNew() function.            |
| [TrnDelHistory](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnDelHistory.html) | Deletes an old history file from the trend system.           |
| [TrnEcho](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnEcho.html) | Enables and disables the echo on the trend display.          |
| [TrnEventGetTable](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnEventGetTable.html) | Stores event trend data and the associated time stamp in an event table and time table, for a specified trend tag. |
| [TrnEventGetTableMS](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnEventGetTableMS.html) | Stores event trend data and time data (including milliseconds) for a specified trend tag. |
| [TrnEventSetTable](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnEventSetTable.html) | Sets trend data from a table, for a specified trend tag.     |
| [TrnEventSetTableMS](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnEventSetTableMS.html) | Sets event trend data and time data (including milliseconds) for a specified trend tag. |
| [TrnExportClip](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnExportClip.html) | Exports trend data to the clipboard.                         |
| [TrnExportCSV](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnExportCSV.html) | Exports trend data to a file in CSV (comma separated values) format. |
| [TrnExportDBF](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnExportDBF.html) | Exports trend data to a file in dBASE III format.            |
| [TrnExportDDE](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnExportDDE.html) | Exports trend data to applications via DDE.                  |
| [TrnFlush](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnFlush.html) | Flushes the trend to disk.                                   |
| [TrnGetBufEvent](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetBufEvent.html) | Gets the event number of a trend at an offset for a pen.     |
| [TrnGetBufTime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetBufTime.html) | Gets the trend time at an offset for a pen.                  |
| [TrnGetBufValue](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetBufValue.html) | Gets the trend value at an offset for a pen.                 |
| [TrnGetCluster](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetCluster.html) | Gets the name of the cluster the trend graph is associated with. |
| [TrnGetCursorEvent](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetCursorEvent.html) | Gets the event number of a trend at the trend cursor.        |
| [TrnGetCursorMSTime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetCursorMSTime.html) | Gets the time (in milliseconds from the previous midnight) at a trend cursor for a specified pen. |
| [TrnGetCursorPos](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetCursorPos.html) | Gets the position of the trend cursor.                       |
| [TrnGetCursorTime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetCursorTime.html) | Gets the time/date at the trend cursor.                      |
| [TrnGetCursorValue](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetCursorValue.html) | Gets the current trend cursor value of a pen.                |
| [TrnGetCursorValueStr](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetCursorValueStr.html) | Gets the current trend cursor value of a pen as a formatted string. |
| [TrnGetDefScale](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetDefScale.html) | Gets the default engineering zero and full scales of a trend tag. |
| [TrnGetDisplayMode](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetDisplayMode.html) | Gets the display mode of a trend.                            |
| [TrnGetEvent](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetEvent.html) | Gets the event number of a trend at a percentage along the trend. |
| [TrnGetFormat](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetFormat.html) | Gets the format of a pen.                                    |
| [TrnGetGatedValue](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetGatedValue.html) | Returns the internally stored value for <GATED>.             |
| [TrnGetInvalidValue](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetInvalidValue.html) | Returns the internally stored value for <TRN_NO_VALUES>.     |
| [TrnGetMode](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetMode.html) | Gets the display mode of trends (historical or real-time).   |
| [TrnGetMSTime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetMSTime.html) | Gets the time (in milliseconds from the previous midnight) of the trend (plotted by a specified pen)  at a percentage along the trend,using the time and date of the latest sample displayed. |
| [TrnGetPen](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetPen.html) | Gets the trend tag of a pen.                                 |
| [TrnGetPenComment](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetPenComment.html) | Gets the comment of a trend pen.                             |
| [TrnGetPenFocus](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetPenFocus.html) | Gets the number of the pen currently in focus.               |
| [TrnGetPenNo](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetPenNo.html) | Gets the pen number of a pen name.                           |
| [TrnGetPeriod](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetPeriod.html) | Gets the display period of a trend.                          |
| [TrnGetScale](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetScale.html) | Gets the scale of a pen.                                     |
| [TrnGetScaleStr](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetScaleStr.html) | Gets the scale of a pen as a formatted string.               |
| [TrnGetSpan](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetSpan.html) | Gets the span time of a trend.                               |
| [TrnGetTable](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetTable.html) | Stores trend data in an array.                               |
| [TrnGetTime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetTime.html) | Gets the time/date of a pen.                                 |
| [TrnGetUnits](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnGetUnits.html) | Gets the data units of a trend pen.                          |
| [TrnInfo](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnInfo.html) | Gets the configured values of a trend tag.                   |
| [TrnIsValidValue](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnIsValidValue.html) | Determines whether a logged trend value is <VALID>, <GATED>, or invalid <TRN_NO_VALUES>. |
| [TrnNew](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnNew.html) | Creates a new trend at run time.                             |
| [TrnPlot](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnPlot.html) | Prints a plot of one or more trend tags.                     |
| [TrnPrint](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnPrint.html) | Prints a trend that is displayed on the screen.              |
| [TrnSamplesConfigured](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSamplesConfigured.html) | Gets the number of samples configured for the currently displayed trend. |
| [TrnScroll](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnScroll.html) | Scrolls a trend pen.                                         |
| [TrnSelect](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSelect.html) | Sets up a page for a trend.                                  |
| [TrnSetCursor](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetCursor.html) | Moves the trend cursor a specified number of samples.        |
| [TrnSetCursorPos](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetCursorPos.html) | Moves the trend cursor to the given x-axis position.         |
| [TrnSetDisplayMode](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetDisplayMode.html) | Specifies how trend samples will be displayed on the screen. |
| [TrnSetEvent](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetEvent.html) | Sets the start event of a trend pen.                         |
| [TrnSetPen](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetPen.html) | Sets a trend pen to a new trend tag.                         |
| [TrnSetPenFocus](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetPenFocus.html) | Sets the pen focus.                                          |
| [TrnSetPeriod](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetPeriod.html) | Sets the display period (time base) of a trend.              |
| [TrnSetScale](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetScale.html) | Re-scales a pen.                                             |
| [TrnSetSpan](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetSpan.html) | Sets the span time of a trend.                               |
| [TrnSetTable](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetTable.html) | Sets trend data from an array.                               |
| [TrnSetTime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrnSetTime.html) | Sets the starting time/date of a pen.                        |

The following trend functions are used on  standard trend templates. Use these functions only if you create your  own trend templates
(These functions are written in Cicode and can be found in the include project.)

| [TrendDspCursorComment](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendDspCursorComment.html) | Displays the Trend Comment for the currently selected pen.   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [TrendDspCursorScale](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendDspCursorScale.html) | Displays a scale value for the current pen.                  |
| [TrendDspCursorTag](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendDspCursorTag.html) | Displays the tag name of the current pen.                    |
| [TrendDspCursorTime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendDspCursorTime.html) | Displays the cursor time of the current pen.                 |
| [TrendDspCursorValue](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendDspCursorValue.html) | Displays the cursor value of the current pen.                |
| [TrendGetAn](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendGetAn.html) | Gets the AN number of the trend under the mouse position.    |
| [TrendPopUp](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendPopUp.html) | Displays a pop-up trend with the specified trend pens.       |
| [TrendRun](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendRun.html) | Initializes the cursor and rubber-band features on a trend page. |
| [TrendSetDate](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendSetDate.html) | Sets the starting date for the pens on a trend.              |
| [TrendSetScale](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendSetScale.html) | Sets the scale of one or more pens on a trend.               |
| [TrendSetSpan](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendSetSpan.html) | Sets the span time of a trend.                               |
| [TrendSetTime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendSetTime.html) | Sets the starting time for the pens on a trend.              |
| [TrendSetTimebase](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendSetTimebase.html) | Sets a new sampling period for a trend.                      |
| [TrendWin](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendWin.html) | Displays a trend page (in a new window) with the specified trend pens. |
| [TrendZoom](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TrendZoom.html) | Zooms a trend in either one or both axes.                    |

## TrnGetTable

Ця функція дозволяє зводити значення в таблицю з певного розділу тренду. Значення в таблиці (можливо, змінна масиву) впорядковані за часом.

Якщо період (*Період*) відрізняється від періоду вибірки тренду (налаштованого в базі даних тегів тренду), повернуті значення визначаються за допомогою *DisplayMode*.

Ця функція є блокуючою функцією. Вона блокуватиме виклик завдання Cicode, доки операція не буде завершена.

**TrnGetTable**(*Tag, Time, Period, Length, Table, DisplayMode, Milliseconds [, sClusterName]* )

*Tag:*  The trend tag enclosed in quotation marks "" (can be prefixed  by the name of the cluster that is ClusterName.Tag).

Time: Час і дата закінчення (довге ціле число) потрібного розділу тренду. Після того, як ви введете час і дату завершення (Time), період (Period) і кількість зібраних значень тегу тренду (Length), час і дата початку (start time) будуть розраховані автоматично. Наприклад, якщо `Time = StrToDate("18/12/96") + StrToTime("09:00")`, Period = 30 і Length = 60, час початку буде 08:30. Іншими словами, значення тенденцій для періоду з 8:30 до 9 ранку (18 грудня 1996 р.) будуть наведені в таблицю. Якщо для цього аргументу встановлено значення 0 (нуль), використовуваним часом буде поточний час.

*Period:*  Різниця в часі між поверненими в таблиці значеннями тренду (у секундах). Наприклад, якщо встановити цей період на 30 секунд, Citect SCADA отримає останнє значення тенденції (вибірка в кінці розділу тренду), потім отримає значення тренду, яке було відібрано за 30 секунд до цього, і так далі, поки воно не досягне час початку розділу тренду. Якщо цей період відрізняється від періоду вибірки тренду, значення тренду будуть усереднені або інтерпольовані. Установіть значення 0 (нуль), щоб за замовчуванням відповідати фактичним періодом тренду.

*Length:* Кількість значень тренду для збереження в таблиці трендів, від 1 до максимальної кількості елементів у таблиці. Цей аргумент має максимум 4000 (у v6). Якщо вказати довжину, що перевищує 4000, повертається значення 0 і IsError()=274 (INVALID_ARGUMENT). Це обмеження можна налаштувати за допомогою параметра citect.ini [Trend]MaxRequestLength.

*Table:*  Змінна, що містить масив Cicode, в якому зберігаються дані тренду. Тут можна ввести назву масиву (див. приклад).

*DisplayMode:*  Параметри режиму відображення дозволяють ввести одне ціле число для визначення параметрів відображення тенденції (максимум для восьми трендів). Щоб обчислити ціле число, яке ви повинні ввести для певної тенденції, виберіть параметри, які ви хочете використовувати, із перелічених нижче, додавши їх пов’язані числа разом. Отримане ціле число є параметром DisplayMode для цієї тенденції.

**Invalid/Gated trend options**:

*0* - Convert invalid/gated trend samples to zero.

*1* - Leave invalid/gated trend samples as they are.

**Ordering trend sample options**:

*0* - Order returned trend samples from oldest to newest.

*2* - Order returned trend samples from newest to oldest.

**Condense method options**:

*0* - Set the condense method to use the mean of the samples.

*4* - Set the condense method to use the minimum of the samples.

*8* - Set the condense method to use the maximum of the samples.

*12* - Set the condense method to use the newest of the samples.

**Stretch method options**:

*0* - Set the stretch method to step.

*128* - Set the stretch method to use a ratio.

*256* - Set the stretch method to use raw samples.

**Gap Fill Constant option**:

*n* - the number of missed samples that the user wants to gap fill) x 4096.

**Synchronize to Display Period options**:

*0* - Synchronize the returned samples to the nearest display period.

*16777216* - Do not synchronize samples to the nearest display period.

Options listed in each group are mutually exclusive. The default value for each Display Mode is 258 (0 + 2 + 256).

*Milliseconds:*         

This argument allows you to set your sample request time  with millisecond precision. After defining the time and date  in seconds with the Time argument, you can then use this  argument to define the milliseconds component of the time.

For example, if you wanted to  request data from the 18/12/96, at 9am, 13 seconds, and 250 milliseconds you could set the Time and Milliseconds arguments as follows:

```
Time = StrToDate("18/12/96") + StrToTime("09:00:13")Milliseconds = 250
```

If you don't enter a Milliseconds  value, it defaults to 0 (zero). There is no range constraint, but as  there are only 1000 milliseconds in a second, you should keep your entry between 0 (zero) and 999.

*sClusterName:*         

Name of the cluster in which the trend tag resides. This is  optional if you have one cluster or are resolving the trend via  the current cluster context. The argument is enclosed in  quotation marks "".

Return Value

The actual number of samples read. 0(zero) is  returned if an error occurs. You can call the IsError() function to get  the actual [error](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/Cicode_Errors.html) code.

## TrnBrowse*

Отримання переліку тренд-тегів за фільтром назви обладнання Equipment

```c
FUNCTION GetTrnedTagsFromEquip (STRING sEquipName)
	ErrSet(1);
	tagstr =""; 
	STRING sFilter = "EQUIPMENT=" + sEquipName + "*";
    STRING sField = "NAME";
    STRING sTag = "";
    INT iStatus = -1;
    INT hTagBrowse =  TrnBrowseOpen (sFilter,sField);
    IF (hTagBrowse <> -1) THEN
        iStatus = TrnBrowseFirst(hTagBrowse);
        WHILE iStatus = 0 DO
             sTag = TrnBrowseGetField(hTagBrowse,sField);
             tagstr = tagstr + sTag + ";" 
             iStatus = TrnBrowseNext(hTagBrowse);
             nError=IsError();
        END
        TrnBrowseClose(hTagBrowse);
    END  
END
```

