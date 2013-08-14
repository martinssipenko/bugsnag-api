Errors API
============

Bugsnag represents groups of similar exceptions as what we call *Errors*. The Errors API allows you to update, delete and get detailed information about Bugsnag Errors.


Contents
--------

- [List a Project's Errors](#list-a-project-s-errors)
- [Get Error details](#get-error-details)
- [Update an Error's status](#update-an-error-s-status)
- [Delete an Error](#delete-an-error)


List a Project's Errors
-----------------------

Get a list of all errors (grouped exceptions) for the given Bugsnag [Project](projects).

```http
GET /projects/:project_id/errors
```

### Parameters

- **sort** - `created_at`. Default: `created_at`.
- **direction** - `asc`, `desc`. Default `desc`.
- **per_page** - how many results to return per page. Default 30.

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors?offset=1375288557>; rel="next"
```
```json
[
  {
    "id": "518031bcd775355c48a1cd4e",
    "class": "NoMethodError",
    "last_message": "undefined method `name' for nil:NilClass",
    "last_context": "mailer#admin",
    "resolved": false,
    "occurrences": 12,
    "users_affected": 13,
    "contexts": {
      "mailer#admin": 12
    },
    "release_stages": {
      "production": 12
    },
    "first_received": "2013-04-30T21:03:56Z",
    "last_received": "2013-07-29T10:42:05Z",
    "comments_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/comments",
    "events_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/events",
    "html_url": "https://bugsnag.com/errors/518031bcd775355c48a1cd4e",
    "url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e"
  }
]
```


Get Error details
-----------------

Get the details of the given Bugsnag Error.

```http
GET /errors/:error_id
```

### Response

```http
Status: 200 OK
```
```json
{
  "id": "518031bcd775355c48a1cd4e",
  "class": "NoMethodError",
  "last_message": "undefined method `name' for nil:NilClass",
  "last_context": "mailer#admin",
  "resolved": false,
  "occurrences": 12,
  "users_affected": 13,
  "contexts": {
    "mailer#admin": 12
  },
  "release_stages": {
    "production": 12
  },
  "first_received": "2013-04-30T21:03:56Z",
  "last_received": "2013-07-29T10:42:05Z",
  "comments_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/comments",
  "events_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/events",
  "html_url": "https://bugsnag.com/errors/518031bcd775355c48a1cd4e",
  "url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e"
}
```


Update an Error's status
------------------------

Update the status (resolved, unresolved, etc) of an Error.

```http
PATCH /errors/:error_id
```

### Parameters

- **resolved** - `true`, `false`

### Response

```http
Status: 200 OK
```
```json
{
  "id": "518031bcd775355c48a1cd4e",
  "class": "NoMethodError",
  "last_message": "undefined method `name' for nil:NilClass",
  "last_context": "mailer#admin",
  "resolved": false,
  "occurrences": 12,
  "users_affected": 13,
  "contexts": {
    "mailer#admin": 12
  },
  "release_stages": {
    "production": 12
  },
  "first_received": "2013-04-30T21:03:56Z",
  "last_received": "2013-07-29T10:42:05Z",
  "comments_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/comments",
  "events_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/events",
  "html_url": "https://bugsnag.com/errors/518031bcd775355c48a1cd4e",
  "url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e"
}
```


Delete an Error
---------------

Delete an Error and all associated [Events](events) from Bugsnag.

```http
DELETE /errors/:error_id
```

### Response

```http
Status: 204 No Content
```