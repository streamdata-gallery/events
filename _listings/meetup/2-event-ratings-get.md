---
swagger: "2.0"
info:
  title: Meetup Ratings v2
  description: API method for accessing Meetup comments
  version: 1.0.0
host: api.meetup.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /2/event_ratings:
    get:
      summary: Ratings v2
      description: API method for accessing Meetup comments
      operationId: events
      parameters:
      - in: query
        name: event_id
        description: The ID of the event to fetch ratings data for
        type: string
      - in: query
        name: member_id
        description: The ID of a member to filter ratings on
        type: string
      responses:
        200:
          description: OK
      tags:
      - events
      - groups
definitions: []
x-collection-name: Meetup
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---