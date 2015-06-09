Accounts API
============

The Accounts API allows you to get information about Bugsnag accounts. Accounts normally represent a company or individual, can contain many [Projects](projects.md) and many [Users](users.md) can have access to the Account.

Contents
--------

-   [The Account object](#the-account-object)
-   [List your Accounts](#list-your-accounts)
-   [Get the authenticated Account](#get-the-authenticated-account)
-   [Get Account details](#get-account-details)


The Account object
------------------

The following fields are present on Account responses:

Name              | Description
----------------- | -----------
`id`              | The ID of this account, eg *515fb9337c1074f6fd000009*
`name`            | The name of this account, eg *Acme Co.*
`slug`            | The URL-friendly name for this account, eg *acme-co*
`account_creator` | A [User](user.md) object representing the User who created this Account
`billing_contact` | A [User](user.md) object representing the billing contact for this account
`url`             | The API URL to fetch this Account resource
`users_url`       | The API URL to fetch a list of [Users](users.md) who have access to this Account
`projects_url`    | The API URL to fetch a list of [Projects](projects.md) on this account
`created_at`      | When this Account was created, in [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) format
`updated_at`      | When this Account was updated, in [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) format


List your Accounts
------------------

Get a list of all Accounts accessible by the authenticated [User](users.md) or Account.

### Request

```http
GET /accounts
```

### Parameters

Name        | Description
----------- | -----------
`sort`      | What to sort results by. Can be only `created_at`. Default: `created_at`
`direction` | The direction of the sort. Can be either `asc` or `desc`. Default: `desc`
`per_page`  | How many results to return per page. Default: `30`

### Response Example

```http
Status: 200 OK
Link: <https://api.bugsnag.com/accounts?offset=50baee27a43ccdf778000002>; rel="next"
X-Total-Count: 123
```
```json
[
  {
    "id": "515fb9337c1074f6fd000009",
    "name": "Example",
    "slug": "example",
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
    "url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009",
    "users_url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009/users",
    "projects_url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009/users",
    "created_at": "2013-04-06T05:57:07Z",
    "updated_at": "2013-07-29T17:46:11Z"
  }
]
```


Get the authenticated Account
-----------------------------

*Note: Only available when authenticated with account credentials.*

Get the details of the currently authenticated Bugsnag Account.

### Request

```http
GET /account
```

### Response Example

```http
Status: 200 OK
```
```json
{
  "id": "515fb9337c1074f6fd000009",
  "name": "Example",
  "slug": "example",
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
  "url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009",
  "users_url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009/users",
  "projects_url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009/users",
  "created_at": "2013-04-06T05:57:07Z",
  "updated_at": "2013-07-29T17:46:11Z"
}
```


Get Account details
-------------------

Get the details of the specified Bugsnag Account.

### Request

```http
GET /account/:account_id
```

### Response Example

```http
Status: 200 OK
```
```json
{
  "id": "515fb9337c1074f6fd000009",
  "name": "Example",
  "slug": "example",
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
  "url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009",
  "users_url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009/users",
  "projects_url": "https://api.bugsnag.com/accounts/515fb9337c1074f6fd000009/users",
  "created_at": "2013-04-06T05:57:07Z",
  "updated_at": "2013-07-29T17:46:11Z"
}
```
