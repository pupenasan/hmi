## Equipment

[Help](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Content/Equipment.htm)

In Plant SCADA, the term "equipment" is used to describe an object-oriented  architecture within a project that can be used to reference the  machinery or processes being monitored. Equipment definitions create  logical groupings that allow you to organize your project using a  hierarchical design. Each definition brings together the base SCADA  properties into a single entity that can be easily replicated within  your project. 

For example, if a pump is represented in  your project as a piece of equipment, it will bring together the tags,  events, alarms, permissions, communications, scheduling and scripting  associated with the pump. You can associate the pump with a particular  geographical area, or include it as part a functional process. 

**Note:** To be able to define equipment, you need to have a [Report Server process](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Add_a_Report_Server_Process.html) defined. 

This section of the help explains the concepts that define the way equipment is configured in a Plant SCADA project. These include:

- [Equipment Hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_Hierarchy.htm) — the object model that is created by the equipment definitions in a project
- [Equipment Types](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_Types.htm) — the templates you can use to  add multiple instances of a particular piece of equipment to your project 
- [Equipment Instances](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_Instances.htm) — the representation of a physical piece of equipment in your project that can be based on a particular equipment type
- [Equipment States](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_States.htm) — operational states for a piece of equipment that you can use for scheduling
- [Equipment References](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_References.htm) -  the link  added between a piece of equipment, and/or items belonging to other equipment  within your project. The equipment reference can  also be to equipment,  and/or items that is outside the equipment  hierarchy. 

We will also discuss the different approaches you can take when defining equipment within a project.

- If you are creating a new  project (or adding a new section to an existing project), use the  Equipment Editor to build an equipment hierarchy and automatically  generate tags from that hierarchy (see [The Equipment Editor](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/The_Equipment_Editor.htm)). For specific, task-based information that describes how to configure equipment in a Plant SCADA project using the Equipment Editor, see [Configure Equipment Types using the Equipment Editor](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_Equipment_Types_in_the_Equipment_Editor.htm). 
- If you would like to add an  equipment hierarchy to an existing project, you can associate your  existing variable tags, trends and alarms with equipment in Plant SCADA Studio (see [Define Equipment Association for an Existing Tag](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Define_an_Equipment_Association_for_aTag.htm)). For specific, task-based information that describes how to configure equipment in Plant SCADA Studio, see [Configure Equipment in Plant SCADA Studio](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_Equipment_in_the_Engineering_Environment.htm). 

### Configure Equipment in Plant SCADA Studio

The way you configure equipment in Plant SCADA will initially depend on whether or not your project has existing tags. If you have a project with existing tags, you can use Plant SCADA Studio to associate equipment with your tags (see [Define an Equipment Association for Existing Tags](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Define_an_Equipment_Association_for_aTag.htm)).

Equipment can be configured in the System Model activity of Plant SCADA Studio.

**Note**: If you are  starting a new project (or adding a new area or process to an existing  project) you can use the Equipment Editor to generate tags (see [Configure Equipment Using Equipment Editor](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_Equipment_Types_in_the_Equipment_Editor.htm)).

**Associate Existing Tags with an Equipment Hierarchy**

Plant SCADA allows you to build an [equipment hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_Hierarchy.htm) into a project that is already configured to include tags, alarms, trends, and so on. 

When you build an equipment  hierarchy into an existing system, you create a way to reference your  tags using logical groupings that may reflect geographical areas or  functional processes. 

Associating equipment with tags in an existing project is a two-step process:

1. Define the required equipment.
2. To achieve this, [add rows](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/GridEditor_Add_Rows_to_Grid.htm) to the **Equipment** list in the **System Model** activity (see [Define Equipment in Plant SCADA Studio](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Define_Equipment.htm)).

3. Associate tags with the equipment you've defined. 
4. To achieve this, you set the Equipment property for a tag in the **System Model**activity (see [Define an Equipment Association for a Tag](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Define_an_Equipment_Association_for_aTag.htm)).

You can also define equipment associations for your tags directly in the project database using Microsoft Excel™   (see [Use the Project DBF Add-In to Define Equipment Associations](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Use_the_ProjectDBF_Add-In_to_Edit_the_Equipment_Database.htm)).

#### Define Equipment in Plant SCADA Studio

You can manually add equipment definitions to a Plant SCADA project that adhere to an [equipment hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_Hierarchy.htm). 

The hierarchy is created from the names you apply to the equipment you define. If you include a period (.) in a  name, it specifies a hierarchy level. You can then use this hierarchy as a way to reference the tags in your project using logical equipment  groupings (see [Define an Equipment Association with an Existing Tag](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Define_an_Equipment_Association_for_aTag.htm)).

To  link equipment to equipment and equipment.items outside the equipment hierarchy, you can create equipment references (see [Define Equipment References](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Manually_Define_Equipment_References.htm)).

**Note:** If you are adding equipment to an existing project, it is recommended that you leave the **Type** field blank. An equipment type is primarily used to generate new tags  from Equipment Editor, and this is not required if your tags already  exist. If you want to define equipment that is associated with an  equipment type, you should use the Equipment Editor instead of Plant SCADA Studio (see [Equipment Editor](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/The_Equipment_Editor.htm)).

To manually define equipment:

1. In the **System Model** activity, select **Equipment**. 
2. On the menu below the Command Bar, select **Model**. 
3. The  list of equipment definitions will display in the Grid Editor. 

4. [Add a row to the Grid Editor](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/GridEditor_Add_Rows_to_Grid.htm). 
5. Type the required information in each column, or in the [Property Grid](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Plant_SCADA_Studio_Property_Grid.html) (see below for a description of the properties).            
6. Click **Save**. 

The equipment you have defined will now available to associate with the existing tags in your project (see [Define an Equipment Association for a Tag](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Define_an_Equipment_Association_for_aTag.htm)). 

You can also [Define Equipment States](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Manually_Define_Equipment_States.htm) for the equipment to support scheduling.

Equipment Properties

**General Properties**

| Property         | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| **Name**         | The name of  the equipment. This can be a name that represents a single piece of  equipment, or a name that also reflects the location of the equipment  within an [equipment hierarchy](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_Hierarchy.htm) (where a period (.) is used to indicate levels in the hierarchy).The length of  the complete name for the equipment is recommended to be less than 128  characters. The maximum length is 254 chars, however, long names can be  harder to use within configuration expressions and Cicode. When naming equipment the following rules apply:   • Equipment names need to be unique within the same cluster. •Equipment names cannot be the same as alarm tag names. •A period (.) may be used in equipment name to specify equipment hierarchy levels,for example: •Plant1.Filling.Tank1. •Each period delimiter denotes an extra level in the equipment hierarchy. •Up to 14 hierarchy levels are supported. The name applied to  each hierarchy level may notexceed 63  characters. •Individual names (delimited by a period) within an equipment path need to follow [tag name syntax](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Tag_Name_Syntax.html).  For example, characters such as '%', '?' and '/' are not allowed. •The name of root level equipment may not be the same as any cluster names. •   The name of the root level equipment  may not be a reserved word, such as IF, FOR, WHILE, END, 										OR,  or AND. |
| **Display Name** | A meaningful name for the equipment that can be used at runtime to easily identify it. Enter a value of 254 characters or less. |
| **Cluster Name** | The name of the cluster to which the equipment is assigned. The specified cluster  should be configured otherwise a compile will not be successful. If no  cluster name is set, the equipment will run on every cluster. |
| **Type**         | The specific type of equipment in the system. This drop down box is populated from the types database created by the [Equipment Types](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Equipment_Types.htm) form. |
| **Location**     | A string describing the location of the equipment. Enter a value of 254 characters or less. |
| **Page**         | The name of the page on which this equipment appears. Enter a value of 254 characters or less.This enables an operator to navigate directly to the page that hosts the piece of  equipment. If the graphic object appears on more than one page, the page specified here should represent its primary operational context.Where  duplicated variations of a page exist to suit HD1080 and UHD4K screen  resolutions, the page that is used is determined by the resolution of  the host workspace. This means you do not need to add the suffix  "_HD1080" or "_UHD4K" to the end of a name to specify a particular page. For more information, see [Configure a Project that Supports Multiple Screen Resolutions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Support_Multiple_Screen_Resolutions.htm). |
| **Content**      | Відокремлений комами список, який містить назви вмісту, пов’язаного з елементом обладнання. Це може включати сторінки, лицьові панелі та документи. Наприклад: Area1_Page_L1, Process1_Page_L2, Pump_Faceplate_FP. Цей вміст буде доступний під час виконання, коли обладнання потрапить у контекст. Якщо існують повторювані варіанти лицьової панелі або сторінки, які відповідають роздільній здатності екрана HD1080 і UHD4K, вміст, який викликається, визначається роздільною здатністю робочого простору хоста. Це означає, що вам не потрібно додавати суфікс "_HD1080" або "_UHD4K" в кінці імені. Додаткову інформацію див. у розділі [Налаштування проекту, який підтримує кілька роздільних можливостей](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Situational_Awareness_Support_Multiple_Screen_Resolutions.htm). |
| **Help**         | The help context string.  Enter a value of 254 characters or less. |
| **Comment**      | Any useful comment. Enter a value of 254 characters or less. |
| **Parameters**   | A list of parameters that are defined in Equipment Editor as [Custom Parameters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CustomParameters.htm) in an associated equipment type. This is a property list separated by semi-colon characters. For example:MyProp1=abc; MyProp2=def; MyProp3=123. This field is not available at runtime. |
| **Tag Prefix**   | Designed to  store a prefix that can be applied to the tags generated for the  equipment instance. It can be used at runtime to find tags associated  with the equipment. |
| **I/O Device**   | The I/O device  used to communicate with this piece of equipment. Specify redundant  devices with a comma between primary and standby, for example,  "IODev1,IODev2". Enter a value of 254 characters or less. |
| **Hidden**       | When set to true the Equipment will not be visible in the Equipment Tree at runtime.**Note**: The functionality of the Equipment does not change and will continue to function as configured. |

**Security Properties**

| Property | Description                                                  |
| -------- | ------------------------------------------------------------ |
| **Area** | The area number or label to which this equipment belongs. Only users with access to  this area (and any necessary privileges) will be able to perform  operations on the equipment. For example, if you enter Area 1 here,  operators need to have access to Area 1 (plus any necessary privileges)  to perform operations on the equipment. Enter a value of 16 characters  or less. |

**Custom Properties**

| Property               | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| **Custom1 .. Custom8** | User-defined  strings that can be used for filtering equipment when using the Cicode  search functions (maximum 254  characters each). Labels or tags are not  supported. |

**Scheduling Properties**

| Property                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| The following fields, **Default State** and **Scheduled**, are used  when configuring schedules for equipment (see [Configure Equipment for Scheduling](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Configure_Equipment_for_Scheduling.htm)). |                                                              |
| **Default State**                                            | The default state applied to the equipment.                  |
| **Scheduled**                                                | Specifies if the equipment is included in any scheduled actions. The options are "TRUE" or "FALSE".The following fields, **Schedule ID** and **Device Schedule**, are only required when using a schedule configured locally on a BACnet device (see [Integrate BACnet Schedules into Scheduler](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Integrate_BACnet_Schedules_into_Scheduler.htm)). They require the **Scheduled** property to be set to "TRUE". |
| **Schedule ID**                                              | The ID used to identify the required schedule on the BACnet device. This field is only required if the **Device Schedule** property is set to "TRUE". |
| **Device Schedule**                                          | Specifies  whether or not the report server should retrieve the required schedule  from the BACnet device. The options are "TRUE" or "FALSE". |



**Project Properties**

| Property    | Description                                            |
| ----------- | ------------------------------------------------------ |
| **Project** | The project in which the equipment type is configured. |



**Note:** Advanced users  can use the Project DBF plug-in for Microsoft Excel to edit and save  records directly in the EQUIP.DBF file (see [Use the Project DBF Add-In to Define Equipment Associations](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Use_the_ProjectDBF_Add-In_to_Edit_the_Equipment_Database.htm)).        