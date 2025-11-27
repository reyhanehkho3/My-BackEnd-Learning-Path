- REpresentational State Transfer
-  An **architectural style** for designing networked applications. A **REST API** (or RESTful API) is an [API] that conforms to the constraints of the REST architecture.
-  **HTTP** as its protocol.    
- **URLs/URIs** to identify resources (like `/users`).
- **HTTP Methods** (GET, POST, PUT, DELETE) to define actions.
- **Data formats** like **JSON** to send and receive data.

## REST
For an API to be truly "RESTful," it must follow these six guiding principles:
#### client-server
The client and the server are separate.
#### Stateless
Each request must contain the info the server needs to process the request. 
#### Cacheable
Responses from the server must explicitly state whether they can be cached or not.
It means that when a server sends a response back to a client, it must **clearly indicate** whether that response can be stored ("cached") and reused later, or if it must be fetched fresh every time.
#### Uniform Interface
The most fundamental principle.
- **Resource-Based**: Everything is a **resource** (e.g., a user, a product, an order), identified by a URI (like `/users/123`).
- **Manipulation of Resources through Representations**: Clients interact with resources using a **representation** of that resource (like JSON or XML), not the actual resource on the server.
- **Self-descriptive Messages**: Each request and response contains enough information to describe how to process it.
- **HATEOAS (Hypermedia as the Engine of Application State)**: The response from the server should include hyperlinks to other related actions the client can take. (This is an advanced constraint that is often relaxed in simpler APIs).
#### Layered System
 The client doesn't know if it's connected directly to the end server or to an intermediary.
#### Code On Demand
 The server can send executable code to the client (like JavaScript). 
## why is REST so popular?
- **Simplicity & Standardization**: It uses well-known HTTP standards that every developer understands.
- **Scalability**: The stateless and layered nature makes it easy to scale applications.
- **Flexibility & Independence**: The client and server can be written in different programming languages (JavaScript, Python, Java, etc.) and can be developed and deployed independently.
- **Platform Agnostic**: Any device that can use HTTP (phones, browsers, IoT devices) can use a REST API.
 