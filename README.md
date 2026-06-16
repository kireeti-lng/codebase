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
