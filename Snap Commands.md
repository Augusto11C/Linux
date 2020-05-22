
## Uninstall Snap Packages
To list all installed snap package run the following command:

`snap list`
Once the exact package name is known, then it can be uninstalled by typing:

`sudo snap remove package_name`

`snap remove --purge package_name`

### Uninstall Unused Packages
Whenever you install a new package that depends on other packages, the package dependencies will be installed too. When the package is uninstalled, the dependency packages will stay on the system. This leftover packages are no longer used by anything else and can be removed.

`sudo apt autoremove`

## References 
[how-to-uninstall-software-packages-on-ubuntu](https://linuxize.com/post/how-to-uninstall-software-packages-on-ubuntu/)
