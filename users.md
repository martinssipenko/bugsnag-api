Users API
=========

The Users API allows you to get information about Bugsnag users. Users are people who can sign-in and view errors on Bugsnag. Users can be members of one or more [Accounts](accounts.md).


Contents
--------

- [List an Account's Users](#list-an-account-s-users)
- [List a Project's Users](#list-a-project-s-users)
- [Get User details](#get-user-details)
- [Get the authenticated User](#get-the-authenticated-user)
- [Invite a User to an Account](#invite-a-user-to-an-account)
- [Update a User's Account permissions](#update-a-user-s-account-permissions)
- [Delete a User from an Account](#delete-a-user-from-an-account)


List an Account's Users
-----------------------

Get a list of all Users with access to the specified Bugsnag [Account](accounts.md).

```http
GET /accounts/:account_id/users
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
Link: <https://api.bugsnag.com/users?offset=517c41f07c1074aee9000002>; rel="next"
```
```json
[
  {
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith",
    "account_admin": true,
    "email": "james@example.com",
    "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
    "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
    "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
    "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  }
]
```


List a Project's Users
---------------------

Get a list of Users with access to the specified [Project](projects.md).

```http
GET /projects/:project_id/users
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
Link: <https://api.bugsnag.com/projects/517c41f07c1074aee9000002/users?offset=517c41f07c1074aee9000002>; rel="next"
```
```json
[
  {
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith",
    "account_admin": true,
    "email": "james@example.com",
    "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
    "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
    "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
    "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  }
]
```


Get User details
----------------

Get the details about a Bugsnag user, including name and email address. You can only view details for Users in the same authentication scope.

```http
GET /users/:user_id
```

### Response

```http
Status: 200 OK
```
```json
{
  "id": "515fb9337c1074f6fd000007",
  "name": "James Smith",
  "account_admin": true,
  "email": "james@example.com",
  "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
  "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
  "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
  "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
  "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
}
```


Get the authenticated User
--------------------------

*Note: Only available when authenticated with user credentials.*

Get the details of the currently authenticated Bugsnag User.

```http
GET /user
```

### Response

```http
Status: 200 OK
```
```json
{
  "id": "515fb9337c1074f6fd000007",
  "name": "James Smith",
  "account_admin": true,
  "email": "james@example.com",
  "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
  "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
  "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
  "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
  "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
}
```


Invite a User to an Account
---------------------------

Invite a user to become a member of the specified Bugsnag [Account](accounts.md).

```http
POST /accounts/:account_id/users
```

### Parameters

Name          | Description
------------- | -----------
`email`       | The email address of the person to invite, eg ``james@example.com``
`admin`       | Should this person be an account admin? One of `true` or `false`. Default: `false`
`project_ids` | A comma separated list of project IDs this person can access


### Response

```http
Status: 201 Created
```
```json
{
  "id": "515fb9337c1074f6fd000007",
  "name": "James Smith",
  "account_admin": true,
  "email": "james@example.com",
  "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
  "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
  "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
  "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
  "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
}
```


Update a User's Account permissions
-----------------------------------

Update a User's Account permissions, including Project access and Account admin status. Responds with the newly updated User.

```http
PUT /accounts/:account_id/users/:user_id
```

### Parameters

Name          | Description
------------- | -----------
`admin`       | Should this person be an account admin? One of `true` or `false`. Default: `false`
`project_ids` | A comma separated list of project IDs this person can access

### Response

```http
Status: 200 OK
```
```json
{
  "id": "515fb9337c1074f6fd000007",
  "name": "James Smith",
  "account_admin": true,
  "email": "james@example.com",
  "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
  "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
  "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
  "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
  "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
}
```


Delete a user from an Account
-----------------------------

Remove a user from the specified Bugsnag [Account](accounts.md).

```http
DELETE /account/:account_id/users/:user_id
```

### Response

```http
Status: 204 No Content
```
