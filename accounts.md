Accounts API
============

The Accounts API allows you to get information about Bugsnag accounts. Accounts normally represent a company or individual, can contain many [Projects](projects) and many [Users](users) can have access to the Account.

Contents
--------
- [Get your account details](#get-your-account-details)
- [Get your account usage](#get-your-account-usage)


Get your account details
------------------------

Get details about your account, including name and current billing plan.

```
GET /account
```

### Response
```json
{
  "TODO": "response goes here"
}
```


Get Account usage
-----------------

Get information about your current account usage.

```
GET /account/usage
```

### Response
```json
{
  "TODO": "response goes here"
}
```