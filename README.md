# KEIZA_FRAMEWORK
Keiza .NET Framework to help programmer develop application easily and faster.

**A robust, enterprise-grade 3-Tier layered architecture for building scalable web applications with dual database support (MySQL & MSSQL).**

**Version:** 1.0  
**Created:** August 2026  
**Framework Type:** ASP.NET ASMX Web Services with 3-Tier Architecture

---

## 📋 Table of Contents

- [Framework Overview](#framework-overview)
- [Architecture Layers](#architecture-layers)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Database Support](#database-support)
- [File Descriptions](#file-descriptions)
- [Code Standards](#code-standards)
- [Best Practices](#best-practices)
- [Development Workflow](#development-workflow)

---

## 🎯 Framework Overview

Keiza .NET Framework is a clean, production-ready 3-Tier architecture designed for enterprise applications with clear separation of concerns. It uses:

- **Frontend:** HTML5, CSS, jQuery, Bootstrap
- **API Layer:** ASP.NET ASMX Web Services (JSON)
- **Business Logic:** C# Controllers
- **Data Access:** Dual database support (MySQL & MSSQL)
- **Data Models:** Strongly-typed DTOs

### Key Features

✅ Clean Separation of Concerns  
✅ Dual Database Support (MySQL & MSSQL)  
✅ AJAX/REST API Integration  
✅ Comprehensive Error Logging  
✅ Responsive Bootstrap UI  
✅ Input Validation (Frontend & Backend)  
✅ JSON Response Format  
✅ Production-Ready Code  
✅ Easy to Extend  

---

## 🏗️ Architecture Layers

┌─────────────────────────────────────────────────┐ │   1. FRONTEND LAYER (WebHTML_Keiza)             │ │   - HTML5, CSS, jQuery, Bootstrap               │ │   - AJAX calls to REST API                      │ │   - Client-side validation                      │ └──────────────┬──────────────────────────────────┘ │ (AJAX/REST API calls) ┌──────────────▼──────────────────────────────────┐ │   2. WEBSERVICE LAYER (WebService.asmx.cs)      │ │   - ASP.NET ASMX Web Services                   │ │   - [WebMethod] endpoints                       │ │   - JSON serialization                          │ │   - Request validation                          │ └──────────────┬──────────────────────────────────┘ │ (Function calls) ┌──────────────▼──────────────────────────────────┐ │   3. BUSINESS LOGIC LAYER (MainController.cs)   │ │   - Business rules & validation                 │ │   - Data processing                             │ │   - Error handling                              │ │   - Error logging                               │ └──────────────┬──────────────────────────────────┘ │ (SQL queries) ┌──────────────▼──────────────────────────────────┐ │   4. DATA ACCESS LAYER                          │ │   - DBConnect.cs (MySQL)                        │ │   - DBConnect2.cs (MSSQL)                       │ │   - Query execution                             │ │   - Connection management                       │ └──────────────┬──────────────────────────────────┘ │ ┌──────────────▼──────────────────────────────────┐ │   5. DATA MODEL LAYER (MainModel.cs)            │ │   - Data Transfer Objects (DTOs)                │ │   - Data serialization                          │ │   - [DataMember] attributes                     │ └─────────────────────────────────────────────────┘


---

## 📁 Project Structure

Solution_Keiza/ │ ├── WebApp_Keiza/                          (Backend - ASP.NET) │   ├── App_Code/ │   │   ├── Models/ │   │   │   └── MainModel.cs              (Data Transfer Object) │   │   ├── Controllers/ │   │   │   └── MainController.cs         (Business Logic) │   │   ├── Data/ │   │   │   ├── DBConnect.cs              (MySQL Connection) │   │   │   └── DBConnect2.cs             (MSSQL Connection) │   │   ├── Services/ │   │   │   └── WebService.asmx.cs        (API Endpoints) │   │   └── Utilities/ │   │       └── ErrorLogger.cs            (Error Handling) │   ├── Properties/ │   ├── LogFile/                          (Error Logs) │   ├── Web.config                        (Configuration) │   ├── WebService.asmx                   (ASMX File) │   └── WebApp_Keiza.csproj              (Project File) │ └── WebHTML_Keiza/                         (Frontend - HTML/JS) ├── index.html                        (Home Page) ├── css/ │   └── style.css                     (Custom Styles) ├── js/ │   ├── Ajax.API.Caller.js            (AJAX Utility) │   └── app.js                        (Application Logic) ├── forms/ │   └── registration.html             (Registration Form) └── WebHTML_Keiza.csproj             (Project File)


---

## 🚀 Getting Started

### Prerequisites

- Visual Studio 2022 or later
- .NET Framework 4.8.1
- MySQL Connector/NET 6.5.4 or later (for MySQL support)
- MSSQL Server 2016 or later (for MSSQL support)
- jQuery 3.6.0
- Bootstrap 3.3.7

### Quick Setup

1. **Create Solution**
File → New → Project → Solution Name: Solution_Keiza

2. **Create Backend Project**
Add → New Project → ASP.NET Web Application (.NET Framework) Name: WebApp_Keiza Framework: 4.8.1

3. **Create Frontend Project**
Add → New Project → ASP.NET Web Site (.NET Framework) Name: WebHTML_Keiza

4. **Create Folder Structure** (see Project Structure above)

5. **Add Template Files** (see File Descriptions section)

6. **Update Configuration** (see Configuration section)

7. **Build and Test**

---

## ⚙️ Configuration

### Web.config Setup

Update `WebApp_Keiza\Web.config`:
<configuration> <appSettings> <!-- MySQL Connection String --> <add key="MyConnection" value="SERVER=your-mysql-host;DATABASE=your-database-name;UID=your-username;PASSWORD=your-password;"/>
<!-- MSSQL Connection String -->
<add key="MSSQLConnection" value="Server=your-mssql-host;Database=your-database-name;User Id=your-username;Password=your-password;"/>

<!-- Error Log File Path -->
<add key="LogFile" value="~/LogFile/errorLog.txt"/>
</appSettings>
<system.web> <compilation debug="true" targetFramework="4.8.1"> <assemblies> <add assembly="MySql.Data, Version=6.5.4.0, Culture=neutral, PublicKeyToken=C5687FC88969C44D"/> <add assembly="System.Device, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/> </assemblies> </compilation> <httpRuntime executionTimeout="3600" maxRequestLength="400000"/> <webServices> <protocols> <add name="HttpGet"/> <add name="HttpPost"/> </protocols> </webServices> <pages controlRenderingCompatibilityVersion="4.0"/> </system.web>
<system.web.extensions> <scripting> <webServices> <jsonSerialization maxJsonLength="2147483644"/> </webServices> </scripting> </system.web.extensions> </configuration>


### JavaScript API Path

Update `WebHTML_Keiza\js\Ajax.API.Caller.js`:
var pagePath = "http://localhost:YOUR_PORT/WebService.asmx";


Replace `YOUR_PORT` with your actual port number (e.g., 63181)

---

## 🗄️ Database Support

### MySQL (DBConnect.cs)

- **Namespace:** `MySql.Data.MySqlClient`
- **Connection Type:** `MySqlConnection`
- **Methods:**
  - `OpenConnection()` - Opens connection
  - `CloseConnection()` - Closes connection
  - `Insert(query)` - INSERT statement
  - `Update(query)` - UPDATE statement
  - `Delete(query)` - DELETE statement
  - `ExecuteQuery(query)` - SELECT statement

### MSSQL (DBConnect2.cs)

- **Namespace:** `System.Data.SqlClient`
- **Connection Type:** `SqlConnection`
- **Methods:**
  - `OpenConnection()` - Opens connection
  - `CloseConnection()` - Closes connection
  - `Insert(query)` - INSERT statement
  - `Update(query)` - UPDATE statement
  - `Delete(query)` - DELETE statement
  - `ExecuteQuery(query)` - SELECT statement
  - `GetDataTable(query)` - Get results as DataTable
  - `GetScalarValue(query)` - Get single value

---

## 📄 File Descriptions

### Backend Files (WebApp_Keiza)

#### 1. MainModel.cs
**Purpose:** Data Transfer Object (DTO)  
**Responsibility:** Holds data structure with GetSet properties  
**Key Features:**
- [DataContract] and [DataMember] attributes for serialization
- GetSet naming convention (e.g., GetSetid, GetSetname)
- Null value handling

#### 2. DBConnect.cs (MySQL)
**Purpose:** MySQL database connection management  
**Responsibility:** Execute queries and manage connections  
**Key Methods:**
- `OpenConnection()` - Establish connection
- `CloseConnection()` - Close connection
- `Insert(query)` - Execute INSERT
- `Update(query)` - Execute UPDATE
- `Delete(query)` - Execute DELETE
- `ExecuteQuery(query)` - Execute SELECT

#### 3. DBConnect2.cs (MSSQL)
**Purpose:** MSSQL Server database connection management  
**Responsibility:** Execute queries and manage connections  
**Extended Methods:**
- All methods from DBConnect plus:
- `GetDataTable(query)` - Return DataTable
- `GetScalarValue(query)` - Return single value

#### 4. MainController.cs
**Purpose:** Business Logic Layer  
**Responsibility:**
- Validate business rules
- Orchestrate database operations
- Handle error logging
- Process and transform data

**Key Methods:**
- `getUserProfile(idno, idtype)` - Retrieve user profiles
- `getUserProfileDetails(id)` - Get single user details
- `registerAsnaf(name, idno, emailaddress)` - Register new user
- `replaceNull(dataReader, columnName)` - Handle null values
- `WriteToLogFile(message)` - Log errors

#### 5. WebService.asmx.cs
**Purpose:** API Endpoints  
**Responsibility:**
- Receive requests from frontend
- Validate inputs
- Call business logic
- Return JSON responses

**Key Methods:**
- `HelloWorld()` - Test connection
- `HelloWorld2(status, message)` - Test JSON response
- `getUserProfileDetails(id)` - Get user details
- `registerAsnaf(name, icno, emailaddress)` - Register user

#### 6. Web.config
**Purpose:** Application Configuration  
**Contains:**
- Database connection strings
- Assembly bindings
- HTTP runtime settings
- Web service protocols

---

### Frontend Files (WebHTML_Keiza)

#### 1. Ajax.API.Caller.js
**Purpose:** AJAX Utility Functions  
**Key Functions:**
- `PageMethod(fn, paramArray, successFn, errorFn, asyncFn)` - Call WebService
- `showAlert(message, alertType, containerId)` - Display alerts
- `isValidEmail(email)` - Validate email format
- `trimValue(value)` - Trim whitespace
- `isEmpty(value)` - Check if empty
- `formatDate(date)` - Format dates

#### 2. app.js
**Purpose:** Application Logic  
**Key Functions:**
- `initializeApp()` - Initialize application
- `bindEventHandlers()` - Bind event listeners
- Global AJAX error handler

#### 3. style.css
**Purpose:** Custom Styling  
**Includes:**
- Bootstrap customization
- Form styling
- Alert styling
- Panel styling
- Responsive design

#### 4. index.html
**Purpose:** Home Page  
**Contains:**
- Navigation bar
- Framework information
- Quick links
- WebService test button

#### 5. registration.html
**Purpose:** Asnaf Registration Form  
**Form Fields:**
- Name (required)
- IC Number (required)
- Email Address (required)
- Submit and Reset buttons

**Validation:**
- Client-side: Required fields, email format
- Server-side: Null check, data validation

---

## 📝 Code Standards

### Naming Conventions

**Classes:** PascalCase
public class MainModel { } public class MainController { } public class DBConnect { }


**Methods:** PascalCase (Public), camelCase (Private)
public MainModel getUserProfileDetails(String id) { } private bool validateInput(String input) { }


**Variables:** camelCase with type prefix
String sName = "";           // s prefix for strings int iCount = 0;              // i prefix for integers double dPrice = 0.0;         // d prefix for decimals bool bIsActive = true;       // b prefix for booleans ArrayList lsUsers = new ArrayList();  // ls prefix for lists MainModel oUser = new MainModel();    // o prefix for objects


**Properties:** GetSet prefix
private string name = ""; [DataMember] public string GetSetname { get { return name; } set { name = value; } }


### Code Structure Pattern

**WebMethod Pattern:**
[WebMethod(EnableSession = true)] [ScriptMethod(UseHttpGet = false, ResponseFormat = ResponseFormat.Json)] public void methodName(String param1, String param2) { String jsonResponse = "";
try
{
    // Validate inputs
    if (string.IsNullOrWhiteSpace(param1))
    {
        object objError = new { status = "N", message = "Error message" };
        jsonResponse = new JavaScriptSerializer().Serialize(objError);
    }
    else
    {
        // Call controller
        MainController oMainCon = new MainController();
        var result = oMainCon.methodName(param1, param2);
        
        if (result)
        {
            object objSuccess = new { status = "Y", message = "Success message" };
            jsonResponse = new JavaScriptSerializer().Serialize(objSuccess);
        }
        else
        {
            object objFail = new { status = "N", message = "Failed" };
            jsonResponse = new JavaScriptSerializer().Serialize(objFail);
        }
    }
}
catch (Exception ex)
{
    object objEx = new { status = "N", message = "Error: " + ex.Message };
    jsonResponse = new JavaScriptSerializer().Serialize(objEx);
}

HttpContext.Current.Response.Clear();
HttpContext.Current.Response.ContentType = "application/json; charset=utf-8";
HttpContext.Current.Response.Write(jsonResponse);
HttpContext.Current.Response.Flush();
HttpContext.Current.Response.End();
}


**Controller Method Pattern:**
public bool registerUser(String name, String email) { DBConnect dbConnect = new DBConnect(sErrorLog); String query = "";
try
{
    // Validate inputs
    if (string.IsNullOrWhiteSpace(name) || string.IsNullOrWhiteSpace(email))
    {
        WriteToLogFile("MainController-registerUser: Invalid parameters");
        return false;
    }
    
    // Build query
    query = @" INSERT INTO users (name, email, status) 
              VALUES ('" + name + "', '" + email + "', 'ACTIVE') ";
    
    // Execute
    return dbConnect.Insert(query);
}
catch (Exception e)
{
    WriteToLogFile("MainController-registerUser: " + e.Message);
    return false;
}
}


**JavaScript Function Pattern:**
function submitForm() { // Get values var name = $("#txtName").val().trim(); var email = $("#txtEmail").val().trim();
// Validate
if (!name || !email) {
    displayAlert("All fields required", "danger");
    return;
}

if (!isValidEmail(email)) {
    displayAlert("Invalid email", "danger");
    return;
}

// Prepare data
var paramArray = JSON.stringify({
    GetSetname: name,
    GetSetemailaddress: email
});

// Call API
PageMethod("registerUser", paramArray, onSuccess, onError, false);
}
function onSuccess(response) { if (response.status === "Y") { displayAlert("Success: " + response.message, "success"); } else { displayAlert("Error: " + response.message, "danger"); } }
function onError(error) { displayAlert("Request failed", "danger"); console.error(error); }
function displayAlert(message, type) { var html = '<div class="alert alert-' + type + '">' + message + '</div>'; $("#messageContainer").html(html); }


---

## ✅ Best Practices

### Error Handling
- ✅ Always wrap database operations in try-catch blocks
- ✅ Log errors with context information
- ✅ Return user-friendly error messages
- ✅ Don't expose sensitive system information

### Performance
- ✅ Close database connections in finally blocks
- ✅ Use parameterized queries (prevent SQL injection)
- ✅ Cache frequently accessed data
- ✅ Minimize database round trips
- ✅ Use async operations where applicable

### Security
- ✅ Validate all user inputs (frontend & backend)
- ✅ Use parameterized queries for database access
- ✅ Don't hard-code credentials (use Web.config)
- ✅ Implement proper authentication/authorization
- ✅ Use SSL/HTTPS for sensitive data
- ✅ Implement rate limiting on API endpoints

### Code Quality
- ✅ Use meaningful class and method names
- ✅ Keep methods focused on single responsibility
- ✅ Add XML documentation comments
- ✅ Follow naming conventions consistently
- ✅ Keep methods under 50 lines
- ✅ Avoid code duplication (DRY principle)

### Testing
- ✅ Test each layer independently
- ✅ Use unit tests for business logic
- ✅ Test API endpoints (use Postman)
- ✅ Test form validation
- ✅ Test error scenarios

---

## 📊 Data Flow Example: User Registration
1.	USER ACTION (Frontend) ↓ User fills registration form and clicks Submit
2.	CLIENT-SIDE VALIDATION (JavaScript) ↓
•	Validate required fields
•	Validate email format
•	Show error if validation fails
3.	AJAX REQUEST ↓ POST /WebService.asmx/registerAsnaf { "GetSetname": "John Doe", "GetSeticno": "123456-12-1234", "GetSetemailaddress": "john@example.com" }
4.	WEBSERVICE LAYER ↓
•	Receive request
•	Validate null inputs
•	Call MainController.registerAsnaf()
5.	BUSINESS LOGIC LAYER ↓
•	Validate business rules
•	Check duplicate records
•	Call DBConnect.Insert()
6.	DATA ACCESS LAYER ↓
•	Open connection to MySQL
•	Execute INSERT query
•	Close connection
7.	RESPONSE ↓ JSON: { status: "Y", message: "Registration successful" }
8.	FRONTEND DISPLAY ↓
•	JavaScript receives response
•	Display success alert to user
•	Clear form fields


---

## 🔧 Development Workflow

### Adding New Feature: User Login

#### Step 1: Create Data Model
Add property to `MainModel.cs`:
private string password = ""; [DataMember] public string GetSetpassword { get { return password; } set { password = value; } }


#### Step 2: Add Business Logic
Add method to `MainController.cs`:
public MainModel loginUser(String email, String password) { MainModel oUser = new MainModel(); DBConnect dbConnect = new DBConnect(sErrorLog);
try
{
    if (dbConnect.OpenConnection() == true)
    {
        String query = @" SELECT id, name, email 
                        FROM users 
                        WHERE email = '" + email + "' 
                        AND password = '" + password + "' ";
        
        MySqlCommand cmd = new MySqlCommand(query, dbConnect.connection);
        MySqlDataReader dataReader = cmd.ExecuteReader();
        
        if (dataReader.Read())
        {
            oUser.GetSetid = replaceNull(dataReader, "id");
            oUser.GetSetname = replaceNull(dataReader, "name");
            oUser.GetSetemailaddress = replaceNull(dataReader, "email");
        }
        dbConnect.CloseConnection();
    }
}
catch (Exception e)
{
    WriteToLogFile("MainController-loginUser: " + e.Message);
}

return oUser;
}


#### Step 3: Add WebService Endpoint
Add method to `WebService.asmx.cs`:
[WebMethod(EnableSession = true)] [ScriptMethod(UseHttpGet = false, ResponseFormat = ResponseFormat.Json)] public void loginUser(String GetSetemailaddress, String GetSetpassword) { String jsonResponse = "";
try
{
    if (string.IsNullOrWhiteSpace(GetSetemailaddress) || string.IsNullOrWhiteSpace(GetSetpassword))
    {
        object objError = new { status = "N", message = "Email and password required" };
        jsonResponse = new JavaScriptSerializer().Serialize(objError);
    }
    else
    {
        MainController oMainCon = new MainController();
        MainModel oUser = oMainCon.loginUser(GetSetemailaddress, GetSetpassword);
        
        if (!string.IsNullOrEmpty(oUser.GetSetid))
        {
            object objSuccess = new { status = "Y", message = "Login successful", user = oUser };
            jsonResponse = new JavaScriptSerializer().Serialize(objSuccess);
        }
        else
        {
            object objFail = new { status = "N", message = "Invalid credentials" };
            jsonResponse = new JavaScriptSerializer().Serialize(objFail);
        }
    }
}
catch (Exception ex)
{
    object objEx = new { status = "N", message = "Error: " + ex.Message };
    jsonResponse = new JavaScriptSerializer().Serialize(objEx);
}

HttpContext.Current.Response.Clear();
HttpContext.Current.Response.ContentType = "application/json; charset=utf-8";
HttpContext.Current.Response.Write(jsonResponse);
HttpContext.Current.Response.Flush();
HttpContext.Current.Response.End();
}


#### Step 4: Create Frontend Form
Create `login.html`:
<div class="form-group"> <label for="txtEmail">Email</label> <input type="email" id="txtEmail" class="form-control" required /> </div>
<div class="form-group"> <label for="txtPassword">Password</label> <input type="password" id="txtPassword" class="form-control" required /> </div>
<button class="btn btn-primary" onclick="submitLogin()">Login</button>


#### Step 5: Add JavaScript Handler
Add to `app.js`:
function submitLogin() { var email = $("#txtEmail").val().trim(); var password = $("#txtPassword").val().trim();
if (!email || !password) {
    displayAlert("Email and password required", "danger");
    return;
}

var paramArray = JSON.stringify({
    GetSetemailaddress: email,
    GetSetpassword: password
});

PageMethod("loginUser", paramArray, onLoginSuccess, onLoginError, false);
}
function onLoginSuccess(response) { if (response.status === "Y") { displayAlert("Welcome, " + response.user.GetSetname, "success"); // Redirect to dashboard window.location.href = "dashboard.html"; } else { displayAlert("Invalid credentials", "danger"); } }
function onLoginError(error) { displayAlert("Login failed", "danger"); console.error(error); }


---

## 🐛 Troubleshooting

### Connection Issues
- Verify connection string in Web.config
- Check database server is running
- Verify username/password are correct
- Check firewall allows connection

### AJAX Errors
- Check browser console (F12) for error messages
- Verify WebService.asmx URL is correct
- Ensure JSON response format is valid
- Check Content-Type header

### Data Not Displaying
- Verify SQL query returns data
- Check data is serialized to JSON correctly
- Verify frontend JavaScript accesses data correctly
- Check for null values

---

## 📚 Documentation Files

### README.md
Framework overview and getting started guide

### CONTRIBUTING.md
Development guidelines, naming conventions, and code standards

---

## 🎓 Learning Resources

### Framework Concepts
1. **3-Tier Architecture** - Separation of concerns
2. **MVC Pattern** - Model-View-Controller principles
3. **REST APIs** - RESTful web service design
4. **AJAX** - Asynchronous JavaScript and XML
5. **JSON** - Data serialization format

### Technologies
- ASP.NET ASMX Web Services
- MySQL and MSSQL databases
- jQuery and Bootstrap
- HTML5 and CSS3

---

## 📝 Changelog

### Version 1.0 (August 2026)
- Initial framework release
- 3-Tier architecture implementation
- MySQL and MSSQL support
- AJAX/REST API integration
- Bootstrap responsive UI
- Comprehensive documentation

---

## 🤝 Support

For questions or issues:
1. Check the troubleshooting section
2. Review code standards in CONTRIBUTING.md
3. Check error logs in LogFile folder
4. Refer to method XML documentation

---

## 📄 License

Keiza .NET Framework v1.0  
Created: August 2026

---

**Happy coding with Keiza .NET Framework!** 🚀
