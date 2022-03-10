# github-action-new-relic-upload-sourcemap

GH Action to upload sourcemaps to New Relic

## Example

```yaml
on:
  push:
    branches:
      - master

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - run: |
        echo "REMOTE_URL=$(git remote get-url origin)">>$GITHUB_ENV
    - uses: easyPEP/github-action-new-relic-upload-sourcemap@master
      with:
        api_key: ${{ secrets.NEW_RELIC_USER_API_KEY }}
        app_id: ${ secrets.NEW_RELIC_APP_ID }
        sourcemap_path: path/to/application.js.map
        javascript_url: https://example.com/assets/application.min.js
        release_id: ${GITHUB_SHA}
        release_name: prod-${GITHUB_SHA}
        github_repository_url: ${REMOTE_URL}
```

## Inputs

Name | Required? | Default | Description
---|---|---|---
api_key | Y | N/A | A valid user API key
app_id | Y | N/A | A valid application id
sourcemap_path | Y | N/A | Path to the sourcemap file
javascript_url | Y | N/A | URL of the file on your server
release_id | N | Commit Hash | Unique id for the release, e.g. git hash or semver, default git commit hash
release_name | N | Commit Hash | Name for the release, e.g. `v1.0`, default git commit hash
github_repository_url | Y | N/A | URL of the repository

## License

[MIT][License] (c) 2022 easyPEP and contributors

[License]: https://github.com/easyPEP/github-action-new-relic-upload-sourcemap/blob/master/LICENSE
