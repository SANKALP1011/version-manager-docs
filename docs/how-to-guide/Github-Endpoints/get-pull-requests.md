---
sidebar_position: 4
---

# Get User Pull Requests

## About

- The `getRepositoryClosedPullRequest` function, an Express.js route handler, retrieves `closed pull request` details for a user's GitHub repository. It checks user existence, `fetches closed pull requests` using GitHub service, and handles scenarios like `no user, GitHub service failure, or absence of closed pull requests`. The function `organizes and prepares structured data for each closed pull request`, updating or creating pull request documents in the database. User and repository details are also updated accordingly. `Error handling` ensures appropriate responses for various scenarios, ensuring a reliable interaction with GitHub and the database.

## Flow

```mermaid
graph TD
A[User] -- Request with User ID and Repo Name --> B[Verify User Existence]
B --|User Exists| --> C[Fetch Closed Pull Requests from GitHub]
C --|GitHub Service Success| --> D[Organize Pull Request Data]
D --|Document Exists?| --> E[Update Existing Document]
E --|Document Not Exists| --> F[Create New Document]
F --> G[Save Document to Database]
G --> H[Update User and Repo Details]
H --> I[Respond with Pull Request Data]
C --|GitHub Service Failure| --> J[Handle GitHub Service Error]
J --> I[Respond with Appropriate Error]
B --|User Not Found| --> K[Handle User Not Found Error]
K --> I[Respond with appropriate condtition]
```

## Endpoint

```javascript title="Routes/Repository/repos.router.js"
ReposRouter.get(
  "/user/repos/repo/getPullRequest",
  getRepositoryClosedPullRequest
);
```
