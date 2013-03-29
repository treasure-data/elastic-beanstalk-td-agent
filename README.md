td-agent on Amazon Elatic Beanstalk
===================================

This is an example application template of installing td-agent on AWS Elastic Beanstalk (see .rbextentions directory)

# Installing td-agent on your Beanstalk container

    $ cd $YOUR_REPO
    $ mkdir -p .ebextensions
    $ wget -O.ebextensions/0-td-agent-gen-config.config 'https://raw.github.com/treasure-data/elastic-beanstalk-td-agent/master/.ebextensions/0-td-agent-gen-config.config'
    $ wget -O.ebextensions/1-td-agent-install.config 'https://raw.github.com/treasure-data/elastic-beanstalk-td-agent/master/.ebextensions/1-td-agent-install.config'
