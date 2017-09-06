# AFS (Andrew File System)

Since the start of the 2016 school-year, [AFS](https://www.openafs.org/)  replaces [GlusterFS](https://www.gluster.org) for network shares and student accounts.

## Linux session

## AFS folder

By logging in with login and password, an afs folder is automatically mounted at one's root folder : `/home/login/afs`. It is essential to understand that anything that is not located in this folder will be erased on reboot. Projects should be saved in this folder.

## AFS configuration

At account creation, plenty of configuration files are set in the .confs folder of afs : `/home/login/afs/.confs/`.

For configuration to be taken into account, the script `/home/login/afs/.confs/install.sh` is called on each session boot and deals with symbolic links in folders. For example : `ln -s $AFS_DIR/.confs/bashrc $HOME/.bashrc`. It is possible to add new links in this file.

Those configuration files being symbolic links, it is identical to modify `/home/my_login/afs/.confs/bashrc` and `/home/my_login/.bashrc`. To see all links, one should type ls -la in his terminal, being in his personnal folder.

It is possible to retrieve initial configuration in the folder : `/afs/cri.epita.net/resources/confs/`.

## Access AFS folder of an other user

If you know the login and password of an user, you can access his afs folder from an other session. It might be useful, for instance, if you can't log in your session because of corrupted config files and want to edit them using the anonym epita account.

To get the rights to edit the content of the afs folder of an user called `login_x`, you shall follow this process :

 * Execute `kinit login_x`
 * Enter `login_x`'s password
 * Execute `aklog`

If the user has a login of the form `firstname.lastname` (logins for new users since 2016), the argument for the first step have to be replaced with `kinit firstname_lastname`.

You can then execute `cd /afs/cri.epita.net/user/l/lo/login_x/u/`, read and edit the content of `login_x`'s afs folder.

If you are using the anonym epita account, do not forget to execute `unlog && destroy` to destroy the token before logging out (alternatively, you may shutdown the computer).
