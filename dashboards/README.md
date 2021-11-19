See [../README.md](../README.md) for general info, here are more dashboard-specific instructions:

## Folder structure here is replicated on the Grafana server!

Grafana will make folders for dashboards as necessary to match the directory structure here.

## And, folders on the Grafana server grant permissions!

Users in Grafana are assigned to Grafana teams based on their GitHub teams (H/T [broadinstitute/github-grafana-team-sync](https://github.com/broadinstitute/grafana-github-team-sync)). Those teams are in turn granted access to specific folders.

This isn't a big deal unless you're modifying top-level folders--just check with DevOps before making changes there.
