# dotnet-interview-prep

### What is Big O Notation ?

### What is CLR ?
CLR (Common Language Runtime) is the runtime environment that converts the IL code to machine code.
Features are:
* [x] Garbage collection
* [x] Ease usage of library written in other languages
* [x] Performance improvements
### What is IL (Intermediate Language) ?
When we compile any code written in high level language such as C#, code written is converted to IL (Intermediate Language) code. Then after IL code runs over the CLR to get executed on the machine.
### Explain the importance of garbage collector ?
The garbage collector (GC) acts a a memory manager. It is the background process which runs under CLR and claims unused managed resources.
### What is managed code and unmanaged code ?
<p>Code which runs under the CLR is called managed code.</p>
<p>Code which does not run under the control of CLR is called unmanaged code. </p>

### What are value types and reference types?

### Explain boxing and unboxing?
When data moves from value type to reference type it is called Boxing. Example.
```csharp
int a = 25;
object o = a;
```
When data moves from reference type to value type it is called Unboxing. Example:
```csharp
object o = 25;
int a = (int)o;
```
Boxing and Unboxing leads to performance problem. We should avoid it as much as possible.
### What is the use of finally block?
It is the block of code which executes irrespective of the exception or not. It is used along with `try` and `catch` block. Some cleanup code is written in this block. For example:
```csharp
var con = new SqlConnection();
try 
{
    con.Open();
}
catch(Exception ex)
{
    throw ex;
}
finally
{
    con.Close();
}
```
### Explain casting, implicit casting and explicit casting?
Converting from one data type to another is called casting.
If the casting happen automatically, then it is called implicit casting.
In other words, when you try to convert lower types to higher types it is called as implicit casting.
```csharp
short a = 25;
int b = a;
```
When you try to convert higher types to lower types then it is called explicit casting.
```csharp 
double a = 25.23;
int b = a;
```
Here ``` .23 ``` is loosed. That is the disadvantage of explicit casting i.e data loss.
### Difference between constant and read only ?
| const                                                                            | readonly                                                                                                           |
|----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| It is considered as absolute constant i.e we have to initialize while declaring. | The variable declared with readonly keyword will be initialized either while declaring or within the construcutor. |
| It is compile time constant.                                                     | It is runtime constant.                                                                                            |
### Difference between ref and out keyword ?

### Difference between stack and heap ?

### What is the difference between Array and ArrayList ?
| Array                                       | ArrayList                                            |
|---------------------------------------------|------------------------------------------------------|
| Array has fixed length.                     | ArrayList is dynamic in nature.                      |
| It is strongly typed.                       | It does not have strong typings.                     |
| Array can only store define data types.     | ArrayList can store any datatypes.                   |
| It is included in `System.Array` namespace. | It is included in `System.Collections` namespace.     |
| It is performant than ArrayList             | It has performance issue due to Boxing and Unboxing. |
### What is the purpose of “params” keyword in C# ?
Params is used as a parameter which can take the variable number of arguments. For example:
```csharp
public int Add(params int[] numbers)
{
    int sum = 0;
    for(int i=0; i < numbers.Length; i++)
    {
        sum += numbers[i];
    }

    return sum;
}

Console.WriteLine(Add(123));
Console.WriteLine(Add(1234567));
```
### What is the difference between String and StringBuilder?
| String                                                                                                                                                         | StringBuilder                             |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| It is immutable.                                                                                                                                               | It is mutable                             |
| It is included in `System` namespace.                                                                                                                          | It is included in `System.Text` namespace |
| It is not recommended to use string for large string manipulation because every time when you assign a new value to a string variable new instance is created. | It is performant for larger strings.      |

### What is the difference between Fields and Properties?
A Field is a normal class variable. Example:
```csharp
class Employee 
{
    public string name;
}
```
A Property is an abstraction over a field. Getters and Setters can be define for a Property. A Property internally  maintains aa field known as `backing field`. Example:
```csharp
class Employee
{
    public string Name { get; set; }
}
```

### What do you mean by Reflection in C# ? 
Reflection is the ability of a code to access the metadata of the assembly during the runtime.
Example:
```csharp 
 string name = "Chetan Kharel";
 Console.WriteLine(name.GetType());
```
### When should we use abstract classes and when should we use interfaces? When do you override a function?

### What is Singleton class and what are its use cases?

### What do you know about Onion Architecture?

### What is Dependency Injection? What are the popular Dependency Injection libraries? What are the various life time and scopes and its practical use cases?

###  What do you know about SOLID principles?

### What do you know about ORM? What are the advantages of ORM?
ORM (Object Relational Mapping) is a mapping tool which is used to convert data between systems of incompatible types using object oriented programming languages. Advantages of ORM are:
* [x] It speeds up the development time.
* [x] It abstracts the logic for maintaining the database connection. 
* [x] It improves security. ORM eliminates the potential SQL injection attack by sanitizing the parameter.

### What is connection pooling in ADO.NET ?
Opening of database connection is very costly. To open a physical database connection our application does following:
* [x] Establish a socket connection
* [x] Make a initial hand-shake with the server
* [x] Parse the connection string
* [x] Make an authentication request to the server
* [x] Finally the connection object will be created
<p>Hence, to minimize the cost of opening of connections, ADO.NET uses an optimization technique called connection pooling. A connection pool is different for every unique connection string.</p>

### What are the different types of architecture available in ADO.NET ?
ADO.NET supports two type of architecture or model for interacting with the database. i.e
* a. ADO.NET Disconnected
When we use ADO.NET Disconnected Model then we don't need the connectivity between the application and the database for interacting with any database. We use `Connection`, `DataAdapter` and `DataSet` classes provided by the `System.Data` namespace for the disconnected model.
* b. ADO.NET Connection Oriented Model
When we use ADO.NET Connection Oriented Model then the connectivity between the application and the database has to be maintained till the application interacts with the database. We use `Connection`, `Commmand`,`DataReader` classes provided by the `System.Data` namespace for the connection oriented model.

### What is LINQ and why is it used ?
LINQ stands for Language Integrated Query. It is a uniform programming model for any kind of data access. LINQ enables you to query and manipulate data independently of data sources. It also provides full type safety and compile time checking.

### What are the differences between lazy, eager and explicit loading in Entity Framework?
Eager Loading refers to the related data to be loaded from the database as a part of the initial the initial query. Example:
```csharp
using (var context = new AppDbContext())
{
    var employees = context.Employees.Include(employee => employee.Department);
}
```
Lazy loading refers to the related data to be loaded only when the navigation property is accessed.
We need to use additional package called `Microsoft.EntityFrameworkCore.Proxies` for the EF Core to utilize Lazy loading feature and the property in the model should be marked as `virtual` as well. Example:
```csharp
// This is done in Startup.cs or Program.cs (dotnet core 6.0 +)
var builder = WebApplicationBuilder.CreateBuilder(args);
builder.services.AddDbContext<AppDbContext>(
        opts => opts
        .UseLazyLoadingProxies()
        //.Use (Any database provider)
        );
```

Explicit Loading refers to the loading mechanism where we load related data at the later point of time when required. This initial query does not contain the related records. It is the choice of the developer to load the data using Explicit loading. Example:
```csharp
using(var context = new AppDbContext())
{
    var employee = context.Employees.First();

    context.Entry(employee)
            .Reference(e => e.Department)
            .Load();
}
```

### What do you know about change tracking in Entity Framework?

### What is the difference between IEnumerable and IQueryable in Entity Framework?
| IEnumerable                                                          | IQueryable                                                      |
|----------------------------------------------------------------------|-----------------------------------------------------------------|
| We can make use of IEnumerable using `System.Collections` namespace. | We can make use of IQueryable using `System.Linq` namespace.    |
| It is best suitable for in-memory operations.                        | It is best suitable for out-memory(remote database) operations. |
| It can be used for Linq to Objects or Linq to XML operations.        | It can be used for Linq to SQL operations.                      |
### How is ACID property achieved in Entity Framework? How are auto increments handled in this ACID context?

### What do you know about repository patterns and unit of work pattern?

### What do you know about CQS, CQRS and ES?

### What is the meaning of asynchronous? How does Task Parallel Library help in performance? How do you handle DI lifetime and scope when starting a new Task?

### Define REST API. What is the difference between API and REST API? What makes API a REST API?

### How do you secure API?

### What are various HTTP Verbs/Methods? What are the major differences between GET and POST?
The various HTTP Verbs/Methods are as:
* [x] GET
* [x] POST
* [x] PUT
* [x] PATCH
* [x] DELETE

The major differences between `GET` and `POST` are as:

| GET                                                      | POST                                                                         |
|----------------------------------------------------------|------------------------------------------------------------------------------|
| GET requests are saved in browser history.               | POST requests are not saved in browser history.                              |
| GET method only supports 2048 characters in the request. | It has no restriction over the amount of data to be sent.                    |
| Data are visible in the URL.                             | Data are sent using request body so that none of the request payload is visible. |
| It only supports the following encoding: application/x-www-form-urlencoded                 | It supports following encoding type:application/x-www-form-urlencoded and multipart/form-data   |

### What are the various HTTP Response codes and their purpose?
| Status Code | Purpose                                                                     |
|-------------|-----------------------------------------------------------------------------|
| 200         | It refers to successful HTTP response.                                      |
| 201         | It refers to successful creation of a resource.                             |
| 301         | It refers to permanent redirection.                                         |
| 400         | It refers to Bad Request. Generally thrown when validating request payload. |
| 401         | It refers to Unauthorized.                                                  |
| 404         | It refers to Not found HTTP response.                                       |
| 500         | It refers to Internal Server Error.                                         |
### What are the differences between Authentication and Authorization? How are RBAC and Claims used in regards to Authorization? How is Policy Based Authorization used in Aspnetcore?

### What are various types of Authentication? Eg Basic Auth.

### How do you manage multiple versions of API? Eg you have v1 and v2 APIs?

### What are middlewares in Aspnetcore? What is their usage?

### How familiar are you with AspnetIdentity and IdentityServer? Have you customized default behaviors of AspnetIdentitiy features (eg implementing custom hash function instead of default AspnetIdentity hash function)? Have you implemented MFA and passwordless authentication? Have you implemented LDAP authentication using AspentIdentity?