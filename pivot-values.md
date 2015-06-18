Pivot Values API
================

The Pivot Values API allows you to [pivot](http://en.wikipedia.org/wiki/Pivot_table) on Event fields, allowing you to group similar Events and explore their impact. For example, you may wish to see a breakdown of events grouped by release stage (eg. "production" vs "development"), or grouped by application version (eg. 1.2.0 vs 1.3.0).


Contents
--------
-   [The Pivot Value Object](#the-pivot-value-object)
-   [Get Pivot Values on a Project](#get-pivot-values-on-a-project)
-   [Get Pivot Values on an Error](#get-pivot-values-on-an-error)


The Pivot Value Object
----------------------

The following fields are present on Pivot Value responses:

Name                | Description
------------------- | -----------
`value`             | The pivot value, eg *production*. Events where this Pivot field was not present will have grouped under the `null` value
`events`            | The number of Events matching this pivot value (respects filters)
`proportion`        | The proportion of Events matching this pivot value (a number between 0 and 1, respects filters)
`first_seen`        | When this pivot value was first seen, in [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) format (respects filters)
`last_seen`         | When this pivot value was last seen, in [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) format (respects filters)
`event_fields`      | Certain Pivots (eg. `user.id`) will return additional fields to help describe the pivot value


Get Pivot Values on a Project
-----------------------------

Get a list of each Pivot value for the given field on the given Project.


### Request

```http
GET /projects/:project_id/pivots/:pivot_id/values
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
  },
  {
    "value": null,
    "events": 123,
    "proportion": 0.1
  }
]
```


Get Pivot Values on an Error
----------------------------

Get a list of each Pivot value for the given field on the given Error.

```http
GET /errors/:error_id/pivots/:pivot_id/values
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
