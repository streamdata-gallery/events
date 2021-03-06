---
swagger: "2.0"
x-collection-name: Foursquare
x-complete: 0
info:
  title: Foursquare Get Events Event
  description: /campaigns/{CAMPAIGN_ID}/start
  version: 1.0.0
host: api.foursquare.com
basePath: /v2/
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /events/categories:
    get:
      summary: Get Events Categories
      description: /events/{EVENT_ID}
      operationId: eventsevent-id
      x-api-path-slug: eventscategories-get
      parameters:
      - in: query
        name: v
        description: All requests now accept a v=YYYYMMDD param, which indicates that
          the client is up to date as of the specified date
      responses:
        200:
          description: OK
      tags:
      - Events
      - Categories
  /events/search:
    get:
      summary: Get Events Search
      description: /events/categories
      operationId: eventscategories
      x-api-path-slug: eventssearch-get
      parameters:
      - in: query
        name: domain
        description: Identifier for a known third-party event provider
      - in: query
        name: eventId
        description: Identifier used by third-party specifed in domain, which we will
          attempt to match against our events listings
      - in: query
        name: participantId
        description: Identifier used by third-party specifed in domain, which we will
          attempt to match against our events listings
      - in: query
        name: v
        description: All requests now accept a v=YYYYMMDD param, which indicates that
          the client is up to date as of the specified date
      responses:
        200:
          description: OK
      tags:
      - Events
      - Search
  /events/{EVENT_ID}:
    get:
      summary: Get Events Event
      description: /campaigns/{CAMPAIGN_ID}/start
      operationId: campaignscampaign-idstart
      x-api-path-slug: eventsevent-id-get
      parameters:
      - in: query
        name: EVENT_ID
        description: The ID of the event to retrieve additional information for
      - in: path
        name: EVENT_ID
      - in: query
        name: v
        description: All requests now accept a v=YYYYMMDD param, which indicates that
          the client is up to date as of the specified date
      responses:
        200:
          description: OK
      tags:
      - Events
      - Event
  /venues/{VENUE_ID}/events:
    get:
      summary: Get Venues Events
      description: /venues/trending
      operationId: venuestrending
      x-api-path-slug: venuesvenue-idevents-get
      parameters:
      - in: query
        name: v
        description: All requests now accept a v=YYYYMMDD param, which indicates that
          the client is up to date as of the specified date
      - in: query
        name: VENUE_ID
        description: The venue id for which events are being requested
      - in: path
        name: VENUE_ID
      responses:
        200:
          description: OK
      tags:
      - Venues
      - Events
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