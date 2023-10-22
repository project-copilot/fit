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
- Press "Complete" button and check status until processing is done 2 times
- Write a technical reference command:
```xml
<technical-reference>Compose a proposal outlining the implementation of the 'getCalories()' function for calculating the total calories burned. Additionally, provide the pseudocode for the 'getCalories()' function.</technical-reference>
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

[![User Story 3 - Step 1](http://img.youtube.com/vi/AWyS-uvkR-Y/0.jpg)](https://www.youtube.com/watch?v=AWyS-uvkR-Y "User Story 3 - Step 1")

[![User Story 3 - Step 2](http://img.youtube.com/vi/zOTJbq7Brmg/0.jpg)](https://www.youtube.com/watch?v=zOTJbq7Brmg "User Story 3 - Step 2")