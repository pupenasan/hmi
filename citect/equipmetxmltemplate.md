# Import Equipment Using XML Templates

Equipment tags can be created by importing them in much the same way as tags can be imported using TagGen. An XML template is used to specify the fields of input and output  databases, and define filters and transformation rules that create tags  from existing database fields.

Equipment XML templates are configuration files that are linked with equipment types that you create (see Manually Define Equipment Types). Each equipment type can has an associated template file specified.

The Update Equipment tool (accessible via the Command Bar when **Equipment** is selected in the **System Model** activity) processes the template for each piece of equipment to manage the  associated configuration records. When updating the equipment  configuration, the associated records are updated by modifying, adding  or deleting as required. 

For example, a set of associated records defined by the template may consist of a set of variable tags, alarms  and trends. When an equipment record is added, the update tool will  create the associated records. If the template is modified, the update  tool will modify the associated records. If the equipment record is  deleted, the update tool will delete the associated records.

## Equipment XML Template

The equipment template is an XML file that uses proprietary tags and attributes to specify the fields of input and  output databases, and define filters and transformation rules that  create tags from existing database fields. It uses the existing TagGen syntax rules.

The template file is linked to a specific equipment type. Equipment types can be supplied from different sources:

- The SCADA product 
- An add-on pack
- External library
- User-defined. 

Types defined by your project should use a  project specific prefix to avoid conflicting with templates from another source. You should not use 'SE' or 'LIB' as prefixes for your template  type names to avoid conflict with future product supplied templates.

It is recommended that the template file name  should use the corresponding equipment type name for consistency. When  adding the template to your project, the equipment type name should be  the type name used by the template (see Parameters).

An equipment template XML file consists of five sections:

- Header            
- Parameters            
- Input            
- Outputs            
- Footer            

Sample template files are located in the example project directory, and include `Building Level.xml`, `Building Light Dimmer.xml`, `Building Light.xml`, `Building Room.xml`, `Plant  Level.xml`, `Plant Light.xml`, and `Plant Line.xml`.

### Equipment Templates: Header 

The template (XML) file should contain the header section that defines the:

- version
- start of the template node
- template description

The example below can be used without  modification. However the header should reflect the actual encoding and  the characters used. There are two ways to achieve this, either:

-  change the encoding in the header e.g. to iso-8859-1 (latin-1) if using ANSI characters.
  or

- change any ANSI characters used to their Unicode equivalent.

Example

```xml
<?xml version="1.0" encoding="utf-8"?>
<template desc="Equipment template">
```

### Equipment Templates: Parameters 

The template (XML) file needs to contain a  parameter section that defines the equipment type parameter. Other  parameters can be added within this node as needed. Refer to the  advanced section below or the [`TagGen`](taggenxmltemplate.md) help topic in the product help  for additional information.

The parameter string is used to define the  template type name that is referenced in other parts of the template  file. To use the example below, replace:

- `[Type]` with the name of your equipment type. This should be unique across the  templates used in your project(s). It needs to match the value specified in the name field of the record that defines the template type in the  project.
- `[TypeRef]` with an abbreviation (if required) of the type name. This is recommended to be less than  16 chars. When using an abbreviation, it should follow the same rules as the type name, such that it has to be unique across the templates used  in your project(s).

Example

```xml
  <param name="type" desc="equipment type parameters">
    <string name="name">[Type]</string>
    <string name="ref">[TypeRef]</string>
  </param>
```

### Equipment Templates: Input 

The template (XML) file should contain an input section that defines the input node for the equipment database (DBF)  file source. The input node is defined within the XML template node and  contains the list of database fields that are to be available for use by the template. Only one input node can to be defined within the  template.

The example below can be used without  modification and lists the complete set of the available data fields  from the equipment database (DBF) file.

There are three built-in functions that can be used to manipulate strings in the XML template: 

- SubString(string, start, count) 
- Split(string, delimiter) 
- ToProperty(string, separator, delimiter) 

These functions are the same as used in the TagGen XML templates and are described in Built-in Functions. 

Example

```xml
  <!-- ===================================================
    Input Section - Equipment
  ===================================================
  -->
  <input name="equipment" file="equip.dbf" desc="Equipment Database">
    <field name="name"></field>
    <field name="cluster"></field>
    <field name="type"></field>
    <field name="iodevice"></field>
    <array name="iodevice_list">{Split('{iodevice}',',')}</array>
    <field name="tagprefix"></field>
    <field name="area"></field>
    <field name="page"></field>
    <array name="page_list">{Split('{page}',',')}</array>
    <field name="help"></field>
    <field name="location"></field>
    <field name="comment"></field>
    <field name="scheduled"></field>
    <field name="defstate"></field>
    <field name="param"></field>
    <array name="param_list">{ToProperty('{param}','=',';')}</array>
    <field name="custom1"></field>
    <field name="custom2"></field>
    <field name="custom3"></field>
    <field name="custom4"></field>
    <field name="custom5"></field>
    <field name="custom6"></field>
    <field name="custom7"></field>
    <field name="custom8"></field>
  </input>
```

### Equipment Templates: Outputs 

The template (XML) file can contain 1 or more  output sections that define the configuration records that are to be  created in other database (DBF) files. The output nodes are defined  within the template node and contain the list of database fields that are to be updated in the new record. An Output Node should be added for each record that is to be created, such as a variable tag, alarm, trend, etc.

The values specified for each of the Output Field elements will be written to the database (DBF) field of the output  file. Values from input fields and parameter strings can be referenced  within this section to construct the resulting value for the output record field. Each output node should have a unique output name specified across the records in the template.

Refer to the following available output databases section for specific details on each of the available output  databases and other advanced topics.

The example below shows a sample for an output  to the variable database (DBF). For each output section, the field names specified should include the Output Common fields and the fields specific to each Output Database.

To use the example below, replace the following in your template:

- [FileRef] with a short  string reference for the output destination database. Such as 'Var',  'Trend', 'AlmDig', 'Menu', etc. Examples are provided with the list of  available databases
- [RefID] with a unique  index (1, 2, 3, etc.) or a related string value for the entry (such as  ON, STOP, etc.) for the specific output record. 
- [TypeRef] with the  abbreviation of the type name as defined in the parameter section. This  may need to be an abbreviation of the full type name as the total length of [TypeRef].[RefID] should be 32 chars or less to fit the 'taggenlink' field. 

Example

```xml
  <!-- ===================================================
  Output Section - <my variable tag>
  ===================================================
  -->
  <output name="[FileRef].[RefID]" file="variable.dbf" filter="'{equipment.type}={type.name}'">
    <field name="taggenlink" load="true">[TypeRef].[RefID]</field>
    <field name="linked">1</field>
    <field name="editcode">11</field>

    <field name="name" key="true">{equipment.tagprefix}[Tag Suffix]</field>
    <field name="type">[Tag Data Type]</field>
    <field name="unit">{equipment.iodevice_list[0]}</field>
    <field name="addr">[Tag Address]</field>
    <field name="comment">[Tag Comment]</field>
    </output>
```

### Equipment Templates: Output Node

The output node contains the following attributes:

- **Output Name** The output node name attribute  should be unique across the output nodes in the template. One way to  achieve this consistently is to use the format of [FileRef]. [RefID] (as outlined in Equipment Templates: Outputs). The recommended value for [FileRef] is listed with each output database.
- **Output File** The output node file attribute refers to the filename for the associated database (DBF) file.
- **Output Filter** The output node filter attribute is  used to match the equipment defined in the equipment database (DBF). The filter value needs to match the type name specified in the type filed  of the equipment. The recommend value for the filter is the parameter  string for the type defined at the beginning of the template file. Each output node defines the associated Output Common fields and Output Database fields for the record that is to be created.

### Equipment Templates: Output Field

The output node fields can reference the values from the associated equipment input record. The following is a list of  the fields that can be used based on the input section of the template  (XML) file. The value is referenced using the syntax  `{equipment.<Field Name>}` where `<Field Name>` can be used  from the list below:

| Input Name       | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| Area             | The required area                                            |
| Cluster          | The associated cluster                                       |
| Comment          | The configuration comment                                    |
| custom1 .. 8     | The custom runtime fields                                    |
| Defstate         | The default state for the scheduler                          |
| Help             | The help reference                                           |
| Iodevice         | The list of IO devices                                       |
| iodevice_list[n] | The array of IO devices, where n in the zero based index     |
| Location         | The location reference                                       |
| Name             | The full equipment name                                      |
| Page             | The list of pages                                            |
| page_list[n]     | The array of pages, where n in the zero based index          |
| Param            | The list of parameters                                       |
| param_list[name] | The list of parameters, where name is the specific parameter name |
| scheduled        | The configuration of scheduler participation                 |
| Tagprefix        | The prefix for the associated tags                           |
| Type             | The equipment type                                           |


### Equipment Templates: Output Common Fields

There are three common fields that should be used with each output node:

- **Output Tag Gen Link**. The taggenlink field specifies a  name that is used to identify the record in the database so that it is  linked with the template. This allows the record to be found for an update or delete operation.

  The value should include a unique  reference to the template type and a reference to the output record  within the template. The recommended way to achieve this consistently is to use the format of [TypeRef].[RefID] (as outlined in Template  Section: Outputs).
- **Output Linked** The linked field should be set to '1'.
- **Output Edit Code** The edit code is a number that represents the bitmask of the database (DBF) fields based on the physical order in the DBF file. When the bit in the mask is set, the corresponding field will be marked read-only in the Project activity. If no fields are to be marked as read only, this field can be left blank or removed from the output definition.

The algorithm to determine an edit code is listed in Equipment Templates: Output Database. The combined edit code for few fields is a sum of edit codes of all fields. For example, the edit code for first (edit code = 1), second (edit code = 2), fourth (edit code = 8) and 20th fields (edit code = 524288)  is 1 + 2 + 8 + 524288 = 524299, or in decimals: 0x00001 (edit code for first field) + 0x00002 (edit code for second field) + 0x00008 (edit code for third field) + 0x80000 (edit code for 20th field) = 0x8000B 

### Equipment Templates: Output Database

Below is a list of available output databases  and the corresponding output files and output file references to use in  your equipment template.

| Database                    | Output File         | Output File Reference |
| --------------------------- | ------------------- | --------------------- |
| Accumulators                | file="accums.dbf"   | Accum                 |
| Advanced Alarms             | file="advalm.dbf"   | AdAlm                 |
| Alarm Categories            | file="category.dbf" | ACat                  |
| Analog Alarms               | file="anaalm.dbf"   | AAlm                  |
| Devices                     | file="devices.dbf"  | Dev                   |
| Digital Alarms              | file="digalm.dbf"   | DAlm                  |
| Equipment                   | file="equip.dbf"    | Equip                 |
| Equipment States            | file="eqstate.dbf"  | State                 |
| Events                      | file="events.dbf"   | Event                 |
| Fonts                       | file="fonts.dbf"    | Font                  |
| Groups                      | file="groups.dbf"   | Group                 |
| Labels                      | file="labels.dbf"   | Label                 |
| Local Variables             | file="locvar.dbf"   | LVar                  |
| Menu Configuration          | file="pagemenu.dbf" | Menu                  |
| Multi-digital Alarms        | file="argdig.dbf"   | MDAlm                 |
| Parameters                  | file="param.dbf"    | Param                 |
| ReMapping                   | file="remap.dbf"    | Remap                 |
| Reports                     | file="reports.dbf"  | Rep                   |
| SPC Tags                    | file="spc.dbf"      | SPC                   |
| Time Stamped Alarms         | file="hresalm.dbf"  | TSAlm                 |
| Time Stamped Analog Alarms  | file="tsana.dbf"    | TAAlm                 |
| Time Stamped Digital Alarms | file="tsdig.dbf"    | TDAlm                 |
| Trend Tags                  | file="trend.dbf"    | Trend                 |
| Variable Tags               | file="variable.dbf" | Var                   |

To determine acceptable field names for Tags and Alarms

To determine the acceptable field names and,  respective edit codes, either open citect.frm and find the respective  output file without an extension (for example, advalm for advanced  alarms) or open the respective dbf in the DBF Add-In. Every field listed in the dbf are acceptable field names. The edit code of the first field in the table is initialized to 1. The edit code of the fields other  than 1 equals the edit code of the previous field times 2 (i.e. the edit code of the second field is 2, third is 4, fourth is 8 and so on).

### Equipment Templates: Footer 

The template (XML) file should contain a footer section to help so that the XML is formatted correctly. The footer  contains the end marker for the template node. The example below can be used without modification.

Example

```xml
</template>
```

### Calculator Examples 

The following examples  demonstrate five cases where the calculator function could be applied to an equipment XML template. In each case, you need to add an additional  line to the XML template:

```xml
<calculator>{parameter} + 1</calculator>
```

1. Calculator based on string parameter in the input section of the XML. This is only recommended if  the calculated parameter is constant for each instance of equipment for  this type; however, this is not a typical scenario.

   ```xml
   <string name="MyString">1000</string>
   <calculator name="MyCalc">{MyString} + 1</calculator>
   ```

2. Calculator based on equipment field, for example, `{equipment.Custom1}`.

   ```xml
   <calculator name="MyCalc">{equipment.Custom1} + 1</calculator>
   ```

3. Calculator based on ungrouped parameter (defined in Equipment Editor).

   ```xml
   <calculator name="MyCalc">{equipment.param_list[Param1]} + 1</calculator>
   ```

4. Calculator based on grouped parameter (defined in Equipment Editor).

   ```xml
   <calculator name="MyCalc">{equipment.ParamGroup[Param2]} + 1</calculator>
   ```

   These can then be used in fields for an element:

   ```xml
   <field name="addr">MW_{MyCalc}_2</field>
   ```

5. Calculator based on grouped parameter (in the output section).

   ```xml
   <output name="Element" file="variable.dbf" filter="'{equipment.type}={type.name}'">
   	<calculator name="TagAddress">
           {equipment.TagAddressing[StructOffset]} + 0
       </calculator>
   ...
   </output>
   ```

6. These can then be used in fields for an element:

   ```xml
   <field name="addr">MW_{MyCalc}_2</field>
   ```

   

#### Example 1 - Type with Calculator based on STRING

```xml
<?xml version="1.0" encoding="utf-8"?>
      <template desc="">
        <param name="type">
        <string name="name">TypeWithCalc</string>
        <string name="ref">TypeWithCalc</string>
        <string name="blank"></string>
        <string name="wildcard"></string>
        <string name="parameter-definitions">param_list.param1=;Addr.BaseAddr=</string>
        </param>
        <input name="equipment" file="equip.dbf" desc="Equipment Database">
        <field name="PARAM" />
        <field name="TAGPREFIX" />
        <field name="IODEVICE" />
        <field name="CLUSTER" />
        <field name="NAME" />
        <field name="AREA" />
        <field name="LOCATION" />
        <field name="COMMENT" />
        <field name="CUSTOM1" />
        <field name="CUSTOM2" />
        <field name="CUSTOM3" />
        <field name="CUSTOM4" />
        <field name="CUSTOM5" />
        <field name="CUSTOM6" />
        <field name="CUSTOM7" />
        <field name="CUSTOM8" />
        <field name="PAGE" />
        <field name="HELP" />
        <field name="DEFSTATE" />
        <field name="SCHEDULED" />
        <field name="COMPOSITE" />
        <field name="TYPE" />
        <array name="param_list">{ToProperty('{param}','=',';')}</array>
        <array name="Addr">{ToProperty('{equipment.param_list[Addr]}',':',',')}</array>
        <string name="MyAddrString">250</string>
        <calculator name="myaddrcalc">{MyAddrString}+5</calculator>
        </input>
        <output name="Element" file="variable.dbf" filter="'{equipment.type}={type.name}'">
        <field name="NAME" key="true">{equipment.TAGPREFIX}_Tag1</field>
        <field name="TYPE">INT</field>
        <field name="UNIT">{equipment.IODEVICE}</field>
        <field name="ADDR">{myaddrcalc}</field>
        <field name="ENG_ZERO">0</field>
        <field name="ENG_FULL">1000</field>
        <field name="CLUSTER" key="true">{equipment.CLUSTER}</field>
        <field name="EQUIP">{equipment.name}</field>
        <field name="ITEM">Tag1</field>
        <field name="TAGGENLINK" load="true">TypeWithCalc_0006</field>
        <field name="LINKED">1</field>
        <field name="EDITCODE">3938511</field>
        </output>
      </template>
```

#### Example 2 - Type with Calculator based on Equipment Field

```xml
<?xml version="1.0" encoding="utf-8"?>
    <template desc="">
       <param name="type">
       <string name="name">TypeWithCalc</string>
       <string name="ref">TypeWithCalc</string>
       <string name="blank"></string>
       <string name="wildcard"></string>
       <string name="parameter-definitions">param_list.param1=;Addr.BaseAddr=</string>
       </param>
       <input name="equipment" file="equip.dbf" desc="Equipment Database">
       <field name="PARAM" />
       <field name="TAGPREFIX" />
       <field name="IODEVICE" />
       <field name="CLUSTER" />
       <field name="NAME" />
       <field name="AREA" />
       <field name="LOCATION" />
       <field name="COMMENT" />
       <field name="CUSTOM1" />
       <field name="CUSTOM2" />
       <field name="CUSTOM3" />
       <field name="CUSTOM4" />
       <field name="CUSTOM5" />
       <field name="CUSTOM6" />
       <field name="CUSTOM7" />
       <field name="CUSTOM8" />
       <field name="PAGE" />
       <field name="HELP" />
       <field name="DEFSTATE" />
       <field name="SCHEDULED" />
       <field name="COMPOSITE" />
       <field name="TYPE" />
       <array name="param_list">{ToProperty('{param}','=',';')}</array>
       <array name="Addr">{ToProperty('{equipment.param_list[Addr]}',':',',')}</array>
       <string name="MyAddrString">250</string>
       <calculator name="myaddrcalc">{equipment.CUSTOM1}+5</calculator>
       </input>
       <output name="Element" file="variable.dbf" filter="'{equipment.type}={type.name}'">
       <field name="NAME" key="true">{equipment.TAGPREFIX}_Tag1</field>
       <field name="TYPE">INT</field>
       <field name="UNIT">{equipment.IODEVICE}</field>
       <field name="ADDR">{myaddrcalc}</field>
       <field name="ENG_ZERO">0</field>
       <field name="ENG_FULL">1000</field>
       <field name="CLUSTER" key="true">{equipment.CLUSTER}</field>
       <field name="EQUIP">{equipment.name}</field>
       <field name="ITEM">Tag1</field>
       <field name="TAGGENLINK" load="true">TypeWithCalc_0006</field>
       <field name="LINKED">1</field>
       <field name="EDITCODE">3938511</field>
       </output>
      </template>
```

#### Example 3 - Type with Calculator based on Ungrouped and Grouped Parameter

```xml
<?xml version="1.0" encoding="utf-8"?>
      <template desc="">
        <param name="type">
        <string name="name">TypeWithCalc</string>
        <string name="ref">TypeWithCalc</string>
        <string name="blank"></string>
        <string name="wildcard"></string>
        <string name="parameter-definitions">param_list.param1=;Addr.BaseAddr=</string>
        </param>
        <input name="equipment" file="equip.dbf" desc="Equipment Database">
        <field name="PARAM" />
        <field name="TAGPREFIX" />
        <field name="IODEVICE" />
        <field name="CLUSTER" />
        <field name="NAME" />
        <field name="AREA" />
        <field name="LOCATION" />
        <field name="COMMENT" />
        <field name="CUSTOM1" />
        <field name="CUSTOM2" />
        <field name="CUSTOM3" />
        <field name="CUSTOM4" />
        <field name="CUSTOM5" />
        <field name="CUSTOM6" />
        <field name="CUSTOM7" />
        <field name="CUSTOM8" />
        <field name="PAGE" />
        <field name="HELP" />
        <field name="DEFSTATE" />
        <field name="SCHEDULED" />
        <field name="COMPOSITE" />
        <field name="TYPE" />
        <array name="param_list">{ToProperty('{param}','=',';')}</array>
        <array name="Addr">{ToProperty('{equipment.param_list[Addr]}',':',',')}</array>
        <calculator name="myaddrcalc">{equipment.param_list[param1]}+5</calculator>
        <calculator name="myaddrcalc2">{equipment.Addr[BaseAddr]}+10</calculator>
        </input>
        <output name="Element" file="variable.dbf" filter="'{equipment.type}={type.name}'">
        <field name="NAME" key="true">{equipment.TAGPREFIX}_Tag1</field>
        <field name="TYPE">INT</field>
        <field name="UNIT">{equipment.IODEVICE}</field>
        <field name="ADDR">MW{myaddrcalc}_2</field>
        <field name="ENG_ZERO">0</field>
        <field name="ENG_FULL">1000</field>
        <field name="CLUSTER" key="true">{equipment.CLUSTER}</field>
        <field name="EQUIP">{equipment.name}</field>
        <field name="ITEM">Tag1</field>
        <field name="TAGGENLINK" load="true">TypeWithCalc_0006</field>
        <field name="LINKED">1</field>
        <field name="EDITCODE">3938511</field>
        </output>
      </template>
```

#### Example 4 - Type with Calculator in Output Section

```xml
<?xml version="1.0" encoding="utf-8"?>
	<template desc="">
	  <param name="type">
          <string name="name">TypeWithCalculator</string>
          <string name="ref">TypeWithCalculator</string>
          <string name="blank"></string>
          <string name="wildcard"></string>
          <string name="parameter-definitions">TagAddressing.PLC.DBNumber=;TagAddressing.StructOffset=</string>
	  </param>
        
	  <input name="equipment" file="equip.dbf" desc="Equipment Database">
          <field name="PARAM" />
          <field name="TAGPREFIX" />
          <field name="NAME" />
          <field name="IODEVICE" />
          <field name="CLUSTER" />
          <field name="AREA" />
          <field name="LOCATION" />
          <field name="COMMENT" />
          <field name="CUSTOM1" />
          <field name="CUSTOM2" />
          <field name="CUSTOM3" />
          <field name="CUSTOM4" />
          <field name="CUSTOM5" />
          <field name="CUSTOM6" />
          <field name="CUSTOM7" />
          <field name="CUSTOM8" />
          <field name="PAGE" />
          <field name="HELP" />
          <field name="DEFSTATE" />
          <field name="SCHEDULED" />
          <field name="COMPOSITE" />
          <field name="TYPE" />
          <array name="param_list">{ToProperty('{param}','=',';')}</array>
          <array name="TagAddressing">{ToProperty('{equipment.param_list[TagAddressing]}',':',',')}</array>
	  </input>
        
	  <output name="Element" file="variable.dbf" filter="'{equipment.type}={type.name}'">
          <calculator name="TagAddress">
              {equipment.TagAddressing[StructOffset]} + 0
          </calculator>
          <field name="NAME" key="true">{equipment.tagprefix}_Enable</field>
          <field name="EQUIP">{equipment.name}</field>
          <field name="UNIT">{equipment.iodevice}</field>
          <field name="CLUSTER" key="true">{equipment.cluster}</field>
          <field name="TYPE">DIGITAL</field>
          <field name="COMMENT">Machine Enable</field>
          <field name="ADDR">
              DB{equipment.TagAddressing[PLC.DBNumber]},{TagAddress}.0
          </field>
          <field name="ITEM">Enable</field>
          <field name="TAGGENLINK" load="true">12345</field>
          <field name="LINKED">1</field>
          <field name="EDITCODE">3939343</field>
	  </output>
	</template>
```

## Troubleshooting - Equipment XML Templates 

**After running an equipment update there are no records created in the output database files.**        

Check that the type name defined in the first parameter of the template file is the same as the name defined for the equipment type record of the project.

**After running an equipment update there are duplicate records in the output database files.**        

Check that the 'taggenlink' field in the output section of the template was not changed. When this field is changed, any previously generated entries need to be manually deleted.

After running an equipment update some tags were not created. Is there a log file I can check?

You can check the log file called EquipGen.log; however you should set the ini parameter `[CtEdit]LogLevel` to turn it on.

`[CtEdit]LogLevel` increases the verbosity of the log file so that more information can be recorded. The following values are accepted:

```ini
Error=3
Summary=5
Details=10
Verbose=15 (set this to 15 when more detailed logging relating to EquipGen is required.)
```

The log file is located in the default log directory which is set using `[CtEdit]Logs`. To access the log file, in Citect Studio select **Log Folder** from the System menu. 

**Note:** If you leave LogLevel on during runtime, it can affect system performance as other logging functions may be impacted.

**What happens if the Equipment type XML file is corrupted?**        

When the equipment type is saved in the  Equipment Editor, a file called `EquipType.xml.backup` is created. This  file is of the previous configuration before the last save.  If the XML  file is corrupted, it can be replaced with the `xml.backup` file.

