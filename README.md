# dotnet-interview-prep

### What is Big O Notation ?

### What is CLR ?
CLR (Common Language Runtime) is the runtime environment that converts the IL code to machine code.
Features are:
* [x] Garbage collection
* [x] Ease usage of library written in other languages
* [x] Performance improvements
### What is IL (Intermediate Language) ?

### Explain the importance of garbage collector ?
The garbage collector (GC) acts a a memory manager. It is the background process which runs under CLR and claims unused managed resources.
### What is managed code and unmanaged code ?
<p>Code which runs under the CLR is called managed code.</p>
<p>Code which does not run under the control of CLR is called unmanaged code. </p>

### What are value types and reference types?

### Explain boxing and unboxing?

### What is the use of finally block?	

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

### Difference between ref and out keyword ?

### Difference between stack and heap ?

### What is the difference between Array and ArrayList ?

### What is the purpose of “params” keyword in C# ?

### What is the difference between String and StringBuilder?

### What is the difference between Fields and Properties?

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

### What is connection pooling in ADO.NET ?
Opening of database connection is very costly. To open a physical database connection our application does following:
* [x] Establish a socket connection
* [x] Make a initial hand-shake with the server
* [x] Parse the connection string
* [x] Make an authentication request to the server
* [x] Finally the connection object will be created
<p>Hence, to minimize the cost of opening of connections, ADO.NET uses an optimization technique called connection pooling. A connection pool is different for every unique connection string.</p>

### What are the different types of architecture available in ADO.NET ?

### What is LINQ and why is it used ?
LINQ stands for Language Integrated Query. It is a uniform programming model for any kind of data access. LINQ enables you to query and manipulate data independently of data sources. It also provides full type safety and compile time checking.

### What are the differences between lazy, eager and explicit loading in Entity Framework?

### What do you know about change tracking in Entity Framework?

### What is the difference between IEnumerable and IQueryable in Entity Framework?

### How is ACID property achieved in Entity Framework? How are auto increments handled in this ACID context?

### What do you know about repository patterns and unit of work pattern?

### What do you know about CQS, CQRS and ES?

### What is the meaning of asynchronous? How does Task Parallel Library help in performance? How do you handle DI lifetime and scope when starting a new Task?

### Define REST API. What is the difference between API and REST API? What makes API a REST API?

### How do you secure API?

### What are various HTTP Verbs/Methods? What are the major differences between GET and POST?

### What are the various HTTP Response codes and their purpose?

### What are the differences between Authentication and Authorization? How are RBAC and Claims used in regards to Authorization? How is Policy Based Authorization used in Aspnetcore?

### What are various types of Authentication? Eg Basic Auth.

### How do you manage multiple versions of API? Eg you have v1 and v2 APIs?

### What are middlewares in Aspnetcore? What is their usage?

### How familiar are you with AspnetIdentity and IdentityServer? Have you customized default behaviors of AspnetIdentitiy features (eg implementing custom hash function instead of default AspnetIdentity hash function)? Have you implemented MFA and passwordless authentication? Have you implemented LDAP authentication using AspentIdentity?