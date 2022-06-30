[SAP Docs - Site Setup](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/41720d7370b21014bbc5a10ce4041860.html?q=Provider%20configuration%20error#trusted-site-urls)
If your implementation includes social login on mobile devices, make sure that all the URLs that participate in the redirect social login flow are added to the list of Trusted Site URLs. 


Swift: `gsapi://*`


For Objective-C, enter both `gsapi://*` and the bundle ID of your project (e.g., `com.app.app://*`).

## Custom Buttons

Custom Buttons work using the Swift SDK. But, they must be formated like this.

`["screenSet": "",  "startScreen": "", "deviceType": "", "containerID": "", "customButtons": [{"idpName": "", "providerName": "", "type": "saml", "position": "1"}]`



From [https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/416ee62770b21014bbc5a10ce4041860.html](SAP Docs - SAML Proxy Page), SAML is not supported natively in iOS but does work in WebView.