# The Airflow


- [Using Apache Airflow to build reusable ETL on AWS Redshift](https://sonra.io/2018/01/01/using-apache-airflow-to-build-a-data-pipeline-on-aws/)
  - Inputing Connections via the GUI helps "hide" them, perhaps a better way to avoid GUI and still protect your credentials?
  - Great hands-on view of building out your own Operator (e.g. Load data from S3 to RedShift)
- [Airflow with Maxime Beauchemin - Episode 44](https://www.podcastinit.com/episode-44-airflow-with-maxime-beauchemin/)


#### Plugins
- [Airflow Plugins Github Page](https://github.com/airflow-plugins)
- [Airflow Plugins Docs](https://airflow.apache.org/plugins.html)


#### DAGs
[Example-Airflow-DAGs](https://github.com/airflow-plugins/Example-Airflow-DAGs)



#### Airflow vs other Workflow Management solutions
- e.g. Oozie, Luigi, Azkaban, Cron

- [What we learned migrating off Cron to Airflow](https://medium.com/videoamp/what-we-learned-migrating-off-cron-to-airflow-b391841a0da4)


- LocalExector
After some time you'll likely max out the workers on that local instance and so then you would need something like the `CeleryExecutor` or `MesosExecutor`
