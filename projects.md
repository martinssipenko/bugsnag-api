Projects API
============

Projects represent individual applications on your Bugsnag account for which you are tracking errors.


List account projects
---------------------

List all projects for the authenticated account.

```shell
GET /projects
```

### Parameters

- **sort** - `createdAt`. Default: `createdAt`.
- **direction** - `asc`, `desc`. Default `desc`.
- **per_page** - how many results to return per page. Default 30.

### Response

```
Status: 200 OK
Link: <https://api.bugsnag.com/projects?offset=50baee27a43ccdf778000002>; rel="next"
```

```javascript
[
  {
    "apiKey": "a0f5e56c125d2eeac31fd66e4f0cbd79",
    "createdAt": "2012-12-02T05:54:25Z",
    "errors": 78,
    "errorsUrl": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors",
    "eventsUrl": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/events",
    "frameworkIcon": "https://bugsnag.com/assets/frameworks/rails.png",
    "htmlUrl": "https://bugsnag.com/dashboard/website",
    "id": "50baed119bf39c1431000004",
    "name": "Website",
    "releaseStages": ["production", "development"],
    "type": "rails",
    "updatedAt": "2013-06-17T19:57:49Z",
    "url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004"
  }
]
```


Get a project
-------------

Get the details of a single Bugsnag project.

```shell
GET /projects/:project_id
```

### Response

```
Status: 200 OK
```

```javascript
{
  "apiKey": "a0f5e56c125d2eeac31fd66e4f0cbd79",
  "createdAt": "2012-12-02T05:54:25Z",
  "errors": 78,
  "errorsUrl": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors",
  "eventsUrl": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/events",
  "frameworkIcon": "https://bugsnag.com/assets/frameworks/rails.png",
  "htmlUrl": "https://bugsnag.com/dashboard/website",
  "id": "50baed119bf39c1431000004",
  "name": "Website",
  "releaseStages": ["production", "development"],
  "type": "rails",
  "updatedAt": "2013-06-17T19:57:49Z",
  "url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004"
}
```


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


Get events on a project
-----------------------

This request allows you to get a list of each exception event for a particular project.

```
GET /projects/:project_id/events
```

### Response
```
Status: 200 OK
Link: <https://api.bugsnag.com/projects/50baed119bf39c1431000004/events?offset=51f93d6af002c6686d058c49>; rel="next"
```

```javascript
[
  {
    "id": "51f5d152f002c6686d013a22",
    "exceptions": [
      {
        "errorClass": "ActionView::Template::Error",
        "message": "source sequence is illegal/malformed utf-8",
        "stacktrace": [
          {
            "lineNumber": 285,
            "columNumber": 20,
            "file": "app/models/user.rb",
            "method": "generate"
          },
        ]
      },
    ],
    "userId": "5164f626a43ccd384400000b",
    "context": "events#show",
    "appVersion": "1.0.1",
    "osVersion": "Windows Vista",
    "metaData": { ... },
    "url": "https://api.bugsnag.com/events/51f5d152f002c6686d013a22",
    "htmlUrl": "https://bugsnag.com/errors/51f5cbadcf4cfd7373c8cc2d/events/51f5d152f002c6686d013a22"
  }
]
```