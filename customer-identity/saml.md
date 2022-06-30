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