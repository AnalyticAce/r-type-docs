# Build Instructions
Build the project using **CMake** and ensure you manage third-party dependencies with conan.

!!! warning "Network Security"
    Running the server on a public network may expose it to security risks; consider implementing proper security measures.
## On Linux
 - You may execute the script `install.sh`:
```bash
chmod +x install.sh
./install.sh
cp bin/r-type_server bin/r-type_server ..
```

or the following commands:
```bash
make build
```

## On Windows
 - You may execute the script `build.bat`:
```bash
mkdir build
cd build
conan install .. --build=missing
cmake -DCMAKE_MODULE_PATH="$(pwd)" -DCMAKE_SYSTEM_NAME=Windows -DCMAKE_CXX_COMPILER=i686-w64-mingw32-g++ ..
msbuild .\r-type_client.vcxproj
msbuild .\r-type_client.vcxproj
copy ".\bin\r-type_server.exe" .
copy ".\bin\r-type_client.exe" .
```

If you have make install on your system execute the command below:
```bash
make build
```
