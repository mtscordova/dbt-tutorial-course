python3 -m venv dbt-venv

source dbt-venv/bin/activate

# Loguear en gcloud

gcloud auth application-default login --scopes='https://www.googleapis.com/auth/bigquery,https://www.googleapis.com/auth/drive.readonly,https://www.googleapis.com/auth/iam.test'

# Verificar en que cuenta estoy logueado
gcloud config list account --format "value(core.account)"


# correr modelo en especifico
# --select == -s
# este comando se debe correr dentro de una carpeta de projecto en especifico
dbt run --select stg_ecommerce__orders  --profiles-dir .

# encontrar profile.yml
dbt debug --config-dir

explorer.exe `wslpath -w ~/.dbt`

## Este comando mira una fuente o source y una tabla  y genera el sql para el select
dbt run-operation generate_base_model --args '{"source_name":"thelook_ecommerce", "table_name": "orders"}'

# Este comando genera un archivo yml para modelo
dbt run-operation generate_model_yaml --args '{"model_names": ["stg_ecommerce__orders"]}'