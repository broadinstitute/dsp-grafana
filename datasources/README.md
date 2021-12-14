This folder is a work-in-progress. Some random notes:

- `readOnly` stops edits in the UI, I think
- Providing a `uid` should stop duplicates and other nastiness

### How to get the JSON

1. Make a data source in the UI

2. Run this and find your data source in the list:

```bash
curl -v -X GET -H "Content-Type: application/json" https://$(vault read -field=username secret/suitable/grafana/basic_auth/admin):$(vault read -field=password secret/suitable/grafana/basic_auth/admin)@grafana.dsp-devops.broadinstitute.org/api/datasources | jq
```

3. Delete your data source in the UI

4. Commit the JSON here **(delete the id field, you don't want that committed here)**.
