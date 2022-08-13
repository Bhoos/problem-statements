# Problem Statement 3
When communication happens between 2 parties, there is always a chance that one of them is using a different version. And as such, when the communication format changes, things may break.

**Requirements:**
- Reading code

**Problem Goal:** 
- Find a fix satisfying the problem statement.

**Problem Description:**
Teams scored some points based on their performance and all the meta-data collected was aggregated and plotted in a graph.

Here is the data format. The “fields” field contains all the data collected from the team.
```
{
 "value": {
   "rankings": {
     "count": 10,
     "rows": [ /* ranking data here*/ ]
   },
   "history": {
     "fields": [
       "count",
       "score",
       "recklessScore",
       "chickenScore",
       "dhoosScore",
       "responseTime",
       "winCount",
       "lossCount",
       "dqCount",
       "toCount",
       "isRankingMatch", /* added later */
       "createdAt"
     ],
     "data": {
        /* team id is used as key */
       /* holds data for team based on fields */
       "1": [
         [ 20, 6, 32, 12.2, 115, 15.3, null, null, null, null, true,
           "2022-03-14T11:14:41.951Z"
         ],
         [ 5, 2, 7, 3, 35, 5.9, null, null, null, null, true,
           "2022-03-18T09:09:49.161Z"
         ],         
         /* many many more data here */
       ]
     }
   }
 }
}
```
And the first step of the pipeline in front-end for data aggregation.

```
// Single Team History Data
const singleTeamDataObject = {};
 
Object.entries(singleTeamHistoryData.value.history.data).forEach(
 ([key, value]: any, idx) => {
   singleTeamDataObject[key] = value.map(
     ([
       count,
       score,
       recklessScore,
       chickenScore,
       dhoosScore,
       responseTime,
       winCount,
       lossCount,
       dqCount,
       toCount,
       createdAt,
     ]) => ({
       count,
       score,
       recklessScore,
       chickenScore,
       dhoosScore,
       responseTime,
       winCount,
       lossCount,
       dqCount,
       toCount,
       createdAt,
     })
   );
 }
);

```
When a new field, “isRankingMatch” was added to the “fields”, the graph stopped working correctly (only displayed a single point on a time-graph)
<!-- ![Problem 2](/assets/problem2.png "Problem 2") -->