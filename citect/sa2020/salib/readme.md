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
| sa_belt           | Містить [ланцюгові об’єкти](belt.md), такі як жолоб, стрічки та конвеєри. |
| sa_chart          | Містить [додаткові об’єкти](additional.md), такі як полярна зірка та стовпчаста діаграма XY. |
| sa_common         | Містить об'єкти прикраси виділення для відображення меж навколо об'єктів, панелі виводу, трекера, міток та індикаторів OOS. |
| sa_dataobjects    | Містить такі об’єкти, як кнопки вгору/вниз, числове та текстове введення, які надають додаткові методи відображення даних і пов’язаних властивостей. |
| sa_deviationmeter | Містить об’єкт [Deviation meter](meters.md) та його компоненти, включаючи межі сигналізації, PV-трекер тощо. |
| sa_drive          | Містить [об’єкти приводів](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_Drive_Objects.htm), такі як компресори, гальма, насоси тощо різних розмірів та орієнтації. |
| sa_dualmeter      | Містить об’єкт [Dual meter](meters.md) та його компоненти, включаючи межі сигналізації, PV-трекер тощо. |
| sa_faceplates     | Містить компоненти для створення [faceplates](faceplates.md). |
| sa_meter          | Містить [об’єкти вимірювання](meters.md), такі як аналізатор, вимірювач тиску, температури тощо в різних розмірах та орієнтаціях. |
| sa_mining         | Містить [об'єкти видобутку](mining.md), такі як дробарки, різаки, магніти тощо |
| sa_misc           | Містить [додаткові об’єкти](additional.md), такі як тривоги, перемикач ручного перемикача тощо. |
| sa_trend          | Містить [об’єкти тренду](trends.md), такі як ручки, межі, край тренду тощо. |
| sa_valve          | Містить [об'єкти клапанів](valves.md), такі як прості клапани, регулюючі клапани, клапани заслонок тощо в різних розмірах та орієнтаціях |

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