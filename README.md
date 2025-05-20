# matos-sast-github-actions
MatosSphere SAST GitHub Action


## Simple usage example

```yaml
# Steps represent a sequence of tasks that will be executed as part of the job
steps:
  # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
  - uses: actions/checkout@v4

  # Scan your templates or IaC with MatosSphere
  - name: run matossphere scan
    uses: cloudmatos/matos-sast-github-actions@latest
    with:
      # Scanning a directory named "template"
      scan_dir: ${{ secrets.SCAN_DIR }}
      api_key: ${{ secrets.MATOS_API_KEY }}
      tenant_id: ${{ secrets.MATOS_TENANT_ID }}
```



## Set Secrets for Project

To use this GitHub Action, you need to securely store your MatosSphere API credentials in your repository's secrets.

1. Go to your GitHub repository.
2. Click on Settings.
3. In the left sidebar, click Secrets and variables → Actions.
4. Click the New repository secret button
5. Add the following secrets:

    | Name                | Description                            |
    |:--------------------|:---------------------------------------|
    | SCAN_DIR            | DIrectory to scan (e.g. ".", "src")    |
    | MATOS_API_KEY       | Your MatosSphere API key               |
    | MATOS_TENANT_ID     | Your MatosSphere tenant ID             |

6. Click Add secret after entering each one.

These secrets will be referenced in your workflow like this:

```yaml
with:
  scan_dir: 'template'
  api_key: ${{ secrets.MATOS_API_KEY }}
  tenant_id: ${{ secrets.MATOS_TENANT_ID }}
```