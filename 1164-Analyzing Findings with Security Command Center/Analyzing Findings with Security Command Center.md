# Analyzing Findings with Security Command Center || [GSP1164](https://www.cloudskillsboost.google/focuses/71931?parent=catalog) ||

### Run the following Commands in CloudShell

```
curl -LO raw.githubusercontent.com/Epulvis/GCP/main/Analyzing%20Findings%20with%20Security%20Command%20Center/gsp1164-1.sh

sudo chmod +x gsp1164-1.sh

./gsp1164-1.sh
```

* Go to `Export to Pub/Sub` from [here](https://console.cloud.google.com/security/command-center/config/continuous-exports/pubsub)

* For the continuous export name, enter in `export-findings-pubsub`.

### Run again the following Commands in CloudShell

```
export ZONE=
export REGION=
```

```
curl -LO raw.githubusercontent.com/Epulvis/GCP/main/Analyzing%20Findings%20with%20Security%20Command%20Center/gsp1164-2.sh

sudo chmod +x gsp1164-2.sh

./gsp1164-2.sh
```
```
bq query --apilog=/dev/null --use_legacy_sql=false  \
"SELECT finding_id,event_time,finding.category FROM continuous_export_dataset.findings"
```

* Got to `Create a bucket` from [here](https://console.cloud.google.com/storage/create-bucket)

* for BUCKET NAME type `scc-export-bucket-`YOUR_PROJECT_ID

* Now go to `Export findings to Cloud Storage` from [here](https://console.cloud.google.com/security/command-center/export)

* Set the filename to `findings.jsonl`

* Go to `BigQuery Studio` from [here](https://console.cloud.google.com/bigquery)

* Set the TABLE NAME to `old_findings`

* Now paste in the following schema

```
[   
  {
    "mode": "NULLABLE",
    "name": "resource",
    "type": "JSON"
  },   
  {
    "mode": "NULLABLE",
    "name": "finding",
    "type": "JSON"
  }
]
```

##### *You Have Successfully Demonstrated Your Skills And Determination.*

#### *Well done!*
