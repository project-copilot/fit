# CodeLab: Creating a Fitness App Using Project Copilot and GitHub Copilot
## Step 3: Implement Project code using GitHub Copilot
Utilizing the enhanced user stories, create a code proposal with the assistance of GitHub Copilot. 
The following steps outline how to generate the code proposal for each corresponding story using a generic prompt for GitHub Chat:

### Prompt for GitHub Copilot Chat

Complete the following code:
"""

"""
To implement the following user story:
"""

"""

### To start to work using GitHub Copilot also define initial seed code in an index.html page

```html
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

    </script>
    <h1>Fitness App</h1>
    <button onclick="getToken();">Get access token</button> <br><br>
    <button onclick="getStepCount();">Get Step Count</button> <br><br>
    <button onclick="revokeToken();">Revoke token</button>
  </body>
</html>
```

### Steps:

#### Step 1: Implement User Story FIT-5
##### Prompt for GitHub Copilot Chat

Complete the following code:
"""
```html
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

    </script>
    <h1>Fitness App</h1>
    <button onclick="getToken();">Get access token</button> <br><br>
    <button onclick="getStepCount();">Get Step Count</button> <br><br>
    <button onclick="revokeToken();">Revoke token</button>
  </body>
</html>
```
"""
To implement the following user story:
"""
Title: Calculate today's calories burned based on the number of steps
Description:
User:

As a fitness enthusiast, I want to track my daily calorie burn based on the number of steps I take.

Action:

I want to retrieve the number of steps I have taken today and calculate and display the corresponding calories burned.

Outcome:

So I can have a clear understanding of my daily calorie burn and track my progress towards my fitness goals. This will help me make informed decisions about my diet and exercise routine.

Acceptance Criteria:

1. Given that I am a fitness enthusiast, when I retrieve the number of steps I have taken today, then I should be able to calculate the corresponding calories burned

2. Given that I am a fitness enthusiast, when I calculate the calories burned based on the number of steps, then the result should be accurate and reliable

3. Given that I am a fitness enthusiast, when I track my daily calorie burn, then I should be able to view the calculated calories burned for today

4. Given that I am a fitness enthusiast, when I track my daily calorie burn, then I should be able to track my progress towards my fitness goals

5. Given that I am a fitness enthusiast, when I track my daily calorie burn, then I should be able to make informed decisions about my diet and exercise routine

6. Given that I am a fitness enthusiast, when I track my daily calorie burn, then I should be able to have a clear understanding of my daily calorie burn

Technical Reference:

To implement the javascript function to calculate the calories based on the steps, you can use the following code snippet:

```javascript

function calculateCalories() {

  const steps = getStepCount(); // Assuming there is a function getStepCount() that returns today’s number of user steps

  const caloriesBurned = steps * 0.05; // Assuming 1 step burns 0.05 calories

  return caloriesBurned;

}

```

This function retrieves the number of steps using the `getStepCount()` function and calculates the corresponding calories burned by multiplying the steps with a factor of 0.05. You can adjust the factor based on your specific requirements.

Considering the semantically related user stories, this feature can be integrated into a fitness tracking app that allows users to compare energy plans, track their fitness goals, and make informed decisions about their diet and exercise routine.

"""

#### Step 2: Implement User Story FIT-6
##### Prompt for GitHub Copilot Chat
