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
As a fitness enthusiast, I want to calculate today's calories burned based on the number of steps I have taken.

Action:
I would like to press a button to retrieve the number of steps I have taken today. Then, I expect the system to calculate and display the calories burned throughout the day.

Outcome:
By implementing this feature, I will be able to track and monitor my daily calorie expenditure based on the number of steps I have taken. This will provide me with valuable information to help me achieve my fitness goals and maintain a healthy lifestyle.

Acceptance Criteria:
1. The system should provide a button for the user to retrieve the number of steps they have taken today, allowing them to track their physical activity.
2. The system should calculate the calories burned throughout the day based on the number of steps retrieved, providing the user with an estimation of their calorie expenditure.
3. The system should display the calculated calories burned to the user, enabling them to monitor their daily calorie expenditure.
4. The system should ensure that the calculation of calories burned is accurate and based on a reliable algorithm or formula.
5. The system should update the calculated calories burned in real-time as the user retrieves the number of steps, providing them with up-to-date information.
6. The system should consider the user's personal information, such as weight and height, if applicable, to improve the accuracy of the calorie calculation.
7. The system should provide a clear and user-friendly interface for the user to view the calculated calories burned, ensuring ease of use and understanding.
8. The system should store the calculated calories burned for future reference or analysis, allowing the user to track their progress over time.
9. The system should ensure the privacy and security of the user's personal information, adhering to relevant data protection regulations.
10. The system should provide an option for the user to reset or clear the calculated calories burned, allowing them to start tracking from zero if desired.

Technical Reference: 

Proposal for the JavaScript function to calculate calories based on steps for an average person:

```javascript
function getCalories() {
const steps = getStepCount(); // Function to retrieve the number of steps
const averageBMR = 1800; // Average Basal Metabolic Rate
const averageNEAT = 450; // Average Non-Exercise Activity Thermogenesis
const averageTEF = 200; // Average Thermic Effect of Food
const adaptiveThermogenesis = 100; // Average Adaptive Thermogenesis
const caloriesPerStep = 0.05; // Average calories burned per step

const totalCalories = (steps * caloriesPerStep) + averageBMR + averageNEAT + averageTEF + adaptiveThermogenesis;

return totalCalories;
}
```