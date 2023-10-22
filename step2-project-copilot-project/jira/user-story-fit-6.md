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
<technical-reference>Describe how to implement 'calculateHealthStatusScore()', a javascript function for calculating the health status. Additionally, provide the pseudocode for the 'calculateHealthStatusScore()' function.</technical-reference>
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

Please note that the formula used in this function is based on WHO/AHA guidelines and provides a health assessment aligned with evidence-based calorie and exercise guidelines for a healthy adult.

References:

[Technical Reference: Fitness Formulas](link_to_confluence_page)

[Software Architecture Document](link_to_confluence_page)

[![User Story 4 - Step 1](http://img.youtube.com/vi/PgkGvSvGxbc/0.jpg)](https://www.youtube.com/watch?v=PgkGvSvGxbc "User Story 4 - Step 1")

[![User Story 4 - Step 2](http://img.youtube.com/vi/GjQUgxp_AR8/0.jpg)](https://www.youtube.com/watch?v=GjQUgxp_AR8 "User Story 4 - Step 2")