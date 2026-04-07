<p><a target="_blank" href="https://app.eraser.io/workspace/pSyY6zJcmvl6GXcmtKov" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

### 📦 **RabbitMQ = Post Office**
-  You send a parcel 📦 
-  It goes to a queue 
-  One person receives it 
-  Once delivered → it’s **gone**
👉 Used for:

-  Sending email 
-  Processing orders 
-  Background jobs
### 📺 **Apache Kafka = YouTube / Netflix**
-  Video is uploaded once 🎥 
-  Many people can watch it 
-  You can replay anytime ⏪ 
👉 Used for:

-  Tracking events (bank transactions) 
-  Logs 
-  Real-time data streaming


## 🔑 Main Difference (1 line)
- **RabbitMQ** → “Do this task once” 
- **Kafka** → “Store and share events again and again”




🐰 **RabbitMQ Flow (Spring Boot)**

```
Controller → Service → Producer → Exchange → (RoutingKey MATCH) → Queue → Consumer
```
### Producer (Sender)
Uses: `RabbitTemplate`  (Spring interface)

### `Exchange (Router)` 
- ` Decides **which queue** message goes to` 
### ` Queue (Storage)` 
- ` Holds message until consumed` 
### Consumer (Listener)
Uses: `@RabbitListener` 





## 🧠 Key Classes / Interfaces
- `RabbitTemplate`  → Producer 
- `@RabbitListener`  → Consumer 
- `MessageListenerContainer`  → Internal listener 
- `Queue` , `Exchange` , `Binding`  → Config classes




<!--- Eraser file: https://app.eraser.io/workspace/pSyY6zJcmvl6GXcmtKov --->