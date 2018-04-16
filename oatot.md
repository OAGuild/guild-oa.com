---
layout: page
title: OATOT mod
---

## Idea

Make betting (with both virtual currency or [BTC][BTC-link]) possible in [OA][OA-link].

## Motivation

Just for fun and to keep the game I love alive.

## Version 0.1

Modified OAX. The mod is currently **only CTF-oriented** (both betting structure and user interface).

*Modified weapons parameters*.<br>
Fast rockets (rocket speed 1000 u/s),
weak RG (damage 80), LG damage is now 7.

*Easy item pickup is enabled*.<br>
"High" items (you don't need to slow down to pick them up while strafing).

*Flag info widgets, new sound on flag drops*.<br>

*Advanced scoreboard*.<br>
New statistics such as K/D ratio, accuracy, damage (taken and given),
average speed, number of flag captures and grabs, favorite weapon
(the one with which player made maximal damage).
It is also possible to configure additional scoreboard design
effects (see client-side Cvars section below).

*New available console commands.*<br>
Stuff you can call by typing `/<command>` in OA game console.

```
 - bet              <horse>[red,blue] <amount> <currency>[BTC,OAC]
 - unbet            <bet_ID>
 - pastBets
 - pastBets         elder
 - betsSummary
 - ready
 - help
 - shareBalance
 - shareBalance     <currency>[BTC,OAC]
```

*Graphical menu to make, discard and edit bets.*

<img src ="/oatot_images/betting_menu.jpg" width="668px" height="432px"/>

*Game stages*

Game process is splitted into the following stages, the only way to switch between them
is to use `ready` command or by finishing the match
in some way.

 - **FORMING_TEAMS**<br>
    Available commands: `pastBets, betsSummary, ready, help, shareBalance`.
    Players are able to switch teams or spec and disconnect. No additional restrictions
    comparing to normal game, but scores (both flags and personal) aren't counted.
    You can't make any bets yet, teams aren't formed.

 - **MAKING_BETS**<br>
    Available commands: `bet, unbet, pastBets, betsSummary, help, shareBalance`.
    Teams are fixed, you can't switch. If someone disconnects, `map_restart` is called.
    You can now make and discard your bets. Still no scores though.
    Next stage will be started in `g_makingBetsTime`.

 - **PLAYING**<br>
    Available commands: `pastBets, betsSummary, help, shareBalance`.
    Betting is finished. Teams are still locked, but the game has started already,
    so score is now counted.

*New Cvars*

**Server-side:**<br>
 - `g_enableBetting`<br>
    1 to enable *all* the betting features, 1 by default.
 - `g_backendAddr`<br>
    The address (IP:port) string of oatot backend.
    This Cvar has the same defaults as backend's `grpc-addr` flag.
 - `g_makingBetsTime`<br>
    The duration of MAKING_BETS in mins, 2 by default.
 - `g_easyItemPickup`<br>
    1 for easy item pickup (high items), 1 by default.
 - `g_scoreboardDefaultSeason`<br>
    Season which will be set as default scoreboard season on clients, 1 by default.
    0 - no season, 1 - winter, 2 - spring, 3 - summer, 4 - autumn.

**Client-side:**<br>
 - `cg_scoreboardEffects`<br>
    0 to disable all additional scoreboard effects, 1 by default.
 - `cg_scoreboardSeason`<br>
    Scoreboard season, `g_scoreboardDefaultSeason` (server-side Cvar) by default.
    0 - no season, 1 - winter, 2 - spring, 3 - summer, 4 - autumn.
    Set to -1 in order to set server defaults again.
    Will be forced updated when default changes on the server.
 - `cg_scoreboardAggressive`<br>
    1 to enable aggressive scoreboard effects. Incompatible with `cg_scoreboardSeason != 0`.
    0 by default.

*How to earn OaCoins?*

 - Every new player is sponsored with 10 OAC for first sign up.
 - Your score after every single match played in oatot mod is transferred to your
    *prize top-up* in case your team won (1 score point is equal to 1 OAC for now).
 - Obviously - by making bets and winning them! :)<br>

*Future solutions*
 - Mining.
 - Make OaCoins visible items on the map so you can collect them while playing.

## For developers

Source code is available on [GitHub](https://github.com/oatot/oatot).
See the README for implementation and internals overview.

## Gallery<br>

<img src ="/oatot_images/shot0000.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0001.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0002.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0003.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0004.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0005.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0006.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0007.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0008.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0009.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0010.jpg" width="668px" height="432px"/>
<img src ="/oatot_images/shot0012.jpg" width="668px" height="432px"/>

[BTC-link]: https://en.wikipedia.org/wiki/Bitcoin
[OA-link]: https://en.wikipedia.org/wiki/OpenArena
