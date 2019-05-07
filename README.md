# data-engineering-tools
A list of tools and whatnot under the umbrella of Data Engineering

#### Systems Engineering Overview
- [System Design Primer](https://github.com/donnemartin/system-design-primer)


## Things a Data Engineer should know

### Cloud Computing (e.g. AWS, Google Cloud, Azure)
- AWS resources:
  - S3
  - EC2
  - RDS
  - RedShift
  - EMR
  - Kinesis
  - Athena
  - Lambda
  - VPC
  - Glue
  - Sagemaker
- AWS tools:
  - Boto3 (Python)
  - AWS CLI
----
### Job Scheduling
- Cron, Airflow, Ooozie, Luigi, and/or AWS Step Functions
----
### Frameworks
- Scheduling/Workflows: Airflow, Oozie, Luigi, Cron, and/or AWS Step Functions
- Spark
- Data Transformation: Pandas, Dask
- ML Pipelines: Numpy, Scikit-Learn
----
### Languages
- Python
- Bash
- SQL
- Optional: Scala (for Spark), Java (for Spark, Kafka, or Storm)
----
#### Data Modeling
- Fact-Dimensional Warehouses
- Slowly Changing Dimensions
- Star Schema, Snowflake Schema
- Index Tuning
- Query Tuning
- Transactional Processing: Lock and Block
- OLTP vs OLAP
----
#### Data Warehousing Architectures
- Lambda Architecture
- Kappa Architecture
- Batch
- Mini-Batch
- Streaming
----
#### Business Intelligence Tools
- Click and Drag (e.g. Looker)
- SQL Based (e.g. Tableau, Looker, Mode, Periscope)
- SQL/Python/R based (e.g. Jupyter, Mode)
----
#### Data Warehouse Serving Layers
- RedShift
- BigQuery
- Snowflake
- RDBMS (e.g. AWS RDS, Google SQL)
----




A quick preview of some favorite tools and/or frameworks are:

- Python
  - Airflow
  - Spark
  - Dask
  - Pandas
  - Boto3 (AWS SDK)
  - Flask
  - Pyramid
  - Scikit-Learn
  - TensorFlow
  - [Apache Arrow](https://arrow.apache.org/) - [PyArrow](https://arrow.apache.org/docs/python/)
  
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
  - MapD [Database](https://github.com/omnisci/mapd-core), [Charting](https://github.com/omnisci/mapd-charting), [Rendering Engine](https://www.omnisci.com/platform/immerse/) by [OmniSci](https://www.omnisci.com/)
  - SuperSet
  - ELK Stack (Kibana)
  - Bokeh
  - Plotly
  - Dash

- Data Visualization Projects
  - [UW Falcon](https://github.com/uwdata/falcon)
  - [Interactive Python Data Visualization with Bokeh](https://realpython.com/python-data-visualization-bokeh/)
  - [Python Module Imports Visualization](https://chezsoi.org/lucas/blog/python-modules-imports-visualization.html) - [code](https://github.com/Lucas-C/dotfiles_and_notes/blob/master/languages/python/gen_modules_graph.py)
  


# Data Engineer - First Things First
If you're going to be a Python developer of any kind, e.g. Data Scientist, Web Developer, and/or Data Engineer there's a few things you should set up from the beginning. Many of these will help abstract away sensitive information (e.g. passwords) from your code repos so you don't accidently commit any sensitive info to Github. They also help make your workflows much faster.

Some potential things you should consider doing first:
1. Install Miniconda (latest version)
2. Set considerations for you in setting up environment variables
    - Customize your Bash terminal
    - Aliases for bash, awk, grep, sed, git commands
    - [Dotfiles](https://dotfiles.github.io/)
    - [Turbo charge your Mac development environment](https://www.mugo.ca/Blog/Turbo-charge-your-Mac-development-environment)


### 1. Installing Python
I recommend installing the latest stable version of [Miniconda](https://conda.io/miniconda.html), as of this post that was Python 3.x. You can still set up conda environments for Python 2.x and we'll get to that later. If you have any problems with installing, read the documentation, do a web search query (e.g. Google, DuckDuckGo, Brave, FireFox), or search for help on YouTube. You got this.


### 2. Setting Up conda & pip
In Python you're going to need an `environment manager` and a `package manager`. Conda is both. You can read more about Conda here: [Conda: Myths and Misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/), [Conda - Package Manager](https://conda.io/docs/user-guide/tasks/manage-pkgs.html), [Conda - Environment Manager](https://conda.io/docs/user-guide/tasks/manage-environments.html). My _personal recommendation_ is to use Conda to manage your environments, but **NOT** to manage your package installation. The main reason is because conda-forge (where Conda installs from) doesn't have all the packages Pypi does (where `pip` installs from). So for package management, I recommend using [pip](https://pypi.org/project/pip/). 


### 3. Setting Environment Variables on your `*nix` machine
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

Some other environment config variables examples should be stored accordingly in one of the following
- `.bashrc`
- AWS - `.aws/credentials`
- SSJ - `.ssh` - here you will have your `id_rsa` secret and public ssh key files

So what's the difference between your `.bash_profile` and your `.bashrc` file? Well StackExchange has a great answer for that [here](https://apple.stackexchange.com/questions/51036/what-is-the-difference-between-bash-profile-and-bashrc), but simply put once you open up a terminal your `.bash_profile` is loaded immediately and you have access to all of those environment variables immediately. On a Mac and (I think) most Linux distros (I haven't tried them all) you start with some CLI tool, e.g. bash. So that is your "login" shell. When you type another interactive shell at that command line, e.g. `bash`, `python`, `python3`, or `ksh` you will now load the `.bashrc` file. This might be something you want say when you use Python at the CLI. 

If you want to keep some environment variables separate, you can always put a statement into your `.bash_profile` to load variables from another area on `login`. 

For example, put this in your `.bash_profile` and it will load all the environment variables from your `.bashrc` file. You can do this with any other file, e.g. `.aws/credentials`
```bash
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
```

### 4. Set up and Configure Git
You may use whatever version/source control you like. There's two main flavors, subversion and git. As of this writing, Git has 3 main hosting services: [Github](https://github.com/), [Bitbucket](https://bitbucket.org/), and [Gitlab](https://about.gitlab.com/).

Then you're going to need to generate an SSH key so you can SSH from your host (e.g. your laptop or an EC2) to your git responsitory (e.g. Github).

There's some instructiosn on how to this here: [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)

#### If you have Multiple SSH Keys (often you will)
You have to do some magic to make it work. There's a few suggestions here: [SSHing into Multiple Github Accounts](https://gist.github.com/jexchan/2351996)

For example your `~/.ssh folder may have multiple keys:
```
~/.ssh/id_rsa
~/.ssh/id_rsa_home
~/.ssh/id_rsa_work
~/.ssh/id_rsa_aws
```

You will have to add all these keys to your SSH agent,
e.g.
```
ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/id_rsa_home
ssh-add ~/.ssh/id_rsa_work
ssh-add ~/.ssh/id_rsa_aws
```

Now to use each for a specific task you'll have to use the `-i` (identity) tag for the correct pairing.
e.g. `ssh -i ~/.ssh/id_rsa_aws ubuntu@aws-sdf-adfs-s112312.com`


If you need to add SSH keys to an EC2, you can find instructions for that here:
- [How do I add new user accounts with SSH access to my Amazon EC2 Linux instance?](https://aws.amazon.com/premiumsupport/knowledge-center/new-user-accounts-linux-instance/)



------- Not yet organized

`brew upgrade brew` ## upgrades to all current packages
`brew upgrade` ## installs upgrades for any previously installed packages



### Best Practices
- [Gitlab Best Practices](https://docs.gitlab.com/ee/development/README.html#databases)
- [Advanced Git Tips for Python Developers](https://realpython.com/advanced-git-for-pythonistas/)


### AWS
- [Python, Boto3, and AWS S3: Demystified](https://realpython.com/python-boto3-aws-s3/)


### Dot Files
- [Getting Started with DotFiles](https://medium.com/@webprolific/getting-started-with-dotfiles-43c3602fd789)
- [Donne Martin's DotFile](https://github.com/donnemartin/dev-setup)
- [Awesome DotFiles](https://github.com/webpro/awesome-dotfiles)
- [Mathias Bynens DotFiles](https://github.com/mathiasbynens/dotfiles)
- https://dotfiles.github.io/
- https://blog.flowblok.id.au/2013-02/shell-startup-scripts.html
- 


### Git
- [Interactive Git Cheatsheet](http://www.ndpsoftware.com/git-cheatsheet.html)

### Git Q&A
- https://stackoverflow.com/questions/67699/how-to-clone-all-remote-branches-in-git?rq=1
- https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-both-locally-and-remotely?rq=1
- https://stackoverflow.com/questions/61212/how-to-remove-local-untracked-files-from-the-current-git-working-tree?rq=1
- https://stackoverflow.com/questions/1628088/reset-local-repository-branch-to-be-just-like-remote-repository-head?noredirect=1&lq=1
- https://stackoverflow.com/questions/32056324/there-is-no-tracking-information-for-the-current-branch


