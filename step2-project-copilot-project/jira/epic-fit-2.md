# Epic
## ID: FIT-2
## Title: Analyze and process Google Fit data
## Initial Description:
Analyze Google Fit data to calculate calories consumed and progress in health status.
## Linked documents:
[Software Architecture Document](/step2-project-copilot-project/confluence/software-architecture-document.md)
[Technical Reference: Google FIT Rest API](/step2-project-copilot-project/confluence/technical-reference-google-fit-rest-api.md)
[Technical Reference: Fitness Formulas](/step2-project-copilot-project/confluence/technical-reference-fitness-formulas.md)
## Actions in Project Copilot:
- Press "Complete" button
## Final Description:
As part of our ongoing efforts to promote health and fitness, we aim to develop a robust Health and Calorie Analysis integration into our platform. This Agile software project involves creating a small HTML/JavaScript client-side app that will analyze Google Fit data, calculate calories consumed, and estimate the user's health status. This integration will utilize the Google Fit REST API to access and process user fitness data, allowing us to provide valuable insights and recommendations to our users.

**Objectives**:

1. **Data Integration**: Integrate with the Google Fit API to access user fitness data efficiently.
2. **Calorie Calculation**: Calculate daily calories consumed by users based on various components.
3. **Health Status Estimation**: Estimate user health status using a formula that combines calorie consumption and heart points.
4. **Recommendations**: Provide basic health recommendations to users based on the calculated metrics.

**Scope**: The scope of this epic includes the development of a client-side app with the following core features:
1. **Data Retrieval**: Fetch user fitness data from the Google Fit API.
2. **Calorie Calculation**: Calculate calories burned per day, considering various components (BMR, NEAT, TEF, Adaptive Thermogenesis, and Exercise Activity).
3. **Heart Points Analysis**: Calculate average heart points per day.
4. **Data Visualization**: Display calories burned and heart points over time.
5. **Health Recommendations**: Provide basic health recommendations based on calculated metrics.
6. **Health Status Classification**: Determine the user's health status based on WHO/AHA guidelines.

**Acceptance Criteria**:
1. The client-side app successfully retrieves user fitness data from the Google Fit API.
2. Daily calorie consumption is accurately calculated using the specified components.
3. Average heart points per day are calculated correctly.
4. The app displays calorie burn and heart points over time through intuitive visualizations.
5. Basic health recommendations are generated based on the calculated metrics.
6. The health status of the user is correctly classified according to the provided guidelines.

**Additional Information**:
- Health Score Formula: Health Score = (CaloriesBurned / 2250) + (HeartPoints / 21)
- Health Status Classification:
    - If Health Score < 1, Health Status is "Needs Improvement."
    - If Health Score >= 1 and <= 2, Health Status is "Normal."
    - If Health Score > 2, Health Status is "Excellent."
- Calorie Components:
    - Basal Metabolic Rate (BMR)
    - Non-Exercise Activity Thermogenesis (NEAT)
    - Thermic Effect of Food (TEF)
    - Adaptive Thermogenesis
    - Exercise Activity
    - Steps walked (with an average calorie consumption per step of 0.04)

- Average Values:
    - const averageBMR = 1800
    - const averageNEAT = 450
    - const averageTEF = 200
    - const adaptiveThermogenesis = 100
    - Steps x 0.04 is added to the total calories burned.

**Dependencies**:
- Integration with Google Fit API
- Availability of user fitness data

**Assumptions**:
- Users have access to Google Fit data.
- Accurate user attributes are available for BMR calculations.
- The app will be initially implemented without AI assistance and then enhanced using AI tools for comparison.

**Risks**:
- API changes or limitations in Google Fit API.
- Accuracy of user-provided attributes for BMR calculation.
- Accuracy of health status estimation based on provided formulas.

This epic serves as the foundation for creating user stories that will address each of the specified objectives and features in detail, allowing for a more granular breakdown of the work required for this project.