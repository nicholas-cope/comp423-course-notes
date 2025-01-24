# Setting up a dev container for Go

* Primary author: [Nicholas Cope](https://github.com/nicholas-cope)

* Reviewer: [Luke Allen](https://github.com/lukeallen13)

Welcome! In this introductory tutorial to the Go language, you'll set up a dev container, create a new project, and write a basic "Hello COMP423" program. 

!!! note
    This tutorial is heavily based on [this MkDocs tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/) by Kris Jordan.

## Prerequisites
1. **Git installed:** [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don't already have it.
2. **Visual Studio Code (VS Code):** Download and install it from [here](https://code.visualstudio.com/).
3. **Docker installed:** Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop).
4. **Command-line basics:** Your COMP211 command-line knowledge will serve you well here. If in doubt, review the Learn a CLI text!

## Part 1. Project Setup: Creating the Repository
### Step 1. Create a Local Directory and Initialize Git
(A) Open your terminal or command prompt.

(B) Create a new directory for your project. (Note: Of course, if you'd like to organize this tutorial somewhere else on your machine, go ahead and change into that parent directory first. By default this will be in your user's home directory.):

``` pwsh
mkdir comp423-course-notes
cd comp423-course-notes
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


<!-- ``` go
package main

import "fmt"

func main() {
    fmt.Println("hello world")
}
``` -->