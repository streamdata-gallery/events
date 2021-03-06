---
swagger: "2.0"
info:
  title: Akamai API Get Entry Point Data for Flash Live Streams
  description: Get Entry Point Data for Flash Live Streams
  version: 1.0.0
host: developer.akamai.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /events/v2/{accountId}/events/{eventId}/trafficdata/entrypoint/flashlive:
    get:
      summary: Get Entry Point Data for Flash Live Streams
      description: Get Entry Point Data for Flash Live Streams
      operationId: eventsv2accountideventseventidtrafficdataentrypointflashlive
      parameters:
      - in: query
        name: accountId
        description: Unique identifier for the account
        type: string
      - in: query
        name: eventId
        description: Unique identifier for the event
        type: string
      responses:
        200:
          description: OK
      tags:
      - events
      - account
      - events
      - event
      - trafficdata
      - entrypoint
      - flashlive
definitions: []
x-collection-name: Akamai
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