Events API
==========

Bugsnag represents individual crashes (typically an exception in your applications) as what we call *Events*. The Events API allows you to get information about and delete Bugsnag Events.


Contents
--------

- [List a Project's Events](#list-a-project-s-events)
- [List an Errors's Events](#list-an-error-s-events)
- [Get Event details](#get-event-details)
- [Delete an Event](#delete-an-event)


List a Project's Events
-----------------------

Get a list of all events (individual crashes) for the specified Bugsnag [Project](projects.md).

```http
GET /projects/:project_id/events
```

### Parameters

Name        | Description
----------- | -----------
`sort`      | What to sort results by. Can be only `created_at`. Default: `created_at`
`direction` | The direction of the sort. Can be either `asc` or `desc`. Default: `desc`
`per_page`  | How many results to return per page. Default: `10`
`start_time`| Start time for the query. Optional, ISO 8601 format ("2013-10-23T15:23:34Z").
`end_time`  | End time for the query. Optional, ISO 8601 format ("2013-10-24T15:23:34Z").

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/projects/50baed119bf39c1431000004/events?offset=51f93d6af002c6686d058c49>; rel="next"
```
```json
[
  {
    "id": "51f5d152f002c6686d013a22",
    "exceptions": [
      {
        "class": "ActionView::Template::Error",
        "message": "source sequence is illegal/malformed utf-8",
        "stacktrace": [
          {
            "line": 285,
            "column": 20,
            "file": "app/models/user.rb",
            "method": "generate"
          },
        ]
      },
    ],
    "user_id": "user@yoursite.com",
    "received_at": "2012-12-02T05:54:25Z",
    "context": "events#show",
    "app_version": "1.0.1",
    "os_version": "Windows Vista",
    "meta_data": { ... },
    "url": "https://api.bugsnag.com/events/51f5d152f002c6686d013a22",
    "html_url": "https://bugsnag.com/errors/51f5cbadcf4cfd7373c8cc2d/events/51f5d152f002c6686d013a22"
  }
]
```


List an Error's Events
-----------------------

Get a list of all events (individual crashes) grouped under the specified Bugsnag [Error](errors.md).

```http
GET /errors/:error_id/events
```

### Parameters

Name        | Description
----------- | -----------
`sort`      | What to sort results by. Can be only `created_at`. Default: `created_at`
`direction` | The direction of the sort. Can be either `asc` or `desc`. Default: `desc`
`per_page`  | How many results to return per page. Default: `10`
`start_time`| Start time for the query. Optional, ISO 8601 format ("2013-10-23T15:23:34Z").
`end_time`  | End time for the query. Optional, ISO 8601 format ("2013-10-24T15:23:34Z").

### Response

```http
Status: 200 OK
Link: <http://api.bugsnag.com/projects/515fbcfc7c1074a459000001/events?desc=id&offset=51ac4eef95f3b06728000afc&per_page=1>; rel="next"
```
```json
[
  {
    "id": "51f5d152f002c6686d013a22",
    "exceptions": [
      {
        "class": "ActionView::Template::Error",
        "message": "source sequence is illegal/malformed utf-8",
        "stacktrace": [
          {
            "line": 285,
            "column": 20,
            "file": "app/models/user.rb",
            "method": "generate"
          },
        ]
      },
    ],
    "user_id": "user@yoursite.com",
    "received_at": "2012-12-02T05:54:25Z",
    "context": "events#show",
    "app_version": "1.0.1",
    "os_version": "Windows Vista",
    "meta_data": { ... },
    "url": "https://api.bugsnag.com/events/51f5d152f002c6686d013a22",
    "html_url": "https://bugsnag.com/errors/51f5cbadcf4cfd7373c8cc2d/events/51f5d152f002c6686d013a22"
  }
]
```


Get Event details
-----------------

Get the details of the given Bugsnag Event.

```http
GET /events/:event_id
```

### Response

```http
Status: 200 OK
```
```json
{
  "id": "51f5d152f002c6686d013a22",
  "exceptions": [
    {
      "class": "ActionView::Template::Error",
      "message": "source sequence is illegal/malformed utf-8",
      "stacktrace": [
        {
          "line": 285,
          "column": 20,
          "file": "app/models/user.rb",
          "method": "generate"
        },
      ]
    },
  ],
  "user_id": "user@yoursite.com",
  "received_at": "2012-12-02T05:54:25Z",
  "context": "events#show",
  "app_version": "1.0.1",
  "os_version": "Windows Vista",
  "meta_data": { ... },
  "url": "https://api.bugsnag.com/events/51f5d152f002c6686d013a22",
  "html_url": "https://bugsnag.com/errors/51f5cbadcf4cfd7373c8cc2d/events/51f5d152f002c6686d013a22"
}
```


Delete an Event
---------------

Delete an Event from Bugsnag.

```http
DELETE /events/:event_id
```

### Response

```http
Status: 204 No Content
```
