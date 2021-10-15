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

# Notice

If you issue a certificate with too many domains with DNS alias mode. The TXT records' length will likely exceed the DNS provider's limit and fails ([acmesh-official/acme.sh#3748](https://github.com/acmesh-official/acme.sh/issues/3748)). To workaround this, this action will run acme.sh **multiple times** and issue a smaller certificate each time (so we can verify a smaller amount of domains each time). The result certificate will be fine.

# See also

You can deploy your newly issued SSL certificate to Azure Web App with the [Deploy SSL certificate to Azure Web App](https://github.com/marketplace/actions/deploy-ssl-certificate-to-azure-web-app) action.

You can deploy your newly issued SSL certificate to Aliyun Certificates Service and Aliyun CDN with the [Deploy SSL certificate to Aliyun](https://github.com/marketplace/actions/deploy-ssl-certificate-to-aliyun) action.
