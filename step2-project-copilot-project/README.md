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

![FIT-1](/step2-project-copilot-project/fit-1.png)

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

![FIT-2](/step2-project-copilot-project/fit-2.png)

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

![FIT-3](/step2-project-copilot-project/fit-3.png)

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

![FIT-4](/step2-project-copilot-project/fit-4.png)

### User story
#### ID: FIT-5
#### Epic ID: FIT-2
#### Title: Calculate today's calories burned based on the number of steps
#### Initial Description:
Press a button and retrieve today number of steps and calculate and display the calories burned in a day.
#### Actions in Project Copilot:
- Press "Complete" button 2 times
- Write a technical reference command:
```xml
<technical-reference>Write a proposal of how to implement the javascript function to calculate the calories based on the steps if there is a function getStepCount() that returns today’s number of user steps. Add to the total calories the average BMR: 1,800 calories per day,  average NEAT: 450 calories per day , average TEF: 200 calories per day, and adaptive Thermogenesis 100 calories per day. Write the function getCalories()</technical-reference>
```
- Press "Complete" button
#### Final Description:
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

To implement the JavaScript function to calculate the calories based on the steps, we can use the following approach:

```javascript

function getCalories() {

  const steps = getStepCount(); // Assuming there is a function getStepCount() that returns today's number of user steps

  const averageBMR = 1800; // Average Basal Metabolic Rate (BMR) in calories per day

  const averageNEAT = 450; // Average Non-Exercise Activity Thermogenesis (NEAT) in calories per day

  const averageTEF = 200; // Average Thermic Effect of Food (TEF) in calories per day

  const adaptiveThermogenesis = 100; // Adaptive Thermogenesis in calories per day

  const caloriesBurned = steps + averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis;

  return caloriesBurned;

}

```

This function calculates the total calories burned by adding the number of steps to the average BMR, NEAT, TEF, and adaptive thermogenesis. The average values used in this example are 1800 calories per day for BMR, 450 calories per day for NEAT, 200 calories per day for TEF, and 100 calories per day for adaptive thermogenesis.

By calling the `getCalories()` function, the system will retrieve the number of steps using the `getStepCount()` function and calculate the calories burned based on the predefined formula.

![FIT-5](/step2-project-copilot-project/fit-5.png)

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
```xml
<technical-reference>Write the javascript function that calculates the health status score based on compare calories consumed in a day and the heart points retrieving these values from these two functions getCaloriesBurned() that provides today's burned calories and getHeartPoints() that provides today's heart points, and return one of these 3 possible health status: Excellent, Good and Needs Improvement</technical-reference>
```
- Press "Complete" button
#### Final Description:
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

![FIT-6](/step2-project-copilot-project/fit-6.png)