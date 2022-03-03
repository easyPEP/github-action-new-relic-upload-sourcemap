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
    - uses: actions/checkout@v2
    - uses: frncsdrk/github-action-new-relic-upload-sourcemap@master
      with:
        api_key: ${{ secrets.NEW_RELIC_USER_API_KEY }}
        minified_url: https://example.com/assets/application.min.js
        minified_file: path/to/application.min.js
        source_map: path/to/application.js.map
```

## Inputs

Name | Required? | Default | Description
---|---|---|---
api_key | Y | N/A | TODO
app_id | Y | N/A | TODO
