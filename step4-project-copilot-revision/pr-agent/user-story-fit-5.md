# User story
## ID: FIT-5
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
    </script>
  </head>
  <body onload="initClient()">
    <h1>Fitness App</h1>
    <button onclick="getToken();">Get access token</button> <br><br>
    <button onclick="getStepCount();">Get Step Count</button> <br><br>
    <button onclick="revokeToken();">Revoke token</button>
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

### PR-Agent Analysis

#### PR Analysis:
- **Main theme**: Implementing user story 3
- **PR summary**: This PR adds code to implement user story 3, which involves calculating and displaying the total calories burned in the Fitness App.
- **Type of PR**: Enhancement
- **Estimated effort to review [1-5]**: 2, because the changes are straightforward and the diff is small.
#### PR Feedback: 
- **General suggestions**: 
    - The code changes look good overall. It would be helpful to add some comments to explain the purpose of the new functions and variables.

![PR-Agent Analysis](/step4-project-copilot-revision/pr-agent/pr-analysis-user-story-3.png)


