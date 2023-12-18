---
sidebar_position: 9
---

# Get Total Open Issue Analysis

## About

- The `getTotalOpenIssueAnalysis` function is a server-side endpoint responsible for analyzing and providing the total count of open issues across all repositories associated with a specific user. The process begins by extracting the user ID from the incoming request, retrieving user information from the database, and fetching details about the user's repositories. The function then iterates through each repository, summing up the counts of open issues. The result is a JSON object containing the total count of open issues. In case the user is not found, the function throws a custom error class, UserNotFoundError, and responds with an appropriate status code and error details in JSON format. If any other errors occur during the process, the function logs the error for debugging purposes and returns the error.

## Flow

```meramaid
graph TD
A[Start] -->|Receive Request| B[Extract User ID]
B -->|User ID| C[Retrieve User by ID]
C -->|User Not Found| D[Handle User Not Found Error]
D -->|Error| N[Log Error]
C -->|User Found| E[Fetch User Repositories]
E -->|Repositories Fetched| F[Initialize Open Issue Count]
F -->|Count Initialized| G[Iterate Through Repositories]
G -->|Repository Iteration| H[Extract Repository Open Issue Counts]
H -->|Issue Count Data| I[Sum Up Open Issue Counts]
I -->|Summation Complete| G
G -->|All Repositories Processed| J[Respond with JSON Object]
J -->|Response| K[End]
N -->|Error| K[End]

```

## Endpoint

## Endpoint

```javascript title="Routes/Analysis/profileAnalysis.router.js"
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/totalOpenIssuesCounts",
  getTotalOpenIssueAnalysis
);
```
