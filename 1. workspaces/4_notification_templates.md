# Notification Templates

## Intro

Notification templates allow us to control how incoming notifications are
displayed to users and the behaviour of those notifications.

Notifications may be displayed for:

- An incoming chat, text or social channel conversation
- A chat being transferred from another agent
- Conversation escalated by another agent or bot

## Create a Notification Template (Activity)

We are going to create a notification template for unauthenticated chat. This
is because it is the easiest template to test:

1. Navigate to Admin Center -> Workspaces -> Notifications
2. Click New Notification Template
3. Add a name, e.g. {your initials} Demo Unauthenticated Notification
4. Add a unique name, e.g. {your initials}\_demoUnauthenticatedNotification
5. Add a title, e.g. Demo: {headerText}

Note, the title uses a slug, the curly braces are required here. We will look at
slugs in more detail later.

### Auto-Assign Work Items and Show Reject Button

If auto-assign work items is enabled, the agent receiving the notification will
automatically be assigned the activity. Assignment will happen when:

- The agent clicks the accept button
- The timeout has expired

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
3. Search for Comment for the user and select add

There is a wide variety of fields we can choose from. In all cases the values of
these fields will be populated using the Automation Dictionary.

The automation dictionary is covered later, the main thing to note at this point
is that:

- Slugs are one of the formats understood by the Automation Dictionary
- If a value cannot be found it will be empty

Since we are designing a notification template for unauthenticated users, it
would not make sense to use the Name of the customer field.

### Using Notification Templates (Activity)

To use a notification template, we need to associate it with a worksteam.

1. Navigate to Admin Center -> Workstreams
2. Select any chat workstream
3. At the bottom of the workstream form select show advanced settings
4. Select edit in the agent notification section
5. Add your template to the Incoming Unauthenticated trigger

### Testing Notification Templates (Optional Activity)

1. Create a new html file
2. Add the boilerplate, e.g. with an emmet abbreviation
3. Near the top of the chat channel, select Copy Live Chat Widget Script
4. Paste this into the head of the html
5. Open Workspaces and the html file in seperate browser windows
6. Start a chat in the html file
7. Verify that the notification template displays as intended

## Notification Configuration

In addition to defining notification templates, we can also configure options
which apply generally to all notifications. These options can all be found from:

Admin Center -> Workspaces -> Notifications

### Missed Notifications

The missed notifications tab contains a single option, change agent status to
inactive after a missed notification.

This status change is useful when:

- Unified routing is set-up with work auto-assigned to agents, AND
- The workstream/s do not have away set as an allowed presence

If these conditions are met, the agent will no longer be auto-assigned work
until they manually change their status to an allowed presence.

### Agent Reject

This tab is very similar to the Missed Notification tab. It contains a single
option, change agent status to do not disturb when the agent rejects a
notification.

Again, this is designed to be used in conjunction with unified routing where
Busy - DND is not set as an allowed presence.

### Sound Notifications

In this tab we can able sound notifications, once enabled there is a range of
options to configure sound notifications by channel:

- Play sound: enable sound notifications for the channel
- Sound: the sound to be played
- Repeat until answered
- Volume

## Summary

Agent notifications can be used to display contextual data to agents about an
incoming conversation. There are a variety of triggers for notifications, e.g.
depending on whether or not the customer is authenticated.

We can provide contextual data using the Automation Dictionary. The easiest way
to interact with this dictionary is with slugs. We should be mindful of the
data that will be available for a given trigger when designing our templates.
