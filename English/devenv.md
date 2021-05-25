# Development environments

Vscan has three development environments created in docker in three different versions.

The 3 currently supported versions are :

* Ubuntu 20.04
* Centos 7
* Centos 8

Debian will arrive soon as OpenSuse.

To create the development environment you only need to clone the gitlab repository of vscan and run the following script:

```bash
./start-dev-env
```
The options will be indicated to you:

```
centos:8             Create and start Centos 8 vscan dev environnement.
centos:8:release	Create and start release Centos 8 release.
centos:7             Create and start Centos 7 vscan dev environnement.
centos:7:release     Create and start release Centos 7 release.
ubuntu:18.04         Create and start Ubuntu 18.04 vscan dev environnement (DEPRECATED)
ubuntu:20.04         Create and start Ubuntu 20.04 vscan dev environnement
```

You will arrive in a container with vscan installed, a web interface for mysql ([sidu](https://sourceforge.net/projects/sidu/)) accessible via your web browser at this address : http://127.0.0.1:8080 .
