# 

## Agenda

note taker

1. Brief updates teams, since last month and next steps. Introduction with why here and hoping to get out of it.

2. Brainstorming and go over requirements https://github.com/w3f/messaging

3. Suggested timelines and milestones
a) How much is in phases vs parallel efforts?
b) More precise problem statements / research questions that we agree on

Specific pieces:
- data sync layer
- packet format
- incentive layer
  - paying for each message and cover traffic issues
- relay selection / discovery problem
- PKI
- light client
- noise protocol for handshake setup
- also see libp2p issue https://github.com/libp2p/libp2p/issues/71
- Barry's ideas re rate limit for privacy guarantees and limit network traffic, and pay nodes rewards
- e2e a la mls
  - issues re decentralization, who is on this effort?
  - https://mailarchive.ietf.org/arch/msg/mls/oSArWtEqBzF1s5BpXGX11jaZrFI
- libp2p semi-generic issues
  - nat traversal
  - spec

ethcc workshop raw notes: https://notes.status.im/Cy-k3yqKQHa6bR5Emg0Cog#

4. Misc and next steps
- also naming: whisper bad name
- bi-weekly?
- zoom recording a la eth2

## Notes

### Web3 Bi-Weekly 26th March, 2019

Oskar:
    - Goal is messaging for web3, also work on the mixnets, data sync and so on.
    - Let's give brief update since the last call, go through requirements and do some brainstorming.

Jeff:
    - working for web3 foundation
    - working on mixnet related stuff

Robert:
    - working at validity labs
    - implementing messaging protocol called Hopper

Sebastian:
    - validity labs
    - Whisper is not catering for all needs so working on a new solution

Adam:
    - working at Status
    - working on status-go and Whisper as well as seperate client and documenting Status protocol

Dustin:
    - Nimbus team at Status
    - how interaction between the Status and Ethereum through implementation gonna look liek

Fatemah:
    - working on web3
    - PhD in related stuff, research position

Jacek:
    - Status, researcher

Jarrad:
    - Status
    - finding a better solution for Whisper
    - want to be involved in mixnets

Oskar:
    - Status
    - working on data sync
    - looking at other data sync approaches rather than diving deeper into the first proposal
    - documenting the current Status protocol

Oskar:
    - what changed in the last month from Validity Labs and web3 Foundation

Jeff:
    - more push for MLS stuff and how to decentralize it
    - PKI stuff (no impact in the short term)
    - spec for packet format and stuff in the near future

Robert:
    - working on stable version of Hopper
    - redesigining payment scheme allowing ...?

Sebastian:
    - showing demo of Hopper at ...?
    - lacking libraries and stuff on top of that for easy demo
    - make Hopper scalable and stable

Harry:
    - quick update on MLS
    - MLS new IETF standard building a messaging protocol having the same feature set like Signal (DH, double ratchet) but scalable
    - desire to replace XMPP federation
    - topics: identification by keys, concurrency
    - more people/servers talking to each other, messages can get dropped, how to scale it?
    - no joint view of a distributed system
    - no huge decisions yet
    - mixnet build is very classic for now

Jeff:
    - keys issue which might not be a big deal
    - headers descryption that is fine
    - synchronization is a worrying part in a case of large user base
        - Harry: this is part of the concurrency issue

Harry:
    - PhD student working on a formal verification of cryptography but no scalability or privacy
    - e.g. group creator might be easy to detect now
    - should be possible to verify security properties in case of a group split
    - formal verification of distributed systems not possible really yet

Jeff:
    - concurrency, more precisely tree merging is a problem

Oskar:
    - not entirely clear on federation topic

Jeff:
    - more on site of delivery side of things???

Harry:
    - are there any requirements to change the cryptography to support multiple authentication services?
    - federation topic more seriously to have a separate spec maybe
    - in MLS none of the members are malicious
        - might not be a great assumption in p2p
    - support for group of sizes up to 50k maybe
    - more adverserial and privacy conditions to consider
    - 1-1 comm gives the same properties like Signal but not exactly Signal protocol

Robert:
    - MLS agnostic to delivery method?
        - Harry: confirmed

Jeff:
    - what happens when we have concurrent updates?

Oskar:
    - let's move on form MLS
    - what changed/evolved in terms of mixnet layer since the last call
    - light mode has strong security properties to think about during the design rather than after

Jeff:
    - light mode needs some assumption like recent communication between parties happened

Robert:
    - distinguish between light vs regular nodes probably is required
    - rely nodes

Oskar:
    - no technical solution now but being on the same page
    - as a mobile phone you should be able to select a rely node

Sebastian:
    - missing in academic discussion: formal definition of decentralization and incentivization
    - who maintains PKIs -- how ensure they are set-up in decentralized way?
    - without that a lot of information can be leaked

Jeff:
    - two approaches: TOR pretend they ignore the problem but community watches what's going on (human driven) vs (the first one that ignores it completely)
    - panoramic ...?
    - fundamental problem: sending messages which taking different paths, there is possiblity I select enough bad paths for the adeversary to figure out stuff
    - use all techniques together
    - have a community to look if there are no suspicious behaviour
    - loopix has features to minimize active attacks

Sebastian:
    - what about passive adversaries

Jeff:
    - no really a good generic solution

Oskar:
    - any other requirements/ideas?

Robert:
    - latency of 5 seconds is too much; 2 seconds would be fine

Oskar:
    - what is the next resonable timeline?
    - data sync is the most immediate milestone for Status
    - other things to work on parallel vs step-by-step

Jeff:
    - will send an email to ???

Robert:
    - Hopper: the next goal is to save reordering issue, improve docs, give better access to the project
    - have sender-reciver ???

Oskar:
    - split spec to work in parallel
    - e.g. PKI is hard to maybe move it for later
    - specific phases should be defined

Robert:
    - Phase 0: stable delivery method so that we can test the sync layer

Oskar:
    - that makes sense

Robert:
    - would be great to have a dummy delivery method to test the data sync layer
    - have a GH doc with the current data sync layer progress and code (interfaces)

Oskar:
    - will send a link with early PoC
    - will share again when it is more mature

Robert:
    - dummy delivery protocol + data sync layer we can replace the dummy layer with actual mixnet layer
    - in meanwhile I can do the opposite

Oskar:
    - more concrete regarding the data sync layer will be presented before the next call
    - research log: https://discuss.status.im/t/data-sync-research-log/1100
    - papers: https://www.zotero.org/groups/2306124/secure_messaging

Harry:
    - don't get the federation thing kicked out
    - no big mixnet redesign until April
    - might need more requirements first
    - how manny messages are delivered within a min or hour?

Oskar:
    - what is missing from the requirements?
        - Harry: how manny messages are delivered within a min or hour? within the system

Jacek:
    - also consider machine-machine communication
    - this is dangerous becahse machine-to-machine might use up the whole available capacity

Robert/Jeff:
    - also have a use case for machine-to-machine
    - machine-to-machine comm: evaluate privacy concerns

Oskar:
    - should we do live streaming?

Jeff/Robert:
    - when we have a better structure of the meeting :D

Oskar:
    - next call in two weeks
