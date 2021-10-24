## TagGen XML Template

The TagGen template is an XML file that uses  proprietary tags and attributes to specify the fields of input and  output databases, and define filters and transformation rules that  create tags from existing database fields. The basic structure of the XML file is as follows:

```xml
<?xml version="1.0"?>
<template>
  <param name="parameter"> </param>
  <input name="variable" file="variable.dbf"> </input>
  <output name="trend" file="trend.dbf" filter=""> </output>
</template>
```

This outline template specifies no parameters,  takes input from the variable.dbf database and outputs the results to  the trend.dbf database. The `<template>` tag is the root tag of the template document and need to be present.

Within the `<template>` tag are three sections:

- `<param>`
- This is an optional section you can use to specify string constants that can be referred to in other sections of  the template. For example: 

- ```xml
  <param name="parameters">
  	<string name="MyIODevice">DISK_PLC</string>
  </param>
  ```

-  In this example the variable *MyIODevice* is given the value DISK_PLC. 

- The `<param>` tag has a *name* attribute. You can use any name provided that it uniquely identifies  the section within the XML file. This section name is used when  referring to variables from other sections of the file. See [Referencing variables](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Referencing_Variables.html). 

- Strings defined here are displayed in the [Additional Tag Generation Configuration](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Additional_Tag_Generation_Configuration.html) dialog when templates are selected. It is possible to define strings  that are otherwise not used in the template to specify version or  revision information in order to track template modifications. 

- `<input>`
- The `<input>` section specifies the name of the database and the fields that are used for processing into tags. There needs to be only one input section in  the XML file. For example: 

- ```xml
  <input name="variable" file="variable.dbf">
  <field name="name"></field>
  <field name="type"></field>
  <field name="unit" load="true">{parameter.IODevice}</field>
  <field name="custom"></field>
  <array name="taginfo">{ToProperty('{custom}', '=', ';')}</
  array>
  <string name="alarminfo">{variable.taginfo[VJA]}</string>
  <string name="trendinfo">{variable.taginfo[VJT]}</string></input>
  ```

- This example identifies four fields from the `variable.dbf` database: *name*, *type*, *unit* and *custom*. These fields are used later in the file. The input section loads only rows where the *unit* field matches the value of the IODevice variable in the parameter  section. This helps improve performance by avoiding the processing of  irrelevant rows. 

- An array is created called taginfo that  contains key value pairs based on the value of the custom field. If the  custom field value was "VJA=Alarm;VJT=Trend", then an array is created  containing the values taginfo[VJA] = "Alarm" and taginfo[VJT] = "Trend". 

-  Two string variables are created based on the values of the taginfo array. 

- `<output>`
- The `<output>` section defines the output database, the processing to be done on the  input fields and the respective output fields to be generated. There can be many output sections in the XML file. The output section can specify the same database file as the input section if necessary. For example: 

- ```xml
  <output name="digalm" file="digalm.dbf" 
  filter="'{variable.alarminfo}=VJA' AND 
  '{variable.type}=DIGITAL'">
  <field name="tag">{variable.name}_ALARM</field>
  <field name="name">{variable.name}_ALARM</field>
  <field name="var_a" key="true">{variable.name}</field>
  <field name="taggenlink" load="true">{parameter.IODevice}</
  field>
  </output>
  ```

- In this example, fields are written to the `digalm.dbf` database. Output processing only occurs for the current row if the input row relates to a digital alarm. That is, if the *alarminfo* variable from the input section has the value of "VJA" and the type field from the input database is "DIGITAL. The *tag* and *name* fields are given the value *name*_ALARM.

Curly braces are usually used for substitutions to replace pre-defined texts with tag properties. To use curly brace  characters as normal characters, use double curly braces which will be  exceptionally converted to singular ones to express curly braces. Round  brackets are not regarded as special characters when used in tags other  than <calculator> tag.

**Example**

```xml
<output name="digalm" file="digalm.dbf" filter=" ( '{variable.alarminfo1}=VJA' OR '{variable.alarminfo2}=VJA' ) AND '{variable.type}=DIGITAL'" desc="Generate digital alarm tags from input digital variable tags">
	<field name="tag">{variable.name}_ALARM</field>
	<field name="name">{variable.name}_ALARM</field>
	<field name="var_a" key="true">{variable.name}</field>
	<field name="taggenlink" load="true">{parameter.IODevice}</field>
	<field name="comment">{{Testing1}}</field>
</output>
```

Proprietary tags used in the template are described in [XML template tags](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/XML_Template_Tags.html). See [Sample XML Templates](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Sample_XML_Templates.html) for more comprehensive examples.

##### Referencing variables 

Variables can be used to temporarily store information. Variables can be defined either globally in the `<param>` section of the XML file or locally in an `<input>` or `<output>` section.

Variables are defined using the `<string>` tag as shown in [XML template tags](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/XML_Template_Tags.html). For example:

```xml
<string name="MyIODevice">DISK_PLC</string>
```

To refer to a variable, use the following syntax:

```
{SectionName.VariableName}
```

and for this example: 

```
{parameters.MyIODevice}
```

The *SectionName* can be omitted if you are referencing a variable defined in the same section.

Variables are evaluated sequentially in the XML file. Variables in the `<param>` section are assigned first, followed by those in the `<input>` section, followed by variables in each `<output>` section in sequence. This means that:

- Variables in the `<param>` section can be referenced by the `<input>` section and every `<output>` section in the same template.
- Variables in the `<input>` section can be referenced by every `<output>` section.
- Variables in each `<output>` section can only be referenced by subsequent `<output>` sections.

##### Referencing Arrays 

To reference a member of an array by member name use:

```xml
{SectionName.ArrayName[MemberName]}
```

To reference a member of an array by matching a pattern use:

```
{SectionName.ArrayName(PatternString)}
```

See [Pattern matching](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Pattern_Matching.html) for information on pattern matching wildcards.

##### XML Template Tags

The proprietary tags used in TagGen XML files are listed below.

###### `<template>`

This is the root tag in the XML file. Only have one `<template>` tag in each XML file.

Can contain:

```xml
<param>, <input>, <output>
```

Attributes:

***desc***
Description of the template section.

###### `<param>`

This optional tag defines global parameters for the XML file. Here you can specify string constants to be used in the  rest of the file.

Can contain:

```xml
<string>
```

Attributes:

***name***
Name of the parameter section.

***desc***
Description of the parameter section.

###### `<input>`

This defines the source database of the XML file, the fields to be imported and any input filtering that might be  necessary. There needs to be only one input section defined.

Can contain:

```
<field>, <string>, <array>, <calculator>
```

Attributes:

***name***
Name of the input section.

***file***
Input database file name.

***desc***
Description of the input section.

###### `<output>`

This defines the output database of the XML  file, the tags to be generated and any transformations necessary to  generate tag data from input variable data. A template needs to have at  least one output section defined.

Can contain:

```
<field>, <string>, <array>, <calculator>
```

Attributes:

***name***
Name of an output section

***file***
Output database file name

***filter***
Output section filter, syntax:

```
filter="`*variable*`=`*FilterString*`"
```

<FilterString> is a string expression  that can combine wildcards or wildcard strings with boolean operators  (AND, OR and NOT), as well as grouped boolean terms using parentheses.  For example, "L*" will match if string beginning with the letter "L";  "L* OR H*" will match if string beginning with "L" or "H". See [Pattern matching](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Pattern_Matching.html) for a list of wildcard operators.

***desc***
Description of the output section.

###### `<field>`

This tag specifies the database fields that will be processed in `<input>` and `<output>` sections.

When used in the input section it specifies the named fields for each record loaded from the input database. It is read only.

When used in an output section it specifies the named fields to write to for each generated tag record in the output database.

Attributes:

***name***
Case insensitive name of a database field.

***key***
Valid for output sections only, this boolean flag indicates  whether this is a key field. This is useful for special handling  in the output section. For example, you can synchronize  between a new record set and an old record set by matching  the key fields.

***load***
Valid for both input and output sections, this boolean flag  indicates whether this is a load filter field. Load filter fields  are used to filter records when loading data from the input  database and output database.

***desc***
Description of the field element.

**Note:** Key and Load  string expressions can contain a regular string, a variable reference,  wild card operators, or a mixture of these. See [Pattern matching](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Pattern_Matching.html) for a list of wildcard operators.

###### `<string>`

This tag defines a string constant that can be used in `<param>`, `<input>` and `<output>` sections. 

Attributes:

***name***
Name of a variable string.

***desc***
Description of the string element.

**Note:** For Unity SpeedLink, the string "IODevice", when defined in the `<param>` section, refers to the project's IO Device. Do not assign it another value.

###### `<array>`

This tag defines a dynamic array of strings in `<input>` and `<output>` sections.

The set of strings depends on the fields of the record being processed and those strings that are generated by the  ToProperty() and Split() commands. See [Built-In Functions](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Built-In_Functions.html) for more information.

Attributes:

***name***
Name of a variable string array.

***desc***
Description of the array element.

###### `<calculator>`

This tag defines an expression variable in `<input>` and `<output>` sections. 

The content of this tag is a mathematical expression used to specify a simple operation for data transformation.

The operands in the expression can be only  numbers or variables with numeric values. The expression can use  parentheses to change the precedence of the evaluation.

For example, the following calculator in an `<input>` section counts input records by incrementing its current value.

```
<calculator name="c1" initial="0">{c1} + 1</calculator>
```

Attributes:

***name***
Name of a calculator.

***initial***
Initial value of the calculator, zero by default.

***desc***
Description of the calculator element.

##### Pattern matching 

The following wildcards can be used in strings 

| Character | Description                                                  |
| --------- | ------------------------------------------------------------ |
| *         | Matches any string in the input data stream                  |
| ?         | Matches any single character in the data stream              |
| %d        | Matches any decimal integer (nnn... where n is 0-9) in the data stream |
| %e        | Matches any octal number (0onnn... where n is 0-7) in the data stream |
| %h        | Matches any hexadecimal number (0xnnn... where n is 0-9, A-F or a-f) in the data stream |
| %s        | Matches any string in the data stream (same as *)            |
| {         | Begin a token string. The  characters between { and } in the Input Pattern (including regular and  special characters) represent a "token string". The characters in the  data stream that match this token string are a token, and can be  referenced by the Output Data String, and written directly to the output database as a group |
| }         | End of a token string                                        |
| \         | Treat the following character  as a literal. For example, if a literal `*' character was expected in  the input data stream, you would use \* to denote this. If a literal  backslash \ is expected, use \\. |

##### Built-In Functions

There are three built-in functions that can be  used to manipulate strings in the XML template. The syntax to call a  built-in function as follows:

```
{<FunctionName>(<arg1>, <arg2>,...)}
```

The three built-in functions are:

**SubString**(*string, 'start', 'count'*)

This function extracts a substring from the given source string starting at character *start* and ending after *count* characters.

```
<string name="AddrWord">{SubString('{tagprefix}','3','2')}</string> 
```

**Split**(*string, delimiter*)

This function splits the source string into  parts separated by the delimiter and stores them in a zero based string  array. For example:

```
<array name="tagid">
{split('VJA;VJT', ';')}
</array>
```

produces tagid[0] = VJA, tagid[1] = VJT.

**ToProperty**(*string, separator, delimiter*)

This function splits the source string parts  separated by the delimiter, and then further into key value pairs  separated by the separator. For example:

```
<array name="taginfo">
{ToProperty('VJA=Alarm;VJT=Trend', '=', ';')}
</array>
```

produces taginfo[VJA] = Alarm, taginfo[VJT] = Trend.

##### Sample XML Templates 

A sample template is provided to create analog  or digital alarm tags and trend tags. The template shown below specifies the rules for generating Citect SCADA Alarm and Trend tags from a `Unity SpeedLink device/database`, for the import and/or synchronization of variable tags.

**Note:** You will need to modify this template to suit your particular requirements. Refer to [TagGen XML Template](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/TagGen_XML_Template.html) for more information.

For each Unity Database variable tag with the text "VJA" in the custom field imported in to Citect SCADA of type "DIGITAL", this file will generate a linked Digital Alarm Tag within Citect SCADA (digalm.dbf) with the name `<variablename>_ALARM`.

For each Unity Database variable tag with the text "VJA" in the custom field imported in to Citect SCADA not of type "DIGITAL" and not of type "STRING", this file will generate a linked Analogue Alarm Tag within Citect SCADA (anaalm.dbf) with the name `<variablename>_ALARM`.

For each Unity Database variable tag with the text "VJT" in the custom field imported in to Citect SCADA, this file will generate a linked Trend Tag within Citect SCADA (`trend.dbf`) with the name `<variablename>_TREND`. This example file does not enter values for any of the other Trend tag properties.

```xml
<?xml version="1.0"?>
<template desc="Default SpeedLink Unity Pro TagGen template">
    <param name="parameter">
        <string name="IODevice" desc="SpeedLink necessary parameter, it will be set to the given I/O Device name by the system."></string>
    </param>
    <input name="variable" file="variable.dbf" desc="Load variable tags for the specified I/O Device">
        <field name="name"></field>
        <field name="type"></field>
        <field name="unit" load="true">{parameter.IODevice}</field>
        <field name="custom"></field>
        <array name="taginfo">{ToProperty('{custom}', '=', ';')}</array><string name="alarminfo">{variable.taginfo[VJA]}</string>
        <string name="trendinfo">{variable.taginfo[VJT]}</string>
    </input>
    <output name="digalm" file="digalm.dbf" filter="'{variable.alarminfo}=VJA' AND 
'{variable.type}=DIGITAL'" desc="Generate digital alarm tags from input digital variable tags">
        <field name="tag">{variable.name}_ALARM</field>
        <field name="name">{variable.name}_ALARM</field>
        <field name="var_a" key="true">{variable.name}</field>
        <field name="taggenlink" load="true">{parameter.IODevice}</field>
    </output>
    <output name="anaalm" file="anaalm.dbf" filter="'{variable.alarminfo}=VJA' AND 
'{variable.type}=NOT DIGITAL' AND '{variable.type}=NOT STRING'" desc="Generate analog 
alarms from input analog variable tags">
        <field name="tag">{variable.name}_ALARM</field>
        <field name="name">{variable.name}_ALARM</field>
        <field name="var" key="true">{variable.name}</field>
        <field name="taggenlink" load="true">{parameter.IODevice}</field>
    </output><output name="trend" file="trend.dbf" filter="'{variable.trendinfo}=VJT'" desc="Generate trend tags from input variable tags">
    <field name="name">{variable.name}_TREND</field>
    <field name="expr" key="true">{variable.name}</field>
    <field name="taggenlink" load="true">{parameter.IODevice}</field>
    </output>
</template>
```

**Simple Wildcard Example**

The following example shows how an empty string variable called "wildcard" can be used as a wildcard pattern to load a  set of data from a variable database. The string variable is substituted for a "* " wildcard character when the xml file is processed. The  example below loads data where the names of variable tags contain the  word "Tank". 

```xml
<input name="variable" file="variable.dbf">
    <string name="wildcard"></string>
	<!-- Loading set of data where string contains the word "Tank" -->
    <field name="name" load="true">{wildcard}Tank{wildcard}</field>
    <field name="unit"></field>
    <field name="custom"></field>
</input>
```

**Sample Analog Alarm Example**

The following example specifies the rules for generating Citect SCADA Analog Alarm Tags and setting the high-high limit attribute, based on the engineering scale of the linked variable Tag.

For each Unity Database variable tag with the text "VJA" in the custom field imported in to Citect SCADA not of type "DIGITAL" and not of type "STRING", this file will generate a linked Analog Alarm Tag within Citect SCADA (anaalm.dbf) with the name `<variablename>_ALARM`, with the following properties:

- high-high limit based on the variable tag's full and zero engineering scale properties and a user specified fraction "Divisor".

In this example, only analog alarms for integer variables will have the limit set.

```xml
<?xml version="1.0" encoding="utf-8"?>
<template>
    <param name="parameter">
        <string name="IODevice"></string>
        <string name="Divisor"></string>
    </param>
    <input name="variable" file="variable.dbf">
        <field name="name"></field>
        <field name="type" ></field>
        <field name="unit" load="true">{parameter.IODevice}</field>
        <field name="eng_zero"></string>
        <field name="eng_full"></string>
        <field name="custom"></field>
        <!-- customstring field may contain "VJA;VJT;VJC" -->
        <array name="taginfo">{ToProperty('{custom}', '=', ';')}</array>
        <string name="alarminfo">{variable.taginfo[VJA]}</string>
    </input>
    <!-- output section -->
    <output name="anaalm" file="anaalm.dbf" filter="'{variable.alarminfo}=VJA' AND 
'{variable.type}=INT'">
        <field name="tag">{variable.name}_ALARM</field>
        <field name="name">{variable.name}_ALARM</field>
        <field name="var" key="true">{variable.name}</field>
        <field name="taggenlink" load="true">{parameter.IODevice}</field>
        <calculator name="highh" >({variable.eng_full}-{variable.eng_zero})/
{parameter.Divisor} </calculator>
        <field name="highhigh">{highh}</field>
    </output>
</template>
```