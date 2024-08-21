# **API Cheat Sheet**

<details>
  <summary><h2>1. What is an API?</h2></summary>
  
  - **API (Application Programming Interface):** A set of rules and tools for building software applications. APIs define how different software components should interact with each other.
  
</details>

<details>
  <summary><h2>2. Types of APIs</h2></summary>

  - **Open APIs (Public APIs):** Available to external developers and users. Examples: Google Maps API, Twitter API.
  - **Internal APIs (Private APIs):** Used within an organization. Not exposed to external users.
  - **Partner APIs:** Shared externally but with specific partners. Often used for business-to-business (B2B) transactions.
  - **Composite APIs:** Combine multiple data or service APIs into one. Useful for reducing client requests.

</details>

<details>
  <summary><h2>3. API Architectures</h2></summary>
  
  - **REST (Representational State Transfer):**
    - **Stateless:** Each request from a client to the server must contain all the information needed to understand and process the request.
    - **Resource-Based:** Resources (nouns) are identified by URLs. Actions are performed using standard HTTP methods.
    - **HTTP Methods:**
      - `GET`: Retrieve data.
      - `POST`: Create data.
      - `PUT`: Update data.
      - `DELETE`: Delete data.

  - **SOAP (Simple Object Access Protocol):**
    - **Protocol-Based:** Strictly defined standards for communication and messaging.
    - **XML-Based:** All requests and responses are formatted in XML.
    - **WS-Security:** Built-in security features.

  - **GraphQL:**
    - **Query Language:** Clients can request specific data.
    - **Single Endpoint:** One endpoint serves all requests.
    - **Real-Time Data:** Supports subscriptions for real-time updates.

  - **gRPC (Google Remote Procedure Call):**
    - **Protocol Buffers:** Uses a binary format for efficient serialization.
    - **Streaming:** Supports client-server streaming.
    - **Language Agnostic:** Can be used with multiple languages.

</details>

<details>
  <summary><h2>4. API Authentication</h2></summary>

  - **API Key:** Simple string that identifies the client.
  - **OAuth 2.0:** Token-based authentication standard that provides more secure and flexible access control.
    - **Flows:**
      - Authorization Code Flow
      - Client Credentials Flow
      - Implicit Flow
  - **JWT (JSON Web Tokens):** Compact, URL-safe tokens that contain user information. Often used with OAuth 2.0.

</details>

<details>
  <summary><h2>5. API Rate Limiting</h2></summary>

  - **Purpose:** Control the number of requests a client can make to prevent abuse.
  - **Common Strategies:**
    - **Fixed Window:** Limits based on a fixed time interval.
    - **Sliding Window:** More flexible; allows more requests in a sliding time window.
    - **Token Bucket:** Clients are given a certain number of tokens that they can spend on requests.

</details>

<details>
  <summary><h2>6. API Versioning</h2></summary>

  - **URL Versioning:** `/api/v1/resource`
  - **Header Versioning:** Custom header with version info.
  - **Query String Versioning:** `GET /resource?version=1.0`
  - **Semantic Versioning:** Follows `MAJOR.MINOR.PATCH` format (e.g., v2.1.0).

</details>

<details>
  <summary><h2>7. API Documentation</h2></summary>

  - **Swagger/OpenAPI:** Standard for defining RESTful APIs. Used to generate interactive documentation.
  - **Postman Collections:** Import and test APIs directly within Postman.
  - **RAML:** RESTful API Modeling Language for describing APIs.
  - **API Blueprint:** Markdown-based document for API description.

</details>

<details>
  <summary><h2>8. HTTP Status Codes</h2></summary>
  - **Response Code meaning**
    - 1xx - Information
    - 2xx - Success
    - 3xx - Redirect
    - 4xx - Client Error
    - 5xx - Server Error
  
  - Top 10:
    - `200 OK`: - *Successful request.
    - `201 Created`: Resource successfully created.
    - `204 No Content`: The server successfully processed the request, but is not returning any content.
    - `304 Not Modified`: The resource has not been modified since the last request.
    - `400 Bad Request`: The request could not be understood or was missing required parameters.
    - `401 Unauthorized`: Authentication failed or user does not have permissions.
    - `403 Forbidden`: Authentication succeeded, but the authenticated user does not have access.
    - `404 Not Found`: The requested resource could not be found.
    - `409 Conflict`: The request could not be processed because of a conflict in the request.
    - `500 Internal Server Error`: A generic error occurred on the server.

  - **HTTP Status Codes:**
    - `200 OK`: - *Successful request.
    - `201 Created`: Resource successfully created.
    - `204 No Content`: The server successfully processed the request, but is not returning any content.
    - `301 Moved Permanently`: The resource has been permanently moved to a new URL.
    - `302 Found`: The resource has been temporarily moved to a different URL.
    - `304 Not Modified`: The resource has not been modified since the last request.
    - `400 Bad Request`: The request could not be understood or was missing required parameters.
    - `401 Unauthorized`: Authentication failed or user does not have permissions.
    - `403 Forbidden`: Authentication succeeded, but the authenticated user does not have access.
    - `404 Not Found`: The requested resource could not be found.
    - `405 Method Not Allowed`: The HTTP method used is not allowed for this resource.
    - `409 Conflict`: The request could not be processed because of a conflict in the request.
    - `410 Gone`: The resource requested is no longer available and will not be available again.
    - `415 Unsupported Media Type`: The server does not support the media format of the requested data.
    - `422 Unprocessable Entity`: The request was well-formed but was unable to be followed due to semantic errors.
    - `429 Too Many Requests`: The user has sent too many requests in a given amount of time.
    - `500 Internal Server Error`: A generic error occurred on the server.
    - `502 Bad Gateway`: The server was acting as a gateway or proxy and received an invalid response from the upstream server.
    - `503 Service Unavailable`: The server is currently unavailable (due to overload or maintenance).
    - `504 Gateway Timeout`: The server was acting as a gateway or proxy and did not receive a timely response from the upstream server.

  - **Error Response Format:**
    $$$
    {
      "status": 400,
      "error": "Bad Request",
      "message": "User ID must be provided"
    }
    $$$

</details>

<details>
  <summary><h2>9. API Best Practices</h2></summary>

  - **Use HTTPS:** Always secure your API using HTTPS.
  - **Keep It Simple:** Use simple, intuitive, and consistent naming conventions.
  - **Idempotency:** Ensure that repeating requests have the same effect as a single request, particularly for `PUT` and `DELETE` operations.
  - **Pagination:** Implement pagination for endpoints that return large sets of data.
  - **Cache Responses:** Use caching to reduce server load and improve performance.
  - **Rate Limiting:** Implement rate limits to prevent abuse.
  - **Monitoring and Analytics:** Track usage and performance metrics to understand API usage patterns.

</details>

<details>
  <summary><h2>10. Tools for API Development</h2></summary>

  - **Postman:** For API testing and development.
  - **Insomnia:** An alternative to Postman, focused on simplicity.
  - **Swagger Editor:** For creating and editing OpenAPI specs.
  - **Newman:** Command-line tool for running Postman collections.
  - **Apigee:** API management platform by Google.
  - **Kong:** Open-source API gateway for managing and securing APIs.

</details>

<details>
  <summary><h2>11. API Gateway and Load Balancer</h2></summary>

  ### **API Gateway:**
  - **Purpose:** Acts as a single entry point for all client requests to an API. It handles routing, request composition, and other tasks such as authentication and rate limiting.
  - **Functions:**
    - **Request Routing:** Directs requests to the appropriate microservice or backend system.
    - **Authentication:** Verifies client credentials before forwarding requests.
    - **Rate Limiting:** Controls the rate of incoming requests to prevent abuse.
    - **Request Aggregation:** Combines data from multiple services into a single response.

  ### **Load Balancer:**
  - **Purpose:** Distributes incoming network traffic across multiple servers to ensure reliability and performance.
  - **Types:**
    - **Layer 4 (Transport Layer) Load Balancing:** Distributes traffic based on IP address and TCP/UDP port.
    - **Layer 7 (Application Layer) Load Balancing:** Distributes traffic based on data from the application layer protocols (e.g., HTTP, HTTPS).
  - **Functions:**
    - **Traffic Distribution:** Ensures no single server bears too much load, preventing overloads.
    - **Health Monitoring:** Regularly checks server health and directs traffic away from unhealthy servers.
    - **SSL Termination:** Offloads SSL decryption from the server, improving performance.

  ### **How They Work Together:**
  - **Client Request:** When a client makes an API request, it first hits the API Gateway.
  - **Routing & Authentication:** The API Gateway authenticates the request and routes it to the appropriate backend service.
  - **Load Balancing:** If the backend service is replicated across multiple servers, the API Gateway or a separate Load Balancer will distribute the requests among these servers to balance the load.
  - **Response:** The backend service processes the request and sends the response back through the API Gateway, which may aggregate data from multiple services before returning it to the client.

  ### **Example Workflow:**
  1. **Client sends a request** to the API Gateway.
  2. **API Gateway authenticates** the client and determines which service should handle the request.
  3. **Load Balancer** distributes the request to one of the available servers hosting the service.
 

 4. **Backend service processes** the request and returns the data to the API Gateway.
  5. **API Gateway aggregates** the data if necessary and sends the response back to the client.

</details>
