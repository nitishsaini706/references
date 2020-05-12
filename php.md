### what is php ?
- it stands for php:hypertext processor 
- it's files has .php extension
- php files contain text , html , css , js and php code

### basic syntax 
- php scripts starts with  <?php and ends with ?>
``` php
<?php
	//code
?>
```
- it normally contains html tags and php code
- php statements ends with ;
- it is not case sensitie , variables are case sensitive
- we user // , # , /*  */ for comments 
- it also has strict mode to enable it 
``` php
<?php declare (strict_types=1);

?>
```
### variables
-  $ sign is used , echo is used to display on screen
```php

<?php

 $text = "hello";
echo " i m $text ";
// or 
echo "i m " . $text . " hello" ;
?>
```
- variable scope = local , global , static
	- we cannot use global variables inside function , we need to use global keywrod 
	- usually when function is executed all functino variables are deleted , to reuse them we use static keyword while declaring them

### data types
- string - first character is 0 
- int 
- float
- bool
- array
- object 
- NULL 
- resource
- we need to declare class object using class keyword 
``` php

<?php

class car {
	function car( ){
		$this -> model="honde";
		     }
	}
// creating new object
$maruti = new car ( );
echo $maruti -> model;

?>
``` 

- string functions 
1. strlen( ) - used to get length of string  , strlen("string");
1. str_word_count( ) - used to count words in string , str_word_count("string") ;
1. strrev( ) - reverse the string
1. strpos( ) - search text within string  , strpos("hello world", "world");
1. str_replace ( "to replace ", "replace with" , "string" )

```php
$name = "Harry is a good boy";
echo $name;
echo "<br>";

echo "The length of " . "my string is " . strlen($name);
echo "<br>";
echo str_word_count($name);
echo "<br>";
echo strrev($name);
echo "<br>";
echo strpos($name, "Harry");
echo "<br>";
echo str_replace("Harry", "Rohan", $name);
echo "<br>";
echo str_repeat($name, 4);
echo "<br>";
echo "<pre>";
echo rtrim("    this is a good boy     ");
echo "<br>";
echo ltrim("    this is a good boy     ");
echo "</pre>";

```
- numbers  
1. Nan - not a number 
1. change variable type or type cast (type)$a
1.  to create constant we use define ( ) function
``` php
define (name , value , case-insensitive (false by default) );
```
 
- operators same as js 

- conditions
``` php 

<?php

if (condition) 
{
	code ;
}
else if (condition) 
{
	code ; 
}
else
{ 
	code ;
}

switch(n) 
{	
	case label 1 :
		code ;
		break;
	default :
		code;
}

?>
```
- loops
``` php

<?php

while(condition)
{
	code:
}

for ( $x=0 ; $x <= 10 ; $x++ )
{
	code ;
}

// foreach loop  = only used on array

foreach($array as $ value )
{
	code;
}

$color = array("red","green","blue");
foreach($color as $ value )
{
	echo "$ value <br>";
}

?>
```

### functions
- we use function keyword to declare functions
``` php 
<?php

function Name()
{
	code ;
	return statement ;
}
?>
```
- we can pass arguments also 
- we can also change return type
	- return (type)($a);   eg """ return(int)($a); """
### arrays 
- array() ;  - keyword is used , index start from x
- count() ; = length of array 
	- count($array);
- sort() 
- arrray_shift()
- array_slice()
- array_replace()
- array_search()
- array_pop()
- ksort() - sort according to key , asc
- rsort() - sort in des
- asort() - acc to value in asc

``` php 

// These are called indexed arrays:
$arr = array('this', 'that', 'what');
echo $arr[0];
echo $arr[1];
echo $arr[2]; 

// these are called associative arrays

$age = array("nitish" => "35" , "saini " => "25");
echo $age["peter"] ;

foreach( $age as $x => $x_value)
{
	echo $age ;
}


```

### superglobal variables
predefined variables in php , accessible throught file 

	- $GLOBALS
	- $_SERVER
	- $_REQUEST
	- $_POST
	- $_GET
	- $_FILES
	- $_ENV
	- $_COOKIE
	- $_SESSION

- $_GLOBAL - **$GLOBALS** is a PHP super global variable which is used to access global variables from anywhere in the PHP script (also from within functions or methods).
PHP stores all global variables in an array called $GLOBALS[index]. The index holds the name of the variable.

``` php 
<?php
$x = 75;
$y = 25;
 
function addition() {
  $GLOBALS['z'] = $GLOBALS['x'] + $GLOBALS['y'];
}
 
addition();
echo $z;
?>
```

- $_SERVER is a PHP super global variable which holds information about headers, paths, and script locations


	- $_SERVER['PHP_SELF'] 	Returns the filename of the currently executing script

	- $_SERVER['GATEWAY_INTERFACE']	Returns the version of the Common Gateway Interface (CGI) the server is using
	- $_SERVER['SERVER_ADDR']	Returns the IP address of the host server
	- $_SERVER['SERVER_NAME']	Returns the name of the host server 
	- $_SERVER['SERVER_SOFTWARE']	Returns the server identification string (such as Apache/2.2.24)
	- $_SERVER['SERVER_PROTOCOL']	Returns the name and revision of the information protocol (such as HTTP/1.1)
	- $_SERVER['REQUEST_METHOD']	Returns the request method used to access the page (such as POST)
	- $_SERVER['REQUEST_TIME']	Returns the timestamp of the start of the request (such as 1377687496)
	- $_SERVER['QUERY_STRING']	Returns the query string if the page is accessed via a query string
	- $_SERVER['HTTP_ACCEPT']	Returns the Accept header from the current request
	- $_SERVER['HTTP_ACCEPT_CHARSET']	Returns the Accept_Charset header from the current request (such as utf-8,ISO-8859-1)
	- $_SERVER['HTTP_HOST']	Returns the Host header from the current request
	- $_SERVER['HTTP_REFERER']	Returns the complete URL of the current page (not reliable because not all user-agents support it)
	- $_SERVER['HTTPS']	Is the script queried through a secure HTTP protocol
	- $_SERVER['REMOTE_ADDR']	Returns the IP address from where the user is viewing the current page
	- $_SERVER['REMOTE_HOST']	Returns the Host name from where the user is viewing the current page
	- $_SERVER['REMOTE_PORT']	Returns the port being used on the user's machine to communicate with the web server
	- $_SERVER['SCRIPT_FILENAME']	Returns the absolute pathname of the currently executing script
	- $_SERVER['SERVER_ADMIN']	Returns the value given to the SERVER_ADMIN directive in the web server configuration file (if your script runs on a virtual host, it will be the value defined for that virtual host) 
	- $_SERVER['SERVER_PORT']	Returns the port on the server machine being used by the web server for communication (such as 80)
	- $_SERVER['SERVER_SIGNATURE']	Returns the server version and virtual host name which are added to server-generated pages
	- $_SERVER['PATH_TRANSLATED']	Returns the file system based path to the current script
	- $_SERVER['SCRIPT_NAME']	Returns the path of the current script
	- $_SERVER['SCRIPT_URI']	Returns the URI of the current page

-  $_REQUEST is a PHP super global variable which is used to collect data after submitting an HTML form 

``` php 
<html>
<body>

<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
  Name: <input type="text" name="fname">
  <input type="submit">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  // collect value of input field
  $name = $_REQUEST['fname'];
  if (empty($name)) {
    echo "Name is empty";
  } else {
    echo $name;
  }
}
?>

</body>
</html>
```

- $_POST is a PHP super global variable which is used to collect form data after submitting an HTML form with method="post". $_POST is also widely used to pass variables

``` php

<html>
<body>

<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
  Name: <input type="text" name="fname">
  <input type="submit">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  // collect value of input field
  $name = $_POST['fname'];
  if (empty($name)) {
    echo "Name is empty";
  } else {
    echo $name;
  }
}
?>

</body>
</html>

```
- $_GET is a PHP super global variable which is used to collect form data after submitting an HTML form with method="get".

- $_GET can also collect data sent in the URL
- to prevent hacker we use htmlspecialchars() function which converts < , > in &lt and &gt , also we trim() and , stripsplasehs to remove spaces and / etc

### file handling
- readfile (file) - is used to read file and output its content in buffer
- fopen(file,mode) 
- fclose()
- fread (file , bytes to read )

``` php
fread($myfile , filesize("File"))
```
- fgets () - read single line
- feof() - end of file , used for looping till end of file
- fgetc() - get single character
- fwrite (file,text to replace ) - used to write 

- modes in file
	- r - read
	- w - write , data is overwritten
	- a - preserved and write (append)
	- x - create new file for write only , false if exist
	- r+ - read / write
	- w+  
	- a+ - read / write
	- x+ - read / write

### cookie
- A cookie is created with the setcookie() function
 ``` php
setcookie($cookie_name, value, expire, path, domain, secure, httponly);
 ```
- Only the name parameter is required. All other parameters are optional.

- to retrieve cookie
	- $_COOKIE($cookie_name)

``` php
<?php
$cookie_name = "user";
$cookie_value = "Alex Porter";
setcookie($cookie_name, $cookie_value, time() + (86400 * 30), "/");
?>
<html>
<body>

<?php
if(!isset($_COOKIE[$cookie_name])) {
  echo "Cookie named '" . $cookie_name . "' is not set!";
} else {
  echo "Cookie '" . $cookie_name . "' is set!<br>";
  echo "Value is: " . $_COOKIE[$cookie_name];
}
?>

</body>
</html>
```

### session
- A session is a way to store information (in variables) to be used across multiple pages.

- Unlike a cookie, the information is not stored on the users computer
- A session is started with the session_start() function.

- Session variables are set with the PHP global variable: $_SESSION

	- $_SESSOIN[key] = value ; // stores session info 

- remove all session variables
	- session_unset();

- destroy the session
	- session_destroy();

``` php
<?php
session_start();
?>
<!DOCTYPE html>
<html>
<body>

<?php
// to change a session variable, just overwrite it
$_SESSION["favcolor"] = "yellow";
print_r($_SESSION);
?>

</body>
</html>
```

- The filter_var() function both validate and sanitize data from external source like cookies
, forms ,inputs ,etc 

### php json
- The json_encode() function is used to encode a value to JSON format.
- The json_decode() function is used to decode a JSON object into a PHP object or an associative array

``` php
<?php

$cars = array("Volvo", "BMW", "Toyota");

echo json_encode($cars);

$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';

$obj = json_decode($jsonobj);

echo $obj->Peter;
echo $obj->Ben;
echo $obj->Joe;

$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';

$arr = json_decode($jsonobj, true);

echo $arr["Peter"];
echo $arr["Ben"];
echo $arr["Joe"];

$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';

$obj = json_decode($jsonobj);

foreach($obj as $key => $value) {
  echo $key . " => " . $value . "<br>";
}

?>
```


### oops
- -> is called object operator 

``` php
class name {
	//properties
		public $name;
		public $color;
	
	//methods
	function set_name($name){
		$this->name = $ $name;
		return $this->name;
	}
}

$apple = new fruit();
echo $apple->set_name("apple");


// constructor 

__construct() , this fn is called when object created

function __construct($name){
	$this->name = $name;
}

$apple = new fruit("apple");
```

### mysql db with php
- we first need to connect  , mysqli , i= improved

- connect 
``` php
// creating mysqli object 
$con= new mysqli($servername , usr ,pass)

// checking if connected 
if ($con -> connect_error){
	die("Conn fail" .$con->connect_error);
}

$con->close();
```

- now after we have checked connection we can create db

``` php
$sql = "CREATE DATABAES mydb";

if($con->query($sql)==true){
	echo "sucess";
}
// we can pass all commands like this 
// we use same procedure to create tables and all those things 

// to send multiple query

$con ->multiquery($sql)

// querying data

$sql = "select id ,fname FROM mydb ";
$result = $con->query($sql);
if ($result ->num_rows >0 ){
	while ($row = $result->fetch_assoc()){
		echo row[id]
	}
}

// close all connections


```
- num_rows() - check if more than zero rows returned

- fetch_assoc() - puts all resultys into an associative array that we can loop through 