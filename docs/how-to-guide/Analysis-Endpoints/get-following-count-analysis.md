---
sidebar_position: 3
---

# Get Following Count Analysis

## About

- The `getFollowingCountAnalysis` function plays a pivotal role in the server application by managing requests for the analysis of following counts for a designated user. This asynchronous function extracts the user ID from incoming requests, schedules periodic follower updates with `scheduleFollowerUpdateJob`, and retrieves the updated following count using `getUpdatedFollowing`. Upon success, it responds with a JSON object containing the following count and a 200 status code. In the event of analysis failure, it gracefully handles errors, throwing a custom error, `FailedToPerformFollowerorFollowingCountAnalysis`, with pertinent details. This meticulous error handling ensures informative responses, enhancing the reliability of the server's following count analysis functionality.

## Flow

```mermaid
graph TD
A[Start] --> B[Receive Request]
B --> C[Extract User ID]
C --> D[Schedule Follower Update Job]
D --> E[Retrieve Updated Following Count]
E --|Success| --> F[Generate JSON Object]
F --> G[Respond with 200 Status Code]
E --|Failure| --> H[Throw FailedToPerformFollowerorFollowingCountAnalysis Error]
H --> I[Handle Analysis Failure]
I --> J[Respond with Error Details]
J --> K[End]
```

## Cron Job

- As the user's following count undergoes regular changes, either increasing or decreasing, I've implemented a cron scheduler. This scheduler fetches the latest user data from the GitHub REST API service and ensures that the database is updated accordingly.

## Cron Following Scheduler Flow

```mermaid
graph TD
A[Start] --> B[Retrieve User by ID]
B --|User Not Found| --> C[Handle User Not Found Error]
C --> I[Respond with Error]
B --|User Found| --> D[Fetch Updated Following Count]
D --|Fetch Success| --> E[Check if Response is Array]
E --|Response Not Array| --> F[Handle Fetch Error]
F --> I[Respond with Error]
E --|Response is Array| --> G[Calculate New Following Count]
G --> H[Update User in Database]
H --> I[Respond with New Following Count and Change Status]
D --|Fetch Failure| --> F[Handle Fetch Error]
I[End]
```

:::info

- For more about cron schedulers , refer to to the following doc about [Schedulers](/docs/Scheduler/Scheduler.md).

:::

## Endpoint

```javascript title="Routes/Analysis/profileAnalysis.router.js"
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/followingAnalysis",
  getFollowingCountAnalysis
);
```
