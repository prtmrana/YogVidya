<p><a target="_blank" href="https://app.eraser.io/workspace/eZhx1OICCbfVwM4zuHFx" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

I have used spring boot  by default logging framework :

- **SLF4J (Simple Logging Facade for Java)** → abstraction 
- **Logback** → actual implementation
` private static final Logger logger = LoggerFactory.getLogger(UserService.class);` 



```
logger.trace("Trace log - very detailed");
logger.debug("Debug log - developer info");
logger.info("User created successfully");
logger.warn("Unexpected input received");
logger.error("Exception occurred while saving user", e);
```
| Level | Use Case |
| ----- | ----- |
| TRACE | Very detailed (rarely used) |
| DEBUG | Debugging during development |
| INFO | Normal application flow |
| WARN | Unexpected but handled |
| ERROR | Failure or exception |
✅ Configure logging in `application.properties` 

```
logging.level.root=INFO
logging.level.com.myapp=DEBUG

logging.file.name=app.log
logging.pattern.console=%d{yyyy-MM-dd HH:mm:ss} - %msg%n  
```
**✔ Use placeholders (avoid string concatenation)**

```
logger.info("User {} logged in", userId);
```
** instead of  ❌ Avoid:  `logger.info("User " + userId + " logged in");` 



### **In which folder these logs come in tomcat server : **
Location: `<TOMCAT_HOME>/logs/` 

Important files:

- `catalina.out`  → main logs 
- `localhost.log` 
- `manager.log` 
👉 Your application logs usually go into `**catalina.out**` by default 



in properties file we have to define which level we want to get logs:

`logging.level.root=INFO` : this is by default .

but we can change it : `logging.level.root=DEBUG` 



# **Logback-spring.xml**
# ✅ 1. What is `logback-spring.xml`?
👉 It is a **custom configuration file for Logback** (Spring Boot logging system)

-  Gives full control over logging 
-  More powerful than `application.properties` 
-  Supports **profiles (dev, prod)**
  We use logback-spring.xml to customize logging behavior such as : 

1. log format ✅
2.  file storage ✅
3. log rotation ✅




![image.png](/.eraser/eZhx1OICCbfVwM4zuHFx___reH6N9pVJiNfGdAXN9KgdrK06xP2___image_FdI1i0x4uxIeVAC6BWLP8.png "image.png")



 different log levels for different environment🚀 Application Starts
              │
              ▼
Spring Boot Logging Initialization
              │
              ▼
Detect Logging Framework (SLF4J + Logback)
              │
              ▼
Load Configuration File
(logback-spring.xml ✅)
              │
              ▼
Parse XML Configuration
├── Properties (LOG_PATH, PATTERN)
├── Appenders (CONSOLE, FILE)
├── Logger Levels
└── Root Logger
              │
              ▼
Create Appenders
├── ConsoleAppender → Terminal / Tomcat
└── RollingFileAppender → Log File
              │
              ▼
Application Running...
              │
              ▼
🧑‍💻 Code Executes
logger.debug("Inside authenticate()")
              │
              ▼
Check Log Level
├── DEBUG enabled? → YES ✅ → Continue
└── NO ❌ → Ignore log
              │
              ▼
Logger Hierarchy Check
├── Package Logger (com.myapp.service)
└── Else Root Logger
              │
              ▼
Send Log to Appenders
├── CONSOLE
└── FILE
              │
              ▼
Encoder Formats Log
Example:
2026-04-09 12:00:00 DEBUG AuthService - Inside authenticate()
              │
              ▼
Output Generated
├── Console (visible in terminal / Tomcat)
└── File (/opt/app/logs/app.log) 





***********************************************************************

![image.png](/.eraser/eZhx1OICCbfVwM4zuHFx___reH6N9pVJiNfGdAXN9KgdrK06xP2___image_PzJYpju3Fby_NBOCULCYf.png "image.png")

When the Spring Boot application starts, it loads the logback-spring.xml configuration file. This file defines appenders like console and file, and sets log levels for different packages. When a logger statement is executed, Logback checks whether the log level is enabled. If enabled, it formats the log using a defined pattern and sends it to configured destinations like console or log files. In production, we usually log to files with rolling policies instead of console.



<!--- Eraser file: https://app.eraser.io/workspace/eZhx1OICCbfVwM4zuHFx --->