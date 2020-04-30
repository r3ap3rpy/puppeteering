## PuppetDB

Puppet DB allows us to have extensive reporting capabilities.

Open up the console on your puppet master and issue the following command.

``` bash
puppet resource package puppetdb ensure=latest
```

The configuration file is located at */etc/sysconfig/puppetdb*