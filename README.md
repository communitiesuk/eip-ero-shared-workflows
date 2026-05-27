# eip-ero-shared-workflows

This repository contains common GitHub Action workflows used by EROP repositories.

## Secrets

If the reusable workflow requires an implicit secret,
`secrets: inherit` should be specified.

For repositories using the shared workflows
each environment should have the environment secret `IAM_GITHUB_ROLE_ARN`
set to the AWS IAM role ARN of the GitHub role for that specific environment.

The repositories should also have a repository secret `PREPROD_IAM_GITHUB_ROLE_ARN`
set to the IAM role ARN of the read/write GitHub role for dev2 environment.
This role is used for deployments on merging to the `main` branch and the GitHub role
must be allowed to act on the `main` branch.
Note that this is a repository secret, not a GitHub Action environment secret.

The repositories should also have a repository secret `PREPROD_READ_ONLY_IAM_GITHUB_ROLE_ARN`
set to the IAM role ARN of a read only GitHub role in the AWS preprod account.
This is used when read-only access is sufficient, namely build/dependency checks
and fetching pre-prod ECR images before they are copied to the live environment.
This role must be useable on all branches, GitHub Action environments and pull requests.
Note that this is a repository secret, not a GitHub Action environment secret.

Any repositories using the `todo-check-with-slack-notify` workflow should also have 
the following repository secrets:
- `JIRA_USER` - see login for Jira user "svc-ier-todo-checker" for TODO checker, found in Keeper folder Elections
- `JIRA_PASSWORD` - use password for above user in Keeper
- `SLACK_TODO_CHECKER_ALERTS_WEBHOOK` - use contents of Todo Github Action Incoming Webhook Url, found in Keeper folder EIP EROP

Any repositories using the `send-slack-notification` workflow should have a repository 
secret `SLACK_TODO_CHECKER_ALERTS_WEBHOOK` - use contents of Todo Github Action Incoming Webhook Url, found in Keeper folder EIP EROP
