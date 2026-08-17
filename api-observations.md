# API observations

## /users/khairulezwan2015-code
- status: 200
- content-type: application/json; charset=utf-8
- unexpected field: `node_id` (an internal GitHub identifier, format `U_kgDODsWldQ`) and `gravatar_id` (empty string when user has no Gravatar)

## /repos/khairulezwan2015-code/git-practice
- status: 404
- content-type: application/json; charset=utf-8
- unexpected field: none — the response is a `Not Found` error object (`message`, `documentation_url`, `status`)
- note: this repo is private, so unauthenticated API calls return 404 instead of 200. An authenticated request with a token would return the repo metadata.

## /repos/khairulezwan2015-code/git-practice/commits
- status: 404
- content-type: application/json; charset=utf-8
- unexpected field: none — same 404 error object
- note: same reason — repo is private. The endpoint would otherwise return an array of commit objects with fields like `sha`, `commit.message`, `commit.author`, `commit.tree`.

## Key insight
GitHub's public API hides private repos by returning 404 instead of leaking their existence. Without authentication, you cannot tell whether a repo doesn't exist or is private — both look the same.
