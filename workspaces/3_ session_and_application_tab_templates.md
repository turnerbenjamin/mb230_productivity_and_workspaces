# Session and Application Tab Templates

## What are Session and Application Tabs?

While working with a customer on a case, an agent may want access to additional
pages containing context not available within the case/activity record.

In addition, an agent may need to work on multiple customers/issues at once. For
each customer/issue the agent may want a separate set of context pages.

Without an in app tabbing feature, the agent may choose to have a separate
browser window for each customer/issue and use tabs in each window to hold
context pages.

This could become unwieldy, so Customer Service has the concepts of session and
application tabs:

### Sessions

These tabs are near the top of the page, level with the site-map menu. Session
tabs separate different issues/customers. Using the example above, they are
analogous to different browser windows.

### Application Tabs

These are tabs within a session. Each session has its own set of application
tabs. Application tabs are used to separate different context pages relevant to
the issue that is the subject of the session. Using the example above,
application tabs are analogous to tabs within the different browser windows.

## Creating a Session Template (Activity)

We will now create a simple session template

### Step 1: Create an Application Tab Template (optional)

All session templates have an anchor tab. This tab cannot be closed and cannot
be modified. However, we can create additional application templates that will
open when the session opens:

1. Navigate to Admin Center -> Workspaces -> Application tab templates
2. Select New from the command bar
3. Provide a name, e.g. {your initials} - Customer Summary
4. Provide a unique name, e.g. {your initials}\_customerSummary
5. Set title, e.g. Customer Summary
6. Set page type to Entity Record
7. Optionally, give a description
8. Set can close to Yes
9. Save the record

Once the record has been saved we will see a list of parameters. The contents
of this list depend on the Page Type. We will come back to these shortly

### Step 2: Create a Session Template

Next, we will create a session template which will use our custom application
tab template.

1. Navigate to Admin Center -> Workspaces - Session templates
2. Select New from the command bar
3. Provide a name, e.g. {your initials} Case Session
4. Provide a unique name, e.g. {your initials}\_caseSession
5. Set Type as Entity and Entity as Case
6. Save the record
7. In additional tabs, select Add Existing Application Tab Template
8. Select your custom application tab template
9. Save the record again

### Step 3: Apply the Session Template

Next we need to apply the template to our custom profile:

1. Navigate to Admin Center -> Workspaces -> Agent Experience Profiles
2. Select your custom profile
3. Select Add entity session templates
4. Click add
5. Set Entity to Case and find your session template
6. Save and close

### Step 4: Test the template

We can now test the template.

1. Open Workspace and refresh the page
2. Open a case in a new session (shift+click)
3. Check that the application tabs includes:
   - An anchor tab with the case
   - An additional tab with the title you provided

This can take a minute to apply. If the application tabs do not open as expected
refresh and try again.

### Step 5: Fixing the Template

Currently, our custom application tab should be broken. This is because the tab
has no way of knowing what it should show. This is where the variables section
of the application tab template is used.

As mentioned, the variables listed will depend on the template type. We must
manually assign values to these variables to use them. Generally, we will do
this using slugs which reference the anchor tab object.

For the entity record type the only required variable is entity name, i.e. the
logical name of the table that the record belongs to. If we provide the entity
name only, a create record form will open.

We can add an additional variable, validateRecord and set the value to true,
in this case, if there is no record the tab simply will not open. This may be
useful if we want separate tabs depending on whether the customer is a contact
or an account.

For our purposes, showing the customer record, we will also need to provide the
entity id.

1. Navigate to your application tab
2. Set entityName to: {anchor._customerid_value@Microsoft.Dynamics.CRM.lookuplogicalname}
3. Set entityId to: {anchor.\_customerid_value}

### Step 6: Retest

We can now retest the tab, following the steps from step 4. Remember that the
changes will not be applied right away and you may need to refresh a few times.

## Generic Templates

In the activity above we created an entity specific session template. These are
used with Agent Experience Profiles and are used when a session of the relevant
type is opened.

We can only assign one template to each record type, e.g. for case and account

If we want to add a template to a workstream, applying to all sessions opened
for items from that workstream, we need to use a generic session template.

The main difference in terms of creation is that we must specify the anchor tab
explicitly and should define it with this in mind.

First, when we define a generic session template we are required to set the
anchor tab explicitly.

### Exploring Generic Templates (Activity)

In this activity, we will look at the default templates to understand how they
work.

1. Navigate to your custom Agent Experience Profile, notice that:
   - We are attaching "entity session templates"
   - That we can only specify one template per entity type
2. Navigate to Workstreams and select a workstream, notice that:
   - When you edit sessions, only generic sessions are permitted
   - The session template used will be named with the channel in mind
3. Select the current session template used, notice that:
   - The type is set to generic
   - The anchor tab is a required field
4. Select the application tab template used as the anchor tab, notice that:
   - The tab is designed to accomodate any items from the channel
