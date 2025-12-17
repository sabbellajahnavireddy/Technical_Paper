# REST Technical Paper

### 1. What is REST?
- REST (Representational State Transfer) is an architectural style for designing network-based applications.
- It uses standard HTTP protocols for communication between client and server.
Resources are identified using URLs.
Operations are performed using HTTP methods like GET, POST, PUT, and DELETE.
### 2. What is a RESTful API?
- A RESTful API is an API that follows REST architectural principles. It uses resource-based URLs and standard HTTP methods for operations. Each request is stateless, meaning the server does not maintain client session data. Responses are usually sent in a lightweight format such as JSON.

### 3. What is a resource in REST?
- A resource in REST represents any data entity that can be accessed or manipulated through an API. Each resource is uniquely identified by a URL. Resources can be collections or individual items. For example, /directors represents all directors, while /directors/1 represents a single director.

### 4. Explain the purpose of GET /directors.
- The GET /directors endpoint is used to retrieve a list of all directors from the server. It is a read-only operation and does not modify any data. The server responds with the data in JSON format. A successful request usually returns the HTTP status code 200 OK.

### 5. Explain the purpose of POST /directors.
- The POST /directors endpoint is used to create a new director resource. The client sends the director details in the request body. The server processes and stores the new data in the database. Upon successful creation, the server returns the status code 201 Created.

### 6. Explain the purpose of GET /directors/{id}.
- The GET /directors/{id} endpoint retrieves details of a specific director using its unique identifier. It allows the client to access a single resource. This operation does not change server data. If the resource exists, the server returns 200 OK; otherwise, it returns 404 Not Found.

### 7. Explain the purpose of PUT /directors/{id}.
- The PUT /directors/{id} endpoint is used to update an existing director’s information. The client sends the updated data in the request body. This operation replaces the existing resource with new values. A successful update returns 200 OK or 204 No Content.

### 8. Explain the purpose of DELETE /directors/{id}.
- The DELETE /directors/{id} endpoint is used to remove a director resource from the system. The ID specifies which resource should be deleted. Once deleted, the resource cannot be accessed again. A successful deletion returns 200 OK or 204 No Content.

### 9. What are RESTful API best practices?
- RESTful API best practices include using meaningful resource names and standard HTTP methods. APIs should be stateless to improve scalability. Proper HTTP status codes must be returned for every request. Data should be exchanged in a common format like JSON.

### 10. What HTTP status codes are commonly used in REST APIs?
- Common HTTP status codes in REST APIs include 200 OK for successful requests and 201 Created for resource creation. Client-side errors are indicated using 400 Bad Request. 404 Not Found is used when a resource does not exist. Server-side issues return 500 Internal Server Error.

### 11. How does REST use HTTP methods to perform CRUD operations?
- REST maps CRUD operations to HTTP methods in a standard way. GET is used to read data, POST is used to create new resources, PUT is used to update existing resources, and DELETE is used to remove resources. This clear mapping makes APIs easy to understand and maintain. Each method has a defined purpose and behavior.
- Example:
```bash
GET /directors
POST /directors
PUT /directors/1
DELETE /directors/1
```
### 12. How should request and response bodies be handled in REST APIs?
- In REST APIs, request and response bodies are usually exchanged in JSON format. The client sends data to the server using the request body for POST and PUT requests. The server responds with structured JSON data. This approach ensures platform independence and easy parsing.
- Example
```json
{
  "name": "Christopher Nolan",
  "country": "UK"
}
```

### 13. What is statelessness in REST and why is it important?
- Statelessness means that each client request contains all the information needed to process it. The server does not store any client session data between requests. This improves scalability and reliability. Each request is independent of previous requests.
- Example:
```bash
GET /directors/2
Authorization: Bearer <token>
```

### 14. How are HTTP status codes used in REST API responses?
- HTTP status codes indicate the result of an API request. They help the client understand whether the request was successful or failed. Correct usage of status codes improves API clarity and debugging. REST APIs must always return meaningful status codes.
- Example:
```bash
201 Created
404 Not Found
500 Internal Server Error
```

### 15. Give an example of a simple REST API endpoint implementation.
- A REST endpoint handles client requests and sends responses based on the HTTP method. It processes input data, performs business logic, and returns appropriate responses. Below is a simple example of a GET endpoint.
- Example:
```js
app.get("/directors", function (req, res) {
  res.status(200).json(directors);
});
```