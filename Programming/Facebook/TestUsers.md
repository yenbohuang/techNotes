# Adding New Test User

* Test users are not real accounts and will not be locked by Facebook spam system.
* Follow instructions and add test account from App Dashboard (<https://developers.facebook.com/apps>):
  * Login App Dashboard and enter the test application.
    * Select "Roles -> Test User" at the left panel.
    * Click at "Add" button and set the following options:
      * "Authorize Test Users for This App?" -> Yes
      * "API Version to Install" -> Use default value.
      * "Login Permissions" -> Grant with "email".
        * Refer to <https://developers.facebook.com/docs/facebook-login/permissions/> if you need more.
      * "Select Test User language" -> Use default value.
    * Click "Edit -> Login as this test user" and make other changes in Facebook website.

# Getting Test User's Access Token

* After the test user is created, we can get the access tokens under the test application by Facebook Graph API 
  * <https://developers.facebook.com/docs/graph-api/reference/v2.8/app/accounts/test-users>
* App access token is available on Access Token Tool after login developer account.
  * <https://developers.facebook.com/tools/accesstoken/>

```
https://graph.facebook.com/v2.8/{App ID}/accounts/test-users?fields=access_token&access_token={App access token}
```

Refer to the following pages for more details:
* <https://developers.facebook.com/docs/apps/test-users>
