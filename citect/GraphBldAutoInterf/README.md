# Graphics Builder Automation Interface

[Help](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Content/Graphics_Builder_Automation_Interface.html)

Plant SCADA Graphics Builder тепер пропонує підтримку «автоматизації», послуги OLE, яка дозволяє програмам демонструвати свою функціональність або контролювати функціональність інших програм на тому ж комп’ютері або в мережі. В результаті програми можна інтегрувати та автоматизувати за допомогою програмного коду.

Два ключових елемента автоматизації:

- Програми або програмні компоненти, які називаються **серверами автоматизації**, якими можна керувати, оскільки їхня функціональність була відкрита і стала доступною для інших програм. Прикладами серверів Microsoft Automation є програми Microsoft Office і Microsoft Project. Ці сервери автоматизації демонструють свою функціональність через об’єктні моделі.
- Інші програми або інструменти розробки, які називаються **контролерами автоматизації**, які можуть керувати серверами OLE Automation за допомогою програмного коду, одержуючи доступ до функціональних можливостей серверів Automation. Прикладами контролерів Microsoft Automation є Microsoft Visual Basic, Microsoft Visual C++ і Microsoft Visual Basic для додатків (який вбудований в Microsoft Access, Microsoft Excel і Microsoft Project).

*Автоматизація* — це загальний термін для процесу, за допомогою якого контролер автоматизації надсилає інструкції на сервер автоматизації (використовуючи функціональні можливості, надані сервером автоматизації), де вони запускаються. Інтерфейс автоматизації Plant SCADA Graphics Builder дозволяє Plant SCADA Graphics Builder діяти як сервер автоматизації, оскільки він надає багато функцій Graphics Builder.

Інтерфейс підтримує просту об’єктну модель: функції знаходяться на кореневому рівні. Імена структуровані та містять ідентифікатор групи та ім’я функції; наприклад, DrawLine, DrawRectangle, PositionAt, PositionRotate, ProjectSelect, ProjectUpgrade. Ці функції можна викликати з програми Visual Basic (VB).

**Примітка.** У середовищі розробки VB необхідно попередньо вибрати Type Library GraphicsBuilder. Для цього виберіть **References** у меню Проект у VB і перевірте Graphics Builder Type Library.

**Example** 

Наведений нижче приклад коду VB дозволяє вам створити нову сторінку Plant SCADA, розмістити Genie в певному місці, встановити один з його параметрів, намалювати лінію, а потім зберегти сторінку з назвою "TEST".

```vb
Dim GraphicsBuilder As IGraphicsBuilder2
Set GraphicsBuilder = New GraphicsBuilder.GraphicsBuilder
With GraphicsBuilder
	.Visible = True
	.PageNew "include", "standard", "normal", 0, True, True
    '.PageNew "SA_Include", "situational_awareness", "pagecontent", 7, False, True
	.LibraryObjectPlace "include", "motors", "motor_1_east", 0, True
	.PositionAt 300, 500
	.LibraryObjectPutProperty "Tag", "Test_Tag"
	.DrawLine 100, 100, 300, 300
	.AttributeLineColour = 120
	.PageSaveAs "Example", "TEST"
	.PageClose
	.Visible = False
End With
Set GraphicsBuilder = Nothing
```

### Error Handling

Функції, викликані з VB, викликають виняток у разі помилки. У наступній таблиці перелічено можливі помилки HRESULT, які можуть виникнути:

| C++ define   | Hex value | Hex codes in VB | Description                                                  |
| ------------ | --------- | --------------- | ------------------------------------------------------------ |
| S_OK         | 0         | No exception    | Successful execution                                         |
| E_INVALIDARG | 80070057  | 5               | One or more arguments are out of range                       |
| E_HANDLE     | 80070006  | 80070006        | No active object (page or graphical object)                  |
| E_POINTER    | 80004003  | 80004003        | Missing or broken link encountered                           |
| E_ABORT      | 80000007  | 11F             | Enumeration terminated or function manually canceled (for example ProjectUpdate) |
| E_FAIL       | 80004005  | 80004005        | Every other error                                            |

Для обробки коду помилки можна використовувати наступний код VB:

```vb
On Error Resume Next
Err.Clear
GraphicsBuilder.LibObjectName Project, File, Page, Type
If Err.Number <> 0 Then
	Debug.Print "Error occurred in LibObjectName"
End If
```

Зверніть увагу на наступні моменти:

- VB встановлює змінну Err тільки в помилковому випадку. Він не буде встановлений на 0, якщо функція виконана успішно.
- Коли VB обробляє виняток, він ігнорує параметри функцій. Отже, коли функція, як ProjectNext, не вдається, повертається рядок є невизначеним, а не порожнім рядком.

Функції в групах [Page Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Page_Functionsb.html), [Options Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Options_Functions.html), [Object Drawing and Property Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Object_Drawing_and_Property_Functions.html), [Text Property Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Text_Property_Functions.html) та окремі функції[LibSelectionHooksEnabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/LibSelectionHooksEnabled.html), [SelectionEventEnabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/SelectionEventEnabled.html), [BrokenLinkCancelEnabled](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/BrokenLinkCancelEnabled.html) розглядаються як змінні у VB.

Викликаючи ці функції з C++, вам потрібно використовувати префікс "put_" або "get_", наприклад, "put_Visible(TRUE)", "get_Visible(bValue)", щоб встановити або отримати значення, за винятком випадків, коли атрибут читається -тільки. У цьому випадку функція така сама в C++; наприклад, PageName.

Щоб оцінити правильну назву функції для C++, зверніться до бібліотеки типів CTDRAW32.TLB, яку можна знайти в каталозі BIN Plant SCADA. Ви можете використовувати засіб Microsoft Visual Studio Tool OLE / COM Object Viewer (виберіть меню File | View Typelib...), щоб переглянути бібліотеку типів.

### Automation Events

Конструктор графіки також надає сповіщення про події на основі подій, які клієнт автоматизації може перехопити та відповідно реагувати на них. У наведеному нижче прикладі створюється форма, створюється об’єкт автоматизації конструктора графіки з можливістю подій і виконує дії з двома подіями, які може генерувати конструктор графіки, вставляючи символ і зберігаючи сторінку.

To enable this:

- The Graphics Builder object needs to be declared "WithEvents"
- The event handler subroutine needs to have the correct name and signature. Note how the event handler function names are gb, the graphics builder object, followed by _<eventName> e.g gb_PasteSymbol. This is consistent with standard Visual Basic event handling subroutine naming.

For details, see the individual event subroutine description. 

Щоб увімкнути це:

- Об’єкт Graphics Builder має бути оголошений «WithEvents»
- Підпрограма обробника подій повинна мати правильне ім'я та підпис. Зверніть увагу на те, що імена функцій обробника подій – `gb`, об’єкт графічного побудовника, за яким слідує `_<eventName>`, наприклад, `gb_PasteSymbol`. Це узгоджується зі стандартним іменуванням підпрограм обробки подій Visual Basic.

Додаткову інформацію див. в описі підпрограми окремих подій.

```vb
Private WithEvents gb As GraphicsBuilder.GraphicsBuilder
Public Sub Form_Load()
    	Set gb = New GraphicsBuilder.GraphicsBuilder
    	gb.LibrarySelectionHooksEnabled = True
    	gb.Visible = True
End Sub

Public Sub gb_PasteSymbol()
    	MsgBox ("PasteSymbol")
End Sub

Private Sub gb_PageSaved(ByVal Project As String, ByVal Page As String,
	 ByVal LastPage As Boolean)
    	MsgBox "PageSaved: " + Project + "." + Page + "--"
End Sub         
```

### Function Categories

У цій таблиці перелічено функції Plant SCADA, які доступні через інтерфейс автоматизації Graphics Builder, згруповані в такі категорії:

|                                                              |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Alarm Indicator Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Alarm_Indicator_Functions.html) | Дозволяє означити вигляд індикатора тривоги, прикріпленого до джина. Пов’язано з частиною вкладки Alarm  Indicator Properties Tab діалогового вікна Genie Properties dialog |
| [Arrange and Position Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Arrange_and_Position_Functions.html) | Дозволяє змінювати положення вибраного об’єкта в трьох вимірах (порядок X, Y та Z). |
| [Composite Genie Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Functions.htm) | Дозволяє розмістити або знайти Composite Genies.             |
| [Events Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Events_Functions.html) | Дозволяє використовувати механізм автоматизації диспетчеризації для запуску подій у конкретних ситуаціях. |
| [Specific Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Specific_Functions.html) | Наразі включає лише функцію Visible.                         |
| [Dynamic Properties Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Dynamic_Properties_Functions.html) | Дозволяє змінювати динамічні властивості графічних об’єктів у вашому проекті (переміщення, масштабування, обертання, повзунки, динамічна заливка кольором). |
| [Library Object Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Library_Object_Functions.html) | Дозволяє використовувати і маніпулювати об’єктами, що зберігаються в бібліотеках у вашому проекті. Сюди входять такі об’єкти, як джини, суперджини, символи тощо. |
| [Miscellaneous Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Miscellaneous_Functionsc.html) | Використовується для спеціальної взаємодії з Graphics Builder, наприклад, зовнішню дію перетягування можна виконати, запитуючи активний дескриптор вікна. |
| [Object Drawing and Property Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Object_Drawing_and_Property_Functions.html) | Дозволяє малювати об’єкти та маніпулювати властивостями об’єктів. |
| [Options Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Options_Functions.html) | Пов’язано з параметрами, знайденими в меню Інструменти Graphics Builder. |
| [Page Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Page_Functionsb.html) | Дозволяє маніпулювати сторінками у вашому проекті (наприклад, відкривати, закривати, зберігати, видаляти) та вибирати об’єкти на цих сторінках. Сюди входять шаблони, символи, джини, суперджини. |
| [Page Properties Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Page_Properties_Functions.html) | Дозволяє маніпулювати властивостями сторінок у вашому проекті. |
| [Project Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Project_Functions.html) | Ці функції діють на рівні проекту. Деякі фактично ініційовані в Plant SCADA Studio. |
| [Text Property Functions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Text_Property_Functions.html) | Дозволяє читати та змінювати властивості текстових об’єктів у вашому проекті. |

​            