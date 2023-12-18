---
sidebar_position: 18
---

# Get Pull Event Analysis

## About

- The `getUserPullEventAnalysis` function is a server-side endpoint designed to analyze and provide insights into a user's pull request events on GitHub. The process begins by verifying the existence of the user in the database. If the user is not found, the function throws a custom error, UserNotFoundError. Following user verification, the function fetches the user's events, specifically focusing on pull request events, using the getUserActionsEvents function. If the events are successfully fetched, the function filters and extracts relevant data, such as the event type, date, and repository name, and responds with a JSON array containing details of the user's pull request events. In case of errors, the function handles specific scenarios, throwing a FailedToGetPushEventDataAnalysis error when unable to retrieve or analyze the pull request events. This function contributes to understanding a user's engagement and activity related to pull requests on GitHub.

## Flow

```mermaid
graph TD
A[User] -- Request with User ID --> B[Verify User Existence]
B --|User Exists| --> C[Fetch User Events]
C --|Events Fetched| --> D[Filter and Extract Pull Request Events]
D --|Pull Request Events Analyzed| --> E[Respond with Pull Request Event Data]
C --|Failed to Fetch Events| --> F[Handle Fetch Events Error]
F --> G[Respond with Error Details]
D --|No Pull Request Events Found| --> H[Respond with No Pull Request Events Message]
B --|User Not Found| --> I[Handle User Not Found Error]
I --> G[Respond with Error Details]

```

## Endpoint

```javascript title="Routes/Analysis/profileAnalysis.router.js"
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/getUserPullEventsAnalysis",
  getUserPullEventAnalysis
);
```
