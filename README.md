# dsp-grafana: Dashboards, Datasources, and Notification Channels

## Looking to version-control your dashboards for [DSP's Grafana instance](https://grafana.dsp-devops.broadinstitute.org/)? Look no further.

This repository can contain `.json` files for Grafana dashboards, datasources, and notifiers (notification channels). When you merge a PR, the Grafana instance will automatically pick up any changes.

Most folks will be working with the dashboard files here--the datasources and notifiers will change much less frequently. Just ping [#dsp-devops-champions](https://broadinstitute.slack.com/archives/CADM7MZ35) if you'd like help.

### Do we have to version control dashboards?

Nope! For stable dashboards that are frequently viewed but rarely edited, having them version-controlled might make sense.

### How do we develop the `.json` files themselves?

For development work, the UI is your friend.

- For dashboards:
  - If they're new, create them in the UI and when you're done you can can get the "JSON Model" from the gear icon in the top right.
  - If they already exist, go ahead and edit like normal--when you click the save button you'll get a prompt with JSON you can copy.
- For datasources and notifiers:
  - WIP here! Grafana doesn't expose the JSON as easily here--ping DevOps for help

### My `.json` needs to have a password or token in it!

This shouldn't ever happen for dashboards--but for datasources and notifiers, read on.

A little secret: this repository supports `.json.ctmpl` files. When the CI/CD action finds a `.json.ctmpl` file, it renders it with Vault access (and the rendered file is deployed to Kubernetes as a Secret, not a ConfigMap).

[See here for info on the syntax you'd need to use.](https://github.com/hashicorp/consul-template/blob/master/docs/templating-language.md#secret)

The CI/CD action used for this purpose only has the ability to read `secret/suitable/grafana/config/*`, so put anything you need there.

Why is the ability to template files here an intentionally-poorly-kept secret? Because templating is not recommended for any purpose other than simple Vault access, and it is **extremely discouraged for dashboards (which should not need passwords or tokens)**. DevOps has specific items in our roadmap to make editing dashboards easier, and none of that will work if the dashboard files here contain Consul templating.
