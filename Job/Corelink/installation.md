# Installation

## Notes

> These documents are a work in progress, and we are trying to improve upon them on a daily basis. However, given our
> capacity and workload, there are bound to be things which get missed or checked in which should not have been checked
> in. If you find mistakes or documents wanting information, and you would like to help, you can do so in two ways
> 1. Submit corrections. When you update anything and submit a PR, we will review it and if all looks good, it will be
     added. This is the fastest way that one can expect changes to be in.
> 2. Submit tickets. If you are not sure how to make updates, or if you are short on time, please raise an issue in the
     repo, with details and what you think needs to be the expected text. We will try and update the literature to
     reflect any changes that we feel are merited. Note that this route will take longer than the first approach and
     there are no guarantees on the timeline.


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
-  [CMake](https://cmake.org/download/) - Used to build Corelink. Other build systems can be used, but 

> On most systems `OpenSSL` is the recommended TLS library to use. We highly recommend installing OpenSSL from a package
> manager or downloading the appropriate binaries from the website. However, this is not a possibility for embedded
> platforms. In this case other choices of TLS libraries from the list can be explored.


### Installing Corelink C++ client dependencies


- You can install Libwebsockets and your chosen TLS library from
    - `brew` on OSX
    - `vcpkg` on Windows
    - `apt` like package managers on Linux
- These are not the only way you can install these libraries. In many cases, they are shipped with your version of the
  OS.
- On *nix style systems (OSX, Linux), these packages will be typically installed in `/usr/local` or `/usr` or `/opt`
  paths. You will need to keep track of where the package manager installed these for you. The path is typically emitted
  when you install the libraries.
#### TLS Library

- If you wish to enable and use WSS on the client, you will need a compatible TLS library. Please see the list of
  supported TLS libraries above.

#### Libwebsockets

- Libwebsockets (LWS) is installable just like the TLS libraries above from package managers. We have tested the client
  to work for version `4.3.x`. We do not guarantee API compatibility should you choose to you use another version.
- You can also build LWS from source by heading over to their GitHub page, and following their instructions.
- Based on the installation method, you will need to keep track of the path that these libraries were installed under.

#### Installation examples

For Windows using vcpkg:

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

### Building Corelink Client

In order to build the client, you will first need to specify the following paths, either by command line, shell script, or by creating a `CMakeListsUser.txt` file:

```
CORELINK_CPP_STD
CORELINK_ASIO_CPP_PATH
CORELINK_RAPID_JSON_CPP_PATH
CORELINK_LWS_INCLUDE_PATH
CORELINK_OPENSSL_INCLUDE_PATH
CORELINK_LWS_LIB_PATH
CORELINK_OPENSSL_LIB_PATH
CORELINK_OPENSSL_BIN_PATH
```


##### CMake

We set up our CMake toolchain the following way

- We have a master file `CMakeLists.txt` which has all the generic parameters which can be shared amongst a group of
  developers.
- A user file called `CMakeListsUser.txt` which has parameters specific to your system and toolchain. This is never
  shared amongst developers.

Below are the contents of a sample `CMakeLists.txt` file for an OSX system.

> NB: This is just a sample file and the paths here could be different from the one on your system. Please do not raise
> tickets or issues to correct or fix these.

```cmake
####
# Author : Sarthak Tickoo (NYU IT HSRN)
####

# specify the minimum cmake version required.
cmake_minimum_required(VERSION 3.1)

# specify a name for your project. this can be anything
project(corelink-examples VERSION 0.1.0
        LANGUAGES C CXX)

# this piece of script tries to locate the user file on your system
# note that this looks for the user file in the project directory which typically is the directory this master 
# file resides in
if (EXISTS "${PROJECT_SOURCE_DIR}/CMakeListsUser.txt")
    include("${PROJECT_SOURCE_DIR}/CMakeListsUser.txt")
endif ()

# make sure that you force the specification of a C++ standard.
# minimum is 11. this will be set as a part of the user file
set(CMAKE_CXX_STANDARD_REQUIRED True)

# specify the target name as a variable
set(TEST basic-connect-test)

# prepare the target for build. this is where all your C++ header and source files go if you want to compile them
add_executable(${TEST} basic-connect-test.cpp)

# force treatment of warnings as errors. this saves lives. trust me.
target_compile_options(${TEST} PRIVATE
        $<$<CXX_COMPILER_ID:MSVC>:/W4 /WX>
        $<$<NOT:$<CXX_COMPILER_ID:MSVC>>:-Wall -Wextra -Wpedantic -Werror -Wno-deprecated-declarations>
        )
# Add the include paths that are needed
# the first path is the path to corelink c++ library itself
# the rest of the paths are defined as variables in the user file.
target_include_directories(${TEST}
        PUBLIC "/Users/sarthak/Work/hsrn/corelink/repos/corelink-client/cpp/include/"
        PUBLIC "${CORELINK_ASIO_CPP_PATH}"
        PUBLIC "${CORELINK_RAPID_JSON_CPP_PATH}"
        PUBLIC "${CORELINK_LWS_INCLUDE_PATH}"
        PUBLIC "${CORELINK_OPENSSL_INCLUDE_PATH}"
        )

# Add the paths for libraries to be linked
target_link_directories(${TEST}
        PUBLIC "${CORELINK_LWS_LIB_PATH}"
        PUBLIC "${CORELINK_LWS_BIN_PATH}"
        PUBLIC "${CORELINK_OPENSSL_LIB_PATH}"
        PUBLIC "${CORELINK_OPENSSL_BIN_PATH}"
        )

# set the dynamic library extension and prefix. This is dumb but works for now.
set(DYNA_LIB_EXT so)
set(LWS_PREFIX lib)
if (APPLE)
    set(DYNA_LIB_EXT dylib)
endif (APPLE)
if (WIN32)
    set(DYNA_LIB_EXT dll)
    set(LWS_PREFIX "")
endif (WIN32)
# specify which libraries need to be linked against our target
target_link_libraries(${TEST}
        ${LWS_PREFIX}websockets.${DYNA_LIB_EXT}
        libssl.${DYNA_LIB_EXT}
        libcrypto.${DYNA_LIB_EXT})
```

Below are the contents of a sample `CMakeListsUser.txt` file for an OSX system.

```cmake
# set the C++ standard we want to use
set(CMAKE_CXX_STANDARD 17)
 
# set appropriate paths for Libwebsockets to be visible to the compiler
set(CORELINK_LWS_ROOT "C:\\path\\to\\vcpkg\\installed\\x64-windows")
# this is where the header files for LWS reside
set(CORELINK_LWS_INCLUDE_PATH "${CORELINK_LWS_ROOT}\\include")
# this is where the prebuilt binaries for LWS reside
set(CORELINK_LWS_LIB_PATH "${CORELINK_LWS_ROOT}\\lib")
set(CORELINK_LWS_BIN_PATH "${CORELINK_LWS_ROOT}\\bin")
 
# set the appropriate paths for OpenSSL 1.1.1 to be visible to the compiler
set(CORELINK_OPENSSL_ROOT"C:\\path\\to\\vcpkg\\installed\\x64-windows")
# this is where the header files for OpenSSL reside
set(CORELINK_OPENSSL_INCLUDE_PATH "${CORELINK_OPENSSL_ROOT}\\include")
# this is where the prebuilt binaries for OpenSSL reside
set(CORELINK_OPENSSL_LIB_PATH "${CORELINK_OPENSSL_ROOT}\\lib")
set(CORELINK_OPENSSL_BIN_PATH "${CORELINK_OPENSSL_ROOT}\\bin")
 
# Set the appropriate paths for external source only dependencies
set(CORELINK_ASIO_CPP_PATH "C:\\path\\to\\corelink-client\\external-dependencies\\cpp\\asio-cpp\\v1.24.0\\")
set(CORELINK_RAPID_JSON_CPP_PATH "C:\\path\\to\\corelink-client\\external-dependencies\\cpp\\")
```


Once you've set the paths on your `CMakeListsUser.txt` file, you can build 


```bash
cd /path/to/corelink-client/cpp/
cmake -B client-build-debug -S .
cmake --build client-build-debug
```

## Closing remarks

- As you can gather from the steps above, the "installation" is merely downloading or installing things from package
  managers or git repositories.
- These steps have been reproduced on OSX, Mainstream Linux distributions, and Windows systems. In theory, these should
  work just fine on any system, if you use a standard C++ compiler.

