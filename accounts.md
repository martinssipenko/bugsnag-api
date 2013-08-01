Accounts API
============

The Accounts API allows you to get information about Bugsnag accounts. Accounts normally represent a company or individual, can contain many [Projects](projects) and many [Users](users) can have access to the Account.

Contents
--------
- [Get Account details](#get-account-details)
- [Get Account usage](#get-account-usage)


Get Account details
-------------------

Get details for the currently authenticated Account, including name and current billing plan.

```http
GET /account
```

### Response
```json
{
  "id": "515fb9337c1074f6fd000009",
  "name": "Bugsnag",
  "accountCreator": {
    "id": "515fb9337c1074f6fd000003",
    "name": "Bob Hoskins",
    "accountAdmin": true,
    "email": "bob@example.com",
    "gravatarUrl": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  },
  "billingContact": {
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith",
    "accountAdmin": true,
    "email": "james@example.com",
    "gravatarUrl": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a71",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  },
  "createdAt": "2013-04-06T05:57:07Z",
  "updatedAt": "2013-07-29T17:46:11Z"
}
```


Get Account usage
-----------------

Get information about your current account usage.

```http
GET /account/usage
```

### Response
```json
{
  "TODO": "response goes here"
}
```