## Composite Genies

Композитний Джин — це набір окремих Джинів, зібраних у єдиний об’єкт. Окремі об’єкти та їх властивості визначаються у файлі шаблону XML разом із макетами для колекції, тобто Composite Genie. Ви можете вставити кілька екземплярів складеного об’єкта на графічну сторінку та вказати різні параметри, включаючи значення, вирівнювання та параметри відображення для кожного екземпляра, щоб налаштувати Composite Genie відповідно до ваших вимог.

Наприклад, ви хочете створити дзеркальний об’єкт компресора, який може додатково відображати етикетку, індикатор режиму та лічильник поряд із символом. До Plant SCADA 2020 R2 ви могли створити окремих джинів для кожної з перестановок, або ви могли створити одного джина, який використовував видимість для відображення/приховування елементів під час виконання. За допомогою Composite Genies ви можете просто вибрати [шаблон XML](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genie_Templates.htm) для компресора, який надає [набір параметрів презентації](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm) для налаштування мітки, орієнтації тощо. Все, що вам потрібно зробити, це встановити значення для цих параметрів і вставити об’єкт на сторінку.

| Without Composite Genies                                     | Using Composite Genies                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Instead of inserting and configuring individual Genies:    ![img](media/GeniesCollection1.png)You need to change the layout and alignment of these Genies manually. | [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm):    ![img](media/CompositeGenie1.png)All [components laid out neatly](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genie_Templates.htm) with alignment and layout options that engineers can customize. |
| If you add related  equipment indication to your compressor Genie above, the alignment of  the objects needs to be adjusted to accommodate the new Genie:    ![img](media/GeniesCollection2.png) | With a Composite Genie, simply bring up the [Presentation Options](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm) and select to add an output bar resulting in:    ![img](media/CompositeGenie2.png) |

З використанням Composite Genies:

- Розмір бібліотек об’єктів можна значно зменшити, оскільки потрібно підтримувати лише один Composite Genie, а не підтримувати декілька перестановок кожного об’єкта, що використовується на графічних сторінках.

- Інженери можуть отримати більш чітке уявлення про дизайн своєї сторінки, оскільки Composite Genie відображає лише ті параметри, які були вибрані.
- Доступний розширений інтерфейс параметрів. Використовуючи XML-шаблон, дизайнери бібліотек можуть збагатити інтерфейс параметрів, що дозволяє операторам вибирати з різних макетів, режимів, представляє параметри з урахуванням залежностей, правил імен тощо.

As with Genies and Symbols, Composite  Genies can be inserted for use in a graphics page, template or super  genie. You can perform the following operations:

- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm)                
- [Edit/Update a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Edit_Update_Composite_Genie.htm)                
- [Delete Unused Composite Genie Instances](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Delete_Unused_Composite_Genie_Instances.htm)                
- [Delete a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Delete_a_Composite_Genie.htm)                

### Insert a Composite Genie

A Composite Genie can be inserted into any  graphics page, template or Super Genie. It cannot be inserted into a  Genie or symbol. 

**Note:** The appearance of Composite  Genies can be affected by different DPI settings. It is recommended that when running Graphics Builder, the **Scale and Layout** setting should be set to "100%" in the Windows™ **Display** settings. After changing the Scale and Layout setting for a computer, you should restart it. 

To insert a Composite Genie:

1. Open Graphics Builder.
2. Click the **Paste Composite Genie** button in the Objects toolbox. 
3. ​                    ![img](media/PasteCompositeGenie_32x29.png)                

4. The Open dialog box is displayed.

5. Select the XML template for the Composite Genie from the list of templates.
6. **Note**: The template file that you select needs to be in located in the Composite Genies folder in the  current project folder (or one of its included projects).

7. Click **OK**. The Presentation Options dialog box is displayed.

​                ![img](media/PresOptions1.png)            

1. Type or select the values for the parameters displayed. 
2. **Note**: Depending upon the options you choose, some items may be hidden or displayed. For example, on the  Meter Composite Genies, when you select the **Display Control Output** check box, the **Display Trend** and **Trend Type** options are displayed.

3. Use the **Search** box to search for parameters in the dialog box. Type the parameter name or part of the parameter name to locate a parameter.
4. **Note**: Clear the Search box before clicking **OK** on the Presentation Options dialog box.

5. Use the **Show only parameters with invalid input** option to display options for which incorrect or no values have been selected or specified.
6. Click **OK** to insert the Composite Genie, or **Cancel** to close the Presentation Options dialog box without inserting the Composite Genie.

**Note**: You cannot rotate or mirror a Composite Genie that has been inserted on a page.

### Edit/Update a Composite Genie

To edit the parameter options for an existing Composite Genie:

1. Open Graphics Builder.
2. Click to select the inserted Composite Genie.
3. Right-click the Composite Genie, and select **Edit Composite Genie** from the context menu. The Presentation Options dialog box is displayed with the Composite Genie instance name and template ID. 
4. Edit the parameters as required.
5. Click **OK**.

Double-clicking on the template ID selects  the ID. You can copy the ID and use it to locate duplicate instances of  the template in Windows Explorer. 

If you modify a Composite Genie after you  have used it in your project, all instances of the Composite Genie may  be automatically updated with the latest version of the template.  Changes including updates to labels, genies and layout will be  propagated to all instances. If a template is up to date, associated  instances will not be updated. 

**Note**: You should not modify the properties of the folder in which Composite Genie instances are stored (%PROGRAMDATA%\AVEVA Plant SCADA 2020 R2\User\<Project Name>\_CompositionCaches). You should not manually delete or modify  files in this folder. Doing so many result in errors when inserting  Composite Genies on graphics pages.

An error message is displayed if a problem  is encountered during the update process. The message details the cause  and the options available for resolving the issue. An error may occur if a Composite Genie does not exist or if the project is erroneous. 

For example, if you create a copy of an  existing template, but retain the same GUID in the XML file of the  copied template, you will see the following message:

​                ![img](media/CG_Update_Error_590x345.png)            

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Update a Particular Instance](javascript:void(0))

Updating a particular  instance of a Composite Genie allows you to verify the changes to a  Composite Genie without affecting other instances of the object on other pages.

To update a particular instance of a Composite Genie:

1. Open Graphics Builder. 
2. Update the Composite Genie template as required.
3. Double-click the instance represented by the template. The Presentation Options  dialog box is displayed with the modified parameters. For example if you have added a new parameter, the Presentation Options dialog should show the parameter.
4. Click **OK**. The changes including updates to labels, genies and layout will be propagated to this instance of the Composite Genie.
5. Save the page. 

**Note**: Before you  apply the changes to all instances of Composite Genies across all pages, verify the changes using the instructions above.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Update All Instances](javascript:void(0))

 To update instances of Composite Genies: 

1. Open Graphics Builder. 
2. On the **Tools** menu, select **Update Pages**. This command will replace an existing Composite Genie with its newest  version available. This command will only affect the Active project and  its includes. Compile the project for the changes to take effect for  runtime. 

**Note**: This change cannot be reversed.

**Note**: If a runtime page contains an updated Composite Genie instance, an online change will update runtime. Refer to [Online Changes](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Online_Changes.htm) for more information.

### Delete Unused Composite Genie Instances

When you add a graphic object as a  Composite Genie on a page, a Composite Genie instance that is uniquely  identified by its presentation options, is automatically created in the  project folder. This establishes a reference from the graphic object to  this Composite Genie instance. There can be multiple graphic objects  that refer to the same instance of a Composite Genie if their  presentation options are the same. Therefore, deleting a graphic object  does not delete the associated Composite Genie instance.

Over time there can be a number of  Composite Genie instances that are not associated with any graphic  object.  These unused Composite Genie instances can slow down operations and occupy project disk space.  You can use the **Pack Libraries** option to remove unused instances.

**Note**: You should not modify the properties of the folder in which Composite Genie instances are stored (%PROGRAMDATA%\AVEVA Plant SCADA 2020 R2\User\<Project Name>\_CompositionCaches). You should not manually delete or modify  files in this folder. Doing so may either prevent your pages from  opening or cause your Composite Genies to be displayed incorrectly.

To delete unused instances:

1. Open Graphics Builder.
2. On the **Tools** menu, select **Pack Libraries in Active Projects** or **Pack Libraries in Active and Included Projects**. The following message is displayed. 

​                ![img](media/Clear_CGCache_Pack.png)            

1. Click **Yes**. All unused instances of Composite Genies will be deleted.

### Delete a Composite Genie

To delete a Composite Genie:

1. Open the page in which the Composite Genie has been inserted.
2. Click to select the Composite Genie.
3. Press the **Delete** key. This will remove the Composite Genie from the page.
4. Save the page.

### Composite Genie Templates

Plant SCADA provides a wide range of out-of-the box Composite Genies in the form of XML templates. An XML template contains the definition of a Composite  Genie. A library engineer may modify an existing XML template or create  new templates defining their own Composite Genies. It is recommended  that you make a copy of the template before you modify it so that  templates are not overwritten if you re-install Plant SCADA.

**IMPORTANT**: If you make a copy of a  template, you need to assign a new GUID to the template and all the  compositions in the template. For more information, see [Visual Template](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Visual_Template.htm) and [Compositions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Composites.htm).

XML templates for Composite Genies are located in the %PROGRAMDATA%\AVEVA Plant SCADA 2020 R2\User\<project name>\ Composite Genies folder.

The **CompositionTemplate.xsd** file,  located in the %PROGRAMFILES(X86)%\AVEVA Plant SCADA\Bin, contains the  schema for the Composite Genie XML templates. This file describes the  elements and attributes that may be contained in an XML template for a  Composite Genie, and the order in which the elements and attributes need to be added to the XML template.  The XML template file is validated  against the XSD file.  When you modify an XML template or create a new  one, it is recommended that you use a good XML editor that supports  schema error detection so that errors are highlighted and can be  addressed easily.

Errors may be encountered if the XML file  for a Composite Genie does not conform to the definitions in the  underlying XSD. Alternatively, errors may be encountered if there are  duplicate IDs for elements, undefined conditions, and so on. In both  cases, errors will be reported with details of the line number and  position of the error when an operator inserts the Composite Genie on to a page. For more details, see [Edit/Update a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Edit_Update_Composite_Genie.htm).

An XML template for a Composite Genie contains the following elements:

- [Visual Template](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Visual_Template.htm)                
- [Parameters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Parameters.htm)                
- [Content Items](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Content_Items.htm)                
- [Compositions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Composites.htm)                
- [Conditions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Conditions.htm)                
- [Alarm Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_AlarmIndicators.htm)                

Each of these elements is explained in  detail in the sections below. It is recommended that you review these  sections before you modify existing XML templates or create new  templates.

#### Visual Template

This section comprises standard XML  declarations. In addition, this section contains  the GUID, which is a  unique identifier for the XML template.

**Note**: If you modify an existing  template or create a new Composite Genie template, you should validate  the XML file by loading the schema definition file  (CompositionTemplate.xsd which is in the <Plant SCADA installation folder>\bin folder) into your XML editor.

 If you create your own Composite Genie,  you will need to create a GUID for it. Several online tools are  available for generating a GUID.

To generate a GUID:

1. Search for the term  "generate GUID" in a browser using any search engine. A list of websites that can generate a GUID is displayed.
2. Access any one of the sites.
3. Select the format for  the GUID. The GUID format should include braces and hyphens and should  be in upper case. For example, {1E49C603-FCBC-4913-ABD1-97920283C6BD}.
4. Generate the GUID. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Example](javascript:void(0))

![img](media/CG_VisualTemplate_505x114.png)                    

#### Parameters

The <Parameter> element defines the  attributes that will be displayed as Presentation Options to the user  when they insert a Composite Genie on to a graphics page. It is  comprised of the following attributes for each parameter:

| Attribute    | Description                                                  |
| ------------ | ------------------------------------------------------------ |
| Name         | Unique name for the parameter.                               |
| Label        | Display name for the parameter.                              |
| Type         | Data type of the parameter – Boolean, Integer or String.     |
| MinLength    | Minimum number of characters that the parameter value needs to contain. |
| MaxLength    | Maximum allowable characters for the parameter value         |
| MinValue     | Minimum value that can be specified for the parameter        |
| MaxValue     | Maximum allowable value for the parameter                    |
| DefaultValue | Default value set for the parameter                          |
| NamingRules  | Naming rules can be  used to force the user to enter parameter values in a particular format. For example, to use equipment naming rules, set this attribute to  “Equipment”. Refer to the Equipment Naming Rules and [Tag Naming Rules](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Tag_Names.htm) sections for more information. |
| Description  | Description of the  parameter. This appears at the bottom of the Parameter Options dialog  box when the operator clicks to specify the value for a parameter. It is recommended that you enter a description for the parameter in order to  help engineers to specify valid values for the parameters. |
| Values       | List of selectable  values if an option is to be displayed as a dropdown list in the  Parameter Options dialog box.  To create a list of values, each value needs to be declared with a  unique ID and Label. The label will appear as one of the values the user can select. For example, if you need an option titled “Orientation”  with the values “Vertical” and “Horizontal” available for selection, the following code needs to be included in the Parameters element:     ![img](media/CG_ValueDefinitionCode.png) |

Parameter definitions can include the  <Dependency> element to show or hide parameters. This element can  use Global, Parameter or Composite conditions to show or hide a  parameter based on the operator's selection of an option or value.  For  more information about conditions, refer to [Conditions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Conditions.htm).

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Example - Simple ](javascript:void(0))

This is a simple example where a dependency has been defined using the <Dependency> element to show the **Label** parameter only if the operator selects the **Display Label** checkbox. This is achieved through the use of a [Global Condition](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Conditions.htm). You can also use Parameter and/or Composite conditions within the <Dependency> element. 

![img](media/CG_ParametersSimpleCode.png)                    

The above code will display the following presentation options.

![img](media/CG_Presentation_Options_Simple.png)                    

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Example - Complex](javascript:void(0))

This example provides a  slightly more complex scenario with parameters to be displayed based on  the operator’s selection of value.  Therefore, a list of values and a  dependency need to be defined.

- Refer to the XML code for the “Number of sub equipment” parameter. This parameter  can take the values 0, 1, 2, 3, 4 or 5. The <Values> attribute  defines this list of selectable values (see the sample code below).

![img](media/CG_CompressorCodeValues.png)                    

- Depending  upon the value the operator selects for this parameter, the Sub  Equipment parameter(s) will be displayed. For example, if the operator  selects 0 for the “Number of sub equipment” parameter, the Sub Equipment parameter will not be displayed, if the user selects 1, a single Sub  Equipment parameter with the label Sub Equipment #1 Name will be  displayed, if the user selects 2, two Sub Equipment parameters with the  labels Sub Equipment #1 Name and Sub Equipment #2 Name will be displayed and so on. The user can choose up to 5 pieces of sub equipment.
- To be able  to select 5 pieces of sub equipment, a parameter each needs to be  defined for each piece of sub equipment. In addition, each of these  parameters needs to have a dependency defined within it (see below for  sample code that shows the definition for two sub equipment pieces).
- A dependency is defined using the <Dependency> attribute. For Sub Equipment 1, global condition “Show_MEO1” needs to be satisfied. For detailed  information about conditions, see the Conditions topic.

![img](media/CG_CompressorCodeParameters.png)                    

![img](media/CG_Presentation_Options_Complex.png)                    

#### Alarm Indicators

The <AlarmIndicators> element is an optional element for displaying [alarm indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Alarm_Indicator.htm) for equipment. It comprises the following child elements:

| Element       | Description                                                  | Attribute                 | Description                                                  |
| ------------- | ------------------------------------------------------------ | ------------------------- | ------------------------------------------------------------ |
| EquipmentLink | Defines each piece of related  equipment for which an alarm needs to be displayed. | Id                        | A unique string  identifier with which <AlarmIndicator> elements in  compositions can refer to the forward-declared equipment link. |
|               |                                                              | TemplateParameter         | Name of the template parameter.  The value of this is used as the equipment expression of the alarm indicator.  The template parameter needs to be defined in the  <Parameters> element in the same document. |
|               |                                                              | IncludeEquipmentReference | Set this to 'true' to include  equipment references when determining the highest priority alarm for the  alarm indicator. Set this to 'false' if you do not want to include equipment  references. |
|               |                                                              | Hierarchy                 | Node in the equipment hierarchy  that will be used to determine the highest priority alarm for the alarm  indicator. You can set this to include equipment that occur at nodes down the  equipment hierarchy (referred to as "children"). Set this to one of  the following:EquipmentOnly     EquipmentAndChildren     ChildrenOnly |
| BorderStyle   | Defines the alarm display  settings.                         | Id                        | A unique string identifier with  which <AlarmIndicator> elements in compositions can refer to the  forward declared border style. |
|               |                                                              | Width                     | Sets the width of the alarm  border (in pixels).             |
|               |                                                              | Padding                   | Sets the amount of space (in  pixels) between the extent of the object group or Genie and the inside edge  of the alarm border. |
|               |                                                              | IsInside                  | Set this to 'true' to place the  border within the extent of the object group or Composite Genie. Note that  you cannot set a padding in this case. |
|               |                                                              | IsDefault                 | Set this to 'true' to make this  border style the default style. |

**Note**: An alarm indicator is applied  to all equipment items within the Composite Genie. The items are  automatically grouped and the alarm border is applied to the composite  if there are more than two visible items in the container. 

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Example](javascript:void(0))

![img](media/CG_AlarmIndicator.png)                    

#### Content Items

The <ContentItems> element defines  the library objects (Genies) that are available to be included in  compositions for the Composite Genie. It contains one or more  <ContentItem> child elements, each of which comprises the  following attributes:

| Attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| Id        | Unique numeric identifier within the <ContentItems> section.  **Note**: You should not use the same numeric Id for more than one <ContentItem> elements. Doing so would result in an error when the system reads this visual template document. |
| Type      | This is set to the type of the object that makes up the Composite Genie and should not be modified. **Note**: In this version Composite Genies constitute only Genies. So, Type is set to “Genie” in the XML templates. |
| Project   | Name of the project  which contains the referred library object. The project needs to be  either the same as the project in which the visual template resides or  one of its include projects. **Note**:  If the  project is renamed, the Genie will not be available for use unless this  attribute is modified in the XML template. Keep this in mind when  renaming a project. |
| Library   | Name of the object library to which this item belongs.       |
| Item      | Name of the item to be included in the Composite Genie.      |

**Note**: You need to explicitly define each and every item that you want to include in your compositions.

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Example](javascript:void(0))

Each line in the code below defines an item, in this case a Genie, that will be available to be included in a composition.

![img](media/CG_ContentItmesCode.png)                    

#### Compositions

The <Composition> element details the “composition” of the Composite Genie, that is, the possible layouts,  parameter conditions and parameters that constitute the Composite Genie.  It contains multiple elements each with a set of attributes.  Typically, the XML template for a Composite Genie is made up of several  compositions to represent the different layouts available. Each  composition can define only one layout. The template needs to have at  least one composition.

| Attribute      | Description                                                  |
| -------------- | ------------------------------------------------------------ |
| Composition Id | Unique identifier for the composition. This is an ID that is generated using the GUID Generator tool. |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Example](javascript:void(0))

​                        ![img](media/CG_CompositionIdCode.png)                    

##### Prerequisites

Within a composition, one or more  prerequisites may be defined within the <Prerequisite> element.  Prerequisites  are made up of conditions, which are evaluated at  runtime. If a prerequisite is true, the corresponding composition will  be applied. Otherwise, the next composition will be evaluated, and a  composition will be applied only when the prerequisite is satisfied.  Prerequisites are applied sequentially.  For more information, refer to  the Conditions topic.

**Note**: When defining conditions, it  is recommended that you start with the most complex condition first and  then add conditions in decreasing order of complexity. This is so that  the most specific composition is selected for the Composite Genie.

​                

| Attribute          | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| GlobalConditionRef | Used to refer to a predefined Global condition               |
| ParameterCondition | Used to specify conditions by comparing a template parameter value to a predefined value. |
| CompositeCondition | Used to combine  more than one condition with either AND or OR relation specified in its  attribute. Its child conditions can be made up of predefined Global  conditions <GlobalConditionRef Id="..."/>, a Parameter condition  and nested Composite conditions. |

[![Open](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Skins/Default/Stylesheets/Images/transparent.gif)Example](javascript:void(0))                        ![img](media/CG_Prerequisite.png)                    



todo