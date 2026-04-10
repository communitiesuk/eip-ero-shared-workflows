# eip-ero-shared-workflows

This repository contains common GitHub Action workflows used by EROP repositories.

## Secrets

If the reusable workflow requires an implicit secret,
`secrets: inherit` should be specified.

For repositories using the shared workflows
each environment should have the environment secret `IAM_GITHUB_ROLE_ARN`
set to the AWS IAM role ARN of the GitHub role for that specific environment.

The repositories should also have a repository secret `PREPROD_IAM_GITHUB_ROLE_ARN`
set to the IAM role ARN of the GitHub role for a preprod environment,
which could be the `dev2` role.
Note that this is a repository secret, not an environment secret.

Any repositories using the `todo-check-with-slack-notify` workflow should also have 
the following repository secrets:
- `JIRA_USER` - see login for Jira user "Digital Tools Jira" for TODO checker, found in Keeper folder Elections
- `JIRA_PASSWORD` - use password for above login in Keeper
- `SLACK_TODO_CHECKER_ALERTS_WEBHOOK` - use contents of Todo Github Action Incoming Webhook Url, found in Keeper folder EIP EROP

Any repositories using the `send-slack-notification` workflow should have a repository 
secret `SLACK_TODO_CHECKER_ALERTS_WEBHOOK` - use contents of Todo Github Action Incoming Webhook Url, found in Keeper folder EIP EROP
