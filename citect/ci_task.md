## QueWrite

Writes an integer and string onto the end of a queue. The integer and  string have no meaning to the queue system, they are just passed from QueWrite() to QueRead(). Queue data is written to the end of the queue. When the  data is later read from the queue, it is returned on a  first-in-first-out basis.

This function is a blocking function. It will block the calling Cicode task until the operation is complete.

Syntax

```
QueWrite (hQue, Type, Str)
```

*hQue:* The queue handle, returned from the QueOpen() function.  The queue handle identifies the table where all data on the  associated queue is stored.

*nType:* The integer to put into the queue.

*Str:* The string to put into the queue.

Return Value

0 (zero) if successful, otherwise an [error code](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/Cicode_and_General_Errors.html) is returned.

Related Functions

[QueClose](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/QueClose.html), [QueLength](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/QueLength.html), [QueOpen](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/QueOpen.html), [QueRead](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/QueRead.html), [QuePeek](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/QuePeek.html)

Example

```
QueWrite(hQue,2,"Hello there");
QueWrite(hQue,4,"Help");
```

## QueOpen

Open a queue for  reading and writing data elements. Use this function to create a new  queue or open an existing queue. Use queues for sending data from one  task to another or for other buffering operations.

```
QueOpen(Name, Mode)
```

*sName:* The name of the queue. You need to use the following syntax:

- Names need to begin with either an alpha character (A-Z or a-z) or the underscore character (_).
- Any following characters  need to be either alpha characters (A-Z or a-z), digit characters (0 -  9), period characters (.), backslash characters (\), or underscore  characters (_).

The use of any other characters will result in the name being modified. 

*Mode:* The mode of the queue open:

*0* - Open existing queue.

*1* - Create new queue.

*2* - Attempts to open an existing queue. If the queue does not exist, it will create it.

*4* - Create a queue that can have multiple blocked readers.

Return Value: The queue handle, or -1 if the queue cannot be opened. The queue handle identifies the table where all data on the  associated queue is stored.

```pascal
! Create a queue.
hQue=QueOpen("MyQue",1);
! Write data into the queue.
QueWrite(hQue,1,"Quetext");
QueWrite(hQue,1,"Moretext");
! Read back data from the queue.
QueRead(hQue,Type,Str,0);
```

## TaskNew

Creates a new Cicode task and returns the task handle. You pass the *sName* of the function (that creates the task) as a string, not as the function tag, and pass the arguments for that function in *Arg*. After the task is created, it runs in parallel to the calling task. The new task will run forever unless it returns from the function or is  killed by another task.

 By default, Plant SCADA requests necessary I/O device data and waits for the data to be returned before starting the task -  the task is provided with the correct data, but there will be a delay in starting the task.  If you add 16 to the Mode, Plant SCADA starts the task immediately, without waiting for any data from the I/O devices -  any I/O device variable that you use will either contain 0 (zero) or the last value read. 

You can specify that if the task is already running, the function will exit without launching a new task and an [error](file:///C:/Program Files (x86)/AVEVA Plant SCADA/Bin/Help/SCADA Help/Subsystems/CicodeReferenceCitectHTML/Content/Cicode_Errors.html) will display. This is useful when you want only a single instance of the function running at any point in time.

It is also possible to run the task within  the context of a particular cluster in a multi cluster system by setting the ClusterName parameter. If a cluster is not specified, the task will use the cluster context of the caller, be it a page or Cicode task.  Please be aware that the cluster context cannot be changed once the code is running.

Any animation output for the new task is  displayed in the window where it was created. If you want to send output to other windows, use the WinSelect() function.

```
TaskNew(sName, sArg, Mode [, sClusterName])
```

*sName:* The name of the function to create the task, as a string.

*sArg:* The set of arguments to be passed to the function. Individual arguments need to be separated by commas (,). Enclose string arguments in quotes "" and use the string escape character (^) around strings enclosed within a string. If the string in quotes is not enclosed, then the string is only the first tag found. The entire set of arguments need to be enclosed in quotes ("").

*Mode:* The mode of the task:

- *0* - Task runs forever.
- *1* - Task runs until the current page is changed.
- *2* - Task runs until the current window is freed.
- *4* - This mode is deprecated and not active. Currently, by default, task requests I/O device data before starting.
- *8* - If the task already exists, the function will exit without launching the new task.
- *16*- Task doesn't wait for necessary I/O device data and starts immediately.

You can select any one of  modes 0, 1 or 2 and may add mode 4 and/or mode 8 and/or mode 16. For  example, set Mode to 6 to request I/O device data before starting the  task, and to run the task until the current window is freed.

*sClusterName:*

The name of the cluster context to be applied to the new Cicode task. This is optional if you have one cluster or are resolving the task via the current cluster context. The argument is enclosed in quotation marks "". You may pass "-" as the ClusterName argument to run the requested Cicode task without a cluster context.

Return Value

The task handle, or -1 if the task cannot  be successfully created. The task handle identifies the table where data on the associated task is stored.

```pascal
! Create a task that displays a message for 10 seconds.
hTask=TaskNew("MyFunc","Data",0);
! Continue to run while task runs.
FUNCTION MyFunc(STRING Msg)	
	FOR I=0 TO 10 DO		
		Prompt(Msg);		
		Sleep(1);	
	END
END
...
! Call a function which expects more complex argument
hTask=TaskNew("ArgFunc","^"string one^",^"string two^",1,2",0);
hTask=TaskNew("ArgFunc","^""+sOne+"^",^""+sTwo+"^","+iOne:##+","+
iTwo:##,0);
FUNCTIONArgFunc(STRING sOne, STRING sTwo, INT iOne, INT iTwo)	
...
END
```