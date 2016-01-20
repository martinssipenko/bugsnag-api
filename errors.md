Errors API
============

Bugsnag represents groups of similar exceptions as what we call *Errors*. The Errors API allows you to update, delete and get detailed information about Bugsnag Errors.


Contents
--------

- [List a Project's Errors](#list-a-project-s-errors)
- [Get Error details](#get-error-details)
- [Get Error trend](#get-error-trend)
- [Update an Error's status](#update-an-error-s-status)
- [Delete an Error](#delete-an-error)


The Error object
----------------

The following fields are present on Error responses:

Name                | Description
--------------------| -----------
`id`                | The ID of this error, eg *515fb9337c1074f6fd000009*
`error_class`       | The class of the latest exception grouped under this error (not filtered)
`message`           | The latest error message for this error (not filtered)
`context`           | The latest context where this error occurred (not filtered)
`events`            | The number of occurrences of this error (respects filters)
`users`             | The number of users who saw this error (respects filters)
`first_seen`        | When this error was first seen, in [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) format (respects filters)
`last_seen`         | When this error was last seen, in [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) format (respects filters)
`status`            | The current status of this error (`open`, `snoozed`, `fixed` or `ignored`)
`snooze_conditions` | Only in `snoozed` status. The conditions for snoozing this error.
`assigned_user`     | The Bugsnag User (if any) who has been assigned this error
`linked_issue`      | The external issue (if any) in your issue tracker linked to this error
`latest_event`      | The most recent Event seen for this error (respects filters)
`trend`             | 2-week trend information TODO


List a Project's Errors
-----------------------

Get a list of all errors (grouped exceptions) for the specified Bugsnag [Project](projects.md).


### Request

```http
GET /projects/:project_id/errors
```


### Parameters

Name             | Description
---------------- | -----------
`sort`           | What to sort results by. Can be only `updated_at`. Default: `updated_at`
`direction`      | The direction of the sort. Can be either `asc` or `desc`. Default: `desc`
`per_page`       | How many results to return per page. Default: `30`
`filters`        | Filters to apply to the query, see [filtering errors, events or pivots](filters.md#filtering-errors-events-or-pivots) for details


### Response Example

```http
Status: 200 OK
Link: <https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors?offset=1375288557>; rel="next"
X-Total-Count: 123
```
```json
[
  {
    "id": "518031bcd775355c48a1cd4e",
    "events": 456,
    "users": 123,
    "first_seen": "2013-04-30T21:03:56Z",
    "last_seen": "2013-04-30T21:03:56Z",
    "status": "snoozed",
    "snooze_conditions": {
      "dimension": "time",
      "target": "2013-04-30T21:03:56Z",
      "input": 21600
    },
    "assigned_user": {
      "id": "518031bcd775355c48a1cd4e",
      "name": "TODO"
    },
    "linked_issue": {
      "id": 123,
      "url": "http://google.com",
      "system": "GitHub Issues"
    },
    "trend": [
      ["2015-05-27T00:00:00.000Z", 123],
      ["2015-05-27T00:00:00.000Z", 456]
    ],
    "latest_event": {
      "id": "551c5888093024ce168bdfca",
      "error_class": "Moped::Errors::QueryFailure",
      "message": "Something bad happened",
      "context": "api/accounts#index",
      "release_stage": "production",
      "severity": "error"
    }
  }
]
```


Get Error details
-----------------

Get the details of the given Bugsnag Error.


### Request

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
  "error_class": "RuntimeError",
  "message": "No such connection",
  "context": "dashboard/home#index",
  "events": 456,
  "users": 123,
  "first_seen": "2013-04-30T21:03:56Z",
  "last_seen": "2013-04-30T21:03:56Z",
  "status": "snoozed",
  "snooze_conditions": {
    "dimension": "time",
    "target": "2013-04-30T21:03:56Z",
    "input": 21600
  },
  "assigned_user": {
    "id": "518031bcd775355c48a1cd4e",
    "name": "TODO"
  },
  "linked_issue": {
    "id": 123,
    "url": "http://google.com",
    "system": "GitHub Issues"
  },
  "trend": [
    ["2015-05-27T00:00:00.000Z", 123],
    ["2015-05-27T00:00:00.000Z", 456]
  ],
  "latest_event": {
    "id": "551c5888093024ce168bdfca",
    "error_class": "Moped::Errors::QueryFailure",
    "message": "Something bad happened",
    "context": "api/accounts#index",
    "release_stage": "production",
    "severity": "error"
  }
}
```

Get Error trend
-----------------

Get counts of error occurrences between two times, divided into n buckets.

### Request

```http
GET /errors/:error_id/trend
```

### Parameters

Name             | Description
---------------- | -----------
`buckets_count`  | How many buckets to use to group the error occurrence counts. Allowed values are 1 to 50.

By default, trend data will be returned from the time that the error was first seen to the current time. The time range under consideration can be modified using the `event.since` and `event.before` [Filters](filters.md).


### Response

```http
Status: 200 OK
```
```json
[
  ["2015-01-01T08:00:00Z", 0],
  ["2015-01-01T16:00:00Z", 4],
  ["2015-01-02T00:00:00Z", 8],
  ["2015-01-02T08:00:00Z", 0]
]
```


TODO: Update an Error's status
------------------------

Update the status (resolved, unresolved, etc) of an Error.

```http
PATCH /errors/:error_id
```

### Parameters

Name       | Description
---------- | -----------
`resolved` | The new status for this error, can be either `true` or `false`

### Response

```http
Status: 200 OK
```
```json
{
  "id": "518031bcd775355c48a1cd4e",
  "events": 456,
  "users": 123,
  "first_seen": "2013-04-30T21:03:56Z",
  "last_seen": "2013-04-30T21:03:56Z",
  "status": "snoozed",
  "snooze_conditions": {
    "dimension": "time",
    "target": "2013-04-30T21:03:56Z",
    "input": 21600
  },
  "assigned_user": {
    "id": "518031bcd775355c48a1cd4e",
    "name": "TODO"
  },
  "linked_issue": {
    "id": 123,
    "url": "http://google.com",
    "system": "GitHub Issues"
  },
  "trend": [
    ["2015-05-27T00:00:00.000Z", 123],
    ["2015-05-27T00:00:00.000Z", 456]
  ],
  "latest_event": {
    "id": "551c5888093024ce168bdfca",
    "error_class": "Moped::Errors::QueryFailure",
    "message": "Something bad happened",
    "context": "api/accounts#index",
    "release_stage": "production",
    "severity": "error"
  }
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
