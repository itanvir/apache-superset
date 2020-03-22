# Getting Started With [Superset](https://github.com/apache/incubator-superset): Airbnb’s data exploration platform

These instructions are for Amazon Linux Version 2

### Update Python and PIP versions on EC2 (Amazon AMI)

```bash
sudo yum update -y
sudo yum install python3 -y
```

#### Adjust PATH
Add below lines to `~/.bashrc`
```bash
export PATH=/usr/local/bin:$PATH
alias python=python3
```
```bash
source ~/.bashrc
```
### Update PIP & other OS dependencies for Superset
```bash
sudo apt-get install --reinstall build-essential
sudo yum install gcc gcc-c++ python3-devel cyrus-sasl-devel
pip3 install cchardet==1.0.0
```
#### Validate Python and PIP
Check Python and PIP 
```bash
$ python -V
Python 3.5.1

$ pip -V
pip 9.0.1 from /usr/local/lib/python3.5/site-packages (python 3.5)

```

### Setup Superset
Install superset
```bash
sudo pip3 install superset
```

Create an admin user (you will be prompted to set username, first and last name before setting a password)
```bash
fabmanager create-admin --app superset
```

Initialize the database
```bash
superset db upgrade
```

Load some data to play with
```bash
superset load_examples
```

Create default roles and permissions
```bash
superset init
```

Start the web server on port 8088, use -p to bind to another port
```bash
superset runserver -p 8080
```
Adjust security group to allow http port

`http://<EC2 Public DNS>:8080/`

References:
* https://github.com/ApacheInfra/superset/blob/master/docs/installation.rst
* https://stackoverflow.com/questions/34103119/upgrade-pip-in-amazon-linux