# Install Go language

## change to home directory

```bash
 cd ~
```

## retrieve the go file

```bash
curl -OL https://golang.org/dl/go1.20.5.linux-amd64.tar.gz

```

## verify the download

```bash
 sha256sum go1.20.5.linux-amd64.tar.gz
```

## extract the file

```bash
 sudo tar -C /usr/local -xvf go1.20.5.linux-amd64.tar.gz
```

## set up path for go file

```bash
 sudo nano ~/.profile
```

## adding the following line to the end of the file

press crtl+x => y => enter to finish the editing process

```bash
 export PATH=$PATH:/usr/local/go/bin
```

## refresh your profile

```bash
source ~/.profile
```

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

# prepare and initiate geth client

```bash
 sudo add-apt-repository -y ppa:ethereum/ethereum
```

```bash
 sudo apt-get update
```

```bash
 sudo apt-get install ethereum
```

```bash
 apt install make
```

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

leave the folder for the next step

```bash
 cd ..
```

# start your ethereum node

```bash
 geth init --datadir (choose your folder name) genesis.json
```

join as miner node

```bash
 geth --datadir (your folder name) --networkid 4785 --port 30303 --bootnodes (bootstrap-node-record) --mine --miner.threads=1 --miner.etherbase=(your walllet address)
```

join as member node

```bash
geth --datadir (your folder name) --networkid 4785 --port 30303 --bootnodes (bootstrap-node-record)
```
