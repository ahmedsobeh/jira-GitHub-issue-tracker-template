# Jira-GitHub-issue-tracker-template 

This is a template repo that syncs your GitHub issues to your Jira project as tickets.

## How and what does it actually track?

After opening an issue in the repo, a corresponding jira ticket is added to the backlog. The issue
creator is the Jira ticket reporter.

The title gets automatically updated to contain the ticket number on Jira.

The ticket status can be changed using simple comments on the github issue.

#### - An "in progress" label on the issue sets the ticket status to "In Progress".
#### - A "waiting for upstream" label on the issue sets the ticket status to "Waiting for upstream release".
#### - A "selected for development" label on the issue sets the ticket status to "Selected for Development".
#### - Closing the issue sets the ticket status to "Done" and automatically sets the "done" label.

The ticket gets assigned to the person who changes the status, i.e adds one of the above labels.

All discussions/comments on the GitHub issue are mirrored on the Jira ticket(except status changing comments).

## How do I make my actions count?

To be able to create and update issues/tickets, 2 steps are needed.

1. Create a [Jira API token](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/)
2. Create an [actions secret](https://github.com/aiven/ospo-tracker/settings/secrets/actions) (settings -> secrets -> actions), use your github ID as the name of the secret (some limitations apply, see below).  The value should comprise your email and Jira token separated by a comma like this: `ahmed.sobeh@aiven.io,tEstJiratOkEnForReAdMe`

#### Secret names limitations

```
Secret names can only contain alphanumeric characters ([a-z], [A-Z], [0-9]) or underscores (_).
Spaces are not allowed. Must start with a letter ([a-z], [A-Z]) or underscores (_).
```

Please make sure to execute these two steps before opening an issue, otherwise nothing will happen on Jira side when you do!

#### Notes

1. The new tickets will be added to Jira when the issue is opened.
2. Tickets are assigned in Jira to the person that moves them from backlog.  If this is not the correct person the Jira ticket will need to be edited.
3. Tickets that are assigned in Jira will have the Jira number prefixed to the title.
4. As tickets are progressed (`backlog` -> `selected for development` -> `in progress` -> `waiting for upstream`) the state changes in Jira.
5. When progressing the ticket in github remove the earlier state label.
