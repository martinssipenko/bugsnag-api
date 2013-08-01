Events
------

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