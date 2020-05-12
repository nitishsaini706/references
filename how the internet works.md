### How internet works
- we place a query 

- query is sent to the ISP and it resolves the domain name into ip addrs
- a request is sent to IP via HTTP 
- request find fastest path possible to server with specified IP
- it requires hoping from server to server untill we arrive to the exact server
- the requested server figures out exactly what we are asking for
- server builds required content ,pulling data from database 
- server responds with a combination of html , css and js as http response and browser renders it 

### HTTP
it is client-server protocol for transfering data , it works with request and response header which contains data
- request header = client send request to the server
        
                GET             /HTTP/1.1
                HOST            bing.com
                useragent       mozilla------OS-----
                cookie          MUID-asdjfiqohe,SRCHD=alkjdfo
                Referer 
                AcceptEncoding  gzip,deflate
                Keepalive       300

        - host = identify website by hostname or ip

        - useragent = default values by browser (can be spoofed by end user)

        - cookie = stores temp values shared between the client and server for session management

        - Referer = would see when redirected from one url to another. 

        - accept encoding = defines the compression scheme supported by client gzip and deflate most common ones.

- response header = server back to client 

                HTTP/1.1        200 ok
                set cookie      adfjihowee
                server          microsoft IIS/8.5
                content length  53225
        
        - status code = it is 200 ,it tells successful operation back to client

                - 3xx series - indicate redirection
                - 4xx series - errror in client request
                - 5xx series - error on server side

        - set cookie  = random value used by server to identify the client and store temp data

        - server = useful indo about web server

        - content length = no. of bytes in body of response . used so that other party can know when the current requeset/response has finished.
### HTTP methods
- GET = it is used for getting request from the server and informing server to send contents on the webpage to client web browser, we can also pass some info in it via URL eg search a querry ,atmost 255 characters.(like username and password , send this info in  header)

- POST = we send data with request , we are saying to database to post our data ,used to retrieve data from server . this is send via body of request using html forms etc.

- HEAD = it is used to identify the type of server as server only respond to the HTTP header without sending any payload.

- TRACE = this method is used to identify any altercations to request by devices. some proxy servers edit the header thus they can be identified by trace method .(more advance cross site scripting attack use trace to steal user cookies)

- PUT and DELETE - used by developers to upload web pages to server

- OPTIONS - used to query the server for methods that is supports. identified by netcat command


        Request has body , header are the metadata of the body having status code .
                



### Ip header
fields in ip header
- version => it tells about the version of ip we are using ver4 or 6

- header length -> it tells how many words are in ip header 
- type of service -> it is also called tos field (type of service) it is also refered to as differentiated services field , it helps network elements make qulity of service decisions by prioritizing some messages and deprioritizing other
- total length => it tells the total length of the messages including ip header and subsequent data .
- identification - when packets are fragemented it tells if they are fragmented or not .
- flags -> 3 bits total , one is reserved and second indicates whether or not the message can be fragmented , also called df bit ,if set it means dont fragment the message .last bit is used to indicate whether there are addtional framents or not , if set , there are more fragments ,if unset or 0 it means last fragment
- fragment offset -> indicates where the data in packet aligns 
- time to live -> tells how long a message can live on network 
- porotocol - numeric value indicating what the next protocol is .
- checksum -> determine whether the header is intact.
- source address
- dest address

![img](https://github.com/nitishsaini706/references-images/blob/reference/ip-header.gif)
### tcp header

- source port -> port traffic originated from on the sending side.

- dest port 
- sequence num -> set from the sender side 
- ack num -> set from the receiver side
- data offset -> lets the system know where to look for the data
- reserverd -> future use
- control bits -> 6 flag bits ,used to indicate disposition of the message like syn, fin,psh,rst etc
- window -> how many bytes the sender is willing to accept 
- checksum -> to check for the errors
- urgent pointer -> it indicates the next byte value after the urgent data
- options -> these are variable length header fields

![img](https://github.com/nitishsaini706/references-images/blob/reference/tcpheader.jpg)

### cookies and session id 
- http is stateless client-server protocol , where client makes a request and server responds with data . The next request that comes is entirely new request , unrelated to previous request .

- the track of sessions is kept using cookies and session id . 
- session id is set by server , cookie is actual mechaism ussed which the session id is passed back and forth between client the unique ID by setting set-cookie field in response .
- when client receives it stores the session id within browser and associates it to the website url that sent it 
- when user revisits the original website , the browser will send cookie value accross identifying the user.

browser -------------GET---------> SERVER

Server----------------set cookie ,ID and language ------> browser

Browser -------GET (login ,ID , language)------> Server

### types of cookies 
- persistent - stored in hard drive as text files 
- non persistent - stored in memory of the browser valid for perdefined time which is appended to the cookie 
- chrome uses sqlite3 database to store cookie instead of text file 

### cookie parameters 
- Domain - domain to which cookie would be send 

- path - cookie would only be sent to pages inside domain/path
- httponly- prevent xss as javascript won"t be able to access the cookie
- secure - only send over ssl if enabled
- Expires - time specified , cookie stored 

## headers
it is instructions with the get method and some info send to the server 

![img](https://github.com/nitishsaini706/references-images/blob/reference/request_header.png)
![img](https://github.com/nitishsaini706/references-images/blob/reference/response-headers.jpg)

in response headers we see cache-control:private , max age=1670 , the browser has to implement the header , it's a client side control 

## hsts (https strict transport security )
- strict-trasnport-security :  max-age=54665  ;       include  Subdomain ; preload
    - this declars that a client should only interect with a site over https
    - protects against downgrade attacks
    - it relies on trust on first use (tofu)
    - it makes an internal request 
- max-age => declares the period for which insecure request cannot be made , the units are in seconds, the duration reset on every receipt of the response header 
- include subdomanis -> the scope of hsts can be extended to all subdomains 
- preload keyword -> trust on first use is not foolproof that is to make secure connection we need to make connection with http , making it vulnerable to mitm , thus by preloading the website in browser prevents this tofu 

## https public key pinning (hpkp)
 public key pin header , it is used to black list the forged trusted certs ,header
    
         public-key-pins;pin sha1=[pin1] ;pin sha2356=[pin2];max-age=5544;report-uri=[uri];includeSubdomains
this is header pin stores the thumbprint of the original certificate and is used to verify , max-age tell the age of the certificate , report-uri - directs the browser to report thr ke violations via the specified uri 

## content securirty policy 
it protects from xss attack ,
- attacker embed external resources in the page 
- writing script to the page source 
- modifying the document object model (dom)

it helps in declaring content sources 
- it is done by using keyword 
    -  /" *  all
    - none - from no one
    - self - from same site 

          content-security-policy:
          defalut-src 'self' ; script-src 'self' some websites ; style-src 'self' website ; img-src 'self' websites ; font-src 'self' website ; object-src 'none' ; media-src 'none' ; child-src 'self'; connect-src 'self' ; unsafe-eval unsafe-inline

- default-src 'self' = this website is allowed to load content from this website only 
- script-src - from where scripts are allowed to be laoded , self tells that if from no where use from this website 
- style-src - from where style sheet is allowed 
- img-src - from where images is loaded
- font-src - from where font is allowed 
- object-src - flashing or animation in the website
- media - means music 
- child-src - load content from the iframe 
- connect-src - xml , https sockets or request 
- unsafe-inline - it tells to allow inline scripts which are safe as xss attack is done using inline srcipts but still vuln to inline xss , we also paste the hash calculated to only allow the trusted hash only or using nonce that is number used once 
- unsafe-eval - allows eval keyword in the javascript , but this can be exploited by xss as attacker send string eval to perform xss attack 

## frame-ancestors 
- its embedidng the malicious script using the iframe tag . it protect website using this tag
- frame-ancestors 'self' 

### tools 
- using security header.io
- using fiddler csp extension 


### https fundamentals
- certificate authority 
- ssl/tls - now we use tls 1.3 version of tls

![img](https://github.com/nitishsaini706/references/blob/reference/headers.png)
![img](https://github.com/nitishsaini706/references-images/blob/reference/https%20key%201.png)
![img](https://github.com/nitishsaini706/references-images/blob/reference/https%20key%202.png)
![img](https://github.com/nitishsaini706/references-images/blob/reference/https%20keys3.png)


### tls handshake 
- it is done after tcp 3 way handshake , it consist of client hello in which client tells the version of client tls version and cypher suite containing utc ,url ,etc and then server send sever hello with cypher suite and the public key and then certificates containing the public key server encrypted key and server hello done , this is negotiation phase which is not secured and then client share private or encrpyted key in response to server public key and with change cipher spec with client finish , and then server sends server finished with change cypher spec and then connection is secure

### using opnessl to get local certificate 
- many videos on youtube 

- badssl.com is website that tells how https request works , and what if you enter invalid certificate and all those things can happen when we went to these insecure websites .

### hsts http strict transport security 
- it redirects a website internaly , which means if we type http the website will automatically redirect to https website .it uses strict security or hsts header  having max age and to prevent sending the first http request we add preload header which will make this website https and this website cannot be realoded in http in the first place 
, in chromium website we can see the websites already preloaded 

### websites having mix content
- in this page is loaded in https but having some content which is requested in http or insecure connection and someone can change the insecure content

### using lets encrypt website 
- this website creates free certificates    
- using cloudflare for free 

### public pinnning 
- hpkp - http public key pinning -> this defines the public key that are allowed ,it specifies the max age ,whether it applies to subdomains . it is in the response header having public key pins , it means it is having some valid pins and browser checks for these pin , if website is having pin which is already known will be allowed , else the website is blacklisted and discarded 

### https blind spots
- having some links or images neither in hsts or https thus making them blind spots 

### cracking https - fun time 
- how it's done
    - key exchange 
    - data encryption 
    - handshake integrity encryption

- data encyption protocols
    - 3 DES 168 bit -  doing encryption 3 times 
    - AES (128 or 256 bits)
    - new encryption chacha 20 

- aes requires the secret key to encrpyt and decrypt data and thus need this key but was insecure to tansfer the key in secure way , thus using key encrpytion protocol to securely exchange key 
    - key exchange protocls 
        - RSA
        - diffie-hellman(DH) - it is signed with RSA 
        - ECDH - elliptical curve DH 
    

### inital connection 
when client makes request , then server send the certificate and send the prime numbers with this certificate and then client chooses one number ,and then client makes a private key and then take that prime number and then taking power of that private key and then dividing it with the other prime number and taking the mod of that number which is the encrypted key , and we send this number to the server and then server also make same process , it pics any number and do same thing and send the encrypted key to the client , anyone of the network can only see the encrypted key and the prime number but cannot see the prime numbers , but we can do the maths to get that private key to encrypt the session .
img 

