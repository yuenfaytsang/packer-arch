# Packer Project - Arch Linux Vagrant Box 

**Arch Version**: 2019.02.01

**Pre-built Vagrant Box**:

  - [`vagrant init yuenfaytsang/archlinux`](https://app.vagrantup.com/yuenfaytsang/boxes/archlinux)


This packer project configuration installs and configures Arch Linux x86_64 and generates a Vagrant box file for VirtualBox.

## Requirements

The following software must be installed/present on your local machine before you can use Packer to build the Vagrant box file:

  - [Vagrant](http://vagrantup.com/)
  - [VirtualBox](https://www.virtualbox.org/)
  - [Packer](https://www.packer.io/)
  - [Arch Linux Image 2019.02.01](https://www.archlinux.org/download/) in packer Project Folder

## Usage

Make sure all the required software is installed and available on you local system, then change into the directory containing the packer binary, and run:

    $ packer build -var 'vm_version=1.0.0' arch.json

After a few minutes, Packer should tell you the box was generated successfully, and the box was uploaded to Vagrant Cloud.

> **Note**: This configuration includes a post-processor that pushes the built box to Vagrant Cloud (which requires a `VAGRANT_CLOUD_TOKEN` environment variable defined in your local environment). Therefore you also  need to modify the `box_tag` to match your Vagrant Cloud
account.
Remove the `vagrant-cloud` post-processor from the Packer template to build the box locally and if you not wish to push it to Vagrant Cloud. You can omit the `version` variable, if not using the `vagrant-cloud` post-processor.

    $ packer build arch.json

## Testing built boxes

A Vagrantfile is included that allows quick testing of the built Vagrant boxes by executing

    $ vagrant up

in the same directory where the Vagrantfile is located.