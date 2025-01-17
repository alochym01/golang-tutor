### [How to code with Go](https://golang.org/doc/code.html)

-   Using vscode
    -   Setting per workspace `.vscode/settings.json`
        ```
        {
            "go.toolsGopath": "/home/hadn/.go"
        }
        ```
    -   Settings OS enviroment
        ```
        export GOROOT=/usr/local/go
        PATH="$GOROOT/bin:$PATH:$HOME/.local/bin:$HOME/bin"
        export PATH
        ```
    -   Setting GO environment variables before `code .`
        -   Run `export GOPATH=$(pwd)`
        -   Run `export GOBIN=$(pwd)/bin`
-   Code organization
    -   A workspace contains many repo, which is managed by git
    -   Each repo contains one or more packages
    -   Each package contains one or more Go source files in a single directory
    -   The **PATH** to a package's directory detemines its import path
-   Workspace hierarchy with 2 directory at root
    -   `src` contains Go source files
    -   `bin` contains executeable commands
    -   TODO example
-   GOROOT enviroment variable
    -   This is the location of Go executable file - `/usr/local/go/bin`
-   GOPATH enviroment variable
    -   This is the location of your workspace
    -   example: **export GOPATH=$(pwd)**
-   Using library
    -   `mkdir -p {bin,pkg,src}`
    -   Create folder structure
        ```
        chym/
            ├── bin
            ├── pkg         # will be stored compile third party packages
            ├── README.md
            └── src
                ├── github.com
                │   └── user
                │       └── stringutil
                │           └── reverse.go
                └── hello.go
        ```
    -   Create `hello.go` with content
        ```
        package main

        import (
            "fmt"

            "github.com/user/stringutil"
        )

        func main() {
            fmt.Println(stringutil.Reverse("!oG ,olleH"))
        }
        ```
    -   Executing `go run src/hello`
    -   Building `go install src/hello` ==> `bin/hello` executable file
