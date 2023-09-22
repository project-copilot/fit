# CodeLab: Creating a Fitness App Using Project Copilot
## Step 1: Initial Version of the Project Created by Humans Only
This project is planned to be completed in one sprint. For this sprint, 2 epics and 4 user stories were created, with 2 user stories assigned to each epic. Here are the epics and their associated stories:

### Epic
#### ID: FIT-1
#### Title: Security and Authentication on Google Fit
#### Description:
Implement authentication and authorization using Google APIs. The goal is to enable users to access their Google Fit data in order to gain insights into their status and progress.

### Epic
#### ID: FIT-2
#### Title: Analyze and process Google Fit data
#### Description:
Analyze Google Fit data to calculate calories consumed and progress in health status.

_Note: Due to a time budget of 10 hours for the entire project, instead of writing the epics and user stories properly with the correct format, we have only written them as a feature request._

### User story
#### ID: FIT-3
#### Epic ID: FIT-1
#### Title: Create a Google Project and enable Google Fitness API
#### Description:
Set up a project in the Google Cloud Console, enable the Fitness API, and obtain an OAuth 2.0 client ID and API key.
##### Technical reference:
Simple way to deploy the app in a local enviroment using python: python -m http.server
Tool for debug Chrome DevTools
##### Evidence:
- Google Project created.
- Fitness API enabled.
- Credentials to use Fitness API created.
- App name: project-copilot-fitness
- Scopes:
    - .../auth/fitness.activity.read
    - .../auth/fitness.body.read
- OAuth Client ID
    - Application type: Web application
    - Name: FitWebClient
    - Authorized JavaScript origins
        - http://localhost:8000
        - http://localhost
- Developer approved tester: matias.molinas@gmail.com

Note: Simple way to deploy the app in a local enviroment using python: python -m http.server


### User story
#### ID: FIT-4
#### Epic ID: FIT-1
#### Title: Add the authentication to access the Google Fitness API
#### Description:
Add and set up the JavaScript client to authenticate the user, enabling them to retrieve data from Google Fit's REST API.

### User story
#### ID: FIT-5
#### Epic ID: FIT-2
#### Title: Calculate today's calories burned based on the number of steps
#### Description:
Retrieve today number of steps and calculate and display the calories burned in a day.

### User story
#### ID: FIT-6
#### Epic ID: FIT-2
#### Title: Calculate my health status score
#### Description:
Calculate and display the health status score by comparing the heart points  and the daily calories burned with a healthy goal. Take into account that the average adult requires around 2,000 to 2,500 calories per day to maintain their weight, and based on World Health Organization (WHO) and American Heart Association (AHA) guidelines for cardiovascular health, for a healthy person 150 Heart Points per week is a good score, that is approximately 21 Heart Points per day.

## Know issues:

### Bug
#### ID: FIT-7
#### Title: The calories value is not displayed in the UI
#### Description:
In the FIT-5 user story, the goal is to retrieve and display the calories burned in a day. The implementation currently shows the value in the console log, but it needs to display the value in the UI.

### Bug
#### ID: FIT-8
#### Title: Wrong calories value calculated
#### Description:
In the FIT-5 user story, the formula to calculate the calories burned in a day is not specified, and the implementation only calculates calories based on steps, omitting other factors that contribute to the average daily burned calories: 

- Basal Metabolic Rate (BMR): On average, BMR can range from around 1,200 to 2,400 calories per day for adults, depending on factors like age, gender, weight, and muscle mass. The Harris-Benedict equation is commonly used to estimate BMR based on these factors.
- Non-Exercise Activity Thermogenesis (NEAT): NEAT can vary significantly but may account for an additional 100 to 800 calories per day on average.
- Thermic Effect of Food (TEF): TEF typically accounts for about 10% of your daily calorie intake. If you consume 2,000 calories a day, TEF would be approximately 200 calories.
- Adaptive Thermogenesis: This factor is highly variable and can range from negligible to a few hundred calories per day.

We can use the following simplified formula:

Total Daily Calories = (Average BMR) + (Average NEAT) + (Average TEF) + Adaptive Thermogenesis + (Step Count * Calories Burned per Step)

We can use some rough average values:
- Average BMR: 1,800 calories per day (a mid-range estimate for adults)
- Average NEAT: 450 calories per day (a mid-range estimate)
- Average TEF: 200 calories per day (10% of a 2,000-calorie diet, as mentioned earlier)
- Adaptive Thermogenesis: This can vary, so you may or may not include an estimate here. If you want to account for it, you can use a value like 100 calories per day as a rough average.

With these values, the simplified formula becomes:

Total Daily Calories = 1,800 + 450 + 200 + 100 + (Step Count * Calories Burned per Step)

### Bug
#### ID: FIT-9
#### Title: The health score value is not displayed in the UI
#### Description:
In FIT-6, the goal is to calculate and display the health status score within a day. The current implementation shows the value in the console log, but it needs to be displayed in the UI.

### Backlog

![Backlog](/step1-human-only-project/backlog.png)

### Sprint

![Sprint](/step1-human-only-project/sprint.png)
