# mod_ssml

SSML audio rendering format

## Table of Contents

* [Table of Contents](#table-of-contents)
* [Build and install mod_ssml](#build-and-install-mod_ssml)
* [Build standalone mod_ssml module using FreeSWITCH devel package](#build-standalone-mod_ssml-module-using-freeswitch-devel-package)

## Build and install mod_ssml

Change to a directory where the FreeSWITCH sources will be compiled

```
cd /usr/src
```

Clone the FreeSWITCH repository into the above directory

```
git clone https://github.com/signalwire/freeswitch.git
```

Perform an initial bootstrap of FreeSWITCH so that a `modules.conf` file is created

```
./bootstrap.sh
```

Add the mod_ssml to `modules.conf` so that an out-of-source build will be performed

```
mod_ssml|https://github.com/freeswitch/mod_ssml.git -b main
```

Configure, build and install FreeSWITCH

```
./configure
make
make install
```

The following commands will build and install *only* mod_ssml

```
make mod_ssml
make mod_ssml-install
```

To run mod_ssml within FreeSWITCH, perform the following two steps
1. Add mod_ssml to freeswitch/conf/autoload/modules.conf.xml
2. Add conf/autoload_configs/ssml.conf.xml to freeswitch/conf/autoload_configs

## Build standalone mod_ssml module using FreeSWITCH devel package

Install FreeSWITCH devel package (assuming you have [FreeSWITCH Debian repository setup](https://github.com/signalwire/freeswitch/tree/master/scripts/packaging))
```
apt-get update
apt-get install -y libfreeswitch-dev
```

Change to a directory where mod_ssml sources will be compiled
```
cd /usr/src
```

Clone mod_ssml module
```
git clone https://github.com/freeswitch/mod_ssml -b main
```

Go to the module's source folder
```
cd mod_ssml
```

And build normally
```
./bootstrap.sh
./configure
make
make install
```