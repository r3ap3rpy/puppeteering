## Install windows agent

First we need to download the [msi](http://downloads.puppetlabs.com/windows/puppet-agent-x64-latest.msi) package.

Run the installer and when asked specify the *centosa.home* as master.

Now you can issue the following command.

``` bash
puppet agent  --waitforcert 60 --test
```

Then sign the cert on the master.

``` bash
puppetserver ca sign --all
```

If everything goes well the new host should be visible on the foreman.

![2019](/images/2019.PNG)