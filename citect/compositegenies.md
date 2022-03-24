## Composite Genies

[Help](file:///C:/Program%20Files%20(x86)/AVEVA%20Plant%20SCADA/Bin/Help/SCADA%20Help/Content/Composite_Genies.htm)

Композитний Джин — це набір окремих Джинів, зібраних у єдиний об’єкт. Окремі об’єкти та їх властивості означуються у файлі шаблону XML разом із макетами для колекції, тобто Composite Genie. Ви можете вставити кілька екземплярів складеного об’єкта на графічну сторінку та вказати різні параметри, включаючи значення, вирівнювання та параметри відображення для кожного екземпляра, щоб налаштувати Composite Genie відповідно до ваших вимог.

Наприклад, ви хочете створити дзеркальний об’єкт компресора, який може додатково відображати мітку, індикатор режиму та вимірювач поряд із символом. До Plant SCADA 2020 R2 ви могли створити окремі джини для кожної з перестановок, або ви могли створити одного джина, який використовував видимість для відображення/приховування елементів під час виконання. За допомогою Composite Genies ви можете просто вибрати [шаблон XML](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genie_Templates.htm) для компресора, який надає [набір параметрів представлення](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm) для налаштування мітки, орієнтації тощо. Все, що вам потрібно зробити, це встановити значення для цих параметрів і вставити об’єкт на сторінку.

| Without Composite Genies                                     | Using Composite Genies                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Замість того, щоб вставляти та налаштовувати окремих Genies:    ![img](media/GeniesCollection1.png)<br />Вам потрібно змінити макет і вирівнювання цих Джинів вручну | [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm):    ![img](media/CompositeGenie1.png)Усі [компоненти викладені акуратно](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Composite_Genie_Templates.htm) з параметрами вирівнювання та макета, які інженери можуть налаштувати. |
| Якщо ви додасте вказівку відповідного обладнання до свого компресора Genie вище, вирівнювання об’єктів потрібно відрегулювати для розміщення нового Genie:     ![img](media/GeniesCollection2.png) | З Composite Genie просто відкрийте [Параметри презентації](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm) і виберіть, щоб додати вихідний рядок, що призводить до:![img](media/CompositeGenie2.png) |

З використанням Composite Genies:

- Розмір бібліотек об’єктів можна значно зменшити, оскільки потрібно підтримувати лише один Composite Genie, а не підтримувати декілька перестановок кожного об’єкта, що використовується на графічних сторінках.

- Інженери можуть отримати більш чітке уявлення про дизайн своєї сторінки, оскільки Composite Genie відображає лише ті параметри, які були вибрані.
- Доступний розширений інтерфейс параметрів. Використовуючи XML-шаблон, дизайнери бібліотек можуть збагатити інтерфейс параметрів, що дозволяє операторам вибирати з різних макетів, режимів, представляє параметри з урахуванням залежностей, правил імен тощо.

Як і у випадку з Джинами та символами, Composite Genies можна вставити для використання на графічній сторінці, шаблоні або суперджині. Ви можете виконувати такі операції:

- [Insert a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Insert_a_Composite_Genie.htm)
- [Edit/Update a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Edit_Update_Composite_Genie.htm)
- [Delete Unused Composite Genie Instances](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Delete_Unused_Composite_Genie_Instances.htm)
- [Delete a Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Delete_a_Composite_Genie.htm)

### Вставте Composite Genie

Composite Genie можна вставити в будь-яку графічну сторінку, шаблон або Super Genie. Його не можна вставити в джина або символ.

**Примітка.** На зовнішній вигляд Composite Genies можуть впливати різні налаштування DPI. Рекомендується, щоб під час запуску Graphics Builder для параметра **Масштаб і макет** було встановлено значення "100%" у налаштуваннях **Дисплей** Windows™. Після зміни параметра «Масштаб і макет» для комп’ютера слід перезавантаження його.

To insert a Composite Genie:

1. Open Graphics Builder.
2. Click the **Paste Composite Genie** button in the Objects toolbox. 
3. ​    ![img](media/PasteCompositeGenie_32x29.png)

4. The Open dialog box is displayed.

5. Select the XML template for the Composite Genie from the list of templates.
6. **Note**: The template file that you select needs to be in located in the Composite Genies folder in the  current project folder (or one of its included projects).

7. Click **OK**. The Presentation Options dialog box is displayed.

![img](media/PresOptions1.png)    

1. Type or select the values for the parameters displayed. 
2. **Note**: Depending upon the options you choose, some items may be hidden or displayed. For example, on the  Meter Composite Genies, when you select the **Display Control Output** check box, the **Display Trend** and **Trend Type** options are displayed.

3. Use the **Search** box to search for parameters in the dialog box. Type the parameter name or part of the parameter name to locate a parameter.
4. **Note**: Clear the Search box before clicking **OK** on the Presentation Options dialog box.

5. Use the **Show only parameters with invalid input** option to display options for which incorrect or no values have been selected or specified.
6. Click **OK** to insert the Composite Genie, or **Cancel** to close the Presentation Options dialog box without inserting the Composite Genie.

**Note**: You cannot rotate or mirror a Composite Genie that has been inserted on a page.

### Edit/Update a Composite Genie

Щоб відредагувати параметри для існуючого Composite Genie:

1. Відкрийте Graphics Builder.
2. Клацніть, щоб вибрати вставлений Composite Genie.
3. Клацніть правою кнопкою миші Composite Genie і виберіть у контекстному меню **Редагувати Composite Genie**. Відобразиться діалогове вікно Параметри презентації з назвою екземпляра Composite Genie та ідентифікатором шаблону.
4. Відредагуйте необхідні параметри.
5. Натисніть **ОК**.

Подвійне клацання по ID шаблону вибирає ідентифікатор. Ви можете скопіювати ідентифікатор і використовувати його для пошуку повторюваних екземплярів шаблону в Провіднику Windows.

Якщо ви модифікуєте Composite Genie після використання його у своєму проекті, усі екземпляри Composite Genie можуть автоматично оновлюватися за допомогою останньої версії шаблону. Зміни, включаючи оновлення міток, джинів і макета, будуть поширені на всі екземпляри. Якщо шаблон оновлений, пов’язані екземпляри не оновлюватимуться.

**Примітка**: не слід змінювати властивості папки, в якій зберігаються екземпляри Composite Genie (%PROGRAMDATA%\AVEVA Plant SCADA 2020 R2\User\<Назва проекту>\_CompositionCaches). Не слід вручну видаляти чи змінювати файли в цій папці. Такі дії призводять до помилок під час вставки Composite Genies на графічні сторінки.

Якщо під час оновлення виникла проблема, з’являється повідомлення про помилку. У повідомленні детально описана причина та доступні варіанти вирішення проблеми. Помилка може виникнути, якщо Composite Genie не існує або якщо проект є помилковим.

Наприклад, якщо ви створюєте копію існуючого шаблону, але зберігаєте той самий GUID у XML-файлі скопійованого шаблону, ви побачите таке повідомлення:

![img](media/CG_Update_Error_590x345.png)    

**Update a Particular Instance**

Оновлення конкретного екземпляра Composite Genie дозволяє вам перевірити зміни в Composite Genie, не впливаючи на інші екземпляри об’єкта на інших сторінках.

To update a particular instance of a Composite Genie:

1. Open Graphics Builder. 
2. Update the Composite Genie template as required.
3. Double-click the instance represented by the template. The Presentation Options  dialog box is displayed with the modified parameters. For example if you have added a new parameter, the Presentation Options dialog should show the parameter.
4. Click **OK**. The changes including updates to labels, genies and layout will be propagated to this instance of the Composite Genie.
5. Save the page. 

**Note**: Before you  apply the changes to all instances of Composite Genies across all pages, verify the changes using the instructions above.

**Update All Instances**

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

![img](media/Clear_CGCache_Pack.png)    

1. Click **Yes**. All unused instances of Composite Genies will be deleted.

### Delete a Composite Genie

To delete a Composite Genie:

1. Open the page in which the Composite Genie has been inserted.
2. Click to select the Composite Genie.
3. Press the **Delete** key. This will remove the Composite Genie from the page.
4. Save the page.

### Composite Genie Templates

Plant SCADA надає широкий асортимент готових композитних Genies у формі XML-шаблонів. Шаблон XML містить означення Composite Genie. Інженер бібліотеки може змінити існуючий шаблон XML або створити нові шаблони, що означують їхні власні Composite Genies. Рекомендується зробити копію шаблону перед його зміненням, щоб шаблони не перезаписувалися під час повторної інсталяції Plant SCADA.

**ВАЖЛИВО**: якщо ви робите копію шаблону, вам потрібно призначити новий GUID шаблону та всім композиціям у шаблоні. Для отримання додаткової інформації див. [Visual Template](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Visual_Template.htm) і [Compositions](file:// /C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Composites.htm).

Шаблони XML для Composite Genies знаходяться в папці `%PROGRAMDATA%\AVEVA Plant SCADA 2020 R2\User\<ім’я проекту>\Composite Genies`.

Файл **CompositionTemplate.xsd**, розташований у `%PROGRAMFILES(X86)%\AVEVA Plant SCADA\Bin`, містить схему для шаблонів Composite Genie XML. Цей файл описує елементи та атрибути, які можуть міститися в шаблоні XML для Composite Genie, а також порядок, у якому елементи та атрибути потрібно додати до шаблону XML. Файл шаблону XML перевіряється щодо файлу XSD. Коли ви змінюєте шаблон XML або створюєте новий, рекомендується використовувати хороший XML-редактор, який підтримує виявлення помилок схеми, щоб помилки були виділені та їх можна було легко виправити.

Помилки можуть виникнути, якщо файл XML для Composite Genie не відповідає означенням у базовому XSD. Крім того, помилки можуть виникати, якщо є повторювані ідентифікатори елементів, невизначені умови тощо. В обох випадках повідомлятимуться про помилки з деталями номера рядка та положення помилки, коли оператор вставляє Composite Genie на сторінку. Додаткову інформацію див. у розділі [Редагувати/оновлювати Composite Genie](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Edit_Update_Composite_Genie.htm).

An XML template for a Composite Genie contains the following elements:

- [Visual Template](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Visual_Template.htm)
- [Parameters](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Parameters.htm)
- [Content Items](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Content_Items.htm)
- [Compositions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Composites.htm)
- [Conditions](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Conditions.htm)
- [Alarm Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_AlarmIndicators.htm)

Кожен з цих елементів детально пояснюється в розділах нижче. Рекомендується переглянути ці розділи, перш ніж змінювати існуючі шаблони XML або створювати нові шаблони.

#### Visual Template

Цей розділ містить стандартні декларації XML. Крім того, цей розділ містить GUID, який є унікальним ідентифікатором для шаблону XML.

**Примітка**: якщо ви змінюєте існуючий шаблон або створюєте новий шаблон Composite Genie, ви повинні перевірити XML-файл, завантаживши файл означення схеми (CompositionTemplate.xsd, який знаходиться в папці `<Папка інсталяції Plant SCADA>\bin `) у свій XML-редактор.

Якщо ви створюєте власного Composite Genie, вам потрібно буде створити для нього GUID. Для створення GUID доступно кілька онлайн-інструментів.

Щоб створити GUID:

1. Знайдіть термін «генерувати GUID» у браузері за допомогою будь-якої пошукової системи. Відобразиться список веб-сайтів, які можуть генерувати GUID.
2. Відкрийте будь-який із сайтів.
3. Виберіть формат для GUID. Формат GUID має включати дужки та дефіси і має бути у верхньому регістрі. Наприклад, `{1E49C603-FCBC-4913-ABD1-97920283C6BD}`.
4. Згенеруйте GUID.

**Example**

![img](media/CG_VisualTemplate_505x114.png)    

#### Parameters

Елемент `<Parameter>` означує атрибути, які будуть відображатися як параметри презентації для користувача, коли він вставляє Composite Genie на графічну сторінку. Він складається з наступних атрибутів для кожного параметра:

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

Визначення параметрів можуть включати елемент `<Dependency>` для відображення або приховування параметрів. Цей елемент може використовувати умови Global, Parameter або Composite, щоб показати або приховати параметр на основі вибору опції або значення оператором. Для отримання додаткової інформації про умови зверніться до [Умови](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Conditions.htm).

**Простий приклад **

Це простий приклад, коли залежність була означена за допомогою елемента `<Dependency>`, щоб показати параметр **Label**, лише якщо оператор вибрав прапорець **Відображати мітку**. Це досягається за допомогою використання [Global Condition](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_Conditions.htm). Ви також можете використовувати параметри та/або складені умови в елементі `<Dependency>`.

![img](media/CG_ParametersSimpleCode.png)    

Наведений вище код відобразить такі параметри презентації.

![img](media/CG_Presentation_Options_Simple.png)    

**Складний приклад**

Цей приклад надає трохи складніший сценарій з параметрами, які відображаються на основі вибору значення оператором. Тому необхідно означити список значень і залежність.

- Зверніться до XML-коду для параметра “Number of sub equipment”. Цей параметр може приймати значення 0, 1, 2, 3, 4 або 5. Атрибут `<Values>` визначає цей список значень, які можна вибрати (див. зразок коду нижче).

![img](media/CG_CompressorCodeValues.png)    

- Залежно від значення, яке оператор вибирає для цього параметра, будуть відображатися параметри допоміжного обладнання. Наприклад, якщо оператор вибирає 0 для параметра  “Number of sub equipment”, параметр Sub Equipment не відображатиметься, якщо користувач вибирає 1, відображатиметься один параметр Sub  Equipment  з міткою Sub Equipment #1 Name, якщо користувач вибере 2, відображатимуться два параметри Sub Equipment з мітками Sub Equipment #1 Name та Sub Equipment #2 Name тощо. Користувач може вибрати до 5 одиниць додаткового обладнання.
- Щоб мати можливість вибрати 5 одиниць допоміжного обладнання, потрібно означити параметр для кожної частини допоміжного обладнання. Крім того, для кожного з цих параметрів повинна бути визначена залежність (див. нижче приклад коду, який показує визначення для двох частин підобладнання).
- Залежність визначається за допомогою атрибута `<Dependency>`. Для допоміжного обладнання 1 має бути задоволена глобальна умова «Show_MEO1». Щоб отримати детальну інформацію про умови, перегляньте розділ Умови.

![img](media/CG_CompressorCodeParameters.png)    

![img](media/CG_Presentation_Options_Complex.png)    

#### Alarm Indicators

Елемент `<AlarmIndicators>` є додатковим елементом для відображення [індикаторів тривоги](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/Alarm_Indicator.htm) для обладнання. Він містить такі дочірні елементи:

| Element       | Description                                                  | Attribute                 | Description                                                  |
| ------------- | ------------------------------------------------------------ | ------------------------- | ------------------------------------------------------------ |
| EquipmentLink | Defines each piece of related  equipment for which an alarm needs to be displayed. | Id                        | A unique string  identifier with which `<AlarmIndicator>` elements in  compositions can refer to the forward-declared equipment link. |
|               |                                                              | TemplateParameter         | Name of the template parameter.  The value of this is used as the equipment expression of the alarm indicator.  The template parameter needs to be defined in the  `<Parameters>` element in the same document. |
|               |                                                              | IncludeEquipmentReference | Set this to 'true' to include  equipment references when determining the highest priority alarm for the  alarm indicator. Set this to 'false' if you do not want to include equipment  references. |
|               |                                                              | Hierarchy                 | Node in the equipment hierarchy  that will be used to determine the highest priority alarm for the alarm  indicator. You can set this to include equipment that occur at nodes down the  equipment hierarchy (referred to as "children"). Set this to one of  the following:EquipmentOnly     EquipmentAndChildren     ChildrenOnly |
| BorderStyle   | Defines the alarm display  settings.                         | Id                        | A unique string identifier with  which `<AlarmIndicator>` elements in compositions can refer to the  forward declared border style. |
|               |                                                              | Width                     | Sets the width of the alarm  border (in pixels).             |
|               |                                                              | Padding                   | Sets the amount of space (in  pixels) between the extent of the object group or Genie and the inside edge  of the alarm border. |
|               |                                                              | IsInside                  | Set this to 'true' to place the  border within the extent of the object group or Composite Genie. Note that  you cannot set a padding in this case. |
|               |                                                              | IsDefault                 | Set this to 'true' to make this  border style the default style. |

**Note**: An alarm indicator is applied  to all equipment items within the Composite Genie. The items are  automatically grouped and the alarm border is applied to the composite  if there are more than two visible items in the container. 

**Example**

![img](media/CG_AlarmIndicator.png)    

#### Content Items

The `<ContentItems>` element defines  the library objects (Genies) that are available to be included in  compositions for the Composite Genie. It contains one or more  `<ContentItem>` child elements, each of which comprises the  following attributes:

| Attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| Id        | Unique numeric identifier within the `<ContentItems>` section.  **Note**: You should not use the same numeric Id for more than one `<ContentItem>` elements. Doing so would result in an error when the system reads this visual template document. |
| Type      | This is set to the type of the object that makes up the Composite Genie and should not be modified. **Note**: In this version Composite Genies constitute only Genies. So, Type is set to “Genie” in the XML templates. |
| Project   | Name of the project  which contains the referred library object. The project needs to be  either the same as the project in which the visual template resides or  one of its include projects. **Note**:  If the  project is renamed, the Genie will not be available for use unless this  attribute is modified in the XML template. Keep this in mind when  renaming a project. |
| Library   | Name of the object library to which this item belongs.       |
| Item      | Name of the item to be included in the Composite Genie.      |

**Note**: You need to explicitly define each and every item that you want to include in your compositions.

**Example**

Each line in the code below defines an item, in this case a Genie, that will be available to be included in a composition.

![img](media/CG_ContentItmesCode.png)    

#### Compositions

The `<Composition>` element details the “composition” of the Composite Genie, that is, the possible layouts,  parameter conditions and parameters that constitute the Composite Genie.  It contains multiple elements each with a set of attributes.  Typically, the XML template for a Composite Genie is made up of several  compositions to represent the different layouts available. Each  composition can define only one layout. The template needs to have at  least one composition.

| Attribute      | Description                                                  |
| -------------- | ------------------------------------------------------------ |
| Composition Id | Unique identifier for the composition. This is an ID that is generated using the GUID Generator tool. |

**Example**

![img](media/CG_CompositionIdCode.png)    

##### Prerequisites

Within a composition, one or more  prerequisites may be defined within the <Prerequisite> element.  Prerequisites  are made up of conditions, which are evaluated at  runtime. If a prerequisite is true, the corresponding composition will  be applied. Otherwise, the next composition will be evaluated, and a  composition will be applied only when the prerequisite is satisfied.  Prerequisites are applied sequentially.  For more information, refer to  the Conditions topic.

**Note**: When defining conditions, it  is recommended that you start with the most complex condition first and  then add conditions in decreasing order of complexity. This is so that  the most specific composition is selected for the Composite Genie.

| Attribute          | Description                                                  |
| ------------------ | ------------------------------------------------------------ |
| GlobalConditionRef | Used to refer to a predefined Global condition               |
| ParameterCondition | Used to specify conditions by comparing a template parameter value to a predefined value. |
| CompositeCondition | Used to combine  more than one condition with either AND or OR relation specified in its  attribute. Its child conditions can be made up of predefined Global  conditions `<GlobalConditionRef Id="..."/>`, a Parameter condition  and nested Composite conditions. |

**Example**![img](media/CG_Prerequisite.png)    



##### Container

The Container element is mandatory, and contains the details of the layout, Plant SCADA content items (library objects) to be included in the Composite Genie,  their alignment and other display options such as margins (left, right,  top and bottom).

| Attribute      | Description                                                  | Attribute                                                    | Description                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Layout         |                                                              | Hotspot                                                      | Specifies the page co-ordinates where the Composite Genie is placed when inserted on to a page. |
| Container      | Defines the layout options for the Composite Genie including the alignment, margin and stacking options. | Margin                                                       | Positioning (left, top, right and bottom margins) of the object on the page relative to the alignment. |
|                | Layout                                                       | Specifies how the container is laid out - Stacked Horizontal, Stacked Vertical or 				Overlaid. For more information, refer to the More about Layouts section. |                                                              |
|                | VisibleWhen                                                  | Used to show/hide the container based on a Global condition. The container will be visible only when the condition is satisfied. |                                                              |
|                | CreateGroup                                                  | Determines whether the  contents of the container will be a group. When the contents of a  container are in a group, the placement of the contents are  automatically adjusted to accommodate the largest object/text when the  container is re-sized and also at runtime if animations are included. By default, the contents of a container are placed in a group. If the  contents are not grouped, each item needs to be re-sized and placed  manually. You can use the GoTo Object dialog to view the hierarchy of  items in a container.**Note**: The size of a container is defined by the biggest object in the container. |                                                              |
|                | AnimationName                                                | Sets the animation name to apply to the object. This is unique to the layout.**Note**: An  animation name should begin with a letter and contain only  letters,  numbers and the following symbols: _, %, $, @ and #. It should not  exceed 26 characters. |                                                              |
|                | HorizontalAlignment                                          | Sets the alignment of the container to display horizontally within its parent. |                                                              |
|                | VerticalAlignment                                            | Sets the alignment of the container to display vertically within its parent. |                                                              |
|                | ZIndex                                                       | Determines the position of the container when multiple containers are overlaid. The object with the lowest ZIndex is stacked on top of the pile while the object with  the highest ZIndex is placed at the bottom of the stack of containers.  The ZIndex is relative within a container whether or not objects in the  container are grouped. For more information, refer to the More about  Layouts section. |                                                              |
| AlarmIndicator | Sets the alarm indicator that needs to be displayed for this composition. | VisibleWhen                                                  | Alarm Indicator will be displayed if the condition specified here is satisfied. |
| EquipmentLink  | Reference to the Alarm Indicator to be displayed as defined in the <AlarmIndicators> element. |                                                              |                                                              |
| BorderStyle    | Reference to the border style to be used for the Alarm Indicator as defined in the <AlarmIndicators> element. |                                                              |                                                              |
| Content        | Defines the Plant SCADA content items that are available within this composition. | Item ID                                                      | Reference to the Plant SCADA content item such as a Genie. Each item included here should have been included in the <ContentItems> element. |
|                | HorizontalAlignment                                          | Whether the item will be left, right or center-aligned.      |                                                              |
|                | VerticalAlignment                                            | Whether the item will be top, middle or bottom aligned.      |                                                              |
|                | Margin                                                       | Left, top, bottom and right margins. For information, see the More about Margins topic. |                                                              |
|                | VisibleWhen                                                  | Item will be displayed if the condition specified here is satisfied. |                                                              |
|                | AnimationName                                                | Name of the item as configured in the General Access properties.**Note**: An  animation name should begin with a letter and contain only  letters,  numbers and the following symbols: _, %, $, @ and #. It should not  exceed 26 characters. |                                                              |
|                | ZIndex                                                       | Determines the position of the item when multiple items are overlaid. The item with the lowest  ZIndex is placed on top of the stack. |                                                              |
| Parameter      | For each item that you  add to a composition, you need to link it to a parameter defined in the  XML template. This is done so that the value of the parameters can be  passed into the substitution in the content item (for example,  %Equipment%) through the Composite Genie. | Name                                                         | Name of the  substitution parameter specified without the % (for example, "Equipment" for %Equipment% substitution). This name is case sensitive. |
|                | TemplateParameter                                            | Name of parameter as specified in the Parameter element, the value of which is passed into the substitution in the content item. |                                                              |

**Example - Layout**

This example shows the Hotspot co-ordinates for positioning the Composite Genie at a particular location on the page.

![img](media/CG_Layout_HotSpot.png)    

**Example - Container**

This example shows the code for a container, which includes:

- layout options for the container and conditions when it is to be displayed (using the VisibleWhen attribute)
- content items and conditions when they are to be displayed (using the VisibleWhen attribute)
- parameters to be passed into template parameters     ![img](media/CG_LayoutCode.png)    

###### More about Margins and Alignment

Margins and alignment determine the positioning of a Composite Genie. They can be use in conjunction to set the [layout](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_More_About_Layouts.htm) of Composite Genies. 

**Margins**

Margins may be specified  for a container or a content item within a container. Margins can be  used to set the distance between an object and its child, and determine  the positioning of an object relative to its parent. Margins are  specified as a set of four numbers separated by a comma. For example, 2, 0,1,3. Here 2 is the Left margin, 0 is the Top margin, 1 is the right  margin and 3 is the bottom margin. The values for margins may be the  same or different depending upon your requirements. Margins are  specified in pixels.

Margins are applied to the  container as a whole, and/or to each individual item. For example, a  container margin of 2 pixels for the left, top, right and bottom can be  defined with:

![img](media/CG_Container_margins.png)    

This will apply a 2-pixel margin to the group of items within the container.

Margins can be applied to an item within the container as follows:

![img](media/CG_ContainerMargins1.png)    

This will apply a 2-pixel margin on all sides of the object that has the ItemID 1.

![img](media/CG_Margins.png)    

**Alignment**

HorizontalAlignment

The HorizontalAlignment attribute sets the alignment that will be applied to child objects. It can set to:

- Left - Child objects are aligned to the left of the parent object's allocated space.
- Center - Child objects are aligned to the center of the parent object's allocated space.
- Right - Child objects are aligned to the right of the parent object's allocated space.

![img](media/CG_HorizontalAlignment.png)    

VerticalAlignment

The VerticalAlignment attribute sets the alignment that will be applied to child objects. It can be set to:

- Top - Child objects are aligned to the top of the parent object's allocated space. 
- Center - Child objects are aligned to the center of the parent object's allocated space. 
- Bottom - Child objects are aligned to the bottom of the parent object's allocated space.

![img](media/CG_VerticalAlignment.png)    

###### More about Layouts

Layouts can be defined at the container  level or at the object level. It is recommended that layout attributes  be defined for the parent object with respect to the positioning  required for the child object as shown in the examples below. 

**Note**: It is recommended that you group objects if you have changing animations, size or positions at runtime.

Layouts are of the following types:

- **StackedHorizontal**:  Objects are aligned from left to right. By default, the objects as a  group, are center aligned. To top- or bottom-align the objects within  the group, set the VerticalAlignment attribute to “Top” or “Bottom”,  respectively.  This needs to be set in in the XML template. If you have  two objects in a group, you need to specify the vertical alignment only  for the second item. The second item will then be aligned relative to  the first one. Use the Margin attribute to control overlap of objects. A negative margin setting will position an item closer to the object next to it.

- **StackedVertical**: Objects  are aligned from top to bottom. By default, the objects, as a group, are center aligned. To left- or right-align the objects within the group,  set the HorizontalAlignment attribute to “Left” or “Right”,  respectively. If you have two objects in a group, you need to specify  the horizontal alignment only for the second object. The second item  will then be aligned relative to the first object. This needs to be set  in in the XML template. Use the Margin attribute to control overlap of  objects. A negative margin setting will position an item closer to the  item below it.

- **Overlaid**: All objects are placed at the same spot, and the order in which they are placed is  controlled by the value of the ZIndex.  The object with the lowest  ZIndex will be at the top of the overlaid stack. Bigger objects can be  stacked at the bottom and overlaid with smaller objects with the  smallest object on the top.

**Example: StackedHorizontal**

![img](media/CG_StackedHorizontal_315x280.png)    

![img](media/CG_StackedHorizontal_Overlap_351x206.png)    

**Example: StackedVertical**

![img](media/CG_StackedVertical.png)    

![img](media/CG_StackedVertical_Overlap.png)    

**Example: Overlaid**

![img](media/CG_Overlaid1_504x228.png)    

![img](media/CG_Overlaid2_284x180.png)    

##### More about Alarm Indicators

Alarm indicators may be applied to a  Composite Genie as a group or to an individual Genie within the  composite. Alarm indicators can be applied in one of two ways:

- Using the pre-defined alarm indicators from the <AlarmIndicators> attribute. For more information see, [Alarm Indicators](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_AlarmIndicators.htm).
- Making a declaration within a composition using the <AlarmIndicator> attribute (see the example below).

**Example**

In the examples below, we have defined alarm indicators within the composition instead of using the pre-defined indicators. 

In the example below, the  alarm indicator has been defined for the container using the  <AlarmIndicator> attribute. The alarm indicator will be visible  around the Composite Genie with the specified width and padding when the condition is satisfied. 

![img](media/CG_AlarmInd_Container.png)    

You can also define an  alarm indicator for a specific content item (Genie) using the  <AlarmIndicator> attribute. The alarm indicator will be visible  only around the content item with the specified width and padding when  the "VisibleWhen" condition you have specified is satisfied.

**Note**: If a condition is not defined, the alarm indicator will be displayed regardless of user input.

#### Conditions

Conditions can be used for defining  dependencies in a composition. For example, if a parameter needs to be  displayed based on the value selected for another parameter or a  composition needs to be applied based on a set of conditions. Conditions are of the following types:

- Global Conditions
- Parameter Conditions
- Composite Conditions

The order in which conditions are defined  is important because only a condition defined later can use conditions  defined before it. This is to avoid cyclical reference. For example, you have defined Global condition “MEO” first followed by condition  “SmallMeter”. The “SmallMeter” condition can use “MEO” as a Parameter  condition, but the “MEO” condition cannot use the “SmallMeter” condition (shown in Example 1 below).

Before going through details about the  types of conditions, it is important to understand operators that can be used to define conditions. The section below provides details of the  different types of operators.

**Operators**

Conditions can be defined with the help of operators. Operators are of two types:

- Logical – This include “AND” and “OR”. These operators can be used when defining Composite conditions.
- Comparison – The following comparison operators are available to perform comparisons for string, integer and Boolean values:

| Operator               | Used for Comparing Values of Data Types... |
| ---------------------- | ------------------------------------------ |
| IsEqualTo              | Boolean, String and Integer                |
| IsNotEqualTo           | Boolean                                    |
| IsGreaterThan          | Integer                                    |
| IsGreaterThanOrEqualTo |                                            |
| IsLessThan             |                                            |
| IsLessThanOrEqualTo    |                                            |
| StartsWith             | String                                     |
| EndsWith               |                                            |
| Contains               |                                            |

**Global Conditions**

Global conditions are  conditions that  need to be used frequently within an XML template. They are defined once and can be used anywhere within an XML template to  incorporate parameter dependencies or selection of a composition. Global conditions can also be used:

-  to pre-define the components of the Composite Genie that can be enabled or disabled
- in determining parameter dependency, and can be used in one or more compositions within the XML template. 

They may include nested Parameter as well as Composite conditions (shown in Example 2 below).

Global conditions are defined using the GlobalCondition element, which comprises the following attributes:

| Attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| Name      | User friendly name for the condition, which needs to be unique. |

Example

In this example, the Global condition “Show_LabelPadding” is met when the one of the predefined  Global conditions in the Composite condition is met.

![img](media/CG_GlobalCondition.png)    

Example

This example shows a nested condition that can be used to evaluate a Global condition.

![img](media/CG_NestedCondition.png)    

**Parameter Conditions**

Parameter conditions can be used in a composition within the Prerequisite element to determine the  composition that will be selected based on user input and to toggle  visibility of a parameter. Parameter conditions are also used to define  Global conditions. The attributes of a Parameter condition include:

| Attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| Name      | User friendly name for the condition, which needs to be unique. |
| Value     | Expected value of the parameter against which the condition will be evaluated. |

Example

![img](media/CG_ParameterCondition.png)    

**Composite Conditions**

Composite conditions are  conditions that are joined together with the AND or OR operator and  function as a group. Composite conditions can be made up of Global or  Parameter conditions.

| Attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| Operator  | This can be set to “AND” or “OR” and determines how the conditions needs to be evaluated. |

Example

In the sample code, two parameter conditions are joined together using the AND operator.

![img](media/CG_CompositeCondition.png)    

##### Alarm Indicators and Alarm Flags

Alarm indicators and alarm flags are  defined using Global conditions, and are included within a composition  to be made visible to the user via the Presentation Options dialog box.

Given below is the code snippet for the Global condition that defines an alarm indicator.

 ![img](media/CG_AlarmBorder.png)

Alarm indicators can be displayed on a Composite Genie and/or the related equipment associated with it (shown below).

![img](media/CG_AlarmBorder_Display.png)    

Given below is the code snippet for the Global condition that defines an alarm flag and its positioning. 

![img](media/CG_AlarmFlag_917x459.png)    

Alarm flags need to be included in a composition within the [ element](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Content/CG_AlarmIndicators.htm) for them to displayed in the Presentation Options dialog box. 

![img](media/CG_AI_AFlag_960x249.png)    

The triggers are used to define FlagStyle  conditionally. When none of the When conditions is satisfied, the  FlagStyle is set to the fallback value specified by <AlarmIndicator  FlagStyle=”<fallback_value>”> element.

You can also set up the FlagStyle attribute within <AlarmIndicator> without Triggers. The FlagStyle attribute is “Hidden” by default if it is not specified.

An alarm flag can be positioned at one of the following locations: 

- None : Alarm flag is not displayed. This is the default.
- Top Left
- Top Center
- Top Right
- Center Left
- Center Right
- Bottom Left
- Bottom Center
- Bottom Right

**Note:** If you change  the size of an alarm flag and run the Update Pages command, the  Composite Genie instances are re-sized to accommodate the size of the  alarm flag.

​    ![img](media/CG_AlarmFlag_Display.png)