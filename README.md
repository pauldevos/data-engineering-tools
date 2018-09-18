# data-engineering-tools
A list of tools and whatnot under the umbrella of Data Engineering


A quick preview of some favorite tools and/or frameworks are:

- Python
  - Airflow
  - Spark
  - Dask
  - Pandas
  - Boto3 (AWS SDK)
  - Flask
  - Django
  - Scikit-Learn
  - TensorFlow
  
- Jupyter Notebooks
  - JupyterHub


- DockerHub


- Databases
  - Postgres
  - RedShift
  - Presto
  - MapD (the database)
  - ElasticSearch (index/search engine)
  
  
- Business Intelligence Tools
  - MapD (Immerse)
  - SuperSet
  - ELK Stack (Kibana)
  - Bokeh
  - Plotly
  - Dash



### Setting Environment Variables on your `*nix` machine
- Add these to your .bash_profile, your .aws config
- e.g. DB Credentials, AWS Credentials

e.g. update your `.bash_profile`
``` #.bash_profile
export DB_USER = "my_username"
export DB_PASSWORD = "my_password"
```

Then you can access them in your Python scripts like so.
``` python
import os

db_user = os.environ.get("DB_USER")
db_pass = os.environ.get("DB_PASS")

```

Other environment config variables files should be stored accordingly in one of the following
- .bashrc
- AWS - .aws/credentials
- SSJ - .ssh - here you will have your id_rsa files
