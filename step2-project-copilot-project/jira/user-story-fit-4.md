# User story
## ID: FIT-4
## Epic ID: FIT-1
## Title: Add the authentication to access the Google Fitness API
## Initial Description:
Add and set up the JavaScript client to authenticate the user, enabling them to retrieve data from Google Fit's REST API.
## Linked documents:
[Software Architecture Document](/step2-project-copilot-project/confluence/software-architecture-document.md)
[Technical Reference: Google Identity Service JavaScript library](/step2-project-copilot-project/confluence/technical-reference-gis.md)
## Actions in Project Copilot:
- Press "Complete" button and check status until processing is done 2 times
- Add the following text to the user story description:

Technical Reference:

Sample code to retrieve an access token and use it to retrieve the user steps:

```javascript
      var client;
      var access_token;

      function initClient() {
        client = google.accounts.oauth2.initTokenClient({
          //Replace with your CLIENT_ID
          client_id: '505215634987-bk8dd7cve8q34s3v8bc7f0cpga7tvl6i.apps.googleusercontent.com',
          scope: 'https://www.googleapis.com/auth/fitness.activity.read',
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

      function getStepCount() {
        return new Promise((resolve, reject) => {
          var startTimeMillis = new Date().setHours(0, 0, 0, 0); // Start time for today
          var endTimeMillis = new Date().setHours(23, 59, 59, 999); // End time for today

          var requestBody = {
            aggregateBy: [
              {
                dataTypeName: 'com.google.step_count.delta',
              },
            ],
            bucketByTime: { durationMillis: 86400000 }, // 1 day in milliseconds
            startTimeMillis: startTimeMillis,
            endTimeMillis: endTimeMillis,
          };

          var xhr = new XMLHttpRequest();
          xhr.onreadystatechange = function () {
            if (this.readyState == 4) {
              if (this.status == 200) {
                var response = JSON.parse(this.responseText);
                var stepCount = response.bucket[0].dataset[0].point[0].value[0].intVal;
                console.log('Step Count for Today:', stepCount);
                resolve(stepCount); // Resolve the promise with the step count
              } else {
                reject(new Error('Failed to fetch step count')); // Reject the promise on error
              }
            }
          };
          xhr.open('POST', 'https://www.googleapis.com/fitness/v1/users/me/dataset:aggregate');
          xhr.setRequestHeader('Authorization', 'Bearer ' + access_token);
          xhr.setRequestHeader('Content-Type', 'application/json');
          xhr.send(JSON.stringify(requestBody));
        });
      }
```

## Final Description:
User:
As a developer, I need to add authentication to access the Google Fitness API.

Action:
I will add and set up the JavaScript client to authenticate the user, allowing them to retrieve data from Google Fit's REST API.

Outcome:
By implementing authentication, users will be able to securely access and retrieve data from the Google Fitness API. This will ensure that only authorized individuals can interact with the API, protecting user data and maintaining privacy. This enhancement will enable developers to build applications that leverage Google Fit's data, providing users with personalized and meaningful fitness insights.
Acceptance Criteria:
1. The system should implement authentication to access the Google Fitness API, ensuring that only authorized individuals can interact with the API.
2. The system should provide a JavaScript client that allows users to authenticate and retrieve data from the Google Fit's REST API.
3. The authentication process should securely authenticate the user, protecting user data and maintaining privacy.
4. The system should enable developers to set up the JavaScript client to authenticate the user and retrieve data from the Google Fitness API.
5. The authentication implementation should follow best practices and adhere to the security guidelines provided by Google.
6. The system should provide clear and concise documentation on how to set up and use the authentication mechanism for accessing the Google Fitness API.
7. The authentication process should seamlessly integrate with the existing application or system, ensuring a smooth user experience.
8. The system should handle authentication errors gracefully and provide meaningful error messages to the user in case of authentication failures.
9. The authentication mechanism should be scalable and able to handle a large number of concurrent users accessing the Google Fitness API.
10. The system should regularly update and maintain the authentication mechanism to address any security vulnerabilities or changes in the Google Fitness API's authentication requirements.

Technical Reference:

Sample code to retrieve an access token and use it to retrieve the user steps:

```javascript
      var client;
      var access_token;

      function initClient() {
        client = google.accounts.oauth2.initTokenClient({
          //Replace with your CLIENT_ID
          client_id: '505215634987-bk8dd7cve8q34s3v8bc7f0cpga7tvl6i.apps.googleusercontent.com',
          scope: 'https://www.googleapis.com/auth/fitness.activity.read',
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

      function getStepCount() {
        return new Promise((resolve, reject) => {
          var startTimeMillis = new Date().setHours(0, 0, 0, 0); // Start time for today
          var endTimeMillis = new Date().setHours(23, 59, 59, 999); // End time for today

          var requestBody = {
            aggregateBy: [
              {
                dataTypeName: 'com.google.step_count.delta',
              },
            ],
            bucketByTime: { durationMillis: 86400000 }, // 1 day in milliseconds
            startTimeMillis: startTimeMillis,
            endTimeMillis: endTimeMillis,
          };

          var xhr = new XMLHttpRequest();
          xhr.onreadystatechange = function () {
            if (this.readyState == 4) {
              if (this.status == 200) {
                var response = JSON.parse(this.responseText);
                var stepCount = response.bucket[0].dataset[0].point[0].value[0].intVal;
                console.log('Step Count for Today:', stepCount);
                resolve(stepCount); // Resolve the promise with the step count
              } else {
                reject(new Error('Failed to fetch step count')); // Reject the promise on error
              }
            }
          };
          xhr.open('POST', 'https://www.googleapis.com/fitness/v1/users/me/dataset:aggregate');
          xhr.setRequestHeader('Authorization', 'Bearer ' + access_token);
          xhr.setRequestHeader('Content-Type', 'application/json');
          xhr.send(JSON.stringify(requestBody));
        });
      }
```

_Note: In this user story, the Tech Reference is authored by the user after AI assistance generates the user story and acceptance criteria. Is it feasible to automatically generate the Technical Reference by employing the custom command 'Technical Reference:' in italics. This process works seamlessly when there is a similar user story with a matching Technical Reference or when a Technical Design Document from Confluence is linked to the user story._

[![User Story 2](http://img.youtube.com/vi/E1YMcOzmRZY/0.jpg)](https://www.youtube.com/watch?v=E1YMcOzmRZY "User Story 2")