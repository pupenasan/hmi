# Controls Genie Library

The SA_Controls system project includes the "sa_controls" library. It includes the  following Genies:   

- [Alarm List Genie](https://localhost:28808/Plant SCADA/#showid/1206906)
- [Alarm List Vertical Genie](https://localhost:28808/Plant SCADA/#showid/1206907)
- [Generic List Genie](https://localhost:28808/Plant SCADA/#showid/1206908)
- [Generic List Vertical Genie](https://localhost:28808/Plant SCADA/#showid/1206909)
- [List Row Genie](https://localhost:28808/Plant SCADA/#showid/1206910).         

Note: The SA_Inlcude system project also contains a library named "sa_controls". For a      list of the Genies it includes, see Controls Genie Library.   

## Alarm List Genie

Genie Alarm List (з назвою "alarmlist") дозволяє розмістити на графічній сторінці список тривог у заздалегідь визначеному форматі із заголовком таблиці та смугами прокручування. Він є варіантом Genie Alarm List Vertical, який формує список без рядка заголовка і лише з вертикальною смугою прокручування.

Цей Genie можна використовувати разом із List Row Genie, який забезпечує:

- вибір рядків;
- контекстне меню рядка;
- зміну кольору фону рядків.

За замовчуванням Genie списку тривог відображає поля, налаштовані за допомогою Cicode-функції AlarmListCreate. За допомогою цієї ж функції можна також задати шрифти відображення та індикатори тривог.

Детальні інструкції щодо використання Alarm List Genie наведені в розділі «Додавання списку тривог на сторінку».

> Примітка. Також можна використовувати параметр `Citect.ini` [Format]FormatName, щоб задати формат за замовчуванням для полів, які відображаються у списку тривог.

У діалоговому вікні Genie Properties заповніть такі властивості:

| Властивість | Опис                                                         |
| ----------- | ------------------------------------------------------------ |
| AN          | Автоматично згенерований унікальний ідентифікатор об'єкта Genie. |
| Name        | Необов'язкове поле. Якщо потрібно звертатися до Genie під час виконання через Cicode, задайте унікальне ім'я. |



| Параметр                  | Опис                                                         |
| ------------------------- | ------------------------------------------------------------ |
| AN                        | Заповнюється автоматично та відповідає значенню AN у вікні Genie Properties. Змінювати не можна. |
| OnRightClickFunction      | Дозволяє обробити клацання правою кнопкою миші по списку тривог і виконати операції з контекстного меню. |
| OnColumnSelectedFunction  | Викликається при виборі стовпця.                             |
| OnColumnReorderedFunction | Викликається після зміни порядку стовпців. Наприклад, можна використати `ArrayView_SetFormat()`. |
| OnColumnResizedFunction   | Викликається після зміни ширини стовпців.                    |

Щоб Genie працював під час виконання, перед початком анімації необхідно ініціалізувати деякі масиви.

У діалоговому вікні Page Properties, на вкладці Events, налаштуйте такі події.

#### On Page Entry

```cicode
_ArrayView_Initialize();
AlarmListCreate(
    DspGetAnFromName("alarmlist"),
    0,
    700-14,
    318,
    32,
    1,
    "",
    "TopActiveAlarms_UHD4K",
    -1,
    DspFontHnd("SA_AlarmHeader4K")
)
```

Призначення:
Створює список тривог з ім'ям "alarmlist" відповідно до параметрів, заданих у функції `AlarmListCreate`.

#### On Page Exit

```cicode
AlarmListDestroy(DspGetAnFromName("alarmlist"))
```

Призначення:
Знищує масив списку тривог, коли користувач залишає сторінку.

## List Row Genie

Genie List Row використовується разом із Genie Alarm List та Generic List. Він забезпечує вибір рядків, обробку клацання правою кнопкою миші (контекстне меню) та керування кольором фону рядків. Доступні кілька варіантів Genie, які відрізняються максимальною кількістю рядків:

| Genie        | Максимальна кількість рядків |
| ------------ | ---------------------------- |
| List Row x5  | 5                            |
| List Row x10 | 10                           |
| List Row x40 | 40                           |
| List Row x80 | 80                           |

Змінювати розмір Genie на графічній сторінці не потрібно. Під час виконання він автоматично займає область, що відповідає розміру списку, з яким пов'язаний.

Докладніше про використання цього Genie див. у розділах «Додавання списку тривог на сторінку» та «Додавання універсального списку на сторінку».

У вікні Genie Properties доступні дві основні властивості:

- `AN` — автоматично згенерований унікальний ідентифікатор об'єкта Genie.
- `Name` — необов'язкове ім'я Genie. Використовується, якщо до нього потрібно звертатися з Cicode під час виконання.

### Параметри

Параметр `ArrayAN` задає AN списку, до якого застосовуватиметься оформлення рядків. Значення можна отримати за допомогою функції `DspGetAnFromName()`, наприклад:

```cicode
DspGetAnFromName("AlarmList")
```

Параметр `RowOffset` визначає номер рядка, з якого починається відображення даного Genie. За замовчуванням використовується значення `0`. Якщо на сторінці розміщено кілька List Row Genie, для кожного потрібно задати власне зміщення. Наприклад, якщо використано два Genie `List Row x10`, то для першого `RowOffset` дорівнює `0`, а для другого — `10`.

Параметр `LeftClickCommand` дозволяє викликати Cicode при клацанні лівою кнопкою миші по рядку списку. Наприклад, для вибору рядка можна використати:

```cicode
AlarmPage_SelectAlarmRecord(DspGetAnFromName("AlarmList"))
```

Параметр `RightClickCommand` дозволяє викликати Cicode при клацанні правою кнопкою миші по рядку списку. Наприклад:

```cicode
Alarm_TopAlarmsRow_RightClickCommand(DspGetAnFromName("AlarmList"))
```