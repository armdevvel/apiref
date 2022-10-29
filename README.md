# apiref - UCRT API forwarding for Windows

apiref is a collection of UCRT API forwarders for Windows, released under the public domain. apiref produces proxy DLLs (api-*.dll), otherwise known as forwarding DLLs, that only exist ephemerally on Windows 10 but have to be physical files on Windows versions below 10. They are used to provide distinct API sets (core, threading, file system, etc.) to applications
    
(a) in a specialized way (e.g. application uses multithreading, but not the file system)

(b) in a platform-agnostic way (e.g. the actual methods can reside in ucrtbase.dll, kernel32.dll and other system libraries which the application does not link against directly).

Proxy DLLs created by apiref can be used to create applications that use the Windows 10 UCRT runtime (expected by certain toolchains, namely [LLVM v>=14](https://github.com/mstorsjo/llvm-mingw)) but can be run on earlier versions of Windows, such as Windows 8.1 or Windows RT.
The API set defined here is not necessarily exhaustive and will be extended if need arises.

# Installing
## From Source
To build apiref from source, all you need is CMake and your toolchain choice. After cloning the source, at the root of the directory you can build the project by running:

```bash
mkdir build && cd build
cmake ..
make
make install
```