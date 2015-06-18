TODO
----
- Get counts for all tabs on timeline page - including Events and Errors count
- Get list of "pivotable" tabs for timeline page
- Get breakdown counts for left side of timeline page


## Private APIs?

- /projects/:project_id/inbox_counts
- /projects/:project_id/timeline_counts


## Real pivot list, with breakdowns

/projects/:project_id/pivots
[
  {
    "name": "Users",
    "field": "user.id"
  },
  {
    "name": "Hosts",
    "field": "device.hostname",
    "breakdown": [
      {},{}
    ]
  },
  {
    "name": "Release Stages",
    "field": "app.release_stage",
    "breakdown": [
      {},{}
    ]
  }
]

## Pivot list, with breakdowns, and extra bonus counts

/projects/:project_id/pivots
[
  {
    "name": "Events",
    "count": 456,
  },
  {
    "name": "Errors",
    "count": 123
  },
  {
    "name": "Users",
    "field": "user.id"
    "count": 123
  },
  {
    "name": "Hosts",
    "field": "device.hostname",
    "count": 123,
    "breakdown": [
      {},{}
    ]
  },
  {
    "name": "Release Stages",
    "field": "app.release_stage",
    "count": 123,
    "breakdown": [
      {},{}
    ]
  }
]


## Pivot values
/projects/:project_id/pivots/user.id
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





Fields
------


field name     |     fuzzy match?    |    show breakdown?     |     show pivot?
-------------------------------------------------------------------------------
app.type       |        no           |         yes            |       yes
