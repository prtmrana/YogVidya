<p><a target="_blank" href="https://app.eraser.io/workspace/xUBfCwf20obCoRDXf0sZ" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

jQuery is a **fast, lightweight JavaScript library** that simplifies:

-  HTML DOM manipulation 
-  Event handling 
-  Animations 
-  AJAX calls 
👉 Instead of writing complex JavaScript, jQuery lets you do it in fewer lines.



```
// JavaScript
document.getElementById("demo").innerHTML = "Hello";

// jQuery
$("#demo").html("Hello");
```
- [ ] **Before jQuery (Problems in JavaScript)**
## ❌ Problem 1: Browser Compatibility
Different browsers had different ways to do the same thing.



```
// Chrome, Firefox
document.getElementById("btn").addEventListener("click", function() {
    alert("Clicked");
});

// Old Internet Explorer
document.getElementById("btn").attachEvent("onclick", function() {
    alert("Clicked");
});
```
✅ Solution 1: Cross-Browser Compatibility

```
$("#btn").click(function() {
    alert("Clicked");
});
```
👉 Works same in all browsers 👉 No need to worry about `addEventListener` vs `attachEvent` 



❌ Problem 2: Too Much Code

```
var element = document.getElementById("myDiv");
element.style.display = "none";
```
## ✅ Solution 2: Less Code (Write Less, Do More)
```
$("#myDiv").hide();
```
❌ Problem 3: Complex DOM Manipulation

```
document.getElementById("text").innerHTML = "Hello World";
```
👉 Finding elements:

- `getElementById` 
- `getElementsByClassName` 
- `getElementsByTagName` 


```
var element = document.getElementById("demo");
element.innerHTML = "Hello Preetam";
```
```
`getElementsByClassName`: ---

<p class="item">One</p>
<p class="item">Two</p>
<p class="item">Three</p>
```
```
var elements = document.getElementsByClassName("item");

for (var i = 0; i < elements.length; i++) {
    elements[i].innerHTML = "Updated";
}
```
```
`getElementsByTagName`:---->

<p>First</p>
<p>Second</p>
<p>Third</p>
```
```
var elements = document.getElementsByTagName("p");

for (var i = 0; i < elements.length; i++) {
    elements[i].style.color = "red";
}
```
✅ Solution 3: Easy DOM Manipulation

```
$("#text").text("Hello World");
```
```
<!DOCTYPE html>
<html>
<head>
    <title>CSS Selectors Example</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>

    <h1 id="title">Heading</h1>

    <p class="item">Item 1</p>
    <p class="item">Item 2</p>

    <p>Normal Paragraph</p>

    <button id="btn">Click Me</button>

    <script>
        $("#btn").click(function() {

            // #id selector
            $("#title").text("Updated Heading");

            // .class selector
            $(".item").css("color", "blue");

            // tag selector
            $("p").css("background", "yellow");

        });
    </script>

</body>
</html>
```
❌ Problem 4: AJAX was Complicated

```
<!DOCTYPE html>
<html>
<body>

<div id="result"></div>
<button onclick="loadData()">Load Data</button>

<script>
function loadData() {
    var xhr = new XMLHttpRequest();
    xhr.open("GET", "data.txt", true);

    xhr.onreadystatechange = function() {
        if (xhr.readyState == 4 && xhr.status == 200) {
            document.getElementById("result").innerHTML = xhr.responseText;
        }
    };

    xhr.send();
}
</script>

</body>
</html>
```
✅ Solution 4: Simplified AJAX

```
$.ajax({
    url: "data.txt",
    method: "GET",
    success: function(response) {
        $("#result").html(response);
    }
});
```




## 🔹 4. How to Use jQuery?
Step 1: Add jQuery

```
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
```
```
$(document).ready(function(){
    $("#btn").click(function(){
        alert("Button clicked");
    });
});
```




#  6. Important jQuery Functions (Interview)
# 🔥 1. `$(document).ready()`  
👉 Ensures DOM is loaded before running code

```
$(document).ready(function() {
    console.log("Page Loaded");
});
```
"It ensures that the DOM is fully loaded before executing jQuery code."



# 🔥 2. `click()`  
👉 Handles click events

```
$("#btn").click(function() {
    alert("Button clicked");
});
```
# 🔥 3. `hide()` / `show()`  
👉 Hide or show elements

```
$("#btn").click(function() {
    $("#text").hide();
});
```
```
$("#btn2").click(function() {
    $("#text").show();
});
```
🔥 4. `toggle()` 

👉 Switch between hide/show

```
$("#btn").click(function() {
    $("#text").toggle();
});
```
"It toggles visibility without writing separate hide/show logic."



# 🔥 5. `css()`  
👉 Change styles

```
$(".item").css("color", "red");
```
Used to dynamically apply CSS styles to elements



# 🔥 6. `addClass()` / `removeClass()`  
👉 Add or remove CSS class

```
$("#box").addClass("highlight");
$("#box").removeClass("highlight");
```
# 🔥 7. `text()` vs `html()`  
👉 Change content

```
$("#demo").text("Hello");        // plain text
$("#demo").html("<b>Hello</b>"); // HTML
```
# 🔥 8. `val()`  
👉 Get/set input value

```
var name = $("#inputBox").val();
```
🔥 9. `append()` / `prepend()` 



```
$("#list").append("<li>New Item</li>");
```
`append()` adds content at the end, `prepend()` adds at the beginning.



# 🔥 10. `ajax()` / `load()`  
👉 API calls



```
$.ajax({
    url: "data.txt",
    success: function(response) {
        $("#result").html(response);
    }
});
```




## **Simple code with ajax and jquery **
```
<!DOCTYPE html>
<html>
<head>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>

<button id="btn">Load Data (jQuery)</button>
<div id="result2"></div>


<button onclick="loadUsers()">Load Users (JS)</button>
<ul id="result1"></ul>

</body>
</html>
```
```
<script>
function loadUsers() {
 var xhr = new XMLHttpRequest();
 xhr.open("GET", "http://localhost:8080/getUsers", true);

 xhr.onload = function() {
 if (xhr.status == 200) {
 var users = JSON.parse(xhr.responseText);

 var output = "";
 for (var i = 0; i < users.length; i++) {
 output += "<li>" + users[i] + "</li>";
 }

 document.getElementById("result1").innerHTML = output;
 }
 };

 xhr.send();
}
</script>
```


Using JQuery:-

```
<script>
$("#btn").click(function() {

    $.ajax({
        url: "http://localhost:8080/getUsers",
        method: "GET",
        success: function(users) {
            var output = "";

            users.forEach(function(user) {
                output += "<li>" + user + "</li>";
            });

            $("#result2").html(output);
        }
    });

});
</script>
```




<!--- Eraser file: https://app.eraser.io/workspace/xUBfCwf20obCoRDXf0sZ --->