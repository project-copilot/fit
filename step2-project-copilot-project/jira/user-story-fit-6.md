# User story
## ID: FIT-6
## Epic ID: FIT-2
## Title: Calculate my health status score
## Initial Description:
Calculate and display the health status score by comparing the heart points and the daily calories burned with a healthy goal.

## Actions in Project Copilot:
- Press "Complete" button to rewrite the user story with the proper format.
- Press "Complete" button to generate the acceptance criteria.
- Write a technical reference command:
```xml
<technical-reference>Write a JavaScript function that calculates a health status score by comparing the calories consumed in a day and the heart points. Retrieve these values from two functions: getCaloriesBurned(), which provides today's burned calories, and getHeartPoints(), which provides today's heart points. The function should return one of three possible health statuses: Excellent, Good, or Needs Improvement.</technical-reference>
```
- Press "Complete" button
## Final Description:
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