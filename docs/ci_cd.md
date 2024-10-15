# R-Type Project: Testing and CI/CD Documentation

## Overview

This document outlines the Continuous Integration and Continuous Deployment (CI/CD) process for the R-Type project. We use GitHub Actions to automate our build, test, and deployment processes.

## CI/CD Workflow

Our CI/CD pipeline is defined in the `.github/workflows/ci.yml` file. The workflow is triggered on:
- Push events to the `main` and `Develop` branches
- Pull requests to the `main` branch

### Workflow Details

#### Name: CI R-Type

#### Jobs:

We have a single job named `build` that runs on the latest Ubuntu environment.

#### Build Matrix:

We use a build matrix to define our build configuration:
- Operating System: Ubuntu Latest
- Build Type: Release
- C Compiler: GCC
- C++ Compiler: G++

#### Steps:

1. **Checkout**: Uses `actions/checkout@v4` to fetch the repository.

2. **Caching**:
   - Conan dependencies are cached using `actions/cache@v4`
   - Build output is cached to speed up subsequent builds

3. **System Updates and Dependencies**:
   - Updates `apt-get`
   - Installs necessary system libraries and development packages

4. **CMake Installation**:
   - Installs CMake using `apt-get`

5. **Google Test Setup**:
   - Configures and builds Google Test from source

6. **Conan Setup**:
   - Installs Conan package manager
   - Creates a default Conan profile

7. **Dependencies Installation**:
   - Uses Conan to install project dependencies

8. **CMake Configuration**:
   - Configures the project using CMake
   - Sets the C++ compiler, C compiler, and build type

9. **Build**:
   - Builds the project using CMake

### Worflow
```
name: CI R-Type

on:
  push:
    branches:
      - main
      - Develop
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ${{ matrix.os }}

    strategy:
      fail-fast: false
      matrix:
        os: [ubuntu-latest]
        build_type: [Release]
        c_compiler: [gcc]
        cpp_compiler: [g++]
        include:
          - os: ubuntu-latest
            c_compiler: gcc
            cpp_compiler: g++

    steps:
      - uses: actions/checkout@v4

      - name: Cache Conan dependencies
        uses: actions/cache@v4
        with:
          path: |
            ~/.conan/data
            ~/.conan
          key: ${{ runner.os }}-conan-${{ hashFiles('conanfile.txt') }}
          restore-keys: |
            ${{ runner.os }}-conan-

      - name: Cache build output
        uses: actions/cache@v4
        with:
          path: build
          key: ${{ runner.os }}-build-${{ hashFiles('**/CMakeLists.txt', '**/*.cpp', '**/*.h*') }}
          restore-keys: |
            ${{ runner.os }}-build-

      - name: Update apt-get
        if: matrix.os == 'ubuntu-latest'
        run: |
          sudo apt-get update
          sudo apt-get upgrade -y
          sudo apt-get install -y libudev-dev libgl-dev \
            libx11-dev libx11-xcb-dev libfontenc-dev libboost-all-dev \
            libgtest-dev libice-dev libsm-dev libxau-dev \
            libxaw7-dev

      - name: Install CMake
        if: matrix.os == 'ubuntu-latest'
        run: sudo apt-get install -y cmake

      - name: Set google test
        if: matrix.os == 'ubuntu-latest'
        run: |
          cd /usr/src/gtest
          sudo cmake .
          sudo make

      - name: Install Conan
        run: pip install conan

      - name: Conan version
        run: conan --version

      - name: Create default Conan profile
        run: conan profile detect --force

      - name: Install dependencies
        if : matrix.os == 'ubuntu-latest'
        run: |
          conan install . --build=missing \
          -c tools.system.package_manager:mode=install \
          -c tools.system.package_manager:sudo=True

      - name: Set reusable strings
        id: strings
        shell: bash
        run: echo "build-output-dir=${{ github.workspace }}/build" >> "$GITHUB_OUTPUT"

      - name: Configure CMake
        if : matrix.os == 'ubuntu-latest'
        run: |
          cmake -B ${{ steps.strings.outputs.build-output-dir }} \
          -DCMAKE_CXX_COMPILER=${{ matrix.cpp_compiler }} \
          -DCMAKE_C_COMPILER=${{ matrix.c_compiler }} \
          -DCMAKE_BUILD_TYPE=${{ matrix.build_type }} \
          -S ${{ github.workspace }}

      - name: Build
        if : matrix.os == 'ubuntu-latest'
        run: |
          cmake --build ${{ steps.strings.outputs.build-output-dir }} \
          --config ${{ matrix.build_type }}
```


## Testing

While not explicitly shown in the workflow, it's implied that Google Test is set up for unit testing. To run tests:

1. Ensure Google Test is properly set up (as done in the workflow).
2. Add a step in the workflow to run tests after the build step:

```yaml
- name: Run Tests
  working-directory: ${{ steps.strings.outputs.build-output-dir }}
  run: ctest -C ${{ matrix.build_type }}
```

## Deployment

The current workflow does not include deployment steps. When ready to add deployment:

1. Add a new job or steps after the build job.
2. Use appropriate GitHub Actions for your deployment target (e.g., AWS, Azure, GCP, etc.).
3. Ensure all necessary secrets are stored in GitHub Secrets.

## Best Practices

1. **Regular Updates**: Keep dependencies and tools updated regularly.
2. **Code Quality**: Consider adding static code analysis tools to the workflow.
3. **Security Scanning**: Implement security scanning for vulnerabilities.
4. **Documentation**: Update this documentation as the workflow evolves.

## Troubleshooting

If the CI/CD pipeline fails:

1. Check the GitHub Actions logs for detailed error messages.
2. Ensure all dependencies are correctly specified in the project files.
3. Verify that the build matrix is appropriate for your project needs.
4. Test the build process locally to isolate issues.

## Future Improvements

1. Add code coverage reporting.
2. Implement automatic versioning.
3. Set up automatic releases for tagged commits.
4. Add performance benchmarking tests.

---

This documentation provides an overview of your current CI/CD setup and includes suggestions for testing and future improvements. As your project evolves, remember to keep this documentation updated to reflect any changes in your CI/CD process.