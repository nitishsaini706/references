### what is ajax?
- it is asynchronous javascript and xml 
- asynchronous means js does not have to wait for server response , but execute other scripts while waiting for server response and deal with response after response is ready
- it is used to load content on pages without reloading the full web page (eg cricket score update , weather update ,etc)
- it is client-side script that communicates to server without refreshing and reloading the entire web page
- it uses asynchronous request-response method to make application more interactive 

### Building blocks of ajax
- javascript = most important component is client side js code. it interacts with web server in the background and processes info before been displayed to user 
    - XMLHTTPREQUEST     api to transfer data between server and client

- dynamic html - it is browser function used to change or update page on fly, its drawback is it was heavily depended on client side code to update page . most of time page was not loaded on client side . thus needed to interact with server side code. this is where ajax came , it create connection between client and server side code by XHR object

- Document Object Model (DOM) - it is framework used to oranize elements in HTML. it is convention for representing and interacting with HTML object . THis model allows an interface for js to dynamically access and update contents of a page using DHTML. DOM is interface used to achieve DHTML.
### workflow
- userinterface --- js ----> ajax engine --- http request -----> webserver ---> db , backend server

- backend ,db server -----> web server --- json/xml/html --> ajax engine ----DHTML ------> user interface

- [1] user types in url and browser sends http request to server. server processes request and responds back with html content display on browser by web rendering engine .in web page js is embeded ,executed by js enterpreter when event is encountered 
- [2] when interacting with web page user encounters an element that uses js and triggers event . eg google search web page. as soon as user start typing in search query, undeyling ajax engine intercepts user's request. then it forwards request to server via http request
- [3] on server side , app layer processs request and return data back to ajax engine in json,xml form. it forwards this data to web render engine to be displayed on the browser and uses DHTML to update only the selected section of page 

### in js
- we create ajax xhr request to make new object
    - var a = new XMLHTTPRequest();

### object methods

- abort() - cancel current request

 - getAllResponseHeaders()- return header info
 - getResponseHeader() - specific header info 
 - open(method, url , async,user,pass) - this opnes a request using request type in method , url or file to open , true and false for syn call , and user and password are optional
- send = send rquest to server , (get request)
- send (string) = send request to server with info (post request)
 - setRequestHeader(Header,value) = adds value pair to header to be send 

### object properties
- onreadystatechange - fn to be called when ready state property changes 
- ready state - holds status of XHR
    - 0 - request not initialized 
    - 1 -server con established
    - 2 request received
    - 3 processing request
    - 4 request finished and response is ready 

- response text - returns response data as string
- response xml - returns repsonse data as xml data
- status - response status no. of request 
200 , 400 , 300 , etc
- status text - returns status text (eg 'OK' or 'NOT FOUND')

### ajax request
- sends request to server , XHR object is used 
    
         var xhttp= new XMLHttpRequest();
        xhttp.open("GET" , "ajax_info.txt",true);
        xhttp.send();

- GET OR POST ? 
- get is simpler and faster but we always use post when :
    - a cached file is not option (update file)
    - sending larger amount of data to server
    - sending user input
- we can send info with get in url 
    - open("GET',"aja.txt?fname=nitish&lname=saini", true);

- post request
    
        x.open("POST","ajax.txt",true);
        x.setRequestHeader("content-type","application/ x-www-form-urlencoded");
        x.send("fname=nitish&lname=saini");
    


``` javascript 

<button type="button" onclick="loadDoc()">Get my CD collection</button>
<br><br>
<table id="demo"></table>

<script>
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      myFunction(this);
    }
  };
  xhttp.open("GET", "cd_catalog.xml", true);
  xhttp.send();
}
function myFunction(xml) {
  var i;
  var xmlDoc = xml.responseXML;
  var table="<tr><th>Artist</th><th>Title</th></tr>";
  var x = xmlDoc.getElementsByTagName("CD");
  for (i = 0; i <x.length; i++) { 
    table += "<tr><td>" +
    x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;
}
</script>
```

``` javascript

let fetchBtn = document.getElementById('fetchBtn');
fetchBtn.addEventListener('click', buttonClickHandler)

function buttonClickHandler() {
     console.log('You have clicked the fetchBtn');

    // Instantiate an xhr object
    const xhr = new XMLHttpRequest();

    // Open the object
    // xhr.open('GET', 'https://jsonplaceholder.typicode.com/todos/1', true);

    // USE THIS FOR POST REQUEST
    xhr.open('POST', 'http://dummy.restapiexample.com/api/v1/create', true);
    xhr.getResponseHeader('Content-type', 'application/json');


    // What to do on progress (optional)
    xhr.onprogress = function(){
        console.log('On progress');
    }


    // xhr.onreadystatechange = function () {
    //     console.log('ready state is ', xhr.readyState);
        
    // }

    // What to do when response is ready
    xhr.onload = function () {
        if(this.status === 200){

            console.log(this.responseText)
        }
        else{
            console.log("Some error occured")
        }
    }

    // send the request
    params = `{"name":"test34sad545","salary":"123","age":"23"}`;
    xhr.send(params);

    console.log("We are done!");

}

let popBtn = document.getElementById('popBtn');
popBtn.addEventListener('click', popHandler);

function popHandler() {
    console.log('You have clicked the pop handler');

    // Instantiate an xhr object
    const xhr = new XMLHttpRequest();

    // Open the object
    xhr.open('GET', 'http://dummy.restapiexample.com/api/v1/employees', true);


    // What to do when response is ready
    xhr.onload = function () {
        if(this.status === 200){
            let obj = JSON.parse(this.responseText);
            console.log(obj);
            let list = document.getElementById('list');
            str = "";
            for (key in obj)
            {
                str += `<li>${obj[key].employee_name} </li>`;
            }
            list.innerHTML = str;
        }
        else{
            console.log("Some error occured")
        }
    }

    // send the request
    xhr.send();
    console.log("We are done fetching employees!");
    
}
```


### using promise for sending request

``` javascript
function func1() {
    return new Promise(function (resolve, reject) {
        setTimeout(() => {
            const error = true;
            if (!error) {
                console.log('Function: Your promise has been resolved')
                resolve();
            }
            else {
                console.log('Function: Your promise has not been resolved')
                reject('Sorry not fulfilled');
            }
        }, 2000);
    })
}

func1().then(function(){
    console.log("Harry: Thanks for resolving")
}).catch(function(error){
    console.log("Harry: Very bad bro. Reason: " + error)
})
```
### alternative to xhr requests
- fetch () - it give 2 promises 
``` javascript
// how to send data using get 
function getdata(){
    url = 'url';
    fetch(url).then(response ()=> return response.text();
    ).then((data =>console.log(data);
    )
}

getdata();

// for post method 

function post()
{
    url='urll';
    data='{ to sent to server in post }';
    para={
        method:"post",
        header:{
            'content-Type':'application/json'
        },
        body:data
    }
    fetch(url,para).then(response () => response.json())
    .then (data ()=>console.log(data))
}
```


### aysnc and await
- it return promise and when await jaha hota ha woh chiz backend mea asych hadle hota and rest code complete hone ke baad jatah vaha 

``` javascript
async function name(){
    console.log("inside function");
    const response = await fetch('url');
    console.log("fetching data ");
    const users = await response.json();
    console.log("data fetched");
    return users;  // promise dega in return
}

console.log("before callling");
let a = name();
console.log(a)
a.then( data => console.log(data))
```