Users API
=========

The Users API allows you to get information about Bugsnag users. Users are people who can sign-in and view errors on Bugsnag, and are part of one or more [Accounts](accounts).


Contents
--------

- [List your Account's Users](#list-your-account-s-users)
- [Get User details](#get-user-details)
- [List a Project's Users](#list-a-project-s-users)
- [Invite a User to an Account](#invite-a-user-to-an-account)
- [Delete a user from an Account](#delete-a-user-from-an-account)
- [Update a user's Account permissions](#update-a-user-s-account-permissions)


List your Account's Users
-------------------------

Description TODO

```
GET /account/users
```

### Parameters

- TODO

### Response

```
TODO: Response headers
```

```json
{
  "TODO": "response"
}
```


Get User details
----------------

Description TODO

```
GET /users/:user_id
```

###Response

```
TODO: Response headers
```

```json
{
  "TODO": "response"
}
```


List a Project's Users
---------------------

Description TODO

```
GET /projects/:project_id/users
```

### Response

```
TODO: Response headers
```

```json
{
  "TODO": "response"
}
```


Invite a User to an Account
---------------------------

Description TODO

```
POST /account/users
```

### Response

```
TODO: Response headers
```

```json
{
  "TODO": "response"
}
```