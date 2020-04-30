## Server 

In order to run the server, we are using a CentOS7 box.

First the official repo needs to be enabled.

``` bash
yum install https://yum.puppet.com/puppet6-release-el-7.noarch.rpm -y
```

Then the server itself installed.

``` bash
yum install puppetserver -y
```

Now we want to make sure the service is automatically starting at boot and start it for now.

``` bash
systemctl start puppetserver
systemctl enable puppetserver
```

By default the server is set to 2GB of RAM, if you want you can go as low as 512MB.
All that is needed is to edit the */etc/sysconfig/puppetserver* config file and modify this line.

``` bash
JAVA_ARGS="-Xms512m -Xmx512m
```

Let's add a nice and popular front end called [Foreman](https://www.theforeman.org)

``` bash
yum install https://yum.theforeman.org/releases/2.0/el7/x86_64/foreman-release.rpm  -y
yum install epel-release -y
```

Now we can install the packages.

``` bash
yum -y install foreman-release-scl
yum -y install foreman-installer
```

Finally execute the installer, which will fail unless the output of `facter fqdn` and `hostname -f` match.

``` bash
foreman-installer
```

You can use the `hostnamectl set-hostname <newname>` to adjust your hostname!

You should see the following output if everything is successfull!

``` bash
Preparing installation Done
  Success!
  * Foreman is running at https://centosa.home
      Initial credentials are admin / 2vJjQfoGSxRd97wW
  * Foreman Proxy is running at https://centosa.home:8443
  The full log is at /var/log/foreman-installer/foreman.log
```

Now if we login to the specified url the followin scenery welcomes us!

![theforeman](/images/theforeman.PNG)