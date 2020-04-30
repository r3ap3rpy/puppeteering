## Install linux agent

Installing linux agents is not that big of a challenge.
First enable the repository.

``` bash
yum install https://yum.puppet.com/puppet6-release-el-7.noarch.rpm -y
```

Then install the agent.

``` bash
yum install puppet-agent -y 
```

Let's add the executable to our PATH, edit the *~/.bash_profile* file.

``` bash
export PATH=/opt/puppetlabs/bin:$PATH
```

Let's add our master to the config file

``` bash
puppet config set server centosa.home
```

Let's try to connect our agent to the master.

``` bash
puppet agent  --waitforcert 60 --test
```

On the master issue the following command.

``` bash
puppetserver ca sign --all
```

If everything goes well we should see our new host in the inventory.

![centosb](/images/centosb.PNG)

Now the agent is installed and connected to our master.