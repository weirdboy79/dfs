## DEFENSE

**Smart & Safe Digital Storage for any Crypto Assets**

Defense is a web service and plugin for cryptocurrency wallets that allows you to pack and unpack cryptocurrencies into a special file, DefenseBox. 

All binaries for different operating systems, you can download in the releases repository:

https://github.com/dfscoin/dfs/releases
P2P port: 28991, RPC port: 28992

----

#### Defense Lab

*An online service for work with Defense Box*

All the features of Defense Box in one service. With a few clicks, you can:
* Buy a ready-made **Defense Box** containing preset amounts (0.1 ETH, 0.01 BTC, etc.);
* Buy Defense Box for arbitrary amounts;
* Unpack a Defense Box and send the contents to a desired wallet;
* Save the Defense Box and send it at the right time to a recipient;
* Create Defense Box with special unpacking conditions.

----

#### What can Defense Box do?

Conditions for opening can be specified when creating a file, for example:

* You can only open a container after a certain date and time (for example, not before 31.12.2020 00:00);
* It is possible to set the opening conditions to depend on the rate of any cryptocurrency being more or less than a certain value;
* Possible to open if **BTC / BCC / ETH / ETC** (supported currencies) rates are greater or less than user-defined values;
* Only a recipient can open it (confirmable via email, Telegram and / or telephone);
* Any smart contracts are no longer valid after a certain date.

----

#### Defense Lab

*An online service for work with Defense Box*

All the features of Defense Box in one service. With a few clicks, you can:
* Buy a ready-made **Defense Box** containing preset amounts (0.1 ETH, 0.01 BTC, etc.);
* Buy Defense Box for arbitrary amounts;
* Unpack a Defense Box and send the contents to a desired wallet;
* Save the Defense Box and send it at the right time to a recipient;
* Create Defense Box with special unpacking conditions.

----

### Masternode Setup Guide

#### Desktop wallet setup Step 1

1. Open your Defense coin wallet
2. Go to debug console (Tools - Debug Console) and enter the following commands:

`masternode genkey` *save this masternode privkey*

`getaccountaddress 0` *you will get new Masternode wallet address*

3. Send 1000 DFS to Masternode wallet address.
4. Enter the following command: 

`masternode outputs` *proof of transaction*

5. Open your masternode.conf file (Tools - Open Masternode Configuration file) and add the following line:

`MN_ALIAS SERVER_IP:28991 masternode_privkey output_txid output_index` 

*Example: MN1 127.0.0.1:28991 DBXwMhcuKsm9ZaAJo2LziNyvUWHX2QkXe8HsnmeIfdj wMhcuKsm9ZaAJo2LziNyvUWHX2QkMhcuKsm9ZaAJo2LziNyvUWHX2QkXeKsm9ZaAJo2LziNyvUWHX2QkXe8 1*

#### Server setup

Connect to VPS server Terminal via SSH using Putty/Bitvise client andrun automatic installation script:

`wget -q https://github.com/dfscoin/dfs/releases/download/v3.0.0.0/masternode.sh && bash masternode.sh` *you'll need to paste your masternode_privkey while installing*

#### Desktop wallet setup Step 2

1. Close and open your Defense coin wallet
2. Go to Debug Console and enter the following command:

`startmasternode alias 0 <MN_ALIAS>` *You should see something like this: { "alias" : "MN1", "result" : "successful" }*

#### Server Usage

`dfs-cli mnsync status`

`dfs-cli getinfo`

`dfs-cli masternode status`

Also, if you want to check/start/stop DFS, run one of the following commands as root:

`systemctl status dfs` *To check the service is running*

`systemctl start dfs` *To start dfs service*

`systemctl stop dfs` *To stop dfs service*

`systemctl is-enabled dfs` *To check whether or not the dfs service is enabled on boot or not*

----

### Masternode Update Collateral Guide

1. Open your masternode.conf file (Tools - Open Masternode Configuration file) and add **#** before MN1

*Example #MN1 127.0.0.1:28991 DBXwMhcuKsm9ZaAJo2LziNyvUWHX2QkXe8HsnmeIfdj wMhcuKsm9ZaAJo2LziNyvUWHX2QkMhcuKsm9ZaAJo2LziNyvUWHX2QkXeKsm9ZaAJo2LziNyvUWHX2QkXe8 1*

2. Close and open your Defense coin wallet
3. Resent new collateral
5. Wait 20 confirmation
6. Enter the following command:

`masternode outputs` *proof of transaction*

7. Open your masternode.conf file (Tools - Open Masternode Configuration file). Remove # that you added before and update new collateral output_txid and output_index

`MN_ALIAS SERVER_IP:28991 masternode_privkey output_txid output_index`

*Example MN1 127.0.0.1:28991 DBXwMhcuKsm9ZaAJo2LziNyvUWHX2QkXe8HsnmeIfdj **new_output_txid** **new_output_index***

8. Close and open your Defense coin wallet
9. Go to Debug Console and enter the following command:

`startmasternode alias 0 <MN_ALIAS>` *You should see something like this: { "alias" : "MN1", "result" : "successful" }*