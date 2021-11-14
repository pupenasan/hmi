# Scheduled Communications (I/O Devices)

Citect SCADA дозволяє планувати зв'язок з вашими пристроями вводу/виводу (незалежно від типу підключення: модем, радіозв'язок тощо). Наприклад, якщо у вас є кілька пристроїв вводу-виводу в одній мережі або лінії, ви можете запланувати читання, щоб важливі пристрої вводу-виводу зчитувалися частіше, ніж менш важливі пристрої вводу-виводу. Крім того, постачальник води з підключенням по радіоканалу до моніторів рівня греблі може запланувати щогодинні зчитування рівня з Citect SCADA, щоб зберегти пропускну здатність.

## Specifying a Schedule

Щоб налаштувати запланований зв’язок із пристроєм вводу/виводу, потрібно позначити його як пристрій «Scheduled». Це робиться за допомогою **Device Communications Wizard**. Якщо ваш пристрій вводу-виводу не підтримує заплановані зв’язки, параметри планування не будуть представлені майстром.

**Примітка.** Заплановані комунікації не працюватимуть для драйверів, які призначені для обробки протоколів Report-By-Exception. Для зв’язку з вашим пристроєм вводу-виводу поза розкладом використовуйте функцію IODeviceControl.

To schedule communications with an I/O Device:

1. Navigate to the Topology activity | I/O Devices. 

2. Click **New Device** on the Command Bar. The 

3. Double-click the **Express I/O Device Setup** icon in the Communications folder of the current project.

4. Follow the instructions to work through the screens, selecting the relevant I/O Device, and so on. When the scheduling screen displays, check the **Connect I/O Device to PSTN** box, even if your I/O Device is not connected via a modem (but leave the Phone number to dial and Caller ID fields blank). 

5. Fill out the schedule fields to achieve the desired schedule. For example (all based on a **Synchronize at** time of 10:00:00).

6. If you enter 12:00:00 in the **Repeat every** field, and start your project at 9 a.m., the I/O Server will  communicate with the I/O Device at 10 a.m., then once every 12 hours  after that, i.e. 10 p.m., then again at 10 a.m. of the following day,  etc. 

7. - If you enter 12:00:00, and start your project at 4 p.m., the I/O Server will communicate with  the I/O Server at 10 p.m., then again at 10 a.m. of the following day,  etc. i.e. it will assume that communications were established at 10  a.m., so it continues as if they had been, communicating once every 12  hours after 10 a.m.
   - If you enter 3 days,  and start your project at 9 a.m. on a Wednesday, the I/O Server will  communicate with the I/O Device at 10 a.m., then once every 3 days after that, i.e. 10 a.m. on the following Saturday, then at 10 a.m. on the  following Tuesday, etc.
   - If you enter the 6th of December in the **Repeat every**, and start your project during November, the I/O Server will communicate with the I/O Device at 10 a.m. on December 6, then again on December 6  of the following year, and so on.

8. Select **On Startup** for a persistent connection. To disconnect a persistent connection, you need to call the IODeviceControl() function with type 8.

9. If your I/O Device is not  connected via a modem, you need to go to the Ports form (select Ports  from the Communication menu) and change the Port number to the actual  number of the COM port.

## Writing to the Scheduled I/O Device

Щоразу, коли пристрій вводу/виводу активно спілкується (згідно з його розкладом), ви можете писати йому безпосередньо. Однак, якщо ви спробуєте написати до нього, коли він не зв’язується, ваш запит на запис буде стояти в черзі, доки зявиться така можливість. Наприклад, ви можете вирішити запланувати один запис на годину. Якщо хтось із Control Client змінить значення тега протягом цієї години, ця зміна не буде записана на пристрій введення-виведення, доки не закінчиться час.

Оскільки запити на запис не записуються на пристрій вводу-виводу, доки він не з’єднається, переконайтеся, що незавершені записи були завершені повністю, перш ніж завершити роботу.

**Примітка.** Не керуйте обладнанням за допомогою запланованого пристрою введення-виведення, оскільки точний стан обладнання може бути невідомим. Хоча ви можете прочитати стан із кешу, він міг змінитися після створення кешу.                                            

## Reading from the scheduled I/O Device

Коли Сервер вводу-виводу ініціює зв'язок з пристроєм вводу-виводу, він негайно записує будь-які запити на запис у черзі, а потім зчитує теги пристрою вводу-виводу. Ці значення потім зберігаються в кеші, щоб ви могли отримати до них доступ між комунікаціями.

**Примітка.** Оскільки сервер введення-виводу зчитує теги під час початку зв'язку, кількість точок ліцензії збільшується, навіть якщо деякі з прочитаних тегів насправді можуть не використовуватися.

### Keeping Data Up-to-Date during Prolonged connections 

Як правило, зв’язок припиняється, як тільки буде виконано кожен запит на читання та запис. Однак іноді ви можете продовжити зв’язок (наприклад, викликавши функцію IODeviceControl() з типом 7).

У цій ситуації (якщо наскрізне кешування вимкнено), коли клієнтські комп’ютери запитують дані пристрою від сервера вводу-виводу, він отримує дані зі свого кешу, а не з пристрою вводу-виводу. Це відбувається, навіть якщо сервер введення-виведення підтримує з’єднання з пристроєм.

Щоб отримати свіжі дані з пристрою введення-виводу, ви можете примусово виконувати періодичне читання за допомогою Cicode або змінити час очікування кешу, встановивши для функції IODeviceControl() значення Тип 11.

Наприклад:

```pascal
INT hTask;
// Initiate communications and read tags.
// Sleep time will depend on how fast your
// modems connect.
FUNCTION
DialDevice(STRING sDevice)
	INT bConnected = 0;
	INT nRetry = 5;
	hTask = TaskHnd("");
	IODeviceControl(sDevice, 7, 0);
	Sleep(20);
	WHILE bConnected <> 1 AND nRetry > 0 DO
		bConnected = IODeviceInfo(sDevice, 18);
		nRetry = nRetry - 1;
		Sleep(10);
	END
	IF bConnected = 1 THEN
		WHILE TRUE DO
			Sleep(2);
			IODeviceControl(sDevice, 16, 0);
		END
	END
END
// Kill the read task and terminate the connection.
FUNCTION
HangupDevice(STRING sDevice)
	TaskKill(hTask);
	IODeviceControl(sDevice, 8, 0);
END
```

Ви також можете змусити сервер вводу-виводу зчитувати дані безпосередньо з пристрою вводу-виводу, увімкнувши кешування наскрізне читання. Якщо налаштувати параметр `[Dial]ReadThroughCache`, сервер вводу-виводу підключений до пристрою, він надаватиме дані клієнтам-запитувачам безпосередньо з пристрою. Кеш не оновлюється протягом цього часу, але оновлюється останніми даними пристрою безпосередньо перед відключенням сервера.

**Примітка.** Якщо ви використовуєте модеми, вам може знадобитися налаштувати або деактивувати таймер бездіяльності у ваших модемах, щоб вони не відключалися, поки дані не зчитуються. Таймер бездіяльності керується регістром S30. Якщо ваш модем не підтримує цей регістр, зверніться до посібника з модему.

### Avoiding Unnecessary Multiple Reads of I/O Device Data

Щоб уникнути непотрібного читання пристрою вводу-виводу, ви можете використовувати кешування даних для тимчасового зберігання даних, зчитованих з пристрою, в пам'яті сервера введення-виводу. Це означає, що якщо сервер вводу-виводу отримує більше одного запиту на дані пристрою протягом короткого періоду часу, замість того, щоб вдруге звертатися до пристрою вводу-виводу та читати ідентичні дані, він може отримати дані з кешу.



## IODeviceControl (Function)

Забезпечує керування окремими пристроями вводу-виводу. Можливо, вам доведеться викликати цю функцію кілька разів. Якщо ви використовуєте несумісні значення для різних параметрів цієї функції, ви можете отримати непередбачувані результати.

Цю функцію можна використовувати, лише якщо сервер введення-виведення знаходиться на поточній машині. Коли сервер вводу-виводу не перебуває у процесі виклику, ця функція блокується, і її не можна буде викликати із завдання переднього плану. У цьому випадку значення, що повертається, буде невизначеним, і буде спрацьовано апаратну тривогу Cicode.

```
IODeviceControl(IODevice, nType, Data [, sClusterName] [, ServerName] )
```

*IODevice:* The number or name of the I/O  device. If you call this function from an I/O server, you can use the  I/O device name. If you call this function from a client, you may use  either the I/O device number or name. To specify all I/O devices, use  "*" (asterisk) or -1.

*nType:*  The type of control action:

*1* -  Увімкнути/вимкнути пристрій вводу-виводу на сервері вводу-виводу. Якщо вимкнено, спроби читання та запису з пристрою вводу/виводу ігноруються. (Якщо інший пристрій вводу-виводу налаштовано як резервний сервер вводу-виводу, Citect SCADA перемикає зв'язок на цей пристрій вводу-виводу.) Сервер вводу-виводу не намагається зв'язатися з пристроєм введення-виводу, доки його не буде повторно увімкнено. Коли пристрій вводу-виводу знову вмикається, сервер вводу-виводу намагається негайно відновити зв'язок. Режим 1 може бути викликаний лише сервером вводу-виводу, який пов’язаний з цим пристроєм.

*4* -  Дані в асоційованому кеші пристрою вводу-виводу очищаються. Це дозволяє очищати дані з пристрою вводу-виводу, не чекаючи часу старіння. Це корисно, якщо у вас довгий час кешування, і ви хочете примусово читати з пристрою введення-виводу.

The Data value is ignored with this mode.

*5* - (For  scheduled and remote I/O devices). Пристрій вводу/виводу додається в нижню частину списку пристроїв вводу/виводу, до яких потрібно зв’язатися. Пристроям введення-виводу, які вже є у списку (уже чекають на зв'язок), надається пріоритет над цим пристроєм введення-виводу.

*6* - (For  scheduled and remote I/O devices). Пристрій вводу-виводу додається вгору списку пристроїв вводу-виводу, до якого необхідно зв'язатися; йому надається високий пріоритет. Якщо у верхній частині списку вже є пристрої вводу-виводу з високим пріоритетом, то цей пристрій вводу-виводу буде додано до списку після них (тобто до нього буде звертатися після них). Для пристроїв віддаленого вводу/виводу, якщо модем уже використовується – підключений до іншого пристрою введення/виводу – цей пристрій вводу/виводу не буде набране, доки це з’єднання не буде розірвано.

*7* - (For  scheduled and remote I/O devices). Пристрій вводу-виводу додається до початку списку пристроїв вводу-виводу, до якого потрібно зв'язатися, і йому надається найвищий пріоритет. Для пристроїв віддаленого вводу/виводу, якщо модем наразі підключений до іншого пристрою введення/виводу, з’єднання буде скасовано, а пристрій вводу/виводу з вищим пріоритетом буде набрано. Він також залишатиметься підключеним до тих пір, поки не буде відключено вручну за допомогою іншого виклику IODeviceControl().

**Note:** This mode will  not attempt to disconnect any other persistent connections. Persistent  connections can only be disconnected using mode 8.

*8* - (For  scheduled and remote I/O devices). Від’єднайте пристрій введення-виведення. Поточні запити будуть виконані до того, як пристрій введення-виведення буде відключено.

*9* - (For  scheduled I/O devices). Розклад зв’язку для пристрою вводу-виводу вимкнено. Це робиться для того, щоб звести до мінімуму ймовірність того, що пристрій вводу-виводу зв’яжеться, коли настане час його запланованого набору.

*10* - (For  scheduled I/O devices). Переводить пристрій введення-виводу в режим запису на запит. Тобто, щойно буде зроблено запит на запис, пристрій вводу-виводу буде додано до списку пристроїв вводу-виводу, з яким потрібно зв'язатися. Йому надається пріоритет над існуючими запитами на читання, але не над існуючими запитами на запис.

In this situation, there will be a delay  while the I/O device is contacted. Do not mistake this pause for  inactivity (for example, do not continually execute a command during  this delay).

*11* - Change the  I/O device cache timeout. If the I/O Server is restarted, the cache  timeout will return to its original value. (For scheduled I/O devices,  this value can be checked using the Kernel Page Unit command. For all  other I/O devices, this value is configured in the Cache Time field at  the I/O Devices Properties form.)

*12* - The time of  day at which to add the I/O device to the list of I/O devices to be  contacted. Set the time in Data in seconds from midnight (for example,  specify 6 p.m. as 18 * 60 * 60). Use Type 12 to specify a  one-timecommunication.

*13* - The  communication period (the time between successive communication  attempts). The value you specify represents different periods, depending on what type of schedule you are using (that is daily, weekly, monthly, or yearly. This is set using Type 15.). You can choose to specify the  communication period either in seconds from midnight, day of week  (0 to 6, Sunday = 0), month (1 to 12), or year. Enter the value in Data. For example, if your schedule is weekly, and you set Data = 3, you are  specifying each Wednesday. If your schedule is monthly, Data = 3  indicates March. For daily communication, set the period in Data in  seconds from midnight; for example, set Data to 6  * 60 * 60 to contact  the I/O device every 6 hours.

*14* - The time at  which the I/O Server will first attempt to communicate with the I/O  device. Set the time in Data in seconds from midnight, for example, to  synchronize at 10a.m., set Data to 10 * 60 * 60.

*15* - Type of schedule. Set *Data* to one of the following:

- 1 - Daily
- 2 - Weekly
- 3 - Monthly
- 4 - Yearly

*16* - (For remote I/O devices) Read all tags from the I/O device. Data is unused - set it to 0 (zero).

*18* - Set Control Inhibit (Control Mode) for all tags of the I/O device.

*Data:*  Data for the control operation*:

*1*:

- Disable the I/O device (Disable Write On Request mode for Type 10)
- Set Control Inhibit to ON (mode for type 18)

*0*:

- Enable the I/O device (Enable Write On Request mode for Type 10) or the I/O device name (for Type 2 or 3).
- Set Control Inhibit to OFF (mode for type 18)

\* For Type 5-8, Data is ignored; enter 0 (zero).

*sClusterName:*  Specifies the name of the cluster  in which the I/O Server resides. This is optional if you have one  cluster or are resolving the I/O server via the current cluster context. The argument is enclosed in quotation marks "".

ServerName: Specifies the name of the the I/O  Server. This parameter is only required if you are running more than one I/O server process from the same cluster on the same computer and need  to instruct the system which process to redirect to. The argument is  enclosed in quotation marks "".