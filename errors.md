Errors API
============

> TODO:JS: describe how to filter Events, Errors and Pivots

> TODO:JS: allow specifying which fields to return

Bugsnag represents groups of similar exceptions as what we call *Errors*. The Errors API allows you to update, delete and get detailed information about Bugsnag Errors.


Contents
--------

- [List a Project's Errors](#list-a-project-s-errors)
- [Get Error details](#get-error-details)
- [Update an Error's status](#update-an-error-s-status)
- [Delete an Error](#delete-an-error)


List a Project's Errors
-----------------------

Get a list of all errors (grouped exceptions) for the specified Bugsnag [Project](projects.md).

```http
GET /projects/:project_id/errors
```

### Parameters

Name             | Description
---------------- | -----------
`release_stages` | Only errors on the given release stages are returned, eg `production` or `production,staging`
`app_versions`   | Only errors affecting the given app versions are returned, eg `eq1.0.0` (errors affecting 1.0.0), `gte1.0.1` (errors affecting >= 1.0.1)
`severity`       | Only errors with the given severities are returned, eg `error` or `error,warning`
`status`         | Only errors with the given status are returned, eg `open`
`sort`           | What to sort results by. Can be only `updated_at`. Default: `updated_at`
`direction`      | The direction of the sort. Can be either `asc` or `desc`. Default: `desc`
`per_page`       | How many results to return per page. Default: `30`
`most_recent_event` | Include the most recent event for every error in the response

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
    "app_versions": {
      "1.0.0": 20
    },
    "first_received": "2013-04-30T21:03:56Z",
    "last_received": "2013-07-29T10:42:05Z",
    "comments_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/comments",
    "events_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/events",
    "html_url": "https://bugsnag.com/errors/518031bcd775355c48a1cd4e",
    "url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e",
    "most_recent_event": {}
  }
]
```


Get Error details
-----------------

Get the details of the given Bugsnag Error.

```http
GET /errors/:error_id
```

### Parameters

Name             | Description
---------------- | -----------
`most_recent_event` | Include the most recent event for every error in the response

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
  "app_versions": {
    "1.0.0": 20
  },
  "first_received": "2013-04-30T21:03:56Z",
  "last_received": "2013-07-29T10:42:05Z",
  "comments_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/comments",
  "events_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/events",
  "html_url": "https://bugsnag.com/errors/518031bcd775355c48a1cd4e",
  "url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e",
  "most_recent_event": {}
}
```


Update an Error's status
------------------------

Update the status (resolved, unresolved, etc) of an Error.

```http
PATCH /errors/:error_id
```

### Parameters

Name       | Description
---------- | -----------
`resolved` | The new status for this error, can be either `true` or `false`
`most_recent_event` | Include the most recent event for every error in the response

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
  "app_versions": {
    "1.0.0": 20
  },
  "first_received": "2013-04-30T21:03:56Z",
  "last_received": "2013-07-29T10:42:05Z",
  "comments_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/comments",
  "events_url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/events",
  "html_url": "https://bugsnag.com/errors/518031bcd775355c48a1cd4e",
  "url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e",
  "most_recent_event": {}
}
```


Delete an Error
---------------

Delete an Error and all associated [Events](events.md) from Bugsnag.

```http
DELETE /errors/:error_id
```

### Response

```http
Status: 204 No Content
```
