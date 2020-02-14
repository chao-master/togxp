# togxp

Toggl to crm timesheet export script

## Configuration

* `Toggl.ApiKey` - Your Toggl API token, findable on your toggl [profile page](https://toggl.com/app/profile).
* `Toggl.Workspace` - The Toggl workspace to target, to find visit the [dashboard](https://toggl.com/app/dashboard/me) for the workspace, and copy the number from the url
* `Crm.Username` - User to log the time entries under on CRM, including domain
* `Output.DefaultLocation` - Default location to output to if `--outfile` is passed without a parameter
* `Projects` - Array of Toggl to CRM lookup rules, rules are evaluated in order and the first one that matches is used.

### Lookup rules

Each lookup rule can specify checks against the client, the project, or both. If both are specified they both need to match for the rule to be valid. If a rule specifies none, then it will match any time entry.

You can either specify a Regex rule or a plain string rule. If you specify both the Regex rule will override the plain text rule.

* `ClientRegex` - A regular expression to match against the name of the client for the toggl time entry.
* `Client` - A string that needs to exactly match the name of the client.
* `ProjectRegex` - A regular expression to match against the name of the project for the toggl time entry.
* `Project` - A string that needs to exactly match the name of the project.

Lookup rules then state how to log the information into CRM. At least one of order or opportunity needs to specified.

* `Order` - The ID of the Order to log against.
* `Opportunity` - The ID of the Opportunity to log against.