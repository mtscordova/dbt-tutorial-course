python3 -m venv dbt-venv

source dbt-venv/bin/activate


gcloud auth application-default login --scopes='https://www.googleapis.com/auth/bigquery,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/iam.test'