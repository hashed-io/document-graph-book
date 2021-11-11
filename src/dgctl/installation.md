```daoctl``` is an open source, command line application for Document Graph organizations written in Go. It is also a secure wallet for managing private keys and submitted transactions.

#### Build

Building ```daoctl``` requires Go v15 and above.

```
git clone https://github.com/hypha-dao/daoctl/
cd daoctl
go build
./daoctl -h
```

#### Download binary

https://github.com/hypha-dao/daoctl/releases


#### Run help
```
./daoctl --help                                                                                                                                     ST 4   master
Decentralized Autonomous Organization (DAO) control application for Hypha DAO query and actions.
Query and manage roles, assignments, periods, payouts, and proposals.

Example use:
	daoctl get assignments --include-proposals
	daoctl get treasury

Hypha - Dapps for a New World - visit online @ hypha.earth

Usage:
  daoctl [command]

Available Commands:
  backup      creates a local backup of current DAO data
  close       close a proposal
  create      create an object (e.g. proposal) based on the JSON file
  edit        propose an edit to an object
  get         get objects from the DAO on-chain smart contract
  help        Help about any command
  propose     propose a role
  query       Query action history on the DAO for specific users
  serve       Start the Hypha prometheus metrics server
  set         set data on the DAO on-chain smart contract
  treasury    multi-chain token/value redemption module
  vault       The vault is a secure key store (wallet). Your key is stored encrypted by the passphrase.
  vote        vote pass or fail on a ballot

Flags:
  -a, --active               show active objects (default true)
      --config string        config file (default is ./daoctl.yaml)
      --csv                  Output data as CSV to console - not supported on all commands yet
      --debug                Enables verbose debug messages
      --expiration int       Set time before transaction expires, in seconds. Defaults to 30 seconds. (default 30)
      --failed-proposals     include a table with failed proposals
  -f, --file string          filename
  -h, --help                 help for daoctl
  -o, --include-archive      include a table with the archive objects
      --include-proposals    include a table with proposals in the output
      --output-file string   Output CSV data to file - not supported on all commands yet (default "output.csv")
      --vault-file string    Wallet file that contains encrypted key material (default "./eosc-vault.json")

Use "daoctl [command] --help" for more information about a command.
```


#### Sample configuration.yaml
Here's a sample configuration file for the testnet. You can save as a file and use ```--config``` then the file name as a parameter.
```yaml
EosioEndpoint: https://test.telos.kitchen
AssetsAsFloat: true
DAOContract: dao.hypha
Treasury:
  TokenContract: husd.hypha
  Symbol: HUSD
  Contract: bank.hypha
  EthUSDTContract: 0xdac17f958d2ee523a2206206994597c13d831ec7
  EthUSDTAddress: 0xC20f453a4B4995CA032570f212988F4978B35dDd
  BtcAddress: 35hfgfaUouzYixTUDV6CFqMiTSZcuNtTf9
TelosDecideContract: trailservice
DAOUser: treasurermmm
HyperionEndpoint: https://testnet.telosusa.io/v2
```
