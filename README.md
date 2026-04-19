
WEEK 4 
•	1.a. listing the steps needed to create a Web form and adding a server control to the form.
1. Create a New ASP.NET Web Forms Project
1.	Open Visual Studio 
2.	Click Create a new project 
3.	Select ASP.NET Web Application (.NET Framework) 
4.	Click Next 
5.	Name your project (example: MyWebApp) 
6.	Click Create 
7.	Select Web Forms 
8.	Click Create
2. Add a Web Form (.aspx page)
1.	In Solution Explorer 
2.	Right-click your project 
3.	Select Add → Web Form 
4.	Name it (example: Default.aspx) 
5.	Click Add
4. Add a Server Control
Server controls are ASP.NET controls that run on the server.
Example: Add a TextBox and Button
Paste this inside the <form runat="server"> tag:
<asp:TextBox ID="txtName" runat="server"></asp:TextBox>

<asp:Button ID="btnSubmit" runat="server" Text="Submit" OnClick="btnSubmit_Click" />

<asp:Label ID="lblMessage" runat="server"></asp:Label>
________________________________________
5. Add Code-Behind Logic
Open Default.aspx.cs and add this:
protected void btnSubmit_Click(object sender, EventArgs e)
{
    lblMessage.Text = "Hello, " + txtName.Text;
}
________________________________________
6. Run the Web Form
1.	Click Start (IIS Express) 
2.	Enter a name in the textbox 
3.	Click Submit 
4.	The label will display the result


•	1.b. describing the access of properties and methods of server controls.
1. Accessing Properties of Server Controls
Properties store or represent the state of a control.
 Example Controls:
•	TextBox.Text 
•	Label.Text 
•	Button.Text 
•	CheckBox.Checked 
 Example:
string name = txtName.Text;
lblMessage.Text = "Hello " + name;
•	txtName.Text → gets user input from the textbox 
•	lblMessage.Text → sets text displayed on the page 
2. Accessing Methods of Server Controls
•  Focus() → sets cursor to a control 
•  Clear() (custom logic, not built-in for all controls) 
•  DataBind() → binds data to control 
•	•  Dispose() → releases resources
3. Accessing Properties & Methods in Events
protected void btnSubmit_Click(object sender, EventArgs e)
{
    lblMessage.Text = "Welcome " + txtName.Text;

    txtName.Focus();
}
5.	Accessing Controls from Code-Behind
<asp:TextBox ID="txtName" runat="server" />
<asp:Label ID="lblMessage" runat="server" />
txtName.Text = "John";
lblMessage.Text = txtName.Text;


•	2.a. describing the advantages of partitioning an ASP.NET page.
1 -You can reuse the same section (like a menu, header, or login box) on multiple pages.
Example: A navigation bar created once can be used across all pages.
2 - When a page is split into parts, you only need to update one section.
•	If you change the header in a Master Page, all pages update automatically. 
•	This reduces errors and saves time.
3 - Smaller parts are easier to read and understand than one large page.
•	Developers can quickly find and fix code. 
•	Improves collaboration in team projects.
4 - - Each part of the page has a specific responsibility:
•	Header → branding/navigation 
•	Content → page-specific data 
•	Footer → links and copyright 
This makes the application more organized and structured
5 - You can build pages faster by assembling pre-made components instead of coding everything from scratch.
Example: Reuse login control instead of rewriting login logic.
.

6 – Since each section is separate, you can test parts individually.
•	If a bug occurs in the menu, you only check the menu control—not the whole page.



•	2.c. analyzing the process of creating and using components.
In ASP.NET (especially Web Forms), components are reusable building blocks such as User Controls (.ascx), custom server controls, or prebuilt controls that encapsulate UI and logic. Analyzing the process of creating and using components means understanding how they are built, how they work internally, and how they are reused across pages.
A component is a self-contained unit that includes:
•	UI (HTML/markup) 
•	Logic (C# code-behind) 
•	Properties and events (optional) 
Examples:
•	Navigation menu 
•	Login box 
•	Product card 
•	Footer section 
2. Process of Creating a Component
Step 1: Create a User Control
•	In Visual Studio → Right-click project 
•	Add → New Item → Web User Control (.ascx)
Example: Header.ascx

Step 2: Design the Component (UI)
Inside .ascx:
<asp:Label ID="lblTitle" runat="server" Text="My Website Header"></asp:Label>
Step 3: Add Logic (Code-behind)
In .ascx.cs:
public string Title
{
    get { return lblTitle.Text; }
    set { lblTitle.Text = value; }
}

•	3.d. describing the process of displaying data on list-bound controls.
In ASP.NET Web Forms, list-bound controls are used to display collections of data from sources like databases, lists, or arrays. Common examples include DropDownList, ListBox, CheckBoxList, RadioButtonList, GridView, and Repeater.

Process of Displaying Data on List-Bound Controls
The process involves getting data, connecting it to the control, and binding it for display.
________________________________________
1. Retrieve Data from a Data Source
First, you must get data from somewhere, such as:
•	Database (SQL Server using Entity Framework or ADO.NET) 
•	In-memory list (List<T>) 
•	Array or collection 
Example:
var categories = context.Categories.ToList();
________________________________________
2. Assign Data Source to the Control
You connect the data to the control using the DataSource property.
Example:
ddlCategories.DataSource = categories;
________________________________________
3. Define Display and Value Fields
You must specify:
•	DataTextField → what the user sees 
•	DataValueField → actual stored value 
Example:
ddlCategories.DataTextField = "Name";
ddlCategories.DataValueField = "CategoryID";
________________________________________
4. Bind the Data
Call DataBind() to display the data.
Example:
ddlCategories.DataBind();

