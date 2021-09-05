# GitHub Action for acme.sh

Issue SSL certificate with acme.sh's DNS API mode.

```yaml
jobs:
  issue-ssl-certificate:
    name: Issue SSL certificate
    runs-on: ubuntu-latest
    steps:
      - use: Menci/acme@beta-v1
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
