Projects API
============

Projects represent individual applications on your Bugsnag account for which you are tracking errors.


Contents
--------

TODO


List Account's Projects
-----------------------

List all projects for the authenticated account.

```http
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
```json
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


Get Project Details
-------------------

Get the details of a single Bugsnag project.

```http
GET /projects/:project_id
```

### Response

```http
Status: 200 OK
```
```json
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





