# AlarmPage

- AlarmPage_Init
- AlarmPage_InitUI
- AlarmPage_GetDefaultParameters
- AlarmPage_IsInitialised
- AlarmPage_Exit
- AlarmPage_FillResponse
- AlarmPage_History_IsHidden
- AlarmPage_SelectAlarmRecord
- AlarmPage_UpdateAlarmSOE
- AlamrPage_IsSOEHidden
- AlarmPage_OnDisplaySOEPeriods
- AlarmPage_GetFullPriv
- AlarmPage_AlarmListOnRightClick
- AlarmPage_GetEquipmentFilterBarColor
- AlarmPage_IsEquipmentFiltered
- AlarmPage_GetReferences
- AlarmPage_Ref_ToggleSelection
- AlarmPage_Ref_DisplayContextMenu



Описи перевірені безпосередньо за реалізацією `SA_Include\AlarmPage.ci` та збережені в [AlarmPage.md](C:/Users/OleksandrPupena/Documents/PlantScada/source-materials/03-cicode/ExampleSA/catalog/function-notes/AlarmPage.md).

- `AlarmPage_Init` — повністю ініціалізує сторінку тривог: списки тривог, SOE, Cause/Response, References, фільтри, шрифти та розміри.
- `AlarmPage_InitUI` — встановлює заголовок сторінки залежно від типу: активні, shelved або історичні тривоги.
- `AlarmPage_GetDefaultParameters` — створює map стандартних розмірів, шрифтів і форматів для HD1080 або UHD/4K.
- `AlarmPage_IsInitialised` — повертає ознаку завершення ініціалізації сторінки.
- `AlarmPage_Exit` — очищає фільтри, знищує списки та звільняє ресурси під час закриття сторінки.
- `AlarmPage_FillResponse` — завантажує Cause/Response вибраної тривоги; також запускає оновлення SOE при зміні вибору.
- `AlarmPage_History_IsHidden` — повертає `TRUE`, якщо не вибрано запис, для якого можна показати історію.
- `AlarmPage_SelectAlarmRecord` — скидає збережений ID вибраного запису, щоб примусово оновити Cause/Response.
- `AlarmPage_UpdateAlarmSOE` — асинхронно запускає оновлення SOE або історії вибраної тривоги.
- `AlamrPage_IsSOEHidden` — визначає, чи потрібно приховати список SOE. `Alamr` — справжня опечатка в назві функції у вихідному коді.
- `AlarmPage_OnDisplaySOEPeriods` — показує меню вибору періоду SOE: 1, 12, 24, 48 годин, 7 або 14 днів.
- `AlarmPage_GetFullPriv` — повертає `TRUE`, лише якщо користувач має всі привілеї від 1 до 8.
- `AlarmPage_AlarmListOnRightClick` — формує контекстне меню тривоги: Navigate, Find, Acknowledge, Shelve, Restore, Add Comment та Add Event. Доступність команд залежить від типу запису і прав користувача.
- `AlarmPage_GetEquipmentFilterBarColor` — повертає активний колір панелі equipment filter, якщо фільтрація ввімкнена.
- `AlarmPage_IsEquipmentFiltered` — повертає поточний стан equipment filter.
- `AlarmPage_GetReferences` — заповнює список equipment references, їхні checkbox-стани та перебудовує список при зміні вибраного обладнання.
- `AlarmPage_Ref_ToggleSelection` — перемикає checked state відповідного обладнання в Equipment Tree.
- `AlarmPage_Ref_DisplayContextMenu` — зарезервований callback правої кнопки для References; у цій версії функція порожня і нічого не виконує.



## AlarmPage_Init 

```
FUNCTION AlarmPage_Init(STRING sParameters, STRING sResolution, INT nType=0, STRING sFormat="")
```

Ця функція призначена для ініціалізації сторінки тривог.

Вона приймає чотири параметри. 

- Параметр `sParameters` містить асоціативний масив (map) з параметрами, які визначають розміри різних елементів сторінки. 
- Параметр `sResolution` задає роздільну здатність, для якої призначена сторінка тривог. 
- Параметр `nType` визначає, який тип тривог буде відображатися: активні, відкладені (Shelved) або архівні. 
- Параметр `sFormat` задає назву формату відображення списку тривог.  Цей формат визначає набір і порядок стовпців, що відображаються у списку. Для формату відображення можна задати власну назву за допомогою параметра `[Format]FormatName`.

Функція не повертає жодного значення (`Nil`).

Функція викликається з події сторінки `On Page Entry`. Асоціативний масив, переданий через параметр `sParameters`, автоматично закривається після закриття сторінки.

## AlarmPage_InitUI

Ініціалізація інтерфейсу сторінки тривог

Функція ініціалізує інтерфейс користувача сторінки тривог.

Параметр `nType` визначає, який тип тривог відображатиметься на сторінці: активні, відкладені (Shelved) або історичні.

Функція не повертає значення (`Nil`).