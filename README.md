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


# Data Engineer - First Things First
If you're going to be a Python developer of any kind, e.g. Data Scientist, Web Developer, and/or Data Engineer there's a few things you should set up from the beginning. Many of these will help abstract away sensitive information (e.g. passwords) from your code repos so you don't accidently commit any sensitive info to Github. They also help make your workflows much faster.

Some potential things you should consider doing first:
1. Install Miniconda (latest version)
2. Set up environment variables
  - Customize your Bash terminal
  - Aliases for bash, awk, grep, sed, git commands

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
