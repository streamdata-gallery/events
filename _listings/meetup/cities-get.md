---
swagger: "2.0"
info:
  title: Meetup Cities
  description: API method for accessing meetup cities
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
  /cities:
    get:
      summary: Cities
      description: API method for accessing meetup cities
      operationId: deprecated
      parameters:
      - in: query
        name: country
        description: Return cities in these countries [separate countries with commas]
        type: string
      - in: query
        name: state
        description: Return cities in these states [separate states with commas]
        type: string
      responses:
        200:
          description: OK
      tags:
      - events
      - cities
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