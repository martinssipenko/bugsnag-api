Filters API
===========

Bugsnag allows you to filter [Error](error.md), [Event](event.md) and [Pivot](pivot.md) API requests to help you better understand the health of your application. The Filters API allows you to discover which filters are available on your Project, and provides an "autocomplete" query API for discovering filter matches.


Contents
--------

-   [List a Project's Filters](#list-a-project-s-filters)
-   [List matches for a Filter](#list-matches-for-a-filter)
-   [Default fields](#default-fields)
    -   [All project types](#all-project-types)
    -   [Projects using deploy tracking](#projects-using-deploy-tracking)
    -   [Projects using app versions](#projects-using-app-versions)
    -   [Backend project types](#backend-project-types)
    -   [JavaScript projects](#javascript-projects)
    -   [Mobile projects](#mobile-projects)


List a Project's Filters
------------------------

Get a list of all fields which are available for filtering.


### Request

```http
GET /project/:project_id/filters
```

### Response

```json
[
  {
    "field": "error.status",
    "name": "error status",
    "description": "open, in progress, fixed…"
  },
  {
    "field": "error.has_issue",
    "name": "has issue",
    "description": "has an issue attached"
  }
]
```


List matches for a Filter
-------------------------

Get a list of possible matches, ordered by frequency of events, for the given Project and filter field. This could be used to provide suggested filter matches in an autocomplete-like input.


### Request

```http
GET /project/:project_id/filters/error.status
```


### Params

Name      | Description
----------|------------
q         | Partial or full query to find filter matches for
count     | Number of results to return. Default: `5`


### Response

TODO

```json
[
  {
    "id": "",
    "name": "",
    "description": ""
  }
]
```


Default fields
--------------

### All project types

Field             | Description                                 | Format
------------------|---------------------------------------------|-------------------------------------
error.status      | Errors with the given status                | `open`, `in progress`, `snoozed`, `fixed`, `ignored`
error.has_issue   | Errors with issue attached/not attached     | `true`, `false`
error.assigned_to | Errors with a Bugsnag user assigned         | *User ID* or `me`, `anyone`
event.since       | Events since the given time                 | *ISO8601* or `1h`,`3h`,`1d`,`7d`,`30d`
event.before      | Events before the given time                | *ISO8601* or `1h`,`3h`,`1d`,`7d`,`30d`
event.class       | Events with the given class                 | *Fuzzy-match string*
event.message     | Events with the given message               | *Fuzzy-match string*
event.file        | Events with stackframes in the given file   | *Fuzzy-match string*
event.method      | Events with stackframes in the given method | *Fuzzy-match string*
event.severity    | Events with given severity                  | `error`, `warning`, `info`
event.context     | Events with given context                   | *Fuzzy-match string*
user.id           | Events affecting an external user id        | *String*
user.name         | Events affecting an external user name      | *String*
user.email        | Events affecting an external user email     | *Fuzzy-match string*
app.release_stage | Events affecting the given release stage    | *String*


### Projects using deploy tracking

Field                | Description                                 | Format
---------------------|---------------------------------------------|-------------------------------------
deploy.seen_in       | Events seen in the given deploy             | *Deploy ID* or `latest`
deploy.introduced_in | Events first seen in the given deploy       | *Deploy ID* or `latest`


### Projects using app versions

Field                   | Description                                     | Format
------------------------|-------------------------------------------------|-------------------------------------
version.seen            | Events seen in the given app version            | *Wildcard String*
version.introduced      | Events first seen in the given app version      | *Wildcard String*
version_code.seen       | Events seen in the given version code           | *Integer*
version_code.introduced | Events first seen in the given version code     | *Integer*


### Backend project types

Field             | Description                                 | Format
------------------|---------------------------------------------|-------------------------------------
app.type          | Events seen on the given app type           | *String*
device.hostname   | Events seen on the given hostname           | *String*
request.url       | Events seen on the given URL (no GET params)| *String*
request.ip        | Events affecting the given IP address       | *String*


### JavaScript projects

Field             | Description                                 | Format
------------------|---------------------------------------------|-------------------------------------
browser.name      | Events affecting given browser              | *String*
browser.version   | Events affecting given browser version      | *Wildcard String*
os.name           | Events seen on the given O/S                | *String*
os.version        | Events seen on the given O/S version        | *Wildcard String*
request.url       | Events seen on the given URL (no GET params)| *String*
request.ip        | Events affecting the given IP address       | *String*


### Mobile projects

Field                   | Description                                     | Format
------------------------|-------------------------------------------------|-------------------------------------
os.name                 | Events seen on the given O/S                    | *String*
os.version              | Events seen on the given O/S version            | *Wildcard String*
device.manufacturer     | Events affecting the given device manufacturer  | *String*
device.id               | Events affecting the given device ID            | *String*
