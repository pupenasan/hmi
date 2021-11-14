# CICODE

## Working with Operators

### Using Mathematical Operators 

Standard mathematical operators allow you to  perform arithmetic calculations on numeric variables - integers and  floating point numbers.

| Operator | Description         |
| -------- | ------------------- |
| +        | Addition            |
| -        | Subtraction         |
| *        | Multiplication      |
| /        | Division            |
| MOD      | Modulus (Remainder) |

Example

The following are examples of mathematical operators

| Command                     | Comment                                                      |
| --------------------------- | ------------------------------------------------------------ |
| PV12 = PV10 + PV11;         | PV12 is the sum of PV10 and PV11                             |
| Counter = Counter - 1;      | The value of Counter is decreased by 1                       |
| PV12 = Speed * Counter;     | PV12 is the product of Speed and Counter                     |
| Average = Total / ShiftHrs; | Average is Total divided by ShiftHrs                         |
| Hold = PV12 MOD PV13;       | If PV12 = 10 and PV13 = 8, Hold equals 2(the **remainder** when PV12 is divided by PV13) |

**Note:** Cicode uses the standard order of precedence, that is multiplication and division are calculated  before addition and subtraction. In the statement A=1+4/2, 4 is divided  by 2 before it is added to 1, and the result is 3. In the statement  A=(1+4)/2 , 1 is first added to 4 before the division, and the result is 2.5.

You can also use the addition operator (+) to concatenate (join) two strings.

| **Operator** | **Description** |
| ------------ | --------------- |
| +            | Concatenate     |

Example

| Command | Message = "For info see " + "Supervisor";    |
| ------- | -------------------------------------------- |
| Comment | Message now equals "For info see Supervisor" |

### Using Bit Operators 

With a bit operator, you can compare the  corresponding bits in two numeric expressions. (A bit is the smallest  unit of data a computer can store.)

| Operator | Description  |
| -------- | ------------ |
| BITAND   | AND          |
| BITOR    | OR           |
| BITXOR   | Exclusive OR |

For example

| Command | Tag3 = Tag1 BITAND Tag2; |
| ------- | ------------------------ |
| Command | Tag3 = Tag1 BITAND 0xFF; |
| Command | Tag3 = Tag1 BITOR Tag2;  |
| Command | Tag3 = Tag1 BITXOR Tag2; |

### Using Relational Operators 

Relational operators describe the relationship  between two values. The relationship is expressed as one value being  larger than, the same as, or smaller than another. You can use  relational operators for both numeric and string variables, however you  can only test variables of the same type. A numeric variable cannot be  compared with a string variable.

| Operator | Description                 |
| -------- | --------------------------- |
| =        | Is equal to                 |
| <>       | Is not equal to             |
| <        | Is less than                |
| >        | Is greater than             |
| <=       | Is less than or equal to    |
| >=       | Is greater than or equal to |

For example:

| Command    | IF Message = "Alarm Active" THEN ...   |
| ---------- | -------------------------------------- |
| Expression | PV12 <> PV10;                          |
| Command    | IF (Total + Count) / Avg < 10 THEN ... |
| Expression | Counter > 1;                           |
| Command    | IF PV12 <= PV10 THEN ...               |
| Expression | Total >= Shift * Hours;                |

### Using Logical Operators

With logical operators, you can test several conditions as either TRUE or FALSE.

| Operator | Description |
| -------- | ----------- |
| AND      | Logical AND |
| OR       | Logical OR  |
| NOT      | Logical NOT |

Examples:

| Command    | Result = (PV12 = 10 AND PV13 = 2);                           |
| ---------- | ------------------------------------------------------------ |
| Comment    | If PV12 equals 10 **and** PV13 equals 2 then Result is TRUE(1) |
| Expression | Motor_1 AND Motor_2;                                         |
| Comment    | If **both** Motor_1 **and** Motor_2 are TRUE, that is Digital bits are 1 or ON, then the expression is TRUE |
| Expression | PV12 = 1 OR PV13 > 2 OR Counter <> 0;                        |
| Comment    | If either PV12 equals 1 **or** PV13 is greater than 2 **or** Counter is not equal to 0, then the expression is TRUE |
| Command    | Result = (Motor1_Ol OR Motor2_Ol);                           |
| Comment    | If either Motor1_Ol **or** Motor2_Ol is TRUE, that is Digital bit is 1 or ON, then Result is TRUE (1) |
| Command    | IF NOT PV12 = 10 THEN ...                                    |
| Comment    | If PV12 does **not** equal 10 then the result is TRUE. This is functionally identical to IF PV12 <> 10 THEN . . . |
| Expression | NOT Tag_1;                                                   |
| Comment    | This expression is TRUE if Tag_1 = 0. This is commonly used for testing digital variables |

### Order of Precedence of Operators

The table below shows the order of precedence of operators.

Operators have a set of rules  that govern the order in which operations are performed. These rules are called the order of precedence. The precedence of Cicode operators from highest to lowest is:  

|      |                       |
| ---- | --------------------- |
| 1.   | ()                    |
| 2.   | NOT                   |
| 3.   | *, /, MOD             |
| 4.   | :                     |
| 5.   | +, -                  |
| 6.   | >, <, <=, >=          |
| 7.   | =, <>                 |
| 8.   | AND                   |
| 9.   | OR                    |
| 10.  | BITAND, BITOR, BITXOR |

## Working with Conditional Executors

### Setting IF ... THEN Conditions

The IF statement executes one or more  statements based on the result of an expression. You can use If in one  of two formats: If Then and If Then Else.

```c
If Expression Then
    Statement(s);
END
-or-
If Expression Then
    Statement(s);
Else
    Statement(s);
END
```

When you use the **If Then** format, the statement(s) following are executed only if the expression is TRUE, for example:

```c
INT Counter;
IF PV12 = 10 THEN
    Counter = Counter + 1;
END
```

In this example, the Counter increments only if the tag PV12 is equal to 10, otherwise the value of Counter remains  unchanged. You can include several statements (including other IF  statements), within an IF statement, for example:

```c
INT Counter;
IF PV12 = 10 THEN
    Counter = Counter + 1;
    IF Counter > 100 THEN
        Report("Shift");
    END
END
```

In this example, the report runs when the Counter increments, that is when PV12 = 10, and the value of the counter exceeds 100.

You can use the **If Then Else** format for branching. Depending on the outcome of the expression, one of two actions are performed, for example:

```c
INT Counter;
IF PV12 = 10 THEN
    Report("Shift");
ELSE
    Counter = Counter + 1;
END
```

In this example, the report runs if PV12 is equal to 10 (TRUE), or the counter increments if PV12 is anything but 10 (FALSE).

### Using FOR ... DO Loops

A For loop executes a statement or statements a specified number of times.

```c
FOR Variable=Expression To Expression DO
    Statement(s);
END
```

The following function uses a For loop:

```c
STRING ArrayA[5]="This","is","a","String","Array";
INT
FUNCTION
DisplayArray()
    INT Counter;
    FOR Counter = 0 TO 4 DO
        Prompt(ArrayA[Counter]);
        Sleep(15);
    END
END
```

This function displays the single message "This is a String Array" on the screen one word at a time pausing for 15  seconds between each word.

### Using WHILE ... DO Conditional Loops

A While loop executes a statement or statements in a loop as long as a given condition is true.

```c
WHILE Expression DO
    Statement(s);
END
```

The following code fragment uses a WHILE loop:

```c
INT Counter;
WHILE DevNext(hDev) DO
    Counter = Counter + 1;
END
/* Count the number of records in the device (hDev)*/
```

Be careful when using WHILE loops in your  Cicode functions: WHILE loops can cause excessive loading of the CPU and therefore reduce system performance. If you use a WHILE loop to loop  forever, you should call the Cicode function `Sleep`() so that Citect SCADA can schedule other tasks. The `Sleep`() function increases the performance of your Citect SCADA system if you use many WHILE loops.

### Nested Loops

You can "nest" one loop inside the other. That  is, a conditional statement can be placed completely within (nested  inside) a condition of another statement.

### Using the SELECT CASE statement

The select case statement executes on several  groups of statements, depending on the result of an expression. SELECT  CASE statements are a more efficient way of writing code that would  otherwise have to be done with nested IF THEN statements.

```c
SELECT CASE Expression
CASE CaseExpression1,CaseExpression2
    Statement(s);
CASE CaseExpression3 TO CaseExpression4
    Statement(s);
CASE IS >CaseExpression5,IS<CaseExpression6
    Statement(s);
CASE ELSE
    Statement(s);
END SELECT
```

Where **CaseExpression*****n\*** is any one of the following forms:

```
- expression
- expression TO expression
```

Where the TO keyword specifies an inclusive range of values. The smaller value needs to be placed before TO.

```c
- IS <relop> expression.
```

Use the IS keyword with relational operators (**<relop>)**. Relational operators that may be used are <, <=, =, <>, >, >= .

If the Expression matches any CaseExpression,  the statements following that CASE clause are executed up to the next  CASE clause, or (for the last clause) up to the END SELECT. If the  Expression matches a CaseExpression in more than one CASE clause, only  the statements following the first match are executed.

The CASE ELSE clause is used to indicate the  statements to be executed if no match is found between the Expression  and any of the CaseExpressions. When there is no CASE ELSE statement and no CaseExpressions match the Expression, execution continues at the  next Cicode statement following END SELECT.

You can use multiple expressions or ranges in each CASE clause. For example, the following line is valid:

```c
CASE 1 To 4, 7 To 9, 11, 13, Is > MaxNumber
```

You can also specify ranges and multiple  expressions. In the following example, CASE matches strings that are  exactly equal to "everything", strings that fall between "nuts" and  "soup" in alphabetical order, and the current value of "TestItem":

```c
CASE "everything","nuts" To "soup",TestItem
```

SELECT CASE statements can be nested. Each SELECT CASE statement needs to have a matching END SELECT statement.

For example, if the four possible states of a  ship are Waiting, Berthed, Loading, and Loaded, the Select Case  statement could be run from a button to display a prompt detailing the  ship's current state.

```c
select case iStatus
CASE    1
    Prompt("Waiting");
CASE    2
    Prompt("Berthed");
CASE    3
    Prompt("Loading");
CASE    4
    Prompt("Loaded");
CASE Else
    Prompt("No Status");
END SELECT
```

## Performing Advanced Tasks

This section introduces and explains event handling, Citect SCADA tasks, Citect SCADA threads, how Citect SCADA executes, and multitasking - including foreground and background tasks, controlling tasks, and pre-emptive multitasking.

### Handling Events

Cicode supports event handling. You can define a function that is called only when a particular event  occurs. Event handling reduces the overhead that is required when event  trapping is executed by using a loop. The following example illustrates  the use of the `OnEvent`() function:

```c
INT 
FUNCTION MouseCallback()
    INT x, y;
    DspGetMouse(x,y);
    Prompt("Mouse at "+x:####+","+y:####);
    RETURN 0;
END
OnEvent(0,MouseCallback);
```

The function `MouseCallBack` is called when the mouse is moved - there is no need to poll the mouse to check if it has moved. Citect SCADA watches for an event with the `OnEvent`() function.

Because these functions are  called each time the event occurs, you should avoid complex or time  consuming statements within the function. If the function is executing  when another call is made, the function can be blocked, and some  valuable information may be lost. If you do wish to write complex event  handling functions, you should use the queue handling functions provided with Cicode.

### How Citect SCADA Executes

Your multi-tasking operating system gives Citect SCADA access to the CPU through threads. However, this access time is not continuous, as Citect SCADA needs to share the CPU with other applications and services.

**Note:** Be careful when running other applications at the same time as Citect SCADA. Some applications place high demands on the CPU and reduce the execution speed of   Citect SCADA.

The Citect SCADA process has many operations to perform, including I/O processing, alarm processing, display management, and Cicode execution - operations that  are performed continuously. And, because Citect SCADA is a real-time system, it needs to perform the necessary tasks within a minimum time - at the expense of others. For this reason, Citect SCADA is designed to be multitasking, so it can efficiently manage it's own tasks.

Citect SCADA performs its tasks in a specific order in a continuous loop (cycle). Citect SCADA's internal tasks are scheduled at a higher priority than that of Cicode  and have access to the CPU before the Cicode. For example, the Alarms,  Trends, and I/O Server tasks all get the CPU before any of your Cicode  tasks. The reports are scheduled at the same priority as your Cicode. Citect SCADA background spoolers and other idle tasks are lower priority than your Cicode.

For Cicode, which consists of many tasks, Citect SCADA uses round-robin single priority scheduling. With this type of  scheduling each task has the same priority. When two or more Cicode  tasks exist, they each get a CPU turn in sequence. This is a simple  method of CPU scheduling.

**Note:** If a Cicode  task takes longer than its designated CPU time to execute, it is  preempted until the next cycle - continuing from where it left off. 

### Multitasking

Multitasking is when you can  run more than one task at the same time. Windows supports this feature  at the application level. For example you can run MS-Word and MS-Excel  at the same time.

Citect SCADA also supports multitasking internally; that is you can tell Citect SCADA to do something, and before Citect SCADA has completed that task you can tell Citect SCADA to start some other task. Citect SCADA will perform both tasks at the same time. Citect SCADA automatically creates the tasks, leaving you to call the functions.

Multitasking is a feature of Citect SCADA not the operating system. Many applications cannot do this, for example if you start a macro in Excel, while that macro is running you cannot  do any other operation in Excel until that macro completes.

A multitasking environment is  useful when designing your Cicode. It allows you to be flexible,  allowing the operator to perform one action, while another is already  taking place. For example, you can use Cicode to display two different  input forms at the same time, while allowing the operator to continue  using the screen in the background.

### Foreground and Background Tasks

Cicode tasks (or threads) can  be executing in either foreground or background mode. A foreground task  is one that displays and controls animations on your graphics pages. Any expression (not a command) entered in a property field (that is Text,  Rectangle, Button, etc.) is executed as a foreground task. Any other  commands and expressions are executed in background mode.

The difference between a  background and foreground task is that a background task can be pre-empted. That is, if system resources are limited, the task (for  example, the printing of a report) can pause to allow a higher priority  task to be executed. When the task is completed (or when system  resources become available) the original task resumes. Foreground tasks are the highest priority and can not be pre-empted.

### Controlling Tasks

You can use the Task functions to control the execution of Cicode tasks, and use the Citect SCADA Kernel at runtime to monitor the tasks that are executing. Since Citect SCADA automatically creates new tasks (whenever you call a keyboard command,  etc.), schedules them, and destroys them when they are finished, users  rarely need to consider these activities in detail.

Sometimes it is desirable to  manually 'spawn' a new task. For example, suppose your Cicode is polling an I/O Device (an operation which need to be continuous), but a  situation arises that requires operator input. To display a form would  temporarily halt the polling. Instead you can spawn a new task to get  the operator input, while the original task continues polling the  device.

**Note:** The TaskNew Cicode function is used to spawn new tasks.

### Pre-emptive Multitasking

Cicode supports pre-empted multitasking. If a Cicode task is running, and a higher priority task is scheduled, Citect SCADA will suspend the original task, complete the higher priority task and return to the original task.

Preemption is supported between Cicode threads and other internal processes performed by Citect SCADA. You can, therefore, write Cicode that runs forever (for example, a  continuous while loop) without halting other Cicode threads or Citect SCADA itself. For example:

```c
INT FUNCTION MyLoopFunction()
    WHILE TRUE DO
        // Whatever is required in the continuous loop
        Sleep(1); // Optional
    END
END
```

In the above example, the  function Sleep() is used to force preemption. The Sleep() function is  optional, however it will reduce the load on the CPU, because the loop  is suspended each second (it will not repeat at a high rate).