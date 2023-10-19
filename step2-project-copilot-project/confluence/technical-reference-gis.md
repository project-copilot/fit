# Technical Reference: Google Identity Service JavaScript library
## Title: Technical Reference: Google Identity Service JavaScript library
### Initial content:

#### Setup
Source: 
[Setup  |  Authentication  |  Google for Developers ](https://developers.google.com/identity/gsi/web/guides/get-google-api-clientid)

Before you add Sign In With Google, One Tap, or Automatic sign-in to your website setup your OAuth configuration and optionally configure your site Content Security Policy.

**Note**: You must have a client ID to configure Sign In With Google and to [verify ID tokens](https://developers.google.com/identity/gsi/web/guides/verify-google-id-token) on your backend. A client ID looks like the following example: 1234567890-abc123def456.apps.googleusercontent.com

##### Get your Google API client ID
To enable Sign In With Google on your website, you first need to set up your Google API client ID. To do so, complete the following steps:
1. Open the **Credentials** page of the [Google APIs console](https://console.developers.google.com/apis).
2. Create or select a Google APIs project. If you already have a project for the Sign In With Google button or Google One Tap, use the existing project and the web client ID. When creating production applications, [multiple projects](https://developers.google.com/identity/protocols/oauth2/policies#separate-projects) may be necessary, repeat the remaining steps of this section for each project you manage.
3. Click **Create credentials > OAuth client ID** and for **Application type** select **Web application** to create a new client ID. To use an existing client ID select one of type Web application.
4. Add the URI of your website to **Authorized JavaScript origins**. The URI includes the scheme and fully qualified hostname only. For example, https://www.example.com.
**Key Point**: For local tests or development add both http://localhost and http://localhost:<port_number>
**Key Point**: Google One Tap can only be displayed in HTTPS domains.
5. Optionally, credentials may be returned using a redirect to an endpoint you host rather than through a JavaScript callback. If this is the case, add your redirect URIs to **Authorized redirect URIs**. Redirect URIs include the scheme, fully qualified hostname, and path and must comply with [Redirect URI validation rules](https://developers.google.com/identity/protocols/oauth2/web-server#uri-validation). For example, https://www.example.com/auth-receiver.
**Key Point**: When testing using http and localhost set the Referrer-Policy header in your web app to Referrer-Policy: no-referrer-when-downgrade.

##### Configure your OAuth Consent Screen
Both Sign In With Google and One Tap authentication include a consent screen which tells users the application requesting access to their data, what kind of data they are asked for and the terms that apply.
1. Open the [OAuth consent screen](https://console.developers.google.com/apis/credentials/consent) page of the APIs & Services section of the Google Developer Console.
2. If prompted, select the project you just created.
3. On the "OAuth consent screen" page, fill out the form and click the "Save" button.
    1. **Application name**: The name of the application asking for consent. The name should accurately reflect your application and be consistent with the application name users see elsewhere.
    2. **Application logo**: This image is shown on the consent screen to help users to recognize your app. The logo is shown on Sign In With Google consent screen and on [account settings](https://myaccount.google.com/permissions), but is not shown on One Tap dialog.
    3. **Support email**: Shown on the consent screen for user support and to G Suite administrators evaluating access to your application for their users. This email address is shown to users on the Sign In With Google consent screen when the user clicks the application name.
    4. **Scopes for Google APIs**: Scopes allow your application to access your user's private data. For the authentication, default scope (email, profile, openid) is sufficient, you don't need to add any sensitive scopes. It is generally a best practice to request scopes incrementally, at the time access is required, rather than up front. [Learn more](https://developers.google.com/identity/protocols/oauth2/scopes)
    5. **Authorized domains**: To protect you and your users, Google only allows applications that authenticate using OAuth to use Authorized Domains. Your applications' links must be hosted on Authorized Domains. [Learn more](https://support.google.com/cloud/answer/6158849#authorized-domains).
    6. **Application Homepage link**: Shown on Sign In With Google consent screen and One-Tap GDPR compliant disclaimer information under the "Continue as" button. Must be hosted on an Authorized Domain.
    7. **Application Privacy Policy link**: Shown on Sign In With Google consent screen and One-Tap GDPR compliant disclaimer information under the "Continue as" button. Must be hosted on an Authorized Domain.
    8. **Application Terms of Service link (Optional)**: Shown on Sign In With Google consent screen and One-Tap GDPR compliant disclaimer information under the "Continue as" button. Must be hosted on an Authorized Domain.

4. Check "Verification Status", if your application needs verification then click the "Submit For Verification" button to submit your application for verification. Refer to [OAuth verification requirements](https://support.google.com/cloud/answer/9110914) for details.

##### How To Use GIS
Source: 
[Migrate to Google Identity Services  |  Authorization  |  Google for Developers](https://developers.google.com/identity/oauth2/web/guides/migration-to-gis)

This example shows only the Google Identity Service JavaScript library using the token model and popup dialog for user consent. It is provided to illustrate the minimal number of steps required to configure a client, request and obtain an access token, and to call a Google API.

```html
<!DOCTYPE html>
<html>
  <head>
    <script src="https://accounts.google.com/gsi/client" onload="initClient()" async defer></script>
  </head>
  <body>
    <script>
      var client;
      var access_token;

      function initClient() {
        client = google.accounts.oauth2.initTokenClient({
          client_id: 'YOUR_CLIENT_ID',
          scope: 'https://www.googleapis.com/auth/calendar.readonly \
                  https://www.googleapis.com/auth/contacts.readonly',
          callback: (tokenResponse) => {
            access_token = tokenResponse.access_token;
          },
        });
      }
      function getToken() {
        client.requestAccessToken();
      }
      function revokeToken() {
        google.accounts.oauth2.revoke(access_token, () => {console.log('access token revoked')});
      }
      function loadCalendar() {
        var xhr = new XMLHttpRequest();
        xhr.open('GET', 'https://www.googleapis.com/calendar/v3/calendars/primary/events');
        xhr.setRequestHeader('Authorization', 'Bearer ' + access_token);
        xhr.send();
      }
    </script>
    <h1>Google Identity Services Authorization Token model</h1>
    <button onclick="getToken();">Get access token</button><br><br>
    <button onclick="loadCalendar();">Load Calendar</button><br><br>
    <button onclick="revokeToken();">Revoke token</button>
  </body>
</html>
```

### Actions in Project Copilot:
- Write custom instruction:
```xml
<instruction>...</instruction>
```
### Final content: