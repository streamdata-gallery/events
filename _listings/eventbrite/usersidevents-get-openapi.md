---
swagger: "2.0"
x-collection-name: Eventbrite
x-complete: 0
info:
  title: Eventbrite Get Users Events
  description: Returns a paginated response of events, under the key events, of all
    events the user has access to
  version: 1.0.0
host: www.eventbrite.com
basePath: /%7Bdata-type%7D/
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /events/:
    post:
      summary: Post Events
      description: Makes a new event, and returns an event for the specified event.
      operationId: postEvents
      x-api-path-slug: events-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: event.capacity
        description: Set specific capacity (if omitted, sums ticket capacities)
        type: query
      - in: query
        name: event.category_id
        description: The category (vertical) of the event
        type: query
      - in: query
        name: event.currency
        description: Event currency (3 letter code)
        type: query
      - in: query
        name: event.description.html
        description: The description on the event page
        type: query
      - in: query
        name: event.end.timezone
        description: End time timezone (Olson format)
        type: query
      - in: query
        name: event.end.utc
        description: The end time of the event
        type: query
      - in: query
        name: event.format_id
        description: The format (general type) of the event
        type: query
      - in: query
        name: event.hide_end_date
        description: Whether the end date should be hidden
        type: query
      - in: query
        name: event.hide_start_date
        description: Whether the start date should be hidden
        type: query
      - in: query
        name: event.invite_only
        description: Only invited users can see the event page
        type: query
      - in: query
        name: event.is_reserved_seating
        description: If the event is reserved seating
        type: query
      - in: query
        name: event.listed
        description: If the event is publicly listed and searchable
        type: query
      - in: query
        name: event.logo.id
        description: (Deprecated) The logo for the event
        type: query
      - in: query
        name: event.logo_id
        description: The logo for the event
        type: query
      - in: query
        name: event.name.html
        description: The name of the event
        type: query
      - in: query
        name: event.online_event
        description: Is the event online-only (no venue)?
        type: query
      - in: query
        name: event.organizer_id
        description: The ID of the organizer of this event
        type: query
      - in: query
        name: event.password
        description: Password needed to see the event in unlisted mode
        type: query
      - in: query
        name: event.shareable
        description: If users can share the event on social media
        type: query
      - in: query
        name: event.show_pick_a_seat
        description: For reserved seating event, if attendees can pick their seats
        type: query
      - in: query
        name: event.show_remaining
        description: If the remaining number of tickets is publicly visible on the
          event page
        type: query
      - in: query
        name: event.show_seatmap_thumbnail
        description: For reserved seating event, if venue map thumbnail visible on
          the event page
        type: query
      - in: query
        name: event.source
        description: Source of the event (defaults to API)
        type: query
      - in: query
        name: event.start.timezone
        description: Start time timezone (Olson format)
        type: query
      - in: query
        name: event.start.utc
        description: The start time of the event
        type: query
      - in: query
        name: event.subcategory_id
        description: The subcategory of the event (US only)
        type: query
      - in: query
        name: event.venue_id
        description: The ID of a previously-created venue to associate with this event
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
  /events/{id}:
    get:
      summary: Get Events
      description: Returns an event for the specified event. Many of Eventbrite?s
        API use cases resolve around pulling details of a specific event within an
        Eventbrite account.
      operationId: getEvents
      x-api-path-slug: eventsid-get
      parameters:
      - in: path
        name: id
        description: Event Id
      responses:
        200:
          description: OK
      tags:
      - Events
    post:
      summary: Post Events
      description: Updates an event. Returns an event for the specified event.
      operationId: postEvents
      x-api-path-slug: eventsid-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: id
        description: Event Id
      responses:
        200:
          description: OK
      tags:
      - Events
  /events/:event_id/checkout_settings/:
    get:
      summary: Get Events Event Checkout Settings
      description: Gets and returns a list of checkout_settings associated with a
        given event by its event_id.
      operationId: getEventsEventCheckoutSettings
      x-api-path-slug: eventsevent-idcheckout-settings-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Checkout
      - Settings
    post:
      summary: Post Events Event Checkout Settings
      description: Associate a single or set of checkout_settings with a given event
        by its event_id. This does not add more checkout settings to the event, but
        instead replaces all checkout settings for the event with the one(s) submitted.
        The JSON post body is a string list of the checkout_settings IDs you want
        to associate.
      operationId: postEventsEventCheckoutSettings
      x-api-path-slug: eventsevent-idcheckout-settings-post
      parameters:
      - in: query
        name: checkout_settings_ids
        description: A list of IDs for checkout settings that should be linked to
          the event
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Checkout
      - Settings
  /events/:event_id/payout_settings/:
    get:
      summary: Get Events Event Payout Settings
      description: Gets and returns the payout_settings (user instrument ID) associated
        with a given event by its event_id.
      operationId: getEventsEventPayoutSettings
      x-api-path-slug: eventsevent-idpayout-settings-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Payout
      - Settings
    post:
      summary: Post Events Event Payout Settings
      description: Associate a payout user instrument ID with a given event, or clear
        the association by passing a null value for the user instrument ID.
      operationId: postEventsEventPayoutSettings
      x-api-path-slug: eventsevent-idpayout-settings-post
      parameters:
      - in: query
        name: payout_settings.user_instrument_vault_id
        description: The vault ID for the user instrument to which payouts are sent
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Payout
      - Settings
  /events/{id}/:
    get:
      summary: Get Events
      description: |-
        Returns an event for the specified event. Many of Eventbrite???s API use cases revolve around pulling details
        of a specific event within an Eventbrite account. Does not support fetching a repeating event series parent
        (see GET /series/:id/).
      operationId: getEvents
      x-api-path-slug: eventsid-get
      responses:
        200:
          description: OK
      tags:
      - Events
    post:
      summary: Post Events
      description: |-
        Updates an event. Returns an event for the specified event. Does not support updating a repeating event
        series parent (see POST /series/:id/).
      operationId: postEvents
      x-api-path-slug: eventsid-post
      parameters:
      - in: query
        name: event.capacity
        description: Set specific capacity (if omitted, sums ticket capacities)
        type: query
      - in: query
        name: event.category_id
        description: The category (vertical) of the event
        type: query
      - in: query
        name: event.currency
        description: Event currency (3 letter code)
        type: query
      - in: query
        name: event.description.html
        description: The description on the event page
        type: query
      - in: query
        name: event.end.timezone
        description: End time timezone (Olson format)
        type: query
      - in: query
        name: event.end.utc
        description: The end time of the event
        type: query
      - in: query
        name: event.format_id
        description: The format (general type) of the event
        type: query
      - in: query
        name: event.hide_end_date
        description: Whether the end date should be hidden
        type: query
      - in: query
        name: event.hide_start_date
        description: Whether the start date should be hidden
        type: query
      - in: query
        name: event.invite_only
        description: Only invited users can see the event page
        type: query
      - in: query
        name: event.is_reserved_seating
        description: If the event is reserved seating
        type: query
      - in: query
        name: event.listed
        description: If the event is publicly listed and searchable
        type: query
      - in: query
        name: event.logo.id
        description: (Deprecated) The logo for the event
        type: query
      - in: query
        name: event.logo_id
        description: The logo for the event
        type: query
      - in: query
        name: event.name.html
        description: The name of the event
        type: query
      - in: query
        name: event.online_event
        description: Is the event online-only (no venue)?
        type: query
      - in: query
        name: event.organizer_id
        description: The ID of the organizer of this event
        type: query
      - in: query
        name: event.password
        description: Password needed to see the event in unlisted mode
        type: query
      - in: query
        name: event.shareable
        description: If users can share the event on social media
        type: query
      - in: query
        name: event.show_pick_a_seat
        description: For reserved seating event, if attendees can pick their seats
        type: query
      - in: query
        name: event.show_remaining
        description: If the remaining number of tickets is publicly visible on the
          event page
        type: query
      - in: query
        name: event.show_seatmap_thumbnail
        description: For reserved seating event, if venue map thumbnail visible on
          the event page
        type: query
      - in: query
        name: event.source
        description: Source of the event (defaults to API)
        type: query
      - in: query
        name: event.start.timezone
        description: Start time timezone (Olson format)
        type: query
      - in: query
        name: event.start.utc
        description: The start time of the event
        type: query
      - in: query
        name: event.subcategory_id
        description: The subcategory of the event (US only)
        type: query
      - in: query
        name: event.venue_id
        description: ID of the venue
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
    delete:
      summary: Delete Events
      description: |-
        Deletes an event if the delete is permitted. In order for a delete to be permitted, there must be no pending or
        completed orders. Returns a boolean indicating success or failure of the delete.
      operationId: deleteEvents
      x-api-path-slug: eventsid-delete
      responses:
        200:
          description: OK
      tags:
      - Events
  /events/{id}/publish/:
    post:
      summary: Post Events Publish
      description: |-
        Publishes an event if it has not already been deleted. In order for publish to be permitted, the event must have all
        necessary information, including a name and description, an organizer, at least one ticket, and valid payment options.
        This API endpoint will return argument errors for event fields that fail to validate the publish requirements. Returns
        a boolean indicating success or failure of the publish.
      operationId: postEventsPublish
      x-api-path-slug: eventsidpublish-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Publish
  /events/{id}/unpublish/:
    post:
      summary: Post Events Unpublish
      description: |-
        Unpublishes an event. In order for a free event to be unpublished, it must not have any pending or completed orders,
        even if the event is in the past. In order for a paid event to be unpublished, it must not have any pending or completed
        orders, unless the event has been completed and paid out. Returns a boolean indicating success or failure of the
        unpublish.
      operationId: postEventsUnpublish
      x-api-path-slug: eventsidunpublish-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Unpublish
  /events/{id}/cancel/:
    post:
      summary: Post Events Cancel
      description: |-
        Cancels an event if it has not already been deleted. In order for cancel to be permitted, there must be no pending or
        completed orders. Returns a boolean indicating success or failure of the cancel.
      operationId: postEventsCancel
      x-api-path-slug: eventsidcancel-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Cancel
  /events/{id}/copy/:
    post:
      summary: Post Events Copy
      description: Creates a duplicate version of the event being copied. Returns
        the event object for the newly created event.
      operationId: postEventsCopy
      x-api-path-slug: eventsidcopy-post
      parameters:
      - in: query
        name: end_date
        description: The end time of the new event
        type: query
      - in: query
        name: name
        description: The name of the new event
        type: query
      - in: query
        name: start_date
        description: The start time of the new event
        type: query
      - in: query
        name: timezone
        description: timezone for the new event (Olson format)
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Copy
  /events/{id}/display_settings/:
    get:
      summary: Get Events Display Settings
      description: Retrieves the display settings for an event.
      operationId: getEventsDisplaySettings
      x-api-path-slug: eventsiddisplay-settings-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Display
      - Settings
    post:
      summary: Post Events Display Settings
      description: Updates the display settings for an event.
      operationId: postEventsDisplaySettings
      x-api-path-slug: eventsiddisplay-settings-post
      parameters:
      - in: query
        name: display_settings.show_end_date
        description: Whether to display the end date on the event listing
        type: query
      - in: query
        name: display_settings.show_facebook_friends_going
        description: Whether to display which of the user&#8217;s Facebook friends
          are going
        type: query
      - in: query
        name: display_settings.show_map
        description: Whether to display a map to the venue on the event listing
        type: query
      - in: query
        name: display_settings.show_organizer_facebook
        description: Whether to display a link to the organizer&#8217;s Facebook profile
        type: query
      - in: query
        name: display_settings.show_organizer_twitter
        description: Whether to display a link to the organizer&#8217;s Twitter profile
        type: query
      - in: query
        name: display_settings.show_remaining
        description: Whether to display the number of remaining tickets
        type: query
      - in: query
        name: display_settings.show_start_date
        description: Whether to display the start date on the event listing
        type: query
      - in: query
        name: display_settings.show_start_end_time
        description: Whether to display event start and end time on the event listing
        type: query
      - in: query
        name: display_settings.show_timezone
        description: Whether to display the event timezone on the event listing
        type: query
      - in: query
        name: display_settings.terminology
        description: 'Which terminology should be used to refer to the event (Valid
          choices are: tickets_vertical, or endurance_vertical)'
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Display
      - Settings
  /events/{id}/ticket_classes/:
    get:
      summary: Get Events Ticket Classes
      description: |-
        Returns a paginated response with a key of
        ticket_classes, containing a list of ticket_class.
      operationId: getEventsTicketClasses
      x-api-path-slug: eventsidticket-classes-get
      parameters:
      - in: query
        name: pos
        description: 'Only return ticket classes valid for the given point of sale
          (Valid choices are: online, or at_the_door)'
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Ticket
      - Classes
    post:
      summary: Post Events Ticket Classes
      description: |-
        Creates a new ticket class, returning the result as a ticket_class
        under the key ticket_class.
      operationId: postEventsTicketClasses
      x-api-path-slug: eventsidticket-classes-post
      parameters:
      - in: query
        name: ticket_class.auto_hide
        description: Hide this ticket when it is not on sale
        type: query
      - in: query
        name: ticket_class.auto_hide_after
        description: Override re-hide date for auto-hide
        type: query
      - in: query
        name: ticket_class.auto_hide_before
        description: Override reveal date for auto-hide
        type: query
      - in: query
        name: ticket_class.cost
        description: Cost of the ticket (currently currency must match event currency)
          e
        type: query
      - in: query
        name: ticket_class.description
        description: Description of the ticket
        type: query
      - in: query
        name: ticket_class.donation
        description: Is this a donation? (user-supplied cost)
        type: query
      - in: query
        name: ticket_class.free
        description: Is this a free ticket?
        type: query
      - in: query
        name: ticket_class.hidden
        description: Hide this ticket
        type: query
      - in: query
        name: ticket_class.hide_description
        description: Hide the ticket description on the event page
        type: query
      - in: query
        name: ticket_class.include_fee
        description: Absorb the fee into the displayed cost
        type: query
      - in: query
        name: ticket_class.maximum_quantity
        description: Maximum number per order (blank for unlimited)
        type: query
      - in: query
        name: ticket_class.minimum_quantity
        description: Minimum number per order
        type: query
      - in: query
        name: ticket_class.name
        description: Name of this ticket type
        type: query
      - in: query
        name: ticket_class.order_confirmation_message
        description: Order message per ticket type
        type: query
      - in: query
        name: ticket_class.quantity_total
        description: Total available number of this ticket, required for non-donation
          tickets
        type: query
      - in: query
        name: ticket_class.sales_channels
        description: A list of all supported sales channels ([&#8220;online&#8221;],
          [&#8220;online&#8221;, &#8220;atd&#8221;], [&#8220;atd&#8221;])
        type: query
      - in: query
        name: ticket_class.sales_end
        description: When the ticket stops being on sale (leave empty for &#8216;one
          hour before event start&#8217;)
        type: query
      - in: query
        name: ticket_class.sales_start
        description: When the ticket is available for sale (leave empty for &#8216;when
          event published&#8217;)
        type: query
      - in: query
        name: ticket_class.sales_start_after
        description: The ID of another ticket class - when it sells out, this class
          will go on sale
        type: query
      - in: query
        name: ticket_class.split_fee
        description: Absorb the payment fee, but show the eventbrite fee
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Ticket
      - Classes
  /events/{id}/ticket_classes/:ticket_class_id/:
    get:
      summary: Get Events Ticket Classes Ticket Class
      description: |-
        Gets and returns a single ticket_class by ID, as the key
        ticket_class.
      operationId: getEventsTicketClassesTicketClass
      x-api-path-slug: eventsidticket-classesticket-class-id-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Ticket
      - Classes
      - :ticket
      - Class
    post:
      summary: Post Events Ticket Classes Ticket Class
      description: Updates an existing ticket class, returning the updated result
        as a ticket_class under the key ticket_class.
      operationId: postEventsTicketClassesTicketClass
      x-api-path-slug: eventsidticket-classesticket-class-id-post
      parameters:
      - in: query
        name: ticket_class.auto_hide
        description: Hide this ticket when it is not on sale
        type: query
      - in: query
        name: ticket_class.auto_hide_after
        description: Override re-hide date for auto-hide
        type: query
      - in: query
        name: ticket_class.auto_hide_before
        description: Override reveal date for auto-hide
        type: query
      - in: query
        name: ticket_class.cost
        description: Cost of the ticket (currently currency must match event currency)
          e
        type: query
      - in: query
        name: ticket_class.description
        description: Description of the ticket
        type: query
      - in: query
        name: ticket_class.donation
        description: Is this a donation? (user-supplied cost)
        type: query
      - in: query
        name: ticket_class.free
        description: Is this a free ticket?
        type: query
      - in: query
        name: ticket_class.hidden
        description: Hide this ticket
        type: query
      - in: query
        name: ticket_class.hide_description
        description: Hide the ticket description on the event page
        type: query
      - in: query
        name: ticket_class.include_fee
        description: Absorb the fee into the displayed cost
        type: query
      - in: query
        name: ticket_class.maximum_quantity
        description: Maximum number per order (blank for unlimited)
        type: query
      - in: query
        name: ticket_class.minimum_quantity
        description: Minimum number per order
        type: query
      - in: query
        name: ticket_class.name
        description: Name of this ticket type
        type: query
      - in: query
        name: ticket_class.order_confirmation_message
        description: Order message per ticket type
        type: query
      - in: query
        name: ticket_class.quantity_total
        description: Total available number of this ticket, required for non-donation
          tickets
        type: query
      - in: query
        name: ticket_class.sales_channels
        description: A list of all supported sales channels ([&#8220;online&#8221;],
          [&#8220;online&#8221;, &#8220;atd&#8221;], [&#8220;atd&#8221;])
        type: query
      - in: query
        name: ticket_class.sales_end
        description: When the ticket stops being on sale (leave empty for &#8216;one
          hour before event start&#8217;)
        type: query
      - in: query
        name: ticket_class.sales_start
        description: When the ticket is available for sale (leave empty for &#8216;when
          event published&#8217;)
        type: query
      - in: query
        name: ticket_class.sales_start_after
        description: The ID of another ticket class - when it sells out, this class
          will go on sale
        type: query
      - in: query
        name: ticket_class.split_fee
        description: Absorb the payment fee, but show the eventbrite fee
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Ticket
      - Classes
      - :ticket
      - Class
    delete:
      summary: Delete Events Ticket Classes Ticket Class
      description: 'Deletes the ticket class. Returns {&quot;deleted&quot;: true}.'
      operationId: deleteEventsTicketClassesTicketClass
      x-api-path-slug: eventsidticket-classesticket-class-id-delete
      parameters:
      - in: query
        name: break_dependency
        description: Delete even if ticket sales depend on this ticket
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Ticket
      - Classes
      - :ticket
      - Class
  /events/{id}/canned_questions/:
    get:
      summary: Get Events Canned Questions
      description: 'This endpoint returns canned questions of a single event (examples:
        first name, last name, company, prefix, etc.). This endpoint will return question.'
      operationId: getEventsCannedQuestions
      x-api-path-slug: eventsidcanned-questions-get
      parameters:
      - in: query
        name: as_owner
        description: Return private events and more details
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Canned
      - Questions
    post:
      summary: Post Events Canned Questions
      description: Creates a new canned question; returns the result as a question.
      operationId: postEventsCannedQuestions
      x-api-path-slug: eventsidcanned-questions-post
      parameters:
      - in: query
        name: question.canned_type
        description: String value of canned_type
        type: query
      - in: query
        name: question.choices
        description: Choices for multiple choice questions
        type: query
      - in: query
        name: question.display_answer_on_order
        description: Is this question displayed on order confirmation?
        type: query
      - in: query
        name: question.parent_choice_id
        description: ID of Parent Question (for subquestions)
        type: query
      - in: query
        name: question.question.html
        description: Question displayed to the recipient
        type: query
      - in: query
        name: question.required
        description: Is an answer to this question required for registration?
        type: query
      - in: query
        name: question.respondent
        description: 'Ask this question to the ticket buyer or each attendee? (Valid
          choices are: ticket_buyer, or attendee)'
        type: query
      - in: query
        name: question.ticket_classes
        description: Tickets to which to limit this question
        type: query
      - in: query
        name: question.type
        description: 'Type of Question (Valid choices are: checkbox, dropdown, text,
          paragraph, radio, or waiver)'
        type: query
      - in: query
        name: question.waiver
        description: Waiver content for questions of type waiver
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Canned
      - Questions
  /events/{id}/questions/:
    get:
      summary: Get Events Questions
      description: |-
        Eventbrite allows event organizers to add custom questions that attendees fill
        out upon registration. This endpoint can be helpful for determining what
        custom information is collected and available per event.
      operationId: getEventsQuestions
      x-api-path-slug: eventsidquestions-get
      parameters:
      - in: query
        name: as_owner
        description: Return private events and more details
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Questions
    post:
      summary: Post Events Questions
      description: Creates a new question; returns the result as a question as the
        key question.
      operationId: postEventsQuestions
      x-api-path-slug: eventsidquestions-post
      parameters:
      - in: query
        name: question.choices
        description: Choices for multiple choice questions
        type: query
      - in: query
        name: question.display_answer_on_order
        description: Is this question displayed on order confirmation?
        type: query
      - in: query
        name: question.parent_choice_id
        description: ID of Parent Question Choice (for subquestions)
        type: query
      - in: query
        name: question.parent_id
        description: ID of Parent Question (for subquestions)
        type: query
      - in: query
        name: question.question.html
        description: Question displayed to the recipient
        type: query
      - in: query
        name: question.required
        description: Is an answer to this question required for registration?
        type: query
      - in: query
        name: question.respondent
        description: 'Ask this question to the ticket buyer or each attendee? (Valid
          choices are: ticket_buyer, or attendee)'
        type: query
      - in: query
        name: question.ticket_classes
        description: Tickets to which to limit this question
        type: query
      - in: query
        name: question.type
        description: 'Type of Question (Valid choices are: checkbox, dropdown, text,
          paragraph, radio, or waiver)'
        type: query
      - in: query
        name: question.waiver
        description: Waiver content for questions of type waiver
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Questions
  /events/{id}/questions/{id}/:
    get:
      summary: Get Events Questions
      description: This endpoint will return question for a specific question id.
      operationId: getEventsQuestions
      x-api-path-slug: eventsidquestionsid-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Questions
  /events/{id}/attendees/:attendee_id/:
    get:
      summary: Get Events Attendees Attendee
      description: Returns a single attendee by ID, as the key attendee.
      operationId: getEventsAttendeesAttendee
      x-api-path-slug: eventsidattendeesattendee-id-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Attendees
      - :attendee
  /events/{id}/orders/:
    get:
      summary: Get Events Orders
      description: Returns a paginated response with a key of orders, containing a
        list of order against this event.
      operationId: getEventsOrders
      x-api-path-slug: eventsidorders-get
      parameters:
      - in: query
        name: changed_since
        description: Only return orders changed on or after the time given
        type: query
      - in: query
        name: exclude_emails
        description: Don&#8217;t include orders placed by any of these emails
        type: query
      - in: query
        name: last_item_seen
        description: Only return orders changed on or after the time given and with
          an id bigger than last item seen
        type: query
      - in: query
        name: only_emails
        description: Only include orders placed by one of these emails
        type: query
      - in: query
        name: refund_request_statuses
        description: Return only orders with selected refund requests statuses
        type: query
      - in: query
        name: status
        description: 'Filter to active (attending), inactive (not attending), all
          (both) orders and all_not_deleted (active and inactive but not deleted)
          (Valid choices are: active, inactive, all, or all_not_deleted)'
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Orders
  /events/{id}/discounts/:
    get:
      summary: Get Events Discounts
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/users/#ebapi-get-users-user-id-discounts
      operationId: getEventsDiscounts
      x-api-path-slug: eventsiddiscounts-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Discounts
    post:
      summary: Post Events Discounts
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-post-discounts
      operationId: postEventsDiscounts
      x-api-path-slug: eventsiddiscounts-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Discounts
  /events/{id}/discounts/:discount_id/:
    get:
      summary: Get Events Discounts Discount
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-get-discounts-discount-id
      operationId: getEventsDiscountsDiscount
      x-api-path-slug: eventsiddiscountsdiscount-id-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Discounts
      - :discount
    post:
      summary: Post Events Discounts Discount
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-post-discounts-discount-id
      operationId: postEventsDiscountsDiscount
      x-api-path-slug: eventsiddiscountsdiscount-id-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Discounts
      - :discount
    delete:
      summary: Delete Events Discounts Discount
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-delete-discounts-discount-id
      operationId: deleteEventsDiscountsDiscount
      x-api-path-slug: eventsiddiscountsdiscount-id-delete
      responses:
        200:
          description: OK
      tags:
      - Events
      - Discounts
      - :discount
  /events/{id}/public_discounts/:
    get:
      summary: Get Events Public Discounts
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/users/#ebapi-get-users-user-id-discounts
      operationId: getEventsPublicDiscounts
      x-api-path-slug: eventsidpublic-discounts-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Public
      - Discounts
    post:
      summary: Post Events Public Discounts
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-post-discounts
      operationId: postEventsPublicDiscounts
      x-api-path-slug: eventsidpublic-discounts-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Public
      - Discounts
  /events/{id}/public_discounts/:discount_id/:
    get:
      summary: Get Events Public Discounts Discount
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-get-discounts-discount-id
      operationId: getEventsPublicDiscountsDiscount
      x-api-path-slug: eventsidpublic-discountsdiscount-id-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Public
      - Discounts
      - :discount
    post:
      summary: Post Events Public Discounts Discount
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-post-discounts-discount-id
      operationId: postEventsPublicDiscountsDiscount
      x-api-path-slug: eventsidpublic-discountsdiscount-id-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Public
      - Discounts
      - :discount
    delete:
      summary: Delete Events Public Discounts Discount
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-delete-discounts-discount-id
      operationId: deleteEventsPublicDiscountsDiscount
      x-api-path-slug: eventsidpublic-discountsdiscount-id-delete
      responses:
        200:
          description: OK
      tags:
      - Events
      - Public
      - Discounts
      - :discount
  /events/{id}/access_codes/:
    get:
      summary: Get Events Access Codes
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/users/#ebapi-get-users-user-id-discounts
      operationId: getEventsAccessCodes
      x-api-path-slug: eventsidaccess-codes-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Access
      - Codes
    post:
      summary: Post Events Access Codes
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-post-discounts
      operationId: postEventsAccessCodes
      x-api-path-slug: eventsidaccess-codes-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Access
      - Codes
    delete:
      summary: Delete Events Access Codes
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-delete-discounts-discount-id
      operationId: deleteEventsAccessCodes
      x-api-path-slug: eventsidaccess-codes-delete
      responses:
        200:
          description: OK
      tags:
      - Events
      - Access
      - Codes
  /events/{id}/access_codes/:access_code_id/:
    get:
      summary: Get Events Access Codes Access Code
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-get-discounts-discount-id
      operationId: getEventsAccessCodesAccessCode
      x-api-path-slug: eventsidaccess-codesaccess-code-id-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Access
      - Codes
      - :access
      - Code
    post:
      summary: Post Events Access Codes Access Code
      description: Please use https://www.eventbrite.com/developer/v3/endpoints/cross_event_discounts/#ebapi-get-discounts-discount-id
      operationId: postEventsAccessCodesAccessCode
      x-api-path-slug: eventsidaccess-codesaccess-code-id-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - Access
      - Codes
      - :access
      - Code
  /events/{id}/transfers/:
    get:
      summary: Get Events Transfers
      description: Returns a list of transfers for the event.
      operationId: getEventsTransfers
      x-api-path-slug: eventsidtransfers-get
      parameters:
      - in: query
        name: changed_since
        description: Only return transfers changed on or after the time given
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Transfers
  /events/{id}/teams/:
    get:
      summary: Get Events Teams
      description: Returns a list of attendee-team for the event.
      operationId: getEventsTeams
      x-api-path-slug: eventsidteams-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Teams
  /events/{id}/teams/{id}/:
    get:
      summary: Get Events Teams
      description: Returns information for a single attendee-team.
      operationId: getEventsTeams
      x-api-path-slug: eventsidteamsid-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Teams
  /events/{id}/teams/{id}/attendees/:
    get:
      summary: Get Events Teams Attendees
      description: Returns attendee for a single attendee-team.
      operationId: getEventsTeamsAttendees
      x-api-path-slug: eventsidteamsidattendees-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Teams
      - Attendees
  /events/:event_id/ticket_groups/:
    get:
      summary: Get Events Event Ticket Groups
      description: |-
        Get the list of ticket_group for the event with the specified :event_id.
        By default, only the ticket groups that are live are shown.
      operationId: getEventsEventTicketGroups
      x-api-path-slug: eventsevent-idticket-groups-get
      parameters:
      - in: query
        name: status
        description: 'Limits results to groups with the specific status (Valid choices
          are: live, archived, deleted, or all)'
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Ticket
      - Groups
  /events/:event_id/ticket_classes/:ticket_class_id/ticket_groups/:ticket_group_id/:
    post:
      summary: Post Events Event Ticket Classes Ticket Class Ticket Groups Ticket
        Group
      description: Add the Ticket Class with the specified :ticket_class_id that belongs
        to the event with :event_id to the Ticket Group identified by :ticket_group_id.
      operationId: postEventsEventTicketClassesTicketClassTicketGroupsTicketGroup
      x-api-path-slug: eventsevent-idticket-classesticket-class-idticket-groupsticket-group-id-post
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Ticket
      - Classes
      - :ticket
      - Class
      - Ticket
      - Groups
      - :ticket
      - Group
    delete:
      summary: Delete Events Event Ticket Classes Ticket Class Ticket Groups Ticket
        Group
      description: Remove the Ticket Class with the specified :ticket_class_id that
        belongs to the event with :event_id from the Ticket Group identified by :ticket_group_id.
      operationId: deleteEventsEventTicketClassesTicketClassTicketGroupsTicketGroup
      x-api-path-slug: eventsevent-idticket-classesticket-class-idticket-groupsticket-group-id-delete
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Ticket
      - Classes
      - :ticket
      - Class
      - Ticket
      - Groups
      - :ticket
      - Group
  /events/:event_id/ticket_classes/:ticket_class_id/ticket_groups/:
    get:
      summary: Get Events Event Ticket Classes Ticket Class Ticket Groups
      description: |-
        Get the Ticket Groups for Ticket Class with the specified :ticket_class_id that belongs to the event with :event_id.
        By default, only the ticket groups that are live are shown.
      operationId: getEventsEventTicketClassesTicketClassTicketGroups
      x-api-path-slug: eventsevent-idticket-classesticket-class-idticket-groups-get
      parameters:
      - in: query
        name: status
        description: 'Limits results to groups with the specific status (Valid choices
          are: live, archived, deleted, or all)'
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Ticket
      - Classes
      - :ticket
      - Class
      - Ticket
      - Groups
  /events/{id}/ticket_buyer_settings/:
    get:
      summary: Get Events Ticket Buyer Settings
      description: Returns a ticket_buyer_settings for an event.
      operationId: getEventsTicketBuyerSettings
      x-api-path-slug: eventsidticket-buyer-settings-get
      responses:
        200:
          description: OK
      tags:
      - Events
      - Ticket
      - Buyer
      - Settings
    post:
      summary: Post Events Ticket Buyer Settings
      description: Updates the ticket buyer settings for an event. Returns a ticket_buyer_settings.
      operationId: postEventsTicketBuyerSettings
      x-api-path-slug: eventsidticket-buyer-settings-post
      parameters:
      - in: query
        name: ticket_buyer_settings.confirmation_message.html
        description: Confirmation message to display on order completion
        type: query
      - in: query
        name: ticket_buyer_settings.instructions.html
        description: Instructions to display on the ticket
        type: query
      - in: query
        name: ticket_buyer_settings.redirect_url
        description: Redirect to this url post-purchase
        type: query
      - in: query
        name: ticket_buyer_settings.refund_request_enabled
        description: Whether refund requests are accepted for the event
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - Ticket
      - Buyer
      - Settings
  /organizers/{id}/events/:
    get:
      summary: Get Organizers Events
      description: Gets events of the organizer.
      operationId: getOrganizersEvents
      x-api-path-slug: organizersidevents-get
      parameters:
      - in: query
        name: only_public
        description: Only show public events even if viewing your own events
        type: query
      - in: query
        name: order_by
        description: 'How to order the results (Valid choices are: start_asc, start_desc,
          created_asc, or created_desc)'
        type: query
      - in: query
        name: start_date.range_end
        description: Only return events with start dates before the given date
        type: query
      - in: query
        name: start_date.range_start
        description: Only return events with start dates after the given date
        type: query
      - in: query
        name: status
        description: Only return events with a specific status set
        type: query
      responses:
        200:
          description: OK
      tags:
      - Organizers
      - Events
  /events/:event_id/tracking_beacons/:
    get:
      summary: Get Events Event Tracking Beacons
      description: Returns the list of tracking_beacon for the event :event_id
      operationId: getEventsEventTrackingBeacons
      x-api-path-slug: eventsevent-idtracking-beacons-get
      parameters:
      - in: query
        name: return_fmt
        description: returned format
        type: query
      responses:
        200:
          description: OK
      tags:
      - Events
      - :event
      - Tracking
      - Beacons
  /users/{id}/owned_events/:
    get:
      summary: Get Users Owned Events
      description: |-
        Returns a paginated response of events, under
        the key events, of all events the user owns (i.e. events they are organising)
      operationId: getUsersOwnedEvents
      x-api-path-slug: usersidowned-events-get
      parameters:
      - in: query
        name: order_by
        description: 'How to order the results (Valid choices are: start_asc, start_desc,
          created_asc, created_desc, name_asc, or name_desc)'
        type: query
      - in: query
        name: show_series_parent
        description: 'True: Will show parent of a serie instead of childrenFalse:
          Will show children of a serie (Default value)'
        type: query
      - in: query
        name: status
        description: Filter by events with a specific status set
        type: query
      responses:
        200:
          description: OK
      tags:
      - Users
      - Owned
      - Events
  /users/{id}/events/:
    get:
      summary: Get Users Events
      description: Returns a paginated response of events, under the key events, of
        all events the user has access to
      operationId: getUsersEvents
      x-api-path-slug: usersidevents-get
      parameters:
      - in: query
        name: currency_filter
        description: Filter event results by currency
        type: query
      - in: query
        name: event_group_id
        description: Filter event results by event_group_id
        type: query
      - in: query
        name: name_filter
        description: Filter event results by name
        type: query
      - in: query
        name: order_by
        description: 'How to order the results (Valid choices are: start_asc, start_desc,
          created_asc, created_desc, name_asc, or name_desc)'
        type: query
      - in: query
        name: page_size
        description: Number of records in each page
        type: query
      - in: query
        name: show_series_parent
        description: 'True: Will show parent of a serie instead of childrenFalse:
          Will show children of a serie (Default value)'
        type: query
      - in: query
        name: status
        description: Filter by events with a specific status set
        type: query
      - in: query
        name: time_filter
        description: Limits results to either past or current &amp; future events
          / orders
        type: query
      - in: query
        name: venue_filter
        description: Filter event results by venue IDs
        type: query
      responses:
        200:
          description: OK
      tags:
      - Users
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