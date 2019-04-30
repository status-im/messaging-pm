# Web3 Messaging 3 call

(last call https://hackmd.io/aBkMF2J-Q3iazZyE1tT-yQ?edit)

## Agenda

- Sync
- Swarm PSS
- Validity Labs
- Nym simulation etc
- More projects in space?

## Notes

Oskar:
    - change to Zoom so that we can record and stream to YT
    - let's have sync and updates and then go through questions

Sebastian:
    - let's get a list of the projects in the space

Oskar:
    - brief sync on the changes from the last weeks

Sebastian: maybe intro in one sentence?
Oskar: let's do that
Fateme: researcher from web3. Can help with routing and networking especially. No really much updates on this front.
Jeff: also a researcher in web3. Started going notes on high-level picture on what's being worked on in web3.
Victor: from Swarm Team. Louise (author of PSS) and Vlad (author of Whisper) joined as well.
Sebastian: CTO Validity Labs. We work on Hopper project. Robert is the main dev but ono vacation now. Privacy preserving protocol. Finishing restructuring the implementation in the last two weeks. Had a Gitcoin grant.
Jeff: no one from Panoramic or Nym but they should join in the future. Have kind of mixnet built. 
Oskar: from Status, together with Adam and Dean. Dean and I have been looking on a data sync layer. Started writing a better requirements list. Adam has been documenting the current protocol and we started splitting it up into smaller parts. Data sync layer does not put any requirements on the transport layer so there should be no interface concerns. We will have someone to represent the group on the MLS hackathon. Looking into PSS feeds as a kind of log-based communication (POC).
https://notes.status.im/O7Xgij1GS3uREKNtzs7Dyw 
https://github.com/status-im/specs/ 
https://github.com/status-im/bigbrother-specs/pull/7 

---

Sebastian: still a few things unclear. Incentive mechnism included into swarm, is that already implemented? 
Victor: it's not working yet. Some parts are implemented but it's still pending because of other things needed to be done. Accounting mechanism is done but it's not connected with other parts yet.
Sebastian: you this gradient, a spectrum of Whisper like approach vs recipeint direct way of sending messages. How spamming is prevented when using Whisper like routing?
Victor: incentive mechanism has to take that into account, i.e. passing messages. When luminasity radius is small, you have to pay. Kind of exponential cost must be incorporated.
Sebastian: this means that incentive mechanism will take care of this, right?
Victor: yes
Vlad: in Whisper there is a possiblity of using bloom filters. Every node can receive messages based on bloom filters. This can be used as a spam prevention mechanism as peers will be removed if spamming.
Sebastian: It's exposing what you're interested in.
Vlad: in PSS can send a message and have luminosity radious based on the node hash (address ?). In Whisper, it's a bit different as it leaks topics but it's arbitrary and it's not bound to the address.
Sebastian: any low-level writeups how this is implemented on the lower-level? Package formats etc?
Vlad: in Whisper, it's implemneted but the docs are not created. Documentation is in progress but there is a new guy who is in chard of this.
Sebastian: question was about swarm.
Victor: no proper documentation for that as well. The implementation is in Go and it's fairly readable. PSS itself is pretty easy and we should create the doc already.
Sebastian: would be helpful to understand privacy with regards to metadata.
Victor: an ask for Louise to share the low level tutorials regarding pss and devp2p.
Sebastian: have anyone heard about loki ??? project. It goes in a similar director, have a fork of swarm, has a mechanism to detect good peers with staking mechanism. Using Monero chain to incentivize behaviour. Feels heavy.
Oskar: Andrea can talk more about it as he researched that project (https://discuss.status.im/t/network-incentivisation-log/1173)

---

Oskar: is it clearer in terms of requirements from data sync layer?
Sebastian: let's wait for Jeff writeups before going further with that.
Jeff: data sync layer is dealing much closer with the content of the messages. One design is that data sync layer runs above MLS layer. 
Oskar: it's independent from transport layer.
Jeff: there are consequences but it should be fine. For example, expired messages might be affected and handled properly.
Oskar: how we makes things pluggable?
Jeff: agree with the fact that data sync layer will be independent.
Sebastian: any other projects?
???: Briar
Victor: ???
Oskar: data sync layer required for core functionality of Status but this effort is independent
Sebastian: going into smaller problems like the order of messages and whether it's important or not because in mixnets packets can arrive in different order.
Victor: what are the contexts for data transport?
Jeff: from the app perspective, the packets can be really our of order and that's the reality.
Oskar: double ratchet?
Jeff: it's handled, MLS should handle it.
Oskar: how do you see the mixnet design? 
Victor: no clear idea yet
Jeff: fairly different things, swarm uses broadcast stuff. One model should be polishing broadcast design and when it should be used. It does makes sense to have broadcast layer for certain things. We might have different transport layers and switch between them if necessary. 
Victor: MLS being an extra layer?
Jeff: MLS is different. Not sure if it makes sense to use it for large group. Currently, swarm is a broadcast system. If Status wants swarm to be more modular and switch between different transports???
Oskar: kind of yes. How Hopper and mixnets fit into the swarm design, that's was the question.
Sebastian: privacy guarantees in mixnets vs broadcast scheme comment from Jeff please.
Jeff: broadcast does not quarantee much privacy. You can have a message going through mixnet and then broadcasted through PSS/Whisper which might be better. 
Oskar: Validity Labs has Hopper and there is Nym. What's the first mileston? 
Jeff: sit down with Robert but want to have the same design. They like almost all stuff from Nym.
Oskar: are there other things we can finalize?
Jeff: it should happen quickly.
Fateme: we should finalize stuff from the networking/routing perspective.
Jeff: written much already on the packets format. 
Fateme: but how routing will look like?
Oskar: can we have some requirements, questions we should answer from routing perspective?
Jeff: PKI side is complicated ??? 
Oskar: do you want to quickly talk about group chats? Let's do it offline as Louise can't use audio now. Louise: some resource: https://github.com/nolash/weechat-pss
Victor: there will be a messaging/communication workshop (where ??? when ???)
Sebastian: anybody for New York madness. 10-18th May, ETH NY and stuff
Oskar: Dean might be there. 

Thanks all!

## Zoom notes
```
From Oskar to All panelists: (12:16 PM)
 https://notes.status.im/O7Xgij1GS3uREKNtzs7Dyw https://github.com/status-im/specs/ https://github.com/status-im/bigbrother-specs/pull/7 
From mutedlash to All panelists and attendees: (12:28 PM)
 the question is a bout spec no? so the tutorials will show how to use also how to use the p2p layer but for something decriptive I guess we dont have that an nad *and 
From mutedlash to All panelists and attendees: (12:29 PM)
 actually the group chat prototype thing I'm writing is in python <3 again : 
From Oskar to All panelists: (12:30 PM)
 https://discuss.status.im/t/network-incentivisation-log/1173/2 
From tron to All panelists: (12:34 PM)
 You can actually mount devp2p (TCP stream assumption) 
From mutedlash to All panelists and attendees: (12:41 PM)
 swarm is not using whisper I don't understand 
From Me to All panelists and attendees: (12:42 PM)
 Ok so PSS is a broadcast-like scheme that replaces whisper.  :) 
From Oskar to All panelists: (12:42 PM)
 yeah 
From mutedlash to All panelists and attendees: (12:43 PM)
 yeah I don't think we've really discussed this much in the context of pss/swarm ... 
From Oskar to All panelists: (12:43 PM)
 https://our.status.im/whisper-pss-comparison/ fyi Jeff 
From Sebastian to All panelists and attendees: (12:44 PM)
 You have good resources quickly available Oskar ;) 
From mutedlash to All panelists and attendees: (12:48 PM)
 hm well not so easy on chat yeah my audio doesnt work so http://github.com/nolash/weechat-pss 
From Oskar to All panelists: (12:48 PM)
 Sebastian :P 
From Oskar to All panelists: (12:49 PM)
 https://www.zotero.org/groups/2306124/secure_messaging? we have this too if you want to join 
From mutedlash to All panelists and attendees: (12:49 PM)
 yeah sorry about this audio thing thanks all I will make sure I have audio next time
 ```
