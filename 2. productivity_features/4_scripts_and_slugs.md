# Scripts and Slugs

Scripts are used to provide guidance to agents, the consist of a series of
steps. As an agent progresses through the steps, an icon will be shown:

- Green tick: Completed
- Red Cross: Error

Scripts can include a number of step types including:

- Text
- Macro
- Agent Script (Nested)

## Slugs

We have seen the use of slugs already in the macros section. We will use slugs
in the activity below to show usage in the context of Agent Scripts.

## Create a Script (Activity)

1. Navigate to Admin Center -> Productivity -> Agent Scripts
2. Select New from the Command Bar
3. Enter a name, e.g. {your initials} Letter to Case Script
4. Enter a unique name, e.g. {your initials}\_letterToCaseScript
5. Save the script
6. Add a new scrip step
7. Set the name to Read the Letter
8. Set the unique name to {your initials}\_readTheLetter
9. Set the order to 1
10. Set the action type to text
11. Enter the text instructions, e.g. Read the letter with the subject:
    {anchor.subject}
12. Save and close the step
13. Add a new script step
14. Set the name to create a case
15. Set the unique name to {your initials}\_createACase
16. Set the order to 2
17. Set the action type to macro
18. Set the target macro to your custom macro
19. Save and close the step
20. Save and close the script

## Associate the Script with a Session Template (Activity)

We need to create a session template linked to the letter entity.

1. Navigate to Admin Center -> Workspaces -> Session Templates
2. Select New from the command bar
3. Add a name, e.g. {your initials} Letter Session
4. Add a unique name, e.g. {your initials}\_letterSession
5. Set type to entity and entity to letter
6. Save
7. In the agent scripts tab select add existing agent script
8. Add the script you created above
9. Navigate to your custom Agent Experience Profile
10. Add the session template with entity set to letter
11. Check that the productivity pane is enabled
12. Check that agent scripts is turned on in the production pane

Note, we have associated the session template with an Agent Experience Profile
because the type is set to entity. If the type was generic we would associate
it with a workstream.

## Testing the Script (Activity)

1. Navigate to Customer Service Workspace
2. Select activities from the site map
3. Select letter from the command bar
4. Set the direction to Incoming
5. Select from to a customer record
6. Set the subject, e.g. I have issues
7. Save the letter
8. The script should display in the agent scripts panel. Note that this may take
   a few minutes
9. Work through the script
