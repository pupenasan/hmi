[Проект Situational Awareness](README.md)

## Alarms

[Довідка](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Content/Situational_Awareness_Alarms.htm)

Принципи ситуаційної обізнаності вказують на те, що сигнали тривоги повинні передаватися за допомогою легко впізнаваних форм і високоінтенсивного кольору. Це гарантує, що сигнали тривоги виділяються на фоні переважно ахроматичної колірної схеми, яка використовується для інтерфейсу під час виконання.

Також необхідно надати сповіщення про всі активні тривоги, навіть якщо вони виникають на сторінці, яка в даний момент не відображається. Прямий доступ до сторінки, яка є джерелом тривоги, також має бути доступним, коли надходить сповіщення.

У випадку проекту Situational Awareness Starter Project за замовчуванням набір із шести Genies (три великих і три маленьких) включено до "[sa_priorities](file:///C:/Program Files (x86)/AVEVA Plant SCADA/ Bin/Help/SCADA Help/Content/SA_Control_PrioritiesGenieLibrary.htm)", щоб полегшити сигналізацію тривоги відповідно до цих принципів.

​                ![img](media/Situational_Awareness_Alarm_Genies.png)            

Джини також надаються, щоб уявити, коли тривога «shelved», що означає, що тривога вимкнено на певний період часу. See [Shelve Alarms](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Shelve_Alarms.htm). 

​                ![img](media/Situational_Awareness_Alarms_ShelvedIcon.png)            

**Примітка.** Якщо потрібно, ви можете налаштувати зовнішній вигляд цих джинів.

Джини використовуються для виділення сигналів тривоги в наступних місцях.

#### Alarm Indicators

Індикатори тривог використовуються на сторінках вмісту для виділення стану тривоги для певного об’єкта або групи об’єктів. Вони складаються з прапорця тривоги (великий Genie пріоритет тривоги ) і межі тривоги.

​                        ![img](media/Alarm_Indicator.png)                    

For more information, see [Use Alarm Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Use_Alarm_Indicators.htm).

#### Navigation Zone

Зона навігації забезпечує загальносистемний перегляд поточних тривог на всіх сторінках.

Кожна вкладка містить підрахунок трьох найбільш пріоритетних тривожних сигналів, які активні на сторінках, включених на вкладку.

Кожна кнопка містить підрахунок трьох пріоритетних тривожних сигналів і відкладених тривожних сигналів для місця, яке вона відкриває.

​                        ![img](media/Situational_Awareness_Alarm_NavZone.png)                    

For more information, see [Enable Navigation Zone Alarm Counts](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Enable_Navigation_Zone_Alarm_Counts.htm).

#### Alarm lists

Маленькі значки використовуються для виділення трьох основних пріоритетів тривог в списках тривог.

​                        ![img](media/Situational_Awareness_Alarm_AlarmLists.png)                    

If an alarm is shelved, the priority icon will display a white fill. 

This occurs in the following locations:

- Alarms pages (see [Default Alarm Pages](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Default_AlarmPages.htm)).
- The alarms list in the [Information Zone](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Information_Zone.htm).
- the [Active Alarms Zone](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Alarms_Summary.htm) (if a UHD4K workspace is used). 

#### Alarm Page Tree View

Перегляд дерева на кожній сторінці нагадувань надає кількість нагадувань для трьох головних пріоритетів тривоги та відкладених нагадувань у кожній гілці ієрархії обладнання.  (see [Default Alarm Pages](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Default_AlarmPages.htm)).



​                        ![img](media/Situational_Awareness_Alarm_TreeView.png)                    

 

Крім використання кольору для вказівки пріоритету нагадування, зовнішній вигляд індикатора або значка тривоги можна використовувати для відображення поточного стану тривоги.

#### Alarm States

У наступній таблиці показано, як позначаються різні стани тривоги для тривоги з пріоритетом 1 (надзвичайна ситуація) у проекті, заснованому на проекті Situational Awareness Starter Project.

| State              | Alarm Indicator                                              | Alarm icon                                                   |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| On Unacknowledged  | ![img](media/Situational_Awareness_Alarm_States_Unacknowledged.png)    The border and flag both flash between colored and white fill. | ![img](media/Situational_Awareness_Alarm_Icon_Unacknowledged.png)The icon flash between colored and white fill. |
| On Acknowledged    | ![img](media/Situational_Awareness_Alarm_States_Acknowledged.png)The alarm border is filled with a half-intensity color.     There is no flashing for either element.     If the alarm condition clears, the alarm indicator is no longer displayed. | ![img](media/Situational_Awareness_Alarm_Icon_Acknowledged.png)The icon stops flashing. |
| Off Unacknowledged | ![img](media/Situational_Awareness_Alarm_States_Fleeting.png)    The alarm border appears in a lighter color.The alarm flag flashes.The alarm border does not flash. | ![img](media/Situational_Awareness_Alarm_Icon_Fleeting.png)The icon flash between half-intensity color and white fill. |
| Shelved            | ![img](media/Situational_Awareness_Alarm_States_Shelved.png)    A white alarm border is shown with a generic  						alarm flag symbol. | ![img](media/Situational_Awareness_Alarms_Icon_Shelved_35x31.png)In an alarms list, the priority icon will appear with a white fill.![img](media/Situational_Awareness_Alarms_Icon_Shelved2.png)In an alarm tree view and the Navigation Zone, a generic shelved icon will appear. |

За замовчуванням шість Genies   пріоритету тривоги пов’язані з трьома першими пріоритетами тривоги через властивості відображення для кожного пріоритету.

​                ![img](media/Situational_Awareness_Alarm_Priorities.png)            

Властивість **Genie Name** визначає більшого Genie, який використовується як прапорець тривоги; **Small Genie Name** визначає меншого джина, який використовується як піктограма тривоги. Див. [Налаштування властивостей відображення для пріоритету тривоги](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_Display_Properties_for_an_Alarm_Prioirty.htm).

Genies, які використовуються для представлення тривоги на полиці, пов’язані з режимом тривоги під назвою «Shelved/Disabled» (див. [Налаштування властивостей дисплея для режиму тривоги](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_Display_Properties_for_an_Alarm_Mode.htm)).

