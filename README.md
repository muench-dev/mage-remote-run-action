# mage-remote-run-action

A GitHub Action to install and configure [mage-remote-run](https://www.npmjs.com/package/mage-remote-run).

## Usage

### Basic Usage (OAuth)

```yaml
steps:
  - name: Setup Node.js
    uses: actions/setup-node@v4
    with:
      node-version: '20'

  - name: Setup Mage Remote Run
    uses: ./ # Or your-org/mage-remote-run-action@v1
    with:
      profile-name: "MyStore"
      type: "ac-on-prem" # or magento-os, mage-os
      url: "https://example.com"
      consumer-key: ${{ secrets.MAGE_CONSUMER_KEY }}
      consumer-secret: ${{ secrets.MAGE_CONSUMER_SECRET }}
      access-token: ${{ secrets.MAGE_ACCESS_TOKEN }}
      token-secret: ${{ secrets.MAGE_ACCESS_TOKEN_SECRET }}
```

### Bearer Token Authentication

```yaml
steps:
  - name: Setup Mage Remote Run
    uses: ./
    with:
      profile-name: "MyCloudStore"
      type: "ac-cloud-paas"
      url: "https://example.com"
      auth-method: "bearer"
      token: ${{ secrets.MAGE_BEARER_TOKEN }}
```

### Inputs

| Input | Description | Required | Default |
| --- | --- | --- | --- |
| `version` | Version of mage-remote-run to install | No | `latest` |
| `profile-name` | Profile Name | No | `default` |
| `type` | System Type (`magento-os`, `mage-os`, `ac-on-prem`, `ac-cloud-paas`, `ac-saas`) | **Yes** | |
| `url` | Instance URL | **Yes** | |
| `auth-method` | Auth Method (`bearer`, `oauth1`) | No | |
| `client-id` | Client ID (SaaS) | No | |
| `client-secret` | Client Secret (SaaS) | No | |
| `token` | Bearer Token | No | |
| `consumer-key` | Consumer Key (OAuth1) | No | |
| `consumer-secret` | Consumer Secret (OAuth1) | No | |
| `access-token` | Access Token (OAuth1) | No | |
| `token-secret` | Token Secret (OAuth1) | No | |
| `signature-method` | Signature Method (`hmac-sha256`, `hmac-sha1`) | No | |
| `active` | Set as active profile | No | `true` |
| `no-test` | Skip connection test | No | `false` |
