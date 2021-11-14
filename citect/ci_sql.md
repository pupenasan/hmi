## SQLConnect

Creates an internal  database connection object and tries to connect it to a database  specified by the connection string. Returns a handle to the database  connection object for use by the other database functions. 

You only require one database connection object for each database system to be accessed (for example, Oracle, dBASE,  Excel, etc.).

It is recommended not to use an SQL database for storage of real-time data (such as alarms), because SQL databases do not provide real-time performance when accessing database data. Only  use an SQL database where data transfer is not a priority (for example,  recipes or reports). If you try to use SQL to store real time data, Citect SCADA's performance could be greatly decreased.

Each database connection object created by SQLConnect should be released by calling SQLDisconnect with handle to  the object. The releasing operation should be performed even when the  SQL connection to database is no longer active; for example  automatically dropped by a remote database or manually closed by  SQLClose. Memory leaks can occur if the handles are not properly  released.

**Note:** Currently there are certain  configurations of providers, connection strings and database systems  which can automatically close connections in order to save the database  systems’ resources; for example MS SQL Server dedicated provider with  activated pooling closes the connection to MS SQL Server when there is  no data exchange between the client and the database server for some  predefined time. If such behaviour is observed and is not desired from  the system design point of view, it can be either:

- switched  off by finding and using respective attributes in the connection string  (if existing and supported by database) or 
- by actively  checking error codes returned from SQL CiCode functions and reconnecting by using SQLOpen if the connection is dropped.
   	The actual state of connections can be checked by SQLInfo with type 5.

This function is a blocking function and should not be called from a foreground task.

Syntax

**SQLConnect**(*sConnect*)

*sConnect:*   The connection string, in the format:

```
<attribute>=<value>[;<attribute>=<value>. . .]
```

Acceptable attributes and their  values vary accordingly to the provider and/or the database system, so  please refer to your database documentation. For example, connecting to a SQL Server via ODBC usually requires giving the computer name and the  database name which can be done by defining "Server" and "Database"  attributes. The same connection via OleDB requires defining the computer as "Data Source" and the database as "Initial Catalog".

Providing username and password as a plain text in the connection string may lead to a security breach on the database  side. Please consider using other forms of authentication instead of  username/password login,  for example Windows Authentication. If this is not possible, try to limit the database account rights and not use the  same username and password for other vital parts of the system such as  for SCADA.

Some simple examples are shown below:

**ODBC provider**        

```
"Driver={SQL Server};Server=(local);Trusted_Connection=Yes; Database=MyDatabase;"
"Driver={Microsoft ODBC for Oracle};Server=ORACLE8i7;Persist Security Info=False;Trusted_Connection=Yes"
"Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\doc\MyDatabase.mdb"
"Driver={Microsoft Excel Driver (*.xls)};DBQ=c:\doc\MySheet.xls"
"SCADA Data Provider=Odbc;Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=c:\doc"
"DSN=MyDSNname"
```

**OleDB provider**        

```
"SCADA Data Provider=OleDb;Provider=MSDAORA; Data Source=ORACLE8i7;Persist Security Info=False;Integrated Security=Yes"
"SCADA Data Provider=OleDb;Provider=Microsoft.Jet.OLEDB.4.0; Data Source=c:\bin\LocalAccess40.mdb"
"SCADA Data Provider=OleDb;Provider=SQLOLEDB;Data Source=(local);Integrated Security=SSPI"
```

**SQLClient Provider**        

"SCADA Data Provider=SQLClient;Persist Security Info=False;Integrated Security=true;Initial Catalog=MyCatalog;server=(local)"         

|                          |                                                              |
| ------------------------ | ------------------------------------------------------------ |
| SCADA Data Provider      | The provider to be used to communicate to a database. Allowed values are as follows: ODBC – ODBC provider, default one if no provider specified, OLEDB – OLEDB provider, SQLClient – MS SQL Server dedicated provider |
| SCADA Connection Timeout | The timeout in seconds for establishing connections.         |
| SCADA Query Timeout      | The timeout in seconds for executing queries. This attribute overwrites the [SQL]QueryTimeout INI parameter. |

Return Value - The handle to the database connection object if the connection is successful, otherwise -1 is returned. (For details call the SQLErrMsg() function). The handle identifies the database connection object where details of the associated SQL connection to a DB are stored.

Example

```c
/* Make a connection to an SQL server and select the name fieldfrom each record in the employee database. */
FUNCTION
ListNames()
    INT hSQL;
    STRING sName;
    INT Status;
    hSQL = SQLConnect("DSN=MyDatabase;UID=billw;SRVR=CI1");
    IF hSQL <> -1 THEN
        Status = SQLExec(hSQL, "SELECT NAME FROM EMPLOYEE");
        IF Status = 0 THEN
            WHILE SQLNext(hSQL) = 0 DO
            sName = SQLGetField(hSQL, "NAME");
            .. 
            END
            SQLEnd(hSQL);
        ELSE
            Message("Information", SQLErrMsg(), 48);
        END
        SQLDisconnect(hSQL);
    ELSE
        Message("Information", SQLErrMsg(), 48);
    END
END
```

## SQLExec

Executes an SQL query on a database. With this function, you can execute any SQL query or command supported by the SQL database.

**Note:** All types of fields can be requested in statements, but SCADA has to convert values of the fields  to MBCS 8-bit strings which is not always possible. For example either  single byte database strings or numbers can be converted to MBCS 8-bit strings, multi-byte strings can be converted to MBCS (their proper  presentation depends on correct setup of SCADA and OS), while blobs  cannot be encoded at all.

Data obtained by this function is stored in the default recordset. The default recordset is always a connected  recordset. Connected recordsets fetch only small portion of data when  the query is executed, but later they have to fetch further portions  when recordset functions are used. This kind of recordset needs open  connections to DB, but they need little memory.

The SQLNext() function needs to be called after the SQLExec() function before you can access data in the first record.

Only one query can be active at a time, so  there is no need to end one query before you execute another query; each time you call SQLExec(), the previous query (through a previous  SQLExec() call) is automatically ended. It means that each query  executed from SQLExec cleans the default recordset. 

Queries are queued for execution and a result from one query overwrites the result from preceding one. Similarly, Citect SCADA automatically ends the latest query when it disconnects the database,  even if you have not called SQLEnd(). However, the SQLEnd() function  aids efficiency; SQLEnd() releases the memory that was allocated when  the latest query was executed.

This function is a blocking function and should not be called from a foreground task.

Queries which are built on the basis of user  data, for example inputed by users via graphics pages or forms, may be  prone to SQL Injection attacks. In such case, try to limit the risk by  using CiCode functions from parameterized queries group and refer to a  professional advice in this matter. 

**Note:**  SECURITY BREACH VIA SQL INJECTION 
        \- Validate all textbox entries using validation controls, regular expressions, code
        \- Use parameterized SQL or stored procedures 
        \- Use a limited access account to connect to the database  

**SQLExec**(*hGeneral, sSelect*)

*hGeneral:* - The handle either to the DB  connection object (returned from either SQLCreate() or SQLConnect()  function) or to the query handle (returned from SQLQueryCreate()). When  it is the connection handle and sSelect is an empty string, the  operation is performed on the first query in that DB connection object.  When it is the query handle, the operation is performed on that query  through the DB object which is associated to it.

*sSelect:* The SQL query to be sent to the SQL database.

Return Value - 0 (zero) if successful, otherwise an [error](file:///C:/Program Files (x86)/AVEVA/Citect SCADA 2018 R2/Bin/Help/Citect SCADA/Subsystems/CicodeReferenceCitectHTML/Content/Cicode_Errors.html) number is returned. (For details of the 307 error code, call the SQLErrMsg() function).

**Example**

These examples assume that the following tables are setup in a SQL server (with the name configured in Windows Control  Panel) and opened with the SQLConnect() function:

**PEOPLE**        

| SURNAME | FIRSTNAME | OCCUPATION | DEPARTMENT |
| ------- | --------- | ---------- | ---------- |
| MARTIAN | MARVIN    | ENGINEER   | MANAGEMENT |
| CASE    | CARRIE    | SUPPORT    | SCADA      |
| LIGHT   | LARRY     | PROGRAMMER | SCADA      |
| BOLT    | BETTY     | ENGINEER   | SYSTEMS    |

**PHONE**        

| SURNAME | NUMBER  |
| ------- | ------- |
| MARTIAN | 5551000 |
| CASE    | 5551010 |
| BOLT    | 5551020 |
| LIGHT   | 5551030 |

Each SQL string (sSQL) should be encased within the SQLExec function, for example:

```c
SQLExec(hSQL, sSQL);
To add a record to a table:
sSQL = "INSERT INTO PEOPLE (SURNAME, FIRSTNAME, OCCUPATION, DEPARTMENT)
             VALUES('ALLEN','MATTHEW','PROGRAMMER','SCADA')";
```

***This SQL command changes the PEOPLE table to:***        

**PEOPLE**        

| SURNAME | FIRSTNAME | OCCUPATION | DEPARTMENT |
| ------- | --------- | ---------- | ---------- |
| MARTIAN | MARVIN    | ENGINEER   | MANAGEMENT |
| CASE    | CARRIE    | SUPPORT    | SCADA      |
| LIGHT   | LARRY     | PROGRAMMER | SCADA      |
| BOLT    | BETTY     | ENGINEER   | SYSTEMS    |
| ALLEN   | MATTHEW   | PROGRAMMER | SCADA      |

***To remove records from a table:***        

```c
sSQL = "DELETE FROM (PEOPLE, PHONE) WHERE SURNAME='MARTIAN'";
SQLBeginTran(hSQL);
SQLExec(hSQL,sSQL);
IF (Message("Alert", "Do you really want to DELETE MARTIAN", 33) = 0) THEN
    SQLCommit(hSQL);
ELSE
    SQLRollback(hSQL);
END
```

Assuming that OK was clicked on the Message Box, the tables change to:

**PEOPLE**        

| SURNAME | FIRSTNAME | OCCUPATION | DEPARTMENT |
| ------- | --------- | ---------- | ---------- |
| CASE    | CARRIE    | SUPPORT    | SCADA      |
| LIGHT   | LARRY     | PROGRAMMER | SCADA      |
| BOLT    | BETTY     | ENGINEER   | SYSTEMS    |

**PHONE**        

| SURNAME | NUMBER  |
| ------- | ------- |
| CASE    | 5551010 |
| BOLT    | 5551020 |
| LIGHT   | 5551030 |

To change a record:

```c
sSQL = "UPDATE PEOPLE SET OCCUPATION='SUPPORT' WHERE FIRSTNAME='LARRY'";
```

This SQL command changes the PEOPLE table to: 

**PEOPLE**        

| SURNAME | FIRSTNAME | OCCUPATION | DEPARTMENT |
| ------- | --------- | ---------- | ---------- |
| MARTIAN | MARVIN    | ENGINEER   | MANAGEMENT |
| CASE    | CARRIE    | SUPPORT    | SCADA      |
| LIGHT   | LARRY     | SUPPORT    | SCADA      |
| BOLT    | BETTY     | ENGINEER   | SYSTEMS    |

To select a group of records from a table:

```c
sSQL = "SELECT SURNAME FROM PEOPLE WHERE OCCUPATION='ENGINEER'";
```

This SQL command will return the following table back to Citect SCADA. The table can then be accessed by the SQLNext() function and the SQLGetField() functions.

***CITECT TABLE for hSQL***        

| SURNAME |      |
| ------- | ---- |
| MARTIAN |      |
| BOLT    |      |

You can also select data using a much more complete SQL string, for example:

```c
sSQL = "SELECT (SURNAME, OCCUPATION, NUMBER) FROM (PEOPLE, PHONE) WHERE DEPARTMENT='SCADA' AND PEOPLE.SURNAME = PHONE.SURNAME";
```

This SQL command retrieves the following table:

| SURNAME | OCCUPATION | NUMBER  |
| ------- | ---------- | ------- |
| CASE    | SUPPORT    | 5551010 |
| LIGHT   | PROGRAMMER | 5551030 |

To extract information from a table:

```c
STRING sInfo[3][10]
int i = 0;
WHILE ((SQLNext(hSQL) = 0) and (i < 10)) DO
    sInfo[0][i] = SQLGetField(hSQL, "SURNAME");
    sInfo[1][i] = SQLGetField(hSQL, "OCCUPATION");
    sInfo[2][i] = SQLGetField(hSQL, "NUMBER");
END
```

This code example leaves the information in the sInfo two dimensional array as follows:

***sInfo***        

|      | 0     | 1          | 2       |
| ---- | ----- | ---------- | ------- |
| 0    | CASE  | SUPPORT    | 5551010 |
| 1    | LIGHT | PROGRAMMER | 5551030 |
| 2    |       |            |         |
| 3    |       |            |         |
| 4    |       |            |         |
| ...  |       |            |         |

# Приклади

## Приклад запису даних

```c
STRING
FUNCTION FnWriteToSQL2()
	INT hSQL, INT resi, STRING res, STRING sSQL;
	hSQL = SQLConnect("Driver=SQL Server;Server=DESKTOP-EJN0HKQ\SQLEXPRESS;Database=DB1;UID=G1;PWD=1");
    IF hSQL <> -1 THEN
		sSQL = "INSERT INTO dbo.loop5 VALUES (";
		sSQL = sSQL + "CONVERT(DATETIME,'" + TimestampToStr(LOOP_5_PV.t, 5) + "', 104)," 
		sSQL = sSQL + RealToStr(LOOP_5_PV,5,2,".") + "," + RealToStr(LOOP_5_SP,5,2,".") + ")";
		resi= SQLExec(hSQL,sSQL);
		IF resi= 0 THEN  
			recordcounts2 = recordcounts2 + 1;
			res = "";
		ELSE 
			res = SQLErrMsg();	
		END	 
    ELSE
        res = SQLErrMsg();
    END
    SQLDisconnect(hSQL);
	RETURN res;
END  
```

CONVERT (DATETIME, DATE + " " + TIME, 5)

## Приклад читання даних

```c
STRING
FUNCTION Avgfield(STRING FieldName)
	INT hSQL, INT i, INT hRec, STRING res, STRING sSQL;
	hSQL = SQLConnect("Driver=SQL Server;Server=DESKTOP-EJN0HKQ\SQLEXPRESS;Database=DB1;UID=G1;PWD=1");
    IF hSQL <> -1 THEN
		sSQL = "SELECT AVG(" + FieldName + ") AS avg FROM dbo.loop5";
		hRec = SQLGetRecordset(hSQL, sSQL );
		IF hRec<>-1 THEN  
          res = SQLGetField(hRec, "avg", 0);
		ELSE 
		  res = SQLErrMsg();	
		END	 
    ELSE
        res = SQLErrMsg();
    END
    SQLDisconnect(hSQL);
	RETURN res;
END  
```

