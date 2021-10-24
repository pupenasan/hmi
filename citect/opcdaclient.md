# OPC DA Client

## OPC Driver 

The OPC method of communication to OPC devices uses the OPC driver. OPC specifications v1.0a and v2.0 are supported. Using this method you can connect to single or multiple OPC devices, as shown in this example configuration:     

![img](mk:@MSITStore:C:\Program%20Files%20(x86)\AVEVA\Citect%20SCADA%202018%20R2\Bin\OPC.chm::/Images/setup.jpg)         

The OPC server can also exist on the same computer as the OPC client. Be reminded that the maximum request length (that is, the maximum of data bits that can be read from the I/O device at any one time) for the OPC protocol is 2040. 

**Note:** With the release of version 7.20, Citect SCADA supports the retrieval of time-stamped data directly from field devices. This capability is enabled by the Driver Runtime Interface (DRI), a component of Citect SCADA that is used by the OPC driver to directly update time-stamped digital alarms, time-stamped analog alarms and event-based trends. For more information, see the topic *Retrieving time-stamped data from field devices* in the main Citect SCADA help. 

### Hardware requirements     

In the OPC architecture, each variety of server is allocated a unique identifier, known as a Class ID. OPC clients use these 128-bit numbers, frequently displayed in the form 6B29FC40-CA47-1067-B31D-00DD010662DA, to access the particular vendor's OPC server. To make it easier for users, these numbers are often referred to by a more manageable string identifier called a ProgID (Program Identifier). These identifiers usually take the form **Vendor.Application** with an optional version number appended; for example, the Citect SCADA  OPC Server ProgID is **Citect.OPC**.     

Before the OPC client driver can access a particular OPC server, the server’s ProgID needs to be entered into the Citect SCADA  I/O server registry. Where an in-process server or a local server is being used, this should have been done automatically when the server was installed. To access a remote server, refer to the documentation accompanying the server. Frequently, this step is achieved using a registry script (a .REG file) or a small executable.     

**Note**         

- Familiarize yourself with the target OPC server(s) before using this driver. This will help you enter the item identifiers for the tag addresses using the correct syntax.       
- Using remote servers requires configuring DCOM security. Since configuring security can be complex, you should plan your system settings in advance, and establish a protocol so that the Windows accounts to be used by operators have sufficient privilege. If sufficient privileges are not established, communications errors may result. See [Software requirements](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_software_requirements.htm) for more information. 

### Software requirements     

OPC operates using the Microsoft Distributed COM (DCOM) architecture, which is part of the Windows operating system.     

If a distributed OPC system is being accessed (i.e., remote servers), you need to configure DCOM security settings on the remote machines to allow operators access to the servers. To configure these settings, use the program DcomCnfg.exe. If sufficient privileges are not established, communications errors may result, so take care when configuring your system. 

## OPC Devices and Clients 

### Device Address Information

The address to use is the ProgID for the desired server. These usually take the form Vendor.Application (e.g. Citect.OPC), and should be found in the documents accompanying the OPC Server.

#### Communications Forms     

The following tables show the recommended settings for communication with an OPC device. These settings are implemented by the Express Communications Wizard on the Boards dialog box, Ports dialog box, and Devices dialog box.     

**Boards dialog box**         

The Boards dialog box lists all boards used in the       Citect SCADA  project. Each board record defines a separate board within the project.     



| Text box            | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| **Board Name**      | A unique name (up to 16 alphanumeric character) per server for the computer board being used to connect with the device. This is used by Citect SCADA  in the Ports dialog box. |
| **Board Type**      | The type of board. Enter **OPC**.                            |
| **Address**         | Citect SCADA  doesn’t need an address for the OPC client. Instead you use the **Address** box to set the device scan rate on the OPC Server in milliseconds. The value read from the OPC server is typically taken from the OPC server cache. The scan rate value is often used to indicate how often the OPC server polls the device and updates its cache.             Enter **0** (zero) to use the default of 250ms. Enter any other value to use that value. Valid values range from eight character decimal 0 to 99999999. Up to six character hex values can be used; however, these must be preceded with 0x.             **Note:** As Citect SCADA  supports unsolicited OPC requests, if you set the OPC server to notify Citect SCADA  of changes to the value or quality of an OPC device item, make sure the OPC server scan rate is short enough to provide Citect SCADA  within an adequate timeframe. |
| **I/O Port**        | Leave this field blank.                                      |
| **Interrupt**       | Leave this field blank.                                      |
| **Special Options** | OPC server machine name. (Do not enter this name using the traditional dash delimited style. Enter the machine name, for example **Cit_Primary**.             **Note:** The name entered here is the Windows machine name. For Windows NT and Windows 95 or 98 based OPC servers, you can obtain this from the **Identification** tab of the OPC server machine's network properties. For other OPC server configurations, refer to the server's documentation.             If this field is left blank, the server name is sought in the following manner: a) The in-process (DLL) server on the IO Server machine; b) The local (EXE) server on the I/O server machine; c) The remote server as entered in the I/O server machine's DCOM settings. |
| **Comment**         | Any useful comment. This is viewed in the Boards records database in Citect Project Editor. |



**Ports dialog box**          

The Ports dialog box lists all ports used in the Citect SCADA  project. Each port record defines a separate port within the project.     



| Text box            | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| **Port Name**       | A unique name (up to 16 alphanumeric character) for the computer port being used to connect with the device. This is used by Citect SCADA  in the Devices dialog box. |
| **Port Number**     | An integer value, unique to the board as defined in the Board Name field. The Ethernet port needs no identification; however, the Citect SCADA  communication database requires a value in this field. |
| **Board Name**      | The name of the board this port is attached to as defined on the Boards dialog box. |
| **Baud Rate**       | Leave this field blank.                                      |
| **Data Bits**       | Leave this field blank.                                      |
| **Stop Bits**       | Leave this field blank.                                      |
| **Parity**          | Leave this field blank.                                      |
| **Special Options** | Leave this field blank.                                      |
| **Comment**         | Any useful comment. This is viewed in the Boards records database in Citect Project Editor. |



**Devices dialog box**         



| Text box      | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| **Name**      | A unique name (up to 16 alphanumeric characters) for the I/O device being identified. Each I/O device must have a unique name in the Citect SCADA  system. |
| **Number**    | A unique number for the I/O device (0–16383). Each I/O device must have a unique number in the Citect SCADA  system (unless I/O device redundancy is being used). |
| **Address**   | ProgID for the desired server. These usually take the form Vendor.Application (for example, Citect.OPC) and should be found in the documents accompanying the OPC Server. |
| **Protocol**  | Enter “OPC” or “OPC1”. See [Arrays support](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_arrays_support.htm). |
| **Port Name** | This field must contain one of the names previously defined in the **Port Names** box of the Ports dialog box. There must be only one I/O device per port. |
| **Comment**   | Any useful comment. This is viewed in the Devices records database in Citect SCADA  Project Editor. |

### Data types     

OPC servers can provide data in different data formats. An OPC client can request data in a specific format or use the server’s type (that is, the type in which the data is stored within the server).     

When specifying a data type, consider whether the server will be able to convert data to the requested type.     

Use the table below to help you specify a type for a variable tag. It shows mappings from the types used by OPC (VARTYPE) to Citect SCADA  data types. If followed, these data types coerce the OPC data Citect SCADA  data types.     



| OPC Type (VARTYPE) | Description             | Citect SCADA  Data Type |
| ------------------ | ----------------------- | ----------------------- |
| VT_BOOL            | Boolean                 | DIGITAL                 |
| VT_UI1             | Byte                    | BYTE                    |
| VT_I2              | 2 byte integer          | INT                     |
| VT_UI2             | 2 byte unsigned integer | UINT                    |
| VT_I4              | 4 byte integer          | LONG                    |
| VT_U14             | 4 byte unsigned integer | ULONG (requires v7.0)   |
| VT_CY              | Currency                | STRING                  |
| VT_R4              | 4 byte real             | REAL                    |
| VT_R8              | 8 byte real             | STRING                  |
| VT_DATE            | Date                    | STRING                  |
| VT_BSTR            | String                  | STRING                  |
| VT_ERROR           | Error value             | LONG                    |
| VT_QUALITY         | 2 byte integer          | INT                     |
| VT_TIMESTAMP       | 4 byte integer          | LONG                    |
| VT_MILLISECOND     | 4 byte integer          | LONG                    |

### Include project support     

By default the OPC driver does not support the definition of variable tags in projects that are included below the main project.      

Variable tags defined in a project compiled on a Citect SCADA  client needs to match exactly the tags defined in the project compiled on the I/O server. If a tag is added on the client, it needs to also be added on the I/O server. Otherwise client requests may become mismatched and show incorrect data. 

### Quality values     

The following masks are general bitmasks:     



| OPC_QUALITY_MASK | 0xC0 |
| ---------------- | ---- |
| OPC_STATUS_MASK  | 0xFC |
| OPC_LIMIT_MASK   | 0x03 |



These are specific quality values:     



| OPC_QUALITY_BAD            | 0x00 |
| -------------------------- | ---- |
| OPC_QUALITY_UNCERTAIN      | 0x40 |
| OPC_QUALITY_GOOD           | 0xC0 |
| OPC_QUALITY_CONFIG_ERROR   | 0x04 |
| OPC_QUALITY_NOT_CONNECTED  | 0x08 |
| OPC_QUALITY_DEVICE_FAILURE | 0x0C |
| OPC_QUALITY_SENSOR_FAILURE | 0x10 |
| OPC_QUALITY_LAST_KNOWN     | 0x14 |
| OPC_QUALITY_COMM_FAILURE   | 0x18 |
| OPC_QUALITY_OUT_OF_SERVICE | 0x1C |
| OPC_QUALITY_LAST_USABLE    | 0x44 |
| OPC_QUALITY_SENSOR_CAL     | 0x50 |
| OPC_QUALITY_EGU_EXCEEDED   | 0x54 |
| OPC_QUALITY_SUB_NORMAL     | 0x58 |
| OPC_QUALITY_LOCAL_OVERRIDE | 0xD8 |



These can modify any of the above:     



| OPC_LIMIT_OK    | 0x00 |
| --------------- | ---- |
| OPC_LIMIT_LOW   | 0x01 |
| OPC_LIMIT_HIGH  | 0x02 |
| OPC_LIMIT_CONST |      |

### Arrays support     

To associate a Citect SCADA  variable tag with an OPC array, follow the OPC array address string with a delimiter like “!”, the capital letter “A” (which when combined like this instructs the Citect SCADA  OPC driver that the address is for an array), and follow both with the array size as an integer enclosed within square brackets, like this:     

<OPCArrayName>!A[<OPCArrayLength>]     

**Note:** Replace the placeholders <OPCArrayName> and       <OPCArrayLength> in the **Address** box with the actual valid values of the OPC Array **Name** and       **Length** you want to use, as defined in the OPC server.     

In the following example with an OPC tag defined on a BACnet OPC server, five register addresses are associated with the Citect SCADA  variable tag named Status_Flags:     

- **Variable Tag Name**: Status_Flags
- **Address**: device(7196).analog-output(1).status!A[5]       

You can access individual elements of an OPC array in Citect SCADA  by specifying the Citect SCADA  tag name and an index number representing the individual element of the array. For example, to refer to the third variable of the array in the above example (Status_Flags), use this syntax in Citect SCADA :     

**Variable Tag: Status_Flags[2]**         

**Note:** OPC arrays use zero-based indexing. For example, a five register array would contain individual elements indexed as 0, 1, 2, 3, and 4.     

The OPC address checking in Citect SCADA always ensures that the !A[<n>] suffix is used, otherwise the tag is not recognized as an OPC array, regardless of whether OPC or OPC1 variant is used. Therefore the format '!A[<n>]' must be followed in a tag address if the tag is defined as an array tag.

 For example:     

**With access path: DB1,DINT0,10!A[10**         

Without access path: S7:[OPCFLR]DB1,DINT0,10!A[10]

The OPC1 protocol is used to support Cicode functions TagRead() and       TagWrite() for tags with a left square bracket “[“ in their address.     

However, if there is no left square bracket “[“in the OPC address string, you can use the array length specifier at the end of the address string, and so you should declare OPC as the I/O device protocol used in the I/O device setup procedure. 

| ![img](mk:@MSITStore:C:\Program%20Files%20(x86)\AVEVA\Citect%20SCADA%202018%20R2\Bin\OPC.chm::/Images/warning2.gif) |
| ------------------------------------------------------------ |
| **UNINTENDED EQUIPMENT OPERATION**                     Ensure that the OPC address format used is compliant for the OPC Server with which you are communicating.**Failure to follow these instructions can result in death, serious injury, or equipment damage.** |

**Example:**         

Utilizing the ABCLX array address format <OPCArrayName>/<OPCArray Start Index>!A<OPCArray Length> with the Factory Talk OPC server will produce unexpected results.    

When Citect SCADA  writes to an OPC array, the whole array is read from the driver cache, modified, then written back to the OPC server. However, the driver cache is not updated with the newer data until the server performs its housekeeping tasks and notifies the driver that the array value has been changed. During this time, it is possible for another write request to have been issued with a now out-of-date copy of the original array data from the not-yet-updated driver cache. If subsequently written back to the server, any changes made in the first request of this scenario might be lost inadvertently if they are overwritten by the original duplicated data in the second write back.

To try and minimize this, the OPC driver in Citect SCADA  is forced to do a synchronized read before data is modified. However it still has the possibility of losing data if that data is changed by other OPC clients between the time the data is read out and written back. For this reason, it is not recommended that OPC arrays be used in Citect SCADA  while other OPC clients might be accessing the same data. 

| ![img](mk:@MSITStore:C:\Program%20Files%20(x86)\AVEVA\Citect%20SCADA%202018%20R2\Bin\OPC.chm::/Images/warning2.gif) |
| ------------------------------------------------------------ |
| **UNINTENDED EQUIPMENT OPERATION**                     Do not use OPC arrays in Citect SCADA while other OPC clients have access to the same data.                   **Failure to follow these instructions can result in death, serious injury, or equipment damage.** |

### Timestamp and quality support     

The Citect SCADA  OPC driver can use additional variable tags for quality and timestamp values. Quality or timestamp tags are duplicates of a variable tag, with an appended “!Q” or “!T” or “!M” in the address field to define their purpose. Quality tags need to be configured as either INT or DIGITAL data types, whereas Timestamp tags need to be configured as LONG data types. 

If you just need to know if an OPC item is good or bad quality (i.e. not uncertain), you should consider using DIGITAL data types for quality tags in combination with [[OPC\]DigitalQualityUncertainIsBad](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm), rather than using Cicode to compare the value of an INT quality tag against 0xC0   

**Note:** The quickest way to create a quality or timestamp tag in Citect SCADA  is to locate the relevant variable tag using the Variable Tags dialog box, edit it as required to create a quality or timestamp tag, and save it. This creates a copy of the original variable tag with the required changes saved.     

To create a quality tag:     

1. Open the Variable Tags dialog box in Project Editor (Tags | Variable Tags).       
2. Create a new variable tag, or locate and display the tag that you want to associate the quality tag with.       
3. In the **Variable Tag Name** box, enter an appropriate and unique name for the quality tag, such as “<Tagname>_Quality”.       
4. In the **Data Type** box, choose INT or DIGITAL from the menu.       
5. In the **I/O Device Name** box, select the appropriate I/O device for the tag (if not already displayed).       
6. In the **Address** box, enter the name of the tag you want to associate with the quality value (if not already displayed), and append  “**!Q**” directly to the end of the address (without the quotes and without any spaces).       
7. Click **Add**.       

Note: If the exclamation mark character (!) is already defined in the tag address field (for example, you have already used it to declare an array size "!A[n]"), you either need to include another exclamation mark (e.g. append "!Q" to the tag address) after the closing square bracket of the array size declaration, or you can specify quality for arrayTag!A[5] with just arrayTag!Q".     

To create a timestamp tag:         

1. Open the Variable Tags dialog box in Project Editor (Tags | Variable Tags).       
2. Create a new variable tag, or locate and display the tag that you want to associate the timestamp tag with.       
3. In the **Variable Tag Name** box, enter an appropriate and unique name for the timestamp tag, such as **<Tagname>_sTimestamp** (for seconds) or **<Tagname>_msTimestamp** (for milliseconds).       
4. In the **Data Type** box, choose **Long** from the menu (if not already selected).       
5. In the **I/O Device Name** box, select the appropriate I/O device for the tag (if not already displayed).       
6. In the **Address** box, enter the name of the tag you want to associate with a timestamp value (if not already displayed), and append  “**!T**” or “**!M**” (as appropriate).       

**Note:** If there is already an exclamation mark with other declarations included in the tag address, you don’t need to include them for timestamping. For example, a timestamp tag monitoring TagName!A[64] can be addressed as TagName!T.     

1. Click **Add**.       

**Note:** Timestamps store the number of seconds since 01/01/1970 when using the “!T” element, or the number of milliseconds since midnight using the “!M” element. If you want to store a complete time in millisecond accuracy, you need to create two separate timestamp tags, one for seconds and one for milliseconds, each addressed appropriately.     

Examples     

In the following examples, an OPC device tag defined on a BACnet OPC server is associated with the base Citect SCADA  variable tag named Present_Value:     



| **Variable Tag Name**      | Present_Value                                                |
| -------------------------- | ------------------------------------------------------------ |
| **Address**                | device(7196).analog-output(1).present-value                  |
| Citect SCADA **Data Type** | Data type required by project (for a list of data types, see               [Data types](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_data_types.htm)). |



**Example 1**         

Use the following settings to associate a Citect SCADA  variable tag with the quality stamp of the OPC register value:     



| **Variable Tag Name**      | Present_Value_Quality                         |
| -------------------------- | --------------------------------------------- |
| **Address**                | device(7196).analog-output(1).present-value!Q |
| **OPC Type**               | VT_QUALITY                                    |
| Citect SCADA **Data Type** | INT or DIGITAL                                |



**Example 2**         

The following tag definition will read the Timestamp value measured in seconds from 1/Jan/1970:     



| **Variable Tag Name**      | Present_Value_Timestamp                       |
| -------------------------- | --------------------------------------------- |
| **Address**                | device(7196).analog-output(1).present-value!T |
| **OPC Type**               | VT_TIMESTAMP                                  |
| Citect SCADA **Data Type** | LONG                                          |



**Example 3**         

The tag definition below will read the Millisecond Timestamp value measured in UTC FileTime from beginning (midnight) of the current day:     



| **Variable Tag Name**      | Present_Value_Millisecond                     |
| -------------------------- | --------------------------------------------- |
| **Address**                | device(7196).analog-output(1).present-value!M |
| **OPC Type**               | VT_MILLISECOND                                |
| Citect SCADA **Data Type** | LONG                                          |



The base Citect SCADA  tag needs to be defined in Citect SCADA  before the timestamp and quality values of the associated OPC Server tag value can be read. 

### Advanced configuration and maintenance     

### Status tags     

You can define status tags in your Citect.ini file to allow the OPC driver to determine the current state of an OPC device. For example, a status tag could be configured to monitor an OPC item that indicates the current operational state of a connected device. If the condition of the status tag is true, the OPC driver can allow the device to come online; otherwise the device may be set to offline.

By default, no status tags are created for the OPC driver. They need to be defined in the project Citect.ini file using the OPC status tag parameters. These parameters determine which OPC items are monitored, the condition values, and how often polling occurs.

A status tag can be defined in the [OPCStatusTags] section of the Citect.INI file to determine the online status of OPC devices. You can also create status tag set for each individual I/O device using the following format:

```
 
[OPCStatusTags]
<IOServerName>.<IODeviceName>.<parameter>=<value>
```

For example:

```
 
[OPCStatusTags]
io1.iodev1.tag=ARB3183800_S_2.REQNUM
io1.iodev1.condition= <=10
```

where:

```
"ARB3183800_S_2.REQNUM" 
```

refers to an OPC item configured in the device.

If you are not regularly reading from a particular device, it is recommended that you enable status units checks. To do this, you need to enable the parameter [IOServer]WatchDogPrimary.Standby units are enabled by default. 

### Customizing a project using Citect.ini parameters     

You use Citect.ini parameters to finetune the performance of the Citect SCADA  OPC driver and to perform runtime maintenance diagnostics.     

| ![img](mk:@MSITStore:C:\Program%20Files%20(x86)\AVEVA\Citect%20SCADA%202018%20R2\Bin\OPC.chm::/Images/warning2.gif) |
| ------------------------------------------------------------ |
| **UNINTENDED EQUIPMENT OPERATION**                     Do not under any circumstances change or remove any of the undocumented citect.ini parameters.Before deleting sections of the citect.ini file, confirm that no undocumented parameters will be deleted.**Failure to follow these instructions can result in death, serious injury, or equipment damage.** |

**Note:** Always seek the advice of Technical Support personnel for this product regarding undocumented features.

You can customize the way Citect SCADA  communicates with the OPC system, and even individual PLCs, by creating or editing the [OPC] section of the Citect.ini file for your project.     

There are some common Citect SCADA  driver settings, and custom Citect SCADA  OPC driver settings.     

When Citect SCADA  starts at runtime, it reads configuration values from the Citect.ini file stored locally. Therefore, any OPC configuration settings need to be included in the Citect.ini file located on the computer acting as the I/O server to the OPC system.     

**Note:** By default, Citect SCADA  looks for the ini file in the Citect SCADA  project       \bin directory. If it can't find it there, it searches the default Windows directory.     

The default values for these parameters have been determined by driver development and testing to be optimal for the Citect SCADA  OPC driver. Parameters default to a value tested to work in common configurations. Don’t adjust these default values except on the direct advice of Citect Customer Support.     

This section describes the following types of OPC parameters:     

- [Common Citect.ini driver parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_common_citectini_driver_parameters.htm)             
- [Driver-specific Citect.INI parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm)             
- [OPC device-specific parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm)             
- [OPC access path parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_access_path_parameters.htm)             
- [OPC status tag parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_status_tag_parameters.htm)             
- [OPC array parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_array_parameters.htm)             

For more details, see [Driver-specific Citect.INI parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm)

#### Common Citect.ini driver parameters     

The following table describes the common citect.ini driver parameters.     



| [OPC] Parameter | Allowable Values   | Default Value | Description                                                  |
| --------------- | ------------------ | ------------- | ------------------------------------------------------------ |
| Block           | 5 to 256           | 255           | A value (bytes) used by the Citect SCADA  I/O server to determine if two or more packets can be blocked into one data request before being sent to the OPC driver. For example, if you set the value to 10, and the I/O Server receives two simultaneous data requests (one for byte 3, and another for byte 8) the two requests are blocked into a single physical data request packet. This single request packet is then sent to the I/O device, saving on bandwidth and processing. |
| Delay           | 0 to 300           | 0             | Period (in ms.) to wait between receiving a response and sending the next command to the I/O server. |
| MaxPending      | 1 to 1024          | 250           | Maximum number of pending commands that the Citect SCADA  OPC driver holds ready for immediate execution. |
| Polltime        | 0 to 300           | 1000          | Polling service time (in milliseconds) at which cached data is updated. Recommended to be at least twice that of the value used in the Citect.INI [ALARM] ScanTime parameter. |
| Retry           | 0 to 8             | 0             | Number of times to retry a command after a timeout.          |
| Timeout         | 0 to 32000         | 3000          | Milliseconds to wait for a response before considering a write or polling request to be invalid and displaying an error message in Citect SCADA . |
| Watchtime       | 0 to 128 (seconds) | 15            | Frequency that the Citect SCADA  OPC driver uses to check the communications link to the OPC system and attempts to bring offline units back online. Also determines the frequency of STATUS_UNIT commands to the driver. See [Configuring redundancy](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_configuring_redundancy.htm). |

#### Driver-specific Citect.INI parameters     

The following table describes the driver-specific Citect.ini parameters.     

| [OPC] Parameter              | Allowable Values                                             | Default Value     | Description                                                  |
| ---------------------------- | ------------------------------------------------------------ | ----------------- | ------------------------------------------------------------ |
| AddItemAsVtEmpty             | 0 - Specify data types             1 - Use native data type  | 1                 | Determines whether the OPC driver specifies a data type when adding an item, or whether it uses the native data type when adding items.             This parameter is used to select whether the OPC client will specify a type to force the OPC Server to coerce the data, or for the OPC server to provide the type as configured on the server. |
| ArrayRecordBase              | Greater than total number of tags and less than (65000 – number of arrays) | 30000             | Specifies the base of the array record numbers. Citect SCADA  communicates with the OPC client driver by the record number of the tag in variable.dbf, so this parameter needs to be greater than the total number of tags in the project. |
| CacheRead                    | 0 – Value is refreshed and the latest value returned.             1 – Last known value returned. | 1                 | Determines the value returned when an inactive item is read. See [Overriding [OPC\]CacheRead](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/overriding_opccacheread.htm) for information on how to override the value of this parameter for a particular tag. |
| DebugLevel                   | WARN             ERROR             TRACE             ALL     | -                 | Trace level used for log file             See [Logging](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/logging_opc.htm) for examples. |
| DebugCategory                | TAG             PROT             CACHE             DCB             THRD             MISC             BEND                         FEND             ALL | -                 | TAG: Tag configuration trace.             PROT: Operations related to the OPC protocol interface.             CACHE: Operations related to the driver cache.             DCB: Front end driver trace.             THRD: Thread trace.             MISC: Miscellaneous operations.              BEND Operations related to the back-end thread of the driver.             FEND: Operations related to the front-end thread of the driver.             See [Logging](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/logging_opc.htm) for examples. |
| DebugUnits                   | ALL, (GLOBAL) [include the round brackets] or any combination of I/O device names and (GLOBAL) separated by '\|' characters. | All               | Controls which units logging is performed for. Multiple units can be specified. Debug messages that are unrelated to a specific unit are logged against the (GLOBAL) unit. |
| DigitalQualityUncertainIsBad | **0** - An uncertain quality will be   treated as GOOD when a digital quality reading is taken (normal INT version is unaffected)             **1** - an uncertain quality will be treated as BAD when a digital quality reading is taken (normal INT version is unaffected) | 1                 | Determines how an uncertain quality result is treated when a Digital quality reading is taken. |
| FailOnBadData                |                                                              |                   | The parameter has been deprecated since Citect SCADA v7.30   |
| FailOnUncertain              |                                                              |                   | The parameter has been deprecated since Citect SCADA v7.30   |
| FillCacheOnStartup           | **0** - Subscriptions are created in the inactive state and are only activated as read request are received.             **1** - Subscriptions are created in the active state. | 1                 | Determines whether subscriptions are created in the active or inactive state initially. |
| GoOfflineForBadTag           | **0** – disabled. Do not go offline.             **1** - enabled. Go offline. | 0                 | Sets all tags on an OPC device to                 an OPC_QUALITY status of GOOD before Citect SCADA  declares the I/O device online.             This parameter would only be set on the I/O server where the device is defined as primary, so it can only take over from a standby device definition when all tags and the status tag are valid. This minimizes the chances that  com-breaks occur during switchover from standby to primary. It is strongly recommended not to set it on a standby, as it might only be one tag that is invalid. |
| InhibitActivationOnStandby   | **0** – A standby server will follow the same rules for subscription activation            as the primary server. **1** – A standby server will only active a subscription if it believes the          primary server is not active. | 1                 | This parameter allows a standby server to deliberately leave subscriptions in an inactive state when the primary server is online. This is usually used when the primary and standby server are talking to independent OPC servers to reduce the load the standby OPC server would place on field devices.             On startup of a standby server, if this parameter is set to 1, items will not be activated immediately. They will only be activated when the unit itself            becomes the active unit. |
| ItemLifeTime                 | Time (seconds)                                               | 5                 | Determines the time in before a tag is deemed inactive.             The global LeaveTagsActive parameter overrides the ItemLifeTime parameter to force OPC tags to remain active even though Citect SCADA  is no longer requesting them from the driver.             The ItemLifeTime parameter can be individually overridden for any OPC device by the [Active](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm) parameter. |
| LeaveTagsActive              | **0** - Do not leave tags active.             **1** - Leave tags active. | 1                 | Determines whether OPC tags remain active even though Citect SCADA  is no longer requesting them from the driver. Normally tags are made inactive 5 seconds after the last time they are requested.             Some OPC servers take a long time to return a call to activate/inactivate tags, or doing so slows them down, therefore leaving tags active  can sometimes improve performance.             The global LeaveTagsActive parameter can be individually overridden by an [Active](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm) parameter.             See **ItemLifeTime** parameter (above).             Note: This parameter minimizes the likelihood of deactivation of tags on the currently active unit only. Tags on units that have become inactive (standby) will still deactivate |
| NumConcurrentServerInits     | **-1** – Unlimited**32767**                                  | -1                | Represents the maximum number of concurrent initialization and shutdown operations that are performed on each configured OPC Server. Higher values, or -1 (unlimited), will incur greater load on the server, while 0 and 1 determine that initialization is serialized into effectively a single thread. |
| OPCGroupName                 | Any string (maximum 32 characters)                           | CitectGroup_<*n*> | By default, each OPC server is allocated a sequential group name by the OPC driver, i.e. CitectGroup_1, CitectGroup_2, etc. This parameter allows you to replace the default group name with a customized name. You can set this parameter at a device level using [ OPC device-specific parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm). |
| ReadAfterWrite               | **0** - No read, rely on the normal polling/OnDataChange mechanism.**1** - Force sync read of item written from OPC server cache after write.**2** - Force sync read of item written from device after write. | 0                 | Determines if a force read should be made, and if it should be from the OPC server cache or from the device.**Note:** RefreshAfterWrite causes a refresh of all active items, whereas ReadAfterWrite reads back only the item being written to. You should use one or the other. Where both RefreshAfterWrite and ReadAfterWrite are set to 1, RefreshAfterWrite will take precedence, and ReadAfterWrite will be set to 0. |
| RefreshAfterAdd              | 0 - No REFRESH.             1 - Request a REFRESH from the OPC server cache. 2 - Request a REFRESH from the device. | 1                 | Determines whether an OPC REFRESH is requested from the OPC server after activating the group.             This parameter can be disabled if slow start up times are experienced.             The server could be automatically sending a REFRESH, in which case another request may be unnecessary. |
| RefreshAfterWrite            | 0 – Disable forced REFRESH.1 - Enable forced REFRESH from OPC server cache.2 - Enable forced REFRESH from device. | 0                 | Determines whether to force an OPC REFRESH from the OPC Server of ALL active items after Citect SCADA  writes to an item. |
| RefreshBeforeArrayWrite      | 0 – No refresh command sent 1 – Read command sent to refresh the OPC server cache 2 – Read command sent to refresh the OPC device | 0                 | Enables the driver to send a read command to the OPC server before a write command is sent to the OPC server for an array variant. |
| ServerOnlineStates           | "RUNNING" "FAILED" "NOCONFIG" "SUSPENDED" "TEST"             | "RUNNING"         | Defines the list of OPC Server states that the driver considers online. The format is a "\|" separated string, without spaces. If you experience the OPC Server shutting down on startup, it is recommended that the following states are used: "RUNNING\|NOCONFIG\|SUSPENDED" |
| ShutdownWait                 | Time (milliseconds).                                         | 30000             | Determines the time the OPC driver waits before shutting down. On shutdown, the driver attempts to close the connection to the OPC server. If this takes longer than the time specified by this parameter, the driver shuts down anyway (sometimes with unexpected results). This parameter might be needed if the OPC server does not respond within the default wait time. |
| StatusWaitPeriod             | Time (milliseconds)                                          | 5000              | Determines the time the OPC driver waits before requesting tag status for an OPC I/O device. On startup, the OPC driver waits for a Unit status from the OPC server before adding tags to the server. If the value of this parameter is exceeded, the tags are added anyway.             The OPC server should respond within a few seconds. The default wait time of 5 seconds should usually be adequate. |
| SuppressDataNotYetValidError | **0** – Displays “Data Not Yet Valid” errors in the Kernel window and logs them to the Syslog.dat file.             **1** - Suppresses “Data Not Yet Valid” errors, which are not displayed in the Kernel window or logged. In the Citect kernel, under View -> I/O Devices, Citect SCADA  will display “Error Suppressed” in the Error Message field for the particular device. | 0                 | Determines whether “Data Not Yet Valid” error messages are suppressed, or whether they are displayed in the Kernel window and written to the Syslog.dat file. For Citect SCADA  to display the message “Error Suppressed”, you need V5.50 or above. |
| UseArrays                    | **0** – OPC array support disabled.             **1** – OPC array support enabled. | 1                 | Determines whether array support parameters in the [OPCArrays] section are active.             See [OPC array parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_array_parameters.htm). |
| UseAsyncWrites               | **0** - use synchronous writes. **1** - use asynchronous writes. | 0                 | Determines whether writes are synchronous or asynchronous.**Note:** UseAsyncWrites=1 is only valid when [OPC]UseOPC2=1, since OPC1 does not support asynchronous writes. |
| UseOPC2                      | **0** – OPC2 support disabled (Use OPC 1.0a interface).             **1** – OPC2 support enabled (Use OPC DA2 interface). | 0                 | Globally determines whether to use OPC 1.0a or OPC 2.0 interface. Individual overrides can be set using the [UseOPC2](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm) parameter to force the use of a particular version OPC interface with a particular I/O device. |
| UseStatusTags                | **0** – disabled.             **1** – enabled.               | 0                 | Determines whether parameters in the [OPCStatusTags] section are active. Individual overrides can be set using the[ OPC device-specific parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm) to force the use of a particular status tag parameter with a particular I/O device. |
| ValidDataWaitPeriod          | Time (milliseconds)                                          | 10 seconds        | Determines the maximum time that the OPC driver will wait for OPC_QUALITY to be GOOD for all tags before declaring that Device online. This minimizes the likelihood of a client swapping from a standby to a primary prematurely and suppresses alarm flooding at startup.  Set this parameter to 0 to allow units to come online regardless of whether all items for the unit have been verified as good quality.             Note: FillCacheOnStartup=1 needs to be set when ValidDataWaitPeriod>0 |
| WriteTrueAs1                 | **0** - write true as VARIANT_TRUE(-1).             **1** - write true as 1. | 0                 | Determines whether a digital value of TRUE is written as “VARIANT_TRUE(-1)”  or “1”. This parameter should only be required for incorrectly designed OPC servers. When the Citect SCADA  data type is digital, VARIANT_TRUE (-1) is used with VT_BOOL variant type to write a value of true. This happens even if [OPC]AddItemAsVtEmpty is set, as OPC servers should be designed to convert the value when they receive it. |

Log file size and archiving are now controlled by the general [DEBUG] parameters: 

- [[Debug\]ArchiveFiles](ms-its:parameters.chm::/DebugArchiveFiles.html)             
- [[Debug\]FlushPeriod](ms-its:parameters.chm::/DebugFlushPeriod.html)             
- [[Debug\]MaximumFileSize](ms-its:parameters.chm::/DebugMaximumFileSize.html)             
- [[Debug\]SysLogSize](ms-its:parameters.chm::/DebugSysLogSize.html) 

#### Overriding [OPC]CacheRead     

You can override the value in [OPC]CacheRead for a particular tag by suffixing the tag name with:     

- The delimeter “!”       
- The letter C or D, as follows:       

<Tag Name>!C - The tag value returned will be the cache value at the time of the read.     

<Tag Name>!D - A refresh of the tag value is forced before it is returned.     

**Examples:**         

- Tag1!**D** - Forces a refresh of Tag1 before the value is returned.       
- Tag!**C** - The last known cache value of Tag2 is returned.       

When the tag qualifiers C and D are used with other OPC qualifiers (see       [Timestamp and quality support](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_timestamp_and_quality_support.htm)), they must appear last.     

**Example:**         

Tag3Q**C** - Tag3 is associated with a quality tag and the last known value of Tag3 will be returned. 

#### OPC device-specific parameters     

For each OPC I/O device you can specify  parameter conditions that override the default global settings. To do this, use the following format in the [OPC] section of the Citect.ini file.    

**[OPC]**<**IOServerName**>.<**IODeviceName**>.<**Parameter**>=<**Value**>        

where:     

- <**IOServerName**> = Name of I/O server configured in Citect SCADA .       
- <**IODeviceName**> = Name of I/O device configured for OPC communications.       
- <**Parameter**> = Parameter of the I/O device being overridden.       
- <**Value**> = Value of the overriding parameter being set.       

**Note:** There are also a number of status tag parameters that you can override global settings for in the [OPCStatusTags] section of the Citect.ini file. For more information see [OPC status tag parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_status_tag_parameters.htm).     

The following device-specific parameters are supported.

| [OPC] Parameter | Allowable Values                                             | Default Value                                                | Description                                                  |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Active          | **0** - deactivate tag.             **1** - leave tag active. | Value of [LeaveTagsActive](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm) parameter. | Allows user to individually override the global default LeaveTagsActive parameter to specify whether tags should be left active or inactive for a particular OPC I/O device.             Replace the placeholders <IOServerName> and <IODeviceName> in the parameter with the names of the OPC 'I/O Server' and 'I/O Device' you want to override and have remain active.             Determines whether individual OPC tags are left active even though Citect SCADA  is no longer requesting them from the driver. Normally tags are made inactive 5 seconds from the last time they are requested. See the [ItemLifeTime](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm) parameter. |
| Update          | 0 to 32000 (milliseconds)                                    | Scan rate specified in the **Address** box of the Boards form. | Allows the user to individually override the.Default.Update parameter to specify the tag update rate for a particular I/O device. The update rate is the frequency with which the OPC server polls the device for values and updates its own cache.             Replace the placeholders <IOServerName> and <IODeviceName> in the parameter with the actual names of the OPC I/O server and I/O device you want to override with a specific update rate.             This parameter controls polling performed by the OPC server, not by               Citect SCADA. The scope of the parameter is communication between the OPC server and a device, not between the OPC server and Citect SCADA. |
| UseAsyncWrites  | 0 - use synchronous writes. 1 - use asynchronous writes.     | 0                                                            | Determines whether writes are synchronous or asynchronous.**Note:** UseAsyncWrites=1 is only valid when [OPC]UseOPC2=1, since OPC1 does not support asynchronous writes. |
| UseOPC2         | 0 – Individual OPC2 support disabled (Use OPC 1.0a interface).             1 – Individual OPC2 support enabled (Use OPC DA2 interface). | Value of global UseOPC2 parameter                            | Allows user to individually override the global default [UseOPC2](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm) parameter and to specify whether to use OPC 1.0a or OPC 2.0 for a particular I/O device.             Replace the placeholders <IOServerName> and <IODeviceName> in the parameter with the actual names of the OPC I/O server and I/O device you want to override and have with a particular version OPC interface. |

#### OPC access path parameters     

In some instances, an OPC server might have several ways to access a particular item. For instance, a particular server, which communicates by means of modem, might have multiple modems at its disposal. It might be desired that certain items in the OPC server are always accessed using a particular modem, the fastest of the group, for example. OPC allows you to specify this preference by using the Access Path <**OPCAccessPath**> value.     

An access path is optional, provided in addition to the Item ID (the tag address), which is provided as a recommendation to the server, regarding how to access the data.     

**Note:** The availability, format, and use of access paths is server-specific. Refer to your OPC server documentation for details relevant to your server.     

[OPCAccessPaths]<IOServerName>.<IODeviceName>=<OPCAccessPath>    

where:     

- <IOServerName> = Name of I/O server configured in Citect SCADA .       
- <IODeviceName> = Name of I/O device configured for OPC communications.       
- <OPCAccessPath> = Access path to set up communications to the OPC server.       

This parameter is not normally required with most OPC servers.     

The Citect SCADA  OPC client driver supports specification of a single access path for each configured I/O device using the [OPCAccessPaths] section of the Citect.ini file.     

To specify the access path for a particular device, add an entry to the ini file in the format <**IOServerName**>.<**IODeviceName**>. For example, to specify that the access path COM1: should be used for the I/O device OPC1 on I/O server IOServer1, add the following entry to the Citect.ini file:     

[OPCAccessPaths]
IOServer1.OPC1=COM1:         

Multiple entries are also acceptable:     

[OPCAccessPaths]
IOServer1.PLC1=PLC4
IOServer1.PLC2=TestPLC 

#### OPC status tag parameters     

The OPC status tag parameters determine the online or offline state of an OPC I/O device using the condition of a specified OPC item in the device. For more information, see [OPC status tags](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_status_tags.htm).

When configuring these parameters, be careful not to confuse the OPC item required for status monitoring with a normal Citect SCADA tag. 

You should also use a full path to identify an OPC item, as a configured access path in your Citect.ini file  will not be known to a device. 

**Note:** Use the [UseStatusTags](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm) parameter to enable or disable support for OPC status tags.     

| [OPCStatusTags] Parameter | Allowable Values                          | Default Value                                                | Description                                                  |
| ------------------------- | ----------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| StartWait                 | time in milliseconds - or - –1 (infinite) | 30000 (milliseonds)                                          | On driver startup, this parameter determines the time the OPC driver will wait before requesting status tag data for an OPC I/O device. The OPC server should respond within a few seconds. The default wait time of 30 seconds is usually adequate. |
| Default.Tag               | An OPC item name                          | STATUS                                                       | This parameter  specifies the default OPC item to be monitored at runtime to determine the operational status of an associated device.**Note:** This parameter implements a global setting for all OPC I/O devices, unless it is specifically overridden using the equivalent [device-specific parameter](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm). |
| Default.Update            | 0 -32000 (milliseconds)                   | The scan rate from Address field in the Citect SCADABoards form | This parameter specifies the default update rate for OPC status tags at runtime. This is the frequency with which the OPC server polls the device for status tag values and then updates its own cache.This parameter controls polling performed by the OPC server, not by Citect SCADA. The scope of the parameter is communication between the OPC server and a device, not between the OPC server and Citect SCADA.**Note:** This parameter implements a global setting for all OPC I/O devices, unless it is specifically overridden using the equivalent [device-specific parameter](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm). |
| Default.Condition         | <condition>(see table below)              | ISGOOD                                                       | This parameter is used to determine if the OPC device is online at runtime, by comparing the <Condition> with the value of the default OPC item named in the .Default.Tag parameter. If the specified condition is determined to be true, the device will be considered online. This parameter represents the default condition for all OPC status tags, unless it is individually overridden using the [OPC device-specific parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm). |

| Allowable values for <condition>                             | Description                         |
| ------------------------------------------------------------ | ----------------------------------- |
| =<Value>                                                     | is equal to <Value>                 |
| !<Value>                                                     | is NOT <Value>                      |
| !=<Value>                                                    | is NOT equal to <Value>             |
| ><Value>                                                     | is greater than <Value>             |
| >=<Value>                                                    | is greater than or equal to <Value> |
| <<Value>                                                     | is less than <Value>                |
| <=<Value>                                                    | is less than or equal to <Value>    |
| ISGOOD                                                       | the tag Quality is GOOD             |
| ISBAD                                                        | the tag Quality is BAD              |
| ISUNCERTAIN                                                  | the tag Quality is UNKNOWN          |
| where **<Value>** is a placeholder for any valid LONG data type value. If the specified condition is determined to be true, the device will be considered online. |                                     |

#### OPC array parameters     

The support for arrays in the OPC client driver have been deprecated in Version 7. In order to carry out similar functionality you should use the procedures described in [Arrays Support](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_arrays_support.htm). 

### Configuring redundancy     

Redundancy is handled in Citect SCADA  by the Citect SCADA  clients. They determine which I/O server to request I/O device data from by allowing the scan rate to be specified per I/O device, and then configuring multiple I/O devices to the same PLC.     

A status tag can be defined in the Citect.ini file to determine whether or not to set a unit offline or online depending on the condition of the status tag. If the condition is true the unit is allowed to come online, otherwise the unit is set to offline.     

The status tag is polled at the same rate configured for the groups of the corresponding unit. The driver supports STATUS_UNIT commands on the inactive server, so even though a particular unit is not currently servicing Citect SCADA  requests, the state of the status condition will be checked periodically allowing the unit to be taken either offline or online (assuming that [IOServer]WatchDog has not changed from its default of 1).     

Both the primary and standby devices will be offline if both have the same status condition and the condition is an error condition. All points in the system for that unit would therefore be #COM.     

Status tags can be defined on a per-device or global basis.  For more information, see "[OPC status tag parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_status_tag_parameters.htm)" and "[OPC device-specific parameters](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/opc_device-specific_parameters.htm)". 

### Scan rates     

The Citect SCADA  OPC driver can define I/O devices with different scan rates. This provides you with the ability to better tune your system, by ordering the tag database into logical groups and defining different scan rates for each group. For example tags that are being read frequently can be placed in a group that is scanned frequently, and tags that are read infrequently can be placed in a group that is scanned infrequently.     

By default, tags are scanned at the default scan rate defined by the ScanRate parameter in the project Citect.INI file. See Citect.INI specific parameters for details.     

Examples     

Set the project scan rate to 1 second (1000 milliseconds):     

[OPC]
ScanRate=1000     

Set the project scan rate to 1 second (1000 milliseconds), and the inactive server scan adjust rate to a factor of 5:     

[OPC]
ScanRate=1000
Set a faster (half second) scan rate for a specific port named “Port1” on the I/O server named “CLServer”:     

[CLServer.Port1]
ScanRate=500     

Set a slower (5 second) scan rate for a specific port named “Port123” on the I/O port named “CLServer”:     

[CLServer.Port123]
ScanRate=5000 

### Tag-based driver considerations     

The Citect SCADA  OPC driver uses OIDs (object identifiers) to uniquely identify tag addresses. These OIDs are generated by Citect SCADA  during compilation.     

You should know how OIDs are implemented in a tag-based driver to minimize the possibility of  tag mismatches. especially if you’re using network distributed systems. For example, all Citect SCADA  servers and clients need to have exactly the same variable database on them, otherwise a client could make a request for a tag with an OID that does not exist on the I/O Server, or refers to a different tag. For this reason, care needs to be taken when editing a variables database.     

The following information highlights activities you should pay special consideration to due to the potential impact they might have on OIDs in your system.     

For details on OIDs, see the Citect SCADA  Knowledge Base article **Q3657**. 

#### Project IDs     

OIDs are generated using a Project ID, and the position (that is, record number) in the associated variable.dbf file. Therefore, when using Control Clients, standby servers, and so on that a project restored to a PC has a consistent Project ID in each machine included in a system.     

This should be checked when you restore a Citect SCADA  project to a PC, because if the Project ID is in use by another project on that computer, Citect SCADA  will generate a new Project ID number.     

A project’s ID number can be determined by selecting a project in Citect Explorer and viewing its properties. The Project ID is shown on the **General** tab. It is also stored in the project backup file (.ctz). 

#### Using Include projects     

Check that each Include project has the same Project ID on each computer using the same Include project. Check this after restoring a project to a computer. 

#### Variable databases     

If you have different variable.dbf files across your plant, you might have OID mismatches.     

To avoid this, check that after changing your variable.dbf on your primary server that you reset the OID (in citect.ini file set [OID] Reset=1) and do a pack and full compile (i.e., ensure that incremental compile is turned off).     

Then copy the variable.dbf file to the standby server and any Control Clients using the project. This sets the OID on your primary server to the same value as the OID used on your display client and/or standby server.     

**Note:** If you are using Include projects, pack your variable.dbf before resetting the OIDs and doing a full compile of your project. There is a downloadable tool available called **PackAll** that will pack the variable.dbfs that are used in your project (even if they are Include projects). You can find this tool under “Database Tools” in the **Toolbox** section of http://www.citect.com. 

## Troubleshooting     

A number of large projects will suffer 'bugs' in the run-time system. However, many problems have simple solutions and require only perseverance to solve them.     

The following topics provide information about the Citect SCADA  tools provided to help resolve problems with communication and configuration.     

- [Driver errors](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver_errors.htm)             
- [Logging](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/logging_opc.htm) 

### Driver errors     

Citect SCADA  OPC driver errors can occur when an OPC device does not respond, is disconnected or offline, or returns an error itself.     

The OPC driver can log combinations of trace levels across different categories. For more information, see [Logging](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/logging_opc.htm). 

#### Common protocol errors     

Citect SCADA  has two kinds of protocol driver errors - generic and specific. Generic errors are hardware errors 0-31, and are common to many protocols. Sometimes only the generic error is available, though often both the generic error and a specific error are given.     

Protocol drivers also have their own specific errors, which can be unique and therefore cannot be recognized by the hardware alarm system. The drivers convert specific errors into generic errors that can be identified by the I/O server. For example, when a driver experiences an error, there is often both a protocol-specific error and a corresponding generic error.     

When a hardware error occurs,Citect SCADA  generates an alarm, and displays the alarm on the hardware alarm page (in the alarm description of the hardware alarm). To see the error number, you need to have Alarm Category 255 defined with a display format that includes {ErrDesc,15} {ErrPage,10}.     

If you need more information to resolve an error, refer to the documentation that accompanied the I/O device (or network). If, after reviewing the documentation, you still cannot solve your problem, contact Technical Support for this product.

#### OPC protocol errors     

The following errors, listed in (hexadecimal) order, are specific to the Citect SCADA  OPC protocol:     



| Error Value (Hex) | Error Definition            | Error Description                                            |
| ----------------- | --------------------------- | ------------------------------------------------------------ |
| 0XC0040001        | GENERIC_SOFTWARE_ERROR      | Invalid handle was passed.                                   |
| 0XC0040002        | GENERIC_SOFTWARE_ERROR      | A duplicate parameter was passed where one is not allowed.   |
| 0XC0040004        | GENERIC_INVALID_DATA_FORMAT | Server cannot convert between the passed or requested data type and the canonical type. |
| 0xC0040006        | GENERIC_ACCESS_VIOLATION    | Item's access rights do not allow the operation.             |
| 0xC0040007        | GENERIC_SOFTWARE_ERROR      | Item definition does not exist within the server’s address space. |
| 0xC0040008        | GENERIC_SOFTWARE_ERROR      | Item definition does not conform to the server's syntax.     |
| 0xC004000B        | GENERIC_INVALID_DATA_FORMAT | Value passed to WRITE was out of range.                      |
| 0x80020008        | GENERIC_SOFTWARE_ERROR      | Bad variable type.                                           |
| 0x8002000A        | GENERIC_SOFTWARE_ERROR      | Out of present range.                                        |
| 0x80020005        | GENERIC_SOFTWARE_ERROR      | Type mismatch.                                               |
| 0x100             | GENERIC_SOFTWARE_ERROR      | Could not access variable dbf.                               |
| 0x101             | DRIVER_BAD_DATA             | Read of data value bad.                                      |
| 0x102             | GENERIC_GENERAL_ERROR       | Write of one or more items not completed.                    |
| 0x103             | DRIVER_UNIT_OFFLINE         | Could not resolve the server CLASSID.                        |
| 0x104             | GENERIC_SOFTWARE_ERROR      | Could not add one or more items to the Server                |
| 0x80010006        | GENERIC_CHANNEL_OFFLINE     | Connection terminated                                        |
| 0x80010007        | GENERIC_CHANNEL_OFFLINE     | Server not available.                                        |
| 0x8001000F        | GENERIC_INVALID_RESPONSE    | Received data is invalid.                                    |
| 0x80010012        | GENERIC_SOFTWARE_ERROR      | Call did not execute.                                        |
| 0x80010100        | GENERIC_SOFTWARE_ERROR      | System call aborted.                                         |
| 0x80010101        | GENERIC_SOFTWARE_ERROR      | Could not allocate some required resource.                   |
| 0x80010103        | GENERIC_BAD_PARAMETER       | Requested interface not registered on server object.         |
| 0x80010104        | GENERIC_SOFTWARE_ERROR      | Could not call server.                                       |
| 0x80010105        | GENERIC_CHANNEL_OFFLINE     | Server threw an exception.                                   |
| 0x80010108        | GENERIC_CHANNEL_OFFLINE     | Server has disconnected from its clients.                    |
| 0x8001011B        | GENERIC_CHANNEL_OFFLINE     | Access denied.                                               |
| 0x8001011C        | GENERIC_CHANNEL_OFFLINE     | Remote calls not allowed for this process.                   |

### Driver statistics     

You can use the following driver statistics to help you debug the OPC driver operation.     



| Statistic         | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
| Cached Reads      | Number of reads that have been serviced directly from the internal cache of current values. |
| Cache Misses      | Number of reads that were not in the internal cache of current values which resulted in a direct request from the server. |
| Active Items      | Number of items with valid server subscriptions which have been activated to receive data change notification. This may be a subset of the total number of items currently subscribed to. |
| Total Items       | Total number of items with valid server subscriptions. These items might or might not be currently activated to receive data change notifications. |
| Bad Items         | Number of items that were not successfully subscribed to. These items might not exist on the server. |
| Start ms          | Internal driver statistic used for driver debugging by Citect support engineers. |
| Last ms           | Internal driver statistic used for driver debugging by Citect support engineers. |
| Difference        | Internal driver statistic used for driver debugging by Citect support engineers. |
| ReadItemsReQueued | Internal driver statistic used for driver debugging by Citect support engineers. |
| DCBsInHandlingQ   | Internal driver statistic used for driver debugging by Citect support engineers. |
| DataNotYetValid   | Internal driver statistic used for driver debugging by Citect support engineers. |

### Logging     

OPC driver events are logged in the syslog.dat file. This file can be rolled over into a configurable backup file. The log file size and archiving are controlled by the following general [DEBUG] parameters in the citect.ini file:

- [Debug]ArchiveFiles
- [Debug]FlushPeriod
- [Debug]MaximumFileSize
- [Debug]SysLogSize

**Note:** In Citect SCADA v7.0 and earlier, this file was delivered to the Windows system directory (for example, C:\Windows) and its location was not configurable. With the release of Citect SCADA v7.10, the file is delivered to the location specified in the [CtEdit]Logs parameter, which is configurable.

The OPC driver also can log combinations of trace levels across different categories. This is achieved by setting the following ini parameters:     

- [DebugLevel](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm)             

- Allows you to define the trace level. The options include alerts, errors traces, or all of the above.

- [DebugCategory](mk:@MSITStore:C:\Program Files (x86)\AVEVA\Citect SCADA 2018 R2\Bin\OPC.chm::/OPC_driver-specific_citectini_parameters.htm)             

- Allows you to enable logging for a particular category of trace. The options include:

- | TAG   | Tag configuration trace                                  |
  | ----- | -------------------------------------------------------- |
  | PROT  | Operations related to the OPC protocol interface         |
  | CACHE | Operations related to the driver cache                   |
  | DCB   | Front end driver trace                                   |
  | MISC  | Miscellaneous operations                                 |
  | THRD  | Thread trace                                             |
  | BEND  | Operations related to the back-end thread of the driver  |
  | FEND  | Operations related to the front-end thread of the driver |
  | ALL   | All of the above                                         |

- **Note:** The more detailed the logging, the larger the amount of log data that will be generated. This could create a large, cumbersome log file, or cause multiple wraparounds that write over data. 

### Maintaining the project database     

Over time with editing, the project database underlying a project can become fragmented and performance can be reduced. During project development you should periodically clear out all duplicated records and any orphaned ones.     

Improperly maintained databases can result in communication errors at runtime. A large number of communications errors come from having duplicated or orphaned records in the communications database.     

Sometimes orphaned records from a previous I/O server are left behind in the database files. As the forms are indexed on the I/O server name, you can use the scroll bar to quickly navigate to the end of the current range of records for a particular I/O server and examine the last few and next few records to validate that they should be there. If you find extra (unwanted) records, delete them.     

You should also check that there are no duplicated records. Use the record search facility to search for duplicate entries of devices that are causing unexplained communication errors. If you find extra (unwanted) records, delete them.     

Once you have deleted orphaned and duplicated records, pack the project. Packing the database removes deleted records, and re-indexes the database. To pack the project databases, from the **File** menu in Citect Project Editor, choose **Pack**. 

## OPC Data Access Server Tag Browser

The OPC Data Access Server Tag Browser dialog generates the strings that the OPC Data Access Server database driver requires in Citect SCADA. 

The OPC Data Access Server Tag Browser dialog has the following fields:

**Machine Name**        

The location of the OPC Server which can be an IP address or the network path server. Leave blank to select the local machine.

**Database Tree Display**        

Displays the Servers on the network that are  running the OPC Server application, and the hierarchical database node  structure for each. 

Select a group of tags to import from an  available database. OPC data can be either a tree (hierarchical) or a  flat structure. The Citect SCADA OPC driver supports access to both types of storage. If the data is in a tree structure, it can be accessed to the first branch level down from  the root node. Deeper levels of branching may be supported in the  future.

**Note:** The authentication values needs to be valid for read/write access, as assigned by the appropriate database administrator. 