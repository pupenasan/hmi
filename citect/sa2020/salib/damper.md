[Проект Situational Awareness](../README.md) -> [Situational Awareness Library](readme.md)



[help](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Content/ASM_Damper.htm)

##### Damper

The damper object is based closely on the  control valve object. It shows the position and status of dampers. The  elements and behavior are as described in the Common Elements.

Levels:

- Level 3 (vertical, horizontal, compact vertical, compact horizontal)
- Level 2 (vertical, horizontal, compact vertical, compact horizontal)
- Level 1 (vertical, horizontal, compact vertical, compact horizontal)
- Basic (vertical, horizontal, compact vertical, compact horizontal)
- Basic with tag (vertical, horizontal, compact vertical, compact horizontal).           

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Damper Valve                                                 |
| Graphical Representation                        | ![img](G:\san\AKIT\ДИСЦИП\ЛМІ\GitVer\citect\sa2020\salib\media\damper_valve.png) |
| Example Equipment Template                      | Valve                                                        |
| Associated Composite Genie                      | Valve.xml                                                    |
| Equipment.Items the Genie expects               | [Open, POS, Closed, Opening, Closing](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Valves.htm#Valves_Control)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Valves.htm#ModeIndicator)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags)[OP ](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Valves.htm#Valves_OP)[OPTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Valves.htm#Valves_OPTrack)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Valves.htm#Valves_Readback)[OOS, OOSDisable](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags)OpenCmdCloseCmdStopCmdAutoCmdManCmdStopped |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range) |
| Associated Faceplate(s)                         | [Simple ON / OFF Valve](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Simple_Valve.htm)[Complex ON / OFF Valve](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Complex_Valve.htm) |
| Equipment.Items that the Faceplate expects      | [OPTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Valves.htm#Valves_OPTrack)[CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Valves.htm#ModeIndicator)OpenCmdCloseCmdStopCmdAutoCmdManCmdStopped |

**Note**: Check that the address configured for a valve in the PLC is the same as the tag address specified in Plant SCADA. If this is not configured correctly, the state and output value of the valve will not be accurate.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                   | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| Equipment Name           | Enter a name for the piece of equipment. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix    | Specify the prefix and the equipment.item the prefix will be applied to. |
| Valve Type               | Select the type of Valve - Block, Control or Damper, Hand.   |
| Size                     | Size of the Valve - small or large.                          |
| Orientation              | Select 	 the  orientation that is appropriate for the presentation of the object on  the graphics page. Horizontal or Vertical. Horizontal is selected by  default. |
| Fail Type                | Select the fail action for the valve (open, closed, or last). |
| Display Label            | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                    | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator  | Select this  option to display an alarm indicator which indicates the highest  priority alarm and its state for this Valve's equipment. |
| Display Alarm Flag       | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator | Select the  location to display a status indicator. Select None if you do not wish  to see the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Output Bar       | Select this option to display a field control or computer control for this object. |
| Display OOS              | Select this option to display an out of service indicator.   |
| Display Control Mode     | Select this option to display a mode indicator for the object. |
| Display Readback         | The [Display Readback](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Value            | Select this option to display the output value.              |