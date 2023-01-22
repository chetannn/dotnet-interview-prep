# dotnet-interview-prep

### What is Big O Notation ?
Big O Notation describes the complexity of the code using algebraic terms. The complexity are termed as `Best-case` and `Worst-case`.

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
`ref` and `out` keywords are used to pass data by reference.
| ref                                       | out                                                                                            |
|-------------------------------------------|------------------------------------------------------------------------------------------------|
| ref is two way from caller to the callee. | out is one way it sends data back from callee to caller and any data from caller is discarded. |
| It passes data and reference.             | It passes the reference only.                                                                  |

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
Singleton is a creational design pattern which ensures that the only one instance of the class is created throughout the life cycle of the application.
It use cases are:
* [x] Logging
* [x] Game Managers in Video games etc.

### What do you know about Onion Architecture?
It is a form of layered architecture where application heavily relies on the domain model which lies at the center of the system. In other words, all coupling is towards the center. Around the domain model, there are other layers which may vary. These layers interact with each others using interfaces. This architecture heavily relies on `Dependency Inversion Principle`.

### What is Dependency Injection? What are the popular Dependency Injection libraries? What are the various life time and scopes and its practical use cases?
Dependency Injection is a design methodology where in rather than  caller creating the instance, it's injected by some framework through constructor.
The popular Dependency Injection libraries are as:
* [AutoFac](https://autofac.org)
* [Simple Injector](https://simpleinjector.org)
* [Light Inject](https://www.lightinject.net)

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
We perform various database operation using Entity Framework. `DbContext` instance has a change tracker which tracks the changes such as `Add`, `Attach` and `Update` or query executed against the database. Whenever `SaveChanges` method is called, the changes made will be persisted to the database.

### What is the difference between IEnumerable and IQueryable in Entity Framework?
| IEnumerable                                                          | IQueryable                                                      |
|----------------------------------------------------------------------|-----------------------------------------------------------------|
| We can make use of IEnumerable using `System.Collections` namespace. | We can make use of IQueryable using `System.Linq` namespace.    |
| It is best suitable for in-memory operations.                        | It is best suitable for out-memory(remote database) operations. |
| It can be used for Linq to Objects or Linq to XML operations.        | It can be used for Linq to SQL operations.                      |
### How is ACID property achieved in Entity Framework? How are auto increments handled in this ACID context?

### What do you know about repository patterns and unit of work pattern?
Repository pattern is an extra layer that mediates bettwen the domain and the data mapping layers, acting like an in-memory collection of domain objects. Benefits are:
* [x] Minimize duplicate query logic.
* [x] Decouples your application from persistence frameworks. (eg. Entity framework)
* [x] It makes easier to unit test our application by creating the mock implementation of the repository.

Unit of work maintains a list of objects affected by a business transaction and coordinates the writing out of changes.

### What do you know about CQS, CQRS and ES?
CQS (Command Query Seperation) is a concept that divides an object's method into two categories:
* [x] <b>Queries:</b> It returns the result and do not change the state of the system.
* [x] <b>Command:</b> It changes the state of the system but does not return any value.

CQRS (Command Query Responsibility Segregation) is an architectural pattern that seperates the models for reading and writing the data. It is based on the `CQS` principal and even has more details. 

ES (Event Sourcing) is a different approach to store data. Instead of storing the current state in the application state are stored as a sequence of events.

### What is the meaning of asynchronous? How does Task Parallel Library help in performance? How do you handle DI lifetime and scope when starting a new Task?

### Define REST API. What is the difference between API and REST API? What makes API a REST API?
REST is a set of guidelines which helps in creating a system where applications can easily communicate with each other. If a system written by applying REST architecture concepts. it is called as RESTful API or REST API.

An API can be implemented using any kind of protocol where as REST API follows the HTTP protocol to communicate between two systems. An API is more over a general term.
Following are the guidelines that makes an API a REST API:

* Seperation of client and server
    * REST strictly operates on the web concept of Client and Server. Client and Server both operates without knowing each other. 

* Stateless
     * The server will not store anything about the latest HTTP request that the client made. It will treat every request as new. No session and no history.

* Uniform Interface
    * Particular resource is identified through URL (Uniform Resource Locator).

* Cacheable
    * The cacheable constraint requires that a response should implicitly or explicitly label itself as cacheable or non-cacheable.

* Layered System
    * The layered system style allows an architecture to be composed of hierarchial layers. For example: MVC is a layered system.

### How do you secure API?
We can secure an API by following ways:
* [x] Strong Authenication and Authorization mechanism such as OAuth 2.0 and OpenID Connect.
* [x] API input validation.
* [x] Rate Limiting.
* [x] Encrypting the traffic with TLS.
* [x] Usage of web application firewall.
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
When an application is deployed and started to be used in the production, It should be consistent and should not break for any reasons. But we are constantly rolling out new features, so in this case we try label the old Apis as the Version 1 and New Apis as Version 2. As a seperate version we can roll out changes without worrying about breaking things in production.
We can use `Microsoft.AspNetCore.Mvc.Versioning` package can be used to version our API.
In `Startup.cs` class:
```csharp
    services.AddApiVersioning(config => {
      config.DefaultApiVersion = new ApiVersion(1, 0);
      config.AssumeDefaultVersionWhenUnspecified = true;
    });
```
In `EmployeesController.cs` class:

```csharp

    [ApiVersion("1.0")]
    [ApiVersion("2.0")]
    public class EmployeesController : ControllerBase
    {
        public IActionResult Get()
        {
            //
        }

        [MapToApiVersion("2.0")]
        public IActionResult Get(string employeeName)
        {
            //
        }
    
    }
```

### What are middlewares in Aspnetcore? What is their usage?
Middlewares are the software that are assembled in an application pipeline. Each middleware can perform activities before and after the next component is called or invoked in the pipeline. Example:
```csharp
app.Run(async context =>
{
    await context.Response.WriteAsync("Hello world!");
});
```
Their usages are:
* [x] To handle exceptions.
* [x] To handle request logs.
* [x] To authorize request.

### How familiar are you with AspnetIdentity and IdentityServer? Have you customized default behaviors of AspnetIdentitiy features (eg implementing custom hash function instead of default AspnetIdentity hash function)? Have you implemented MFA and passwordless authentication? Have you implemented LDAP authentication using AspentIdentity?