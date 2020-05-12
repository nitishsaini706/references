### html dom 
- dom stands for document object model 

- it is structured representation of html ,it is part of document .

- it is interface between javascript and html+css
- it changes html into model , it is standard for how to get , change , add or delete html elements 
- dom methods are actions you can perform on html elements 
- all html elements are defined as objects
- html dom can be accessed by js
- a property is a value that you can get or set (like changing the content of an HTML element).
- method is an action you can do (like add or deleting an HTML element).


![img](https://github.com/nitishsaini706/references-images/blob/master/htmldom.gif)


### finding elements 
- The document object represents your web page
    
    - document.all - whole html document 
    - document.getElementById(id)	= Find an element by element id
    - document.getElementsByTagName(name)	= Find elements by tag name
    - document.getElementsByClassName(name)	 =  Find elements by class name
    - document.queryselector() = it return first element that matches a css style selector # for id  and . for class , only one element
    - document.queryselectorall() = return all elements 
``` javascript
let a = document;
a = document.all;
a = document.body;
a = document.forms[0];
Array.from(a).forEach(function(element){
    console.log(element);
})
a = document.links[0];
// use document.images and document.scripts and print the list of images and scripts on an html page
console.log(a);
```

### changing elements 

- element.innerHTML =  new html (content	Change the inner HTML of an element)
- element.attribute = new value	(Change the attribute value of an HTML element)
- element.style.property = new style	(Change the style of an HTML element)
- element.setAttribute(attribute,value) (Change the attribute value of an HTML element

``` javascript
let element = document.createElement('li');
let text = document.createTextNode('I am a text node');
element.appendChild(text)

// Add a class name to the li element
element.className = 'childul';
element.id = 'createdLi';
element.setAttribute('title', 'mytitle');
// element.innerText = '<b>Hello this is created by harry</b>';
// element.innerHTML = '<b>Hello this is created by harry</b>';

let ul = document.querySelector('ul.this');
ul.appendChild(element);
// console.log(ul)
// console.log(element)

let elem2 = document.createElement('h3');
elem2.id = 'elem2';
elem2.className = 'elem2';
let tnode = document.createTextNode('This is a created node for elem2');
elem2.appendChild(tnode);

element.replaceWith(elem2);
let myul = document.getElementById('myul');
myul.replaceChild(element, document.getElementById('fui'));
myul.removeChild(document.getElementById('lui'));
let pr = elem2.hasAttribute('href');
elem2.removeAttribute('id');
elem2.setAttribute('title', 'myelem2title');
console.log(elem2, pr);


```
)
### changing HTML content
- The easiest way to modify the content of an HTML element is by using the innerHTML property

        document.getElementById(id).innerHTML = new HTML

- we can add event handler also
  
        document.getElementById("myBtn").addEventListener("click", displayDate);
- 
        element.addEventListener("click", function(){ alert("Hello World!"); });


### navigating dom elements
- The entire document is a document node
- Every HTML element is an element node

- The text inside HTML elements are text nodes
- in node tree, top node is called root node
- every node has exaclty one parent , except root
- node can have no. of children

- parent node, childnode[node number]

        var myTitle = document.getElementById("demo").childNodes[0].nodeValue;

``` javascript
let cont = document.querySelector('.no');
cont = document.querySelector('.container');
let nodeName = cont.childNodes[1].nodeName;
let nodeType = cont.childNodes[1].nodeType;
 console.log(cont.childNodes);
// console.log(cont.children);  it returns the collection of html objects 

let container = document.querySelector('div.container');

// console.log(container.children[1].children[0].children);

// console.log(container.firstChild);
// console.log(container.firstElementChild);

// console.log(container.lastChild);
// console.log(container.lastElementChild);
// console.log(container.children);
// console.log(container.childElementCount); // Count of child elements

console.log(container.firstElementChild.parentNode);
console.log(container.firstElementChild.nextSibling);
console.log(container.firstElementChild.nextElementSibling);
console.log(container.firstElementChild.nextElementSibling.nextElementSibling);
```