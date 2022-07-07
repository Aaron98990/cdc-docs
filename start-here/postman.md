Postman is used for sending REST API requests in an easy and graphical matter. 

Dowload the latest version of [Postman](https://www.postman.com/downloads/).

## REST API Lesson

HTTP Methods
- POST: create new resources
- GET: read or retrieve a resourcee
- PUT: update resource
- DELETE: delete resouce
- and many more...

HTTP Response Status Codes
- 100's Informational 
- 200's Successful
    - 200 OK
- 300's Redirection 
    - 301 Moved Permanently
- 400's Client Error
    - 400 Bad Request
    - 401 Unauthorized
    - 404 Not Found
- 500's Server Error
    - 500 Internal Server Error

More often than not, we will focus on GIGYA's error Codes rather than the HTTP Response Codes. Here is the list of error codes [Refernce > Response Code and Errors](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/416d41b170b21014bbc5a10ce4041860.html) if messages are not clear.


### Other things to know
- Remember a post request does not use query parameters but uses the body!
- Path Variables (?id=5&name=sarah) vs Query Params (/:id/:name)
- These are Endpoints -> /id  /orders
- Request Authorization (Bearer Token, Basic Auth)
- Headers (Content-Type)
- Postman Variables {{baseUrl}} – Set in the Collection



### Simple Book API

[Simple Books API](https://github.com/vdespa/introduction-to-postman-course/blob/main/simple-books-api.md) is a must for first-timers. The associated YouTube [Video lesson](https://www.youtube.com/watch?v=VywxIQ2ZXw4) will get you up and running quick. If this is your first time using Postman, this will take three hours to complete.

## Using CDC's REST API
### Postman Bundle

Go the the Global Community > 20_Technical Guides > Technical Guides > Postman > CDC Requestsions.postman_collection.json > Download

(Almost) everything within CDC can be done via APIs. Then in postman, click import and choose the CDC Requestsions.postman_collection.json file. A collection will be added in Postman.

For post requets for CDC, for the body please use form-data or x-www-form-urlencoded. Raw does not work for some reason. Remember not to use Params for POST Requests.

### Authorization

Making API calls requires an API key and a Secret or userKey/secret pair which are obtained from the Gigya Dashboard. 
- The userKey/secret pair can be found by clicking Administration > Appication > Click an Application. Then copying and pasting the userKey and secret. Make sure the API Key is part of the application of the userKey and secret.
- The userKey/secret pair can be found by clicking your initials in the top-right of the CDC Console, going to account, the clicking API Credentials. Please copy the user key and secret key. Ignore the private key and DO NOT click generate.

Click the collection, probably named CDC B2C Requests. Then click variables. Please, input the variables from your console in here. Initial & Current Values should be the same. Make sure to save this!

![The variables](/../assets/variables.png "The variables.")

The great thing is not that all these fields are pre-populated. If you haver over a variable {{variableName}}, you can see the value.

![The variables](/../assets/variables2.png "The variables.")

> If you ever don't need a field for a request, like `isLite` above, uncheck. Do not delete it from the collection.

### Curl

Everything than can be done in Postman, can be done on Curl. Curl is a terminal utility to make API requests.

```
curl https://accounts.us1.gigya.com/accounts.search
--data-urlencode "apiKey=3_mKxxxxXXXXXXXXxxxxxxxxXXXXxxXxxxxxxxxxxxxxxxxxxXXXXXXXXXXXXxxxxx"
--data-urlencode "userKey=AJxXXxXxxX2X"
--data-urlencode "secret=X73xXXXXXxxxxXXXxxxXXXx656767Xxx"
--data-urlencode "format=json"
--data-urlencode "query=select UID, identities.provider, identities.providerUID from accounts limit 10"
```

### GIGYA API Tool

GIGYA has their own API tool to make requests like from Curl or the terminal. Check it out and try to make a request from here: [Gigya API Tool](https://tools.gigya-cs.com/api/).

### Creating a Full Account in CDC from Postman

> Make sure you complete all the steps from the Authorization section & Postman Bundle right above before doing this.



Create an account using postman Postman. Remember, this is the REST API not the WebSDK which uses Javascript. Please, read through the documentation below and try to complete the steps.
- [accounts.initRegistration](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/4136e1f370b21014bbc5a10ce4041860.html?q=accounts.initRegistration)
- [accounts.register](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/4136e1f370b21014bbc5a10ce4041860.html?q=accounts.initRegistration)
> Please scroll to the bottom of the response and always use the new regToken. If there is no new new regToken, you can continue using the old one.
- [accounts.finalizeRegistration](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/4136e1f370b21014bbc5a10ce4041860.html?q=accounts.initRegistration)

> This may be challenging but alreays refer to SAP's documentation. Whe you are done, there will be a Blue R in the Profiles Section for this user.

### Update the Profile

Now from Postman, set the first name and last name. 

This will use [accounts.setAccountInfo](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/4139777d70b21014bbc5a10ce4041860.html?q=web%20sdk%20configuration)

This will require you to be familiar with the [accounts object](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/41693e9270b21014bbc5a10ce4041860.html?q=web%20sdk%20configuration)

### CDC Console Profile Editing

In the Profiles section, find the user and click the edit button. Change the first name and last name to something else now.

