
pre-commit-golang
=================

golang hooks for http://pre-commit.com/

# Purpose
The purpose of pre-commit hooks is to implement automated quality checks before code is committed to maintain a clean codebase and git history.

## Requirements
* [python](https://www.python.org/)
* [pre-commit](https://pre-commit.com/)

## Setup
`pre-commit install` to install the local `.pre-commit-config.yaml`, this will identify which repo (including version) and hooks to run. `pre-commit` will now run on every `git commit`

`pre-commit run <hook_id>` can run a specific hook.

`pre-commit run --all-files` can be used to run all commands.

## Local Development
- Can be used to test new or existing scripts on your local machine.
https://pre-commit.com/#repository-local-hooks

### Using these hooks

Add this to your `.pre-commit-config.yaml`

    - repo: https://github.com/dnephin/pre-commit-golang
      rev: master
      hooks:
        - id: go-fmt
        - id: go-vet
        - id: go-lint
        - id: go-imports
        - id: go-cyclo
          args: [-over=15]
        - id: validate-toml
        - id: no-go-testing
        - id: golangci-lint
        - id: go-critic
        - id: go-unit-tests
        - id: go-build
        - id: go-mod-tidy

### Available hooks

- `go-fmt` - Runs `gofmt`, requires golang
- `go-vet` - Runs `go vet`, requires golang
- `go-lint` - Runs `golint`, requires https://github.com/golang/lint but is unmaintained & deprecated in favour of [`golangci-lint`](https://github.com/golangci/golangci-lint)
- `go-imports` - Runs `goimports`, requires golang.org/x/tools/cmd/goimports
- `go-cyclo` - Runs `gocyclo`, require https://github.com/fzipp/gocyclo
- `validate-toml` - Runs `tomlv`, requires
   https://github.com/BurntSushi/toml/tree/master/cmd/tomlv
- `no-go-testing` - Checks that no files are using `testing.T`, if you want
  developers to use a different testing framework
- `golangci-lint` - run `golangci-lint run ./...`, requires
  [golangci-lint](https://github.com/golangci/golangci-lint)
- `go-critic` - run `gocritic check ./...`, requires [go-critic](https://github.com/go-critic/go-critic)
- `go-unit-tests` - run `go test -tags=unit -timeout 30s -short -v`
- `go-build` - run `go build`, requires golang
- `go-mod-tidy` - run `go mod tidy -v`, requires golang
- `go-mod-vendor` - run `go mod vendor`, requires golang
