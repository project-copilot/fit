# User story
## ID: FIT-5
## Epic ID: FIT-2
## Title: Calculate today's calories burned based on the number of steps
## Initial Description:
Press a button and retrieve today number of steps and calculate and display the calories burned in a day.
## Linked documents:
[Software Architecture Document](/step2-project-copilot-project/confluence/software-architecture-document.md)
[Technical Reference: Google FIT Rest API](/step2-project-copilot-project/confluence/technical-reference-google-fit-rest-api.md)
[Technical Reference: Fitness Formulas](/step2-project-copilot-project/confluence/technical-reference-fitness-formulas.md)
## Actions in Project Copilot:
- Press "Complete" button 2 times
- Write a technical reference command:
```xml
<technical-reference>Write a proposal of how to implement the javascript function to calculate the calories based on the steps for an average person (steps * 0.05), if there is a function getStepCount() that returns today’s number of user steps. Add to the total calories the average BMR: 1,800 calories per day,  average NEAT: 450 calories per day , average TEF: 200 calories per day, and adaptive Thermogenesis 100 calories per day. Write the function getCalories()</technical-reference>
```
- Press "Complete" button
## Final Description:
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