# OpenWRT-Python3-Utils

Package List in this Repository:

 * [X] click
 * [X] csscompressor
 * [X] dnslib
 * [X] docutils
 * [X] ecdsa
 * [ ] jinja2 >= 2.7
 * [ ] libdns
 * [ ] libsass >= 0.4 (some c++ compilation issues with std::round atm)
 * [X] networkx 
 * [X] paramiko
 * [X] passlib
 * [X] pip
 * [X] pycrypto
 * [ ] pyramid
 * [ ] pyramid-debugtoolbar
 * [ ] pyramid_tm
 * [ ] pyramid_rpc
 * [X] PyYAML
 * [X] requests
 * [ ] SQLAlchemy >= 0.9
 * [ ] sqlalchemy_utils
 * [X] tornado
 * [X] waitress
 * [ ] zope.sqlalchemy >= 0.7
 

TODO: Double check all licenses to make sure no copy/paste errors

## Update:

Migrated to use main OpenWRT ``packages/`` feed. Software depends on python3 and setuptools instead of including them in this feed.

## How to Install:

1. Add to your `openwrt/feeds.conf.default` file:

   `src-git py3utils https://github.com/NucleaPeon/OpenWRT-Python3-Utils.git`
2. Update your feeds: `./scripts/feeds update -a` (or `./scripts/feeds update py3utils`)
3. Install packages from your feeds (I've found this way works, but isn't necessarily recommended): `./scripts/feeds install -a`

### Install on Image:
* Run `make menuconfig`
* Enter `Languages --> Python -->` and select desired packages with the built in property `[*]`

**or**

### Install via Modules/Packages
*. Enter `Languages --> Python3 -->` and select desired packages with the modular property `[M]`


## Host Dependencies:

Attempting to install the python3-pycrytpo resulted in an error:

    In file included from /usr/include/stdio.h:27:0,
                 from src/_fastmath.c:29:
    /usr/include/features.h:398:23: fatal error: gnu/stubs.h: No such file or directory
    #include <gnu/stubs.h>

This **may** be an issue with the package not bringing in the correct host build dependencies, but one solution I found was to install the `gcc-4.8-multilib` and `g++-4.8-multilib` packages. Compilation resumes as usual. 

If that doesn't work, go to:

    [*] Advanced Configuration options (for developers) --->
         [*] Toolchain Options --->
         C Library implementation (Use (e)glibc) --->
             (X) Use (e)glibc
             
Ensure that (e)glibc is selected instead of `( ) Use musl`.
    
