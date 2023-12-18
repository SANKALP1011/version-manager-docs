---
sidebar_position: 6
---

# Get Languages Used Analysis

## About

- The `getLanguagesUsedAnalysis` function is a server-side endpoint designed to analyze the distribution of programming languages used by a specific user across their repositories. Upon receiving a request, the function extracts the user ID, retrieves the user's information, and subsequently fetches details about the user's repositories. It then iterates through each repository, aggregating the byte counts for each programming language used in the repositories. The result is a JSON object containing the total byte counts for each programming language. In the event of any errors during this process, the function logs the error for debugging purposes. This function provides valuable insights into the programming language landscape of a user's repositories, aiding in the analysis of their coding preferences and practices.

## Flow

```mermaid
graph TD
A[Start] -->|Receive Request| B[Extract User ID]
B -->|User ID| C[Retrieve User by ID]
C -->|User Not Found| D[Handle User Not Found Error]
D -->|Error| N[Log Error]
C -->|User Found| E[Fetch User Repositories]
E -->|Repositories Fetched| F[Initialize Total Language Byte Counts]
F -->|Counts Initialized| G[Iterate Through Repositories]
G -->|Repository Iteration| H[Extract Repository Languages and Byte Counts]
H -->|Language Data| I[Aggregate Byte Counts for Each Language]
I -->|Aggregation Complete| G
G -->|All Repositories Processed| J[Respond with JSON Object]
J -->|Response| K[End]
N -->|Error| K[End]
```

## Endpoint

```javascript title="Routes/Analysis/profileAnalysis.router.js"
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/tsotalLanguageCountsAnalysi",
  getLanguagesUsedAnalysis
);
```
