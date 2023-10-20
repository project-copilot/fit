# User story
## ID: FIT-4
## Epic ID: FIT-1
## Title: Add the authentication to access the Google Fitness API
## Initial Description:
Add and set up the JavaScript client to authenticate the user, enabling them to retrieve data from Google Fit's REST API.
## Linked documents:
[Software Architecture Document](/step2-project-copilot-project/confluence/software-architecture-document.md)
[Technical Reference: Google Identity Service JavaScript library](/step2-project-copilot-project/confluence/technical-reference-gis.md)
## Actions in Project Copilot:
- Press "Complete" button 2 times

## Final Description:
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

```javascript
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
```

_Note: In this user story, the Tech Reference is authored by the user after AI assistance generates the user story and acceptance criteria. Is it feasible to automatically generate the Technical Reference by employing the custom command 'Technical Reference:' in italics. This process works seamlessly when there is a similar user story with a matching Technical Reference or when a Technical Design Document from Confluence is linked to the user story._

[![User Story 2](http://img.youtube.com/vi/O_EoTV13C0U/0.jpg)](https://www.youtube.com/watch?v=O_EoTV13C0U "User Story 2")