# Getting Started


> These documents are a work in progress, and we are trying to improve upon them on a daily basis. However, given our
> capacity and workload, there are bound to be things which get missed or checked in which should not have been checked
> in. If you find mistakes or documents wanting information, and you would like to help, you can do so in two ways
> 1. Submit corrections. When you update anything and submit a PR, we will review it and if all looks good, it will be
     added. This is the fastest way that one can expect changes to be in.
> 2. Submit tickets. If you are not sure how to make updates, or if you are short on time, please raise an issue in the
     repo, with details and what you think needs to be the expected text. We will try and update the literature to
     reflect any changes that we feel are merited. Note that this route will take longer than the first approach and
     there are no guarantees on the timeline.


There are many ways to set up the Corelink client depending on your setup, machine architecture, host OS, choice of package manager, development environment, and project needs. 


We provide a basic setup guide for 

## Corelink Client Installation

### Notes

- The Corelink C++ client is a _header_ only library.
- What this means is that you only need to add Corelink as part of your header search paths and `#include` it where
  necessary. Ideally, this should be done as early as permissible.
- This has its pros and cons.
    - The pros include the fact that Corelink is built as a part of YOUR application. This means that it is statically
      linked to your application/ library. This has benefits in terms of speed, simplicity and no cross DLL linking or
      marshalling.
    - The cons include the fact that if you have multiple services/ applications, all of them will have a "copy" of
      Corelink in them. Also, compile times are longer.
    - The upsides in our case outweigh the cons, hence the choice of keeping this as a header only library.
    - In theory, Corelink CAN be compiled to a dynamically linked library, but, we have not tested this.
    - This can however change in the future.

### Pre-requisites

The following steps should be generally applicable on any host system .

- You will need a C++ compiler of your choice which supports `C++ 11` or up.
    - On Linux or Mac, you would ideally have `g++` or `clang++`, or both.
    - On Windows, you have the option of using `MSVC++`, `Cygwin`, or `Mingw`. Identify your tool chain well in
      advance.
    - If you are on Windows and have Visual Studio installed, you will most likely have `MSVC++` installed already.
- These documents assume that you are comfortable using your preferred toolchain. We present examples using CMake as it
  is the easiest way of demonstrating and compiling source across platforms.
- There are some platform specific examples for MSVC++ and Xcode, which can be found in the examples repository as an
  addendum, but will not be a focus of this document.
### Installing Corelink Client

You can clone the `corelink-clients` repo by itself, or, get the dependencies associated with it too.

If you wish to clone the client repo with the source only dependencies.

```shell
git clone --recursive --recurse-submodules --remote-submodules https://dev.hsrn.nyu.edu/corelink/corelink-client.git
```

If you just wish to clone the client repo

```shell
git clone https://dev.hsrn.nyu.edu/corelink/corelink-client.git
```

### Dependencies

The current C++ Corelink Client has these direct external dependencies

- [Libwebsockets](https://github.com/warmcat/libwebsockets) - Binary installation/ source compilation required
    - Depends further on TLS libraries for Websocket Secure (`WSS`). Any **one** of the below are supported.
        - `OpenSSL`- v1.1.1
        - `MbedTLS` - Latest
        - `LibreSSL` - Latest
        - `WolfSSL` - Latest
- [Asio C++](https://think-async.com/Asio/asio-1.22.2/doc/) - Header only library. Used for IP based socket protocols.
- [RapidJSON](https://rapidjson.org) - Header only library. Used for JSON functionality within the client.
-  [CMake](https://cmake.org/download/) - Used to build Corelink. Other build systems can be used as per your preference. 

> On most systems `OpenSSL` is the recommended TLS library to use. We highly recommend installing OpenSSL from a package
> manager or downloading the appropriate binaries from the website. However, this is not a possibility for embedded
> platforms. In this case other choices of TLS libraries from the list can be explored.


### Installing Corelink C++ client dependencies

- You can install Libwebsockets and your chosen TLS library from
    - `brew` on OSX
    - `vcpkg` on Windows
    - `apt` like package managers on Linux
- These are **not the only way** you can install these libraries. In many cases, they are shipped with your version of the OS.
- On *nix style systems (OSX, Linux), these packages will be typically installed in `/usr/local` or `/usr` or `/opt`
  paths. You will need to keep track of where the package manager installed these for you. The path is typically emitted
  when you install the libraries.
#### TLS Library

- If you wish to enable and use WSS on the client, you will need a compatible TLS library. Please see the list of
  supported TLS libraries above.
- On most systems, OpenSSL is recommended. 

#### Libwebsockets

- Libwebsockets (LWS) is installable just like the TLS libraries above from package managers. We have tested the client
  to work for version `4.3.x`. We do not guarantee API compatibility should you choose to you use another version.
- You can also build LWS from source by heading over to their GitHub page, and following their instructions.
- Based on the installation method, you will need to keep track of the path that these libraries were installed under.

#### Installation examples

For Windows using `vcpkg`:

```shell
vcpkg install openssl
vcpkg install libwebsockets
```

For OSX using Homebrew:

```shell
brew install openssl
brew install libwebsockets
```


#### Source only header dependencies

The source only dependencies are housed
in [external-dependencies](https://dev.hpc.nyu.edu/corelink/external-dependencies/-/tree/master/) repository.

However, external dependencies is added as a submodule as part of the Corelink client.
If you wish to install them this way, see the [client installation notes](#installing-corelink-client).

You can clone this explicitly.

```bash
git clone https://dev.hsrn.nyu.edu/corelink/external-dependencies.git
```

Some things to note

- This will fetch all the required _source only_ dependencies required for the client and other components to
  function.
- The two libraries that are used from this are ASIO C++ and RapidJSON. There might be other libraries present here,
  but the client does not use them at the moment. However, examples demonstrating the use of the client might. This
  does not imply in any way that the client requires them.
- You will need to identify and keep the paths to the `include` directories of ASIO C++ and RapidJSON handy.
