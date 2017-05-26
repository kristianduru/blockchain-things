Notes of dos and dont's :

* DO use geth --fast and --cache=2048 to do a fast sync to get up to date with the block chain as fast as possible, takes hours instead of days.

* DO clean chaindata with removedb if you are going to do a fresh sync with --fast

* DONT start geth without --fast or it will disregard the reciepts gotten from fast syncing and start all over again with a slooow normal sync.

* DO make sure to force which chain you are going to use or get a client compiled and hard-configured to one of the chains.

* DONT forget to do a DAO refund for BOTH your ETC Ethereum Classic and ETH Ethereum keystore.

* DONT forget extraBalance of DAO refund.

* DO remember that you have an adress that is capable of existing on two chains with the "same" amount of ether ;)

* DO use docker containers to run multiple blockchain clients because its fun and doing sync on both will be hilarious for your diskIO

* DO try the below when creating transactions:
~~~~

// Set account and unlock it 
var defaultAccount = eth.accounts[0]; 
var myAccount = "0x...your account...";  // If not same as default
personal.unlockAccount(myAccount, "the password to myAccount");

// Send recipient 2 ether
var amount = web3.toWei(2.0, "ether")
var transaction = eth.sendTransaction({from:myAccount, to:"0x...recipientaddr...", value: amount})

// You can spam this command a couple times to see whats going on with the transaction
eth.getTransaction(transaction)
// output will have blockNumber set to null until transaction gets on the chain, just wait !  

~~~~
