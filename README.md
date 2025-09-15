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
