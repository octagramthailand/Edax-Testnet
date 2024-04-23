# Creating your Ethereum node

we reccommend using Ubuntu 20.04 as your operating system in order to follow this tutorial

## Please ensure that your environment has the following version of these dependency before starting the Ethereum node

GNU Make 4.3

Go go1.20.5.linux-amd64.tar.gz

GETH (Go-Ethereum) : 1.11.6-stable (the tutorial will instruct how to change the GETH version)

If you need to install these dependency please refer to the follwing sites

for [Go](https://www.digitalocean.com/community/tutorials/how-to-install-go-on-ubuntu-20-04)

for [GETH](https://geth.ethereum.org/downloads)

for [make](https://ioflood.com/blog/install-make-command-linux/)

# optional - testing go

## create directory & change directory

```bash
 mkdir hello
```

```bash
cd hello
```

## create go module

use curl ifconfig.me to find your IP address

```bash
 go mod init (your IP address)/hello
```

## create file for testing

```bash
 nano hello.go
```

## copy the following into hello.go file

```bash

package main

import "fmt"

func main() {
fmt.Println("Hello, World!")
}
```

## run the file

```bash
 go run .
```

expected output on the terminal
Hello, World!

# prepare GETH with the proper version

```bash
 git clone https://github.com/octagramthailand/Edax-Testnet.git
```

```bash
 cd EDAX_GETH
```

```bash
 make geth
```

```bash
 sudo cp build/bin/geth /usr/local/bin/
```

```python
# returns Geth Version: 1.11.6-stable
geth version
```

# start your ethereum node

```bash
 geth init --datadir ethereum-node genesis.json
```

join as miner node

```bash
 geth --datadir ethereum-node --networkid 4785 --port 30303 --bootnodes (bootstrap-node-record) --mine --miner.threads=1 --miner.etherbase=(your walllet address)
```

join as member node

```bash
geth --datadir ethereum-node --networkid 4785 --port 30303 --bootnodes (bootstrap-node-record)
```
