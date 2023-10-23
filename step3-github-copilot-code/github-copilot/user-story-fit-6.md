# User story
## ID: FIT-6
## Epic ID: FIT-2

### Prompt for GitHub Copilot Chat

Complete the following code:
"""
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
"""
To implement the following user story:
"""
# Title: Calculate my health status score
# Description:
User:
As a health-conscious individual, I want to calculate my health status score.

Action:
I would like the system to calculate and display my health status score by comparing my heart points and daily calories burned with a healthy goal.

Outcome:
By providing a health status score, I will be able to assess and track my overall health and fitness level. This score will be determined by comparing my heart points and daily calories burned with a healthy goal, allowing me to understand how well I am meeting my health objectives. This feature will provide valuable insights and motivation for maintaining a healthy lifestyle.

Acceptance Criteria:
1. The system should calculate the user's health status score based on their heart points and daily calories burned.
2. The system should compare the user's heart points and daily calories burned with a healthy goal to determine their health status score.
3. The system should display the calculated health status score to the user.
4. The health status score should provide an assessment of the user's overall health and fitness level.
5. The health status score should serve as a tool for the user to track their progress and understand how well they are meeting their health objectives.
6. The system should provide valuable insights and motivation for the user to maintain a healthy lifestyle.

Technical Reference:

The 'calculateHealthStatusScore()' function can be implemented in JavaScript to calculate the health status score. The function can take the user's heart points and daily calories burned as input and use the following formula to calculate the health status score:

```javascript
function calculateHealthStatusScore(heartPoints, caloriesBurned) {
const healthScore = (caloriesBurned / 2250) + (heartPoints / 21);
if (healthScore < 1) {
return 'Needs Improvement';
} else if (healthScore >= 1 && healthScore <= 2) {
return 'Normal';
} else if (healthScore > 2) {
return 'Excellent';
}
}
```

This function calculates the health score by dividing the user's calories burned by 2250 and adding it to the user's heart points divided by 21. Based on the calculated health score, the function returns the corresponding health status: 'Needs Improvement' if the score is less than 1, 'Normal' if the score is between 1 and 2 (inclusive), and 'Excellent' if the score is greater than 2.
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

          const heartPoints = 50; // Replace with actual heart points value
          const healthScore = (totalCaloriesBurned / 2250) + (heartPoints / 21);
          let healthStatus;
          if (healthScore < 1) {
            healthStatus = 'Needs Improvement';
          } else if (healthScore >= 1 && healthScore <= 2) {
            healthStatus = 'Normal';
          } else if (healthScore > 2) {
            healthStatus = 'Excellent';
          }

          document.getElementById('calories').innerHTML = 'Calories Burned: ' + totalCaloriesBurned.toFixed(2);
          document.getElementById('health-status').innerHTML = 'Health Status: ' + healthStatus;
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
    <div id="health-status"></div>
  </body>
</html>
```

[![User Story 4 - Code generation](http://img.youtube.com/vi/_0wri_UyQb4/0.jpg)](https://www.youtube.com/watch?v=_0wri_UyQb4 "User Story 4 - Code generation")