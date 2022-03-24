[Проект Situational Awareness](../README.md) -> [Situational Awareness Library](readme.md)

## Situational Awareness Library Project

[Сторінка допомоги](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Content/Situational_Awareness_Library_Project.htm)

Проект бібліотеки ситуаційної поінформованості (під назвою "sa_library") - це проект із включенням, який містить набір Genies для звичайних елементів керування інтерфейсом користувача, перелічених у [таблиці](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Library_Project.htm?tocpath=Довідка про системні проекти|Проекти системи ситуаційної поінформованості|Проект бібліотеки ситуаційної поінформованості|_____0#Object_Libraries) нижче.

Крім того, проекти sa_library містять Genies для лічильників, приводів і клапанів, які можна об’єднати для створення [Composite Genies](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/ Content/Composite_Genies.htm). Зверніться до теми [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm), щоб дізнатися, як додати лічильник, диск або клапан на вашу графічну сторінку.

**Примітка.** Проект sa_library Include є проектом системного включення, і він з'являється в дереві списку проектів лише в тому випадку, якщо фільтр **Системні проекти** застосовано в діяльності Проекти. Цей проект включається, коли ви створюєте проект за допомогою проекту Situational Awareness Starter.

### Object Libraries

Library objects are accessible in Graphics Builder from the following object libraries. 

| Library Name      | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
| sa_belt           | Contains [belt objects](belt.md) such as aprons, belts and conveyors. |
| sa_chart          | Contains [additional objects](additional.md) such as polar star and XY Bar Graph. |
| sa_common         | Contains the selection adorner objects to display borders around objects, output bar, tracker, labels and OOS indicators. |
| sa_dataobjects    | Contains  objects such as up/down buttons, numeric and text input that provide  additional methods of displaying data and related properties. |
| sa_deviationmeter | Contains the [Deviation meter](meters.md) object and its components including alarm limits, PV tracker, etc. |
| sa_drive          | Contains [drive objects](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Drive_Objects.htm) such as compressors, brakes, pumps, etc in different sizes and orientations. |
| sa_dualmeter      | Contains the [Dual meter](meters.md) object and its components including alarm limits, PV tracker, etc. |
| sa_faceplates     | Contains the components to build a [faceplate](faceplates.md). |
| sa_meter          | Contains [meter objects](meters.md) such as  analyzer, pressure, temperature meters, etc in different sizes and orientations. |
| sa_mining         | Contains [mining objects](mining.md) such as crushers, cutters, magnets, etc |
| sa_misc           | Contains [additional objects](additional.md) such as alarm light, handswitch selector, etc. |
| sa_trend          | Contains [trend objects](trends.md) such as pens, limits, trend tail, etc. |
| sa_valve          | Contains [valve objects](valves.md) such as simple valves, control valves, damper valves, etc in different sizes and orientations. |

- [Common Object Elements](CommonObjectElements.md)
- [Equipment Custom Parameters](EquipmentCustomParameters.md)
- [Show/Hide Settings](showhidesettings.md)
- [Alarm Limits](AlarmLimits.md)
- [Meters](meters.md)
- [Multiple Meter](multiplemeter.md)
- [Drive, Belt and Mining Objects](driveandother.md)
  - [drive](drive.md)
  - [belt](belt.md)
  - [mining](mining.md)
- [Valves](valves.md)
- [Trends](trends.md)
- [Additional Objects](additional.md)
- [Faceplates](faceplates.md)
- [Core Component Genie Libraries](core.md)