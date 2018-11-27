# uPlexa GUI

Copyright (c) 2014-2018 uPlexa.   
Portions Copyright (c) 2012-2013 The Cryptonote developers.

## Development resources

- Web: [uplexa.com](https://uplexa.com)
- Mail: [uplexa@protonmail.com](mailto:uplexa@protonmail.com)
- GitHub: [https://github.com/uPlexa/uplexa](https://github.com/uPlexa/uplexa)
- Discord: (https://discord.gg/a7mAQwJ)

## Vulnerability response

- Our Vulnerability Response Process encourages responsible disclosure. Please send a message to uplexa@protonmail.com with "vuln" somewhere within the title, or reach out to QuantumL3aper in Discord.

## Introduction

uPlexa  is an anonymous, secure, untraceable, decentralized digital currency, much like Monero. The advantages being that lower end IoT devices are able to mine at a more efficient rate, allowing for the network to become more decentralized. Other advantages include a lightweight blockchain, fast synctimes, and fairly fast transactions (2 minute block times). It may be used by anyone, anywhere. We will reach adoption through technical advancements, whilst also maintaining a focus on the forefront: marketing to adopters.

Our adoption advertising strategies revolve around a unique payment processing merchant we will be launching for UPX. Features for said system, do not exist for any current cryptocurrency. Other strategies will include incentivizing shop owners to have their users use UPX to pay, bringing more eyes to the ease-of-use of our cryptocurrency; whilst also lessening payment processing fee's from mass merchants and banks, all while allowing for security and anonymity.(edited)
Other devices we wish to include are video gaming consoles and smart home appliances. More details will be released about that next year.

**Privacy:** uPlexa uses a cryptographically sound system to allow you to send and receive funds without your transactions being easily revealed on the blockchain (the ledger of transactions that everyone has). This ensures that your purchases, receipts, and all transfers remain absolutely private by default.

**Security:** Using the power of a distributed peer-to-peer consensus network, every transaction on the network is cryptographically secured. Individual wallets have a 25 word mnemonic seed that is only displayed once, and can be written down to backup the wallet. Wallet files are encrypted with a passphrase to ensure they are useless if stolen.

**Untraceability:** By taking advantage of ring signatures, a special property of a certain type of cryptography, uPlexa is able to ensure that transactions are not only untraceable, but have an optional measure of ambiguity that ensures that transactions cannot easily be tied back to an individual user or computer.

## About this project

This is the GUI for the [core uPlexa implementation](https://github.com/uPlexa/uplexa). It is open source and completely free to use without restrictions, except for those specified in the license agreement below. There are no restrictions on anyone creating an alternative implementation of uPlexa that uses the protocol and network in a compatible manner.

As with many development projects, the repository on Github is considered to be the "staging" area for the latest changes. Before changes are merged into that branch on the main repository, they are tested by individual developers in their own branches, submitted as a pull request, and then subsequently tested by contributors who focus on testing and code reviews. That having been said, the repository should be carefully considered before using it in a production environment, unless there is a patch in the repository for a particular show-stopping issue you are experiencing. It is generally a better idea to use a tagged release for stability.

## License

See [LICENSE](LICENSE).

## Compiling the uPlexa GUI from source

### On Linux:

(Tested on Ubuntu 17.10 x64, Ubuntu 18.04 x64 and Gentoo x64)

1. Install uPlexa dependencies

  - For Debian distributions (Debian, Ubuntu, Mint, Tails...)

	`sudo apt install build-essential cmake libboost-all-dev miniupnpc libunbound-dev graphviz doxygen libunwind8-dev pkg-config libssl-dev libzmq3-dev libsodium-dev libhidapi-dev`

  - For Gentoo

	`sudo emerge app-arch/xz-utils app-doc/doxygen dev-cpp/gtest dev-libs/boost dev-libs/expat dev-libs/openssl dev-util/cmake media-gfx/graphviz net-dns/unbound net-libs/ldns net-libs/miniupnpc net-libs/zeromq sys-libs/libunwind dev-libs/libsodium dev-libs/hidapi`

2. Install Qt:

  *Note*: Qt 5.7 is the minimum version required to build the GUI. This makes **some** distributions (mostly based on debian, like Ubuntu 16.x or Linux Mint 18.x) obsolete. You can still build the GUI if you install an [official Qt release](https://wiki.qt.io/Install_Qt_5_on_Ubuntu), but this is not officially supported.

  - For Ubuntu 17.10+

    `sudo apt install qtbase5-dev qt5-default qtdeclarative5-dev qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-dialogs qml-module-qtquick-xmllistmodel qml-module-qt-labs-settings qml-module-qt-labs-folderlistmodel qttools5-dev-tools qml-module-qtquick-templates2`

  - For Gentoo

    `sudo emerge dev-qt/qtcore:5 dev-qt/qtdeclarative:5 dev-qt/qtquickcontrols:5 dev-qt/qtquickcontrols2:5 dev-qt/qtgraphicaleffects:5`

  - Optional : To build the flag `WITH_SCANNER`

    - For Ubuntu

      `sudo apt install qtmultimedia5-dev qml-module-qtmultimedia libzbar-dev`

    - For Gentoo

      The *qml* USE flag must be enabled.

      `emerge dev-qt/qtmultimedia:5 media-gfx/zbar`


3. Clone repository

    `git clone https://github.com/uplexa/uplexa-gui.git`

4. Build

    ```
    cd uplexa-gui
    QT_SELECT=5 ./build.sh
    ```

The executable can be found in the build/release/bin folder.

### On OS X:

1. Install Xcode from AppStore

2. Install [homebrew](http://brew.sh/)

3. Install [uplexa](https://github.com/uPlexa/uplexa) dependencies:

  `brew install boost --c++11`

  `brew install openssl` - to install openssl headers

  `brew install pkgconfig`

  `brew install cmake`

  `brew install zeromq`

  *Note*: If cmake can not find zmq.hpp file on OS X, installing `zmq.hpp` from https://github.com/zeromq/cppzmq to `/usr/local/include` should fix that error.

4. Install Qt:

  `brew install qt5`  (or download QT 5.8+ from [qt.io](https://www.qt.io/download-open-source/))

  If you have an older version of Qt installed via homebrew, you can force it to use 5.x like so:

  `brew link --force --overwrite qt5`

5. Add the Qt bin directory to your path

    Example: `export PATH=$PATH:$HOME/Qt/5.8/clang_64/bin`

    This is the directory where Qt 5.x is installed on **your** system

6. Grab an up-to-date copy of the uplexa-gui repository

  `git clone https://github.com/uplexa/uplexa-gui.git`

7. Go into the repository

  `cd uplexa-gui`

8. Start the build

  `./build.sh`

The executable can be found in the `build/release/bin` folder.

**Note:** Workaround for "ERROR: Xcode not set up properly"

Edit `$HOME/Qt/5.8/clang_64/mkspecs/features/mac/default_pre.prf`

replace
`isEmpty($$list($$system("/usr/bin/xcrun -find xcrun 2>/dev/null")))`

with
`isEmpty($$list($$system("/usr/bin/xcrun -find xcodebuild 2>/dev/null")))`

More info: http://stackoverflow.com/a/35098040/1683164


### On Windows:

The uPlexa GUI on Windows is 64 bits only; 32-bit Windows GUI builds are not officially supported anymore.

1. Install [MSYS2](https://www.msys2.org/), follow the instructions on that page on how to update system and packages to the latest versions

2. Open an 64-bit MSYS2 shell: Use the *MSYS2 MinGW 64-bit* shortcut, or use the `msys2_shell.cmd` batch file with a `-mingw64` parameter

3. Install MSYS2 packages for uPlexa dependencies; the needed 64-bit packages have `x86_64` in their names

    ```
    pacman -S mingw-w64-x86_64-toolchain make mingw-w64-x86_64-cmake mingw-w64-x86_64-boost mingw-w64-x86_64-openssl mingw-w64-x86_64-zeromq mingw-w64-x86_64-libsodium mingw-w64-x86_64-hidapi
    ```

    You find more details about those dependencies in the [uPlexa documentation](https://github.com/uPlexa/uplexa). Note that that there is no more need to compile Boost from source; like everything else, you can install it now with a MSYS2 package.

4. Install Qt5

    ```
    pacman -S mingw-w64-x86_64-qt5
    ```

    There is no more need to download some special installer from the Qt website, the standard MSYS2 package for Qt will do in almost all circumstances.

    **Note:** There is a known issue that GUI won't lauch properly when building tag v0.13.0.3 with Qt 5.11.2.

    If your encounter issue with that, please remove current Qt by: `pacman -R mingw-w64-x86_64-qt5`

    And install 5.11.1 instead by: `pacman -U http://repo.msys2.org/mingw/x86_64/mingw-w64-x86_64-qt5-5.11.1-3-any.pkg.tar.xz`

5. Install git

    ```
    pacman -S git
    ```

6. Clone repository

    ```
    git clone https://github.com/uplexa/uplexa-gui.git
    ```

7. Build

    ```
    cd uplexa-gui
    ./build.sh
    cd build
    make deploy
    ```

The executable can be found in the `.\release\bin` directory.
