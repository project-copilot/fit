# User story
## ID: FIT-6
## Epic ID: FIT-2

### Code before update
    
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

### Code after generate code using user story and GitHub Copilot

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

### PR-Agent Analysis without use User Story in the PR description

#### PR Analysis:
- **Main theme**: Implementing user story 4
- **PR summary**: Implementing code changes for user story 4 in the fitness app.
- **Type of PR**: Enhancement
- **Estimated effort to review [1-5]**: 2.
#### PR Feedback: 
- **General suggestions**: 
    - Consider adding comments to explain the purpose of the new code and any complex logic.
    - **It would be helpful to have a brief description of the user story in the PR description for better context.**

![PR-Agent Analysis](/step4-project-copilot-revision/pr-agent/pr-analysis-user-story-4-1.png)

### PR-Agent Analysis using User Story in the PR description

#### PR Analysis:
- **Main theme**: Implementing user story 4
- **PR summary**: This PR implements the code for calculating the health status score based on heart points and daily calories burned. It adds the necessary JavaScript code to calculate the score and display it on the HTML page.
- **Type of PR**: Enhancement
- **Estimated effort to review [1-5]**: 2, because the changes are straightforward and the code is well-documented.
#### PR Feedback: 
- **General suggestions**: 
    - The implementation looks good overall. However, it would be beneficial to add some input validation to ensure that the heart points and calories burned are valid numbers.

![PR-Agent Analysis](/step4-project-copilot-revision/pr-agent/pr-analysis-user-story-4-2.png)

_Note: The PR-Agent analysis is based on the [PR-Agent](https://github.com/Codium-ai/pr-agent) (License: **Apache License 2.0**) . We are working on our custom version, improving the promts and the analysis using our technology in order to achieve better results._


