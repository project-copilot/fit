# CodeLab: Creating a Fitness App Using Project Copilot and GitHub Copilot
## Step 3: Implement Project code using GitHub Copilot
Utilizing the enhanced user stories, create a code proposal with the assistance of GitHub Copilot. The following steps outline how to generate the code proposal for each corresponding story:

### Tasks:

### Implement User Story
#### ID: FIT-3
#### Epic ID: FIT-1
#### Title: Create a Google Project and enable Google Fitness API
#### Description:
User:

As a developer, I want to create a Google project and enable the Google Fitness API.

Action:

I will set up a project in the Google Cloud Console and enable the Fitness API. Additionally, I will obtain an OAuth 2.0 client ID and API key.

Outcome:

By completing these actions, I will have a Google project set up with the Fitness API enabled. I will also have the necessary credentials (client ID and API key) to access and use the Fitness API in my application.

Acceptance Criteria:

1. The developer should be able to create a Google project in the Google Cloud Console.

2. The developer should be able to enable the Google Fitness API in the created Google project.

3. The developer should be able to obtain an OAuth 2.0 client ID and API key after setting up the Google project and enabling the Fitness API.

4. The developer should have the necessary credentials (client ID and API key) to access and use the Fitness API in their application.

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

### Implement User Story
### User story
#### ID: FIT-4
#### Epic ID: FIT-1
#### Title: Add the authentication to access the Google Fitness API
#### Description:
User:

As a developer integrating Google Fit into my application, I need to authenticate the user to access the Google Fitness API.

Action:

I want to add and set up the JavaScript client to authenticate the user, enabling them to retrieve data from Google Fit's REST API.

Outcome:

So the user will be able to securely access their fitness data from Google Fit and use it within my application, providing them with a seamless experience and allowing them to track their fitness progress effectively.

Acceptance Criteria:

1. The user should be able to navigate to the Google Developer Console and create a new project.

2. The user should be able to enable the Google Fitness API for the created project.

3. The user should be able to set up the JavaScript client library in their application.

4. The user should be able to authenticate the user using the JavaScript client library.

5. The user should be able to retrieve fitness data from the Google Fitness API using the authenticated user.

6. The user should be able to securely access their fitness data from Google Fit within the application.

7. The user should be able to track their fitness progress effectively using the retrieved data.

8. The user should be able to seamlessly use the fitness data within the application.

9. The user should be able to validate the javascript client by retrieving today’s number of steps.

Technical Reference:

Sample code to retrieve user steps:

    function getStepCount() {
        return new Promise((resolve, reject) => {
          var startTimeMillis = new Date().setHours(0, 0, 0, 0); // Start time for today
          var endTimeMillis = new Date().setHours(23, 59, 59, 999); // End time for today

          var requestBody = {
            aggregateBy: [
              {
                dataTypeName: 'com.google.step_count.delta',
              },
            ],
            bucketByTime: { durationMillis: 86400000 }, // 1 day in milliseconds
            startTimeMillis: startTimeMillis,
            endTimeMillis: endTimeMillis,
          };

          var xhr = new XMLHttpRequest();
          xhr.onreadystatechange = function () {
            if (this.readyState == 4) {
              if (this.status == 200) {
                var response = JSON.parse(this.responseText);
                var stepCount = response.bucket[0].dataset[0].point[0].value[0].intVal;
                console.log('Step Count for Today:', stepCount);
                resolve(stepCount); // Resolve the promise with the step count
              } else {
                reject(new Error('Failed to fetch step count')); // Reject the promise on error
              }
            }
          };
          xhr.open('POST', 'https://www.googleapis.com/fitness/v1/users/me/dataset:aggregate');
          xhr.setRequestHeader('Authorization', 'Bearer ' + access_token);
          xhr.setRequestHeader('Content-Type', 'application/json');
          xhr.send(JSON.stringify(requestBody));
        });
      }

#### Actions in VS Code and GitHub Copilot:

1. Create a new project on VS Code. Activate GitHub Copilot
2. Create a index.html
3. Copy the following sample of authentication and authorization code:


4. Open GitHub Copilot Chat window and copy the user story: