# RPSS: Rock-Paper-Scissors Secure

RPSS is a peer-to-peer protocol for playing cryptographically secured games of rock-paper-scissors.

## Abstract

A cryptographically secure implementation of rock-paper-scissors would allow players to compete in a simple game with untrusted partners over an insecure connection.  By operating under a scheme based on Nash equilibrium and leveraging the Bitcoin network, players can stake assets on the outcome of games.  A Nash equilibrium is achieved when the two parties store escrow funds into a multisignature address and refuse to sign the funds back to their sender until after the completion of a successful round of games.  Batching multiple games into a round and using a micropayment channel to iteratively increase payments after each game reduces the number of transactions and corresponding fees.

## Introduction

Online gaming has come to rely on trusted third parties.  These trusted authorities tend to have upkeep costs that result in fees charged the the players.  The servers of trusted authorities become prime targets for malicious attackers.  Large amounts of funds are stored on these servers and must be protected by the authorities, presenting a counterparty risk to players.  RPSS allows players to hold funds in their own full control for the majority of their gaming experience.

Trustless wagering systems exist, but most have been implemented inefficiently as coins layered on top of the Bitcoin protocol.  RPSS functions more efficiently with a direct communication channel between players and basic use of the Bitcoin block chain.  Players do not need to trade their bitcoins for another coin, and the protocol can be extended for similar assets.
