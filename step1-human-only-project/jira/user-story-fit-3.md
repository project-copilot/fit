# User story
## ID: FIT-3
## Epic ID: FIT-1
## Title: Create a Google Project and enable Google Fitness API
## Description:
Set up a project in the Google Cloud Console, enable the Fitness API, and obtain an OAuth 2.0 client ID and API key.
### Technical reference:
Simple way to deploy the app in a local enviroment using python: python -m http.server
Tool for debug Chrome DevTools
### Evidence:
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