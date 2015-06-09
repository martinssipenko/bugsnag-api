Pivots API
==========

The Pivots API allows you to [pivot](http://en.wikipedia.org/wiki/Pivot_table) on Event fields, allowing you to group similar Events and explore their impact. For example, you may wish to see a breakdown of events grouped by release stage (eg. "production" vs "development"), or grouped by application version (eg. 1.2.0 vs 1.3.0).


Contents
--------

- [List Pivot fields on a Project](#list-pivot-fields-on-a-project)
- [List Pivot fields on an Error](#list-pivot-fields-on-an-error)
- [Get Pivot values on a Project](#get-pivot-values-on-a-project)
- [Get Pivot values on an Error](#get-pivot-values-on-an-error)


List Pivot fields on a Project
------------------------------

Get a list of all the Pivot fields available on the given [Project](project.md), along with a summary of the top pivot values.

```http
GET /projects/:project_id/pivots
```

### Parameters

Name           | Description
-------------- | -----------
`filters`      | Filters to apply to the query, see [filtering errors, events or pivots](filters.md#filtering-errors-events-or-pivots) for details
`summary_size` | How many values to show in the summary. Default: `5`

### Response

```http
Status: 200 OK
```
```json
[
  {
    "field": "device.hostname",
    "name": "Hosts",
    "summary": [{
      "value": "app1.ec3.bugsnag.com",
      "events": 123,
      "proportion": 0.75
    }]
  }, {
    "field": "app.release_stage",
    "name": "Release Stages",
    "summary": [{
      "value": "production",
      "events": 123,
      "proportion": 0.1
    }]
  }
]
```


List Pivot fields on an Error
-----------------------------

Get a list of all the Pivot fields available on the given [Error](error.md), along with a summary of the top pivot values.

```http
GET /errors/:error_id/pivots
```

### Parameters

Name           | Description
-------------- | -----------
`filters`      | Filters to apply to the query, see [filtering errors, events or pivots](filters.md#filtering-errors-events-or-pivots) for details
`summary_size` | How many values to show in the summary. Default: `5`

### Response

```http
Status: 200 OK
```
```json
[
  {
    "field": "device.hostname",
    "name": "Hosts",
    "cardinality": 123,
    "summary": [{
      "value": "app1.ec3.bugsnag.com",
      "events": 123,
      "proportion": 0.75
    }]
  }, {
    "field": "app.release_stage",
    "name": "Release Stages",
    "cardinality": 456,
    "summary": [{
      "value": "production",
      "events": 123,
      "proportion": 0.1
    }]
  }
]
```


Get Pivot values on a Project
-----------------------------

Get a list of each Pivot value for the given field on the given Project.

```http
GET /projects/:project_id/pivots/:pivot_field
```

### Parameters

Name           | Description
-------------- | -----------
`filters`      | Filters to apply to the query, see [filtering errors, events or pivots](filters.md#filtering-errors-events-or-pivots) for details

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/projects/70baea119bf39c1431000004/pivots?offset=50baee27a43ccdf778000002>; rel="next"
X-Total-Count: 123
```
```json
[
  {
    "value": "production",
    "events": 123,
    "proportion": 0.1
  },
  {
    "value": "development",
    "events": 456,
    "proportion": 0.8
  }
]
```


Get Pivot values on an Error
----------------------------

Get a list of each Pivot value for the given field on the given Error.

```http
GET /errors/:error_id/pivots/:pivot_field
```

### Parameters

Name           | Description
-------------- | -----------
`filters`      | Filters to apply to the query, see [filtering errors, events or pivots](filters.md#filtering-errors-events-or-pivots) for details

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/errors/70baea119bf39c1431000004/pivots?offset=50baee27a43ccdf778000002>; rel="next"
X-Total-Count: 123
```
```json
[
  {
    "value": "production",
    "events": 123,
    "proportion": 0.1
  },
  {
    "value": "development",
    "events": 456,
    "proportion": 0.8
  }
]
```
