<p><a target="_blank" href="https://app.eraser.io/workspace/AJ7vGokUJrqAcl57x0nF" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

AJAX = **Asynchronous JavaScript And XML**

👉 It allows:

-  Sending/receiving data from server 
-  Without reloading the page
Without AJAX:

-  Full page reload needed 
With AJAX:

-  Faster 
-  Better UX 
-  Partial updates
# 🔹 How AJAX Works (Flow)**
1.  User clicks button 
2.  AJAX request sent to server 
3.  Server processes request (Spring Boot API) 
4.  Response comes (JSON) 
5.  Page updates without reload
- [ ] ** $.ajax() method **
```
$.ajax({
    url: "/api/data",
    type: "GET",
    success: function(response){
        console.log(response);
    },
    error: function(error){
        console.log(error);
    }
});
```
- [ ] **GET Request**
```
$.get("/api/data", function(data){
    console.log(data);
});
```
- [ ] **POST Request**
```
$.post("/api/save", {name: "Preetam"}, function(response){
    console.log(response);
});
```
```
$("#saveBtn").click(function(){
    $.ajax({
        url: "/saveUser",
        type: "POST",
        contentType: "application/json",
        data: JSON.stringify({
            name: "Preetam",
            email: "test@gmail.com"
        }),
        success: function(res){
            alert("Saved Successfully");
        }
    });
});
```
```
@PostMapping("/saveUser")
public ResponseEntity<String> saveUser(@RequestBody User user){
    return ResponseEntity.ok("Saved");
}
```




# 🔥 jQuery vs AJAX (Simple Explanation)
### 🔹 jQuery
👉 **jQuery is a JavaScript library**

-  It helps you: 
    -  Manipulate HTML (DOM) 
    -  Handle events 
    -  Do animations 
    -  Call AJAX easily 

👉 Think:
 **jQuery = tool/library**

---

### 🔹 AJAX
👉 **AJAX is a technique (not a library)**

-  It is used to: 
    -  Send request to server 
    -  Get response from server 
    -  Without reloading the page 

👉 Think:
 **AJAX = concept/approach**



## **👉 jQuery uses AJAX internally**
# 🎯 Real-Life Analogy
- **AJAX = Phone call 📞**
- **jQuery = Smartphone 📱**
👉 You can make a call (AJAX)
 👉 But jQuery makes it **easier and faster**

👉 **“jQuery is a JavaScript library used to simplify coding, while AJAX is a technique used to communicate with the server asynchronously without reloading the page. jQuery provides built-in methods like **`**$.ajax()**`** to implement AJAX easily.”**



<!--- Eraser file: https://app.eraser.io/workspace/AJ7vGokUJrqAcl57x0nF --->