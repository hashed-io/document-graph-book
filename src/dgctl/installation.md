```dgctl``` is an open source, command line application for Document Graph organizations written in Go. It is also a secure wallet for managing private keys and submitted transactions.

#### Build

Building ```dgctl``` requires Go v15 and above.

```
git clone https://github.com/hashed-io/dgctl/
cd dgctl
go build
./dgctl -h
```

#### Download binary

https://github.com/hashed-io/dgctl/releases


#### Run help
```
./dgctl --help                                                                                             
Usage:
  dgctl [command]

Available Commands:
  backup      creates a local backup of current graph
  create      create an object (e.g. proposal) based on the JSON file
  edit        propose an edit to a document
  get         get objects from the on-chain smart contract
  help        Help about any command
  set         set data on the on-chain smart contract
  vault       The vault is a secure key store (wallet). Your key is stored encrypted by the passphrase.

Flags:
  -a, --active               show active objects (default true)
      --config string        config file (default is ./dgctl.yaml)
      --csv                  Output data as CSV to console - not supported on all commands yet
      --debug                Enables verbose debug messages
      --expiration int       Set time before transaction expires, in seconds. Defaults to 30 seconds. (default 30)
  -f, --file string          filename
  -h, --help                 help for dgctl
      --output-file string   Output CSV data to file - not supported on all commands yet (default "output.csv")
      --vault-file string    Wallet file that contains encrypted key material (default "./eosc-vault.json")

Use "dgctl [command] --help" for more information about a command.
```

