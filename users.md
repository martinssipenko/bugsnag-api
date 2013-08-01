Users API
=========

The Users API allows you to get information about Bugsnag users. Users are people who can sign-in and view errors on Bugsnag, and are part of one or more [Accounts](accounts).


Contents
--------

- [List your Account's Users](#list-your-account-s-users)
- [List a Project's Users](#list-a-project-s-users)
- [Get User details](#get-user-details)
- [Invite a User to an Account](#invite-a-user-to-an-account)
- [Delete a User from an Account](#delete-a-user-from-an-account)
- [Update a User's Account permissions](#update-a-user-s-account-permissions)


List your Account's Users
-------------------------

Get a list of all Users with access to the currently authenticated Bugsnag [Account](accounts).

```http
GET /account/users
```

### Parameters

- **sort** - `createdAt`. Default `createdAt`.
- **direction** - `asc`, `desc`. Default `desc`.
- **per_page** - how many results to return per page. Default 30.

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/users?offset=517c41f07c1074aee9000002>; rel="next"
```
```json
[
  {
    "id": "517c41f07c1074aee9000002",
    "name": "James Smith",
    "accountAdmin": true,
    "email": "james@example.com",
    "gravatarUrl": "https://secure.gravatar.com/avatar/9ceeacde2574676c9ef60437aaaa20b",
    "htmlUrl": "https://bugsnag.com/accounts/bugsnag/users/james-plus-test2-at-bugsnag-dot-com/edit",
    "projectsUrl": "https://api.bugsnag.com/users/517c41f07c1074aee9000002/projects",
    "url": "https://api.bugsnag.com/users/517c41f07c1074aee9000002"
  }
]
```


List a Project's Users
---------------------

Get a list of Users with access to the specified [Project](projects).

```http
GET /projects/:project_id/users
```

### Parameters

- **sort** - `createdAt`. Default `createdAt`.
- **direction** - `asc`, `desc`. Default `desc`.
- **per_page** - how many results to return per page. Default 30.

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/projects/517c41f07c1074aee9000002/users?offset=517c41f07c1074aee9000002>; rel="next"
```
```json
[
  {
    "id": "517c41f07c1074aee9000002",
    "name": "James Smith",
    "accountAdmin": true,
    "email": "james@example.com",
    "gravatarUrl": "https://secure.gravatar.com/avatar/9ceeacde2574676c9ef60437aaaa20b",
    "htmlUrl": "https://bugsnag.com/accounts/bugsnag/users/james-plus-test2-at-bugsnag-dot-com/edit",
    "projectsUrl": "https://api.bugsnag.com/users/517c41f07c1074aee9000002/projects",
    "url": "https://api.bugsnag.com/users/517c41f07c1074aee9000002"
  }
]
```


Get User details
----------------

Get the details about a Bugsnag user, including name and email address. You can only view details for Users on the currently authenticated Bugsnag [Account](accounts).

```http
GET /users/:user_id
```

### Response

```http
Status: 200 OK
```
```json
{
  "id": "517c41f07c1074aee9000002",
  "name": "James Smith",
  "accountAdmin": true,
  "email": "james@example.com",
  "gravatarUrl": "https://secure.gravatar.com/avatar/9ceeacde2574676c9ef60437aaaa20b",
  "htmlUrl": "https://bugsnag.com/accounts/bugsnag/users/james-plus-test2-at-bugsnag-dot-com/edit",
  "projectsUrl": "https://api.bugsnag.com/users/517c41f07c1074aee9000002/projects",
  "url": "https://api.bugsnag.com/users/517c41f07c1074aee9000002"
}
```


Invite a User to an Account
---------------------------

Invite a user to become a member of the currently authenticated Bugsnag [Account](accounts).

```http
POST /account/users
```

### Parameters

- **email** - the email address of the person to invite

### Response

```http
Status: 201 Created
```
```json
TODO: Response json (the new or existing user object)
```


Delete a user from an Account
-----------------------------

Remove a user from the currently authenticated Bugsnag [Account](accounts).

```http
DELETE /account/users/:user_id
````

### Response

```http
Status: 204 No Content
```


Update a User's Account permissions
-----------------------------------

Update a User's Account permissions, including Project access and Account admin status.

```http
PATCH /account/users/:user_id
```

### Parameters

- TODO

### Response

```http
Status: 200 OK
```
```json
TODO: Response json (the updated user object)
```