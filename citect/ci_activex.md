## ActiveX Functions

Об’єкти ActiveX не підтримуються в 64-розрядних процесах, таких як  alarm server, що працює в режимі розширеної пам’яті. Якщо виклик функції ActiveX відбувається з 64-розрядного процесу, буде повернуто код помилки, буде згенеровано hardware alarm, і потік Cicode зупиниться.
Інформацію про методи, які можна використовувати для розширення Citect SCADA, які не потребують ActiveX, див. у розділі Extensibility|Componentsв головній довідці Citect SCADA.

Нижче наведено функції, що стосуються об’єктів ActiveX:

|                                |                                                              |
| ------------------------------ | ------------------------------------------------------------ |
| _ObjectCallMethod-             | Calls a specific method for an ActiveX object.               |
| _ObjectGetProperty             | Retrieves a specific property of an ActiveX object.          |
| _ObjectSetProperty             | Sets a specific property of an ActiveX object.               |
| AnByName                       | Retrieves the animation point number of an ActiveX object.   |
| CreateControlObject            | Creates a new instance of an ActiveX object.                 |
| CreateObject                   | Creates the automation component of an ActiveX object.       |
| ObjectAssociateEvents          | Allows you to change the ActiveX object's event class.       |
| ObjectAssociatePropertyWithTag | Establishes an association between a variable tag and an ActiveX object property. |
| ObjectByName                   | Retrieves an ActiveX object.                                 |
| ObjectHasInterface             | Queries the ActiveX component to determine if its specific interface is supported. |
| ObjectIsValid                  | Determines if the given handle for an object is valid.       |
| ObjectToStr                    | Converts an object handle to a string.                       |

## CreateObject

Creates a new instance of an ActiveX object. If you use this function to create an ActiveX object, it will have no  visual component (only the automation component will be created).

If you assign an object created with the  CreateObject() function to a local variable, that object will remain in  existence until the variable it is assigned to goes out of scope. This  means that such an object will only be released when the Cicode function that created it ends.

If you assign an object created with the  CreateObject() function to a module or global scope variable, then that  object will remain in existence until the variable either has another  object assigned or is set to NullObject, *provided the CreateObject() call is not made within a loop.*

Objects created by calls to CreateObject()  within WHILE or FOR loops are only released on termination of the Cicode function in which they are created, regardless of the scope of the  variable to which the object is assigned. The use of CreateObject()  within a loop may therefore result in the exhaustion of system  resources, and is not generally recommended unless performed as shown in the examples below.

**Note:** ActiveX objects are not supported  on a 64-bit process, such as an alarm server operating in Extended  Memory mode. If a call to this function occurs from a 64-bit process, an error code will be returned, a hardware alarm will be raised and the  Cicode thread will stop. 
For information regarding methods you can use to extend Citect SCADA that do not require ActiveX, see the topic *Extending* *Citect SCADA* *with External Libraries* in the main Citect SCADA help. 

Do not use the CreateObject() function within a loop except in strict accordance with the following instructions. **Failure to follow these instructions can result in death, serious injury, or equipment damage.** 

**CreateObject**(*sClass*)

`sClass:` The class of the object. You can use the object's human  readable name, its program ID, or its GUID. If the class does  not exist, the function will return an error.

For example:

- "Calendar Control 8.0" - human readable name
- "MSCAL.Calendar.7" - Program ID
- "{8E27C92B-1264-101C-8A2F-040224009C02}" - GUID

`Return Value` The newly created object, if successful, otherwise an [error](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/Cicode_Errors.html) is generated.

The following examples show correct techniques for calling CreateObject() within a loop.

```c
/* In the example below, the variable objTest is local. Resources 
associated with calls to ProcessObject() will be released each 
time that function ends. */
FUNCTION Forever()
    WHILE 1 DO
ProcessObject();
Sleep(1);
    END
END
FUNCTION ProcessObject()
    .OBJECT objTest;
    objTest=CreateObject("MyObject");
    - do something
END
/* In the example below, the variable objTest is global. Resources 
associated with calls to ProcessObject() will be released when 
objTest is set to NullObject. */
FUNCTION Forever()
    WHILE 1 DO
ProcessObject();
Sleep(1);
    END
END
FUNCTION ProcessObject()
    objTest=CreateObject("MyObject");
    - do something
    objTest=NullObject;
END
```

## ObjectByName

Retrieves an ActiveX  object. This is useful when you know the object by name only (this will often be the case for objects created during configuration, rather than  those created at runtime using a Cicode function).

Syntax

**ObjectByName**(*STRING Name*)

*Name:* The name used to access the  object, as specified when creating it in Cicode. For objects created in  the Graphics Builder, the object name is set in the Access  (Identification) tab, and defaults to "AN" followed by its AN number,  for example, "AN35". The Name argument should be enclosed in quotes "".

 "".

Return Value - The requested object, if successful, otherwise an error is generated.

## CreateControlObject

Creates a new instance of an ActiveX object.

An object created using this function remains  in existence until the page is closed or the associated Cicode Object is deleted. This function does not require an existing animation point.  When the object is created, an animation point is created internally.  This animation point is freed when the object is destroyed.

**Note:** ActiveX objects are not supported  on a 64-bit process, such as an alarm server operating in Extended  Memory mode. If a call to this function occurs from a 64-bit process, an error code will be returned, a hardware alarm will be raised and the Cicode thread will stop. 
For information regarding methods you can use to extend Citect SCADA that do not require ActiveX, see the topic *Extending* *Citect SCADA* *with External Libraries* in the main Citect SCADA help. 

**CreateControlObject**(*sClass*, *sName*, *x1*, *y1*, *x2*, *y2*, *sEventClass*)

*sClass:*  The class of the object. You can use the object's human  readable name, its program ID, or its GUID. If the class does  not exist, the function will return an error message.

For example:

- "Calendar Control 8.0" - human readable name
- "MSCAL.Calendar.7" - Program ID
- "{8E27C92B-1264-101C-8A2F-040224009C02}" - GUID

*sName:*  The name for the object in the form of "AN" followed by its  AN number, for example, "AN35". This name is used to access the  object.

*x1:*The x coordinate of the object's top left hand corner as it will  appear in your Citect SCADA window.

*y1:*The y coordinate of the object's top left hand corner as it will  appear in your Citect SCADA window.

*x2:*The x coordinate of the object's bottom right hand corner as it  will appear in your Citect SCADA window.

*y2:*The y coordinate of the object's bottom right hand corner as  it will appear in your Citect SCADA window.

*sEventClass:*The string you would like to use as the event class for the  object.

Return Value The newly created object, if successful, otherwise an [error](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/Cicode_Errors.html) is generated.

```c
// This function creates a single instance of the calendar control 
at the designated location with an object name of "CalendarEvent" 
and an event class of "CalendarEvent"//
FUNCTION
CreateCalendar()
	OBJECT Calendar;
	STRING sCalendarClass;
	STRING sEventClass;
	STRING sObjectName;
	sCalendarClass = "MSCal.Calendar.7";
	sEventClass = "CalendarEvent";
	sObjectName = "MyCalendar";
	Calendar = CreateControlObject(sCalendarClass, sObjectName, 16, 
	100, 300, 340, sEventClass);
END
// This function shows how to change the title font of the 
calendar//
FUNCTION
CalendarSetFont(STRING sFont)
	OBJECT Font;
	OBJECT Calendar;
	Calendar = ObjectByName("MyCalendar");
	Font = _ObjectGetProperty(Calendar, "TitleFont");
	_ObjectSetProperty(Font, "Name", sFont);
END
// This function shows how to change the background color of the 
calendar//
FUNCTION
CalendarSetColor(INT nRed, INT nGreen, INT nBlue)
	OBJECT Calendar;
	Calendar = ObjectByName("MyCalendar");
	_ObjectSetProperty(Calendar, "BackColor", 
	PackedRGB(nRed,nGreen,nBlue));
END
// This function shows how to call the NextDay method of the 
calendar//
FUNCTION
CalendarNextDay()
	OBJECT	Calendar;
	Calendar = ObjectByName("MyCalendar");
	_ObjectCallMethod(Calendar, "NextDay");
END
// This function shows you how to write a mouse click event 
handler for the calendar//
FUNCTION
CalendarEvent_Click(OBJECT This)
	INT nDay;
	INT nMonth;
	INT nYear;
	nDay = _ObjectGetProperty(This, "Day");
	nMonth = _ObjectGetProperty(This, "Month");
	nYear = _ObjectGetProperty(This, "Year");
	...
	Your code goes here...
	...
END
```

## AnByName

Retrieves the animation point number of an ActiveX object.   

**AnByName**(*sName*)

*sName:*         The name given to the ActiveX  object. This name is visible in the "Identification" tab of the ActiveX  control in the Graphics Builder and is used to access the  object.

If the Animation number for an object is 35 and you renamed the object to fred use AnByName("Fred");		which will return  35.

If you left the name of the object as the default use			AnByName("AN35");		which will return 35. 

Return Value - The animation point number of the object - if successful, otherwise an error code is returned.

## ObjectByName

Retrieves an ActiveX  object. This is useful when you know the object by name only (this will  often be the case for objects created during configuration, rather than  those created at runtime using a Cicode function).

**ObjectByName**(*STRING Name*)

*Name:*  The name used to access the  object, as specified when creating it in Cicode. For objects created in  the Graphics Builder, the object name is set in the Access  (Identification) tab, and defaults to "AN" followed by its AN number,  for example, "AN35". The Name argument should be enclosed in quotes "".

 "".

Return Value - The requested object, if successful, otherwise an error is generated.

## _ObjectCallMethod

Calls a specific  method for an ActiveX object. (See the documentation for your ActiveX  object for details on methods and properties.)

**Note:** The parameter list passed to the control can only have Cicode variables or variable tags; it cannot  use values returned directly from a function because an ActiveX control  may modify parameters passed to it.

For example:

```c
//Calculate a value and pass to ActiveX control
_ObjectCallMethod(hControl, "DoSomething", CalcValue());
```

is not allowed because the return value of a function cannot be modified. The following should be used instead:

```c
INT nMyValue;
//Calculate Value
nMyValue = CalcValue();
//Pass Value to ActiveX control
_ObjectCallMethod(hControl, "DoSomething", nMyValue);
```

**_ObjectCallMethod**(*hObject*, *sMethod*, *vParameters*)

*hObject:* The handle for the object (as returned by the  ObjectByName() function).

*sMethod:* The name of the method.

*vParameters:* A variable length parameter list of method arguments. The  variables will be passed however you enter them, and will  then be coerced into appropriate automation types. Likewise,  any values modified by the automation call will be written  back - with appropriate coercion - into the passed Cicode  variable.

Return Value - The return value from the method - if successful, otherwise an [error code](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/Cicode_and_General_Errors.html) is returned.

## _ObjectGetProperty

Gets a specific property of an ActiveX object.

**_ObjectGetProperty**(*hObject*, *sProperty*)

*hObject:*  The handle for the object (as returned by the  ObjectByName() function).

*sProperty:* The name of the property you want to get.

Return Value - The value of the property - if successful, otherwise [error code](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/Cicode_and_General_Errors.html) is returned.

## _ObjectSetProperty

Sets a specific property of an ActiveX object.

**_ObjectSetProperty**(*hObject*, *sProperty*, *vValue*)

*hObject:*  The handle for the object (as returned by the  ObjectByName() function).

*sProperty:*  The name of the property you want to set.

*vValue:* The value to which the property will be set. This value can be  of any data type. Appropriate coercion will take place when  creating the equivalent automation parameter.

## FAQ 

<https://www.se.com/ru/ru/faqs/FA146303/>

Как в Citect SCADA (Vijeo Citect) реализовать выпадающий список ComboBox?

Выпадающий список ComboBox реализуется с помощью компонента ActiveX и Cicode. На  страницу куда добавляется выпадающий список, необходимо вставить ActiveX компонент Microsoft Forms 2.0 ComboBox. В свойствах вставленного  ComboBox на вкладке Appearance – Tag Association необходимо свойство  Text связать с текстовой переменной, в которую будет записываться  выбранное значение.

Затем необходимо создать функцию Cicode, которая будет определять позиции выпадающего списка. Пример функции:

```c
FUNCTION MyPageLoad()
   OBJECT oComboBox1
   INT iIndex
   oComboBox1 = ObjectByName("AN502")
   _ObjectCallMethod(oComboBox1,"Clear")
   _ObjectCallMethod(oComboBox1,"AddItem","A",iIndex)
   iIndex = iIndex + 1
   _ObjectCallMethod(oComboBox1,"AddItem","B",iIndex)
   iIndex = iIndex + 1
   _ObjectCallMethod(oComboBox1,"AddItem","C",iIndex)
END
```

Здесь вместо AN502 необходимо подставить значение поля Объект ТА  (Animation number) вставленного ComboBox. A, B, C – значения, которые  будут присвоены элементам списка. iIndex – порядковый номер элемента в  списке.

Эту функцию необходимо вызывать при заходе на страницу с ComboBox.  Для этого ее нужно добавить в пункт «При показе страницы» (On page  shown) меню «События» (Events) в свойствах страницы.

Полученный ComboBox при использовании будет предлагать выбор из  пунктов A, B, C и записывать выбранное значение в переменную Text.

Опубликовано:15.06.2012Дата последнего изменения:30.09.2021

## Приклади

