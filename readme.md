# RPSS: Rock-Paper-Scissors Secure

RPSS is a peer-to-peer protocol for playing cryptographically secured games of rock-paper-scissors.

## Abstract

A cryptographically secure implementation of rock-paper-scissors would allow players to compete in a simple game with untrusted partners over an insecure connection.  By operating under a scheme based on Nash equilibrium and leveraging the Bitcoin network, players can stake assets on the outcome of games.  A Nash equilibrium is achieved when the two parties store escrow funds into a multisignature address and refuse to sign the funds back to their sender until after the completion of a successful round of games.  Batching multiple games into a round and using a micropayment channel to iteratively increase payments after each game reduces the number of transactions and corresponding fees.
