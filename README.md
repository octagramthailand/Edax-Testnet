1 install go

// change to home directory

> cd ~

// retrieve the go file

> curl -OL https://golang.org/dl/go1.20.5.linux-amd64.tar.gz

// verify the download

> sha256sum go1.20.5.linux-amd64.tar.gz

// extract the file

> sudo tar -C /usr/local -xvf go1.20.5.linux-amd64.tar.gz

//set up path for go file

> sudo nano ~/.profile

// adding the following line to the end of the file

> export PATH=$PATH:/usr/local/go/bin

> (press crtl+x => y => enter to finish the editing process)

//refresh your profile

> source ~/.profile

optional - testing go

// create directory & change directory

> mkdir hello

> cd hello

// create go module

> go mod init <your IP address>/hello

//create file for testing

> nano hello.go

// copy the following into hello.go file

package main

import "fmt"

func main() {
fmt.Println("Hello, World!")
}

//run the file

> go run .

expected output on the terminal
Hello, World!

2. prepare and initiate geth client

> sudo add-apt-repository -y ppa:ethereum/ethereum

> sudo apt-get update

> sudo apt-get install ethereum

> apt install make

> git clone https://github.com/SorrawitRUNGRUJEE/EDAX_GETH.git

> cd EDAX_GETH

> make geth

> sudo cp build/bin/geth /usr/local/bin/

// leave the folder for the next step

> cd ..

> nano genesis.json

// copy the following content into the terminal

{
"config": {
"chainId": 4785,
"homesteadBlock": 0,
"eip155Block": 0,
"eip158Block": 0,
"byzantiumBlock": 0,
"constantinopleBlock": 0,
"petersburgBlock": 0,
"istanbulBlock": 0,
"muirGlacierBlock": 0,
"berlinBlock": 0,
"londonBlock": 0,
"arrowGlacierBlock": 0,
"grayGlacierBlock": 0,
"eip150Block": 0,
"eip150Hash": "0x0000000000000000000000000000000000000000000000000000000000000000",
"etash":""
},
"difficulty": "1000",
"gasLimit": "2000000",
"alloc": {
"6a45Da18249Fd31AAE38477F5Fe4162E0d575D18": {
"balance": "10000000000000000000000"
},
"49aC57289477f5340d619400Bd4489De25266039": {
"balance": "20000000000000000000000"
},

    "2ad6D7A9A86d9ABe330a1F44B26046f2D93efcdE":{
      "balance":"10000000000000000000000"
    },
    "FeF78F6613B31Fb212A258c877FD222C82580abF":{
        "balance":"10000000000000000000000000000000"
    }

}
}

// press crtl + x then press y then press enter to save the change

> geth init --datadir <choose your folder name> genesis.json

join as miner node

> geth --datadir <your folder name> --networkid 4785 --port 30303 --bootnodes <bootstrap-node-record> --mine --miner.threads=1 --miner.etherbase=<your walllet address>

join as member node

geth --datadir <your folder name> --networkid 4785 --port 30303 --bootnodes <bootstrap-node-record>
