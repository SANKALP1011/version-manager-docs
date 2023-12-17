---
sidebar_position: 1
---

# Introduction

## About

- This documentation details the `analysis endpoints` that leverage [Github-Custom-Endpoints](/docs/how-to-guide/Github-Endpoints/intro.md) to provide valuable `insights into the data stored in our database`. These endpoints are powered by `userStatisticalAnalysis.controller.js`, delivering route handling functionality to each analysis endpoint.

## Analysis Controller

- This controller takes on the crucial role of `managing functionality` for the data stored in our database, `offering insightful` and useful analysis. It incorporates custom error handling and employs parallel data processing to ensure swift and efficient analysis.

```bash title="Controller"
VersionManager/
|-- Controller/
|   | -- userStatisticalAnalysis.controller.js
```

:::info
To capture valuable data from the GitHub REST API and store it in our database, I've developed `repository.controller.js` and `repos.router.js`. These files define routes and route handlers for analyzing the API response and saving the relevant data in the database. For more details, refer to the documentation at [Github-Custom-Endpoints](/docs/how-to-guide/Github-Endpoints/intro.md).
:::

## Endpoints

- These are the set of the endpoints which are defined in the following folder :

```bash title="Controller"
VersionManager/
|-- Routes/
|   | -- Analysis/
|   |    -- profileAnalysis.router.js
```

- This folder includes the following endpoints :

```javascript title="Route/Analysis/profileAnalysis.router.js"
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/followerAnalysis",
  getFollowerCountAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/followingAnalysis",
  getFollowingCountAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/followerToFollowingRatio",
  getFollowerToFollowingCountAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/repoCountAnalysis",
  getNumberOfPublicAndPrivateRepoAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/tsotalLanguageCountsAnalysi",
  getLanguagesUsedAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/totalTopicsCounts",
  getMostUsedTopicAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/totalClosedIssuesCounts",
  getTotalClosedIssueAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/totalOpenIssuesCounts",
  getTotalOpenIssueAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/totalLinesOfCodePushed",
  getNumberOfLinesOfCodePushedAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/totalStarsCounts",
  getTotalStarsForProfileAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/oldestNewestRepo",
  getNewestAndOldestRepoAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/getCompanyNameAnalysis",
  getOrganisationAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/getTopRepoAnalysis",
  getTopRepositoryAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/getRecentCommitAnalysis",
  getMostRecentRepositoryCommitAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/getPullRequestAnalysis",
  getTotalPullRequestCountAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/getUserPushEventsAnalysis",
  getUserPushEventsAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/getUserPullEventsAnalysis",
  getUserPullEventAnalysis
);
ProfileAnalysisRouter.get(
  "/user/profileAnalysis/getUserWatchEventsAnalysis",
  getUserWatchEventAnalysis
);
```
