# Advanced Packaging Tool - APT
`apt` is a command-line utility for installing, updating, removing, and otherwise managing deb packages on Ubuntu, Debian, and related Linux distributions.

Most of the apt commands must be run as a user with `sudo` privileges.

## Main commands apt 

## Updating package index - apt update
The APT package index is basically a database that holds records of available packages from the repositories enabled in the system

To update the package index run the command below. This will pull the latest changes from the APT repositories

`sudo apt update`

## Upgrading packages - apt upgrade
It upgrades the installed packages to their latest versions.

`sudo apt upgrade`

The command **doesn’t upgrade** packages that **require removal of installed packages**.

In order to upgrade a single package, pass the package name:

`sudo apt upgrade package_name`

## Full Upgrading - apt full-upgrade
The difference between upgrade and full-upgrade is that the later will remove the installed packages if that is needed to upgrade the whole system.

`sudo apt full-upgrade`


## Installing packages - apt install
`sudo apt install package_name`

Installing multiple packages with one command, specify them as a space-separated list:

`sudo apt install package1 package2`

To install local **deb** files **provide the full path to file**. Otherwise, the command will try to retrieve and install the package from the APT repositories.

`sudo apt install /full/path/file.deb`


## Removing Packages - apt remove
`sudo apt remove package_name`
 

multiple packages can be specified to be deleted, separated by spaces:

`sudo apt remove package1 package2`

The remove command will uninstall the given packages, **but it may leave some configuration files behind**. To remove the package including all configuration files, use `purge` instead of `remove`

`sudo apt purge package_name`


## Remove Unused Packages - apt autoremove [Usefull]
Whenever a new package that depends on other packages is installed on the system, the package dependencies will be installed too. When the package is removed, the dependencies will stay on the system. This leftover packages are no longer used by anything else and can be removed.

To remove the unneeded dependencies use the following command:

`sudo apt autoremove`

## Listing Packages - apt list
`sudo apt list`

`sudo apt list --installed`

### --upgradeable
Getting a list of the upgradeable packages may be useful before actually upgrading the packages:

`sudo apt list --upgradeable`

## Searching Packages - apt search
`sudo apt search package_name`

This command allows searchs for a given package in the list of the available packages:


If found, the command will return the packages which name matches the search term.

Package Information - apt show
The information about the package dependencies, installation size, the package source, etc.

To retrieve information about a given package, use the show command:
`sudo apt show package_name`


## References
[linuxize - how-to-use-apt-command](https://linuxize.com/post/how-to-use-apt-command/#top)