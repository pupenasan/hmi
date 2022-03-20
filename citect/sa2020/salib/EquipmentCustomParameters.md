##### Equipment Custom Parameters

The following equipment parameters defined  in the equipment template are applicable to most meters, drives and  valves. They are configured on each [equipment instance created](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Add_an_Equipment_Instance.htm) in the Equipment Editor. Any exception is noted in the parameter description. 

[![img](G:\san\AKIT\ДИСЦИП\ЛМІ\GitVer\citect\sa2020\salib\media\Custom_Parameters_thumb_600_600.png)](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/images/Custom_Parameters.png)            

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[InternalIODevice](javascript:void(0))

Name of the persisted  memory PLC that stores the value of internal tags to control the value  of a library object. For example, the PRHigh, PRLow, ORHigh and ORLow  tags may exist in the PLC

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[CicodeIODevice](javascript:void(0))

Name of the I/O device that is used to store values for calculated variables. For example, EqStatus.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[EqStatusFunc](javascript:void(0))

Name of the Cicode function needed to evaluate the value of the status indicator. For example, EquipmentStatus_Drive_GetValue. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[CtrlMode](javascript:void(0))

[Default value for the control mode](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode), which is a value of 0, 1,2,3 or 4 (Automatic, Manual, etc). The CtrlDef defines the current control mode of the equipment set at the PLC level. It takes the same values as the CtrlMode.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[Range](javascript:void(0))

Used to specify the  engineering high and low values for tags that have integer values. For  example, PV, PVTrack, SP, PRHigh, PRLow, ORHigh, ORLow. 

Note that most tags need to have the same range values. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[Alarm Limits](javascript:void(0))

Used to define alarm limits if using analog alarms. 

**Note**: This parameter is not available for valve objects. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[Height](javascript:void(0))

Used only for a Feeder Gate, this is used to specify the engineering range for the height of the gate. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[WindSpeedRange](javascript:void(0))

Used only for a Wind Compass, this is used to specify the high and low values for wind speed tags. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)](javascript:void(0))[SwitchPosition](javascript:void(0))

Used only for a Handswitch  Selector, this tag indicates the position of the handswitch - whether it is left (1), right (2) or center (3).