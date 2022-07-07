accounts.socialLogin JS
``` js
gigya.accounts.socialLogin({"provider": "saml-MetadataCopy"});
```

accounts.showScreenSet JS customButtons Array of Objects
``` js
      gigya.accounts.showScreenSet({
        containerID:'login',
        screenSet: 'Default-RegistrationLogin',
          startScreen: 'gigya-login-screen',
          customButtons: [{
          'type': 'saml',
          'providerName': 'SAML SSO Account',
          'idpName': 'Name from SAML IDPs',
          'lastLoginIconURL': 'https://upload.wikimedia.org/wikipedia/commons/6/66/Simplot_Logo.png',
          'position': '1'}],
    });
```

[Add Custom Button from the WebSDK Configuration](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/417fa48b70b21014bbc5a10ce4041860.html?q=web%20sdk%20configuration#common-use-cases)

WEB SDK Methods
fidm.saml.cancelSSO JS
fidm.saml.continueSSO JS
fidm.saml.initSSO JS

## Beginner Code


Cal the screenset with custom buttons like the one below.
``` js
gigya.accounts.showScreenSet({
        'containerID':'login',
        'screenSet': 'IdP1-RegistrationLogin',
          'startScreen': 'Login-IdP1',
          'customButtons': [{
          'type': 'saml',
          'providerName’: externalIDP1',
          'idpName’: externalIDP1',
          'logoURL': 'https://upload.wikimedia.org/wikipedia/commons/6/66/Simplot_Logo.png',
          'lastLoginIconURL': 'https://upload.wikimedia.org/wikipedia/commons/6/66/Simplot_Logo.png',
          'position': '1'}],

})
```

These pages needs to be hosted in the external domain.
logout.html
``` html
<html>
<head>
  <title>SAML Logout Page</title>
<!-- gigya.js script should only be included once -->
<script type="text/javascript" src="https://cdns.gigya.com/js/gigya.js?apiKey=PASTEYOURAPIKEYHERE">
</script>
</head>
<body>
<script type="text/javascript">
   gigya.accounts.logout({callback:function(resp){
       if(resp.errorCode == 0){
         document.write("You are logged out");
       }else{
         document.write("failed to log out (were you already logged out?)");
       }
     }
   });
</script>
</body>
</html>
```


This page should include the SAP Customer Data Cloud SAML enabling script, located at https://cdns.gigya.com/js/gigya.saml.jsInformation published on non-SAP site. The script accepts your API key as a parameter, and takes care of creating the SAML assersions.
proxy.html
``` html
<script src="https://cdns.gigya.com/js/gigya.saml.js?apiKey=PASTEYOURAPIKEYHERE">
    {
    loginURL:"TBD",
    logoutURL:"TBD"
    }
</script>
```
error.html
``` html
<html>
<head>
<script type="text/javascript">
  function getParameterByName(name) {
  name = name.replace(/[\[]/, "\\[").replace(/[\]]/, "\\]");
  var regex = new RegExp("[\\?&]" + name + "=([^&#]*)"),
  results = regex.exec(location.search);
  return results === null ? "" : decodeURIComponent(results[1].replace(/\+/g, " "));
  }
var gig_err = JSON.parse(getParameterByName("error"));
document.write("<h1>Error Page</h1><p>There was an error: \""+gig_err.errorMessage+"\" in request ID "+gig_err.requestId);
</script>
error page
</html>

```
login.html
``` html
<html> 
<head>
  <title>SAML - Login</title>
<!-- gigya.js script should only be included once -->
<script type="text/javascript" src="https://cdns.gigya.com/js/gigya.js?apiKey=PASTEYOURAPIKEYHERE">
</script>
</head>
<body>
  <h1>SAML - IdP Login</h1>
<div id="container"></div>
<script type="text/javascript">
   gigya.accounts.showScreenSet({containerID:'container',screenSet:'Default-RegistrationLogin',startScreen:'gigya-login-screen'});
   gigya.accounts.addEventHandlers({onLogin:function(res){
       if(console && console.log){
         console.log("you logged in with UID: "+res.UID+" continuing to site");
         gigya.fidm.saml.continueSSO();
       }
     }
   });
</script>
</body>
</html>
```
From Global Community > 30_Project Assets > 6. Fast CDC > SAML