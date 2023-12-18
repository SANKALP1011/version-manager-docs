---
sidebar_position: 1
---

# Introduction

## About

- After successfully authenticating through GitHub, users can leverage our API's various endpoints, each powered by the **GitHub Service function** to retrieve data from GitHub. These service functions are seamlessly integrated into our **Repository Controller**, where they are invoked to process and selectively store essential data in the database—eliminating the need to save the entire response.

## Github Services

- For more about services that are being used for fetching the data from the github rest api , refer to the following [Service](/docs/Services/Services.md).

## Endpoints

- This is a list of endpoints designed to handle and analyze responses, facilitating the saving of essential data in our database :

```javascript title="/Routes/Repository/repos.router.js"
ReposRouter.get("/user/repos", getUserRepository);
ReposRouter.get("/user/repos/getRepoByName", getRepositoryByName);
ReposRouter.get(
  "/user/repos/repo/getPullRequest",
  getRepositoryClosedPullRequest
);
ReposRouter.get("/user/repos/repo/getRepoTopics", getRepositoryTopic);
ReposRouter.get("/user/repos/repo/getRepoLang", getRepositoryLanguages);
ReposRouter.get("/user/repos/repo/getBranches", getRepositoryBranchList);
ReposRouter.get("/user/repos/repo/getIssues", getRepositoryIssue);
ReposRouter.get("/user/repos/repo/getCommits", getRepositoryCommits);
```

:::info

The purpose of these endpoints is to store essential responses in the database using unique values. Once this data is successfully saved, our **analysis microservice** will conduct a comprehensive analysis on the stored responses. The goal is to generate insightful information regarding the user's GitHub usage, offering **valuable insights and statistics**.

:::
