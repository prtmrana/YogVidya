<p><a target="_blank" href="https://app.eraser.io/workspace/d0T3WwsniWJ7rE4OGH1V" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

**ObjectMapper** is a class from the Jackson library used to:

👉 Convert **JSON ↔ Java Objects**



👉 “ObjectMapper is used to serialize Java objects into JSON and deserialize JSON into Java objects.”

# 🔥 What problem does it solve?
Before ObjectMapper, developers had to:

❌ Manually parse JSON
 ❌ Write lots of boilerplate code
 ❌ Handle nulls, types, nested objects manually

```
ObjectMapper mapper = new ObjectMapper();
User user = mapper.readValue(json, User.class);
```




👉 “In our project, ObjectMapper is used after decrypting AES payloads to convert JSON requests into DTOs, and also to convert response objects back into JSON.”



```
ObjectMapper mapper = new ObjectMapper();

// JSON → Object
User user = mapper.readValue(jsonString, User.class);

// Object → JSON
String json = mapper.writeValueAsString(user);
```




<!--- Eraser file: https://app.eraser.io/workspace/d0T3WwsniWJ7rE4OGH1V --->