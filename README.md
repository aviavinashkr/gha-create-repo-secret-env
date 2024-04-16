# GitHub Action - Secret creation/updation

This action is made for creating and updating GitHub secrets for a specific environment.

## Usage

The action is quite simple and can be used for any GitHub organization, the main need is an [Personal Access Token] with the necessary permissions.

When something go wrong the action will throw an error and break the workflow.

### Example workflow

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Run action

      uses: nestle-it/gha-create-repo-secret-for-env@main
      with:
        GitHubToken: ${{ secrets.PAT }}
        SecretName: "secret-name"
        SecretValue: "secret-value"
        Environment: "dev"
        Organization: "nestle-it"
        Repository: "repository name"

```

### Inputs

| Input                                             | Description                                        |
|------------------------------------------------------|-----------------------------------------------|
| `GitHubToken`  | Personal access token from GitHub - it must have permission to create projects in the requested organization    |
| `SecretName`  | Secret name that needs to be added to a specific reposistpory within an environment    |
| `SecretValue`  | Secret value that needs to be created/updated to a specific reposistpory within an environment    |
| `Environment`  | Environment to which the secret needs to be created/updated    |
| `Organization`   | Organization where to create the environments    |
| `Repository`   | Repository name where the environment secret needs to be created/updated  |

## Examples

### Using the optional input

This is how to use the optional input.

```yaml
    uses: ./gha-create-repo-secret-for-env/
    with:
      GitHubToken: ${{ secrets.PAT }}
      SecretName: "ClientID"
      SecretValue: "ClientID_Value"
      Environment: "dev"
      Organization: "nestle-it"
      Repository: "npet-testingsolutionrepo"
```
