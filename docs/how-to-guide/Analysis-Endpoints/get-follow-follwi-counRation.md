---
sidebar_position: 4
---

# Get Follower to Following Count Ratio

## About

- The `getFollowerToFollowingCountAnalysis` function serves as a vital component in the server application, analyzing the follower-to-following ratio for a specified user. Extracting the user ID from incoming requests, the function retrieves user information and calculates the simplified ratio by finding the greatest common divisor. If successful, it responds with a JSON object containing the Follower-to-Following Ratio and a 200 status code. In cases of errors, such as the user not existing or issues during the analysis, it gracefully handles errors and responds with appropriate status codes and error details in JSON format. This function provides valuable insights into the user's engagement dynamics on the platform.

## Flow

```mermaid
graph TD
A[Start] -->|Receive Request| B[Extract User ID]
B -->|User ID| C[Retrieve User]
C -->|User Not Found| D[Handle User Not Found]
C -->|User Found| E[Calculate Simplified Ratio]
E -->|Success| F[Respond with Ratio and Status 200]
E -->|Error| G[Handle Error and Respond with Status Code]
A -->|End| H[End]
D -->|End| H
F -->|End| H
G -->|End| H
```

## Endpoint

```javascript title="Routes/Analysis/profileAnalysis.router.js"
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/followerToFollowingRatio",
  getFollowerToFollowingCountAnalysis
);
```
