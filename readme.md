#Functionalities: 
	1. Given a url through POST method the application returns short and unique alias aka short link.
	2. User will be redirected to original url when he/she access the short url.
	3. The short url has an expiration time after which this will not work. It can be changes manually.

##Architecture : 
	1. Used in-memory h2 database for this demo purpose however NoSQL database can be used as we are anticipating with multiple rows 		   and no relations required between the objects.
		DB Design : 5 parameters
			a ->  id : int
			b ->  original_url : clob
			c ->  short_url : varchar
			d ->  created_at : timestamp
			e ->  expires_at : timestamp
	2. For generating a short url, used hashing algorithm called murmur_3 from Guava package.
	

###To run the Application : 
	1. run the SpringBoot application in local machine.
	2. goto "localhost:8080/h2-console"
	3. select saved settings and setting name : "Generic H2(Server)"
	4. jdbc url : "jdbc:h2:mem:3dbfc80a-76c4-4b2f-8596-c28fddc123a2"
	5. username : "sa"
	6. password : blank
	
	7. Now make POST request at "localhost:8080/generate" with payload as url:""
		it will return {
    				"originalUrl": "https://www.educative.io/courses/grokking-the-system-design-interview/m2ygV4E81AR",
    				"shortLink": "6c84c1f8",
    				"expirationDate": "2021-11-17T18:53:02.615606507"
    				}
    				
    	8. for accessing the original link through shortLink
    		use localhost:8080/shortLink
    		e.g. : localhost:8080/6c84c1f8.
