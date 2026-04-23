<p><a target="_blank" href="https://app.eraser.io/workspace/tGYgTNu2w53AyqgPnGgX" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

CFRS  is a backend system designed to detect, manage, and track fraud-related activities in a banking environment.



- [ ] **High-Level Architecture** 
**Frontend Layer**

-  HTML, CSS, Bootstrap, JS (user dashboards) 
**Backend Layer**

-  Spring Boot microservices 
-  REST APIs 
**Security Layer**

-  Spring Security 
-  AES encryption (for request/response) 
**Database Layer**

-  Oracle (fraud data, user logs, transactions) 
**External Systems**

-  Banking APIs / DB-Link
- [ ] **FLOW:**
User logs into system --> Request goes through Spring Security authentication --> Data is AES encrypted --> API call hits Controller layer --> Controller → Service → Repository -->Data stored/retrieved from Oracle DB --> Fraud detection logic applied -->Response sent back (encrypted)



- [ ] Used **Microservices** → scalability & independent deployment 
- [ ]  Used **AES encryption** → secure sensitive banking data 
- [ ]  Used **DTO + ObjectMapper** → separation of concerns 
- [ ]  Used **Session management** → track user activity


- [ ] Handling Real-World Problems:
- **Concurrency** → multiple fraud requests handled simultaneously 
- **Security** → encrypted APIs + authentication 
- **Scalability** → can add more services if traffic increases 
- **Error handling** → global exception handling


- [ ] Deployment:
-  Built using Maven/Gradle 
-  Deployed on **Tomcat 9**
-  Config managed via `application.yml` 
- [ ] Logging (Log4j / SLF4J)
- [ ] Rate limiting 
- [ ] Future improvement: Kafka / Redis


![image.png](/.eraser/tGYgTNu2w53AyqgPnGgX___reH6N9pVJiNfGdAXN9KgdrK06xP2___image_qV5yqIkx87-NEG5L_1rMU.png "image.png")





- [ ] **Non-Functional Requirements**
1. **Scalability** → Microservices, horizontal scaling 
2. **Security** → AES + Spring Security 
3. **Performance** → Efficient queries, indexing 
4. **Reliability** → Exception handling, logging 
5. **Auditability** → IP logging, session tracking


👉 **System Design =**

```
Problem → Components → Flow → Database → Scaling → Deployment
```


_CFRS is a fraud detection system designed for banking applications. It follows a layered microservices architecture where the frontend interacts with Spring Boot REST APIs. Requests go through Spring Security for authentication and AES encryption. The backend processes requests via controller, service, and repository layers and stores data in MySQL. Fraud detection logic is applied in the service layer. The system also logs user activity like IP and login time for audit purposes. It is designed to be scalable, secure, and is deployed on Tomcat server._















**********************************ELK Stack***********************************



**Elasticsearch**

**Logstash**

**Kibana**



elasticsearch/config/elasticsearch.yml  ---->

```
network.host: 127.0.0.1
http.port: 9200
xpack.security.enabled: false
discovery.type: single-node
```
▶️  Start Elasticsearch

```
cd elasticsearch/bin
elasticsearch.bat
```
👉 Test:

```
http://localhost:9200
```
# ⚙️ Step 4: Configure Logstash
Create file:

C:\elk\logstash.conf



```
input {
  tcp {
    port => 5000
    codec => json
  }
}

output {
  elasticsearch {
    hosts => ["http://localhost:9200"]
    index => "springboot-logs-%{+YYYY.MM.dd}"
  }
  stdout { codec => rubydebug }
}
```
# ▶️ Step 5: Start Logstash
```
cd logstash/bin
logstash -f C:\elk\logstash.conf
```
👉 It should show:

```
Successfully started Logstash
```
# ⚙️ Step 6: Configure Kibana
Go to:

```
kibana/config/kibana.yml
```
Uncomment/set:

```
server.port: 5601
elasticsearch.hosts: ["http://localhost:9200"]
```
# ▶️ Step 7: Start Kibana
```
cd kibana/bin
kibana.bat
```
👉 Open:

```
http://localhost:5601
```
# 🧠 How they connect (simple view)
```
Spring Boot → Logstash → Elasticsearch → Kibana
```
-  Logstash listens on port **5000**
-  Elasticsearch runs on **9200**
-  Kibana runs on **5601**
### Correct order (important)
1.  Start **Elasticsearch**
2.  Start **Logstash**
3.  Start **Kibana**
4.  Run your Spring Boot app




# 🧩 Who does what in ELK?
### 1️⃣ **Elasticsearch** → _Storage + Search Engine_
👉 Think of it as:

>  “Database for logs + super-fast search engine” 

### What it does:
-  Stores all logs 
-  Indexes them (like Google search) 
-  Lets you query/filter logs instantly




### 2️⃣ **Logstash** → _Data Processor_
👉 Think of it as:

>  “Middleman + transformer” 

### What it does:
-  Receives logs from Spring Boot 
-  Converts them into structured JSON 
-  Can filter/modify data 
-  Sends to Elasticsearch


### 3️⃣ **Kibana** → _UI / Dashboard_
👉 Think of it as:

>  “Frontend for Elasticsearch” 

### What it does:
-  Shows logs in UI 
-  Lets you search/filter 
-  Create dashboards, charts, alerts 
### Example:
-  View all errors today 
-  Graph: requests per minute 
-  Filter: logs from one service




************************Swagger Open AI ********************************

I used Swagger (OpenAPI) to document APIs, added request/response schemas, handled error responses, secured it using JWT, and restricted access to admin users. I also disabled it in production using profiles.

### How Swagger works internally?
👉

-  Reads annotations 
-  Generates OpenAPI JSON (`/v3/api-docs` ) 
-  UI renders it




```
springdoc.swagger-ui.enabled=false
```
### Why do we use Swagger?
👉

-  API documentation 
-  Interactive testing 
-  Helps frontend & QA teams


What annotations have you used?



👉 Common ones:



```
@Operation
@ApiResponse
@Schema
@Parameter
```
7. How do you document request and response?

```
@Schema(description = "User name", example = "John")
private String name;
```
8. How do you handle error responses in Swagger?

```
@ApiResponses({
  @ApiResponse(responseCode = "404", description = "Not found")
})
```
###  What annotations have you used?
👉 Common ones:

- `@Operation` 
- `@ApiResponse` 
- `@Schema` 
- `@Parameter` 
---

### 7. How do you document request and response?
```
@Schema(description = "User name", example = "John")private String name;
```
---

### 8. How do you handle error responses in Swagger?
```
@ApiResponses({  @ApiResponse(responseCode = "404", description = "Not found")})
```
---





<!--- Eraser file: https://app.eraser.io/workspace/tGYgTNu2w53AyqgPnGgX --->