# Web3 messaging call 4

## Agenda

1. Sync since last time from teams

2. Nym numbers?

3. Layers https://hackmd.io/aBkMF2J-Q3iazZyE1tT-yQ?edit

(4. Console client / wee chat stuff)

## Notes

Jeff: Layering document main thing, realized the amount of knowledge was lacking for higher level layers. Will try writing a better document for an incentivization strategy.

Viktor: Luis has done lots of work to write up PSS and Feeds group chat.

Oskar: Been working on MVDS in go, and working on playing around with it in the console client. Some things to look in more carefully, dealing with mostly offline devices in large group chats. Looking at bloom fliters, to see if its needed in a minimal version.

https://notes.status.im/I3SxZJpZTvuWjw8rN8MdTQ

Harry: The simulator works, trying to get basic graphs by next week. How many per time tick are we expecting to be successfuly deliveried? 

*Whats the number of users, and what's the number of messages? (user population & rate of sending)*

Lots of nodes are inefficient when mixing.

Jarrad: Realisitically there will be a small set of nodes that are participating in the mixnet.

Harry: When too many nodes the traffic is too thin for the mixnet.

Jeff: We are still suggesting libp2p for transport. Most of the stuff is about future concerns. Mixnet breaksdown into we need some form of PKI, mixing thing and cover traffic. Do we store nodes as accounts on-chain? We should enforce message delay deterministically. For cover traffic everyone wants to take Anias ideas.

Harry: Not sure whether drop messages are necessary. MLS room concept is purely cryptographic.

Jeff: writing up something on packet format
