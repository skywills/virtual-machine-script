## Install Multipass

you may refer multipass [offical site](https://multipass.run/) for installation guide or follow the guideline below.

**linux**

1. setup snap if does not exists - [guide](https://docs.snapcraft.io/installing-snapd?_ga=2.172827114.872544811.1612779899-1716101267.1611558306)

2. install multipass via command
```sh
sudo snap install multipass
```

**macos**

1. download multipass .pkg - [link](https://multipass.run/download/macos)

2. run the downloaded .pkg in an account with Administrator privileges. 

3. If you'd like to use Multipass with VirtualBox use this terminal command:
```sh
sudo multipass set local.driver=virtualbox
```

**window**

1. Note: You need Windows 10 Pro/Enterprise/Education v 1803 or later, or any Windows 10 with VirtualBox

2. download mutipass installer - [link](https://multipass.run/download/windows)

3. Make sure your network is private or Windows prevents Multipass from starting.

4. Run the installer. You need to allow the installer to gain Administrator privileges.


## Launch new ubuntu vm

1. Launch an instance (by default you get the current Ubuntu LTS) with 4GB disk
```sh
multipass launch --name ubuntu-lts
```

2. Launch instance with 10GB disk size
```sh
multipass launch --name ubuntu-lts --disk 10GB
```

3. Launch instance with Number of CPU, Minimum: 1, default: 1.
```sh
multipass launch --name ubuntu-lts --cpu 2
```

4. Launch instance with allocate RAM, Minimum: 128M, default: 1G.
```sh
multipass launch --name ubuntu-lts --mem 2G
```

5. Launch instance with different ubuntu version, find the desire version and put the name
```sh
multipass find
```
```sh
multipass launch --name ubuntu1804 18.04
```

6. for more launch option please refer to the [guide](https://multipass.run/docs/launch-commandhttps://multipass.run/docs/launch-command)

## Run commands in that instance, try running bash (logout or ctrl-d to quit)
```sh
multipass exec ubuntu-lts -- lsb_release -a
```

## List instances
```sh
multipass list
```

## Start/Stop instance
```sh
multipass stop ubuntu-lts
```
```sh
multipass start ubuntu-lts
```

## Clean up what you don’t needClean up what you don’t need
```sh
multipass delete ubuntu-lts
```
```sh
multipass purge
```

## Launch Ubuntu VM's shell
```sh
multipass shell ubuntu-lts
```

## Change Ubuntu VM instance password

1. By default instance created a user `ubuntu`

2. Launch Ubuntu VM's shell `multipass shell ubuntu-lts`

3. change your desire password
```sh
passwd
```

4. Or add your ssh key into the instance `vi ~/.ssh/authorized_keys`

## Connect your Ubuntu VM instance via SSH

1. find your instance IP with `multipass list`

2. connect your instance with ssh
```sh
ssh ubuntu@<instance IP>
```

3. you may using scp to upload your files to the folders too