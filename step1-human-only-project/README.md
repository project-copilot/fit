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
Analyze Google Fit data to calculate the calories consumed during running sessions, considering factors such as the number of steps, session duration, and vital signs, such as heart rate and respiration rate during these sessions. Utilize this information, including vital signs both during and after exercise, to assess progress in health and training status.

_Note: Due to a time budget of 10 hours, instead of writing the epics and user stories properly with the correct format, we have only written them as a feature request._

### User story
#### ID: FIT-3
#### Epic ID: FIT-1
#### Title: Create a Google Project and enable Google Fitness API
#### Description:
Set up a project in the Google Cloud Console, enable the Fitness API, and obtain an OAuth 2.0 client ID and API key.

### User story
#### ID: FIT-4
#### Epic ID: FIT-1
#### Title: Add the authentication to access the Google Fitness API
#### Description:
Add and set up the JavaScript client to authenticate the user, enabling them to retrieve data from Google Fit's REST API.

### User story
#### ID: FIT-5
#### Epic ID: FIT-2
#### Title: Calculate calories consumed on my last running session
#### Description:
Retrieve the time, number of steps, heart rate during the exercise, and optionally the respiration rate from the latest running session. Calculate and display the calories burned.

### User story
#### ID: FIT-6
#### Epic ID: FIT-2
#### Title: Calculate my training status score
#### Description:
If, for the most recent exercise session, we have information about the heart rate during exercise and the heart rate at the end, following a brief rest, we can calculate a training status score based on heart rate recovery. If the respiration rate is available, you can also use it to calculate the training status score. Display the calculated training status score after completing the calculation.
