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
7. The calculated health status score should be based on accurate and reliable calculations.
8. The system should ensure that the user's heart points and daily calories burned are recorded accurately to calculate the health status score.

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