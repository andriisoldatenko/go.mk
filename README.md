# go.mk
Include for Makefile for my personal Go projects, which includes: installing different inting tools and some useful run commands

## Usage

1. Download latest `go.mk` file

```bash
curl https://raw.githubusercontent.com/andriisoldatenko/go.mk/main/go.mk > go.mk
```

2. Include it to your Makefile:

```makefile
# Example of usage
# add this include to you main Makefile

-include go.mk
```

3. run `make install/go-linting`
4. :tada:

## What it includes?

[go.mk](./go.mk) has 3 basic linters ( feel free to add/remove one of your choice)

1. github.com/golangci/golangci-lint
2. github.com/daixiang0/gci
3. golang.org/x/tools

It includes special comment `# renovate depName=golang.org/x/tools` which helps us later to
configure [renovate](./renovate.json5) to automatically keep up-to-date linter versions etc.

#### useful commands:

1. install all linters locally (don't overwrite existing ones):

```bash
$ make install/go-linting
```

2. run linting/formating:

```bash
$ make go/lint
go fmt ./...
gci write --skip-generated .
go vet -copylocks=false ./...
make: ./hack/build/create_go_build_tags.sh: Command not found
golangci-lint run --build-tags "" --timeout 300s
```