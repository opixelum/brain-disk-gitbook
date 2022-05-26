# REST

## What?

REST is an **architectural style** for **developing web services**. It defines
**6 design principles**, used for **APIs**.


### Principles

1. **Uniform interface**: All API requests for the same resource should look
the same, no matter where the request comes from.

2. **Client-server decoupling**: In REST API design, client and server
applications must be completely independent of each other.

3. **Statelessness**: REST APIs are stateless, meaning that each request needs
to include all the information necessary for processing it.

4. **Cacheability**: When possible, resources should be cacheable on the client
or server side. 

5. **Layered system architecture**: In REST APIs, the calls and responses go
through different layers. REST APIs need to be designed so that neither the
client nor the server can tell whether it communicates with the end application
or an intermediary.

6. **Code on demand (optional)**: REST APIs usually send static resources, but
in certain cases, responses can also contain executable code (such as Java
applets).


## How?

REST APIs communicate via **HTTP requests** to perform **standard database**
**functions** like creating, reading, updating and deleting records (CRUD)
within a resource.
