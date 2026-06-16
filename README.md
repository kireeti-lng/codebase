# codebase


# BigQuery CLI (`bq`) Command Cheat Sheet

This guide covers essential commands for executing SQL queries using the Google Cloud SDK.

*Note: Always use `--use_legacy_sql=false` (or `--nouse_legacy_sql`) to ensure BigQuery processes your query using Standard SQL.*

## 1. Run a Basic Inline Query
Execute a quick query directly from your terminal.

bq query \
--use_legacy_sql=false \
'SELECT event_id, event_name, event_date FROM `your-project.your_dataset.events_raw` LIMIT 10'



## 2. Run a Query from a .sql File

Method A: Input Redirection
bq query --use_legacy_sql=false < my_query.sql


Method B: Piping
cat my_query.sql | bq query --use_legacy_sql=false


## 3. Save Results to a Destination Table


bq query \
--use_legacy_sql=false \
--destination_table='your-project:your_dataset.new_summary_table' \
'SELECT event_date, COUNT(event_id) as event_count FROM `your-project.your_dataset.events_raw` GROUP BY event_date'


## 4. Export Results Locally

Export as CSV:

bq query \
--use_legacy_sql=false \
--format=csv \
--max_rows=1000 \
'SELECT * FROM `your-project.your_dataset.events_raw`' > output.csv


Export as JSON:

bq query \
--use_legacy_sql=false \
--format=prettyjson \
'SELECT * FROM `your-project.your_dataset.events_raw` LIMIT 10' > output.json
