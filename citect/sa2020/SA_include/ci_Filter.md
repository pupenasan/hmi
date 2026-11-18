# Filter

- Filter_Exists
- Filter_Create
- Filter_Destroy
- Filter_NewItem
- Filter_AddItem
- Filter_RemoveItem
- Filter_GetItem
- Filter_GetItemCount
- Filter_Clear
- Filter_Contains
- Filter_GetProperty
- Filter_RegisterChanged
- Filter_CallChanged
- Filter_Debug

## Примітки та приклади роботи з фільтрами

Цей файл потрібно компілювати разом із файлом `FilterItem.ci`.

Під час задання callback-функції можна використовувати таку підстановку:

- `#Sender` — посилання на відправника події.

Нижче наведено приклад створення фільтра та додавання до нього елементів фільтрації:

```cicode
STRING pItem;
STRING pFilter = Filter_Create("", "@(Priority Filter)");

IF ("" <> pFilter) THEN
    pItem = Filter_NewItem(pFilter);

    IF ("" <> pItem) THEN
        FilterItem_Set(pFilter, pItem, "NOT P1", "PRIORITY<>1");
        Filter_AddItem(pFilter, pItem);
    END

    pItem = Filter_NewItem(pFilter);

    IF ("" <> pItem) THEN
        FilterItem_Set(pFilter, pItem, "NOT P3", "PRIORITY<>3");
        Filter_AddItem(pFilter, pItem);
    END
END
```

У цьому прикладі створюється фільтр `Priority Filter`, після чого до нього додаються два критерії: виключення тривог із пріоритетом 1 та виключення тривог із пріоритетом 3.

Перебір елементів фільтра можна виконати так:

```cicode
STRING sLabel;
STRING sValue;
INT nItem;
INT nCount = Filter_GetItemCount(pFilter);

FOR nItem = 1 TO nCount DO
    pItem = Filter_GetItem(pFilter, nItem);

    sLabel = FilterItem_GetProperty(
        pFilter,
        pItem,
        "Label"
    );

    sValue = FilterItem_GetProperty(
        pFilter,
        pItem,
        "Value"
    );
END
```

Для кожного елемента функція `FilterItem_GetProperty()` повертає його властивості. Для властивості `Label` очікуються значення на кшталт `NOT P1` або `NOT P3`, а для властивості `Value` — `PRIORITY<>1` або `PRIORITY<>3`.

Якщо посилання на елемент фільтра вже відоме, його властивості можна отримати без перебору всіх елементів:

```cicode
sLabel = FilterItem_GetProperty(pFilter, pItem, "Label");
sValue = FilterItem_GetProperty(pFilter, pItem, "Value");
```

Між фільтрами також можна створювати залежності. У наступному прикладі зміна одного фільтра призводить до очищення двох інших:

```cicode
STRING pFilterCat = Filter_Create("", "@(Category Filter)");
STRING pFilterState = Filter_Create("", "@(State Filter)");

Filter_RegisterChanged(
    pFilter,
    "Filter_Clear(^"" + pFilterCat + "^")"
);

Filter_RegisterChanged(
    pFilter,
    "Filter_Clear(^"" + pFilterState + "^")"
);

Filter_CallChanged(pFilter);
```

Виклик `Filter_CallChanged(pFilter)` запускає зареєстровані callback-функції:

```cicode
Filter_Clear(pFilterCat);
Filter_Clear(pFilterState);
```

## Filter_Create

Функція `Filter_Create` створює об’єкт фільтра із заданим ім’ям, міткою та типом оператора, який використовується для об’єднання елементів фільтра.

```cicode
STRING FUNCTION Filter_Create(
    STRING sFilterName,
    STRING sLabel,
    INT nOper = 0
)
```

- Параметр `sFilterName` задає ім’я фільтра. Воно має бути унікальним у межах процесу. Якщо передати порожній рядок, ім’я буде згенеровано автоматично.

- Параметр `sLabel` задає текстову мітку фільтра, яка використовується для його відображення на екрані.

- Параметр `nOper` визначає оператор, яким об’єднуються окремі елементи фільтра. Наразі значення `0` відповідає оператору `AND`. За замовчуванням використовується `0`.

Функція повертає ім’я створеного фільтра. Якщо створити фільтр не вдалося, повертається порожній рядок.

Реалізація:

```cicode
STRING FUNCTION Filter_Create(
    STRING sFilterName,
    STRING sLabel,
    INT nOper = 0
)
    STRING pFilter = MapGetNew(sFilterName);

    IF ("" <> pFilter) THEN
        MapValueSet(pFilter, l_sPropName_Label, sLabel);
        MapValueSet(pFilter, l_sPropName_Oper, nOper);
        MapValueSet(pFilter, l_sPropName_NewIndex, 0);
        MapGetNew(_Filter_GetCollection(pFilter));
    END

    RETURN pFilter;
END
```

## Filter_Exists

Функція `Filter_Exists` перевіряє, чи існує об’єкт фільтра.

```cicode
INT FUNCTION Filter_Exists(STRING pFilter)
```

- Параметр `pFilter` містить посилання на об’єкт фільтра.

Функція повертає `TRUE`, якщо об’єкт фільтра існує, або `FALSE`, якщо він не існує.

Якщо `pFilter` містить порожній рядок, функція одразу повертає `FALSE`. В іншому випадку існування об’єкта перевіряється функцією `MapExists()`.

```cicode
INT FUNCTION Filter_Exists(STRING pFilter)

    IF ("" = pFilter) THEN
        RETURN FALSE;
    END

    RETURN MapExists(pFilter);

END
```

## Filter_CallChanged

Виклик обробника зміни фільтра

Функція `Filter_CallChanged` викликає функцію, пов’язану з подією зміни фільтра.

```cicode
FUNCTION Filter_CallChanged(STRING pFilter)
```

Параметр `pFilter` містить посилання на об’єкт фільтра.

Функція не повертає значення (`Nil`).