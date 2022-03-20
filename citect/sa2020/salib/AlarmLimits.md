#### Alarm Limits

Alarm limits indicate when a process variable will trigger an alarm in the system. The Situational Awareness support in Plant SCADA allows these limits to be visualized using the Meter Composite Genie library object and its associated faceplates. 

The Meter Composite Genie and faceplates that display meters support:

- Analog alarm tag limits (a single analog alarm defining all the limits) and
- PLC tag-based alarm limits (separate I/O tags to define each limit).

Tag-based alarm limits are particularly  useful if you want dynamic control of the limits and/or if you want to  specify a different category for each limit. 

​                ![img](media/Faceplate.png)            

**Note**: Up to 14 limits  may be defined, but the Meter object supports display of only 4 limits.  However, you can build your own meter object with 6 limits for example.

За замовчуванням все аналогове обладнання та ваш проект налаштовані на використання обмежень аналогової сигналізації. У більшості ситуацій лічильник буде відображати елемент ".PV" для вашого обладнання. Об’єкти вимірювача автоматично отримають ваші значення HighHigh, High, Low і LowLow з відповідного аналогового PV тега тривоги.

Під час використання проектів на основі ситуаційної обізнаності цю поведінку можна змінити такими способами:

1. Використовуйте analog alarm limits для всього обладнання
2. Використовуйте analog alarm limits для більшості обладнання та PLC-based alarm limits для кожного обладнання
3. Використовуйте PLC-based alarm limits для всього обладнання
4. Використовуйте PLC-based alarm limits для більшості обладнання та analog alarm limits для кожного обладнання.

The default you choose will depend upon:

- The number of analog equipment in your system that will use one or the other method
- The importance of the limits in your system. Analog Alarm Limits in Plant SCADA all share the same category. If you want a different category for HH as opposed to LL, PLC-based alarm limits should be used.

##### Configure PLC Limits with Equipment

The steps for setting up and using PLC limits are:

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)1. Choose the default mode for limits (PLC tags or analog alarm limits).](javascript:void(0))

To use PLC limits for all meters, set the INI parameter [[Workspace.Meter\]UseDefaultPLCLimits=TRUE](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/ParametersCitectHTML/Content/SA_Library_Meter_UseDefaultPLCLimits.htm).

To override the behavior of this parameter per equipment, [add an equipment runtime parameter](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Manually_Define_Equipment_Runtime_Param.htm). For more details, see [Step 5](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm?tocpath=System Projects Reference|Situational Awareness System Projects|Situational Awareness Library Project|Alarm Limits|_____1#Step5) below. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)2. Define the Equipment Items Names that the meter limits will use as the source in ](javascript:void(0))[[SA_Library.Meter\]PLCLimitNames](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/ParametersCitectHTML/Content/SA_Library_Meter_PLCLimitNames.htm).

When PLC limits are used, you need to configure a set of custom Equipment Item names representing each of the limits. In the **Setup** Activity, **Parameters** view, add the tags (item names) as a comma separated list as shown below.

​                        ![img](media/PLCLImits_Names.png)                    

The meter library objects will then look for items with these names on your equipment. 

As these items will need to exist alongside your equipment's other items (for example, PV), it is  recommended to use an identifier which makes it clear that they are  limit items (for example, Limit).

**Note**: Up to 14  limits may be defined, but the Meter object supports display of only 4.  However, you can build your own meter object with 6 limits for example. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)3. Define the Analog Limit Labels to display in faceplates](javascript:void(0))

Configure the limit labels  for each of your limits (for example, HH). The limit labels are defined  at a global level as a comma separated list via the parameter [[SA_Library.Meter\]PLCLimitLabels](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/ParametersCitectHTML/Content/SA_Library_Meter_PLCLimitLabel.htm).

​                            ![img](media/PLCLImitLabels_648x60.png)                        

**Note**: The limits should be listed in the same order as the item names, and the number of items defined should be the same.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)4. Define the default Analog Limits](javascript:void(0))

Define the default  PLC alarm limits to use for analog equipment. These are defined at a  global level as a comma-separated list via the parameter [[SA_Library.Meter\]DefaultPLCLimits](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/ParametersCitectHTML/Content/SA_Library_Meter_DefaultPLCLimits.htm).

Typically, you would assign  0 = LL, 1 = L, 2 = H and 3 = HH. This matches the order in which the  limit labels are specified. If you wanted to define only H and HH as the default, you would set the **Value** to -1, -1, 2, 3. 

**Note**: The -1 in the **Value** column means “ignore” the first default limits.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)5. Configure the "PLCLimits" equipment runtime parameter](javascript:void(0))

When the alarm limits need to differ for a specific piece of equipment, the **PLCLimits** equipment runtime parameter can be configured to override the default.

For example, if only H and HH are required, then this can be configured using Equipment Runtime Parameters as shown below  .

​                        ![img](media/PLCLimits_RuntimeParam1.png)                    

To configure this:

1.  In Plant SCADA Studio, navigate to **System Model** activity and select **Equipment**. Select **Runtime Parameters** from the drop-down menu. 
2. For each equipment that needs to override the default limits, in the **Name** property, type PLCLimits. 
3. In the **Value** property, specify your comma-separated list of default PLC limits, that is the order in which the defined PLC alarm limits need to be used. Use the value -1 to skip limits that are not required. 

**Note**`: Setting the **Value** property to * reverses the setting of the UseDefaultPLCLimits  parameter. Therefore, if the UseDefaultPLCLimits parameter is set to  TRUE, it will be reversed and applied as if it were set to FALSE. In  this case, analog alarm limits will apply. If UseDefaultPLCLimits is  FALSE, setting the value of the runtime parameter to * will cause the  associated equipment to use the default PLC limits defined at the  project level.

1. Set the **Is Tag** property to FALSE so that the PLC limit labels are displayed on the meter faceplates.
2. Click **Save**.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)6. Generate variable tag Items for each limit item on your analog equipment.](javascript:void(0))

Усе аналогове обладнання, яке буде відображатися як лічильники, потім потрібно буде налаштувати на включення змінних елементів для цих меж. Ваш код PLC може потім встановити значення за замовчуванням для цих обмежень, або це можна зробити за допомогою Cicode.

​                        ![img](media/PLCLImits_Variables.png)                    

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)7. Generate variable tags representing the condition of the PV against each limit](javascript:void(0))

Після встановлення обмежень створіть цифрову змінну, щоб відобразити, коли PV-сигнал перевищує межу.

Для змінної це може бути керовано з самого PLC, або ви можете використовувати [розрахунковий вираз](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/ Content/Calculated_Variables.htm), який працюватиме на сервері вводу-виводу, як показано нижче:

​                        ![img](media/PLC_DigitalVariable.png)                    

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)8. Generate digital alarm tags.](javascript:void(0))

Цифрові сигнали можуть бути створені для кожного граничного елемента, що дасть вам детальний контроль пріоритету тривоги (категорії). Кожна тривожна сигналізація повинна бути прив’язана до відповідного цифрового тега стану, визначеного в [Крок 7](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_PLC_Limits_with_Equipment.htm?tocpath =Довідка про системні проекти|Проекти системи ситуаційної поінформованості|Проект бібліотеки ситуаційної поінформованості|Обмеження сигналізації|_____1#Крок7).