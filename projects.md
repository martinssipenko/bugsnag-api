Projects API
============

The Projects API allows you to create, modify, delete and get detailed information about Bugsnag projects. Projects represent individual applications on your Bugsnag account for which you are tracking errors.


Contents
--------

- [List your Account's Projects](#list-your-account-s-projects)
- [List a User's Projects](#list-a-user-s-projects)
- [Get Project details](#get-project-details)
- [Create a Project](#create-a-project)
- [Update a Project](#update-a-project)
- [Delete a Project](#delete-a-project)


List an Account's Projects
--------------------------

Get a list of all Projects for the specified Bugsnag [Account](accounts.md).

```http
GET /accounts/:account_id/projects
```

### Parameters

Name        | Description
----------- | -----------
`sort`      | What to sort results by. Can be only `created_at`. Default: `created_at`
`direction` | The direction of the sort. Can be either `asc` or `desc`. Default: `desc`
`per_page`  | How many results to return per page. Default: `30`

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/accounts/70baea119bf39c1431000004/projects?offset=50baee27a43ccdf778000002>; rel="next"
```
```json
[
  {
    "id": "50baed119bf39c1431000004",
    "name": "Website",
    "api_key": "a0f5e56c125d2eeac31fd66e4f0cbd79",
    "errors": 78,
    "icon": "https://bugsnag.com/assets/frameworks/rails.png",
    "release_stages": ["production", "development"],
    "type": "rails",
    "created_at": "2012-12-02T05:54:25Z",
    "updated_at": "2013-06-17T19:57:49Z",
    "errors_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors",
    "events_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/events",
    "html_url": "https://bugsnag.com/dashboard/website",
    "url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004"
  }
]
```


List a User's Projects
----------------------

Get a list of Projects that the specified Bugsnag [User](users.md) has access to.

```http
GET /user/:user_id/projects
```

### Parameters

Name        | Description
----------- | -----------
`sort`      | What to sort results by. Can be only `created_at`. Default: `created_at`
`direction` | The direction of the sort. Can be either `asc` or `desc`. Default: `desc`
`per_page`  | How many results to return per page. Default: `30`

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/user/515fb9337c1074f6fd000007/projects?offset=50baee27a43ccdf778000002>; rel="next"
```
```json
[
  {
    "id": "50baed119bf39c1431000004",
    "name": "Website",
    "api_key": "a0f5e56c125d2eeac31fd66e4f0cbd79",
    "errors": 78,
    "icon": "https://bugsnag.com/assets/frameworks/rails.png",
    "release_stages": ["production", "development"],
    "type": "rails",
    "created_at": "2012-12-02T05:54:25Z",
    "updated_at": "2013-06-17T19:57:49Z",
    "errors_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors",
    "events_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/events",
    "html_url": "https://bugsnag.com/dashboard/website",
    "url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004"
  }
]
```


Get Project Details
-------------------

Get the details of the given Bugsnag Project.

```http
GET /projects/:project_id
```

### Response

```http
Status: 200 OK
```
```json
{
  "id": "50baed119bf39c1431000004",
  "name": "Website",
  "api_key": "a0f5e56c125d2eeac31fd66e4f0cbd79",
  "errors": 78,
  "icon": "https://bugsnag.com/assets/frameworks/rails.png",
  "release_stages": ["production", "development"],
  "type": "rails",
  "created_at": "2012-12-02T05:54:25Z",
  "updated_at": "2013-06-17T19:57:49Z",
  "errors_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors",
  "events_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/events",
  "html_url": "https://bugsnag.com/dashboard/website",
  "url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004"
}
```


Create a Project
----------------

Create a new Project on the specified Bugsnag [Account](accounts.md).

```http
POST /account/:account_id/projects
```

### Parameters

Name        | Description
----------- | -----------
`name`      | The project's name, eg `Website`
`type`      | The type of the project, can be one of `rails`, `django`, `php`, `android`, `ios`, `sinatra`, `node`, `unity`, `js`, `java` or `other`. Default `other`

### Response

```http
Status: 201 Created
```
```json
{
  "id": "50baed119bf39c1431000004",
  "name": "Website",
  "api_key": "a0f5e56c125d2eeac31fd66e4f0cbd79",
  "errors": 78,
  "icon": "https://bugsnag.com/assets/frameworks/rails.png",
  "release_stages": ["production", "development"],
  "type": "rails",
  "created_at": "2012-12-02T05:54:25Z",
  "updated_at": "2013-06-17T19:57:49Z",
  "errors_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors",
  "events_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/events",
  "html_url": "https://bugsnag.com/dashboard/website",
  "url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004"
}
```


Update a Project
----------------

Update a Bugsnag Project's name and other information. Responds with the newly updated Project.

```http
PUT /projects/:project_id
```

### Parameters

Name        | Description
----------- | -----------
`name`      | The project's name, eg `Website`
`type`      | The type of the project, can be one of `rails`, `django`, `php`, `android`, `ios`, `sinatra`, `node`, `unity`, `js`, `java` or `other`. Default `other`

### Response

```http
Status: 200 OK
```
```json
{
  "id": "50baed119bf39c1431000004",
  "name": "Website",
  "api_key": "a0f5e56c125d2eeac31fd66e4f0cbd79",
  "errors": 78,
  "icon": "https://bugsnag.com/assets/frameworks/rails.png",
  "release_stages": ["production", "development"],
  "type": "rails",
  "created_at": "2012-12-02T05:54:25Z",
  "updated_at": "2013-06-17T19:57:49Z",
  "errors_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/errors",
  "events_url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004/events",
  "html_url": "https://bugsnag.com/dashboard/website",
  "url": "https://api.bugsnag.com/projects/50baed119bf39c1431000004"
}
```


Delete a Project
----------------

Delete a Project and all associated [Errors](errors.md) and [Events](events.md) from Bugsnag.

```http
DELETE /projects/:project_id
```

### Response

```http
Status: 204 No Content
```
