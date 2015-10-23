td-agent on AWS Elastic Beanstalk
=================================

This is an example application template of installing td-agent on AWS Elastic Beanstalk (see .ebextentions directory)

### Install td-agent on your Beanstalk container

Please download two files under `.ebextensions` directory, and put into your app's `.ebextensions` dir.

    $ cd $YOUR_REPO
    $ mkdir -p .ebextensions
    $ wget -O.ebextensions/0-td-agent-gen-config.config 'https://raw.github.com/treasure-data/elastic-beanstalk-td-agent/master/.ebextensions/0-td-agent-gen-config.config'
    $ wget -O.ebextensions/1-td-agent-install.config 'https://raw.github.com/treasure-data/elastic-beanstalk-td-agent/master/.ebextensions/1-td-agent-install.config'

Please modify your configuration if you want.

    $ emacs .ebextensions/0-td-agent-gen-config.config
    
Finally, please deploy the change into the production.

    $ eb init
    $ git add .ebextensions/0-td-agent-gen-config.config
    $ git add .ebextensions/1-td-agent-install.config
    $ git commit -a -m 'custom extensions to install td-agent'
    $ eb create
    
### How it Works

- `0-td-agent-gen-config.config`: This script puts the config file under `/etc/td-agent/td-agent.conf`
- `1-td-agent-install.config`: This script installs the td-agent package via yum, and launch the daemon

# References

- [Getting Started Using AWS Elastic Beanstalk](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/GettingStarted.html)
- [Customizing and Configuring AWS Elastic Beanstalk Environments](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/customize-containers.html)
