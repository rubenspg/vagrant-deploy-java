# Deploy Java application in a Vagrant box

## Description

In order to rebuild your environment at any time without loosing installed packageas, or configuration this project is an example
of Infrastructure as Code.
The Vagrant tool allows you to code your infrastructure (VM, OS, Hypervisor, proxy, packages, etc) and use integration tools like
Ansible, Docker, Chef and others to provision your application and configure it.

## How to use

### Dependencies

* [Vagrant](https://www.vagrantup.com/)
  * [Berkshelf plugin]()
* [Virtual Box](https://www.virtualbox.org/)

### Creating the Vagrant box

This Vagrant box is configured to deploy a VM into Virtual Box and provision a Java application using Chef.
For more information about the Vagrant configuration open the Vagrantfile.
If you want to understand the Chef cookbook, feel free to open, read and change the cookbook folder.

### Cloning the repo

First clone or create a fork of this repository. Then, follow the next steps.

```
git clone git@github.com:rubenspg/vagrant-java-deploy.git
```

### Executing Vagrant

Go to the root folder of the cloned repo and execute the following commands:

Install Vagrant Berkshelf plugin that adds Berkshelf integration to the Chef provisioners.
Vagrant Berkshelf will automatically download and install cookbooks onto the Vagrant Virtual Machine.
```
vagrant plugin install vagrant-berkshelf
```

Then execute the Vagrant file to create and provision the VM:

```
vagrant up
```

This command will create the VM into your Virtual Box. Then, it will execute the provisioning with Chef, and the Java application will be installed with its dependencies (Java, Tomcat, etc).

### Execute a test to check if the service is running

Once your VM is ready, you can check if your application was correclty deployed. You can check verifying if the following command return the expected result:

```
curl http://localhost:8080
```

### Troubleshooting

If the application does not startu correctly or the installation failed for some reason, you can enter in the VM via SSH:

```
vagrant ssh
```

In the VM, you can check the following logs:

* Tomcat
```
cat /var/logs/tomcat/catalina.out
```

* Chef
```
cat /var/logs/chef/chef.log
```

## Contributing

You are welcome to contribute. Just follow these steps:

### Clone or fork the repository

```
git clone git@github.com:rubenspg/dev-env.git
```

### Do some work

```
git checkout master
git pull origin master
git checkout -b contrib/branch_name
```

### Create a PR
```
git push -u origin contrib/branch_name
```
