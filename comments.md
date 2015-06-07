Comments API
============

> TODO:JS: this needs to support both comments and activity

The Comments API allows you to get detailed information and delete comments on Bugsnag [Errors](errors.md).


Contents
--------

- [List an Error's Comments](#list-an-error-s-comments)
- [Get Comment details](#get-comment-details)
- [Create a Comment](#create-a-comment)
- [Update a Comment](#update-a-comment)
- [Delete a Comment](#delete-a-comment)


List an Error's Comments
------------------------

Get a list of all comments for the specified Bugsnag [Error](errors.md).

```http
GET /errors/:error_id/comments
```

### Parameters

Name        | Description
----------- | -----------
`sort`      | What to sort results by. Can be only `created_at`. Default: `created_at`
`direction` | The direction of the sort. Can be either `asc` or `desc`. Default: `desc`
`per_page`  | How many results to return per page. Default: `30`

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/errors/50baed119bf39c1431000004/comments?offset=51f93d6af002c6686d058c49>; rel="next"
```
```json
{
  "total_count": 123,
  "items": [
    {
      "id": "520042527c1074dced000017",
      "message": "This was my bug, fixed now",
      "user": {
        "account_admin": true,
        "email": "james@example.com",
        "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
        "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
        "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
        "id": "515fb9337c1074f6fd000007",
        "name": "James Smith",
        "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
        "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
      },
      "url": "https://api.bugsnag.com/comments/520042527c1074dced000017",
      "created_at": "2013-08-06T00:24:50Z"
    }
  ]
}
```


Get Comment details
-------------------

Get the details of the specified Comment.

```http
GET /comments/:comment_id
```

### Response

```http
Status: 200 OK
```
```json
{
  "id": "520042527c1074dced000017",
  "message": "This was my bug, fixed now",
  "user": {
    "account_admin": true,
    "email": "james@example.com",
    "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
    "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
    "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith",
    "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  },
  "url": "https://api.bugsnag.com/comments/520042527c1074dced000017",
  "created_at": "2013-08-06T00:24:50Z"
}
```

Create a Comment
----------------

*Note: Only available when authenticated with user credentials.*

Create a new Comment on the specified Bugsnag [Error](error.md).

```http
POST /errors/:error_id/comments
```

### Parameters

Name        | Description
----------- | -----------
`message`   | The text of the comment

### Response

```http
Status: 201 Created
```
```json
{
  "id": "520042527c1074dced000017",
  "message": "This was my bug, fixed now",
  "user": {
    "account_admin": true,
    "email": "james@example.com",
    "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
    "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
    "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith",
    "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  },
  "url": "https://api.bugsnag.com/comments/520042527c1074dced000017",
  "created_at": "2013-08-06T00:24:50Z"
}
```


Update a Comment
----------------

Update a Bugsnag Comments's message. Responds with the newly updated Project.

```http
PATCH /comments/:comment_id
```

### Parameters

Name        | Description
----------- | -----------
`message`   | The text of the comment

### Response

```http
Status: 200 OK
```
```json
{
  "id": "520042527c1074dced000017",
  "message": "This was my bug, fixed now",
  "user": {
    "account_admin": true,
    "email": "james@example.com",
    "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
    "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
    "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith",
    "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  },
  "url": "https://api.bugsnag.com/comments/520042527c1074dced000017",
  "created_at": "2013-08-06T00:24:50Z"
}
```


Delete a Comment
----------------

Delete a Comment from Bugsnag.

```http
DELETE /comments/:comment_id
```

### Response

```http
Status: 204 No Content
```
