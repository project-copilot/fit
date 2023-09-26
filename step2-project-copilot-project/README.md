# CodeLab: Creating a Fitness App Using Project Copilot and GitHub Copilot
## Step 2: Improving Project Planning using Project Copilot
Revamping the epics and user stories for enhancement with the assistance of Project Copilot, in order to enhance project planning, improve code generation, and mitigate deviations and rework.
Below are the enhanced epics and their corresponding stories:

### Epic
#### ID: FIT-1
#### Title: Security and Authentication on Google Fit
#### Initial description:
Implement authentication and authorization using Google APIs. The goal is to enable users to access their Google Fit data in order to gain insights into their status and progress.
#### Actions in Project Copilot:
- Write custom instruction:
    - _Instruction: Improve this Epic that this a project to create a simple html and javascript client side app_
- Press "Complete" button
#### Final description:
Implement authentication and authorization using Google APIs to create a simple HTML and JavaScript client-side app. The goal is to enable users to access their Google Fit data in order to gain insights into their status and progress.

### Epic
#### ID: FIT-2
#### Title: Analyze and process Google Fit data
#### Initial Description:
Analyze Google Fit data to calculate calories consumed and progress in health status.
#### Actions in Project Copilot:
- Write custom instruction:
    - _Instruction: Clarify that calories consumed are based on number of steps only, and progress is calculated based on heart points_
- Press "Complete" button
#### Final Description:
Analyze Google Fit data to calculate calories consumed and progress in health status. This epic will involve processing the user's step count data to determine the number of calories burned. Additionally, it will utilize heart point data to track the user's progress in achieving their health goals.

### User story
#### ID: FIT-3
#### Epic ID: FIT-1
#### Title: Create a Google Project and enable Google Fitness API
#### Initial Description:
Set up a project in the Google Cloud Console, enable the Fitness API, and obtain an OAuth 2.0 client ID and API key.
#### Actions in Project Copilot:
- Press "Complete" button 2 times
- Write custom instruction:
    - _Instruction: Replace user with developer in the acceptance criteria_
- Press "Complete" button
#### Final Description:
User:

As a developer, I want to create a Google project and enable the Google Fitness API.

Action:

I will set up a project in the Google Cloud Console and enable the Fitness API. Additionally, I will obtain an OAuth 2.0 client ID and API key.

Outcome:

By completing these actions, I will have a Google project set up with the Fitness API enabled. I will also have the necessary credentials (client ID and API key) to access and use the Fitness API in my application.

Acceptance Criteria:

1. The developer should be able to create a Google project in the Google Cloud Console.

2. The developer should be able to enable the Google Fitness API in the created Google project.

3. The developer should be able to obtain an OAuth 2.0 client ID and API key after setting up the Google project and enabling the Fitness API.

4. The developer should have the necessary credentials (client ID and API key) to access and use the Fitness API in their application.

##### Technical reference:
Simple way to deploy the app in a local enviroment using python: python -m http.server
Tool for debug Chrome DevTools

### User story
#### ID: FIT-4
#### Epic ID: FIT-1
#### Title: Add the authentication to access the Google Fitness API
#### Initial Description:
Add and set up the JavaScript client to authenticate the user, enabling them to retrieve data from Google Fit's REST API.
#### Actions in Project Copilot:
- Press "Complete" button 2 times
- Write custom instructtion:
    - _Instruction: Add the requirement of validate the javascript client by retrieving today’s number of steps_
- Press "Complete" button
#### Final Description:
User:

As a developer integrating Google Fit into my application, I need to authenticate the user to access the Google Fitness API.

Action:

I want to add and set up the JavaScript client to authenticate the user, enabling them to retrieve data from Google Fit's REST API.

Outcome:

So the user will be able to securely access their fitness data from Google Fit and use it within my application, providing them with a seamless experience and allowing them to track their fitness progress effectively.

Acceptance Criteria:

1. The user should be able to navigate to the Google Developer Console and create a new project.

2. The user should be able to enable the Google Fitness API for the created project.

3. The user should be able to set up the JavaScript client library in their application.

4. The user should be able to authenticate the user using the JavaScript client library.

5. The user should be able to retrieve fitness data from the Google Fitness API using the authenticated user.

6. The user should be able to securely access their fitness data from Google Fit within the application.

7. The user should be able to track their fitness progress effectively using the retrieved data.

8. The user should be able to seamlessly use the fitness data within the application.

9. The user should be able to validate the javascript client by retrieving today’s number of steps.

Technical Reference:

Sample code to retrieve user steps:

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

_Note: In this user story, the Tech Reference is authored by the user after AI assistance generates the user story and acceptance criteria. Is it feasible to automatically generate the Technical Reference by employing the custom command 'Technical Reference:' in italics. This process works seamlessly when there is a similar user story with a matching Technical Reference or when a Technical Design Document from Confluence is linked to the user story._

### User story
#### ID: FIT-5
#### Epic ID: FIT-2
#### Title: Calculate today's calories burned based on the number of steps
#### Initial Description:
Retrieve today number of steps and calculate and display the calories burned in a day.
#### Actions in Project Copilot:
- Press "Complete" button 2 times
- Write a technical reference command:
    - '<technical-reference>'Write a proposal of how to implement the javascript function to calculate the calories based on the steps if there is a function getStepCount() that returns today’s number of user steps'</technical-reference>'
- Press "Complete" button
#### Final Description:
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

### User story
#### ID: FIT-6
#### Epic ID: FIT-2
#### Title: Calculate my health status score
#### Initial Description:
Calculate and display the health status score by comparing the heart points  and the daily calories burned with a healthy goal. Take into account that the average adult requires around 2,000 to 2,500 calories per day to maintain their weight, and based on World Health Organization (WHO) and American Heart Association (AHA) guidelines for cardiovascular health, for a healthy person 150 Heart Points per week is a good score, that is approximately 21 Heart Points per day.
#### Actions in Project Copilot:
- Press "Complete" button to rewrite the user story with the proper format.
- Add the following note:
    - Note: the average adult requires around 2,000 to 2,500 calories per day to maintain their weight, and based on World Health Organization (WHO) and American Heart Association (AHA) guidelines for cardiovascular health, for a healthy person 150 Heart Points per week is a good score, that is approximately 21 Heart Points per day.
- Press "Complete" button to generate the acceptance criteria.
- Write a technical reference command:
    - '<technical-reference>'Write a proposal of how to implement the javascript function  to calculate the health status score based on the steps if there are two functions getCaloriesBurned() that provides today's burned calories and getHeartPoints() that provides today's heart points considering 3 possible health status: Excellent, Good and Needs Improvement'</technical-reference>'
- Press "Complete" button
#### Final Description:
User:

As a health-conscious individual, I want to track my health status score to monitor my overall well-being.

Action:

I would like to calculate and display my health status score by comparing my heart points and daily calories burned with a healthy goal.

Outcome:

By having access to my health status score, I can easily assess my progress towards maintaining a healthy lifestyle. This will enable me to make informed decisions about my diet and exercise routine, ultimately improving my overall health and well-being.

Note: the average adult requires around 2,000 to 2,500 calories per day to maintain their weight, and based on World Health Organization (WHO) and American Heart Association (AHA) guidelines for cardiovascular health, for a healthy person 150 Heart Points per week is a good score, that is approximately 21 Heart Points per day.

Acceptance Criteria:

1. The user should be able to input their heart points and daily calories burned.

2. The system should compare the user's heart points and daily calories burned with the healthy goal (150 Heart Points per week and 21 Heart Points per day, and 2,000 to 2,500 calories per day).

3. The system should calculate the user's health status score based on the comparison.

4. The calculated health status score should be displayed to the user.

5. The user should be able to view their health status score at any time.

6. The user's health status score should be updated automatically when new heart points or daily calories burned are inputted.

7. The system should provide a clear indication of the user's progress towards maintaining a healthy lifestyle based on their health status score.

8. The user's health status score should be easily understandable and provide meaningful insights.

9. The system should consider the semantically related user stories to enhance the user's experience and provide additional features if applicable.

Technical Reference:

To calculate the health status score, we can implement a JavaScript function that takes the user's heart points and daily calories burned as input. Here's a proposal for the implementation:

```javascript

function calculateHealthStatusScore(heartPoints, caloriesBurned) {

  const healthyGoalHeartPointsPerDay = 21;

  const healthyGoalCaloriesPerDay = 2000;

  const heartPointsScore = heartPoints >= healthyGoalHeartPointsPerDay ? 2 : heartPoints >= healthyGoalHeartPointsPerDay / 2 ? 1 : 0;

  const caloriesScore = caloriesBurned <= healthyGoalCaloriesPerDay ? 2 : caloriesBurned <= healthyGoalCaloriesPerDay + 500 ? 1 : 0;

  const healthStatusScore = heartPointsScore + caloriesScore;

  if (healthStatusScore === 4) {

    return 'Excellent';

  } else if (healthStatusScore >= 2) {

    return 'Good';

  } else {

    return 'Needs Improvement';

  }

}

```

