[SAP Docs - Site Setup](https://help.sap.com/docs/SAP_CUSTOMER_DATA_CLOUD/8b8d6fffe113457094a17701f63e3d6a/41720d7370b21014bbc5a10ce4041860.html?q=Provider%20configuration%20error#trusted-site-urls)
If your implementation includes social login on mobile devices, make sure that all the URLs that participate in the redirect social login flow are added to the list of Trusted Site URLs. For example:


Android:
`com.my.app://home_page` & `gigya://gsapi.com.my.app/login_result`

