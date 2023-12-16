---
sidebar_position: 3
---

# Get Repo by Name

## About

- The `getRepositoryByName` function in Express.js fetches details about a GitHub repository for a user using **query parameters**. It searches the **user's repository document and responds with repository information** in a compact `JSON format`. Error handling ensures appropriate responses for potential issues.

## Flow

```mermaid
graph TD
A[User] -- Request with User ID and Repo Name --> B[Node.js Backend]
B -- Retrieve User Details from DB --> C[Check User Existence]
C -- User Exists --> D[Locate User's Repo Document]
D -- Repo Document Found? --> E[Search for Repo by Name]
E -- Repo Found? --> F[Respond with Repo Details]
F --> G[JSON Response]
E --[Repo Not Found] --> H[Handle Error: Repo Not Found]
H --> I[Error Response]
D -- [Repo Document Not Found] --> J[Handle Error: Repo Document Not Found]
J --> I
C -- User Does Not Exist --> B
```

## Endpoint

```javascript title="Routes/Repository/repos.router.js"
ReposRouter.get("/user/repos/getRepoByName", getRepositoryByName);
```
