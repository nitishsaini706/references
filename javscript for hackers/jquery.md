### jquery
- it is javascript library which shortens our code 
- we need to  add jquery in our file by downloading or by cdn and add it in script tag
- basic syntax $(selector).action()

    - $(document).ready(function())  = this is used to prevent code from running before document is ready 
### selecting
- we can use $ sign to select in jquery , unlinke document.getElementById which is vanila js 

    - eg $('img'),$('h1') ,etc
- we use .css to change style 
    - eg $('h1'.css("color","red");
- we have some keywords like 
    - $("p:first") - to select first p
    - and many more are present

### common jquery methods 
- to change first or last we use .first() or .last() with the tag
- text () - it returns only text
    - $('h1').text().first(); # return heading of the first tag
    - $("h1").text("hello"); # changes the text

- html() - it is same as innerhtml 
    - $("h1").html(); # display html contents
    - $("h1").html("helllo") # changes html contents too

- attr() - attributes  - to change the attribute of a tag
    - $("img").attr("src")  # returns the attribute
    - $("img").attr("src",link)  # set attribute 

- val() - used to extract value of 
    - .val() # used to get value
    - .val("hello") # used to set value

### manipulating classes

- $("h1").addclass("correct") # add h1 to class with name correct
- $("h1").removeclass("name") # removes the class

### event listner in jquery
- jquery click = it is method which is very quick and easy to add a click listner to elements .
    - $("# submit").click(function(){
        console.log("another click");
    });

- keypress = it is quick and easy way to add a keypress listner to element , we use keycode , if user press enter which as keycode is 13 we tell user which key he has pressed , we use which . event.which=13
    - $("input[type = "text"]").keypress(function(){
        alert("hello");
    });

- on() = it is like addeventlistner , let us specify the type of event . we can add any event in this like click , double click , keypress ,etc.
    - $("input").on("click", function(){
        console.log("hello");
    });

    - $("h1").on("clicl",function(){
        $("h1").css("color","red");
    }); 
    - the above statement will change all the h1 when clicked
    - we use this keyword to change only paticular h1 
    - #("h1").on("click",function(){
        $(this).css("colo","red");
    });


    