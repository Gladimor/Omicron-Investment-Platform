Omicron Investment Platform
======================================================
Introduction
---------------------------------------------
Omicron (OMC) is a digital blockchain-based asset that accrues interest through two mechanisms: minting and BTC dividends. It is the first step towards having an unbanked investment world where an independent digital currency asset yields returns in an alternate medium of exchange. OMC plans to be a major inflation and investment vehicle for the cryptocurrency community as well as various brick-and-mortar entities. The core principle of Omicron's investment platform is to allow investors to own a digital asset that adds value to itself- just like shares in a dividend-issuing company. Easily transferable for a quick turnover without the need of intermediary brokers, the OMC asset will be the choice dividend vehicle for investors around the globe. Biweekly dividends ensure that no matter the price of the asset, the asset owner always will receive a 0.00001% share of the dividend pool, per Omicron, every 2 weeks. BTC dividends will be funded every 2 weeks through trading on the volatile altcoin market as well as lending capital for margin-trading exchanges (stable interest). The loan interest guarantees a biweekly issuance of dividends, while the altcoin trading revenue is a major bonus, many times greater than loan yields. The trading yields aren't guaranteed biweekly as there may be an occurrence where there is a net loss during the timeframe. A minimum balance of 10,000 OMC in an address will be required to qualify for dividend yields. A BTC address must be associated with the OMC address, which will be done through the main website, and soon through the Omicron client itself.

Official Omicron Nodes
------------------------------------
All official Omicron nodes are hosted in private datacenters managed by professional cloud hosting providers

Toronto (Seednode): 104.131.60.172

London: 138.68.148.172

Singapore: 139.59.228.205

Frankfurt: 46.101.167.84

San Fransisco: 107.170.221.177

Compilation
-------------------------------------------------
**How to setup a daemon on a Ubuntu 14.04 x64 system**

###*Set up a swapfile if your system has less than 1.5 GB of memory*

fallocate -l 2G /swapfile

  chown root:root /swapfile

  chmod 0600 /swapfile

  mkswap /swapfile

  swapon /swapfile

  nano /etc/fstab
  
**Add this to the bottom of the file:**

  /swapfile none swap sw 0 0
  
###*Begin compilation*

  apt-get update && apt-get upgrade

  apt-get install ntp unzip git build-essential libssl-dev libdb-dev

  apt-get install libdb++-dev libboost-all-dev libqrencode-dev

  apt-get install aptitude

  aptitude install miniupnpc libminiupnpc-dev

  git clone https://github.com/Gladimor/Omicron-Investment-Platform.git

  cd Omicron-Investment-Platform/src/leveldb

  chmod 755 build_detect_platform

  make libleveldb.a libmemenv.a
  
  cd

  cd Omicron-Investment-Platform/src

  make -f makefile.unix USE_UPNP=1 USE_QRCODE=1 USE_UPNP=1

  strip omicrond

  cp omicrond /usr/bin/

  omicrond

  nano ~/.omicron/omicron.conf
Add this to the configuration file:

  rpcuser=rpc_user

  rpcpassword=rpc_pass

  rpcallowip=127.0.0.1

  listen=1

  server=1

  txindex=1

  daemon=1
Run the daemon

  omicrond
