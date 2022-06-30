
The screensets are loaded from SAP CDC's server using the Web SDK [accounts.showScreenSet JS](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/416f995970b21014bbc5a10ce4041860.html). In order to log the user out, we use. [accounts.logout JS](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/4137589670b21014bbc5a10ce4041860.html) In order to know a user is logged in, we use the `onLogin` global event [accounts.addEventHandlers JS](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/41313c7e70b21014bbc5a10ce4041860.html). Without the onLogin global event, the login screen would show even if a user is authenticated (e.g. during page refresh)

!> Please click and read through the SAP Documentation of the WebSDK calls above before moving on.

- Make sure to name the file that ends in .html like `index.html`
- The screensets will not work if you are tying to access the file like this `file://Documents/index.html`
- The `apiKey` in the sample will only work on http://localhost/
    - Download [Visual Studio Code](https://code.visualstudio.com/download) then download the Visual Studio Code Extension [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) by Ritwick Dey. After being downloading, click `Go Live` at the bottom-right of VS Code. A new page should populate on the browser like `http://127.0.0.1:5500/` and navigate to the file like `http://127.0.0.1:5500/index.html`. It may be necessary to change the host to `http://localhost:5500/index.html`, to get the screenset to work.
> http://localhost:5000/ and http://127.0.0.1:5000/ are both the same links and refered to as localhost. `5000` in this case would be the port number.
- Modify the value of the `apiKey` from `4_C1aub4QTBzakJtEjHSaMAA` to your own SAP Customer Data Cloud API Key. 
    - If you are doing this on a hosted site, make sure the site is in the Trusted URLs
    - This code sample uses the default `screenSet` and `startScreen` but you may need to change this. Generally, never create a screenset or change the startscreen names. Just use the default.
- If you are using https, be sure to further adjust the JS API url to: https://cdns.gigya.com/js/gigya.js?apikey=<Your_API_Key>.
- If you come across any errors, check out the Troubleshooting section.

!> Before copying the code, read the instructions above.

```
<html>
<head>
<script type="text/javascript" src="http://cdns.gigya.com/js/gigya.js?apiKey=4_C1aub4QTBzakJtEjHSaMAA">
</script>
</head>
<body>
<div id="login"></div>
<div id="logout" style="display:none">
  <a href="javascript:gigya.accounts.logout({callback:window.location.reload()})">logout</a>
</div>
<div id="profile"></div>


<script type="text/javascript">
  function loginHandler(res){
    console.log(`page JS handler: you logged in with UID:${res.UID}`);
    console.log(res);
    checkLogin(res);
  }
  function checkLogin(res){
    let login = document.getElementById("login");
    let logout = document.getElementById("logout");
    let signup = document.getElementById("signup");
    let profile = document.getElementById("profile");
    if(res.UID){
    gigya.accounts.showScreenSet({
      containerID:'profile',
      startScreen: 'gigya-update-profile-screen',
      screenSet:'Default-ProfileUpdate'
    });
      login.style.display="none";
      logout.style.display="block";
      profile.style.display="block";

    }
    else{
      gigya.accounts.showScreenSet({
        containerID:'login',
        screenSet:'Default-RegistrationLogin',
        startScreen: 'gigya-login-screen'
    });
  login.style.display="block";
      logout.style.display="none";
      profile.style.display="none";
    }
  }
  
  gigya.accounts.addEventHandlers({onLogin:loginHandler});
  gigya.accounts.getAccountInfo({callback:checkLogin})
</script>
</body>
</html>
```

This documentation is based off the [SAP Docs - Screen-set Hosted on SAP Customer Data Cloud Demo](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/416f995970b21014bbc5a10ce4041860.html)