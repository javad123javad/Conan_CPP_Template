# VSCode Template for C++ and Conan

For a long time, using C++ in Windows was a real pain for me. Eventually, I decided to solve this problem once and for all by creating a clean, reproducible workspace setup.

My desired workspace has the following specifications:
- Minimal dependency on the operating system
- A full-featured package manager (similar to `cargo` for Rust)
- Robust debugging tools
- Ease of use

All these requirements led to this setup.

---

## Prerequisites

### Install Conan
Assuming that `pip` and `python` are already installed on your system, you can install Conan with:

```shell
pip install conan
```

Verify your installation by running:

```shell
conan
```

You should see the Conan command-line help output. 
After Conan installation, modify the `conanfile.txt` to include any libraries you plan to use in your project. By default, it only contains the `GTest` library:

```ini
[requires]
gtest/1.17.0
[generators]
CMakeDeps
CMakeToolchain
[layout]
cmake_layout
```

## Project template
When you clone the project, you will see the following structure:

```
CppStack/
├── CMakeLists.txt
├── src/
│   └── main.cpp
├── Libs/
│   ├── include/
│   │   └── List.hpp
│   └── src/
│       └── List.cpp
└── tests/
    ├── CMakeLists.txt
    └── test_template.cpp
```

### `Libs` directory
The `Libs` directory contains a sample (dummy) library. You can add your own libraries here.
Note: You must edit the top-level  file to include any new libraries in the project build.

### `tests` directory

The `tests` directory contains your test files. You can add multiple test files here.
• 	Each new test file must be added to the `CMakeLists.txt` inside the `test` directory.
• 	To enable debugging in VSCode, you need to add a new debug configuration for each test file in the `launch.json` file. For example:

```json
"configurations": [
        {
            "name": "Debug test_template",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/build/build/Debug/tests/test_template.exe",
            "args": [],
            "cwd": "${workspaceFolder}",
            
        }
    ]
```