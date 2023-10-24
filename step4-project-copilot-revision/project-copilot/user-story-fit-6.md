# User story
## ID: FIT-6
## Epic ID: FIT-2
## Title: Calculate my health status score
## Initial Description:
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

## Actions in Project Copilot:
- Write a review command:
```xml
<review>This PR implements the code for calculating the health status score based on heart points and daily calories burned. It adds the necessary JavaScript code to calculate the score and display it on the HTML page</review>
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

Semantic Review:

- The pull request implements the calculation of the health status score as per the user story's requirements.

- The added JavaScript function, calculateHealthStatusScore(), correctly calculates the health status score based on the user's heart points and daily calories burned.

- The function uses the provided formula to determine the health status score and returns the corresponding assessment: 'Needs Improvement', 'Normal', or 'Excellent'.

- The calculated health status score is displayed on the HTML page, fulfilling the acceptance criteria for displaying the score to the user.

- The code implementation aligns with the user story and technical reference, providing an accurate assessment of the user's overall health and fitness level.

- No inconsistencies or missing functionalities were observed in the code.

- The provided technical reference and references to fitness formulas and software architecture documents demonstrate a well-documented and informed approach to the implementation.

- The code satisfies all the acceptance criteria and provides valuable insights and motivation for the user to maintain a healthy lifestyle.

- The semantic review confirms that the code effectively delivers on the user story requirements without any inconsistencies or omissions.

[![User Story 4 - Semantic Review](http://img.youtube.com/vi/LAIR2htnx6A/0.jpg)](https://www.youtube.com/watch?v=LAIR2htnx6A "User Story 4 - Semantic Review")