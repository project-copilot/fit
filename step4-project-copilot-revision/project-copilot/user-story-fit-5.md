# User story
## ID: FIT-5
## Epic ID: FIT-2
## Title: Calculate today's calories burned based on the number of steps
## Initial Description:
User:
As a fitness enthusiast, I want to calculate today's calories burned based on the number of steps I have taken.

Action:
I would like to press a button to retrieve the number of steps I have taken today. Then, I expect the system to calculate and display the calories burned throughout the day.

Outcome:
By implementing this feature, I will be able to track and monitor my daily calorie expenditure based on the number of steps I have taken. This will provide me with valuable information to help me achieve my fitness goals and maintain a healthy lifestyle.

Acceptance Criteria:
1. The system should provide a button for the user to retrieve the number of steps they have taken today, allowing them to track their physical activity.
2. The system should calculate the calories burned throughout the day based on the number of steps retrieved, providing the user with an estimation of their calorie expenditure.
3. The system should display the calculated calories burned to the user, enabling them to monitor their daily calorie expenditure.
4. The system should accurately calculate the calories burned based on a reliable algorithm or formula, ensuring the accuracy of the provided information.
5. The system should consider the user's personal information, such as weight and height, if applicable, to provide a more accurate estimation of calories burned.
6. The system should update the calculated calories burned in real-time or at regular intervals, allowing the user to have up-to-date information on their calorie expenditure throughout the day.
7. The system should provide a clear and user-friendly interface for the user to view the calculated calories burned, ensuring ease of use and understanding.
8. The system should handle any errors or exceptions that may occur during the calculation process, providing appropriate error messages or fallback options to the user.
9. The system should ensure the privacy and security of the user's personal information, adhering to relevant data protection regulations and guidelines.
10. The system should provide an option for the user to reset or clear the calculated calories burned, allowing them to start tracking their calorie expenditure for a new day or session.

Technical Reference: 

Proposal for 'getCalories()' function:

```javascript
function getCalories(steps) {
const averageBMR = 1800;
const averageNEAT = 450;
const averageTEF = 200;
const adaptiveThermogenesis = 100;
const caloriesPerStep = 0.04;

const totalCaloriesBurned = averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis + (steps * caloriesPerStep);

return totalCaloriesBurned;
}
```

## Linked documents:
[Software Architecture Document](/step2-project-copilot-project/confluence/software-architecture-document.md)
[Technical Reference: Google FIT Rest API](/step2-project-copilot-project/confluence/technical-reference-google-fit-rest-api.md)
[Technical Reference: Fitness Formulas](/step2-project-copilot-project/confluence/technical-reference-fitness-formulas.md)

## Actions in Project Copilot:
- Write a review command:
```xml
<review>This PR adds code to implement user story 3, which involves calculating and displaying the total calories burned in the Fitness App</review>
```
- Press "Complete" button
## Final Description:
User:
As a fitness enthusiast, I want to calculate today's calories burned based on the number of steps I have taken.

Action:
I would like to press a button to retrieve the number of steps I have taken today. Then, I expect the system to calculate and display the calories burned throughout the day.

Outcome:
By implementing this feature, I will be able to track and monitor my daily calorie expenditure based on the number of steps I have taken. This will provide me with valuable information to help me achieve my fitness goals and maintain a healthy lifestyle.

Acceptance Criteria:
1. The system should provide a button for the user to retrieve the number of steps they have taken today, allowing them to track their physical activity.
2. The system should calculate the calories burned throughout the day based on the number of steps retrieved, providing the user with an estimation of their calorie expenditure.
3. The system should display the calculated calories burned to the user, enabling them to monitor their daily calorie expenditure.
4. The system should accurately calculate the calories burned based on a reliable algorithm or formula, ensuring the accuracy of the provided information.
5. The system should consider the user's personal information, such as weight and height, if applicable, to provide a more accurate estimation of calories burned.
6. The system should update the calculated calories burned in real-time or at regular intervals, allowing the user to have up-to-date information on their calorie expenditure throughout the day.
7. The system should provide a clear and user-friendly interface for the user to view the calculated calories burned, ensuring ease of use and understanding.
8. The system should handle any errors or exceptions that may occur during the calculation process, providing appropriate error messages or fallback options to the user.
9. The system should ensure the privacy and security of the user's personal information, adhering to relevant data protection regulations and guidelines.
10. The system should provide an option for the user to reset or clear the calculated calories burned, allowing them to start tracking their calorie expenditure for a new day or session.

Technical Reference: 

Proposal for 'getCalories()' function:

```javascript
function getCalories(steps) {
const averageBMR = 1800;
const averageNEAT = 450;
const averageTEF = 200;
const adaptiveThermogenesis = 100;
const caloriesPerStep = 0.04;

const totalCaloriesBurned = averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis + (steps * caloriesPerStep);

return totalCaloriesBurned;
}
```

Semantic Review:

- The pull request description lacks specific details about the code changes made to implement the user story. More information is needed to assess the alignment between the code and the user story requirements.

- The proposed 'getCalories()' function in the Technical Reference section provides a basic algorithm for calculating the total calories burned based on the number of steps. However, it does not consider the user's personal information or update the calories burned in real-time.

- The acceptance criteria specify the need for a button to retrieve the number of steps, real-time updates, consideration of personal information, error handling, and a user-friendly interface. It is unclear if these requirements have been addressed in the code implementation.

- Without further details or evidence from the pull request, it is challenging to determine if the code effectively delivers on the user story requirements or if there are any inconsistencies or missing functionalities. Additional information or code snippets are required for a comprehensive semantic review.

[![User Story 3 - Semantic Review](http://img.youtube.com/vi/-DxHM70g7ME/0.jpg)](https://www.youtube.com/watch?v=-DxHM70g7ME"User Story 3 - Semantic Review)