## Використання користувацьких фільтрів тривог

Для тегів тривог можна визначати власні ключові слова, які потім використовуються для виконання спеціалізованих запитів до даних тривог.

У діалоговому вікні `Alarm Properties` для кожної тривоги можна налаштувати до восьми користувацьких фільтрів (`Custom Filter`). Це дозволяє створювати запити, які відбирають тривоги за додатковими критеріями.

Наприклад, якщо необхідно швидко знаходити тривоги, пов'язані з пожежною небезпекою, можна для всіх відповідних тегів задати значення `fire hazard` у полі `Custom Filter 1`. Після цього Cicode може виконувати запити, які відбирають лише ті тривоги, у яких поле `Custom Filter 1` має значення `fire hazard`. У результаті оператор отримає список тривог, що стосуються потенційно пожежонебезпечних ситуацій.

Аналогічно можна використовувати `Custom Filter 2` для позначення типу обладнання, з яким пов'язана тривога. Наприклад, присвоїти значення `pump`, `conveyor` тощо. Це дозволить формувати запити, які відображають тривоги лише для певного типу обладнання, наприклад усі тривоги, пов'язані з насосами.

### Реалізація запитів із використанням користувацьких фільтрів тривог

Для створення запитів, що використовують користувацькі фільтри тривог, застосовуються такі функції Cicode:

- `AlarmFilterEditOpen`
- `AlarmFilterEditAppend`
- `AlarmFilterEditSet`
- `AlarmFilterEditCommit`
- `AlarmFilterEditFirst`
- `AlarmFilterEditLast`
- `AlarmFilterEditNext`
- `AlarmFilterEditClose`

Тривоги також можна фільтрувати за допомогою функції `AlarmSetInfo`, використовуючи `Type = 12` та іменований фільтр (див. розділ «Named Filters»).

> Примітка. Якщо сформований фільтр виявиться занадто складним (наприклад, містить надто багато умов або вкладених дужок), він буде автоматично очищений і не застосовуватиметься. При цьому на клієнті буде згенерована апаратна тривога `Too many alarms in filters`, а в журналі трасування (TraceLog) з'явиться повідомлення про помилку.

Припустимо, потрібно отримати список поточних тривог, пов'язаних із конвеєрами. Для цього в полі `Custom Filter 1` відповідних тривог можна записати значення `conveyor`.

Далі за допомогою функцій `AlarmFilterEditSet()` і `AlarmFilterEditCommit()` формується та застосовується фільтр:

```cicode
AlarmFilterEditSet(hndl, "Custom1=conveyor");
AlarmFilterEditCommit(hndl);
```

Нижче наведено приклад функції `FilterCustom1()`, яка відображає лише ті тривоги, для яких значення `Custom Filter 1` збігається з переданим параметром.

```pascal
INT FUNCTION FilterCustom1(STRING sValue)
    INT iResult = -1;
    INT iHndl = -1;
    STRING sFilter = "";
    sFilter = "Custom1=" + "^"" + sValue + "^"";
    iHndl = AlarmFilterEditOpen(21);
    IF iHndl <> -1 THEN
        iResult = AlarmFilterEditSet(iHndl, sFilter);
        IF iResult = 0 THEN
            iResult = AlarmFilterEditCommit(iHndl);
        END
        AlarmFilterEditClose(iHndl);
    END
    RETURN iResult;
END
```

Після цього для кнопки на графічній сторінці достатньо викликати:

```cicode
FilterCustom1("conveyor");
```

Для скидання фільтра можна використати такий код:

```cicode
hSession = AlarmFilterEditOpen(21);
AlarmFilterEditSet(hSession, "");
AlarmFilterEditCommit(hSession);
AlarmFilterEditClose(hSession);
```

Можна реалізувати як окремі функції для конкретних полів (наприклад, `FilterCustom1("pumpcontrol")`), так і універсальну функцію, яка приймає готовий вираз фільтра, наприклад `CUSTOM1=pumpcontrol`. У другому випадку функція аналізує переданий рядок і формує фільтр для зазначеного поля.

### Іменовані фільтри

Іменований фільтр можна створити один раз і використовувати одночасно для кількох списків тривог. Іменований фільтр може застосовуватися до списку тривог або лічильника тривог лише тоді, коли цей список або лічильник пов’язаний із фільтром. Сам іменований фільтр не фільтрує тривоги безпосередньо. Він використовується для одночасного оновлення активного фільтра в кількох списках або лічильниках тривог.

Після створення іменованого фільтра його потрібно відредагувати та додати необхідні критерії фільтрації. Щоб пов’язати список тривог з іменованим фільтром, використовується виклик:

```cicode
AlarmSetInfo(AN, 12, "NamedFilter");
```

Тут `AN` — номер анімації списку тривог, `12` — режим прив’язування іменованого фільтра, а `"NamedFilter"` — ім’я фільтра, попередньо створеного функцією `AlarmFilterOpen()`.

Щоб відв’язати фільтр від списку тривог, потрібно передати порожній рядок:

```cicode
AlarmSetInfo(AN, 12, "");
```

Це видаляє зв’язок з іменованим фільтром, але сам список тривог не оновлюється автоматично. Тому попередній фільтр залишатиметься активним, доки не буде застосовано новий.

Щоб пов’язати лічильник тривог з іменованим фільтром, використовується функція:

```cicode
AlarmCount(Type, "NamedFilter", KeepAliveSeconds, CacheMode);
```

Параметри `Type`, `KeepAliveSeconds` і `CacheMode` описані у документації функції `AlarmCount`, а `"NamedFilter"` — це ім’я фільтра, попередньо відкритого функцією `AlarmFilterOpen()`.

Після зміни критеріїв іменованого фільтра автоматично оновлюються всі пов’язані з ним списки та лічильники тривог.

Примітка. Якщо фільтр занадто складний, наприклад містить забагато умов або вкладених дужок, він буде очищений і не застосовуватиметься. При цьому на клієнті буде згенерована апаратна тривога `Too many alarms in filters`, а в журналі трасування з’явиться повідомлення про помилку.

Нижче наведено приклад створення, редагування, прив’язування, відв’язування та закриття іменованого фільтра `MyFilter`.

```pascal
INT FUNCTION AlarmNamedFilterExamples()

    INT iError;
    INT iHndl;

    INT iAN = 21;
    INT iOpenModeNew = 1;
    INT iCloseModeManual = 0;

    INT iAlarmCounted = 0;
    INT iAlarmDisplayed = 0;

    STRING sName;
    STRING sEmptyString = "";
    STRING sNamedFilter;
    STRING sLinkedFilter;

    ! Створити новий фільтр "MyFilter"

    sNamedFilter = "MyFilter";

    iError = AlarmFilterOpen(
        sNamedFilter,
        iOpenModeNew,
        iCloseModeManual
    );

    IF iError <> 0 THEN
        Prompt("MyFilter open error!");
        RETURN iError;
    END;

    ! Задати фільтрацію за категорією 1 та областю 0

    iHndl = AlarmFilterEditOpen(sNamedFilter);

    IF iHndl <> -1 THEN

        iError = AlarmFilterEditSet(
            iHndl,
            "Category=1;Area=0;"
        );

        IF iError = 0 THEN
            iError = AlarmFilterEditCommit(iHndl);

            IF iError = 0 THEN
                iError = AlarmFilterEditClose(iHndl);
            END
        END

        IF iError <> 0 THEN
            Prompt("MyFilter edit error!");
            RETURN iError;
        END

    ELSE
        Prompt("MyFilter hndl-edit error!");
        RETURN iHndl;
    END;

    ! Відкрити сторінку тривог і пов’язати список з фільтром

    PageDisplay("Alarm");

    iError = AlarmSetInfo(iAN, 12, sNamedFilter);

    IF iError <> 0 THEN
        Prompt("MyFilter link error!");
        RETURN iError;
    END

    ! Перевірити ім’я пов’язаного фільтра

    sLinkedFilter = AlarmGetFilterName(iAN);

    IF sLinkedFilter <> sNamedFilter THEN
        Prompt("MyFilter get-name error!");
        RETURN iError;
    END;

    ! Порівняти кількість тривог у фільтрі та у списку

    iAlarmCounted = AlarmCount(
        0,
        sNamedFilter,
        1,
        0
    );

    iAlarmDisplayed = AlarmCountList(iAN);

    IF iAlarmCounted <> iAlarmDisplayed THEN
        Prompt("Count verification error!");
        RETURN iError;
    END;

    ! Відв’язати фільтр від списку

    iError = AlarmSetInfo(iAN, 12, "");

    IF iError <> 0 THEN
        Prompt("MyFilter unlink error!");
        RETURN iError;
    END;

    ! Перевірити відв’язування

    sName = AlarmGetFilterName(iAN);

    IF sName <> sEmptyString THEN
        Prompt("MyFilter unlink error!");
        RETURN iError;
    END;

    ! Закрити фільтр

    iError = AlarmFilterClose(sNamedFilter);

    IF iError <> 0 THEN
        Prompt("MyFilter Close error!");
    END;

    RETURN iError;

END
```

У цьому прикладі функція спочатку створює фільтр `MyFilter`, потім задає умови `Category=1;Area=0`, пов’язує фільтр зі списком тривог із `AN = 21`, перевіряє правильність прив’язування та кількість відображених тривог, після чого відв’язує і закриває фільтр.

### Реалізація фільтрів тривог за допомогою Cicode

Для списків історичних подій можна створити та застосувати окремий фільтр. Такий фільтр не є спільним для кількох списків.

Фільтр складається з набору умов для різних полів, які визначають, які рядки потрібно відображати. Оскільки вираз може бути досить довгим, а Cicode дозволяє використовувати рядки довжиною лише до 254 символів, функції `Set` і `Append` дають змогу розбити фільтр на кілька коротших частин.

Окремі частини не перевіряються на правильність синтаксису під час додавання. Повний фільтр, утворений шляхом об’єднання всіх частин, перевіряється та застосовується пізніше за допомогою функції `Commit`.

Кілька задач Cicode можуть одночасно працювати з одним фільтром і змінювати його. Перегляд і редагування фільтра виконуються в межах окремого сеансу, подібно до механізму перегляду тегів.

#### Синтаксис фільтра

Вираз фільтра може містити ім’я поля, оператор порівняння та значення. Наприклад:

```text
Tag=A
```

Полем може бути будь-яке ім’я, зазначене у довіднику полів перегляду (`Browse Field Reference`).

Підтримуються такі оператори порівняння:

```text
<  <=  >  >=  =  <>
```

Значення може бути рядком, цілим числом, датою і часом або булевим значенням.

Окремі умови можна об’єднувати логічними операторами:

```text
AND
OR
Eqv
NOT
Xor
```

Кілька виразів фільтра можна розділяти крапкою з комою. Крапка з комою інтерпретується як оператор `AND`.

Формальний синтаксис фільтра має такий вигляд:

```text
<filter> ::= <filter_expr> { ";" <filter_expr> }

<filter_expr> ::=
      ["("] <filter_expr> [")"] <logical_binary_op> ["("] <filter_expr> [")"]
    | <comparison>
    | "NOT" "(" <filter_expr> ")"

<comparison> ::= <field> <comparison_op> <value>

<comparison_op> ::= "=" | ">" | "<" | ">=" | "<="

<logical_binary_op> ::= "AND" | "OR"

<value> ::= <string_value> | <boolean_value> | <DateTime_value> | <int_value>

<string_value> ::= <singleword> ["*"]
                 | "'" <singleword> { <space> <singleword> ["*"] } "'"

<singleword> ::= будь-які символи, крім пробілу

<boolean_value> ::= "0" | "1"

<int_value> ::= ["-"] {цифра} ["." цифра]

<DateTime_value> ::= рядок із кількістю секунд,
                     повернутий функцією
                     IntToStr(TimestampToTimeInt(...))
                     у форматі UTC

<field> ::= коректне ім’я поля Plant SCADA
            без урахування регістру
```

Дужки у виразах необов’язкові, але їх рекомендується використовувати для забезпечення правильного порядку обчислення. Якщо дужки використовуються, вони повинні бути парними.

Символ `*` є стандартним символом підстановки. Його можна використовувати лише один раз у межах одного рядкового значення.

Приклади коректних фільтрів:

```text
Tag=A
(Tag=A) OR (TAG=B)
(Tag=A) OR (TAG=B);Name=C
Time > IntToStr(TimestampToTimeInt(yesterday))
Tag=Dig*
Message='quoted sentence with blanks'
(((Tag=A) OR (TAG=B)) AND (category=1))
```

Примітка. Якщо фільтр занадто складний, наприклад містить надто багато умов або вкладених дужок, він буде очищений і не застосовуватиметься. При цьому на клієнті буде згенерована апаратна тривога `Too many alarms in filters`, а в журналі трасування з’явиться повідомлення про помилку.

Під час роботи з функціями фільтрації тривог спочатку потрібно відкрити сеанс за допомогою `AlmFilterOpen`.

Після цього в межах цього сеансу можна:

- переглядати частини фільтра за допомогою `AlmFilterFirst`, `AlmFilterNext` і `AlmFilterPrev`;
- змінювати фільтр за допомогою `AlmFilterSet`, `AlmFilterAppend` і `AlmFilterCommit`.

Сеанс залишається доступним, доки його не буде закрито функцією `AlmFilterClose`.

Для одного списку можна одночасно відкрити кілька сеансів. Якщо кілька сеансів змінюють один і той самий фільтр, активним буде результат останнього виклику `Commit`.