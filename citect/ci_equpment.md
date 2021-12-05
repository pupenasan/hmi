# Equipmet Cicode Functions

## Equipment Database Functions

Following are functions relating to the equipment database.

| Функція                    | опис                                                         |
| -------------------------- | ------------------------------------------------------------ |
| EquipBrowseClose           | Closes an equipment database browse session.                 |
| EquipBrowseFirst           | Gets the first equipment database entry in the browse session. |
| EquipBrowseGetField        | Gets the field indicated by the cursor position in the browse session. |
| EquipBrowseNext            | Gets the next equipment database entry in the browse session. |
| EquipBrowseNumRecords      | Returns the number of records in the current browse session. |
| EquipBrowseOpen            | Opens an equipment database browse session.                  |
| EquipBrowsePrev            | Gets the previous equipment database entry in the browse session. |
| EquipCheckUpdate           | Checks if the equipment database file has been updated, and provides the facility to reload it. |
| EquipGetParameter          | Reads a runtime parameter of an equipment database record from the EQPARAM.RDB database file. |
| EquipGetProperty           | Reads a property of an equipment database record from the EQUIP.DBF file. |
| EquipRefBrowseClose        | Closes an equipment database browse session.                 |
| EquipRefBrowseFirst        | Gets the first equipment database entry in the browse session. |
| EquipRefBrowseGetField     | Gets the field indicated by the cursor position in the browse session. |
| EquipRefBrowseNext         | Gets the next equipment database entry in the browse session. |
| EquipRefBrowseNumRecords   | Returns the number of records in the current browse session. |
| EquipRefBrowseOpen         | Opens an equipment database browse session.                  |
| EquipRefBrowsePrev         | Gets the previous equipment database entry in the browse session. |
| EquipSetProperty           | Sets the property of an item of equipment.                   |
| EquipStateBrowseClose      | Terminates a browsing session and cleans up the resources used by the session. |
| EquipStateBrowseFirst      | Places the data browse cursor at the first record.           |
| EquipStateBrowseGetField   | Returns the value of the particular field in a record to which the data browse cursor is currently referencing. |
| EquipStateBrowseNext       | Places the data browse cursor at the next available record.  |
| EquipStateBrowseNumRecords | Returns the number of records that match the current filter criteria. |
| EquipStateBrowseOpen       | Initiates a new session for browsing the equipment states configured. |
| EquipStateBrowsePrev       | Places the data browse cursor at the previous record.        |

### EquipGetProperty

This function reads a property of an equipment database record from the EQUIP.RDB database file.

This function is a blocking function. It blocks the calling Cicode task until the operation is complete.

Syntax

```c
STRING EquipGetProperty(STRING Name, STRING Field, INT Mode, STRING Cluster)
```

*Name:* The name of the equipment from which to get information. The name of the equipment can be prefixed by the name of the cluster that is "ClusterName.Equipment".

*Field:* The field to read. Supported fields are:

Name, Cluster, Type, Area,  Location, IODevice, Page, Parent, Composite, Help, Comment, Alias,  Content, Hidden, Custom1, Custom2, Custom3, Custom4, Custom5, Custom6,  Custom7, Custom8. Defstate, Scheduled

- *Name* - The name of the equipment (254 characters).

- *Cluster* - The cluster to which the equipment belongs (16 characters).

- *Type* - The equipment-specific type of device (254 characters).

- *Area* - Area number (integer) (16 characters).

- *Location* - Equipment specific field (254 characters).

- *IODevice* - I/O Device name(s) (254 characters).

- *Page* - Page name (254 characters).

- *Parent* - The name of the parent equipment derived from the name of the equipment (maximum 254 characters).

- *Help* - Help context (254 characters).

- *Comment* - User comment (254 characters).

- *Custom1..8* - User definable fields (254 characters each).

- *Composite* - The equipment specific composite name (maximum 254 characters).

- *Defstate* - The default state.

- *Scheduled* - Specifies if the equipment participates in a schedule.

- *Alias*- Meaningful name of equipment (254 characters).

- *Content* - Workspace content associated with equipment instance.

- *Hidden* - Hide from equipment tree at runtime.

Runtime fields (Sate + Mode):

- *MODE* - (the current mode of the equipment) 0 - automatic; 1- Manual Inherited; 2- Manual.

- *DRMODE* - (the current DR mode level  for the equipment). The value will be a positive integer to represent  the current DR level or zero if inactive.

- *STATE* - (the current state of the  equipment. Although you can only set state for equipment in Override  mode, it is still possible to get state for equipment in normal and  inherited override mode.)

*Mode:*

*0* (Block - values are retrieved from the report server, the value will also be stored in local memory cache)

*1* (Cache – values are first retrieved from local memory cache, if the property is missing from the memory  cache, a request will be sent to the report server and the result will  then be cached. If the property is missing from the memory cache or if a previous request is in progress, an empty string will be returned.)

*2* (Local - values are retrieved from  the local RDB, an error will be returned when trying to get the  scheduler engine field in local mode)

*3* (CacheThenLocal – values are first  retrieved from local memory cache, if the property is missing from the  memory cache, a request will be sent to the report server and the result will then be cached. If the property is missing from the memory cache  or if a previous request is in progress, the local RDB will be accessed  to retrieve the property value.)

**Note**: Mode 1 and 3 will access the  report server at least once, there will be a once off performance  penalty on the report server, operating in this mode will always  guarantee equipment properties being the latest. Mode 2 will be the  fastest but cannot guarantee equipment been up-to-date [See Client Side  Online Changes]. Mode 0 will be the slowest as each request is sent  across the wire and the function will block until the report server  responds.

*Cluster* - The name of the cluster (optional for a single cluster system)

Return Value - The value of the specified field as a string.  An empty string may or may not be an indication that an error has been  detected. The last error should be checked in this instance to determine if an error has actually occurred.

### EquipSetProperty

The EquipSetProperty function sets the property of an item of equipment.  This function is a blocking function. It blocks the calling Cicode task until the operation is complete.

Syntax

```c
INT EquipSetProperty(STRING Name, STRING Field, STRING Value, STRING Cluster)
```

*Name:* The name of the equipment.

*field:* Only properties coming from the scheduler engine can be set:

- MODE: (the current mode of the equipment)

- STATE: (the current state of the equipment. The state only can be set for equipment in "Override" mode)

- DRMODE: (the DR mode of the equipment)

*Value:* The value to be set:

- MODE: 0, automatic;  2 Manual

- STATE: Any state configured in the system for this equipment, also the mode set the mode to Manual  otherwise an error will be sent.

- DRMODE:   the current DR mode  level for the equipment. The value will be a positive integer to  represent the current DR level or zero if inactive.

*cluster:* The name of the cluster (optional)

Return Value

Returns 0 if successful otherwise it returns an error.

### EquipGetParameter

Reads a runtime parameter of an equipment database record from the EQPARAM.RDB database file. This function is a blocking function. It blocks the calling Cicode task until the operation is complete.

**EquipGetParameter**(*ClusterName*, *EquipmentName*, *ParameterName*)

*ClusterName* The name of the cluster (optional for a single cluster system)

*EquipmentName* The name of the equipment from which to get  information. The name of the equipment can be prefixed by the name of  the cluster that is "ClusterName.Equipment".

*ParameterName* The name of the parameter for which to retrieve a value.

Return Value

The value of the specified parameter as a string. If the parameter is a tag reference, the value of the tag shall be returned.

**Note:** The value field of the Equipment  Runtime Parameters table can work like a tag reference when the Is Tag  column is set to true or default. It can contain Variable tag, or  equipment and item name reference of a variable tag (using  equipment.item notation) that will result in the tag value being  returned by this function.

An empty string may or may not be an indication that an error has been detected. The last error should be checked in  this instance to determine if an error has actually occurred.

## Приклади

