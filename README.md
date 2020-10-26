# Zowe CLI

GitHub action for create Zowe zosmf profile.

### Workflow

It's recommended that you use [GitHub encrypted secrets](https://docs.github.com/en/actions/reference/encrypted-secrets) to store `ZOSMF_OPTION_NAME`, `ZOSMF_OPTION_HOST`, `ZOSMF_OPTION_PORT`, `ZOSMF_OPTION_USER`, `ZOSMF_OPTION_PASSWORD` and `ZOSMF_OPTION_REJECT_UNAUTHORIZED` information.

#### Example

```yml
name: Create Zowe CLI profile
on:
  push:
    branches: [ master ]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Zowe CLI
        uses: richardnas/zowe-action@v1
        with:
          ZOSMF_OPTION_NAME: ${{ secrets.ZOSMF_OPTION_NAME }}
          ZOSMF_OPTION_HOST: ${{ secrets.ZOSMF_OPTION_HOST }}
          ZOSMF_OPTION_PORT: ${{ secrets.ZOSMF_OPTION_PORT }}
          ZOSMF_OPTION_USER: ${{ secrets.ZOSMF_OPTION_USER }}
          ZOSMF_OPTION_PASSWORD: ${{ secrets.ZOSMF_OPTION_PASSWORD }}
          ZOSMF_OPTION_REJECT_UNAUTHORIZED: ${{ secrets.ZOSMF_OPTION_REJECT_UNAUTHORIZED }}
      - run: zowe zos-files list ds DATASETNAME -a --responseTimeout 60
```

