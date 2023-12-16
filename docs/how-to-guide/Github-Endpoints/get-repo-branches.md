---
sidebar_position: 7
---

# Get Repository Branches

## About

- The `getRepositoryBranchList` function, an Express.js route handler, fetches and communicates a GitHub repository's branch list for a specified user. It verifies the user's existence, throwing a `UserNotFoundError` if not found, and fetches the repository document. Utilizing the `getRepositoryBranches` function, it retrieves the branch list, handling a `FailedToGetRepoistoryBranchs` error if unsuccessful. The function then updates the repository document with branch details and responds with a JSON object containing the branch information. Robust error handling caters to user absence or branch retrieval failure, providing specific error responses for each case, ensuring a smooth user experience.

## Flow

```mermaid
graph TD
A[User] -- Request with User ID and Repo Name --> B[Verify User Existence]
B --|User Exists| --> C[Fetch Repository Document]
C --|Document Found| --> D[Fetch Repository Branches]
D --|Branches Fetched| --> E[Update Repository Document]
E --> F[Respond with Branch Information]
F --> G[JSON Response]
D --|Failed to Fetch Branches| --> H[Throw FailedToGetRepoistoryBranchs Error]
H --> I[Error Response]
C --|Document Not Found| --> J[Throw RepositoryNotFoundError]
J --> I[Error Response]
B --|User Not Found| --> K[Throw UserNotFoundError]
K --> I[Error Response]
I --> L[Internal Server Error Response]
```

## Endpoint

```javascript title="Route/Repoistory/repos.routes.js"
ReposRouter.get("/user/repos/repo/getBranches", getRepositoryBranchList);
```
