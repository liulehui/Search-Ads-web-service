## Content

### Information Retrieval (IR)

Finding material (usually documents) of an **unstructured nature (usually text)** that satisfies an **information need** from within **large collections** (usually stored on computers)

Examples:  

* web search
* email search
* search your labtop
* legal information retrieval

#### inverted index

* For each term t, we must store a list of all documents that contain t.
	+ Identify each doc by a **docID**, a document serial number
Antony -> 1, 2, 5, 6,7   
Brutus -> 1,3,7,9   
mercy -> 2, 5, 9, 14
* Can we used fixed-size arrays for this?   
	* need variable size posing lists
 
**Procedure:** 
 
* Tokenization  
Cut character sequence into word tokens
* Normalization  
Map text and query term to same form:   
e.g. lower case, U.S.A -> USA
* Stemming  
We may wish different forms of a root to match  
* Stop Words  
omit very common words: the, a, of, these   
* inverted index builder   

##### How to process a query with inverted index

* Consider processing the query: Antony AND Brutus 
	* Locate Antony in the Dictionary;
		* Retrieve its postings.
	* Locate Brutus in the Dictionary;
		* Retrieve its postings.
	* “Merge” the two postings (intersect the document sets):  

Antony -> 1, 2, 5, 6,7   
Brutus -> 1,3,7,9  
res -> 1,7  

##### How to process query “star wars” as a phrase
* The sentence “george s. patton is three star general during world war 2” is not a match.  
*  For this, it no longer suffices to store only <term : docs> entries
*  Positional index
*  In the postings, store, for each **term** the position(s) in which tokens of it appear:    
*term, number of docs containing term;
doc1: position1, position2 ... ; doc2: position1, position2 ... ; etc.*  

### IR in Ads
* Step1: build Inverted index for Ad  
	* Key: term in key words, Value: list(AdId)
* Step 2: build forward index for Ad detail information(ads description, bid price, num of key words .etc)
* Step 3: process query
* Step 4: rank Ads candidates

How to rank ads candidates  
● Relevance Score = measure how relevant query is to key words in ads  
● In our project : number of word match query / total number of words in key words  
● Example: Search “Nike running shoes”  

### Web Service  
#### HTTP  
The Hypertext Transfer Protocol (HTTP) is an application-level protocol for distributed, collaborative, hypermedia information systems. It is used to deliver data (HTML files, image files, query results, etc.) on the World Wide Web.  

* connectionless  
The HTTP client, i.e., a browser initiates an HTTP request and after a request is made, the client disconnects
from the server and waits for a response. The server processes the request and re-establishes the connection with the client to send a response back.
* media independent  
It means, any type of data can be sent by HTTP as long as both the client and the server know how to handle the data content.
* stateless  
HTTP is connectionless and it is a direct result of HTTP being a stateless protocol. The server and client are aware of each other only during a current request.


#### How web service handle http request  
1. Parse parameters
2. service (generate the response)  
3. error （service）  


### Map Reduce
#### Map
Divides the input into ranges and creates a map task to transfer each partition input: any string  
output: key, value  
#### Shuffle
distribute partitions to different machine by key  
#### Reduce
collects the various results and combines them to answer the larger problem that the master node needs to solve  
input : key, list(value)  

### Workflow
* index builder
* QU
* Ads Selector
* Ads Filter
* Campaign Manager