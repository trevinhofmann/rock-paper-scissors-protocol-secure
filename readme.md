# RPSPS: Rock-Paper-Scissors Protocol Secure

RPSPS is a peer-to-peer protocol for playing cryptographically secured games of rock-paper-scissors.

## Abstract

A cryptographically secure implementation of rock-paper-scissors would allow players to compete in a simple game with untrusted partners over an insecure connection.  By operating under a scheme based on Nash equilibrium and leveraging the Bitcoin network, players can stake assets on the outcome of games.  A Nash equilibrium is achieved when the two parties store escrow funds into a multisignature address and refuse to sign the funds back to their sender until after the completion of a successful round of games.  Batching multiple games into a round and using a micropayment channel to iteratively increase payments after each game reduces the number of transactions and corresponding fees.

## Introduction

Online gaming has come to rely on trusted third parties.  These trusted authorities tend to have upkeep costs that result in fees charged the the players.  The servers of trusted authorities become prime targets for malicious attackers.  Large amounts of funds are stored on these servers and must be protected by the authorities, presenting a counterparty risk to players.  RPSPS allows players to hold funds in their own full control for the majority of their gaming experience.

Trustless wagering systems exist, but most have been implemented inefficiently as coins layered on top of the Bitcoin protocol.  RPSPS functions more efficiently with a direct communication channel between players and basic use of the Bitcoin block chain.  Players do not need to trade their bitcoins for another coin, and the protocol can be extended for similar assets.


## Communication Flow

To initialize a game, a player first sends an invitation to their desired opponent. This invitation includes data consisting of game parameters and Bitcoin payment information. Upon receiving a request, the other player can reply with either a rejection message to close the connection or an acceptance message with with additional Bitcoin payment information to proceed towards a game. Using the supplied information, each player then independently constructs the identical multisignature Bitcoin address to be used as escrow and a transaction to fund it. Each player signs this transaction, exchanges signatures, and pushes it to the Bitcoin network.

Once the escrow is funded, the players select their choice: rock, paper, or scissors. Their choice is appended to randomly-generated data, and the combined data is hashed. The players then exchange the resulting hashes to commit to their decision without revealing it. After receiving the hash, players exchange the original message containing their choices and the random data. Standard rock-paper-scissors rules are applied to determine the outcome of the game. If the result is not a draw, the loser instantiates a micropayment channel to send the winnings of this game to the victor.

The game process is repeated a number of times according to the game parameters agreed to in the invitation. Additional coins are sent through the micropayment channel to batch multiple game results into a single transaction.

After the entire round is completed and the winning payments have been received, both players create a new transaction to return their deposits from escrow back to themselves. This transaction is signed out of escrow by both players, concluding the RPSPS connection.
