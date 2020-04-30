## Installing Mac OS Agent

First you need to grab the [latest](https://downloads.puppetlabs.com/mac/puppet6/10.15/x86_64/puppet-agent-latest.dmg) installer of the agent.

Once the download is complete you can open in finder and run the installer.

Let's add the executable to our PATH, edit the *~/.bash_profile* file.

``` bash
export PATH=/opt/puppetlabs/bin:$PATH
```

Let's add our master to the config file.

``` bash
puppet config set server centosa.home
```

Let's try to connect our agent to the master.

``` bash
puppet agent  --waitforcert 60 --test
```