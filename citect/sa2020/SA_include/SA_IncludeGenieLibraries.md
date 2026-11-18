# SA_Include Genie Libraries

## Alarm Filter Genie Library              

The SA_Include system project includes the "sa_filter" library. It includes the following      Genies:   

- [Item Acknowledged Genie (HD1080)](https://localhost:28808/Plant SCADA/#showid/1206772)
- [Item Acknowledged Genie (UHD4K)](https://localhost:28808/Plant SCADA/#showid/1206773)
- [Item Base Genie](https://localhost:28808/Plant SCADA/#showid/1206774)
- [Item Priority Genie (HD1080)](https://localhost:28808/Plant SCADA/#showid/1206775)
- [Item Priority Genie (UHD4K)](https://localhost:28808/Plant SCADA/#showid/1206776)
- [Item Shelved Genie (HD1080)](https://localhost:28808/Plant SCADA/#showid/1206777)
- [Item Shelved Genie (UHD4K)](https://localhost:28808/Plant SCADA/#showid/1206778)
- [Item State Genie (HD1080)](https://localhost:28808/Plant SCADA/#showid/1206779)
- [Item State Genie (UHD4K)](https://localhost:28808/Plant SCADA/#showid/1206780)
- [Item Unacknowledged Genie (HD1080)](https://localhost:28808/Plant SCADA/#showid/1206781)
- [Item Unacknowledged Genie (UHD4K)](https://localhost:28808/Plant SCADA/#showid/1206782).         

### Item Base Genie

Genie `Item Base` використовується для створення власної кнопки фільтрації тривог. Він призначений для роботи зі стандартними сторінками тривог Situational Awareness. Докладніше про його використання див. у розділі «Додавання кнопки фільтрації тривог». У вікні `Genie Properties` доступні такі властивості:

- `AN` — автоматично згенерований унікальний ідентифікатор об'єкта Genie.
- `Name` — необов'язкове ім'я Genie. Використовується, якщо до нього потрібно звертатися з Cicode.

- Параметр `IsExclusion` визначає, чи буде результат фільтра виключати знайдені тривоги зі списку або, навпаки, залишати тільки їх.

| Значення | Опис                                                         |
| -------- | ------------------------------------------------------------ |
| `TRUE`   | Тривоги, що відповідають фільтру, виключаються зі списку. Наприклад, для виразу `CATEGORY<>3` тривоги категорії 3 не відображатимуться. |
| `FALSE`  | Відображаються лише тривоги, що відповідають фільтру. Наприклад, для виразу `CATEGORY=3` у списку залишаться тільки тривоги категорії 3. |

- Параметр `FilterExpr` містить вираз Cicode, який повертає ім'я фільтра.

Щоб використовувати стандартний фільтр сторінок Situational Awareness, слід вказати:

```cicode
AlarmPage_GetFilter("TopBar")
```

Якщо використовується власний фільтр, його потрібно створити у події `On Page Entry`, після чого в `FilterExpr` повертати його ім'я.

- Параметр `ValueExpr` містить вираз Cicode, який повертає рядок умови фільтра. Наприклад:

```text
"CATEGORY<>3"
```

- Параметр `Tooltip` задає текст підказки, що відображається при наведенні курсора на кнопку.

- Параметр `Label` задає текст, який буде показаний у рядку активних фільтрів після застосування цього фільтра. Наприклад:

```text
No Cat 3 Alarms
```