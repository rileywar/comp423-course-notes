# Setting up a dev container for Rust

* Primary author: [Riley Warmuth](https://github.com/rileywar)

* Reviewer: [Mason Drabik](https://github.com/mkdrabik)

## Introduction

In this tutorial, you will learn how to set up a development container for Rust from scratch. You will also create a basic "Hello COMP423" Rust program to verify that your environment is properly configured.
#
#

## Prerequisites

1. **Install Docker:** Download and install Docker Desktop. [Get Docker Here](https://www.docker.com/products/docker-desktop).
2. **Install VS Code:** Download and install VS Code. [Get VS Code Here](https://code.visualstudio.com/).
3. **Install the Remote - Containers Extension:** In VS Code, go to the Extensions Marketplace (Ctrl+Shift+X or Cmd+Shift+X on Mac), search for "Dev Containers," and install the official "Remote - Containers" extension.

#
#

## Part 1: Setting up Your Environment
##

**1. Create a folder for your project:**
Open a new terminal and run the following commands:

```bash
mkdir rust-dev-container
cd rust-dev-container
```
This will create and navigate to your project folder.

**2. Initialize a Git repository**

Initialize a new repository by running: ```git init```

Create a README.md file and commit it:

```bash
echo "# Rust Dev Container" > README.md
git add README.md
git commit -m "Initial commit with README"
```
Go onto to GitHub and create a new repository and then 
link your local repository to your remote one on GitHub:
```bash
git remote add origin https://github.com/<your-username>/<your-repository-name>.git
```
Push your changes to GitHub:
```bash
git branch -M main
git push --set-upstream origin main
```
Verify your changes on GitHub.

**3. Create a folder for your devcontainer**

Open your project in VS Code (Ctrl+O or Cmd+O on Mac).

Create a .devcontainer folder:
```bash
mkdir .devcontainer
```

**4. Create a devcontainer.json file**
Create the devcontainer.json file:
```bash
touch .devcontainer/devcontainer.json
```
Add the following configuration:

```json
{
  "name": "Rust Dev Container",
  "image": "mcr.microsoft.com/devcontainers/rust:1",
  "customizations": {
    "vscode": {
      "extensions": [
        "rust-lang.rust-analyzer"
      ]
    }
  },
  "postCreateCommand": "cargo install --list",
  "remoteUser": "vscode"
}
```

**5. Open the project in the dev container**

In VS Code, press Ctrl+Shift+P (or Cmd+Shift+P on Mac) and type "Dev Containers: Reopen in Container."

Wait for the container to build and set up the environment.

**6. Verify the setup**

Open a terminal in VS Code and check the Rust compiler version:
```bash
rustc --version
```
Example output:
```bash
rustc 1.70.0 (example-build-date)
```

##Part 2: Running Rust##

**1. Create a new Rust project**

Use cargo to create a new binary project without initializing a Git repository:
```bash
cargo new hello-comp423 --vcs none
```
Navigate to the project directory:
```bash
cd hello-comp423
```

**2. Edit the main file**

Open src/main.rs and modify it as follows:
```json
fn main() {
    println!("Hello COMP423");
}
```

##Step 3: Build and run the program##

**Build the project**

To build the project, use the following command:
```bash
cargo build
```
This creates an executable file in the target/debug directory. To run it:
```bash
./target/debug/hello-comp423
```
Output:
```bash
Hello COMP423
```
Run the project directly

Alternatively, you can use ```cargo run```, which combines building and running the program in one step:
```bash
cargo run
```
Output:
```bash
Hello COMP423
```

!!! note "Explanation of Commands"
    ```cargo build```: Compiles the project into an executable binary for later use. Similar to gcc -o in C programming.
    ```cargo run```: Compiles and immediately runs the program, ideal for quick testing.


#
##Conclusion##

Congratulations! You have successfully set up a Rust development container, created a new project, and run a Rust program. You’re now ready to explore more advanced Rust features!