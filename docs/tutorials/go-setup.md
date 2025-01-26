# Setting up a dev container for Go

* Primary author: [Nicholas Cope](https://github.com/nicholas-cope)

* Reviewer: [Luke Allen](https://github.com/lukeallen13)

Welcome! In this introductory tutorial to the Go language, you'll set up a dev container, create a new project, and write a basic "Hello COMP423" program. 

!!! note
    This tutorial is heavily based on [this MkDocs tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/) by Kris Jordan.

## Prerequisites
1. **A GitHub account:** If you don't have one yet, sign up at [GitHub](https://github.com/).
2. **Git installed:** [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don't already have it.
3. **Visual Studio Code (VS Code):** Download and install it from [here](https://code.visualstudio.com/).
4. **Docker installed:** Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop).
5. **Command-line basics:** Your COMP211 command-line knowledge will serve you well here. If in doubt, review the Learn a CLI text!

## Part 1. Project Setup: Creating the Repository
### Step 1. Create a Local Directory and Initialize Git
(A) Open your terminal or command prompt.

(B) Create a new directory for your project. (Note: Of course, if you'd like to organize this tutorial somewhere else on your machine, go ahead and change into that parent directory first. By default this will be in your user's home directory.):

``` pwsh
mkdir go-tutorial
cd go-tutorial
```

(C) Initalize a new Git repository:

``` pwsh
git init
```

(D) Create a README file:
``` pwsh
echo "# Go Tutorial" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2. Create a Remote Repository on GitHub
(1) Log in to your GitHub account and navigate to the [Create a New Repository](https://github.com/new) page.

(2) Fill in the details as follows:

- **Repository Name:** ```go-tutorial```
- **Description:** "Tutorial to the Go programming language."
- **Visibility:** Public

(3) Do not initialize the repository with a README, .gitignore, or license.

(4) Click **Create Repository**.

### Step 3. Link your Local Repository to GitHub
(1) Add the GitHub repository as a remote:

```git remote add origin https://github.com/<your-username>/go-tutorial.git```

Replace ```<your-username>``` with your GitHub username.

(2) Check your default branch name with the subcommand ```git branch```. If it's not main, rename it to main with the following command: ```git branch -M main```. Old versions of git choose the name master for the primary branch, but these days ```main``` is the standard primary branch name.

(3) Push your local commits to the GitHub repository:
```git push --set-upstream origin main```

(4) Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been *pushed* to remote. You can use ```git log``` locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.

## Part 2. Setting Up the Development Environment
### What is a Development (Dev) Container?

A dev container ensures that your development environment is consistent and works across different machines. At its core, a dev container is a preconfigured environment defined by a set of files, typically leveraging Docker to create isolated, consistent setups for development. Think of it as a "mini computer" inside your computer that includes everything you need to work on a specific project—like the right programming language, tools, libraries, and dependencies.

Why is this valuable? In the technology industry, teams often work on complex projects that require a specific set of tools and dependencies to function correctly. Without a dev container, each developer must manually set up their environment, leading to errors, wasted time, and inconsistencies. With a dev container, everyone works in an identical environment, reducing bugs caused by "it works on my machine" issues. It also simplifies onboarding new team members since they can start coding with just a few steps.

### Step 1. Add Development Container Configuration
1. In VS Code, open the ```go-tutorial``` directory. You can do this via: File > Open Folder.
2. Install the **Dev Containers** extension for VS Code.
3. Create a ```.devcontainer``` directory in the root of your project with the following file inside of this "hidden" configuration directory:

```.devcontainer/devcontainer.json```

The ```devcontainer.json``` file defines the configuration for your development environment. Here, we're specifying the following:

```name:``` A descriptive name for your dev container.

```image:``` The Docker image to use, in this case, the latest version of a Go environment.

```customizations:``` Adds useful configurations to VS Code, like installing the official Go VSCode Plugin. When you search for VSCode extensions on the marketplace, you will find the string identifier of each extension in its sidebar. Adding extensions here ensures other developers on your project have them installed in their dev containers automatically.


``` json
{
  "name": "COMP 423 Go Tutorial",
  "image": "mcr.microsoft.com/vscode/devcontainers/go",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.go"]
    }
  }
}
```

### Step 2. Reopen the Project in a VSCode Dev Container
Reopen the project in the container by pressing ```Ctrl+Shift+P``` (or ```Cmd+Shift+P``` on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running ```go version``` to see your dev container is running a recent version of Go without much effort!

## Part 3. Create the Program
1. In the terminal run the following command:
``` pwsh
go mod init go-tutorial
```
This creates a ```go.mod``` file, which tracks dependencies for your project.

2. Create a ```main.go``` file with the following content:
``` go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

3. Use the ```run``` command:
``` pwsh
go run main.go
```
Output:
``` Hello COMP423```

4. Use the ```build``` command to create an executable:
``` pwsh
go build -o hello_comp423
```
This produces a binary named ```hello_comp423```. Run the binary directly with:

    ```pwsh
    ./hello_comp423
    ```

!!! question "Why use ```go run``` vs ```go build```?"
    Use ```run``` to compile and run your program in one step for quick testing.
    
    Use ```build``` to create a reusable binary, useful for sharing or deploying applications. You can think of ```build``` as the Go equivalent for the ```gcc``` command you learned in COMP211.


## Conclusion
With this, you now have a functioning Go environment, created a simple program, and learned key go commands. Great job!





<!-- 
Use the mod subcommand
Use the run subcommand
Use the build subcommand (discuss this in the context of COMP211's gcc command), run the built binary directly, and discuss the difference from run -->


<!-- ``` go
package main

import "fmt"

func main() {
    fmt.Println("hello world")
}
``` -->