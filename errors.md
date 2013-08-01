Errors API
----------

List errors on a project
------------------------

Bugsnag represents groups of similar exceptions as what we call *errors*. This request allows you to get a list of all errors under a particular project.

```
GET /projects/:project_id/errors
```

### Response
```
Status: 200 OK
Link: <https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors?offset=1375288557>; rel="next"
```

```javascript
[
  {
    "id": "518031bcd775355c48a1cd4e",
    "contexts": { "mailer#admin": 12 },
    "errorClass": "NoMethodError",
    "lastMessage": "undefined method `name' for nil:NilClass",
    "occurrences": 12,
    "usersAffected": 13,
    "releaseStages": { "production": 12 },
    "firstReceived": "2013-04-30T21:03:56Z",
    "lastReceived": "2013-07-29T10:42:05Z",
    "commentsUrl": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/comments",
    "eventsUrl": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e/events",
    "htmlUrl": "https://bugsnag.com/errors/518031bcd775355c48a1cd4e",
    "url": "https://api.bugsnag.com/errors/518031bcd775355c48a1cd4e"
  }
]
```