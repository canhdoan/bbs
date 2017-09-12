CX Object System
================

[![Build Status](https://travis-ci.org/skycoin/cxo.svg)](https://travis-ci.org/skycoin/cxo)
[![Coverage Status](https://coveralls.io/repos/skycoin/cxo/badge.svg?branch=master)](https://coveralls.io/r/skycoin/cxo?branch=master)
[![GoReportCard](https://goreportcard.com/badge/skycoin/cxo)](https://goreportcard.com/report/skycoin/cxo)
[![Telegram group link](telegram-group.svg)](https://t.me/joinchat/B_ax-A6oCR9eQuAPiJtvaw)

![logo](cxo_logo.png)

The CXO is objects system, goal of which is sharing any objects. The CXO
is low level and designed to build application on top of it

### Get Started and API Documentation

See [CXO wiki](https://github.com/skycoin/cxo/wiki/Get-Started) to get this information

### API Documentation

See [CXO wiki](https://github.com/skycoin/cxo/wiki) to get this information

### Installation and Version

Use [dep](https://github.com/golang/dep) to use particular version of the
CXO. The maser branch of the repository points to latest stable release.
Actually, it points to alpha-release for now.

To get the release use
```
go get -u -t github.com/skycoin/cxo/...
```
Test all packages
```
go test -cover -race github.com/skycoin/cxo/...
```


### Development

- [telegram group](https://t.me/joinchat/B_ax-A6oCR9eQuAPiJtvaw)

#### Modules

- `cmd` - apps
  - `cxocli` - CLI is admin RPC based tool to control any CXO-node
  - `cxod` - an example CXO daemon that accepts all subscriptions
- `data` - database interfaces, obejcts and errors
  - `data/cxds` - CX data store is implementation of key-value store
  - `data/idxdb` - implementation of index DB
  - `data/tests` - tests for the `data` interfaces
- `node` - TCP transport for CXO
  - `node/gnet` - raw TCP transport
  - `node/log` - logger
  - `node/msg` - protocol messages
- `skyobject` - CXO core: schemas, encode/decode, etc

And

- `intro` - examples
  - `intro/pass_through` - three nodes source->pipe->drain
    [README.md](intro/pass_through)
  - `intro/cxtweet` - CXO based command-line tweetter like app


#### Formatting

- All `.go` source files should be formatted with `gofmt`
- It's recommended to limit you lines with 80 or at least 120 characters
- Follow Golang naming convention: `CamelCase`, `Value()/SetValue()`,
  `IsExist()`, etc


### Dependencies

Dependencies are managed with [dep](https://github.com/golang/dep).

To install `dep`:

```sh
go get -u github.com/golang/dep
```

`dep` vendors all dependencies into the repo.

If you change the dependencies, you should update them as needed with
`dep ensure`.

Use `dep help` for instructions on vendoring a specific version of a dependency,
or updating them.

After adding a new dependency (with `dep ensure`), run `dep prune` to remove any
unnecessary subpackages from the dependency.

When updating or initializing, `dep` will find the latest version of a
dependency that will compile.

Examples:

Initialize all dependencies:

```sh
dep init
dep prune
```

Update all dependencies:

```sh
dep ensure -update -v
dep prune
```

Add a single dependency (latest version):

```sh
dep ensure github.com/foo/bar
dep prune
```

Add a single dependency (more specific version), or downgrade an existing
dependency:

```sh
dep ensure github.com/foo/bar@tag
dep prune
```


---