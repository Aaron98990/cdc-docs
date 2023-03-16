> Make sure you are in proper site and partner. If you want to see the logs in the QA site, you must go to that API Key/Site. If you then want to see the logs for UAT site, you then must go to that API/Site. Going to the parent site does not allow you to see the child audit site logs!

The Audit Logs are accessed by clicking Administration (bottom left) > Audit Logs

With "Configuration Updates only" checked, only CDC Console activity will be shown - 

When you uncheck the "Configuration Updates only", you will be able to see activity by end users to their own account. This is a very useful feature to see if there any issues.

![The IP Address](/../assets/configuration-updates-only.png "Configuration Updates Only Checkbox in CDC Audit Log")

> 

Click on a log, to expand the log. Make sure to expand the "General Info" and "Request Parameters" areaas. Below, we can see the user is fastcdc001@yopmail.com, the Page URL of the attempted log in is https://aaron.cxpoc.com/, how the session expiration is set to 0, and the source was showScreenSet. **As you can imagine this tool is important for debugging and monitoring your application. **

![The IP Address](/../assets/expanded.png "The variables.")

After expanding a log, you can hover over any text in the expanded area and a little search icon appears. When you click that search icon, it will fill out the "Customer Where Clause" with the proper syntax automatically. This is an important feature to fine-tune your search. For example, you want to track the user journey with someone with a certain IP Address. Just by clicking the search icon, you can easily do this.

![The IP Address](/../assets/ip.png "The variables.")
![The IP Address](/../assets/search.png "The variables.")

Maybe you want to track down how a certain API is responding to your application. Easy peasy!
![The IP Address](/../assets/api.png "The variables.")


# For You
Now, try to track down the login you did from the screenset section. Can you find the logs for that?
