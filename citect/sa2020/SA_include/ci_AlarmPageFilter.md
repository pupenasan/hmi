# AlarmPageFilter

- AlarmPage_GetFilter
- AlarmPage_GetFilterGroup
- AlarmPage_ChooseState
- _AlarmPage_InitFilter
- _AlarmPage_ExitFilter
- _AlarmPage_OnEqTreeFilterChanged
- _AlarmPage_GetFilterText



## AlarmPage_ChooseState

Функція `AlarmPage_ChooseState` відображає спадне меню, у якому користувач може вибрати стан тривог, що потрібно виключити зі списку тривог.

```cicode
FUNCTION AlarmPage_ChooseState(STRING sFilterName = "TopBar")
```

Параметр `sFilterName` задає ім'я об'єкта фільтра, який використовується на сторінці тривог. За замовчуванням використовується фільтр `TopBar`.

Функція не повертає значення (`Nil`).

## _AlarmPage_InitFilter

Внутрішня функція `_AlarmPage_InitFilter` ініціалізує фільтри, що використовуються на стандартних сторінках тривог.

```cicode
FUNCTION _AlarmPage_InitFilter()
```

Функція не має параметрів і не повертає значення (`Nil`).