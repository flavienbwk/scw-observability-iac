# Scaleway Observability with IaC

Experimenting Scaleway's observability feature with automation scripts.

## Presentation

:warning: Observability is currently an **alpha** feature. API might be unstable or change quickly.

> Scaleway Observability is a platform to monitor applications and their infrastructure. It ingests metrics, using a Prometheus-like API, and logs, using a Grafana Loki API. It also provides a Grafana Dashboard to visualize the metrics and logs.

## Pre-requisite

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#pip-install) version >= `2.11.12`
- Python version >= `3.7.x`

## Getting started

In this example inspired from [the official documentation](https://developers.scaleway.com/en/products/observability/api/v1alpha1), we're going to start a Cockpit instance (observability server), push some logs from a Docker container and visualize them in Grafana.

1. Retrieve [your Scaleway credentials](https://console.scaleway.com/project/credentials) and edit the variables file

    ```bash
    cp ./vars/main.example.yml ./vars/main.yml
    ```

2. Activate Cockpit for your project and create a push token

    ```bash
    ansible-playbook -i inventories/local.ini ./observability.yml --extra-vars @./vars/main.yml
    ```

    You should there see the URL, **username** and **password** for your Grafana instance.

    Additionally, you will see your **push token** name and secret. You will need it to push logs to Cockpit.

## Suggestions & feedbacks for Scaleway team

- Make it possible to filter tokens by name in addition to IDs in GET:/tokens so it is easier to browse and remove
