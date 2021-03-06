swagger: "2.0"
x-collection-name: Google Play
x-complete: 1
info:
  title: Google Play
  version: 1.0.0
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /eventDefinitions:
    get:
      summary: Get Event Definitions
      description: Returns a list of the event definitions in this application.
      operationId: games.events.listDefinitions
      x-api-path-slug: eventdefinitions-get
      parameters:
      - in: query
        name: consistencyToken
        description: The last-seen mutation timestamp
      - in: query
        name: language
        description: The preferred language to use for strings returned by this method
      - in: query
        name: maxResults
        description: The maximum number of event definitions to return in the response,
          used for paging
      - in: query
        name: pageToken
        description: The token returned by the previous request
      responses:
        200:
          description: OK
      tags:
      - Event
  /events:
    get:
      summary: Get Events
      description: Returns a list showing the current progress on events in this application
        for the currently authenticated user.
      operationId: games.events.listByPlayer
      x-api-path-slug: events-get
      parameters:
      - in: query
        name: consistencyToken
        description: The last-seen mutation timestamp
      - in: query
        name: language
        description: The preferred language to use for strings returned by this method
      - in: query
        name: maxResults
        description: The maximum number of events to return in the response, used
          for paging
      - in: query
        name: pageToken
        description: The token returned by the previous request
      responses:
        200:
          description: OK
      tags:
      - Event
    post:
      summary: Create Event
      description: Records a batch of changes to the number of times events have occurred
        for the currently authenticated user of this application.
      operationId: games.events.record
      x-api-path-slug: events-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: consistencyToken
        description: The last-seen mutation timestamp
      - in: query
        name: language
        description: The preferred language to use for strings returned by this method
      responses:
        200:
          description: OK
      tags:
      - Event