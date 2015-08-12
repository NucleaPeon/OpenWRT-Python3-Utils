# OpenWRT-Python3-Utils

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
4. Run `make menuconfig`
5. Enter `Languages --> Python -->` and select desired packages with the built in property `[*]`

**or**

### Install via Modules/Packages
5. Enter `Languages --> Python -->` and select desired packages with the modular property `[M]`

