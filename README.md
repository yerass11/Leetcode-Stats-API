# Leetcode-api

Leetcode API provides a collection of GraphQL queries to interact with Leetcode's GraphQL endpoint. These queries allow you to retrieve various data from Leetcode, such as user profiles and problem sets. This repository serves as a reference for developers who want to integrate Leetcode data into their applications or automate data retrieval processes.

## Getting Started

To start using the Leetcode API GraphQL queries, you need to set up a tool or environment that can send GraphQL requests. Popular tools include:

**Insomnia** or **Postman**

**Insomnia**: A powerful HTTP and GraphQL client.
**Postman**: Another versatile API client that supports GraphQL.
**GraphQL Clients in Code**: Libraries such as requests in Python can be used to send GraphQL queries programmatically.

### Insomnia http request: **"https://leetcode.com/graphql/"**

## GraphQL Queries

### 1. Get User Profile
Retrieve the profile information and submission statistics of a specific Leetcode user.

### Query:
```graphql
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

### Query Variables:
```json
{
  "username": "YOUR_USERNAME"
}

```

### 2. Get Problem Set Question List
Fetch a list of problems from the Leetcode problem set with various filters.

### Query:
```graphql
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

### Query Variables:
```json
{
  "categorySlug": "",
  "skip": 0,
  "limit": 50,
  "filters": {}
}
```

## Sample Responses

### 1. Get User Profile Response
```json
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

### 2. Get Problem Set Question List Response
```json
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
      ]
    }
  }
}
```

## Usage

- ### With Insomnia
#### Insomnia is a popular tool for testing APIs, including GraphQL endpoints. Here's how you can use Insomnia to execute the provided GraphQL queries.

**Steps:**

- **Open Insomnia and create a new request.**
- **Set the Request Type to POST.**
- **Set the URL to https://leetcode.com/graphql/.**
- **Under the Body tab, select GraphQL.**
- **Enter the Query in the Query section.**
- **Provide Query Variables in the Variables section.**
- **Send the Request to receive the response.**

Example:
- **URL: https://leetcode.com/graphql/**
- **Method: POST**
- **Body:**
	- **Type: GraphQL**
	- **Query: (Insert the desired query here)**
	- **Variables: (Insert the corresponding variables here)****


