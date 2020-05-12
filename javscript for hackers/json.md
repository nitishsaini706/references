### what is json?
- it is javascript object notation 

- it is used to store and exchange data between browser and server
- data is name value pair , curly braces hold object amd square brackets hold array

- to access we use = object.key 
- in json key is also a string 
    - { "name" : "nitish"}
- in js key is not string
    - { name : "nitish" }

- we can request json from server using ajax request 
-  we convert js into json and send to server and convert json into js object recieved form server
    - we use JSON.parse() = to convert json into js
- to send data to server we convert js into json
    - JSON.stringify()
- we use ajax request to get json from server 

``` javascript
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
  if (this.readyState == 4 && this.status == 200) {
    var myObj = JSON.parse(this.responseText);
    document.getElementById("demo").innerHTML = myObj.name;
  }
};
xmlhttp.open("GET", "json_demo.txt", true);
xmlhttp.send();
```