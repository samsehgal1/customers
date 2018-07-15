# customers
The system implements an API that allows CRUD operations on customers. RAML is used to implement the design spec of API. 
The API is designed to support the following consumer use cases at a minimum:
- A consumer may periodically (every 5 minutes) consume the API to enable it (the consumer) to maintain a copy of the provider API's customers (the API represents the system of record)
- A mobile application used by customer service representatives that uses the API to retrieve and update the customers details
- Simple extension of the API to support future resources such as orders and products.

Design approach -
1. CASE 1 - The message format is JSON. In memory store Caching has been done for the GET call to reduce the API calls so that consumer can cache the data and reduce the overhead. Thread profiles tuning has also been thought of once the correct volumetrics are available.
2. CASE 2 - Since format is JSON, it makes it easier to work with mobile applications as it is simple and portable to interpret. Methods like GET,PUT,DELETER are well defined and doesn't put much load thus consuming less bandwidth.
3. CASE 3 - Resource Types are used on all the CRUD operations of customers. So RAML is factorised and can be easily extended for orders and products scenario.
4. Basic security has been added by use of access tokens on write methods. This can be extended to OAuth Schemes.




