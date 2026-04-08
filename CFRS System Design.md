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



<!--- Eraser file: https://app.eraser.io/workspace/tGYgTNu2w53AyqgPnGgX --->