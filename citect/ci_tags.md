# Tag Functions

The Tag functions allow you to read the values  of variables in I/O devices such as PLCs, and to write data into these  I/O device variables. These functions also allow you to control I/O  devices and to display information about I/O devices.

Following are functions relating to Tags:

| SubscriptionAddCallback    | Adds a callback function to a tag subscription.              |
| -------------------------- | ------------------------------------------------------------ |
| SubscriptionGetAttribute   | Reads an attribute value of a tag subscription.              |
| SubscriptionGetInfo        | Reads the specified text information about a subscribed tag. |
| SubscriptionGetQuality     | Reads quality of a subscribed tag.                           |
| SubscriptionGetTag         | Reads a value, quality and timestamps of a subscribed tag.   |
| SubscriptionGetTimestamp   | Reads the specified timestamp of a subscribed tag.           |
| SubscriptionGetValue       | Reads a value of a subscribed tag.                           |
| SubscriptionRemoveCallback | Removes a callback function from a tag subscription.         |
| TagBrowseClose             | Terminates an active data browse session and cleans up all resources associated with the session. |
| TagBrowseFirst             | Places the data browse cursor at the first record.           |
| TagBrowseGetField          | Retrieves the value of the specified field from the record the data browse cursor is currently referencing. |
| TagBrowseNext              | Moves the data browse cursor forward one record.             |
| TagBrowseNumRecords        | Gets the number of records for a given browsing session.     |
| TagBrowseOpen              | Initiates a new browse session and returns a handle to the new session that can  be used in subsequent data browse function calls. |
| TagBrowsePrev              | Moves the data browse cursor back one record.                |
| TagDebug                   | Displays a dialog which allows you to select any configured tag to read or change (write) its value. |
| TagDebugForm               | Displays a dialog that allows you to select a variable tag and perform some basic read/write operations. |
| TagEventFormat             | Returns a handle to the format of the data used by the TagEventQueue(). |
| TagEventQueue              | Opens the tag update event queue.                            |
| TagGetProperty             | Gets a property for a variable tag from the datasource.      |
| TagGetScale                | Gets the value of a tag at a specified scale from the datasource. |
| TagGetValue                | Gets the value, quality and timestamp of a tag based on the tag subscription. |
| TagInfo                    | Gets information about a variable tag.                       |
| TagInfoEx                  | Gets information about a variable tag.                       |
| TagRamp                    | Increments a tag by a percentage amount.                     |
| TagRDBReload               | Reloads the variable tag database so when TagInfo is called it picks up online changes to the tag database. |
| TagRead                    | Reads a variable from an I/O Device.                         |
| TagReadEx                  | Reads the value, quality and timestamp of a particular tag element. |
| TagResolve                 | Increments a reference count on a tag to keep it resolved.   |
| TagScaleStr                | Gets the value of a tag at a specified scale.                |
| TagSetOverrideBad          | Sets a quality Override element for a specified tag to Bad Non Specific. |
| TagSetOverrideGood         | Sets a quality Override element for a specified tag to Good Non Specific. |
| TagSetOverrideUncertain    | Sets a quality Override element for a specified tag to Uncertain Non Specific. |
| TagSetOverrideQuality      | Sets a quality Override element for a specified tag.         |
| TagSubscribe               | Subscribes a tag for periodic monitoring and event handling. |
| TagUnsubscribe             | Unsubscribes a tag for periodic monitoring and event handling. |
| TagUnresolve               | Unresolves a reference count implemented on a tag by TagResolve(). |
| TagWrite                   | Writes to an I/O Device variable.                            |
| TagWriteEventQue           | Opens the tag write event queue.                             |
| TagWriteIntArray           | Writes an array of integers to a tag.                        |
| TagWriteRealArray          | Writes an array of reals to a tag.                           |

## TagGetProperty

This function reads a property of a variable tag from the data source. This function replaces [TagInfo](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/TagInfo.html).

Syntax

```
STRING TagGetProperty(STRING Name, STRING Property [, INT CachedMode] [, STRING ClusterName] )
```

*Name:* The name of the tag or the  equipment and item name of a variable tag (using  equipment.item  notation) from which to get information. The tag can be prefixed by the name of the cluster that is "ClusterName.Tag" or "ClusterName.Equipment.Item".

**Note**: If the tag name  exceeds the length limit of 254 characters the hardware alarm "Tag name exceed length limit" will be raised.

*Property:* The property to read. Property names are case sensitive. Supported properties are:

- *Address* - Returns the configured address of the tag (as specified in the variable tags form). 
- *ArraySize* - Array size of the associated tag. Returns 1 for non-array types.
- *ClusterName* - Name of the cluster the tag resides on.
- *DataBitWidth* - Number of bits used to store the value
- *Description* - Tag description
- *EngUnitsHigh* - Maximum scaled value
- *EngUnitsLow* - Minimum scaled value
- *Equipment* - Name of the equipment associated with the Tag.
- *Format* - Format bit string. The format information is stored in the integer as follow
- - Bits 0-7 - format width
  - Bits 8-15 - number of decimal places
  - Bits 16 - zero-padded
  - Bit 17- left-justified 
  - Bit 18 - display engineering units
  - Bit 20 - exponential (scientific) notation
- *FormatDecPlaces* - Number of decimal places for default format
- *FormatWidth* - Number of characters used in default format
- *FullName* - Full name of the tag in the form cluster.tagname.
- *Item* - Name of the equipment item associated with the Tag. If the tag is not resolved, returns an empty string.
- *RangeHigh* - Maximum unscaled value
- *RangeLow* - Minimum unscaled value
- *TagName* - Name of the tag specified.
- *Type* - General type of tag. Allowed values are:

> > - 0 - Digital
> > - 1 - Byte
> > - 2 - Integer16
> > - 3 - UInteger16
> > - 4 - Long
> > - 5 - Real
> > - 6 - String
> > - 7 - ULong
> > - 8 - Undefined

- *Units* - Engineering Units for example, %, mm, Volts.
- *Custom1 ... Custom8* - User-defined strings.
- *CachedMode:*        

Optional parameter that specifies from where to retrieve the value for the property.

**Note:** When retrieving bit width  ("DataBitWidth" property) or array size ("ArraySize" property) from the  local configuration (iCachedMode 2), the value is related to the data  structure in the device. For example,  MODNET, is a 16 bit device and  does not have native LONG and REAL numbers. So when you have a LONG  variable, an array of 2 INTEGERS are needed to store it. In the example, the property "DataBitWidth" against the variable will return 16 and  property "ArraySize" will return 2. The combination of these two return  values will add up to the correct bits.

-1 - The mode is determined by the INI parameter **[Client]TagReadCachedMode**.

0 - The property value is retrieved direct  from the server in blocking mode and an error code is returned if it is  not on the server (or the server is unavailable).

**Note**: For the first call of TagGetProperty to return a proper value for custom fields, mode 0 needs to be specified.

1 - The property value is retrieved from the cache and an error code is returned if the cache is not loaded yet.

2 - The property value is retrieved from the local configuration and an error code is returned if it is not  available (this is the traditional behaviour).

3 - The property value is retrieved from the cache, if the cache is loaded, and from the local configuration, if the cache is not loaded yet.

Default value is -1.

*ClusterName:*        

Specifies the name of the cluster in which the Tag resides. The argument is enclosed in quotation marks.

Return Value

String representation of the property of the tag. If unsuccessful, an empty string and an error code is set.