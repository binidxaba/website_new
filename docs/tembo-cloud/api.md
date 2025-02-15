---
sidebar_position: 4
tags:
  - api
  - authentication
---

# API

To explore the Tembo Cloud API, visit our [API documentation](/docs/tembo-cloud/openapi).

## Authentication 

### Create a service user

To avoid accidentally signing in with your personal Tembo Cloud user when creating a new user, make sure you are not signed into Tembo Cloud, and if applicable, also not signed into your Google account in your browser. Using an incognito window or another browser for this step is recommended.

Sign up with your service user here https://accounts.tembo.io/sign-up with the email / password option

:::caution
Do not use Google, GitHub, or any other third party authentication option.
:::

Then log into the email account of your service user, and confirm.

:::info
There is no need to create a new Tembo Organization with your service user.
:::

### Invite a service user to your organization

- Log into Tembo Cloud with your personal email
- Invite your service user to your organization(s) using [this link](https://accounts.tembo.io/organization)
- In the service user's email, accept the invitation
- Log in as the service user, confirming you have access to the Tembo Organization

### Create a long-lived API token

- We will use the service user's email / password combination to login to Tembo Cloud. Then, we will issue a long-lived API token that can be used for non-interactive authentication with Tembo Cloud.
- You will need to have `curl` and `jq` installed for the following step.
- Run the following command to interactively create a long-lived API token that expires in a configurable number of days.

```shell
bash <(curl -Ls https://raw.githubusercontent.com/tembo-io/website/main/docs/tembo-cloud/scripts/issue-token.sh)
```

- Then, you can use this token in API requests to Tembo Cloud, for example:

```shell
export TOKEN='******'

curl "https://api.tembo.io/api/v1/orgs/instances/schema" \
  -H "authorization: Bearer ${TOKEN}"
```

- You can try the Tembo Cloud API using this token in our [Interactive API documentation](https://api.tembo.io/swagger-ui/) by clicking the "Authorize" button.
