# LBRY Electrum Wallet (LEW) - Lightweight LBRY client

LBRY port of the Electrum 4.3.1 Bitcoin client.

There is currently no plan to maintain this port, it is for educational and research purposes, but feel free to submit issues to [here](https://github.com/Codes4Fun/lbry-electrum-wallet/issues)

The focus is primarily android, though a linux desktop is used in testing, and in theory other platforms could work.

I may also use this to test adding special features unique to lbry, such as managing claims.

```
Licence: MIT Licence
Porting: Codes4Fun
Original Author: Thomas Voegtlin
Language: Python (>= 3.8)
Homepage: https://github.com/Codes4Fun/lbry-electrum-wallet
```

## Getting started

_(If you've come here looking to simply run Electrum,
[you may download it here](https://github.com/Codes4Fun/lbry-electrum-wallet/releases).)_

Electrum itself is pure Python, and so are most of the required dependencies,
but not everything. The following sections describe how to run from source, but here
is a TL;DR:

```
$ sudo apt-get install libsecp256k1-0
$ python3 -m pip install --user ".[gui,crypto]"
```

### Not pure-python dependencies

If you want to use the Qt interface, install the Qt dependencies:
```
$ sudo apt-get install python3-pyqt5
```

For elliptic curve operations,
[libsecp256k1](https://github.com/bitcoin-core/secp256k1)
is a required dependency:
```
$ sudo apt-get install libsecp256k1-0
```

Alternatively, when running from a cloned repository, a script is provided to build
libsecp256k1 yourself:
```
$ sudo apt-get install automake libtool
$ ./contrib/make_libsecp256k1.sh
```

Due to the need for fast symmetric ciphers,
[cryptography](https://github.com/pyca/cryptography) is required.
Install from your package manager (or from pip):
```
$ sudo apt-get install python3-cryptography
```

If you would like hardware wallet support,
[see this](https://github.com/spesmilo/electrum-docs/blob/master/hardware-linux.rst).


### Running from tar.gz

If you downloaded the official package (tar.gz), you can run
Electrum from its root directory without installing it on your
system; all the pure python dependencies are included in the 'packages'
directory. To run Electrum from its root directory, just do:
```
$ ./run_electrum
```

You can also install Electrum on your system, by running this command:
```
$ sudo apt-get install python3-setuptools python3-pip
$ python3 -m pip install --user .
```

This will download and install the Python dependencies used by
Electrum instead of using the 'packages' directory.
It will also place an executable named `electrum` in `~/.local/bin`,
so make sure that is on your `PATH` variable.


### Development version (git clone)

_(For OS-specific instructions, see [here for Windows](contrib/build-wine/README_windows.md),
and [for macOS](contrib/osx/README_macos.md))_

Check out the code from GitHub:
```
$ git clone https://github.com/Codes4Fun/lbry-electrum-wallet.git
$ cd lbry-electrum-wallet
$ git submodule update --init
```

Run install (this should install dependencies):
```
$ python3 -m pip install --user -e .
```

Create translations (optional):
```
$ sudo apt-get install python-requests gettext
$ ./contrib/pull_locale
```

Finally, to start Electrum:
```
$ ./run_electrum
```

## Creating Binaries

- [Linux (tarball)](contrib/build-linux/sdist/README.md)
- [Linux (AppImage)](contrib/build-linux/appimage/README.md)
- [macOS](contrib/osx/README.md)
- [Windows](contrib/build-wine/README.md)
- [Android](contrib/android/Readme.md)

note: only android has been tested!

