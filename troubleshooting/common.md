These are general and common issues. For more specific issues, there should be a troubleshooting section for the specific topic.

- Look at the SAP Documentation.
    - In the top-right corner of the console, click the question mark & read up. There is something you could have overlooked.
- Look at the browser Dev Tools
    - Check that GIGYA Web SDK was loaded
        - In the Console, Check that `gigya.apiKey` gives an API Key. GIGYA is loaded if it does. If not, the Web SDK was not loaded.
    -  Make sure to to log everything including errrors, warning, info, and verbose. Also, please check preserve log from the console settings.
    - Check the console for any errors in red or warnings in yellow
        Use [Refernce > Response Code and Errors](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/416d41b170b21014bbc5a10ce4041860.html) if messages are not clear.
    - Check the network tab and filter by XHR/Fetch and see if there are any error codes or messages.
    - In the console, type `gigya.showDebugUI()`. Please check `Auto Load` always pops up. Click the [...] at the bottom left of the black banner and look for any red errors and look into the response and look at the responses and [error codes]((https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/416d41b170b21014bbc5a10ce4041860.html)).
- Are the API Keys correct?
    - Is it a parent site or the child site.
    - Not confusing qa vs dev versions
- Add site to the Trusted Sites
    - Instead of acessing `http://127.0.0.1:3000`, use `http://localhost:3000`
    - If using Mobile SDK (iOS/Android), there  are special sites that need to be trusted for social login. Read more [here](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/41720d7370b21014bbc5a10ce4041860.html) and in the iOS/Android SDK sections.
    - After adding a site to a trusted list, click save. Refresh the page and double check.
- Compare the working version to the not working version (dev vs qa)?
    - Typos in configuration
- For Consent, Webhook, & RBA make sure that they are enabled or disabled as appropiate. For Site Settings & Schema & UI Builder make sure to click Save. Refresh the page and double check that changes were applied.
- If you are having a hard time registering using the screensets or an `Account Pening Registration` error or error code 206001, that means that a required field has not been filled out. Please, add that to the Registration Completion screen and map additional fields to the missing fields. Go in the console and go to your CDC site that uses the WebSDK. Open the console and paste this code below to see the required fields.
``` js
function showSchemaInfo(json) {
for (x in json.profileSchema.fields){ if (json["profileSchema"]["fields"][x]["required"] == true){ console.log("profile." + x) }}
for (x in json.dataSchema.fields){ if (json["dataSchema"]["fields"][x]["required"] == true){ console.log("data." + x) }}
for (x in json.preferencesSchema.fields){ if (json["preferencesSchema"]["fields"][x]["required"] == true){ console.log("preferences." + x) }}
for (x in json.subscriptionsSchema.fields){ if (json["subscriptionsSchema"]["fields"][x]["required"] == true){ console.log("subscriptions." + x) }}
}
gigya.accounts.getSchema({callback: showSchemaInfo});
```
The output will return the required fields that must be added to the Screen Completion screen. Also, double check that all fields are mapped correctly. It could have a label without being mapped in CDC.
- Try on a different browser (Chrome, Firefox, Safari, Edge etc)
- Clear out the cookies