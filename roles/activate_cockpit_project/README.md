# `activate_cockpit_project` role

This role configures Scaleway's [Observability feature](https://www.scaleway.com/en/betas/#observability) by activating a Cockpit instance and creating a push token for your metrics and logs.

It produces a `./facts.json` file that contains user's observability credentials in order to be used in another context or role.

For more details, refer to [Scaleway's Observability documentation](https://developers.scaleway.com/en/products/observability/api/v1alpha1).

## Requirements

- A Scaleway account with Observability access
- A token API key with Observability access policies (see details below)

## User role variables

| Name                  | Type     | Description                                                                                   |
| --------------------- | -------- | --------------------------------------------------------------------------------------------- |
| `scw_api_key` | String | A token API key to be [retrieved from Scaleway's Console](https://console.scaleway.com/project/credentials). For IAM, you must configure the appropriate [policies](https://console.scaleway.com/iam/policies). |
| `scw_project_id` | String | Your project ID to be [retrieved from Scaleway's Console](https://console.scaleway.com/project/settings) in the `Settings` tab. |

## Default role variables

These variables are used for the internal working of the role. They are usually NOT to be edited unless you have a specific environment requiring so.

| Name                  | Type     | Description                                                                                   |
| --------------------- | -------- | --------------------------------------------------------------------------------------------- |
| `scw_observability_url` | String | Scaleway's Observability endpoint URL. Default: `https://api.scaleway.com/observability/v1alpha1` |
