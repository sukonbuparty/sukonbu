+++
date = '2026-02-20T22:18:16+03:00'
draft = false
title = 'Discord Alternatives'
+++

Continuation of last post.

Ever since the announcement of Discord's age verification, people have been looking for alternatives. I've tried out a few and in this post tell you my experience of them.

## Matrix

Matrix is one of the first replacements that comes to mind. It is not a platform by itself but more so a protocol for federated servers to communicate with eachother (though it uses JSON so far).

Matrix has some popular clients, including Element, nheko, Thunderbird (yes, the mail client!), Neochat, Cinny, Fluffychat and so on. I've personally tried all of the stated ones on desktop, and the one I'll keep using seems to be nheko. Element is too clunky, it works as an Electron application so it just sucks system resources even if it's doing nothing. nheko and Thunderbird doesn't use Electron, but Thunderbird lacks quite a bit in terms of features, same with nheko but the only major lack of feature is just voice calls. Cinny and Fluffychat were both very clunky on my browser so they have been eliminated from my choices.

The situation with so many Matrix clients all feature lacking is interesting, when you and your friends use separate clients it can cause issues such as Element and Fluffychat users can create polls where nheko nor Thunderbird can see them, by default Thunderbird can't even show image previews. Both of them also lack the call feature. They can be made up for by using Jitsi or Mumble, or just using the default Element client for calls.

In terms of homeservers, there are some popular homeservers out there. The most popular one is matrix.org but you can usually communicate with other servers or even create your own. Element allows you to rent servers from them, though it is also possible to host it yourself as long as you own a domain name. You can even disable external server access if you don't want to be a part of the federated network. All of this is able to run under a docker container, which makes deployments as easy as copy pasting a docker compose file.

## IRC

IRC has existed for a long time, even though most people have forgotten about it, it always had a persistent userbase on multiple servers, even so much for the Matrix server hosts implementing IRC bridges to combine the two communities together (although it had it's own drama but we'll not get into that)

I have been using IRC for some time too, I've been using Adiirc and now Thunderbird to connect to IRC servers for a long time. One of the biggest issues people encounter when using IRC for the first time is the lack of message history. Unlike Matrix or Discord, IRC keeps no message history, when you join a server you only get messages as long as you are connected, once you disconnect you are in the blind. A solution to this was to run IRC bouncers on 7/24 machines, that would record all messages and you could configure your client to fetch the messages whenever you wanted, but this required some not so easy configuration and client support.

With the "release" of ircv3, there is a new feature made to fix this (if you consider it to be an issue or not is up to you).

The IRC servers are able to store messages and send them to the clients whenever they want it. This even works for DM messages (although usually requires you to ident so you can't spoof your nick) and as long as you have a compatible client and server, it seems to work flawlessly. I've been using the client Halloy in a server hosted by a friend (using Ergochat as server) for a couple of days, and if you are willing to let go of some conveniences, i think it is definitely worth a shot. It also seems to be easier to configure than Matrix, but don't take my word on that.

The IRC servers are able to store messages and send them to the clients whenever they want it. This even works for DM messages (although usually requires you to ident so you can't spoof your nick) and as long as you have a compatible client and server, it seems to work flawlessly. I've been using the client Halloy in a server hosted by a friend (using Ergochat as server) for a couple of days, and if you are willing to let go of some conveniences, i think it is definitely worth a shot. It also seems to be easier to configure than Matrix, but don't take my word on that, take theirs:

> ```text
> msg: it's been very fun to configure  
> msg: I ran the thing, it came with message history held in ram for as long as a week as the default  
> msg: which is plenty for a lot of configs but I'm used to a discord like setup  
> msg: so I set up the permanent store option which requires hooking up mariadb, which is fine, I had an install of that lying around anyhow  
> msg: another part was getting a TLS certificate, which you can do by letting a web server with let's encrypt certbot do it for you  
> msg: other than that, the config is just one yaml file, everything is explained in the comments, it's so simple and great. doesn't feel that much more complicated than setting up a discord server but way more powerful
> msg: also, you can mention the ObsidianIRC client which is a (...) Discord clone using the cutting edge ircv3 features
> ```

Well, you heard them. I just tried out ObsidianIRC in the process of writing this edit, and I have to say it does a lot more to be like Discord that Revoult does (subtle foreshadowing). While it is not just a drop-in replacement, it may help lower the learning curve ever so slightly if you're looking to move a friend group or similar over to IRC. It has features such as being able to delete messages, set profile pictures, see who is currently typing (which are all revolutionary for IRC). The only issue is that it runs on another port than your regular IRC server does. Do with that as you wish.

## Revoult 

It sucks. It is trying to be a Discord clone but their mobile client is literally a webview window with their website open. The features are sketchy, works half the time. Would not recommend.

Writer: Sukonbu