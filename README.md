Kore Compatible Docker Container
================================

This image can be used to build binaries that are compatible with
the environment on the Kore cluster.

For example, to build ESTools you would take the following steps 
(assuming that you have ```~/ESTools``` on your machine):

```
$ docker run --rm -ti -v ~/:/data gario/dokore
bash-4.2# cd /data/ESTools/scripts
bash-4.2# ./cmake_setup_build.py --release ../build-kore
bash-4.2# cd ../build-kore
bash-4.2# make -j
```

Inside the build-kore directory, you'll have a binary that is
compatible with Kore.

Note that the option -v maps a directory (volume) from the host
machine (in this case the home directory) to a directory of the guest
container (in this case /data). In this way, you can work normally on
your machine (e.g., checkout and update git sources, test the
executable), and only perform the compilation through the docker image
After updating sources you can rebuild the binary by doing:

```
$ docker run --rm -ti -v ~/:/data dokore
bash-4.2# cd /data/ESTools/build-kore
bash-4.2# make -j
```
