<div align="center">

## Repost: ADO\.Net Primer \+ Programming databases using OLE DB with ADO\.Net


</div>

### Description

Moving from ADO to ADO.Net? Planning to access a Non SQL Server database? This article talks about databases on your hard disk, and discusses almost all of the important ADO.Net classes.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[TeknikForce](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/teknikforce.md)
**Level**          |Beginner
**User Rating**    |3.8 (23 globes from 6 users)
**Compatibility**  |VB\.NET
**Category**       |[Databases](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/databases__10-5.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/teknikforce-repost-ado-net-primer-programming-databases-using-ole-db-with-ado-net__10-2885/archive/master.zip)





### Source Code

```
<h1><span style='font-size:12.0pt'>ADO.Net Primer + Programming databases using
OLE DB with ADO.Net<o:p></o:p></span></h1>
<p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Verdana'>By Cyril Gupta<o:p></o:p></span></p>
<p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Verdana'><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></span></p>
<p class=MsoBodyText>Although I’ve been working with Visual Basic for several
years now (started with Visual Basic 3.0), and I was quick to adopt the newer
versions of Visual Basic as they came, I was a rather late entrant on the .Net
scene. </p>
<p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Verdana'><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></span></p>
<p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Verdana'>But migration to .Net had to occur eventually, so here I
am working with .Net, and to keep me company, I’ve decided to write a series of
articles.<o:p></o:p></span></p>
<p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Verdana'><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></span></p>
<h2>Acessing Local Databases</h2>
<p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Verdana'>Read .Net books or tutorials and they will tell you that
data access in VB.Net is pretty straightforward using Ado.Net, Microsoft’s
replacement for ADO. However, if you’ve been using DAO and ADO long enough like
I, you’ll soon be lost among the swamp of new classes and properties that ADO.Net
exposes. <o:p></o:p></span></p>
<p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Verdana'><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></span></p>
<p class=MsoBodyText>ADO.Net has two primary clients to establish the
connection with the data: The SQLClient and OLEDB.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>The SQLClient is designed to connect only and only to
Microsoft SQL Server databases, while the OLEDB client allows you to connect to
any database that has an OLE DB server. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>This is where I was lost for quite a while. Almost all of
the examples in database programming books that I saw were exclusively based on
the SQLClient class. Good, but what about the programmers who don’t use SQL
Server, or make applications that has to be deployed on PCs that don’t have SQL
Server installed?</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>As a maker of packaged applications I use Jet Databases
most of the time and my apps are used by thousands of users. I can’t force them
to install SQL Server.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>You’ve got two options.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>a) Stick to ADO<o:p></o:p></b></p>
<p class=MsoBodyText>The .Net framework has full support for Microsoft ADO
database access. You can declare ADO classes, and use them the same way you’d
use them in your Visual Basic 6 project. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>To use ADO add a reference to the ‘adodb’ .Net component
by right clicking on ‘References’ in your project, and then selecting ‘adodb’
from the Components list. This will allow you to create instances of all the
ADODB classes like Connection, Command and Recordset, and you will never notice
that you’re working with .Net. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>I am not going to show you the code to do this as you
probably already know how, and if you don’t, you can look at the million or so
code examples on the Internet. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>That was the easy way out, and that is what I decided to
do at first. However, when I began, something didn’t feel right. True cowboys
don’t take the easy way out, and I am not inferior in courage, or guts to any plain old cowherd.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Also there’s one more disadvantage. Microsoft.Net does not
use really compiled applications, actually the applications that we make are
compiled to MSIL (Microsoft Intermediate Language) and a Just-In-Time compiler
is used to compile then when they’re run. ADO isn’t natively supported in .Net
so it can’t be compiled to MSIL. Your code will still compile and work, but it
will use COM Interoperability, so the disadvantage is purely from a technical
point of view.<span style='text-transform:uppercase'><o:p></o:p></span></p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Let’s explore the second option.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>b) Use OLEDB<o:p></o:p></b></p>
<p class=MsoBodyText>Just about when I was about to give up on SQLClient and go
back to ADO to access my local databases, I found somewhere that OLEDB is the
interface to use to access all kinds databases with ADO.Net. This naturally
includes Jet databases.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>This is what I decided to use, and this is what the rest
of this tutorial talks about.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b><span style='font-size:12.0pt'>Programming OLEDB <o:p></o:p></span></b></p>
<p class=MsoBodyText>The OLEDB does not provide the same kind of ease of use or
features like ADO or SQLClient does. The class is stricter, and unlike ADO
objects that allow you to declare and initialize the objects in a wide variety
of ways through polymorphed functions, OLEDB objects are harsher and less
adaptable. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Properties like Connection.Provider that you could assign
data to in ADO, are read only in OLEDB, which caused me a lot consternation
when I began using the objects.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Primary OLEDB Objects that you will need to access data:</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style='margin-left:1.0in;text-indent:-.25in;mso-list:l1 level1 lfo2;
tab-stops:list 1.0in'><![if !supportLists]><span style='font-family:Symbol'>·<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><![endif]>OLEDBConnection</p>
<p class=MsoBodyText style='margin-left:1.0in;text-indent:-.25in;mso-list:l1 level1 lfo2;
tab-stops:list 1.0in'><![if !supportLists]><span style='font-family:Symbol'>·<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><![endif]>OLEDBCommand</p>
<p class=MsoBodyText style='margin-left:1.0in;text-indent:-.25in;mso-list:l1 level1 lfo2;
tab-stops:list 1.0in'><![if !supportLists]><span style='font-family:Symbol'>·<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><![endif]>OLEDBDataAdapter</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>OLEDBConnection<o:p></o:p></b></p>
<p class=MsoBodyText>You can call this a replacement for the ADODB.Connection
object. It behaves in a similar manner, and you can open the database the same
way you did with the ADODB.Connectionstring. However, unlike ADODB.Connection
object, most methods in OLEDBConnection object do not support polymorphic
arguments the same way that ADODB.Connection does. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>How does this affect you? For example, you won’t be able
to assign values to OLEDBConnection.Provider or OLEDBConnection.Datasource like
you did with ADODB. All these properties are read only in OLEDB and you will
have to specify everything in the ConnectionString property.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Here’s some sample code.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoNormal style='mso-layout-grid-align:none; text-autospace:none; color: #000099;'><span
style='font-size:10.0pt;font-family:"Courier New"'>cnn.ConnectionString =
&quot;Provider=Microsoft.Jet.OLEDB.4.0;Data Source=c:\dic.mdb;&quot;<o:p></o:p></span></p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>This connectionstring opens a Microsoft Jet 4 Database
named ‘dic.mdb’ located in ‘c:\’.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Here-</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Provider = The database service provider name. If you use
Jet Databases (.MDB) this will mostly be ‘Microsoft.Jet.OLEDB.4.0’ for the new
Acess 2000 databases, and ‘Microsoft.Jet.OLEDB.3.5’ for older databases. You
can open Jet 3.5 databases with Jet 4.0 but not vice-versa. So if you create a
database using the new version of Microsoft Access and not the Database wizard
in Visual Basic 6 then you will have to use the 4.0 provider.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Data Source = The database name. This can be a file, or a
database name if you use a database server like MS Sql Server. Yes, you can
open SQL Server databases using OLEDB object instead of SQLClient if you want
to. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Don’t forget to put the semicolon ‘;’ mark after each
attribute, or the code won’t work.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b><span style='font-size:12.0pt'>OLEDBCommand<o:p></o:p></span></b></p>
<p class=MsoBodyText>The OLE DB command object allows you to execute SQL
procedures on your data tables and to retrieve data from the table.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>To get the records from our data table we must first
assign the connection object to the connection property of the command object.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style1>myCommand = myConnection;</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Now set the ‘Commandtype’ property. The CommandType
property tells OLEDB what kind of command you wish to execute.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>You have three options.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>CommandType<o:p></o:p></b></p>
<p class=MsoBodyText>Text – A normal SQL Query.</p>
<p class=MsoBodyText>StoredProcedure – The procedure name of a stored procedure
in the database.</p>
<p class=MsoBodyText>TableDirect – The Tablename of the table to open.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Most of the time you’ll find yourself using the Text
property or the TableDirect property. However it’s a great idea to use Stored
Procedures in a database to do frequently performed operations.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>I going to set my CommandType to Text for the moment.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style2>myCommand.CommandType = CommandType.Text</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Now you must tell the Command object what Query string to
use.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style1>myCommand.Text = “SELECT * FROM DIC WHERE WORD LIKE ‘A%’”</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>This will retrieve all rows of the DIC table in which the
Word column starts with the letter ‘A’.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>If you used the TableDirect CommandType then you can
simply assign the name of the table to the Command.Text property. This would
look like this.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style1>myCommand.Text = “Dic”</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>This will retrieve all the rows in table Dic.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>More about Queries<o:p></o:p></b></p>
<p class=MsoBodyText>Before we move on to learning how to use the data retrieved
from the query let’s learn a little about Executing queries using the Command
object.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>The Ole DB Command object supports three kinds of Execute
statements.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>ExecuteNonQuery – Execute an SQL statement that does not
return a result.</p>
<p class=MsoBodyText>ExecuteReader – Execute an SQL statement that returns a
DataReader object (More about it later.)</p>
<p class=MsoBodyText>ExecuteScalar – Execute an SQL statement that returns the
first column of the resultant recordset.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>In ADO you could also execute an SQL statement to return a
recordset object that was updateable and editable, this is no longer supported
with ADO.NET. Now you must use Datasets, which can be compared more favorably
with disconnected recordsets even though the comparison is not very apt. More
about DataSets later, let’s see a sample of each type of query statement first.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Examples Query Statements</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style1>myCommand.Text = “DELETE * From Dic”</p>
<p class=MsoBodyText style1>myCommand.ExecuteNonQuery</p>
<p class=MsoBodyText style3>Will delete everything from the table Dic.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style1>myCommand.Text = “SELECT * From Dic”</p>
<p class=MsoBodyText style1>myDataReader = myCommand.ExecuteReader</p>
<p class=MsoBodyText style4>Will get everything from the table Dic and you can assign
to a DataReader object.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style1>myCommand.Text = “SELECT * From Dic”</p>
<p class=MsoBodyText style1>myVar = myCommand.ExecuteScalar</p>
<p class=MsoBodyText style3>Will the first column of the first record from the table
Dic. You can assign this value to a variable.</p>
<p class=MsoBodyText><span class="style3">
 <![if !supportEmptyParas]>
 &nbsp;
 <![endif]>
 <o:p></o:p></span><o:p></o:p></p>
<p class=MsoBodyText>Now let’s come to the most important changes in ADO.NET</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b><span style='font-size:12.0pt'>DataReader, DataAdapters
&amp; DataSet<o:p></o:p></span></b></p>
<p class=MsoBodyText>With the DataReader object you can get a forward only,
read only set of records from the database. The DataReader object establishes a
really fast connection to the record data and you should use it whenever
possible. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>Using DataReaders<o:p></o:p></b></p>
<p class=MsoBodyText>Once you’ve populated a DataReader object with records you
can use the DataReader.Read property to read the column values from the
recordset. On calling Read the DataReader object will automatically move to the
next record.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>DataAdapters<o:p></o:p></b></p>
<p class=MsoBodyText>DataAdapters work as a link between data sources and
DataSets. To get records from or update records to any data source you must go
through a DataAdapter in ADO.Net. </p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>First tell DataAdapter what Command to use using the
‘SelectCommand’ property.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style2>myDataAdapter.SelectCommand = myCommand</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Now you can fill a DataSet with the resulting records.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style2>MyDataAdapter.Fill(myDataSet,”myTable”)</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>DataSets<o:p></o:p></b></p>
<p class=MsoBodyText>The closest comparison of an ADO.Net DataSet would be a
disconnected Recordset in ADO. The DataSet also has XML capabilities and can
read or write XML files direct.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>You can browse the data inside a DataSet using the Tables
collection in the DataSet once you’ve filled it using the DataAdapter’s fill
method.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>To iterate through all the rows in a DataSet you can use
the Rows collection of the table.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>
 <span class="style5">&nbsp;
 <![endif]>
 <o:p></o:p></span></p>
<p class=MsoBodyText style2>Dim myDatRow as Data.DataRow ‘Declare a Datarow</p>
<p class=MsoBodyText style2><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText style2>For Each rsRow in MyDataSet.Tables(“myTable”).Rows</p>
<p class=MsoBodyText style2><span style='mso-tab-count:1'>          </span>Console.WriteLine(“MyColumn”)</p>
<p class=MsoBodyText style2>Next</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>This will iterate through the entire table and write the
value of the column “MyColumn” to the Console window.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText><b>Updating Databases<o:p></o:p></b></p>
<p class=MsoBodyText>You cannot directly update using the DataSet object like
you could with a RecordSet in ADO. To update records to a database you must go
through a DataAdapter Object.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>To add new records or rows to the Dataset you can call the
Add method of the Rows collection of the Table. The Add method either accepts a
new Row object as a parameter or an array filled with values for the new row.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Example:</p>
<p class=MsoBodyText style1>MyDataSet.Tables(“MyTable”).Rows.Add(myNewRow)</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>You can change the values in the row by simply selecting
the required Row and then assigning new values to the columns (No need to call
any ‘Edit’ method)</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Once you’ve finished making changes to the DataSet you can
commit the changes to the Database by calling the DataAdapter’s Update method
and passing the changed DataSet as the parameter.</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Example.</p>
<p class=MsoBodyText style1>myDataAdapter.Update(myDataSet)</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>This winds up the ADO.Net Primer for about now. ADO.Net is
big and this primer is by no means complete. I intend to write more episodes of
the primer and introduce the other features of ADO.Net. The next primer in this
series would most probably be based on processing XML through ADO.Net.</p>
<p class=MsoBodyText><br>
Adios until then</p>
<p class=MsoBodyText><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoBodyText>Cyril Gupta</p>
```

