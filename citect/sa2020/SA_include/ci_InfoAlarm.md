# InfoAlarm

Містить усі функції, що використовуються панеллю `InfoAlarm`.

- InfoAlarm_IsUpdated
- InfoAlarm_EquipmentFilter
- InfoAlarm_EquipmentFilterTask
- InfoAlarm_ListIsHidden
- InfoAlarm_LeftClickCommand
- InfoAlarm_RightClickCommand

## Перевірка актуальності фільтра списку тривог

```
INT FUNCTION InfoAlarm_IsUpdated(STRING sEquipmentContext)
```

Функція перевіряє, чи відповідає поточний фільтр списку тривог вибраному обладнанню.

Інформація про обладнання, за яким зараз виконується фільтрація, зберігається у локальній рядковій змінній сторінки (`Page String`). У цій функції її значення порівнюється з переданим обладнанням.

Параметр `sEquipmentContext` містить ім'я вибраного обладнання.

Функція повертає `TRUE`, якщо список тривог уже відфільтрований для поточного вибраного обладнання.

## InfoAlarm_EquipmentFilter

Обгортка для фільтрації обладнання

```
FUNCTION InfoAlarm_EquipmentFilter(INT hAn, STRING sEquipmentContext)
```

Функція-обгортка викликає функції фільтрації обладнання для панелі `InfoAlarm`.

- Параметр `hAn` задає AN списку тривог.

- Параметр `sEquipmentContext` містить ім’я вибраного обладнання.