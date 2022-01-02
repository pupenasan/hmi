## Situational Awareness Controls Project

The Situational Awareness Controls Project (named "SA_Controls") is an include project contains the following Genie libraries:

- [Controls Genie Library](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_ControlsGenieLibrary.htm)                
- [Common Controls Genie Library](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_CommonControlsGenieLibrary.htm)                
- [Priorities Genie Library](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_PrioritiesGenieLibrary.htm).

**Note:** The SA_Controls project is a system include project, and only appears in the Project list tree  if the **System Projects** filter is applied in the Projects activity. This project is included when you create a project using the Situational Awareness Starter project.

#### Controls Genie Library

The SA_Controls system project includes the "sa_controls" library. It includes the following Genies:

- [Alarm List Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_Genie_AlarmList.htm)                
- [Alarm List Vertical Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_Genie_Alarmlist_V.htm)                
- [Generic List Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_Genie_GenericList.htm)                
- [Generic List Vertical Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_Genie_Genericlist_V.htm)                
- [List Row Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_Genie_List_Row.htm).

**Note:** The **SA_Inlcude** system project also contains a library named "sa_controls". For a list of the Genies it includes, see [Controls Genie Library](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Include_ControlsGenieLibrary.htm). 

##### Alarm List Genie

**Genie Name:** alarmlist
**Genie Library:** sa_controls
**System Project:** SA_Controls

The Alarm List Genie (named "alarmlist")  allows you to place a list of alarms on a graphics page in a pre-defined format with a header row and scroll bars. It is a variation of the [Alarm List Vertical Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_Genie_Alarmlist_V.htm), which produces a list with no header row and just a vertical scroll bar. 

This Genie can be used with the [List Row Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Control_Genie_List_Row.htm), which facilitates row selection, a row context menu and row background color. 

By default, an alarm list Genie displays the fields configured through the [AlarmListCreate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/AlarmListCreate.html) Cicode function. You can also use this function to specify the display fonts and alarm indicators.

For further instructions on how to use the Alarm List Genie, see [Add an Alarms List to a Page](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_an_Alarms_List.htm).

**Note:** You can also use the Citect.ini parameter [[Format\]FormatName](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/ParametersCitectHTML/Content/FormatFormatName.html) to set a default format for the fields displayed in an alarms list. 

###### Alarm List Genie Properties

Complete the following properties for the Genie in the Genie Properties dialog box.

- **AN**: This is an automatically-generated unique ID for the Genie object. 
- **Name**: Optional. If you need to reference the Genie at runtime using Cicode, specify a unique name. 

###### Alarm List Genie Parameters 

Select the Genie and double-click on it to view its parameters. The parameters are used as described in the table below:

| Parameter                 | Description                                                  |
| ------------------------- | ------------------------------------------------------------ |
| AN                        | This is automatically populated and matches the AN in the Genie Properties dialog box. This cannot be modified. |
| OnRightClickFunction      | Allows the user to right-click on  the alarms list and perform operations displayed on the context menu. |
| OnColumnSelectedFunction  | Allows you to select a column.                               |
| OnColumnReorderedFunction | Allows you reorder the columns displayed. For example, ArrayView_SetFormat(). |
| OnColumnResizedFunction   | Allows you to re-size the columns displayed.                 |

###### Alarm List Genie Page Properties

For the Genie to work at  runtime, they require some arrays to be pre-configured before animation  begins. In the Page Properties dialog box, Events tab, select the  following event options and specify the required Cicode command.

| Parameter     | Example                                                      | Comments                                                     |
| ------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| On Page Entry | `_Array View_Initialize(); AlarmListCreate(DspGetAnFromName("alarmlist"), 0, 700-14, 318, 32,  1, "", "TopActiveAlarms_UHD4K", -1, DspFontHnd("SA_AlarmHeader4K")) ` | This code will create the Alarm list called "alarmlist" based on the parameters specified in the [AlarmListCreate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/AlarmListCreate.html) function. |
| On Page Exit  | `AlarmListDestroy(DspGetAnFromName("alarmlist"))`            | This code will destroy the alarm list array when the user exits the page. |

