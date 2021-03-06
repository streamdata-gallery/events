---
swagger: "2.0"
info:
  title: Meetup Topic Categories
  description: Returns a list high level topic categories
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
  /find/topic_categories:
    get:
      summary: Topic Categories
      description: Returns a list high level topic categories
      operationId: topics
      parameters:
      - in: query
        name: fields
        description: A comma-limited list of optional fields to append to the response
        type: string
      - in: query
        name: lat
        description: An optional approximate latitude to center a request for "best_topics"
        type: string
      - in: query
        name: lon
        description: An optional approximate longitude to center a request for "best_topics"
        type: string
      - in: query
        name: radius
        description: An radius (in miles) to center a request for "best_topics"
        type: string
      responses:
        200:
          description: OK
      tags:
      - events
      - search
      - topic categories
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