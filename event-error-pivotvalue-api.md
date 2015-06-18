```ruby

# Get a "full" event
# /events/:event_id

# Get a list of "basic" events for an error
# /errors/:error_id/events
# /errors/:error_id/events/latest

# Get a list of "basic" events for a project
# /projects/:project_id/events
# /projects/:project_id/events/latest

# Get a list of "basic" events, and include release stage, user name and user email
# /projects/:project_id/events?fields[]=app.release_stage&fields=user.name&fields=user.email

# Get a list of errors, with "basic" latest event information
# /project/:project_id/errors

# Get a list of errors, with "basic" latest event information, and include release stage
# /project/:project_id/errors?fields[]=app.release_stage


event_fields = [
  "app.release_stage",
  "exceptions."
]

event = {
  # Basic fields (always in lists)
  "id",
  "received_at"
  "error_id"
  "error_class",
  "message",
  "context",
  "severity",

  # Complex fields (in details, or by request)
  "exceptions[]"
  "user{}",
  "app{}"
  "device{}"
  "meta_data{}"
}

error = {
  # Error id
  "id",

  # Error fields
  "assigned_user",
  "status",
  "linked_issue",
  "snooze_conditions"

  # Event aggregations
  "first_seen",
  "last_seen",
  "event_count",
  "user_count",
  "proportion",

  # Event trend (by request)
  "trend",

  # Latest event
  latest_event: {
    # Basic fields (always in lists)
    "id",
    "received_at"
    "error_id"
    "context",
    "severity",

    # Complex fields (in details, or by request)
    "exceptions[]"
      "error_class",
      "message",
    "user{}",
    "app{}"
    "device{}"
    "meta_data{}"
  }
}

pivot_value = {
  # Pivot id
  "id",

  # Event aggregations
  "first_seen",
  "last_seen",
  "event_count",
  "user_count",
  "proportion",

  # Event trend (by request)
  "trend",

  # Latest event
  latest_event: {
    # Basic fields (always in lists)
    "id",
    "received_at"
    "error_id"
    "error_class",
    "message",
    "context",
    "severity",

    # Complex fields (in details, or by request)
    "exceptions[]"
    "user{}",
    "app{}"
    "device{}"
    "meta_data{}"
  }
}
