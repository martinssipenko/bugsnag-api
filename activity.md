Activity API
============

The Activity API allows you to get a feed of user and system actions for each Error, for example, comments, status changes and assignments.


Contents
--------

- [List an Error's Activity](#list-an-error-s-activity)


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


### Response Fields

Name             | Description
---------------- | -----------
`action`         | The type of activity that occurred, eg `commented`, `snoozed` (see [actions](#actions) for the full list)
`actor`          | The user who performed the action, or "system" if this was a system action
`created_at`     | When this activity occurred, in [ISO8601](http://en.wikipedia.org/wiki/ISO_8601) format


### Actions

Name             | Description
---------------- | -----------
`commented`      | A user added a comment to this error (see `comment_body`)
`snoozed`        | A user marked this error as snoozed (see `snooze_conditions`)
`unsnoozed`      | TODO
`fixed`          | TODO
`unfixed`        | TODO
`ignored`        | TODO
`unignored`      | TODO
`first_seen`     | TODO
`assigned`       | TODO
`resassigned`    | The associated error was assigned to a different Bugsnag user (see `assignee`)
`unassigned`     | The associated error was un-assigned.
`issue_created`  | An issue was created for this error in your issue tracker.
`issue_linked`   | An existing issue from your issues tracker was linked to this error.
`issue_unlinked` | The issue attached to this error was unlinked.


### Response Example

```http
Status: 200 OK
Link: <https://api.bugsnag.com/errors/50baed119bf39c1431000004/comments?offset=51f93d6af002c6686d058c49>; rel="next"
```
```json
{
  "total_count": 11,
  "items": [
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
}
```
