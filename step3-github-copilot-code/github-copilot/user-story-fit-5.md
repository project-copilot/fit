# User story
## ID: FIT-5
## Epic ID: FIT-2

### Prompt for GitHub Copilot Chat

Complete the following code:
"""
<html>
  <head>
    <script src="https://apis.google.com/js/api.js"></script>
    <script>
      var client;
      var access_token;

      function initClient() {
        gapi.load('client:auth2', function() {
          gapi.client.init({
            //Replace with your CLIENT_ID
            clientId: '505215634987-bk8dd7cve8q34s3v8bc7f0cpga7tvl6i.apps.googleusercontent.com',
            scope: 'https://www.googleapis.com/auth/fitness.activity.read',
            discoveryDocs: ['https://www.googleapis.com/discovery/v1/apis/fitness/v1/rest']
          }).then(function () {
            client = gapi.auth2.getAuthInstance();
          });
        });
      }

      function getToken() {
        client.signIn().then(function() {
          access_token = client.currentUser.get().getAuthResponse().access_token;
        });
      }

      function revokeToken() {
        client.disconnect();
        console.log('access token revoked');
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
    </script>
  </head>
  <body onload="initClient()">
    <h1>Fitness App</h1>
    <button onclick="getToken();">Get access token</button> <br><br>
    <button onclick="getStepCount();">Get Step Count</button> <br><br>
    <button onclick="revokeToken();">Revoke token</button>
  </body>
</html>
"""
To implement the following user story:
"""
# Title: Calculate today's calories burned based on the number of steps
# Description:
User:
As a fitness enthusiast, I want to calculate today's calories burned based on the number of steps I have taken.

Action:
I would like to press a button to retrieve the number of steps I have taken today. Then, I expect the system to calculate and display the calories burned throughout the day.

Outcome:
By implementing this feature, I will be able to track and monitor my daily calorie expenditure based on the number of steps I have taken. This will provide me with valuable information to help me achieve my fitness goals and maintain a healthy lifestyle.

Acceptance Criteria:
1. The system should provide a button for the user to retrieve the number of steps they have taken today, allowing them to track their physical activity.
2. The system should calculate the calories burned throughout the day based on the number of steps retrieved, providing the user with an estimation of their calorie expenditure.
3. The system should display the calculated calories burned to the user, enabling them to monitor their daily calorie expenditure.
4. The system should accurately calculate the calories burned based on a reliable algorithm or formula, ensuring the accuracy of the provided information.
5. The system should consider the user's personal information, such as weight and height, if applicable, to provide a more accurate estimation of calories burned.
6. The system should update the calculated calories burned in real-time or at regular intervals, allowing the user to have up-to-date information on their calorie expenditure throughout the day.
7. The system should provide a clear and user-friendly interface for the user to view the calculated calories burned, ensuring ease of use and understanding.
8. The system should handle any errors or exceptions that may occur during the calculation process, providing appropriate error messages or fallback options to the user.
9. The system should ensure the privacy and security of the user's personal information, adhering to relevant data protection regulations and guidelines.
10. The system should provide an option for the user to reset or clear the calculated calories burned, allowing them to start tracking their calorie expenditure for a new day or session.

Technical Reference: 

Proposal for 'getCalories()' function:

```javascript
function getCalories(steps) {
const averageBMR = 1800;
const averageNEAT = 450;
const averageTEF = 200;
const adaptiveThermogenesis = 100;
const caloriesPerStep = 0.04;

const totalCaloriesBurned = averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis + (steps * caloriesPerStep);

return totalCaloriesBurned;
}
```
"""

Generated code:

```html
<html>
  <head>
    <script src="https://apis.google.com/js/api.js"></script>
    <script>
      var client;
      var access_token;

      function initClient() {
        gapi.load('client:auth2', function() {
          gapi.client.init({
            //Replace with your CLIENT_ID
            clientId: '505215634987-bk8dd7cve8q34s3v8bc7f0cpga7tvl6i.apps.googleusercontent.com',
            scope: 'https://www.googleapis.com/auth/fitness.activity.read',
            discoveryDocs: ['https://www.googleapis.com/discovery/v1/apis/fitness/v1/rest']
          }).then(function () {
            client = gapi.auth2.getAuthInstance();
          });
        });
      }

      function getToken() {
        client.signIn().then(function() {
          access_token = client.currentUser.get().getAuthResponse().access_token;
        });
      }

      function revokeToken() {
        client.disconnect();
        console.log('access token revoked');
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

      function getCalories() {
        getStepCount().then(function(steps) {
          const averageBMR = 1800;
          const averageNEAT = 450;
          const averageTEF = 200;
          const adaptiveThermogenesis = 100;
          const caloriesPerStep = 0.04;

          const totalCaloriesBurned = averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis + (steps * caloriesPerStep);

          document.getElementById('calories').innerHTML = 'Calories Burned: ' + totalCaloriesBurned.toFixed(2);
        }).catch(function(error) {
          console.error(error);
        });
      }
    </script>
  </head>
  <body onload="initClient()">
    <h1>Fitness App</h1>
    <button onclick="getToken();">Get access token</button> <br><br>
    <button onclick="getStepCount();">Get Step Count</button> <br><br>
    <button onclick="getCalories();">Get Calories Burned</button> <br><br>
    <button onclick="revokeToken();">Revoke token</button>
    <div id="calories"></div>
  </body>
</html>
```

[![User Story 3 - Code generation](http://img.youtube.com/vi/or6WfMxByqQ/0.jpg)](https://www.youtube.com/watch?v=or6WfMxByqQ "User Story 3 - Code generation")