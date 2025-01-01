# Notification Templates

## Intro

Notification templates allow us to control how incoming notifications are
displayed to users and the behaviour of those notifications.

Notifications may be displayed for:

- An incoming chat, text or social channel conversation
- A chat being transferred from another agent
- Conversation escalated by another agent or bot

## Create a Template (Activity)

1. Navigate to Admin Center -> Workspaces -> Notifications
2. Click New Notification Template
3. Add a name, e.g. {your initials} Demo Notification
4. Add a unique name, e.g. {your initials}\_demoNotification
5. Add a title, e.g. Incoming Chat Notification

### Auto-Assign Work Items and Show Reject Button

If auto-assign work items is enabled, the agent receiving the notification will
automatically be assigned the activity.

The option to show a reject button is locked on false and the accept button
text is set to true.

I cannot find out what the behaviour is if auto-assign is set to false and show
reject button is set to false.

### Show Desktop Notifications

These notifications are useful when the app is out of focus as they reduce the
risk of a notification being missed.

We can set this to:

- Never
- Always
- When app is in the background

However, where desktop notifications are enabled we need to endure that:

- Supported browsers are being used by agents
- Notifications are enabled
- The browser is not in incognito mode

### Notification Fields (Activity)

Notification fields are uded to display information to the agent. We can add
predefined fields or define our own.

1. Save the draft notification template
2. Select Add Existing Notification Field
3. Search for Name of the Customer and select Add

It looks like any fields we add here will be shown to the agent receiving the
notification. The values of the fields are populated using the Automation
Dictionary. This supports:

- Slugs
- OData Queries
- Static values

### Notification Slugs (Activity)

In addition to notification fields, we can also use slugs in the notification
itself.

1. Look at the slug associated with the Name of the Customer Field
2. Use this in the title, e.g. Incoming conversation: {customerName}
3. Save the template

A slug is based on context variables at runtime. Slugs available in this context
include:

- customerName
- caseTitle

### Using Notification Templates (Activity)

To use a notification template, we need to associate it with a worksteam.

1. Navigate to Admin Center -> Workstreams
2. Select any chat workstream
3. At the bottom of the workstream form select show advanced settings
4. Select edit in the agent notification section
5. Add your template to one of the notifications

Note, that the notification we defined used the {customerName} slug, this may
not be populated depending on the notification, e.g. for Incoming
Unauthenticated. The default notification templates include the name of the
notification in them to help avoid the use of unset context variables.
