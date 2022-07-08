If there is an issue that you faced which has taken at least 30+ minutes of your time, please include it here. Please make sure to go through the other troubleshooting pages before writing your issue. Eventually, your issue (and resolution) may be included in the other parts of the documentation to help others.


## Issue Title
**Date** - 1/1/1111
**Owner** - Aaron Feleke

### Issue

Type the issue here. Type any error codes, warnings, and any other useful materials.

### Resolution

Type the resolution here. Include small code snippets and images.

## SAML Error Page from IDP Initiated Login
**Date** - July 7, 2022
**Owner** - Aaron Feleke

### Issue

- Navigate to http://aaron.cxpoc.com/saml4steps/login.html
- Click a button that calls `gigya.fidm.saml.initSSO()`

```
Error Page
There was an error: "Invalid parameter value" in request ID undefined

{"errorCode":400006,
"errorMessage":"Invalid parameter value",
"callId":"d140a706ece34bc19579622073dfdf60",
"errorDetails":"Invalid argument: loginToken is missing",
"errorDescription":"Invalid argument: loginToken is missing"}
```

### Resolution

To call `gigya.fidm.saml.initSSO`, you need to have to have to have an CDC authenticated session. If you don't, you will get this error. Before calling `gigya.fidm.saml.initSSO` (or clicking a button that calls this), ensure that `gigya.showDebugUI()` shows a logged in user.

## IDP Initiated Login Does Everything but Log in
**Date** - July 7, 2022
**Owner** - Aaron Feleke

### Issue

- Navigate to http://aaron.cxpoc.com/saml4steps/login.html
- Login to a CDC Account
- Click a button that calls `gigya.fidm.saml.initSSO({"spName": "CDC2", "redirectURL":"https://aaron.cxpoc.com/saml4steps/login2.html"})`
- It successsfully goes through the SAML flow. But, when it goes the `redirectURL`, I am not logged in but see these query params.

`https://aaron.cxpoc.com/saml4steps/login2.html?errorCode=0&provider=saml-metadatacopy&UID=a01b973fd6a54fd48bb7765c0a4067e1&UIDSignature=TP83zUunECIxi8f9UpUnz7isHSU%3d&signatureTimestamp=1657250427&isSiteUser=true&isConnected=true&isTempUser=false&isLoggedIn=true&loginProvider=saml-MetadataCopy&loginProviderUID=HPMRAwlcA%2fI%3d&isSiteUID=false&nickname=Aaron+Feleke&firstName=Aaron&lastName=Feleke&email=fastcdc667%40yopmail.com&capabilities=Login&providers=saml-MetadataCopy&oldestDataUpdatedTimestamp=1657250426&oldestDataAge=1`

### Resolution

Still Investigating.

## SP Initiated Login Service Configuration Error
**Date** - July 7, 2022
**Owner** - Aaron Feleke

### Issue

- Navigate to http://aaronsp.cxpoc.com
- Open Login Screenset and choose the CAT Identity Provider or call `gigya.accounts.socialLogin({"provider": "saml-MetadataCopy"});`
- Login into IDP
- It redirects back to http://aaronsp.cxpoc.com with an issue on the screenset in red `Provider configuration error` and error code `400122` from `gigya.showdebugUI()` from the `accounts.socialLogin()` call
- What is interesting is on http://aaron.cxpoc.com/saml4steps/login2.html, which this is based off, works perfectly.


### Resolution

Still Investigating.

## Social Login - Invalid Site Domain
**Date** - July 1, 2022
**Owner** - Aaron Feleke

### Issue

- Navigate to http://omarnames.cxpoc.com
- On the screenset, use the Google Social Login
- The new popup says `Invalid site domain` and in `gigya.showDebugUI()` the `accounts.socialLogin` shows error code `400120` with the status message `General Service Error`

In CDC, Google is enabled on the parent and child site.

### Resolution

https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/4144cd9670b21014bbc5a10ce4041860.html?q=captcha
Enter your domains on which the relevant Screen-Sets are hosted.
In the list of domains, also enter a line with console.gigya.com, so that when previewing your registration screen in the UI Builder, Invisible reCAPTCHA will function correctly.

My guess: create out own CAPTCHA credentials with the correct domains.

## CAPTCHA not showing 
**Date** - July 1, 2022
**Owner** - Aaron Feleke

### Issue

- Navigate to http://omarnames.cxpoc.com
- Activate the Captcha RBA rule by entering the wrong password for the same login multiple times
- The following text in red shows up on the screenset `To login, confirm you are not a robot` but no captcha shows. I also recieve a warning in the Web Dev Tools `[warn] Missing captcha configuration` although it is there.

The CAPTCHA configuration is in both the parent and child site.

### Resolution

My guess: create our own Google credentials with the correct domains.