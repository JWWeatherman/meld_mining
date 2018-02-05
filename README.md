![alt text](https://user-images.githubusercontent.com/32912678/35784331-37a7f8be-09e4-11e8-81d9-db255096ff6a.png "Overview Diagram")
# Meld Mining
### Cloud mining that reduces fraud and provides more control to customers. 

---

# Introduction
The cost of specialized hardware 
is prohibitive for many people 
that would like to participate in Bitcoin mining.
As a result "cloud mining" has become very popular,
but it has two major drawbacks.

First, fraud is very common with cloud mining
because the users are not able to verify that 
their mining time did or did not earn a block reward. 

Second, the mining rewards are distributed 
through large numbers of small payments.
This can be tedious and is
unlike bitcoin mining where a miner
may mine for months 
before discovering a block that contains a large reward.

Meld mining fixes these problems
by providing proof the mining was executed,
and by allowing miners
control of the mining difficulty level 
(the higher the difficulty the less often blocks are discovered,
but the higher the block reward).

---
# Major Components
There are three participants in meld mining.
![alt text](https://user-images.githubusercontent.com/32912678/35784331-37a7f8be-09e4-11e8-81d9-db255096ff6a.png "Overview Diagram")

## Meld Mining Coordinator
This service coordinates mining
between miners and cloud providers.
Sell nonces to miners,
provide nonces to cloud operators,
accumulate payments from cloud operators
and distribute earnings 
(with evidence that calculations were correctly completed).

## Cloud Mining Provider
Cloud mining providers maintain and operate data-center equipment
on behalf of the miners.
They accept nonce ranges,
execute the hash calculations,
broadcast found blocks to the bitcoin network,
and distribute bitcoin block rewards.

## Miners
Miners pay cloud operators to 
perform calculations to discover a 
bitcoin block using nonces they select.

# How it works
![Diagram](https://user-images.githubusercontent.com/32912678/35783537-fd182474-09d6-11e8-9ebb-0e17a95fccac.png)Format: ![Alt Text](url)
## Step 1
Miners purchase a range of nonces
that will be mined.
They are provided with a time stamped
hash of the ranges so that they will be able to verify
mining was executed correctly.

This is essentially a purchase of mining hardware
hosting that can range from a seconds to weeks.

## Step 2
The meld mining coordinator
provides the nonces to mine
and pays the cloud mining provider
for the rental of mining hardware.

## Step 3
As the cloud hardware provider
calculates hashes 
he discovers bitcoin blocks.
He keeps block rewards as they are discovered.

## Step 4
As the cloud hardware provider
calculates hashes 
using the provided nonces 
he publishes the proof that the job is completed
in the form of attempted blocks.

## Step 5
Periodically the cloud hardware provider
makes payments to the meld mining coordinator
based on the % of the block rewards discovered 
using the provided nonces.

## Step 6
Miners are able to query attempted blocks database
to ensure that their nonces were correctly calculated.

## Step 7
Miners are paid when their nonces 
meet the difficulty level they specified. 

## Difficulty Selection
When miners purchase the use of mining hardware
by specifying a range of nonces to use,
they also specify the difficulty level 
than needs to be met for a mining reward.

If they selected standard difficulty
this will match the current difficulty to obtain a bitcoin block reward.
The amount paid to the miner 
will be the same amount of bitcoin as a bitcoin block reward
(averaged over the mining period).

If they selected a lower difficulty level 
they will be paid when a nonce they 
selected is close
to finding a block reward
(this is how mining pools pay miners more often)
and the reward will be proportionally lower.

If they selected a higher difficulty level
they will be paid when a nonce they 
selected finds a bitcoin block AND meets the higher 
level of difficulty
and the reward will be proportionally higher.

# Security Threats

## A malicious mining partner could delay or ignore block with successful nonces 
If a malicious mining partner could delay any blocks discovered
with a selected nonce,
they could give themselves an advantage 
in finding a block using another nonce first.
This would allow them to obtain the block reward 
even though we have paid for the computing power.

### Safety Features
* We are get paid daily for our "hash power" 
so even if the miner avoids our wining block
it will not effect the compensation for mining.
* We still determine the winner based on the nonce 
meeting or exceeding the difficulty level.
But as long as a hash is generated,
using that nonce,
we can determine if we have a winner.
* We will ensure that cloud partners 
calculate our nonces first
and have enough processing power
to do this within the first 30 seconds of a 
block being discovered.
This is to ensure that nonces don't need 
to be calculated on blocks that have
already been found.

## A malicious meld mining reseller could harm the mining partner by sharing the nonces
A meld mining reseller knows the nonce,
but is not paid by the block reward,
so he could share the nonce with a competing miner.
This would allow the competing miner,
assuming he has more hash power,
to reduce the profitability of his competitor
by ensuring he will never be first to find a block
using those nonces.

### Safety Features
* The mining partner would detect this breach
as soon as the first block is mined 
by a competitor using the nonce range.
* A competitor must still mine the nonce range.
Assuming a 10% profitability this would earn 
the malicious competitor a total of ~20k assuming a $200,000
block reward.
This is not enough to justify the effort involved by the malicious reseller
and the malicious miner to coordinate the deal,
let alone cover the costs of mining reconfiguration, etc.
* With several major competitors in bitcoin mining,
it would be uninteresting for any miner to cost a competitor
a single block reward.

## A malicious mining partner could use the wrong public key after finding a block
If a mining partner discovers a valid block,
using a nonce range that has been selected,
he could simply keep the block reward for himself 
rather than using our public key in the coinbase transaction.

### Safety Features
* We are get paid daily for our "hash power" 
so we don't care if the block
that is found earns a block reward.
* We still determine the winner based on the nonce 
meeting or exceeding the difficulty level.
But as long as a hash is generated,
using that nonce,
we can determine if we have a winner.

## An end customer could buy a nonce range and share it with a competing miner 
If an end customer knows the nonces that he has selected
he could share them with a competing miner,
and, unlike the risk from a malicious reseller,
this attack could be repeated regularly.

* The end customer is not provided with the nonces,
but rather a time stamped hash of the nonces he has selected.
After the mining period the nonces and resulting hashes
are published with the time stamped hash
so that he can be sure his nonces were mined and verify
that the winner was selected fairly.







