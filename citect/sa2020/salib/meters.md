#### Meters

Meters provide a graphical and a numeric  representation of instrument readings. The graphical representation  allows you to visually compare the PV with reference values such as  alarm limits and/or user-configured reference values (e.g., the  “tracker” or optimal range). Many of the meters have variations that  allow them to also be used to represent a controller. These variations  include additional elements such as output  (OP) and feedback indicator  (FB).

You can insert multiple instances of a meter in duplicate or triplicate by using the [MeterMultiple.xml  Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Multiple_Meter.htm). 

Meters are  associated with equipment, and require the following items to be defined:

| Item Name                                                    | Description                                    |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB) | Feedback Indicator                             |
| [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP) | Output                                         |
| [ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR) | Optimal Range Display                          |
| [ORLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR) | Optimal Range (OR) Low                         |
| [ORHigh](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR) | Optimal Range (OR) High                        |
| [PR](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators) | Practical Range specific to Deviation meters   |
| [PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators) | Practical Range (PR) Low                       |
| [PRHigh](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators) | Practical Range (PR) High                      |
| [PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV) | Process Variable                               |
| [PVTarget](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV) | Process Variable specific to Target meters     |
| [PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV) | Process ValueTracker                           |
| [SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint) | Setpoint                                       |
| [TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker) | Controls whether or not a tracker is displayed |

The Meter objects available in the Situational Awareness library include:

- [Analyzer](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Analyzer.htm)
- [Deviation](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Deviation.htm)
- [Dual Level](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Dual_Level.htm)
- [Flow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Flow.htm)
- [Level](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Level.htm)
- [Miscellaneous](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Miscellaneous.htm)
- [Pressure ](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Pressure.htm)
- [Target](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Target_Meter.htm)
- [Temperature](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Temperature.htm)

##### Meter Orientations

For most meters, several orientations are provided in order to give page designers flexibility in how the graphics are laid out.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Mirrored](javascript:void(0))

A mirrored meter reverses  the left/right position of some meter elements as shown in the example  below. The positions of the running state indicator, rate of change  arrow,  PV, engineering units, and  mode indicator (for control meters)  are affected. 

![img](media/MeterVersion_Mirrorred.png)    

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Horizontal](javascript:void(0))

The orientation of the  meter is changed to horizontal as shown in the example below. Note that  the proportions of the alarm border, meter symbol and controller output  indicator are slightly different for the horizontal version compared to  the vertical version.

![img](media/MeterVersion_Horizontal.png)    

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Horizontal + Mirrored](javascript:void(0))

Horizontal meters can also  be mirrored. Typically, this orientation is used primarily with regular  meters rather than control meters.

![img](media/MeterVersion_HorizontalMirr.png)    

##### Meter Common Elements

The figure below shows an example of the elements that make up a meter.

![img](media/Meters_CommonElements.png)    

**Meter Symbol and Graphical PV**

Graphical PV connects to: EquipmentName.PV, EquipmentName.PVTarget

The appearance of the meter symbol and graphical PV tells operators what type of reading is being  displayed (flow vs. temperature vs. pressure, etc.). For example, flow  meters are represented as a basic ‘stick’ shape, with a black dot as the graphical PV. Temperature meters resemble a thermometer. Level meters  resemble a (thin) vessel with a fill that rises and falls to represent  the level, and so on. The symbols and PVs for each type of meter are  shown in the following image.

| Analyzer Meter                              | Deviation Meter                              | Flow Meter                       | Level Meter                              | Misc Meter                              | Pressure Meter                       | Target Meter                              | Temperature Meter                |
| ------------------------------------------- | -------------------------------------------- | -------------------------------- | ---------------------------------------- | --------------------------------------- | ------------------------------------ | ----------------------------------------- | -------------------------------- |
| ![img](media/SYM_Analyzer_Meter_28x196.png) | ![img](media/SYM_Deviation_Meter_26x191.png) | ![img](media/SYM_Flow_Meter.png) | ![img](media/SYM_Level_Meter_32x165.png) | ![img](media/SYM_Misc_Meter_25x181.png) | ![img](media/SYM_Pressure_Meter.png) | ![img](media/SYM_Target_Meter_33x165.png) | ![img](media/SYM_Temp_Meter.png) |

**Full Range Indicators**

Connects to: EquipmentName.PRHigh, EquipmentName.PRLow, EquipmentName.PR

Each meter allows you to  set a “normal” operating range ( “practical” range). During most  operating situations, the meter’s full range is much bigger than the  actual region of interest. By setting the normal operating range you can see meaningful variation in the PV when looking at the meter.

The EquipmentName.PR item is applicable to Deviation meters only. PRHigh and PRLow are not applicable to these meters.

If the PV moves outside the normal operating range, the meter scale will automatically change to  show the full range of the instrument. To differentiate a meter that is  showing its full range, additional flags appear at the top of the meter  and the meter symbol line color changes from grey to black, as in the  example below:

![img](media/Meters_FullRangeIndicators.png)    

**Alarm Limits**

Connects to:  EquipmentName.PV (analog alarm - current) or (EquipmentName.HHAlm,  EquipmentName.HAlm, EquipmentName.LAlm, EquipmentName.LLAlm) or  PLC Alarm Limits if configured.

The alarm limit indicators  appear on the meter symbol to show the location of any configured alarm  limits. This allows operators to see when a PV is approaching an alarm  limit. Four types of alarm limits are shown using different symbols.

**Note**: For more information about configuring PLC alarm limits, see [Associate PLC Limits with Equipment.](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm)

|                                          |                       |
| ---------------------------------------- | --------------------- |
| ![img](media/Meters_HHAlarm.png)         | High high alarm limit |
| ![img](media/Meters_HiAlarmLimit.png)    | High alarm limit      |
| ![img](media/Meters_LowAlarmLimit.png)   | Low alarm limit       |
| ![img](media/Meters_LoLoAlarmLimits.png) | Low Low alarm limit   |

For more information, see [Alarm Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Alarm_Indicator.htm).

An alarm limit indicator  will not appear if the corresponding alarm limit is not configured for  the instrument or if the limit is outside of the range shown by the  meter. Note that the precise width of the alarm limit indicators varies  somewhat for different meter types in order to accommodate the width of  the meter symbol. For example, alarm limit indicators are wider on a  level meter than on a flow meter.

**Engineering Units**

Connects to: EquipmentName.PV (eng units field).

The engineering units represent the unit of measurement for the instrument.

**PV**

Connects to: EquipmentName.PV, EquipmentName.PVTarget

The numeric PV provides a  text-based representation of the instrument reading. This provides  operators with precise values when needed.

**Display Name/Nickname**

The display name/nickname  shows the instrument name (by default), or, if entered by the user, a  “display name”. The nickname is usually a common name used to help  identify the reading (for example, “Oil temp”, instead of “TI1001”). The field accommodates up to 79 characters. 

![img](media/Meters_tagName.png)    

**Optimal Range Box**

Connects to: EquipmentName.ORHigh, EquipmentName.ORLow, Visibility connected to EquipmentName.ORDsp.

The optimal range box  highlights a specific range of the meter. Typically, operators will use  this feature to remind themselves of the desired or “optimal” range for  the PV, depending on the operating conditions. It should be possible to  enable and set the endpoints for the optimal range from the point  detail.  If the optimal range is not set or enabled, the box is not  shown.

![img](media/Meters_OptimalRange.png)    

**Tracker**

Connects to: EquipmentName.PVTrack, EquipmentName.OPTrack, EquipmentName.TrackDsp.

Similar to the optimal  range box, the tracker is a user-configured indicator that marks a  specific value on the meter. An operator can mark the current value of a PV so that when they look at the reading again later, they can see if  it has changed. The tracker can be set and enabled/disabled from the  meter faceplate.

![img](media/Meters_Tracker.png)    

#####  Control Meters - Common Elements

When a meter is used to show readings from a controller, additional information is included. Control meters include all of the [common elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm) previously described for regular meters, plus the additional elements shown below.

![img](media/ControlMeters_CommonElements.png)    

**Setpoint Indicator**

Connects to: EquipmentName.SP

The setpoint indicator is  an additional mark on the meter symbol (similar to the tracker and alarm limit indicators) which shows the position of the controller setpoint  value.

**Output Indicator**

Connects to: EquipmentName.OP

The outer rectangle shape with white fill represents the entire range of the [controller output](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm) (typically 0-100%), while the darker fill represents the output value.

**Feedback Indicator**

Connects to: EquipmentName.FB

This small triangular  indicator represents the actual output for the controller (if available  from the control system). It shares the same scale as the controller  output indicator (e.g. 0-100%). This allows the operator to quickly see  if the output and actual output values match. This can be particularly  useful where the controller has a ramping function.

**Mode Indicator**

Connects to: EquipmentName.CtrlMode, EquipmentName.CtrlModeDef

This is a single-character  code that indicates the mode of the controller. Typically, the set of  modes includes Manual (M), Auto (A), and Cascade (C).

![img](media/Meter_ControllerMode.png)    

**Control Mode Indicator states**:

- 0 – Auto (A)
- 1 – Manual (M)
- 2 – Cascade (C)
- 3 – Local (L)
- 4 – Special control (computer symbol)

**Note**: The Mode  Indicator is not displayed if the tag is set to CtrlModeDef. To view the control mode at all times, remove the CtrlModeDef tag from the  equipment template. 

##### Meter Special Elements

Certain meters can have elements in addition to those described in [Meter Common Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm). There are three special elements.

**Differential Indicator**

The delta symbol (Δ) is  used for temperature and pressure meters to indicate when a differential reading is being displayed. It is a static element which is enabled at  configuration and is not connected to the control system. It consists of a simple triangle shape which is placed next to the meter.

![img](media/Meters_DeltaSymbol.png)    

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[Descriptor](javascript:void(0))

The Miscellaneous,  Deviation, and Analyzer meters can all be used to show many different  types of readings. Therefore, it is recommended that short text  (up to 3 characters) is provided to help identify the reading (e.g., “O2” for  Oxygen content, “SG” for density, “Vis” for viscosity, “Trq” for torque, etc.) .  

![img](media/Meters_Descriptor.png)    

**Clock Timer**

Connects to: EquipmentName.Timer, EquipmentName.TimerEXP

Таймер годинника є незалежним об'єктом, який інтегрований з вимірювальними приладами Analyzer. Його можна використовувати в тих випадках, коли аналізатор показує переривчасті показання зразка. Для цих типів показань таймер годинника показує, як давно значення було оновлено. Це допомагає операторам зрозуміти, наскільки поточне значення. Якщо аналізатор зчитує безперервно, таймер годинника не відображається.

![img](media/Meters_ClockTimer.png)    

##### Analyzer Meter

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Analyzer                                                     |
| Graphical Representation                        | ![img](media/Meters_Analyzer_New.png)                        |
| Example Equipment Template                      | Meter                                                        |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[Timer, TimerExp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm#Meters_Timer) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Meter Type                      | From the  drop-down select one of the following meters: Level, Flow, Temperature,  Pressure, Analyzer, Miscellaneous, Target, Deviation and Dual Level |
| Equipment Name                  | Enter a name for the equipment associated with the meter. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix           | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create three meters to monitor  power, voltage and current  for a single pump. You would create three  meters on the pump and assign the equipment item prefix "Power",  "Voltage" and "Current". So, the PV values for the meters would be  PowerPV, VoltagePV and CurrentPV respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  PowerPV, PowerOP, VoltagePV, VoltageOP, CurrentPV, CurrentOP and so on.The following equipment item names (where applicable) can be prefixed:    FB    FullScale    OP    ORDsp    ORLow    ORHigh    PRLow    PRHigh    PV    PVTrack    PVTarget     SP    Timer    TrackDsp |
| Size                            | Size of the meter object image - small or large              |
| Orientation                     | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                   | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                           | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator         | Select this option to display an alarm border around the  Genie. |
| Display Alarm Flag              | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator        | Use this setting to display a status indicator at the selected location. Select **None** if you do not want to display the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable        | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode            | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the **Display Control Readback** option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output       | Select to display an output indicator with the meter. For more information, see [Output Bar](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm). |
| Display Setpoint                | Select to display a setpoint indicator with the meter.       |
| Display OOS                     | Select to display Out of Service indicator.                  |
| Display Differential Indication | Select to display an indicator when a differential reading is detected. **This is visible only on Pressure and Temperature meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Descriptor                      | Enter a short 3-character text descriptor  to indicate what is being measured. If left blank no descriptor will be displayed. **This is visible only on Miscellaneous, Deviation and Analyzer meters**. |
| Display Clock Timer             | Select to display a clock timer on the meter. **This is  visible only on Analyzer meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Display Control Readback        | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Display Trend                   | Select this option to display a [Trend object](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trends.htm) with the meter. On selecting this option, the **Trend Type** dropdown is displayed. Select either **Tail** or **Full**.**Note**: When the **Display Trend** option is selected, the Mirrored option is not available. |
| Trend Type                      | Select the type of trend to be displayed with the meter: [Tail](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trend_Tail.htm) or [Full](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Full_Trend.htm). |
| Mirrored                        | Inserts a mirror image of the meter based on the selected presentation options. |

##### Deviation Meter

The deviation meter is used to represent  the difference between two values. A positive difference is shown as a  bar  extending upwards from the middle of the meter symbol. A negative  difference extends downwards. The configured input range for the  deviation meter needs to be in equal proportions around a zero (for  example -200 to +200 or -50 to +50). The PV will be shown as a deviation from setpoint, where zero=setpoint. If the PV exceeds this range, the  color of the bar will change to black.

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Deviation                                                    |
| Graphical Representation                        | ![img](media/Dev_Meter_173x167.png)                          |
| Example Equipment Template                      | DeviationMeter                                               |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PR](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Meter Type                      | From the  drop-down select one of the following meters: Level, Flow, Temperature,  Pressure, Analyzer, Miscellaneous, Target, Deviation and Dual Level |
| Equipment Name                  | Enter a name for the equipment associated with the meter. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix           | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create three meters to monitor  power, voltage and current  for a single pump. You would create three  meters on the pump and assign the equipment item prefix "Power",  "Voltage" and "Current". So, the PV values for the meters would be  PowerPV, VoltagePV and CurrentPV respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  PowerPV, PowerOP, VoltagePV, VoltageOP, CurrentPV, CurrentOP and so on.The following equipment item names (where applicable) can be prefixed:    FB    FullScale    OP    ORDsp    ORLow    ORHigh    PRLow    PRHigh    PV    PVTrack    PVTarget     SP    Timer    TrackDsp |
| Size                            | Size of the meter object image - small or large              |
| Orientation                     | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                   | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                           | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator         | Select this option to display an alarm border around the  Genie. |
| Display Alarm Flag              | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator        | Use this setting to display a status indicator at the selected location. Select **None** if you do not want to display the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable        | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode            | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the **Display Control Readback** option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output       | Select to display an output indicator with the meter. For more information, see [Output Bar](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm). |
| Display Setpoint                | Select to display a setpoint indicator with the meter.       |
| Display OOS                     | Select to display Out of Service indicator.                  |
| Display Differential Indication | Select to display an indicator when a differential reading is detected. **This is visible only on Pressure and Temperature meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Descriptor                      | Enter a short 3-character text descriptor  to indicate what is being measured. If left blank no descriptor will be displayed. **This is visible only on Miscellaneous, Deviation and Analyzer meters**. |
| Display Clock Timer             | Select to display a clock timer on the meter. **This is  visible only on Analyzer meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Display Control Readback        | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Display Trend                   | Select this option to display a [Trend object](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trends.htm) with the meter. On selecting this option, the **Trend Type** dropdown is displayed. Select either **Tail** or **Full**.**Note**: When the **Display Trend** option is selected, the Mirrored option is not available. |
| Trend Type                      | Select the type of trend to be displayed with the meter: [Tail](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trend_Tail.htm) or [Full](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Full_Trend.htm). |
| Mirrored                        | Inserts a mirror image of the meter based on the selected presentation options. |

##### Dual Level Meter

This object provides a compact way to  monitor two related levels simultaneously. The level indication is  presented on a linear scale. For example, you could use a Dual Level  meter to indicate the levels of two tanks. One of the tanks is shown in a slightly darker shade of gray than the other. The Dual Level meter is  designed to display the values of two levels that share a common set of  scales (engineering range, practical range and alarm limits). 

**Note**: If you need to display the values of two levels with different scales, use the Multiple Meter. 

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Dual Level                                                   |
| Graphical Representation                        | ![img](media/Meter_Dual_Level_190x182.png)                   |
| Example Equipment Template                      | Meter                                                        |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                                             | Description                                                  |
| -------------------------------------------------- | ------------------------------------------------------------ |
| Meter Type                                         | From the dropdown list, select Dual Level.                   |
| Reference Equipment Name                           | Enter the full  name and path for the equipment associated with the dual meter. The path and name should be prefixed with the equipment's cluster name for  multi-cluster systems. You can enter a maximum of 160 characters for  this option. |
| Equipment Name and Equipment #2 Name               | Enter the full name and path of the two equipment objects. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix and Equipment #2 Item Prefix | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create two meters to monitor  power or voltage  for a single pump. You would create two meters on the  pump and assign the equipment item prefix "Power1" and "Power2" or  "Voltage1" and "Voltage2". So, the PV values for the meters would be  Power1PV, Power2PV, etc, respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  Power1PV, Power2PV and so on.The following equipment item names can be prefixed:    PV    OP    ORDsp    TrackDsp    FB    PRLow    PRHigh    ORLow    ORHigh    SP    PVTrack    FullScale    OPTrack    Timer    PVTarget |
| Size                                               | Size of the meter object image - small or large              |
| Orientation                                        | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                                      | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                                              | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Status Indicator                           | Select the  location to display a status indicator. Select None if you do not wish  to see the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable                           | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode                               | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the “Display Control Readback” option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output                          | Select to display an output indicator with the meter. For more information, see [Output Ba](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm)r. |
| Display Setpoint                                   | Select to display a setpoint indicator with the meter.       |
| Display OOS                                        | Select to display Out of Service indicator.                  |
| Display Control Readback                           | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Mirrored                                           | Inserts a mirror image of the meter based on the selected presentation options. |

**Note**: The Control Mode, PV and OP bar take values only from **Equipment Name**. **Equipment Name #2** is only used to display the height of the second bar (the light grey bar).

##### Flow Meter

The flow indication is presented on a  linear scale, containing a “floating ball” PV indicator like commonly  found physical flow meters.  The meter limit markers  will appear only  if there are no alarm limits shown, in order to better define the meter  range visually.

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Flow                                                         |
| Graphical Representation                        | ![img](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Content/images/Meters_Flow_122x176.png) |
| Example Equipment Template                      | Meter                                                        |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[Timer, TimerExp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm#Meters_Timer) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Meter Type                      | From the  drop-down select one of the following meters: Level, Flow, Temperature,  Pressure, Analyzer, Miscellaneous, Target, Deviation and Dual Level |
| Equipment Name                  | Enter a name for the equipment associated with the meter. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix           | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create three meters to monitor  power, voltage and current  for a single pump. You would create three  meters on the pump and assign the equipment item prefix "Power",  "Voltage" and "Current". So, the PV values for the meters would be  PowerPV, VoltagePV and CurrentPV respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  PowerPV, PowerOP, VoltagePV, VoltageOP, CurrentPV, CurrentOP and so on.The following equipment item names (where applicable) can be prefixed:    FB    FullScale    OP    ORDsp    ORLow    ORHigh    PRLow    PRHigh    PV    PVTrack    PVTarget     SP    Timer    TrackDsp |
| Size                            | Size of the meter object image - small or large              |
| Orientation                     | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                   | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                           | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator         | Select this option to display an alarm border around the  Genie. |
| Display Alarm Flag              | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator        | Use this setting to display a status indicator at the selected location. Select **None** if you do not want to display the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable        | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode            | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the **Display Control Readback** option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output       | Select to display an output indicator with the meter. For more information, see [Output Bar](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm). |
| Display Setpoint                | Select to display a setpoint indicator with the meter.       |
| Display OOS                     | Select to display Out of Service indicator.                  |
| Display Differential Indication | Select to display an indicator when a differential reading is detected. **This is visible only on Pressure and Temperature meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Descriptor                      | Enter a short 3-character text descriptor  to indicate what is being measured. If left blank no descriptor will be displayed. **This is visible only on Miscellaneous, Deviation and Analyzer meters**. |
| Display Clock Timer             | Select to display a clock timer on the meter. **This is  visible only on Analyzer meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Display Control Readback        | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Display Trend                   | Select this option to display a [Trend object](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trends.htm) with the meter. On selecting this option, the **Trend Type** dropdown is displayed. Select either **Tail** or **Full**.**Note**: When the **Display Trend** option is selected, the Mirrored option is not available. |
| Trend Type                      | Select the type of trend to be displayed with the meter: [Tail](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trend_Tail.htm) or [Full](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Full_Trend.htm). |
| Mirrored                        | Inserts a mirror image of the meter based on the selected presentation options. |

##### Level Meter

The meter symbol for a Level meter is a  narrow box shape that resembles a “skinny” vessel. The graphical PV is  shown as a darker fill within the vessel. The fill rises and falls to  indicate the actual level.

Level meters are provided in both vertical  and horizontal orientations, although it is expected they will be used  primarily in the vertical orientation.

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Level                                                        |
| Graphical Representation                        | ![img](media/Meter_Level_148x198.png)                        |
| Example Equipment Template                      | Meter                                                        |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[Timer, TimerExp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm#Meters_Timer) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Meter Type                      | From the  drop-down select one of the following meters: Level, Flow, Temperature,  Pressure, Analyzer, Miscellaneous, Target, Deviation and Dual Level |
| Equipment Name                  | Enter a name for the equipment associated with the meter. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix           | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create three meters to monitor  power, voltage and current  for a single pump. You would create three  meters on the pump and assign the equipment item prefix "Power",  "Voltage" and "Current". So, the PV values for the meters would be  PowerPV, VoltagePV and CurrentPV respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  PowerPV, PowerOP, VoltagePV, VoltageOP, CurrentPV, CurrentOP and so on.The following equipment item names (where applicable) can be prefixed:    FB    FullScale    OP    ORDsp    ORLow    ORHigh    PRLow    PRHigh    PV    PVTrack    PVTarget     SP    Timer    TrackDsp |
| Size                            | Size of the meter object image - small or large              |
| Orientation                     | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                   | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                           | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator         | Select this option to display an alarm border around the  Genie. |
| Display Alarm Flag              | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator        | Use this setting to display a status indicator at the selected location. Select **None** if you do not want to display the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable        | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode            | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the **Display Control Readback** option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output       | Select to display an output indicator with the meter. For more information, see [Output Bar](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm). |
| Display Setpoint                | Select to display a setpoint indicator with the meter.       |
| Display OOS                     | Select to display Out of Service indicator.                  |
| Display Differential Indication | Select to display an indicator when a differential reading is detected. **This is visible only on Pressure and Temperature meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Descriptor                      | Enter a short 3-character text descriptor  to indicate what is being measured. If left blank no descriptor will be displayed. **This is visible only on Miscellaneous, Deviation and Analyzer meters**. |
| Display Clock Timer             | Select to display a clock timer on the meter. **This is  visible only on Analyzer meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Display Control Readback        | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Display Trend                   | Select this option to display a [Trend object](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trends.htm) with the meter. On selecting this option, the **Trend Type** dropdown is displayed. Select either **Tail** or **Full**.**Note**: When the **Display Trend** option is selected, the Mirrored option is not available. |
| Trend Type                      | Select the type of trend to be displayed with the meter: [Tail](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trend_Tail.htm) or [Full](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Full_Trend.htm). |
| Mirrored                        | Inserts a mirror image of the meter based on the selected presentation options. |

##### Miscellaneous Meter

The miscellaneous meter indication is  presented on a linear scale, containing a filled rectangle as a PV  indicator. The miscellaneous meter is usually used to represent readings that do not have a dedicated meter type (e.g., weight, speed, torque,  etc.).

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Miscellaneous                                                |
| Graphical Representation                        | ![img](media/Meter_Miscellaneous_216x177.png)                |
| Example Equipment Template                      | Meter                                                        |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Meter Type                      | From the  drop-down select one of the following meters: Level, Flow, Temperature,  Pressure, Analyzer, Miscellaneous, Target, Deviation and Dual Level |
| Equipment Name                  | Enter a name for the equipment associated with the meter. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix           | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create three meters to monitor  power, voltage and current  for a single pump. You would create three  meters on the pump and assign the equipment item prefix "Power",  "Voltage" and "Current". So, the PV values for the meters would be  PowerPV, VoltagePV and CurrentPV respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  PowerPV, PowerOP, VoltagePV, VoltageOP, CurrentPV, CurrentOP and so on.The following equipment item names (where applicable) can be prefixed:    FB    FullScale    OP    ORDsp    ORLow    ORHigh    PRLow    PRHigh    PV    PVTrack    PVTarget     SP    Timer    TrackDsp |
| Size                            | Size of the meter object image - small or large              |
| Orientation                     | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                   | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                           | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator         | Select this option to display an alarm border around the  Genie. |
| Display Alarm Flag              | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator        | Use this setting to display a status indicator at the selected location. Select **None** if you do not want to display the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable        | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode            | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the **Display Control Readback** option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output       | Select to display an output indicator with the meter. For more information, see [Output Bar](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm). |
| Display Setpoint                | Select to display a setpoint indicator with the meter.       |
| Display OOS                     | Select to display Out of Service indicator.                  |
| Display Differential Indication | Select to display an indicator when a differential reading is detected. **This is visible only on Pressure and Temperature meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Descriptor                      | Enter a short 3-character text descriptor  to indicate what is being measured. If left blank no descriptor will be displayed. **This is visible only on Miscellaneous, Deviation and Analyzer meters**. |
| Display Clock Timer             | Select to display a clock timer on the meter. **This is  visible only on Analyzer meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Display Control Readback        | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Display Trend                   | Select this option to display a [Trend object](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trends.htm) with the meter. On selecting this option, the **Trend Type** dropdown is displayed. Select either **Tail** or **Full**.**Note**: When the **Display Trend** option is selected, the Mirrored option is not available. |
| Trend Type                      | Select the type of trend to be displayed with the meter: [Tail](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trend_Tail.htm) or [Full](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Full_Trend.htm). |
| Mirrored                        | Inserts a mirror image of the meter based on the selected presentation options. |

##### Pressure Meter

 Pressure meters can be used to show regular pressure readings, or differential pressure readings.

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Pressure                                                     |
| Graphical Representation                        | ![img](media/Meter_Pressure_164x204.png)                     |
| Example Equipment Template                      | Meter                                                        |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Meter Type                      | From the  drop-down select one of the following meters: Level, Flow, Temperature,  Pressure, Analyzer, Miscellaneous, Target, Deviation and Dual Level |
| Equipment Name                  | Enter a name for the equipment associated with the meter. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix           | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create three meters to monitor  power, voltage and current  for a single pump. You would create three  meters on the pump and assign the equipment item prefix "Power",  "Voltage" and "Current". So, the PV values for the meters would be  PowerPV, VoltagePV and CurrentPV respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  PowerPV, PowerOP, VoltagePV, VoltageOP, CurrentPV, CurrentOP and so on.The following equipment item names (where applicable) can be prefixed:    FB    FullScale    OP    ORDsp    ORLow    ORHigh    PRLow    PRHigh    PV    PVTrack    PVTarget     SP    Timer    TrackDsp |
| Size                            | Size of the meter object image - small or large              |
| Orientation                     | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                   | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                           | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator         | Select this option to display an alarm border around the  Genie. |
| Display Alarm Flag              | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator        | Use this setting to display a status indicator at the selected location. Select **None** if you do not want to display the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable        | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode            | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the **Display Control Readback** option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output       | Select to display an output indicator with the meter. For more information, see [Output Bar](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm). |
| Display Setpoint                | Select to display a setpoint indicator with the meter.       |
| Display OOS                     | Select to display Out of Service indicator.                  |
| Display Differential Indication | Select to display an indicator when a differential reading is detected. **This is visible only on Pressure and Temperature meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Descriptor                      | Enter a short 3-character text descriptor  to indicate what is being measured. If left blank no descriptor will be displayed. **This is visible only on Miscellaneous, Deviation and Analyzer meters**. |
| Display Clock Timer             | Select to display a clock timer on the meter. **This is  visible only on Analyzer meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Display Control Readback        | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Display Trend                   | Select this option to display a [Trend object](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trends.htm) with the meter. On selecting this option, the **Trend Type** dropdown is displayed. Select either **Tail** or **Full**.**Note**: When the **Display Trend** option is selected, the Mirrored option is not available. |
| Trend Type                      | Select the type of trend to be displayed with the meter: [Tail](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trend_Tail.htm) or [Full](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Full_Trend.htm). |
| Mirrored                        | Inserts a mirror image of the meter based on the selected presentation options. |

##### Target Meter

The Target meter is used to show deviations from setpoint in level.

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Target                                                       |
| Graphical Representation                        | ![img](media/Meter_Target_155x213.png)                       |
| Example Equipment Template                      | TargetMeter                                                  |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Meter Type                      | From the  drop-down select one of the following meters: Level, Flow, Temperature,  Pressure, Analyzer, Miscellaneous, Target, Deviation and Dual Level |
| Equipment Name                  | Enter a name for the equipment associated with the meter. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix           | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create three meters to monitor  power, voltage and current  for a single pump. You would create three  meters on the pump and assign the equipment item prefix "Power",  "Voltage" and "Current". So, the PV values for the meters would be  PowerPV, VoltagePV and CurrentPV respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  PowerPV, PowerOP, VoltagePV, VoltageOP, CurrentPV, CurrentOP and so on.The following equipment item names (where applicable) can be prefixed:    FB    FullScale    OP    ORDsp    ORLow    ORHigh    PRLow    PRHigh    PV    PVTrack    PVTarget     SP    Timer    TrackDsp |
| Size                            | Size of the meter object image - small or large              |
| Orientation                     | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                   | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                           | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator         | Select this option to display an alarm border around the  Genie. |
| Display Alarm Flag              | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator        | Use this setting to display a status indicator at the selected location. Select **None** if you do not want to display the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable        | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode            | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the **Display Control Readback** option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output       | Select to display an output indicator with the meter. For more information, see [Output Bar](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm). |
| Display Setpoint                | Select to display a setpoint indicator with the meter.       |
| Display OOS                     | Select to display Out of Service indicator.                  |
| Display Differential Indication | Select to display an indicator when a differential reading is detected. **This is visible only on Pressure and Temperature meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Descriptor                      | Enter a short 3-character text descriptor  to indicate what is being measured. If left blank no descriptor will be displayed. **This is visible only on Miscellaneous, Deviation and Analyzer meters**. |
| Display Clock Timer             | Select to display a clock timer on the meter. **This is  visible only on Analyzer meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Display Control Readback        | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Display Trend                   | Select this option to display a [Trend object](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trends.htm) with the meter. On selecting this option, the **Trend Type** dropdown is displayed. Select either **Tail** or **Full**.**Note**: When the **Display Trend** option is selected, the Mirrored option is not available. |
| Trend Type                      | Select the type of trend to be displayed with the meter: [Tail](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trend_Tail.htm) or [Full](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Full_Trend.htm). |
| Mirrored                        | Inserts a mirror image of the meter based on the selected presentation options. |

##### Temperature Meter

Temperatures are indicated on a linear  scale.  Temperature meters can be used to show regular temperature  readings, or differential temperature readings.

| Property                                        | Description                                                  |
| :---------------------------------------------- | :----------------------------------------------------------- |
| Name                                            | Deviation                                                    |
| Graphical Representation                        | ![img](media/Meter_Temperature_184x182.png)                  |
| Example Equipment Template                      | Meter                                                        |
| Associated Composite Genie                      | Meter.xml                                                    |
| Equipment.Items that the Genie expects          | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meter_GraphicalPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[FB](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_FB)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)[RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[EqStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm#EqStatus)[TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker) |
| Equipment Parameters the Equipment Items Expect | [InternalIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_InternalIODevice)[CicodeIODevice](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CicodeIODevice)[EqStatusFunc](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_EqStatusFunc)[CtrlMode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_CtrlMode)[Range](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Range)[Alarm Limits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Equipment_Parameters.htm#Param_Alarm) |
| Associated Faceplate(s)                         | [Analog Controller](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Controller.htm)[Analog Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_FP_Analog_Indicator.htm) |
| Equipment.Items that the Faceplate Expects      | [OP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_OP)[ORHigh, ORLow, ORDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_OR)[PRHigh, PRLow](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Full_Range_Indicators)[OPTrack, PVTrack, TrackDsp](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_Tracker)[PV](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Common_Elements.htm#Meters_NumericPV)[SP](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Setpoint)[CtrlMode, CtrlModeDef](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode)AutoCmd, ManCmd, CasCmd    [RunStatus](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#RunStatus_Tag)[OOS, OOSDisabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_MeO_States.htm#OOS_Tags) |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Configuration Tasks](javascript:void(0))

- [Create equipment and organize equipment in a hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Add_Equipment_Using_Equipment_Editor.htm): Create equipment instances for the required objects, and organize the  equipment in a hierarchy. Objects can be referred to by their name when  you add Composite Genies to a graphics page. You can add one or more instances of an equipment to a page.
- [Associate PLC Alarm Limits for Meters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm): This is an optional task that is required if you want to use PLC alarm limits instead of the standard analog alarm limits.
- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm): Create graphics pages with instances of [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genies.htm) that are associated with the  equipment you have defined in your project. 
- [Create a new faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Create_A_New_FP.htm): Add a [faceplate](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SA_Library_Faceplates.htm) for the equipment to allow operators to engage with the equipment at runtime.                    
- Write Cicode functions to initialize PR and OR values. Refer to the Cicode Reference Online help for more information. It is recommended that for a  Dual Level meter you set these values on both meters to the same value. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Presentation Options](javascript:void(0))

The following presentation options are available for this object.

| Option                          | Description                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| Meter Type                      | From the  drop-down select one of the following meters: Level, Flow, Temperature,  Pressure, Analyzer, Miscellaneous, Target, Deviation and Dual Level |
| Equipment Name                  | Enter a name for the equipment associated with the meter. You can enter a maximum of 160 characters for this option. |
| Equipment Item Prefix           | Prefix applied to the equipment  item name. This allows for displaying multiple values for a single piece of equipment. For example, you want to create three meters to monitor  power, voltage and current  for a single pump. You would create three  meters on the pump and assign the equipment item prefix "Power",  "Voltage" and "Current". So, the PV values for the meters would be  PowerPV, VoltagePV and CurrentPV respectively.**Note**: To get a meter with a prefix to work correctly, you need to create tags with the required  item names. From the example above, you will need to create the tags  PowerPV, PowerOP, VoltagePV, VoltageOP, CurrentPV, CurrentOP and so on.The following equipment item names (where applicable) can be prefixed:    FB    FullScale    OP    ORDsp    ORLow    ORHigh    PRLow    PRHigh    PV    PVTrack    PVTarget     SP    Timer    TrackDsp |
| Size                            | Size of the meter object image - small or large              |
| Orientation                     | Select the orientation that is appropriate for the presentation of the object on the graphics page. |
| Display Label                   | Use this setting to display a label at the selected position. Select **None** if you do not want to display a label. |
| Label                           | Enter the text that will display at the location specified in **Display Label** field. You can enter a maximum of 30 characters for this option. |
| Display Alarm Indicator         | Select this option to display an alarm border around the  Genie. |
| Display Alarm Flag              | Use this setting to display an alarm flag at the selected position. **Note:** If you select the same position for the alarm flag and **Display Status** indicator (see below), they will overlap. The alarm flag will not be visible. |
| Display Status Indicator        | Use this setting to display a status indicator at the selected location. Select **None** if you do not want to display the status indicator. For more information, see [Status Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Status_Indicators.htm). |
| Display Process Variable        | Select to display a process variable (numeric PV) with the meter. This option is selected by default. |
| Display Control Mode            | Select this option to display the [Controller Mode Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm). On selecting this option the **Display Control Readback** option box is also displayed. The [Display Control Readback Indicator](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm) represents the actual output for the controller. |
| Display Controller Output       | Select to display an output indicator with the meter. For more information, see [Output Bar](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_OutputBar_Indicator.htm). |
| Display Setpoint                | Select to display a setpoint indicator with the meter.       |
| Display OOS                     | Select to display Out of Service indicator.                  |
| Display Differential Indication | Select to display an indicator when a differential reading is detected. **This is visible only on Pressure and Temperature meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Descriptor                      | Enter a short 3-character text descriptor  to indicate what is being measured. If left blank no descriptor will be displayed. **This is visible only on Miscellaneous, Deviation and Analyzer meters**. |
| Display Clock Timer             | Select to display a clock timer on the meter. **This is  visible only on Analyzer meters**. For more information, see [Meter Special Elements](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Meters_Special_Elements.htm). |
| Display Control Readback        | Select to display a readback indicator (also known as feedback indicator) with the meter. |
| Display Trend                   | Select this option to display a [Trend object](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trends.htm) with the meter. On selecting this option, the **Trend Type** dropdown is displayed. Select either **Tail** or **Full**.**Note**: When the **Display Trend** option is selected, the Mirrored option is not available. |
| Trend Type                      | Select the type of trend to be displayed with the meter: [Tail](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Trend_Tail.htm) or [Full](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Full_Trend.htm). |
| Mirrored                        | Inserts a mirror image of the meter based on the selected presentation options. |