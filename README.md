# OpenWRT-Python3-Utils

Fixed setuptools and pip issues as far as I know. Pip no longer errors out on setuptools module missing, likely due to InstallDev section and proper python3 mk imports and variables.


Package List in this Repository:

 * [X] csscompressor
 * [X] ecdsa
 * [ ] libsass (some c++ compilation issues with std::round atm)
 * [X] paramiko
 * [X] pip
 * [X] pycrypto
 * [X] setuptools
 * [X] tornado
 * [ ] pyramid
 * [ ] pyramid-debugtoolbar
 * [ ] pyramid_tm
 * [ ] pyramid_rpc
 * [X] waitress
 * [ ] sqlalchemy_utils
 * [X] passlib
 * [X] docutils
 * [X] click
 * [X] networkx
 * [X] PyYAML
 * [ ] SQLAlchemy >= 0.9
 * [ ] zope.sqlalchemy >= 0.7
 * [ ] jinja2 >= 2.7
 * [ ] libsass >= 0.4

TODO: Double check all licenses to make sure no copy/paste errors

## How to Install:

1. Add to your `openwrt/feeds.conf.default` file:
   `src-git py3utils https://github.com/NucleaPeon/OpenWRT-Python3.4-Tornado.git`
2. Update your feeds: `./scripts/feeds update -a` (or `./scripts/feeds update py3utils`)
3. Install packages from your feeds (I've found this way works, but isn't necessarily recommended): `./scripts/feeds install -a`

### Install on Image:
* Run `make menuconfig`
* Enter `Languages --> Python -->` and select desired packages with the built in property `[*]`

**or**

### Install via Modules/Packages
*. Enter `Languages --> Python -->` and select desired packages with the modular property `[M]`


## Host Dependencies:

Attempting to install the python3-pycrytpo resulted in an error:

    In file included from /usr/include/stdio.h:27:0,
                 from src/_fastmath.c:29:
    /usr/include/features.h:398:23: fatal error: gnu/stubs.h: No such file or directory
    #include <gnu/stubs.h>

This **may** be an issue with the package not bringing in the correct host build dependencies, but one solution I found was to install the `gcc-4.8-multilib` and `g++-4.8-multilib` packages. Compilation resumes as usual.
