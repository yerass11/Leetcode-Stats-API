# Leetcode-api

## These leetcode GraphQL queries can help you get the various data from the leetcode's GraphQL endpoint.


### Insomnia http request: "https://leetcode.com/graphql/"


#### query:
body -> GraphQL -> query
```
query getUserProfile($username: String!) {
  matchedUser(username: $username) {
    username
    submitStats: submitStatsGlobal {
      acSubmissionNum {
        difficulty
        count
      }
    }
  }
}
```
#### query variables:
{
	"username": "YOUR_USERNAME"
}

#### Sample Response:
```
{
	"data": {
		"matchedUser": {
			"username": "ais1ee",
			"submitStats": {
				"acSubmissionNum": [
					{
						"difficulty": "All",
						"count": 254
					},
					{
						"difficulty": "Easy",
						"count": 184
					},
					{
						"difficulty": "Medium",
						"count": 66
					},
					{
						"difficulty": "Hard",
						"count": 4
					}
				]
			}
		}
	}
}
```

#### query:
```
query problemsetQuestionList($categorySlug: String, $limit: Int, $skip: Int, $filters: QuestionListFilterInput) {
  problemsetQuestionList: questionList(
    categorySlug: $categorySlug
    limit: $limit
    skip: $skip
    filters: $filters
  ) {
    total: totalNum
    questions: data {
      acRate
      difficulty
      freqBar
      frontendQuestionId: questionFrontendId
      isFavor
      paidOnly: isPaidOnly
      status
      title
      titleSlug
      topicTags {
        name
        id
        slug
      }
      hasSolution
      hasVideoSolution
    }
  }
}
```
#### query variables:
```
{"categorySlug": "", "skip": 0, "limit": 50, "filters": {}}
```

#### Sample Response:
```
{
	"data": {
		"problemsetQuestionList": {
			"total": 3166,
			"questions": [
				{
					"acRate": 52.6721723918133,
					"difficulty": "Easy",
					"freqBar": null,
					"frontendQuestionId": "1",
					"isFavor": false,
					"paidOnly": false,
					"status": null,
					"title": "Two Sum",
					"titleSlug": "two-sum",
					"topicTags": [
						{
							"name": "Array",
							"id": "VG9waWNUYWdOb2RlOjU=",
							"slug": "array"
						},
						{
							"name": "Hash Table",
							"id": "VG9waWNUYWdOb2RlOjY=",
							"slug": "hash-table"
						}
					],
					"hasSolution": true,
					"hasVideoSolution": true
				},
      ...
```
