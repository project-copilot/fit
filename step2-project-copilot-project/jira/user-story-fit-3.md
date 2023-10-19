# User story
## ID: FIT-3
## Epic ID: FIT-1
## Title: Create a Google Project and enable Google Fitness API
## Initial Description:
Set up a project in the Google Cloud Console, enable the Fitness API, and obtain an OAuth 2.0 client ID and API key.
## Linked documents:
[Software Architecture Document](/step2-project-copilot-project/confluence/software-architecture-document.md)
[Technical Reference: Google Identity Service JavaScript library](/step2-project-copilot-project/confluence/technical-reference-gis.md)
## Actions in Project Copilot:
- Press "Complete" button 2 times
- Write custom instruction:
```xml
<instruction>Replace user with developer in the acceptance criteria</instruction>
```
- Press "Complete" button
## Final Description:
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

### Technical reference:
Simple way to deploy the app in a local enviroment using python: python -m http.server
Tool for debug Chrome DevTools