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

As a fitness enthusiast, I want to track the number of steps I take in a day and calculate the calories burned.

Action:

I want to press a button to retrieve the number of steps I have taken today and calculate the calories burned based on that number.

Outcome:

So I can see the total calories burned for the day, which will help me track my fitness progress and make informed decisions about my diet and exercise routine.

Acceptance Criteria:

1. Given that I am a fitness enthusiast, when I press the button to retrieve the number of steps I have taken today, then the system should display the total number of steps taken.

2. Given that I am a fitness enthusiast, when I press the button to calculate the calories burned, then the system should use the number of steps taken to calculate the calories burned.

3. Given that I am a fitness enthusiast, when the system calculates the calories burned, then it should use a predefined formula or algorithm to accurately calculate the calories burned based on the number of steps.

4. Given that I am a fitness enthusiast, when the system displays the total calories burned for the day, then it should show the calculated value in a clear and easily readable format.

5. Given that I am a fitness enthusiast, when I view the total calories burned for the day, then it should help me track my fitness progress and make informed decisions about my diet and exercise routine.

Technical Reference:

To implement the JavaScript function to calculate the calories based on the steps for an average person, we can use the following code:

```javascript

function getCalories() {

  const steps = getStepCount();

  const caloriesFromSteps = steps * 0.05;

  const averageBMR = 1800;

  const averageNEAT = 450;

  const averageTEF = 200;

  const adaptiveThermogenesis = 100;

  const totalCalories = caloriesFromSteps + averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis;

  return totalCalories;

}

```

This function uses the `getStepCount()` function to retrieve the number of steps taken today and calculates the calories burned based on that number. It then adds the average Basal Metabolic Rate (BMR), Non-Exercise Activity Thermogenesis (NEAT), Thermic Effect of Food (TEF), and Adaptive Thermogenesis to the total calories burned. The function returns the total calories.

This implementation assumes that the `getStepCount()` function is already implemented and returns today's number of user steps.
"""

##### Code generated by GitHub Copilot Chat

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

      function getCalories() {
        const steps = getStepCount();
        const caloriesFromSteps = steps * 0.05;
        const averageBMR = 1800;
        const averageNEAT = 450;
        const averageTEF = 200;
        const adaptiveThermogenesis = 100;
        const totalCalories = caloriesFromSteps + averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis;
        return totalCalories;
      }

    </script>
    <h1>Fitness App</h1>
    <button onclick="getToken();">Get access token</button> <br><br>
    <button onclick="getStepCount();">Get Step Count</button> <br><br>
    <button onclick="revokeToken();">Revoke token</button>
    <br><br>
    <button onclick="alert(`Total Calories Burned: ${getCalories()}`);">Calculate Calories Burned</button>
  </body>
</html>
```

#### Step 2: Implement User Story FIT-6
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

      function getCalories() {
        const steps = getStepCount();
        const caloriesFromSteps = steps * 0.05;
        const averageBMR = 1800;
        const averageNEAT = 450;
        const averageTEF = 200;
        const adaptiveThermogenesis = 100;
        const totalCalories = caloriesFromSteps + averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis;
        return totalCalories;
      }

    </script>
    <h1>Fitness App</h1>
    <button onclick="getToken();">Get access token</button> <br><br>
    <button onclick="getStepCount();">Get Step Count</button> <br><br>
    <button onclick="revokeToken();">Revoke token</button>
    <br><br>
    <button onclick="alert(`Total Calories Burned: ${getCalories()}`);">Calculate Calories Burned</button>
  </body>
</html>
```
"""
To implement the following user story:
"""
User:

As a health-conscious individual, I want to be able to calculate my health status score.

Action:

I want to press a button to calculate and display my health status score by comparing my heart points and daily calories burned with a healthy goal.

Outcome:

So I can easily track my progress and determine if I am meeting the recommended guidelines for cardiovascular health. This will help me make informed decisions about my lifestyle and improve my overall well-being.

Note: the average adult requires around 2,000 to 2,500 calories per day to maintain their weight, and based on World Health Organization (WHO) and American Heart Association (AHA) guidelines for cardiovascular health, for a healthy person 150 Heart Points per week is a good score, that is approximately 21 Heart Points per day.

Acceptance Criteria:

1. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should calculate my health status score.

2. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should display my health status score.

3. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should compare my heart points and daily calories burned with a healthy goal.

4. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should track my progress and determine if I am meeting the recommended guidelines for cardiovascular health.

5. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should help me make informed decisions about my lifestyle and improve my overall well-being.

6. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should calculate my health status score based on the average adult's daily calorie requirement of 2,000 to 2,500 calories.

7. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should calculate my health status score based on the recommended guidelines for cardiovascular health, which is 150 Heart Points per week.

8. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should calculate my health status score based on the average adult's daily calorie requirement and the recommended guidelines for cardiovascular health.

9. Given that I am a health-conscious individual, when I press the 'Calculate' button, then the system should display my health status score calculated based on the average adult's daily calorie requirement and the recommended guidelines for cardiovascular health.

Technical Reference:

To calculate the health status score, a JavaScript function can be implemented. The function can retrieve the calories burned in a day using the getCaloriesBurned() function and the heart points using the getHeartPoints() function. The function can then compare these values with the healthy goal of 21 Heart Points per day and the average adult's daily calorie requirement of 2,000 to 2,500 calories. Based on the comparison, the function can return one of the three possible health statuses: Excellent, Good, or Needs Improvement.

```javascript

function calculateHealthStatusScore() {

  const caloriesBurned = getCaloriesBurned();

  const heartPoints = getHeartPoints();

  const healthyGoal = 21;

  const calorieRequirementMin = 2000;

  const calorieRequirementMax = 2500;

  if (heartPoints >= healthyGoal && caloriesBurned >= calorieRequirementMin && caloriesBurned <= calorieRequirementMax) {

    return 'Excellent';

  } else if (heartPoints >= healthyGoal || (caloriesBurned >= calorieRequirementMin && caloriesBurned <= calorieRequirementMax)) {

    return 'Good';

  } else {

    return 'Needs Improvement';

  }

}

```
"""

##### Snippets of Code generated by GitHub Copilot Chat

```html

  <script>

    function getHeartPoints() {
      const heartPoints = 0; // Replace with actual heart points calculation
      return heartPoints;
    }

    function calculateHealthStatusScore() {
        const caloriesBurned = getCaloriesBurned();
        const heartPoints = getHeartPoints();
        const healthyGoal = 21;
        const calorieRequirementMin = 2000;
        const calorieRequirementMax = 2500;
        if (heartPoints >= healthyGoal && caloriesBurned >= calorieRequirementMin && caloriesBurned <= calorieRequirementMax) {
          return 'Excellent';
        } else if (heartPoints >= healthyGoal || (caloriesBurned >= calorieRequirementMin && caloriesBurned <= calorieRequirementMax)) {
          return 'Good';
        } else {
          return 'Needs Improvement';
        }
      }

    </script>

    <button onclick="alert(`Health Status Score: ${calculateHealthStatusScore()}`);">Calculate Health Status Score</button>
```

##### Additional prompt to complete Code generated by GitHub Copilot Chat

Write a proposal of getHeartPoints using getStepsPoints as reference:

##### Snippets of Code generated by GitHub Copilot Chat

```html

<script>
function getHeartPoints() {
  return new Promise((resolve, reject) => {
    var startTimeMillis = new Date().setHours(0, 0, 0, 0); // Start time for today
    var endTimeMillis = new Date().setHours(23, 59, 59, 999); // End time for today

    var requestBody = {
      aggregateBy: [
        {
          dataTypeName: 'com.google.heart_minutes',
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
          var heartPoints = response.bucket[0].dataset[0].point[0].value[0].intVal;
          console.log('Heart Points for Today:', heartPoints);
          resolve(heartPoints); // Resolve the promise with the heart points
        } else {
          reject(new Error('Failed to fetch heart points')); // Reject the promise on error
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
```

