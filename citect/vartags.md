# Variable Tags

## Tag Elements 

A variable tag is a representation of data elements. Each element provides access to a view of the data value for the tag.  Each variable tag can be used on its own or by referencing a particular element to access the following information:

| Element       | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| .field        | The field element, which represents the latest field data received from the device. |
| .valid        | The valid element, which represents the last field data which had ‘Good’ quality. |
| .override     | The override element, which represents the overridden tag value. |
| .overridemode | The override mode, which is used to set the override behavior of the tag. |
| .controlmode  | The control mode, which is used to set the control inhibit mode of the tag. |
| .status       | The tag status element, which is used to represent the current status of the tag. |

 The tag and each element have items that can be referenced to access the following information:

| Item | Description                                                  |
| ---- | ------------------------------------------------------------ |
| v    | The value item. Use this to retrieve the current data value of the tag or element. |
| vt   | The value timestamp item. Use this to retrieve a timestamp that represents when the value last changed. |
| q    | The quality item. Use this to retrieve  the quality of the value.The quality item differs to other elements as  it offers several layers of information. For more information, see The Quality Item. |
| qt   | The quality timestamp item. Use this to retrieve a timestamp that represents when the quality last changed. |
| t    | The timestamp item. This will access the timestamp of when the tag or element was last updated. |

To refer to tag elements in your project, you use Tag Extensions. 

### The Quality Item

The majority of data which is contained within  the variable tag is represented as an element which includes the items  "Value", "ValueTimestamp", "Quality", "QualityTimestamp" and  "Timestamp". With the exception of "Quality" these items are absolutes of a single value. However the "Quality" item has  several layers of information within it. These layers of information are covered by the following categories:

The primary layer identifies the **General Quality Values**.

| Cicode Label Name | Value | Description                                                  |
| ----------------- | ----- | ------------------------------------------------------------ |
| QUAL_BAD          | 0x00  | Value is not useful for reasons indicated by the Substatus Bit Field. |
| QUAL_UNCR         | 0x01  | The Quality of the value is uncertain for reasons indicated by the Substatus Bit Field. |
| QUAL_GOOD         | 0x03  | The Quality of the value is Good.                            |

These can be accessed from a text object on a graphics page at runtime, or with the Cicode function QualityGetPart using the necessary value for the Part parameter.

Within each of these quality values is a  substatus layer, and a third extended substatus layer. These layers of  information can also be accessed using the QualityGetPart Cicode  function.

## Tag Extensions

Tag extensions allow you to refer to the elements of a tag. They support the following functionality:

- Provide access to the quality and time stamp information associated with a tag value.
- Provide extended data to Citect SCADA client components, such as a display client, trend server, alarm server, report server, Cicode and CtAPI.
- Allow you to apply an override to a tag, and prohibit writing to the tag value.
- Allow you to display and trend tag values even if their quality is not "good".
- Enable tag value persistence, and replication of tag data.

The tag reference syntax used for tag extensions is as follows:

`[Cluster.]Tag[.Element][.Item][[n]]`       

Where:

| Cluster | The optional cluster name.                                   |
| ------- | ------------------------------------------------------------ |
| Tag     | The tag name or Super Genie association.                     |
| Element | The optional element name. If the element name is not specified, the requested element will be determined at runtime. |
| Item    | The optional item name. If the item name is not specified, the whole element is referenced. |
| n       | The optional array index if the tag is defined as an array   |

The array index is at the end of the reference  (MyArray.v[n], MyArray.Field[n], MyArray.Field.v[n]). There is only a  single quality and timestamp for each array, each member will return the same quality and timestamp.

**Note:** Consider the impact  on network traffic when configuring tag extensions, as the distribution  of quality and value timestamps increases the amount of data being sent  between servers.

You can use tag extensions to access tag data in the following ways:

- Reference tag data using only the tag name, for example: 
- "MyTag" (unqualified tag reference).

- This will provide default access to the **.field** element information, unless the tag is in one of the override modes.

- Reference tag data using the tag name and the item name, for example:
- "MyTag.q" (unqualified tag reference)

- This will provide access to the item information for the tag, either default from **.field** or **.override** element.

- Reference the tag data by using the tag name and the element name, for example:
- "MyTag.field" (qualified tag reference)

- This reference will provide access to the specified tag element information.

- Reference the tag data by using the tag name, element name and the item name, for example:
- "MyTag.field.vt" (qualified tag reference)

-  This reference will provide access to the specific tag element item.

You can also access alarm data in a similar way. See Using Alarm Properties as Tags. 

**Note:** Consider the impact  on network traffic when configuring tag extensions, as the distribution  of quality and value timestamps increases the amount of data being sent  between servers.

### Controlling Tag Extension Behavior

By default, the tag data referenced without an  element will provide access to the data value when the value is of  quality is good and an error (#BAD, #COM, etc) when the quality is bad.  The configuration parameter [Page]IgnoreValueQuality can be used to  change this behavior, including automatically changing the background  color of text and number graphics objects on a page with changes in  quality of the tag.

Tag extension behavior is controlled by several citect.ini file settings which are described in the Parameters  Reference. For each of these settings there is a corresponding setting  in the project database parameters (param.dbf). 

A citect.ini file setting specifies behavior for a particular machine and a parameter database setting is applied system-wide.

**Note:** By default, the  TagSubscribe Cicode function is set to retrieve "lightweight" tag values that exclude quality and value timestamps. If you need a subscription  to retrieve timestamp data, you need to set the "bLightweight" argument  to 0 (false).

