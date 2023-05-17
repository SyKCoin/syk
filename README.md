# # SYK COIN Masternode Setup  
# Step by step guide
 

Requirements: 	

1.) for 1 Masternode you need a wallet with 500 SYK Coins (1 additional coin you need for fees!)
2.) VPS for example on vultr, digital ocean or any other vps services

Feel free to use our reflinks to signup:

vultr: <a href="https://www.vultr.com/?ref=8953070"><img src="https://www.vultr.com/media/banners/banner_468x60.png" width="468" height="60"></a>

digital ocean: <a href="https://www.digitalocean.com/?refcode=7937f503c47f&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge"><img src="https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%201.svg" alt="DigitalOcean Referral Badge" /></a>
 
## start in the wallet 
in wallet: Open Debug console: 

```bash
createmasternodekey
```

<table>
<tr><td>example</td></tr>
<tr><td>alias= syk1</td></tr>
<tr><td>7Qd77fH2LGXwUZYHwXkXYz1naTAEMxbytRWwNFdfsjFe3MzaQPJ</td></tr>
</table>

```bash
getnewaddress "syk1"  
```

<table>
<tr><td>example</td></tr>
<tr><td>Sbf4EKxwKiSnzoC9g3uqfKhsNhbmkEePWp</td></tr>
</table>

send exact 20000 Coins to the address (confirmation need: 20) 


# Installation: for Security use SSH on your vps!!

# Start install the requirements on VPS:

```bash
sudo apt-get update && sudo apt-get upgrade -y
```
```bash
sudo apt-get upgrade -y
```
```bash
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip software-properties-common cmake -y
```
```bash
sudo add-apt-repository ppa:bitcoin/bitcoin
```
You will be prompted with "Enter". press enter

```bash
sudo apt-get update && sudo apt-get install libdb4.8-dev libdb4.8++-dev -y
```

download the wallet-client, tx and daemon file

```bash

wget https://github.com/SyKCoin/syk/releases/download/3000/linux.zip
```
fillout the password of your username and press enter


```bash
unzip linux.zip
```
```bash
sudo chmod +x sykd
```
```bash
sudo chmod +x syk-tx
```
```bash
sudo chmod +x syk-cli
```
```bash
sudo mv sykd syk-cli syk-tx /usr/bin/
```
```bash
sudo apt-get install libdb4.8-dev libdb4.8++-dev -y
```
```bash
mkdir $HOME/.syk
```
```bash
nano $HOME/.syk/syk.conf
```

copy this with your details in th conf. file (choose only another good rpcuser and a very good password, you need your masternode genkey from wallet and the ip address of the vps server)
```bash
#----
rpcuser=rpc_userchooseagoodone
rpcpassword=chooseagoodpassword
rpcallowip=127.0.0.1
#----
listen=1
server=1
daemon=1
maxconnections=1024
#----
externalip=your VPS IP-address
masternode=1
masternodeprivkey=MASTERNODE-GENKEY-from-debugconsole

addnode=158.247.203.147
addnode=216.238.80.97
addnode=158.247.220.9
addnode=139.180.169.66
#----
```
save this file by pressing CONTROL+O and press enter
close this file by pressing CONTROL+X

# start the vps server with

```bash
sykcoind
```
if everything is fine: you get an output: sykcoin server starting




### back in wallet
 
go to debug console

```bash
getmasternodeoutputs
```
<table>
<tr><td>example</td></tr>
 <tr><td>{</td></tr>
<tr><td>    "txhash": "b78439775da93558b3577c67ffab8a6a8f942c07d83ab2e9f5f3478014052d75", </td></tr>
<tr><td>     "outputidx": 0 {</td></tr>
<tr><td>   }</td></tr>
</table>


# Configure masternode.conf file (look at the example in file), reopen wallet and start masternode in debug console

<table>
<tr><td>example for masternode in masternode.conf file </td></tr>
<tr><td>mn1 IP_OF_THE_SERVER:4468 MASTERNODE_GENKEY TX_HASH TX_OUTPUTS</td></tr>
<tr><td>syk01 45.32.87.179:4468 7Qd77fH2LGXwUZYHwXkXYz1naTAEMxbytRWwNFdfsjFe3MzaQPJ b78439775da93558b3577c67ffab8a6a8f942c07d83ab2e9f5f3478014052d75 0</td></tr>
</table>

save file, reopen wallet and start in debug console !

```bash
startmasternode alias lockwallet "Alias"
```
