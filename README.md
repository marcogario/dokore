Kore Compatible Docker Container
================================

This image can be used to build binaries that are compatible with
the environment on the Kore cluster.

For example, to build ESTools you would take the following steps:

```
$ docker run --rm -ti -v ~/:/data gario/dokore
bash-4.2# cd /data/ESTools/scripts
bash-4.2# ./cmake_setup_build.py --release ../build-kore
bash-4.2# cd ../build-kore
bash-4.2# make -j
```

Inside the build-kore directory, you'll have a binary that is
compatible with Kore. Note that the directory is physically on the
host machine. In this way, you can work normally on your machine
(e.g., update git sources, test the executable), and only perform the
compilation through the docker image. I.e., after updating sources you
can rebuild the binary by doing:

```
$ docker run --rm -ti -v ~/:/data dokore
bash-4.2# cd /data/ESTools/build-kore
bash-4.2# make -j
```
