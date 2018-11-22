# Making Docker work on 18.04

To install Docker on a **native** Ubuntu 18.04 LTS, the following steps should work (i.e., tested & approved):

## Install Docker

Install Docker:

    sudo apt install docker.io
  
## Appprove your user to the `docker` group

More information: [https://docs.docker.com/install/linux/linux-postinstall/#manage-docker-as-a-non-root-user](https://docs.docker.com/install/linux/linux-postinstall/#manage-docker-as-a-non-root-user)

Create a `docker` group:

    sudo groupadd docker

Add your user to the `docker` group:

    sudo usermod -aG docker $USER

## Install `docker-compose`

Get and install:

    sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

Give rights:

    sudo chmod +x /usr/local/bin/docker-compose

Reinstall the bash completion scripts:

    sudo curl -L https://raw.githubusercontent.com/docker/compose/1.23.1/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose

## Install `docker-machine`

Get and install:

    base=https://github.com/docker/machine/releases/download/v0.16.0 && curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine && sudo install /tmp/docker-machine /usr/local/bin/docker-machine
    
Install virtualbox:

    sudo apt install virtualbox

Make sure the case-sensitivity is alright by making a link:

    sudo ln -s /usr/local/bin/VBoxManage /usr/local/bin/vboxmanage

You're **done**!

More information can be found on:  [https://github.com/docker/machine/issues/4590](https://github.com/docker/machine/issues/4590)
