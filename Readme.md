# Getting started with Vagrant 
Vagrant is a tool for building and managing virtual development environments. It is primary used for creating and configuring lightweight, reproducible, and portable virtual machine environments. In this guide we are going to cover the basics of vagrant.

## Prerequisites
- Install latest version of [vagrant](https://developer.hashicorp.com/vagrant/install)
- Install a virtualization product or Hypervisor such as (VirtualBox, VMware or Hyper-V).

## How to install vagrant 
To have vagrant up and running in your computer you can use the link below:
```bash
https://developer.hashicorp.com/vagrant/install
```

## Initializing a project directory.
The first step to configure any vagrant project is to first of all create a ```Vagrantfile```. This file allows you to do the following:
- Mark the root directory of your project since many configuration options in vagrant are relative to the root directory.
- Describe the type of machine and resources you need to run your project, as well as what software to install and how you want to access it.

## Create a directory
```bash
mkdir vagrant-getting-started
cd vagrant-getting-started
```

## Initialize the project
Vagrant has a built-in command to initialize a project, ```vagrant init```, which can take a box name and URL as arguments. Use the command below to initialize your project.
```bash
vagrant init hashicorp/bionic64
```

## What is a vagrant box
A vagrant box is just a base image that you can use to create your image. This increase the speed at which we create our virtual machines rather than creating it from scratch which will take more time.

Note: Once you initialize your project using the command above a ```Vagrantfile``` will be created containing the box (base image) that will be used to create our virtual machine. 

Sometimes you will want to install a box without actually creating a Vagrantfile this can be achieved with the subcommand ```box add```. see full command below:
```bash
vagrant box add hashicorp/bionic64 # downloads the image and adds it to vagrant
```

## Use vagrant box
The next step is to configure our project to use the image added above as base image. Once you've added the box to vagrant either by initializing or adding it explicitly, you need to configure your project to use the box as base image. Open the Vagrantfile and add the following.
```bash
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
end
```

Note: If you added the box while initializing the project then no need to add this because it is done automatically for you.

You can equally add the version of the box you want to use and also the url of the box as seen below:
```bash
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
  config.vm.box_version = "1.0.282"
  config.vm.box_url = "https://vagrantcloud.com/hashicorp/bionic64"
end
```

[Find more boxes here](https://app.vagrantup.com/boxes/search)

# Start your environment.
Now that our project has been initialized and configured to use the ```bionic64 box```, it is time to boot our first vagrant environment.

## Bring up your virtual environment.
Run the following command:
```bash
vagrant up # this command launches our vm and make it running.
```

## SSH into the machine.
```bash
vagrant ssh
```

## Destroy machine
```bash
vagrant destroy
```

## Remove the box
The ```vagrant destroy``` command does not remove downloaded boxes. So see the boxes that exist use the command below:
```bash
vagrant box list
```

Remove the box:
```bash
vagrant box remove box_name
```
