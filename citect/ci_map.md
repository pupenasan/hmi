# Map Functions

Функції карти (Map functions) дозволяють асоціювати значення з ключами (keys) на карті.

Оскільки дескриптор карти (або ім’я карти) є рядком, він може зберігатися або як ключ, або як значення в іншій карті, тому карти можна використовувати для створення довільно складних структур даних.

Розглядаючи карту як еквівалентну «екземпляру» «об’єкта» на «об’єктно-орієнтованій» мові, можна досягти спрощеного об’єктно-орієнтованого стилю програмування. Це можна зробити, передавши назву карти як параметр до функцій «об’єкта».

Ключі на карті чутливі до регістру та впорядковані в алфавітному порядку, як можна спостерігати, послідовно виявляючи кожен ключ на карті (за допомогою MapKeyFirst і MapKeyNext). Алфавітне впорядкування не є лексикографічним і визначає лише повторюваний порядок для даного набору ключів.

Following are Map functions:

|                                                              |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [MapOpen](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapOpen.html) | Create a new or open an existing map.                        |
| [MapClear](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapClear.html) | Clear all entries in a map.                                  |
| [MapClose](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapClose.html) | Deletes a previously created map.                            |
| [MapExists](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapExists.html) | Check if the map exists using a returned error code.         |
| [MapKeyCount](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapKeyCount.html) | Retrieves the number of keys in a map.                       |
| [MapKeyDelete](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapKeyDelete.html) | Delete a  key and its value from a map.                      |
| [MapKeyExists](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapKeyExists.html) | Check if a  key exists in a map.                             |
| [MapKeyFirst](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapKeyFirst.html) | Retrieves the first  key in a maps so that all the keys in a map can be discovered. |
| [MapKeyNext](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapKeyNext.html) | Retrieves the next key after the supplied key in a map so that all the keys in a map can be discovered. |
| [MapValueGet](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapValueGet.html) | Retrieves the value from a key in a map.                     |
| [MapValueSet](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapValueSet.html) | Sets the value of a key in a map.                            |
| [MapValueSetQuality](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/MapValueSetQuality.html) | Sets the quality of a value in a map.                        |

## MapOpen

Use this function to create a new map or to open an existing map. 

**Note:** There is no limit on the  number of maps or map items you can create. However, a large number of  maps may require a lot of memory. It is recommended that maps created in custom Cicode are destroyed using MapClose when they are no longer  needed. 

Syntax

```
STRING **MapOpen**(STRING *sMapName*, INT *nOpenMode*, STRING *sCloseCallback*)
```

*sMapName:* 

Name of the map to create or  open. The default name is an empty string. If name is empty, it will  generate an available random name.

*nOpenMode:* 

Indicates the open or create mode of the map. Modes include:

Mode 0 - Create a new map. If a map with the same name exists an “Out of handles” error (271) will be raised.

Mode 1 - Opens an existing map. if there is no map with that name a “Record not found” error (536) will be raised.

Mode 2 – Open an existing map , or creates a new map if the map name does not exist. The error codes  from modes 0 and 1 can occur.

*sCloseCallback:* 

The function to call when this instance is closed.

Return Value

Name of map if successful, otherwise an empty string will be returned.

If the map name is empty an “Invalid argument” error (274) will be raised.

If the open mode is less than 0 or greater than 2, an “Invalid argument” error (274) will be raised.

If an empty map name is supplied along with open mode 1, an “Invalid argument” error (274) will be raised.

Example

```c
! Demonstrate MapOpen.
STRING sMapName = MapOpen();
! sMapName is a randomly generated text that uniquely identifies the map
INT iMapCloseResult = MapClose(sMapName);
! The map that is identified by sMapName is now closed and unavailable
 
! Demonstrate MapOpen with a close callback
STRING sMapName = MapOpen(“”, 0, “MyCloseCallback”);
! sMapName is a randomly generated text that uniquely identifies the map
INT iMapCloseResult = MapClose(sMapName);
! The map that is identified by sMapName is now closed and unavailable
! The function MyCloseCallback is called, but it may or may not be
! completed before the MapClose function returns.

! This is a MapClose callback function
! The callback must take one string argument which is the name of the
! map that is being closed.
FUNCTION MyCloseCallback(STRING sMapName)
! sMapName is a valid map for the duration of the callback, at the
! exit of the callback the memory is released and any subsequent
! use of the map will result in an error.
END		
```

## MapValueSet

Use this function to set a value of a map key. 

```
INT **MapValueSet**(STRING *sMapName*, STRING *sKeyName*, VARIANT *Value* INT *nSetMode*)
```

*sMapName:* Name of the map to create or open. 

*sKeyName:* Name of the key to set.

*Value:* Name of the value to be set

*nSetMode:* 

- 0 - Create a new property
- 1- Override an existing property
- 2 - Assign the value whether the key already exists or not. This is the default mode.

Return Value

- If the value is set correctly, the result is “No Error” (0), otherwise an error code is returned.
- If the map name or key name is empty, an “Invalid argument” error (274) will be raised and returned.
- If the map does not exist a “Record not found” error (536) will be returned.
- If the key does not exist and set mode is 1, a “Record not found” error (536) will be returned.
- If the key exists and set mode is 0, an “Out of handles” error (271) will be returned.

Example

```c
! Demonstrate MapValueSet.
STRING sMapName = MapOpen();
! sMapName is a randomly generated text that uniquely identifies the map
INT iMapValueSetResult = MapValueSet(sMapName, “SomeKey”, “SomeValue”);
STRING sMapValueGetResult = MapValueGet(sMapName, “SomeKey”);
! sMapValueGetResult will be set to “SomeValue”
INT iMapCloseResult = MapClose(sMapName);
! The map that is identified by sMapName is now closed and unavailable		
```