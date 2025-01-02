# Additional Productivity Features

## Overview

There are a number of productivity features which are covered in the course
materials but not mentioned explicitly in the learning outcomes. These will be
covered briefly here.

## Enable the Sharing of Knowledge Articles

Agents may find it helpful to share knowledge articles with customers. This is
done by sharing a link to the article.

To enable this we first need to make the article publically accessable. We can
do this by deploying a Power Platform portal with the Customer Service Template.
All articles, not marked as internal, will be publically accessible through
this portal.

Next, we need to tell Customer Service where the articles are hosted. To do this
navigate to Admin Center -> Knowledge -> Portal.

We can then enable Use External Portal and provide a url to the the support
portal.

Once the portal has been set-up and linked to Customer Service agents will have
access to an option to copy an article link from the knowledge search control.
They can then send this link to the customer.

## Email Templates

Create email templates from Admin Center -> Productivity -> Email Templates.

This process is straight forward the only things to note are:

- We can add slugs manually or by using the Insert Dynamic Text button in the
  command bar
- Templates have a category which associates them with a given entity, e.g.
  cases. This will likely impact which slugs are populated
- There are permission levels of individual or organisation.

Agents are also able to create email templates from workspaces and hub. There is
an email templates option in the site map for both apps.

To use a template, we can use the Insert Template button from the email form.

## Contextual/Enhanced Email

Contextual email, also termed enhanced email, is a feature that allows the email
form to be opened as a popup rather than in a new tab. This enables users to
create an email without leaving the record.

The form used will not change, just the location of the form.

Contextual email is only available when creating an email from the timeline and
it must be enabled.

To enable contextual email navigate to:

Advanced Settings -> Email Configuration -> Email Configuration Settings and
enable the option under Enhanced email for timeline.

## Configure Email Forms

There are a number of forms used for email out of the box with slight
differences, for example, the Email for Interactive Experience form displays
attachments with thumbnails rather than as a list.

We can configure the display of attachments in email forms using make.powerapps

To use a given form by default, navigate to the email table in make.powerapps
and select forms. In form settings change the form order so that the prefered
form is displayed first in the list.

## Email Attachment Size Limits

There is not limit on the number of attachments on emails, however, there is a
limit on the size of individual email attachments. By default the limit is 5mb.

We can increase this to a maximum of 128mb by navigating to the environment in
admin.powerplatform and selecting Settings -> Email Settings.

## Timeline Configuration

Timelines are components of forms. We can add a timeline to a form or configure
a timeline contained in an existing form.

To configure the timeline find the relevant form in make.powerapps and select
the timeline component. This opens a panel containing configuration options.

There are various options, but for MB-230 the main thing to note is that we can
configure the types of records shown.

Note that a form can contain a maximum of 1 timeline and that timelines can only
be included in forms with a type of main.
