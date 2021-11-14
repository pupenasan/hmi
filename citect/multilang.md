## Languages

Citect SCADA supports a language switching capability that allows text within the  runtime environment to be translated into a variety of languages. 

Items such as alarm descriptions, button text,  keyboard/alarm logs, graphics text and Cicode strings can be marked for  translation during the configuration of a project, and then displayed in a specified language at runtime.  A project can support multiple  languages, and you can dynamically switch between them.

 **Note:** Text translation  does not happen automatically. A language can only be supported if the  required translations are manually inserted into localized language  databases.

To enable your runtime system to switch between different languages, your firstly need to mark the text you would like  translated and locate the required translations. See [Prepare a Project for Multi-language Support](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Prepare_a_Project_for_Multi-language_Support.html). 

You will then be able to:

- [Set the Local Language Used at Runtime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Set_the_Local_Language_Used_at_Runtime.html)            
- [Change the Local Language during Runtime](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Change_the_Local_Languages_at_Runtime.html).

### Set the Local Language Used at Runtime

 The default local language that gets displayed at runtime is determined by the Citect.ini parameter  [Language]LocalLanguage. However, the language entered in this parameter should be pre-defined in the Lang.dbf file. 

Once this parameter is set (and the steps outlined in [Prepare a Project for Multi-language Support](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Prepare_a_Project_for_Multi-language_Support.html) are complete), you can then configure either the Login(), UserLogin()  or LoginForm() functions to set the preferred language for the project  at runtime. When the user logs in to the project, any marked native text will be replaced by the preferred language defined in the corresponding .dbf file. Be aware that changing languages at runtime will cause any  open pages to reload. 

**Note:** To use  characters for Baltic, Central European, Cyrillic, Greek, Turkish, and  Asian languages, or right-to-left languages (Arabic, Hebrew, Farsi, and  Urdu) the operating system needs to have the corresponding language  version of Windows, or have installed system support for that language.

### Prepare a Project for Multi-language Support

To  prepare a project for multi-language support, you need to consider the following procedures:

- **Defining the languages supported by a project**            
- A Citect SCADA project includes a database named LANG.dbf. This database specifies  which local languages you would like a project to support. During  compilation, a local language database is created for each language  defined in LANG.dbf. 

- See [Define the Languages Supported by a Project](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Define_the_Languages_Supported_by_a_Project.html).

- **Translating the language databases**            
- Local language databases are used to define the translations from native language to local language. When a  project is compiled, any text that is marked for translation is drawn  into the supported language databases. You can then manually edit a  databases to define the translations required for the specified  language. Recompiling the project will then capture the translations you have input.

- See [Translate a Local Language Database](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Translate_a_Local_Language_database.html).

- **Marking text and alarm text for translation**            
- Language change indicators are used to identify any text you would like translated at runtime. 

- Citect SCADA distinguishes between a project's *native* language (that is, the language used by the developer during configuration), and the *local* language (the language displayed to the end user). Based on this  principle, any text marked with a language change indicator can be  converted from native language to a local language at runtime.

- See [Mark Text for Translation](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Mark_Text_for_Translation.html) and for alarm specific strings [Mark Alarm Text for Translation](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Mark_Alarm_Text_for_Translation.html).

- 

#### Define an Unsupported Language 

The format for specifying an unsupported language is: `<LanguageName>(<RegionName>)`

При необхідності ви можете вказати в мовній базі даних (LANG.DBF) мови, які [офіційно не підтримуються](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Content/Officially_Supported_Languages.html) від Citect SCADA.

Формат для визначення непідтримуваної мови має відповідати визначенням мови та регіону Windows.

Формат для визначення непідтримуваної мови: `<Назва мови>(<RegionName>)`

Наприклад,

«Hebrew(Israel)», де назва мови — «Hebrew», а назва регіону — «Israel».

«Chinese (Traditional)(Taiwan)», де назва мови — «Chinese (Traditional)», а назва регіону — «Taiwan».

Якщо в LANG.DBF вказано непідтримувану мову та використовується під час входу (тобто з функціями Cicode LoginForm(), Login() або UserLogin()), середовище виконання відобразить рядок підказки «Unsupported language» та відобразить вміст вказаною мовою.

Якщо зазначена мова не підтримується, деякі системні тексти відображаються англійською, а не вказаною мовою, як-от поле повідомлення SOE. Можливо, система не зможе визначити набір символів мови, яка не підтримує Citect SCADA. У цьому випадку вам потрібно надати бажані набори символів:

- встановивши`[Language]CharSet = <value>`,
- викликавши `ParameterPut("Language", "CharSet", <value>)`

Підтримувані значення для `<value>`:

- 0 - ANSI ASCII
- 1 - System Default Character Set
- 128 - Japanese - Shift JIS 
- 129 - Korean - Hangul 
- 130 - Korean - Johab 
- 134 - Chinese - simplified GB2312 
- 136 - Chinese - traditional Big5 
- 161 - Greek 
- 162 - Turkish
- 163 - Vietnamese 
- 177 - Hebrew 
- 178 - Arabic 
- 186 - Baltic 
- 204 - Russian
- 222 - Thai 
- 238 - East European

#### [CtEdit]SuppressCompilerWarning

Allows suppression of specific compiler warning messages using an associated warning message number. 

When a compiler warning message is displayed, it will include a number prefixed by "W". For example:

 The specified language is not supported (W1027)

To suppress a particular type of warning  message, apply the associated warning number to this parameter. For  example, to suppress the unsupported language message demonstrated  above, set the parameter to the following value:

[CtEdit]SuppressCompilerWarning=W1027

**Allowable Values**: One or more warning message numbers. If more than one is used, separate them with commas.

**Default Value**: No messages suppressed.