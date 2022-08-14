# `activate_cockpit_project` role

This role sets-up a Docker Compose configuration as a demo to inject logs and/or metrics to Scaleway's Cockpit, part of [Observability feature](https://www.scaleway.com/en/betas/#observability).

For more details, refer to [Scaleway's Observability documentation](https://developers.scaleway.com/en/products/observability/api/v1alpha1).

## Requirements

- Docker & docker-compose on the target host

This role requires the `facts.json` file generated by the [activate_cockpit_project](../activate_cockpit_project) role before getting run.

The `facts.json` file must look like this :

```json
{
  "cockpit_grafana_url": "https://grafana---.fnc.fr-par.scw.cloud",
  "cockpit_grafana_username": "user",
  "cockpit_grafana_password": "...",
  "cockpit_logs_url": "https://logs.prd.obs.fr-par.scw.cloud",
  "cockpit_metrics_url": "https://metrics.prd.obs.fr-par.scw.cloud",
  "cockpit_alertmanager_url": "https://alertmanager.prd.obs.fr-par.scw.cloud",
  "cockpit_token_name": "...",
  "cockpit_token_secret_key": "...",
  "cockpit_token_id": "..."
}
```

## User role variables

| Name                  | Type     | Description                                                                                   |
| --------------------- | -------- | --------------------------------------------------------------------------------------------- |
| `push_use_case` | String | If set to `logs`, will push logs from a container to Cockpit. If set to `metrics`, will push the same logs along with host's CPU/memory/storage metrics. |

## Default role variables

These variables are used for the internal working of the role. They are usually NOT to be edited unless you have a specific environment requiring so.

| Name                  | Type     | Description                                                                                   |
| --------------------- | -------- | --------------------------------------------------------------------------------------------- |
| `remote_playground_path` | String | Path to which the compose configuration is copied and run. Default to `/tmp/scw-cockpit-demo`. |
| `facts_file_path` | String | Path to the file containing user's Observability credentials from the [activate_cockpit_project](../activate_cockpit_project) role. Default to `./facts.json`.  |