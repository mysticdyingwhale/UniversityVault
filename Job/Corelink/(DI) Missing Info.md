# Docs Missing Info
DI (Docs Improvements)


Docs need to be updated:

```cpp
// enable all features by defining this macro
#define CORELINK_ENABLE_ALL_FEATURES
#define CORELINK_USE_CONCURRENT_QUEUE
#define CORELINK_USE_UDP
#define CORELINK_USE_TCP
#define CORELINK_USE_WEBSOCKET
// C++ compiler will see this macro above and then expand all the necessary items
#include <corelink_all.hpp>
```

You will need to install Libwebsockets and a TLS Library (OpenSSL recommended)
- For Windows, use [vcpkg](https://vcpkg.io/en/) 
- For OSX, use [Homebew](https://brew.sh/)
- For Linux, many options exist depending on your distribution.

- Provide links for `vcpkg` and how to install `lws` and `openssl` with it

- Link examples repo in examples page 
  
- VS screenshots not accurate
	- Missing Corelink build directory
	- Missing corelink.lib
	- For linker and include directories just use the `x64-windows` installed directory
		- convenience is important

- Add a common error guide
	- DLL errors
	- Debugging->Environment-> `PATH=%PATH%;C:\path\to\vcpkg\installed\x64-windows\bin`

- Additional information on the general docs site. 

- Reproduce on CLion

- Needs guide for building core-link on Windows:

```bash
cd /path/to/corelink-client/cpp/
cmake -B client-build-debug -S .
cmake --build client-build-debug
```

Make sure you have make a `CMakeListsUser.txt` file in your `corelink-client/cpp` folder with the following:

**FILL IN THE PATHS**

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
set(CORELINK_ASIO_CPP_PATH C:\\path\\to\\corelink-client\\external-dependencies\\cpp\\asio-cpp\\v1.24.0\\)
set(CORELINK_RAPID_JSON_CPP_PATH C:\\path\\to\\corelink-client\\external-dependencies\\cpp\\)
```



NOTE: the cpp specific docs are in the docs folder of the cpp client




