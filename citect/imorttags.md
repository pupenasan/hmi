# Import Variable Tags  from an External Data Source

Importing tags from an external data source allows you to program an I/O device and then import the tags straight into Citect SCADA, where they are treated as regular tags. Citect SCADA will automatically create a variable tag records for every tag in the I/O device.

**Note:** Citect SCADA only supports the use of alphanumeric characters, the backslash and underscore characters (see [Tag name syntax](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Tag_Name_Syntax.html)). Any other characters will be converted to underscores on import. This  may result in Duplicate Tag error messages on compilation.

#### About Importing Variable Tags

Like linking, importing tags is an I/O device specific operation: you import the tags for a particular  I/O device. Unlike linking, however, imported tag records are not linked in any way to the tags in the external data source. Therefore,  importing is typically a one-time operation. To update imported tags,  you need to import them again. 

**Note:** Tags  will be imported into the project in which the selected I/O device is  defined. This could be either the selected project or one of its  included projects. 

For most external data sources, the import process involves two steps. First you export the data from  the I/O device to a format that Citect SCADA can read, then you import the database into Citect SCADA. However, tag data saved using `Mitsubishi` or `Unity FastLinxUnity Pro` can be read directly by Citect SCADA. This means that no export is necessary.

Some characteristics of the import are defined in the format files in the `Config` directory (with the extension `.fmt`). There is one format file for each database type, and each file specifies how external data is converted to Citect SCADA variable data. In general, imported tags are either added to the Citect SCADA variable database if the tag does not already exist, or updated if the tag exists. However, if a field is listed in the `[EditableFields]` section of the format file corresponding to the import database type:        

- If the tag already exists, the Citect SCADA field for the tag will not be updated with the external value.
- If the tag does not yet exist, the Citect SCADA field for the tag will be updated with the external value.

For example, if a tag has 10  fields to be imported and five of them are listed in the  [EditableFields] section of the format file, then if the tag already  exists in Citect SCADA the tag  will be updated with the external values for the five fields that are  listed in [EditableFields]. If the tag does not already exist then the  tag will be created with the external values for every 10 fields.

Fields marked as editable in this way can be changed by Citect SCADA. To avoid internal changes being lost, changes to these fields in the external database are ignored.

**Note:** If the external database supports to LiveUpdate and the **LiveUpdate Link** has been selected for the I/O device, existing Citect SCADA tags will be synchronized with the external database and the tags will  be updated for the imported fields regardless of whether it is  marked  as an editable field. An I/O device configured as **Linked** or **Auto-refreshed Linked** will behave as in a normal import and will not update fields marked as editable.

When you import tags into Citect SCADA, you have two options for dealing with existing tags:

- Delete tags associated with that I/O device prior to the import.
- Update existing tags on import. Tags found in Citect SCADA and in the external data source are updated in Citect SCADA. Tags found in Citect SCADA but not in the external data source will remain untouched. New tags are appended.

If you import a data source  that is already linked, every tag in the data source are duplicated.  That is, you will have two copies of each tag: one local and one linked.

See [Imported Tags](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Imported_Tags.html) for information about levels of support between Unity and Citect SCADA.

Some properties defined for the external tags will not be relevant to Citect SCADA. Also, some will not be in a format that Citect SCADA can read. To define what information is copied to Citect SCADA's variable tags database and how this information is to be converted, you need to edit the I/O device's format file.

To import variable tags from an external database:

1. In the **Topology** activity, select **I/O Devices**.
2. On the Command Bar, select **Import Tags**.
3. Complete the **Import Variable Tags** dialog box.
4. See Import Variable Tags Properties below for a description of the information required in each field. 

#### Import Variable Tags Properties

| Property                                        | Description                                                  |
| ----------------------------------------------- | ------------------------------------------------------------ |
| **I/O Device**                                  | **Note:** If an I/O device is linked to an external data source the Database  Type, External Database, Connection String, and Tag Prefix fields will  be greyed out. The Import Variable Tags dialog has the following fields: The I/O Device for which you are importing tags. Use the menu to select an I/O Device that has been defined using Citect SCADA. **Note:** Tags will be imported into the project in which the selected I/O Device is defined. This could be either the project selected in the Explorer,  or in one of its included projects. |
| **Database type**                               | The format of the data referenced by the external data source. |
| **External database**  (128 Chars.)             | References the  source for the external database. Click the Browse button to either  navigate to the file or to specify configuration options. The external  database can be:    <br />- An explicit path and file (for example, "C:\Data\Tags.csv")    <br />- An IP address and node (for example, "127.0.0.1\HMI_Scada")    <br />- A URL (for example "http://www.abicom.com.au/main/scada")    <br />- A computer name (for example "\\coms\data\scada").<br />Tag data can be read directly from a `Unity SpeedLink` or `OPC Factory ServerUnity` or `Mitsubishi Fastlinx` data sources. Click the browse button to specify configuration options. See [OPC Factory Server Tag Import](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/OFS_Tag_Import.html), [FastLinx for Mitsubishi Tag Import](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/FastLinx_for_Mitsubishi_Tag_Import.html), or [Unity Link Tag Import](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Unity_Link_Tag_Import.html). |
| **Connection string** (128 Chars.)              | Connection details for the data source. This is similar to an ODBC connection string. For example:<br />`UserID = XXX; Password = YYY` <br />or <br />`ServerNode=111.2.3.44; Branch=XXX` <br />Only certain drivers require a connection string:            <br />- Mitsubishi FastLinx                <br />- Unity Fastlinx (Static/Dynamic)<br />- Unity SpeedLink (Static/Dynamic)<br />- Unity SpeedLink (Static/Dynamic)    <br />- OPC<br />Selecting one of  these drivers and then browsing for the external database will  automatically populate the Connection String field where necessary. |
| **Add prefix to imported tags**                 | Select this box to insert a prefix in front of the names of imported tags in your *Variable*.DBF. |
| **Tag prefix**                                  | The prefix (8 characters max.) that is inserted in front of the names of imported tags in the variable tags database. |
| **Delete I/O Device tags prior to import**      | Select this box to delete every one of the I/O Device's tags (from the variable tags database) before importing.If this check box is not selected, tags found in Citect SCADA and in the external data source are updated in Citect SCADA. Tags found in Citect SCADA but not in the external data source remain untouched. New tags are appended. |
| **Purge deleted tags not found in data source** | Select this box to  delete tags which have been removed from the external database. In other words, if a tag is still part of the I/O Device in your project, but  not in the external database, it is deleted from your project. |



## Unity Link Tag Import

The Unity Link Configuration dialog specifies the parameters used to generate alarm and trend tags. It has the following fields:

#### I/O Device & Protocol Driver

The name of the destination I/O Device and its corresponding protocol. Unity SpeedLink, SpeedLinkFastLinx will only import tags to an I/O Device using either the MODBUS, MODNET, MBPLUS, or UNITE. 

#### Unity Database Type

The import/export database driver type selected from the Import Variable Tags dialog.

#### PLC Family

The family  name of the PLC you are importing from. It can be either Premium or Quantum. This option is only valid for the Unity SpeedLink, SpeedLinkFastLinx Static protocol.

#### Unity File

Path of the Unity project file from which you want to import the tags. 

- If the database type is Unity SpeedLinkSpeedLinkFastLinx Dynamic, this is a .stu file. 
- If the database type is Unity SpeedLinkSpeedLinkFastLinx Static, this is a .xsy file.

#### Unity Profile Enable

Enable this if the Unity database is restricted by user profile and a user  name and password combination are needed to gain access. See the Access  Security Management section of the Unity Pro online help for further  information. 

#### Unity Username and Password

The username and password, if it is necessary, for the Unity database from which you are importing.

#### DCOM Enable

Enable this if the database host is a DCOM server.

#### DCOM Server Name

If enabled, the DCOM server that the client uses to hosts the database from which you are extracting tags.

#### DCOM Username and Password

If enabled, the username and password for the DCOM server.

#### Tag Gen Configuration Enable

Enable this to automatically generate tags from the variable Tags database.  Tags are created using rules specified in the XML template file.

#### Configured template is saved as

Filename of the [TagGen XML Template](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/TagGen_XML_Template.html) file that specifies the rules for generating tags. Click Configure to select and configure the XML file. See [Additional Tag Generation Configuration](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Additional_Tag_Generation_Configuration.html).

#### Log File Path

The path name for log files generated during the import or export process.

#### Logging Level

The level of detail necessary in the import or export logs.

#### Log Pool Size

Specifies the maximum number of log files for the given device.

#### Validate

Click the validate button to check the Unity Link settings are correct. This button enables the OK button on the page. 

#### Additional Tag Generation Configuration

This dialog specifies the path of the XML  template, the parameters specified in the template, and displays the  template description (extracted from the `desc` attributes used in the template).

1. Click **Browse** to select the XML file to use.
2. Double click on a parameter in the parameters list to change its value.
3. Click **OK** to save this template into your project. The template will be copied into the project and, when validated, saved with a `taggen_import_`*ioDeviceName*`.xml` or `taggen_link_`*ioDeviceName*`.xml` filename.
4. **Note:** When you return to this dialog, the path name will point to the location of  the template in the project, rather than the path of the original  template file.

