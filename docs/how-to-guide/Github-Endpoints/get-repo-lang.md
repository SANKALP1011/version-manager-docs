---
sidebar_position: 6
---

# Get Repository Language

## About

- The `getRepositoryLanguages` function, an Express.js route handler, retrieves details about programming languages and their corresponding code sizes in a user's GitHub repository. It begins by validating the user's existence and fetching the associated repository document. Utilizing `getRepositoryBuildLang` for language information, the function updates the repository document with details on each language and its code size. The response consists of a JSON object containing language information. Robust error handling includes scenarios like user not found (`UserNotFoundError`), repository absence (`RepositoryNotFoundError`), language information retrieval failure (`FailedToFetchRepositoryLanguages`), or internal server errors, providing precise error responses for each case, ensuring a seamless user experience.

## Flow

```mermaid
graph TD
A[User] -- Request with User ID and Repo Name --> B[Verify User Existence]
B --|User Exists| --> C[Fetch Repository Document]
C --|Document Found| --> D[Fetch Repository Languages]
D --|Languages Fetched| --> E[Update Repository Document]
E --> F[Respond with Language Information]
F --> G[JSON Response]
D --|Failed to Fetch Languages| --> H[Throw FailedToFetchRepositoryLanguages Error]
H --> I[Error Response]
C --|Document Not Found| --> J[Throw RepositoryNotFoundError]
J --> I[Error Response]
B --|User Not Found| --> K[Throw UserNotFoundError]
K --> I[Error Response]
I --> L[Internal Server Error Response]
```

## Endpoint

```javascript title="Route/Repoistory/repos.routes.js"
ReposRouter.get("/user/repos/repo/getRepoLang", getRepositoryLanguages);
```
