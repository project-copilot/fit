# CodeLab: Creating a Fitness App Using Project Copilot and GitHub Copilot
## Summary
<img align="left" src="/logo.png" />
This CodeLab is a brief tutorial on how to utilize [Project Copilot](https://projectcopilot.co/) and GitHub Copilot in a small software development project.

## Introduction to Project Copilot

[![Project Copilot](http://img.youtube.com/vi/2m4d0exOH1U/0.jpg)](https://www.youtube.com/watch?v=2m4d0exOH1U "User Story Improvement on JIRA with Project Copilot's Custom Instructions")

### The Advantages of Project Copilot
- With Project Copilot, receive assistance from an Artificial Intelligence system designed to enhance your Epics, User Stories, and Subtasks:
    - Leverages comprehensive data analysis and utilization of the Atlassian Knowledge Graph
        - Integrates relevant Confluence Design Documents
        - Incorporates related and linked Epics, User Stories and Subtasks
```mermaid
flowchart TD
    A[Atlassian Knowledge Graph] -->|Get context| B(Project Copilot)
    L[Epic/User Story/SubTask] -->|Draft & Commands| B(Project Copilot)
    B --> C{Prompt Expert Engine}
    C -->|Improved| D[Epic/User Story/SubTask]
```

### ChatGPT vs Project Copilot 
- Both provides Generative AI for Epics, User Stories and Sub Tasks
    - Why is better Project Copilot?
        - You don't need to write prompts from scratch
        - Context based on Atlassian Knowledge Graph
        - You can extend the prompt expert engine with commands
            - Current commands:
                - _Instruction: user definition of the custom instruction_
```xml
<technical-reference>User context for the technical reference </technical-reference>
```
        
```mermaid
flowchart TD
    A[Atlassian Knowledge Graph] -->|Get context| B(Project Copilot)
    L[Jira Epic/User Story/SubTask] -->|Jira User Draft & Commands| B(Project Copilot)
    B --> C{Prompt Expert Engine}
    C -->|Improved| D[Jira Epic/User Story/SubTask]
    F[ChatGPT User Draft & Prompt] -->|Get context| G(ChatGPT)
    G --> H[ChatGPT Epic/User Story/SubTask]
```

### GitHub Copilot
- Generative AI for Code
    - Based on 
        - Previous code
        - Code comments
        - Chat
    - Cons
        - Deviation of code regarding requeriments for poor user stories
        - Rework because deviation
```mermaid
flowchart TD
    A[Previous Code] -->|Get context| D(GitHub Copilot)
    B[Code Comments] -->|Get context| D(GitHub Copilot)
    C[GitHub Chat] -->|Get context| D(GitHub Copilot)
    D(GitHub Copilot) --> E(New Code)
```

### Project Copilot and GitHub Copilot
- Generative AI for Project Planning (Epics, User Stories, Sub Tasks) and Code
    - Generate Epics, User Stories and Sub-Tasks
    - Use User Stories and Sub-Tasks for chat code generation
```mermaid
flowchart TD
    A[User Draft] -->|Get context| B(Project Copilot)
    B(Project Copilot) --> C(User Story)
    C(User Story) -->|Get context| D(GitHub Copilot Chat)
    D(GitHub Copilot Chat) --> E(New Code)
```

### Project Copilot for Semantic Validation
- Automatic semantic description for code of pull requests (PR)
- Validation of semantic description of PR regarding user stories
```mermaid
flowchart TD
    A[User Draft] -->|Get context| B(Project Copilot)
    B(Project Copilot) --> C(User Story)
    C(User Story) -->|Get context| D(GitHub Copilot Chat)
    D(GitHub Copilot Chat) --> E(New Code)
    E(New Code) --> F(PR)
    F(PR) --> |Get context|G(Project Copilot)
    G(Project Copilot) --> H(PR Semantic Description)
    H(PR Semantic Description) --> I(Semantic Validation)
```

## CodeLab

The CodeLab provides an initial version of the project as a starting point. This version was exclusively created by a human, with the constraint of completing the project epics, user stories, sub-tasks, code, and peer reviews in a maximum of 10 hours.
The goal of the CodeLab is to gradually recreate the same project with the assistance of Project Copilot and GitHub Copilot in less than 1 hour to finally compare both projects, and get metrics about the planning and implementation.

The project's objective is to develop a compact client-side fitness application using HTML and JavaScript. This application should be capable of interfacing with the Google Fit REST API and computing daily calorie consumption based on the number of steps taken. Additionally, it should calculate a health score derived from these calories and "heart points."

Use this link to install [Project Copilot](https://marketplace.atlassian.com/apps/1231554?tab=overview&hosting=cloud)



