Instructions [here](https://grafana.com/docs/grafana/latest/administration/provisioning/#datasources). 

This can get you the json of a data source that you made in the UI: 
```bash
curl -v -X GET -H "Content-Type: application/json" https://$(vault read -field=username secret/suitable/grafana/basic_auth/admin):$(vault read -field=password secret/suitable/grafana/basic_auth/admin)@grafana.dsp-devops.broadinstitute.org/api/datasources | jq
```
