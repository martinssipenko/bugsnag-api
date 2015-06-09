Activity Items API
==================

The Activity API allows you to get a feed of user and system actions for each [Error](error.md), eg. status changes and assignments.


Contents
--------
-   [The Activity Item object](#the-activity-item-object)
    -   [Fields](#fields)
    -   [Actions](#actions)
-   [List an Error's Activity Items](#list-an-error-s-activity-items)


The Activity Item object
------------------------

### Fields

The following fields are present on Activity Item responses.

Name                | Description
------------------- | -----------
`action`            | The type of activity that occurred, eg `commented`, `snoozed` (see [actions](#actions) for the full list)
`actor`             | The user who performed the action, or "system" if this was a system action
`created_at`        | When this activity occurred, in [ISO8601](http://en.wikipedia.org/wiki/ISO_8601) format
`snooze_conditions` | Only for `snooze` actions. The conditions for snoozing this Error. For example: `{"dimension": "time", "target": "2013-08-06T00:24:50Z", "input": 21600}`
`assignee`          | Only for `assigned` and `reassigned` actions. The user who was assigned this Error.
`issue_tracker`     | Only for `issue_created` and `issue_linked` actions. The issue tracker name.
`issue_url`         | Only for `issue_created` and `issue_linked` actions. The URL of the linked issue.


### Actions

The following are valid actions which may be returned in the `action` field of a response.

Name             | Description
---------------- | -----------
`snoozed`        | A user marked this error as *snoozed*
`unsnoozed`      | The *snoozed* status was removed from this error, either by a user or because snooze conditions were matched
`fixed`          | A user marked this error as *fixed*
`unfixed`        | The *fixed* status was removed from this error, either by a user action or because the error occurred again in a new release
`ignored`        | A user marked this error as *ignored*
`unignored`      | The *ignored* status was removed from this error, by a user action
`first_seen`     | This error was seen for the first time
`assigned`       | The error was assigned to a Bugsnag user
`resassigned`    | The associated error was assigned to a different Bugsnag user
`unassigned`     | The associated error was un-assigned
`issue_created`  | An issue was created in your issue tracker for this error
`issue_linked`   | An existing issue from your issues tracker was linked to this error
`issue_unlinked` | The issue attached to this error was unlinked


List an Error's Activity
------------------------

Get a list of all activity for the specified Bugsnag [Error](errors.md).


### Request

```http
GET /errors/:error_id/activity
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
Link: <https://api.bugsnag.com/errors/50baed119bf39c1431000004/comments?offset=51f93d6af002c6686d058c49>; rel="next"
```
```json
[
  {
    "action": "snoozed",
    "actor": {
      "account_admin": true,
      "email": "james@example.com",
      "gravatar_id": "b05c5ca80cf9fe757efdaa9e2afe4a76",
      "gravatar_url": "https://secure.gravatar.com/avatar/b05c5ca80cf9fe757efdaa9e2afe4a76",
      "html_url": "https://bugsnag.com/accounts/example/users/james-smith/edit",
      "id": "515fb9337c1074f6fd000007",
      "name": "James Smith",
      "projects_url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007/projects",
      "url": "https://api.bugsnag.com/users/515fb9337c1074f6fd000007"
    },
    "snooze_conditions": {
      "dimension": "time",
      "target": "2013-08-06T00:24:50Z",
      "input": "21600"
    },
    "created_at": "2013-08-06T00:24:50Z"
  }
]
```
