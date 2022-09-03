[Проект Situational Awareness](../README.md) -> [Situational Awareness Library](readme.md)

# CiCode Trend.ci

## SATrend_LoadItems

```pascal
INT FUNCTION SATrend_LoadItems(STRING sANName, STRING sTrendSymbol, STRING sEquip, STRING sPrefix = "", STRING sItem = "", STRING sSpan = "")
```

Ця функція використовується для ініціалізації перегляду трендів. ЇЇ можна викликати з виразу видимості графічного об’єкта, який буде приховано після успішної ініціалізації.

- ANName: ім'я графічного об'єкта, куди буде відобаражтися тренд
- TrendSymbol: символ тренда, куди буде відображатися тренд
- Prefix: 
- Equip: обладнання для використання для тегів трендів
- Item: (необов'язково) конкретна назва елемента, яка буде використовуватися для пера тренда. Якщо не вказано, пера будуть додані з перших 4 аналогових елементів для обладнання
- Span: проміжок часу за замовчуванням для перегляду трендів, зазначений як HH:MM:SS

## SATrend_UpdateSpan

INT FUNCTION SATrend_UpdateSpan(STRING sANName, STRING sTrendANName)

## SATrend_SelectPen

FUNCTION SATrend_SelectPen(STRING sANName, INT nPen)

## _SATrend_LoadTask

Функція для внутрішнього використання.

```
FUNCTION _SATrend_LoadTask()
```



## _SATrend_UpdateScale

INT FUNCTION _SATrend_UpdateScale(INT nAN, STRING sEquip, STRING sPrefix, STRING sItem)

## _SATrend_GetTrendTag

STRING FUNCTION _SATrend_GetTrendTag(STRING sCluster, STRING sEquip, STRING sItem)

## _SATrend_SetPen

Функція для внутрішнього використання.

```pascal
FUNCTION _SATrend_SetPen(STRING sTrendSymbol, INT nAN, INT nPen, STRING sCluster, STRING sTrend, STRING sSpan)
	TrnNew(nAN, sTrendSymbol, "", "", "", "", "", "", "", "", sCluster); 
	SleepMS(10);
	TrnSetPen(nAN, nPen, sTrend);
	TrnSetCursorPos(nAN, 0);
		
	IF (StrLength(sSpan) > 0) THEN
		TrnSetSpan(nAN, StrToTime(sSpan));
	END
```



## _SATrend_BrowsePens

FUNCTION _SATrend_BrowsePens(STRING sTrendSymbol, INT nAN, STRING sCluster, STRING sEquip, STRING sSpan)

## _SATrend_GetEquipmentCluster

STRING FUNCTION _SATrend_GetEquipmentCluster(STRING sEquip)



