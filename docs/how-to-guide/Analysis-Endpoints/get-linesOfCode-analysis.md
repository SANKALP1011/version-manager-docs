---
sidebar_position: 10
---

# Get Number Of Lines Of Code Pushed Analysis

## About

- The `getNumberOfLinesOfCodePushedAnalysis` function is a server-side endpoint that calculates and provides valuable insights into the total number of lines of code pushed by a specific user since joining Git. The process involves extracting the user ID, retrieving user information, and fetching details about the user's repositories. By summing up the bytes of code pushed for each programming language across all repositories, the function returns a JSON object with the total count of bytes of code pushed. It incorporates robust error handling, throwing custom error classes for scenarios like a user not existing or a document retrieval failure, and responds with appropriate status codes and error details in JSON format. This functionality enhances the understanding of a user's coding activity and contribution over their Git journey.

## Flow

```mermaid
graph TD
A[Start] -->|Receive Request| B[Extract User ID]
B -->|User ID| C[Retrieve User by ID]
C -->|User Not Found| D[Handle User Not Found Error]
D -->|Error| N[Log Error]
C -->|User Found| E[Fetch User Repositories]
E -->|Repositories Fetched| F[Initialize Total Bytes of Code Pushed]
F -->|Count Initialized| G[Iterate Through Repositories]
G -->|Repository Iteration| H[Iterate Through Languages]
H -->|Language Iteration| I[Sum Up Bytes of Code Pushed]
I -->|Summation Complete| H
H -->|All Languages Processed| G
G -->|All Repositories Processed| J[Respond with JSON Object]
J -->|Response| K[End]
N -->|Error| K[End]
```

## Endpoint

```javascript title="Routes/Analysis/profileAnalysis.router.js"
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/totalLinesOfCodePushed",
  getNumberOfLinesOfCodePushedAnalysis
);
```
