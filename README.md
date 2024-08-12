# sweeper-bot
Using this bot, you can create a bundle of transaction that execute against the compromised account, spending ETH that was received in the same block.


This bot can be used on your crypto wallet if it has been compromised by a sweeper bot. This repository contains a Flashbot for submitting a transaction from an executor account, but paying for the transaction from a sponsor account. This is accomplished by submitting a Flashbots transaction bundle, with the first "sponsor" transaction paying the "executor" wallet in ETH, followed by a series of executor transactions that spend this newly received ETH on gas fees.

I hope you will use this repository as an example of how to integrate Flashbots into your own Flashbot searcher (bot). For more information,

Use case
The use case for this multi-transaction setup is to make calls from an account that has a compromised private key. Since transferring in any ETH to this compromised wallet will immediately be swept by bots that monitor that account, transferring in funds will also give any attacker the ability to withdraw tokens that are held by that account.

Environment Variables
In the File Index.ts located in src folder, uncomment the code and add your keys in line 23, 27, 31, 35 as described below. Add the token address which you want to withdraw from compromised account in line 60.
Or better contact me at ourrehman063@gmail.com as one wrong line of code can send your funds to wrong address.
ETHEREUM_RPC_URL - Ethereum RPC endpoint. Can not be the same as FLASHBOTS_RPC_URL
PRIVATE_KEY_EXECUTOR - Private key for the compromised Ethereum EOA that owns assets that needs to be transferred
PRIVATE_KEY_SPONSOR - Private key for an account that has ETH that will be used to fund the miner for the "ZERO_GAS" transactions
RECIPIENT - Ethereum EOA to receive assets from ZERO_GAS account
FLASHBOTS_RELAY_SIGNING_KEY - Optional param, private key used to sign messages to Flashbots to establish reputation of profitability
Setting Miner Reward
Inside src/index.ts is :

const PRIORITY_GAS_PRICE = GWEI.mul(31)
This is the priority fee, on top of baseFee, sent to the miner for all transactions in the bundle, including the sponsor-funding transaction. All transactions use the same gasPrice, with no coinbase transfers in any transaction. In the case of a block re-organization, hopefully all transactions will appear in the next block as well, preventing sweeper bots from gaining access to the incoming ETH before it is spent on gas fees.

Selecting a different "engine"
This system can operate against different protocols by swapping a new "engine" class that adheres to "Base" functionality in the main() function. Available engines:

TransferERC20
CryptoKitties
Approval721
An engine accepts relevant parameters during construction and provides functions to retrieve transaction descriptions to be passed in to Flashbots. Selecting and configuring a different engine requires directly modifying the source, uncommenting the engine and setting the necessary variables.

Usage

What you need to do step by step :

download the files and unzip into a folder called rescue on your desktop
go to google and search for download Node js , download it and install it .
use Vscode software , drag the folder inside Vscode
in vscode menu look for terminal > open new terminal .
in terminal make sure you are in the folder rescue , type "ls" and enter key , you should see other folders and files , if so type "npm i" wait for the modules to be downloaded .
edit the file index.js , Global_modules.js and .env to your needs , in index.js you can manipulate the Gas needed to make your Tx go first before the sweeper bot , in Global_modules.js you will need to replace that base64 code with yours where you incode the smart contract ABI of the token you are trying to rescue into base64 and paste it there and finally in the .env file you need to setup your sender address : hacked wallet / reciver address : safe wallet where you want the tokens to be sent , token contract : smart contract address , network put the ticker of the network i.e : on ethereum put : ETH , on fantom put FTM , on binance network put BNB etc .., and private keys of the compromised wallet , and so on ..
go back to the terminal in vs code , type "node index.js" the bot will run , it will keep on looping and waiting for Gas , you need to send some native tokens to that wallet and observe , sometimes you might need to send just a bit extra but in chunks so when the sweeper bot is busy the rescue bot transfers out your stuck tokens !

#CryptoSecurity #Flashbot #EthSweeperBot #WalletCompromise #FundWithdrawal #SecureYourAssets #BlockchainProtection #CryptoRecovery #CryptoSecurityMatters #FlashbotWithdrawalService #WalletRecoverySolutions #EthSweeperBotProtection #SecureYourCryptoAssets #FundSecurityMeasures #BlockchainSafety #CompromisedWalletRecovery Keywords: Flashbot withdrawal service for compromised wallets. Safeguarding crypto funds from Eth Sweeper bot attacks. Recovering funds from compromised Ethereum wallets. Securing your assets after a wallet compromise incident. Crypto users' fund recovery solution against Eth Sweeper bot breaches. Protecting blockchain assets affected by wallet hacks. Preventing unauthorized access to cryptocurrency wallets. Flashbot-powered solution for compromised wallet funds withdrawal. Counteracting Eth Sweeper bot attacks on crypto wallets. Restoring funds from hacked Ethereum wallets securely. Strengthening asset protection post-wallet compromise incident. Safeguarding cryptocurrency funds against breaches by Eth Sweeper bots. Reinforcing blockchain security in the face of wallet hacks. Mitigating unauthorized access to digital currency wallets.



