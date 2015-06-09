Filters API
===========

Bugsnag allows you to filter [Error](error.md), [Event](event.md) and [Pivot](pivot.md) API requests to help you better understand the health of your application. The Filters API allows you to discover which filters are available on your Project, and provides an "autocomplete" query API for discovering filter matches.


Contents
--------

-   [List a Project's Filters](#list-a-project-s-filters)
-   [List matches for a Filter](#list-matches-for-a-filter)
-   [Filtering Errors, Events or Pivots](#filtering-errors-events-or-pivots)
-   [Default fields](#default-fields)
    -   [All project types](#all-project-types)
    -   [Projects using deploy tracking](#projects-using-deploy-tracking)
    -   [Projects using app versions](#projects-using-app-versions)
    -   [Backend project types](#backend-project-types)
    -   [JavaScript projects](#javascript-projects)
    -   [Mobile projects](#mobile-projects)


List a Project's Filters
------------------------

Get a list of all fields which are available for filtering. Some fields will include a fixed list of possible field values which can be used for autocomplete.


### Request

```http
GET /project/:project_id/filters
```


### Response Fields

Name            | Description
----------------|-------------
`field`         | The filter's field ID, used when [filtering queries](#filtering-errors-events-or-pivots)
`name`          | A friendly name for the filter
`description`   | A description for the filter
`values`        | Optional. A fixed list of values for this filter


### Response Example

```http
Status: 200 OK
```
```json
[
  {
    "field": "error.status",
    "name": "error status",
    "description": "open, in progress, fixed…",
    "values": [
      {
        "id": "open",
        "name": "Open"
      }, {
        "id": "in progress",
        "name": "In Progress"
      }, {
        "id": "fixed",
        "name": "Fixed"
      }, {
        "id": "snoozed",
        "name": "Snoozed"
      }, {
        "id": "ignored",
        "name": "Ignored"
      }
    ]
  },
  {
    "field": "app.release_stage",
    "name": "release stage",
    "description": "production, development, etc"
  }
]
```


List matches for a Filter
-------------------------

Get a list of possible matches, for the given Project and filter field. This could be used to provide suggested filter matches in an autocomplete-like input.


### Request

```http
GET /project/:project_id/filters/:filter_field
```


### Params

Name        | Description
------------|------------
q           | Partial or full query to find filter matches for
result_size | Number of results to return. Default: `5`


### Response Fields

Name            | Description
----------------|-------------
`id`            | The value to send when [filtering queries](#filtering-errors-events-or-pivots)
`name`          | Optional. A friendly display name for value
`description`   | Optional. An additional description for the value


### Response Example

```http
Status: 200 OK
```
```json
[
  {
    "id": "me",
    "name": "Me"
  },
  {
    "id": "anyone",
    "name": "Anyone"
  },
  {
    "id": "515fb9337c1074f6fd000007",
    "name": "James Smith"
  }
]
```


Filtering Errors, Events or Pivots
----------------------------------

API requests to [Error](error.md), [Event](event.md) and [Pivot](pivot.md) endpoints can be filtered to help you better understand the health of your application. Any request which supports filtering can be filtered by sending a `filters` parameter:

```json
"filters": {
  "event.since": "1h",
  "error.status": ["fixed", "snoozed"],
  "event.class": "timeout"
}
```

Since GET request parameters must be encoded into the URL, we require that this filter object be encoded in jQuery/PHP style parameter format. For example, using jQuery's [$.param](http://api.jquery.com/jquery.param/) function:

```
filters[event.since]=1h&filters[error.status][]=fixed&filters[error.status][]=snoozed&filters[event.class]=timeout
```


Default fields
--------------

Depending on your Project type, there are numerous fields available by default on your Project:

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
