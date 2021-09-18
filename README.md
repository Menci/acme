# GitHub Action for acme.sh

Issue SSL certificate with acme.sh's DNS API mode.

You probably want to use this action in a private repo, to upload your issued SSL certificate to repo.

# Usage

```yaml
jobs:
  issue-ssl-certificate:
    name: Issue SSL certificate
    runs-on: ubuntu-latest
    steps:
      - uses: Menci/acme@beta-v1
        with:
          version: 3.0.0
          account-conf-content: ${{ secrets.ACME_SH_ACCOUNT_CONF }}
          domains: example.com example.net example.org example.edu
          domains-file: ''
          append-wildcard: true
          arguments: --dns dns_cf --challenge-alias example.com
          arguments-file: ''
          output-fullchain: output/fullchain.pem
          output-key: output/key.pem
          output-pfx: output/certificate.pfx
          output-pfx-password: qwq
```

# See also

You can deploy your newly issued SSL certificate to Azure Web App with the [Deploy SSL certificate to Azure Web App](https://github.com/marketplace/actions/deploy-ssl-certificate-to-azure-web-app) action.
