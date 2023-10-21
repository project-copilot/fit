# CodeLab: Creating a Fitness App Using Project Copilot and GitHub Copilot
## Step 2: Project Planning using Project Copilot

### Use the following link to install the new Alpha version of Project Copilot App for Confluence:

[Project Copilot for confluence Alpha version 0.1](https://developer.atlassian.com/console/install/8a93e156-3682-44f1-a179-d03e01379de2?signature=4e995d26b6bb159474223be4c8018b55e06a8a1a6571e03f50ecdf866ac31eb5ad0a567d47d904c9d65b59d1f44a76d37561e34d4ee0f4fa64d204c73e6203b2&product=confluence)

_Note: This initial version offers limited functionality, primarily designed to either finalize the next paragraph in a document or execute a custom instruction with the following syntax:_

```xml
<instruction> my custom instruction to improve the content or add content to the document </instruction>
```

### Use the following link to install the new version of Project Copilot App for Jira:
[Project Copilot for Jira on Atlassian Marketplace](https://marketplace.atlassian.com/apps/1231554)

_Note: This version introduces an enhanced search feature for retrieving relevant content from Confluence documents, which can be used as context for improving or composing user stories within the App. Additionally, this version includes the inaugural release of the 'Semantic Validation Workflow.' This internal workflow conducts a semantic evaluation of the code implementation description in relation to the user story. To initiate the semantic validation process, users are required to employ the following syntax and then click 'Complete':_

```xml
<validation> semantic code description </validation>
```

_Note the semantic code description can be generated with one of these third-party tools:_

- [GitHub Copilot for Pull Requests](https://githubnext.com/projects/copilot-for-pull-requests)
- [Codium-AI PR-Agent](https://github.com/Codium-ai/pr-agent)

### Confluence Documents

_In this CodeLab only the Software Architecture Document (SAD) is created using the new Project Copilot for Confluence App:_

#### Software Architecture Document (SAD):
- link to complete the SAD step by step using Project Copilot for Confluence App: [SAD](/step2-project-copilot-project/confluence/software-architecture-document.md)

_We have also developed three Technical Reference documents containing information about the Google Fit API, Google Identity Services, and valuable fitness formulas sourced from websites. These documents serve to enhance the context for the user stories in Jira._

#### Technical Reference: Google Identity Service JavaScript library

- link: [Technical Reference: Google Identity Service JavaScript library](/step2-project-copilot-project/confluence/technical-reference-gis.md)

#### Technical Reference: Google FIT Rest API

- link: [Technical Reference: Google FIT Rest API](/step2-project-copilot-project/confluence/technical-reference-google-fit-rest-api.md)

#### Technical Reference: Fitness Formulas

- link: [Technical Reference: Fitness Formulas](/step2-project-copilot-project/confluence/technical-reference-fitness-formulas.md)

### Jira Project

### Epics:
#### Epic 1: Security and Authentication on Google Fit
- link: [Epic 1](/step2-project-copilot-project/jira/epic-fit-1.md)

#### Epic 2: Analyze and process Google Fit data
- link: [Epic 2](/step2-project-copilot-project/jira/epic-fit-2.md)

### User stories:

#### User story 1: Create a Google Project and enable Google Fitness API
- link [User story 1](/step2-project-copilot-project/jira/user-story-fit-3.md)

#### User story 2: Add the authentication to access the Google Fitness API
- link [User story 2](/step2-project-copilot-project/jira/user-story-fit-4.md)

#### User story 3: Calculate today's calories burned based on the number of steps
- link [User story 3](/step2-project-copilot-project/jira/user-story-fit-5.md)

#### User story 4: Calculate my health status score
- link [User story 4](/step2-project-copilot-project/jira/user-story-fit-6.md)