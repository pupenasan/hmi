[Проект Situational Awareness](../README.md) -> [Situational Awareness Library](readme.md)

### Equipment Custom Parameters

Наступні параметри обладнання, визначені в шаблоні обладнання, застосовні до більшості індикаторів, приводів і клапанів. Вони налаштовуються для кожного [створеного екземпляра обладнання](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Add_an_Equipment_Instance.htm) у редакторі обладнання. Будь-який виняток зазначається в описі параметра.

[![img](G:\san\AKIT\ДИСЦИП\ЛМІ\GitVer\citect\sa2020\salib\media\Custom_Parameters_thumb_600_600.png)](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/images/Custom_Parameters.png)            

**InternalIODevice**

Ім’я постійної пам’яті ПЛК , що зберігає значення внутрішніх тегів для керування значенням об’єкта бібліотеки. Наприклад, теги PRHigh, PRLow, ORHigh і ORLow можуть існувати в PLC

**CicodeIODevice**

Назва пристрою вводу-виводу, який використовується для зберігання значень обчислюваних змінних. Наприклад, EqStatus.

**EqStatusFunc**

Назва функції Cicode, необхідної для оцінки значення індикатора стану. Наприклад, EquipmentStatus_Drive_GetValue.

**CtrlMode**

[Значення за замовчуванням для режиму керування](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/ASM_COntrol_Meters_Common_Elements.htm#Meters_Mode), яке є значенням 0, 1,2,3 або 4 (автоматичний, ручний тощо). CtrlDef означує поточний режим керування обладнанням, встановленим на рівні ПЛК. Він приймає ті ж значення, що й CtrlMode.

**Range**

Використовується для означення інженерних високих і низьких значень для тегів, які мають цілі значення. Наприклад, PV, PVTrack, SP, PRHigh, PRLow, ORHigh, ORLow.

Зауважте, що більшість тегів повинні мати однакові значення діапазону.

**Alarm Limits**

Використовується для означення меж тривог при використанні аналогових тривог.

**Примітка**: цей параметр недоступний для об'єктів клапана.

**Height**

Використовується лише для Feeder Gate, він використовується для означення інженерного діапазону висоти воріт.

**WindSpeedRange**

Використовується лише для Wind Compass, він використовується для визначення високих і низьких значень для тегів швидкості вітру. 

**SwitchPosition**

Цей тег, який використовується лише для перемикача ручного перемикача, вказує положення ручного перемикача – ліворуч (1), праворуч (2) чи центральне (3).

[--> Show/Hide Settings](showhidesettings.md)