Accounts API
============

The Accounts API allows you to get information about Bugsnag accounts. Accounts normally represent a company or individual, can contain many [Projects](projects.md) and many [Users](users.md) can have access to the Account.

Contents
--------

- [Get Account details](#get-account-details)


Get Account details
-------------------

Get details for the currently authenticated Account.

```http
GET /account
```

### Response

```http
Status: 200 OK
```
```json
{
  "id": "515fb9337c1074f6fd000009",
  "name": "Example",
  "account_creator": {
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith",
    "account_admin": true,
    "email": "james@example.com",
    "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a7",
    "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a7",
    "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  },
  "billing_contact": {
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith",
    "account_admin": true,
    "email": "james@example.com",
    "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a7",
    "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a7",
    "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
    "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
  },
  "created_at": "2013-04-06T05:57:07Z",
  "updated_at": "2013-07-29T17:46:11Z"
}
```