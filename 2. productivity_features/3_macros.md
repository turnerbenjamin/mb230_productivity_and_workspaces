# Macros

Macros are just flows which may be manually triggered by agents. They can be
used to:

- Speed-up common tasks
- Reduce human error
- Encourage process compliance

**Note**, macro flows have a different UI from the powerautomate flows. We can,
however, call a powerautomate flow from a macro using the flow connector.

## Automation Dictionary

The automation dictionary holds contextual data for sessions. We are able to use
this dictionary to insert dynamic values into macros and slugs. The automation
dictionary gets data from a number of sources:

- Channel providers may include context data, e.g. from pre-chat surveys
- User actions, like opening a new record may be stored as context data
- Odata queries may be used to query the dataverse
- Macro actions may generate context data used by later actions

We can access this data using:

- Slugs
- Odata queries
- Static values

In the following activity, we will use the automation dictionary to get context
data for our macro. We will access this data with slugs.

## Creating a Macro (Activity)

For this activity we will create a new macro which will create a case from a
letter.

**Declare the macro:**

1. Navigate to Admin Center -> Productivity -> Macros
2. Select New from the command bar
3. Enter a name, e.g. {your initials} Create Case
4. Enter a description, e.g. create case from an email

**Set the trigger**

5. Select start macro execution as the trigger

**Get the anchor tab id. This will be used later to refresh the tab**

6. Add a Get the Current Tab action

**Open a new case form**

7. Add an Open a new form to create a record action
8. Set entity logical name to incident

**Populate the title field**

9. Add a new Productivity Automation Action, Autofill form fields
10. Use the entity logical name dynamic value for entity logical name
11. Set Attribute Name - 1 to title
12. Set Attibute Value - 1 to {anchor.subject}

**Mark the letter activity as complete**

13. Add an Update an Existing record action
14. Set the entity logical name to letter
15. Set the entity record id to {anchor.activityid}
16. In advanced options set attribute name to statecode and the value to 1

**Refresh the anchor tab to show updated status**

17. Add a Refresh the Tab action
18. Set the tabId to the dynamic value from the Get the Current Tab step

**Save and Close**

19. Save and close the macro

## Using A Macro

Macros can be triggered by:

- An API call
- Manually by agents from the productivity pane

For MB-230, the relvant option is through the productivity pane. To do this we
will need to create and Agent Script.

## Debugging Macros

To view executions of a given macro, select view run history. This will show
whether the exection was successful or not.

Opening an execution will show where the macro failed and the values that
variables held during the run.
