# EcToo

In order to use the aws commands to controll the AWS instances you will need to have a profile set up as described, and the EC2 instance will need to be tagged appropriately:

#### EC2 Tagging
create a tag on the ec2 instance that conforms to the following

`Projectname Production`
or
`Projectname Staging`
with the first letters being **Capitalized**

#### Local Configuration
`~/.aws/credentials`

```
[projectname]
aws_access_key_id = AWSKEY
aws_secret_access_key = AWSSECRETKEY
```

`~/.aws/config`
Make sure you keep the `profile` prefix as the config file follows a different naming convention
```
[profile projectname]
output = json
region = us-east-1
```

#### EcToo Options
```
Example Usage:

  ectoo -i=Production -r=describe -p=default -j=Tracktum

Available options

  -j | --project        The 1st part of your ec2 tag
  -i | --instance       The 2nd part of your ec2 tag ie. Production/Staging
  -r | --run            Specifiy which command to run
  -c | --commands       List available commands to run
  -p | --profile        Specify the configured profile to use from ~/.aws/config
  -h | --help           Show this help resource
```

#### Available Commands
```
  start             Start an instance with the given tags
  stop              Stop an instance with the given tags
  state             Display the state of an instance with the given tags [running/stopped]
  address           List the IP address of an instance with the given tags
  describe          Dump the entire description of an instance with the given tags
```

# Installation

## OS X Install With Homebrew

```
brew tap peledies/tap
brew install ectoo
```


## Linux Install

```
sudo git clone https://github.com/peledies/ectoo.git /opt/ectoo
```

##### Create Symbolic Link to `ectoo`
```
ln -s /opt/ectoo/ectoo /usr/local/bin/ectoo
```

##### Add execute permissions to `ectoo`
```
sudo chmod +x /opt/ectoo/ectoo
```

##### Updating

```
cd /opt/ectoo && sudo git fetch --all && sudo git reset --hard origin/master
 && cd -
```