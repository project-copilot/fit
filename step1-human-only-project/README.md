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
Retrieve today number of steps and calculate and display the calories burned.

### User story
#### ID: FIT-6
#### Epic ID: FIT-2
#### Title: Calculate my health status score
#### Description:
Calculate the health status score by comparing the heart points  and the daily calories burned with a healthy goal. Take into account that the average adult requires around 2,000 to 2,500 calories per day to maintain their weight, and based on World Health Organization (WHO) and American Heart Association (AHA) guidelines for cardiovascular health, for a healthy person 150 Heart Points per week is a good score, that is approximately 21 Heart Points per day.
