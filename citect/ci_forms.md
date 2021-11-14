# Form Functions

Following are functions relating to forms:

| FormActive         | Checks if a form is currently active.                        |
| ------------------ | ------------------------------------------------------------ |
| FormAddList        | Adds a text string to a list box or combo box.               |
| FormButton         | Adds a button to a form.                                     |
| FormCheckBox       | Adds a check box to the current form.                        |
| FormComboBox       | Adds a combo box to the current form.                        |
| FormCurr           | Gets the current form and field handles.                     |
| FormDestroy        | Removes a form from the screen.                              |
| FormEdit           | Adds edit fields to a form.                                  |
| FormField          | Adds general fields to a form.                               |
| FormGetCurrInst    | Gets data associated with a field.                           |
| FormGetData        | Gets the data associated with a form.                        |
| FormGetInst        | Gets data associated with a field on a form.                 |
| FormGetText        | Gets field text on an active form.                           |
| FormGoto           | Go to a specified form.                                      |
| FormGroupBox       | Adds a group box to the current form.                        |
| FormInput          | Adds an input field to a form.                               |
| FormListAddText    | Adds a new text entry to a combo box or a list box.          |
| FormListBox        | Adds a list box to the current form.                         |
| FormListDeleteText | Deletes existing text from combo box or list box.            |
| FormListSelectText | Selects (highlights) a text entry in a combo box or a list box. |
| FormNew            | Creates a new form.                                          |
| FormNumPad         | Provides a keypad form for the operator to add numeric values. |
| FormOpenFile       | Displays a File Open dialog box.                             |
| FormPassword       | Adds a password (no echo) input field.                       |
| FormSecurePassword | Adds a secure password (no echo) input field.                |
| FormPosition       | Sets the position of a form on the screen, before it is displayed. |
| FormPrompt         | Adds a prompt to a form.                                     |
| FormRadioButton    | Adds a radio button to the current form.                     |
| FormRead           | Displays a form and reads user input.                        |
| FormSaveAsFile     | Displays a File Save As dialog box.                          |
| FormSelectPrinter  | Displays the Select Printer dialog box.                      |
| FormSetData        | Sets data in a form.                                         |
| FormSetInst        | Associates data to a field on a form.                        |
| FormSetText        | Sets field text on an active form.                           |
| FormWndHnd         | Gets the window handle for the given form.                   |

## FormNew

Creates a new data  entry form and defines its size and mode. After the form is created, you can add fields, and then display the form.

Before you can display a form on the screen,  you need to call this function to set the size and mode of the form, and then call the various form field functions, FormInput(), FormButton(),  FormEdit() etc to add user input fields to the form. To display the form on the screen (to allow the user to enter data) call the FormRead()  function.

Syntax

```c
FormNew(Title, Width, Height, Mode)
```

*Title:*The title of the form.

*Width:* The character width of the form (1 to 131).

*Height:* The character height of the form (1 to 131).

*Mode:*The mode of the form:

*0* - Default font and text spacing

*1* - Small font

*2* - Fixed pitch font

*4* - Static text  compression where the vertical spacing is reduced. This can cause  formatting errors if buttons are too close, because the vertical spacing will be less than the height of a button.

*8* - Keep the form on top of the Citect SCADA window.

*16* - The current window cannot be changed or closed until the form is finished or cancelled.

*32* - Makes a form with no caption.

*128* - The form will not close if the **ESC** or **ENTER** key is pressed, unless you specifically define at least one button on the form which acts as an **OK** or **Cancel** button. For a form with no buttons, the **ENTER** key normally closes the form; this mode disables that behavior.

256 – Makes a from with no system-menu (mostly appears as a single close button X) .

Multiple modes can be selected by adding them (for example, to use Modes 4 and 2, specify Mode 6).

Return Value

The form handle if the form is created  successfully, otherwise -1 is returned. The form handle identifies the  table where all data on the associated form is stored.

Example

```c
FormNew("Recipe",30,5,0);
FormInput(1,1,"Recipe No",Recipe,20);
FormInput(1,2,"Amount",Amount,10);
FormRead(0);
```