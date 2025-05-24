---
classification: public
---

# Furcadia Client-to-Server Commands
## Overview
The following is a list of commands accepted by the server. The commands are described as they are delivered to the server, rather than how they are typed out in the client.

For example:
* `` `join `` is something you type in the client to join someone, and since it's a direct client-to-server command, it will be written down as `join` in the list (i.e., no prefix)
* ` cookies-reject ` is something you *say* in-game to reject all cookies, and since it is a said command, it will be written down as `"cookies-reject` in this list (i.e., with the `"` prefix).

You can trigger any command in this list by prefixing it with the <code>`</code> in the client text box, and yes - you say "say" things by typing:
```
`"things go here
```
...it's just kinda pointless...

## Command Sections
* [Cookies](#cookies)
* [Communication](#communication)
* [Channels - Broadcast Channels](#channels---broadcast-channels)
* [Channels - Chat Channels](#channels---chat-channels)
* [Navigation](#navigation)
* [Character](#character)
* [Information](#information)
* [Dream Control](#dream-control)
* [Digos - General](#digos---general)
* [Digos - Species](#digos---species)
* [Digos - Magic](#digos---magic)
* [Digos - Roses](#digos---roses)
* [Digos - Gifts](#digos---gifts)
* [Digos - Description Tags](#digos---description-tags-desctags)
* [Digos - Secure Trade](#digos---secure-trade)
* [Server & Session](#server--session)
* [Beekin Commands](#beekin-commands)

---------------------------------------------------------------------------------------------------

## Cookies
| Command                            | Description                                               |
| :--------------------------------- | --------------------------------------------------------- |
| [buy-cookie](#buy-cookie)          | Buy a freshly baked in-game cookie (using DragonScales)   |
| ["cookies-accept](#cookies-accept) | Accept cookies from all furres                            |
| ["cookies-reject](#cookies-reject) | Reject cookies from all furres                            |
| ["eat-cookie](#eat-cookie)         | Eat an active (description) cookie                        |
| ["give-cookie](#give-cookie)       | Give an active (description) cookie to a furre            |
| ["make-cookie](#make-cookie)       | Give an inactive (baking) cookie to a furre               |
| ["make-secret](#make-secret)       | Secretly give an inactive (baking) cookie to a furre      |
| ["munch-cookie](#munch-cookie)     | Loudly eat an active (description) cookie - alerts others |
| ["secret-cookie](#secret-cookie)   | Secretly give an active (description) cookie to a furre   |

---------------------------------------------------------------------------------------------------

### buy-cookie
Buy a freshly baked in-game cookie (using DragonScales)

**Syntax**
```
buy-cookie
```

**Comments**
1. Displays a confirmation dialog prior to purchase (even if you lack funds).

**Output: Confirmation Dialog**
```
]#601 3 You get a few free Cookies each day.  But you can get extras here if you want!  This will exchange 5 Copper Dragonscales for 1 Freshly Baked Cookie.  (No refunds available.)  Click "Ok" to get the Cookie.  Click "Cancel" to keep your DragonScales.
```
* This dialog appears after executing the command

**Output: Insufficient Funds**
```
#TODO
```

**Output: Cookie Purchase Confirmation**
```
#TODO
```

-------------------------------------------------------------------------------

### "cookies-accept
Accept cookies from all furres. You will start receiving cookies from everyone.

**Syntax**
```
"cookies-accept
"cookiesaccept
```

**Comments**
1. Use ["cookies-reject](#cookies-reject) to reject cookies from all furres.

**Output: Confirmation**
```
(<font color='success'>You are now accepting cookies.</font>
```

-------------------------------------------------------------------------------

### "cookies-off
Disable the ability for everybody to give cookies within the dream

**Syntax**
```
"cookies-off
"cookiesoff
```

**Comments**
1. Use ["cookies-on](#cookies-on) to enable cookies.

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "cookies-on
Enable the ability for everybody to give cookies within the dream

**Syntax**
```
"cookies-on
"cookieson
```

**Comments**
1. Use ["cookies-off](#cookies-off) to disable cookies.

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "cookies-reject
Reject cookies from all furres. You will not receive cookies from anyone.

**Syntax**
```
"cookies-reject
"cookiesreject
```

**Comments**
1. Use ["cookies-accept](#cookies-accept) to accept cookies from all furres.

**Output: Confirmation**
```
(<font color='success'>You are now rejecting cookies.</font>
```

-------------------------------------------------------------------------------

### "eat-cookie
Eat an active (description) cookie. 

**Syntax**
```
"eat-cookie
"eatcookie
```

**Output: Confirmation**
```
#TODO
```

**Output: No Cookies**
```
(<font color='error'>You have no cookies left!</font>
```

-------------------------------------------------------------------------------

### "give-cookie
Give an active (description) cookie to a furre, with an optional message

**Syntax**
```
"give-cookie {name}
"givecookie {name}
```

**Usage Examples**
```
"give-cookie artex
"givecookie artex 
```

**Output: Confirmation**
```
#TODO
```

**Output: No Cookies**
```
(<font color='error'>You do not have any more cookies to give away right now. Get more here!</font>
```

**Output: Ambiguous Name**
```
(<font color='error'>More than one furre's name begins that way in this dream.</font>
```

**Output: Public Announcement**
```
(<img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> <name shortname='cpu'>CPU</name> just gave <name shortname='artex'>Artex</name> a cookie.
```

**Output: Cookies Still Baking**
```
#TODO
```

**Output: Cookies Are Ready**
```
(<font color='success'><img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> Your cookies are ready.  http://furcadia.com/cookies/ for more info!</font>
```

-------------------------------------------------------------------------------

### "make-cookie
Give an inactive (baking) cookie to a furre, with an optional message

**Syntax**
```
"make-cookie {name}
"makecookie {name}
```

**Usage Examples**
```
"make-cookie artex
"makecookie artex
```

**Output: Cannot Give Cookies To Yourself**
```
(<img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> You cannot give cookies to yourself.
```
* Triggered when trying to `make-cookie` on another character in the same account.

**Output: Ambiguous Name**
```
(<font color='error'>More than one furre's name begins that way in this dream.</font>
```

**Output: Public Announcement**
```
(<img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> <name shortname='cpu'>CPU</name> just gave <name shortname='artex'>Artex</name> a cookie.
```

**Output: Cookies Still Baking**
```
#TODO
```

**Output: Cookies Are Ready**
```
(<font color='success'><img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> Your cookies are ready.  http://furcadia.com/cookies/ for more info!</font>
```

-------------------------------------------------------------------------------

### "make-secret
Secretly give an inactive (baking) cookie to a furre

**Syntax**
```
"make-secret {name}
"makesecret {name}
```

**Usage Examples**
```
"make-secret artex
"makesecret artex
```

**Output: Confirmation**
```
(<img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> You gave <name shortname='albertquirky'>Albert|Quirky</name> a cookie
```

**Output: Cannot Give Cookies To Yourself**
```
(<img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> You cannot give cookies to yourself.
```
* Triggered when trying to use `make-secret` on another character in the same account.

-------------------------------------------------------------------------------

### "munch-cookie
#deprecated 
Loudly eat an active (description) cookie - alerts others

**Syntax**
```
"munch-cookie
"munchcookie
```

**Comments**
1. This command is OBSOLETE and DOES NOT work anymore
2. Using this command will say it out loud

-------------------------------------------------------------------------------

### "secret-cookie
Secretly give an active (description) cookie to a furre

**Syntax**
```
"secret-cookie {name}
"secretcookie {name}
```

**Usage Examples**
```
"secret-cookie artex
"secretcookie artex
```

**Output: Confirmation**
```
(<img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> You gave <name shortname='albertquirky'>Albert|Quirky</name> a cookie
```

**Output: Cannot Give Cookies To Yourself**
```
(<img src='fsh://system.fsh:90' alt='@cookie' /><channel name='@cookie' /> You cannot give cookies to yourself.
```
* Triggered when trying to `secret-cookie` on another character in the same account.


---------------------------------------------------------------------------------------------------

## Communication
| Command                      | Description                                                                                                      |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| [" (say)](#say)              | Say something to the people within your range of sight in the dream                                              |
| [- (shout)](#--shout)        | Shout something to all people in the dream who have the shout channel on, locally activating it if necessary<br> |
| [: (emote)](#emote)          | Emote something to all people within your range of sight                                                         |
| [wh](#wh)                    | Whisper something to a specific person                                                                           |
| ["roll](#roll)               | Roll dice publicly                                                                                               |
| ["ROLL](#roll-uppercase)     | Roll dice publicly (with separate die results)                                                                   |
| ["whisperson](#whisperson)   | Allow incoming whispers                                                                                          |
| ["whispersoff](#whispersoff) | Disallow incoming whispers                                                                                       |

---------------------------------------------------------------------------------------------------

### `"` (say)
Say something to the people within your range of sight

**Syntax**
```
"Rawr!.. and other such stuff...
```

**Output: Confirmation**
```
]-#Aw&&&&&&&&&&###�#
(<font color='myspeech'>You say, "Rawr!.. and other such stuff..."</font>
```
* The `]-` instruction displays your specitag prior to the text.

**Output: Incoming Say**
```
]-#Aw%5K(J;,;;;#;$�#
(<name shortname='artex'>Artex</name>: Bah. It's 4am already :\
```
* Triggered when somebody else says something using this command.
* The `]-` instruction displays your specitag prior to the text.

-------------------------------------------------------------------------------

### `-` (shout)
Shout the text to all people in the dream who have the shout channel on, locally activating it if necessary

**Syntax**
```
-
-{text}
```
* The first option turns the Shout channel on or off
* The second option turns the Shout channel on if needed, and sends a message there

**Usage Example**
```
-
-Rawr!.. and other stuff...
```

**Comments**
1. If no message is specified, the command enables/disables the Shouts channel.
2. If a message is provided, the Shouts channel is enabled, and the message is shouted out into it.

**Output: Confirmation**
```
(<font color='shout'>You shout, "Rawr"</font>
```
* This message DOES NOT have a specitag prefix - this is not a documentation error!

**Output: Incoming Shout**
```
]-#Aw%5K(J;,;;;#;$�#
(<font color='shout'>{S} <name shortname='artex'>Artex</name> shouts: rawr</font>
```
* Triggered when somebody else shouts something using this command.
* The `]-` instruction displays your specitag prior to the text.

**Output: Shouts On**
```
(<font color='success'>Shouts on: You will now hear shouts even when this map is crowded. Type - to toggle them back off.</font>
```
* Triggered when enabled via `-`, or BEFORE a shout is sent if the Shout channel was off.

**Output: Shouts Off**
```
(<font color='success'>Shouts off: You'll only hear shouts when there aren't many people here.</font>
```

-------------------------------------------------------------------------------

### `:` (emote)
Emote text (action) to all people within your range of sight

**Syntax**
```
:{text}
```

**Usage Example**
```
:does something silly
```

**Output: Confirmation**
```
]-#Aw&&&&&&&&&&###�#
(<font color='emote'><name shortname='cpu'>CPU</name> rawr</font>
```
* The `]-` instruction displays your specitag prior to the text.

**Output: Incoming Emote**
```
]-#Aw8807C<<(<(1&$�#
(<font color='emote'><name shortname='albertquirky'>Albert|Quirky</name> nods solemnly</font>
```
* Triggered when somebody else posts something using this command.
* The `]-` instruction displays your specitag prior to the text.

-------------------------------------------------------------------------------

### wh
Whisper something to a specific person

**Syntax**
```
wh {name} {message}
wh %{exactname} {message}
wh %%{exactname} {message}
```

**Usage Examples**
```
wh artex Hey there! This can be sent to "Artex" or "Artex Panther"
wh %artex Hey there! This is sent precisely to "artex"
wh %%artex Hey there! And if you're offline, the whisper will be stored.
```

**Comments**
1. Without a prefix, the whisper uses fuzzy name matching (e.g., "art" -> "artex")
2. With a `%` prefix, the whisper uses exact name matching
	* This prefix was first introduced in the **Squirrel Update**
3. With a `%%` prefix, the whisper will be stored on the server and be delivered to the furre next time they come online. (aka: "offline whispers")

**Output: Confirmation**
```
]-#Aw&&&&&&&&&&###�#
(<font color='whisper'>[ You whisper "Rawr and stuff!" to <name shortname='artex' forced src='whisper-to'>Artex</name>. ]</font>
```
* The `]-` instruction displays your specitag prior to the text.

**Output: Not Online - Fuzzy Match**
```
(<font color='error'>Sorry, there are no furres around right now with a name starting with rawr!  -- Beekin the Help Dragon</font>
```

**Output: Not Online - Exact Name**
```
(<font color='error'>Sorry, there's no furre around right now with an exact name rawr! To find similar names, try typing the name without the '%' at the beginning of the name. -- Beekin the Help Dragon</font>
```

**Output: Offline Whisper**
```
(<font color='whisper'>[ You whisper "Rawr! (Offline message sent Apr 11, 07:46pm FST)<auto><offline>" to <name shortname='rawr' forced src='whisper-to'>rawr</name>. ]</font>
(<font color='success'>Your whisper to 'rawr' was stored and will be delivered when the furre comes online.</font>
```

**Output: Incoming Offline Whisper**
```
#TODO
```

-------------------------------------------------------------------------------

### "roll
Roll dice publicly

**Syntax**
```
"roll {n}d{sides}{text}
```

**Usage Examples**
```
"roll 2d10
"roll 2d10literally anything here
```

**Output: Confirmation**
```
(<font color='roll'><img src='fsh://system.fsh:101' alt='@roll' /><channel name='@roll' /> <name shortname='cpu'>CPU</name> rolls 2d10literally anything here & gets 19.</font>
```

-------------------------------------------------------------------------------

### "ROLL uppercase
Roll dice publicly (with  separate die results)

**Syntax**
```
"ROLL {n}d{sides}
"ROLL {n}d{sides}{text}
```

**Usage Examples**
```
"ROLL 2d10
"ROLL 3d10stuff here
```

**Output: Confirmation**
```
(<font color='roll'><img src='fsh://system.fsh:101' alt='@roll' /><channel name='@roll' /> <name shortname='cpu'>CPU</name> rolls 2d10: (10) (7) = 17.</font>
```

**Output: Confirmation With Text**
```
(<font color='roll'><img src='fsh://system.fsh:101' alt='@roll' /><channel name='@roll' /> <name shortname='cpu'>CPU</name> rolls 3d10stuff here: (2) (1) (8) = 11.</font>
```

-------------------------------------------------------------------------------

### "whisperson
Allow incoming whispers

**Syntax**
```
"whisperson
```

**Comments**
1. Use ["whispersoff](#whispersoff) to block incoming whispers
2. This command requires Silver Sponsorship on the character, or Gold Sponsorship on the account.

**Output: Confirmation**
```
(<font color='success'>Whispers on. Everyone can whisper to you again.</font>
```

**Output: No Sponsorship**
```
#TODO
```

-------------------------------------------------------------------------------

### "whispersoff
Disallow incoming whispers from anyone

**Syntax**
```
"whispersoff
```

**Comments**
1. Use ["whisperson](#whisperson) to allow incoming whispers again and counteract this command
2. This command requires Silver Sponsorship on the character, or Gold Sponsorship on the account.

**Output: Confirmation**
```
(<font color='warning'>Whispers off. Nobody can whisper to you now.</font>
```

**Output: No Sponsorship**
```
#TODO
```

**Output: Offline Whispers Warning**
```
(<font color='warning'>Your whispers are currently switched off. <name shortname='rawr'>rawr</name> will not be able to respond to you in whispers.</font>
```
* Triggered when you send someone an offline whisper while in `whispersoff` mode.


---------------------------------------------------------------------------------------------------

## Channels - Broadcast Channels
| Command                 | Description                                                                 |
| :---------------------- | --------------------------------------------------------------------------- |
| ["=talz](#talz)         | Toggle the Talzhemir channel                                                |
| ["=fel](#fel)           | Toggle the Felorin channel                                                  |
| ["=emmie](#emmie)       | Toggle the Emerald Flame channel                                            |
| ["=sd](#sd)             | Toggle the Second Dreaming channel                                          |
| ["=news](#news)         | Toggle the News channel                                                     |
| ["=event](#event)       | Toggle the Events channel                                                   |
| ["=fun](#fun)           | Toggle the Fun channel                                                      |
| ["=spice](#spice)       | Toggle the Spice channel (M16+, A18+ and AO dreams only)                    |
| ["={group}](#group)     | Toggle the broadcast channel for a registered group, or broadcast a message |

**Reference**
* [Channel Commands](https://cms.furcadia.com/help/commands/keycommands/generalcommands/channelcommands)

---------------------------------------------------------------------------------------------------

### "=talz
Toggle the Talzhemir channel

**Syntax**
```
"=talz
```

**Output: Enabled**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000016.png' alt='=talz' /><channel name='=talz' /> Talz channel on. Mrrelcome!</font>
]n$=#'talz�v|#爟H
```

**Output: Disabled**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000016.png' alt='=talz' /><channel name='=talz' /> Talz channel off. See you later!</font>
]n$=#'talzav|#爟H
```

-------------------------------------------------------------------------------

### "=fel
Toggle the Felorin channel

**Syntax**
```
"=fel
```

**Output: Enabled**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000014.png' alt='=fel' /><channel name='=fel' /> Fel channel on - all Felorin, all the time.</font>
]n$=#&fel�v|#刟H
```

**Output: Disabled**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000014.png' alt='=fel' /><channel name='=fel' /> Fel channel off - reality will resume in five minutes.</font>
]n$=#&felav|#刟H
```

-------------------------------------------------------------------------------

### "=emmie
Toggle the Emerald Flame channel

**Syntax**
```
"=emmie
```

**Output: Enabled**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000015.png' alt='=emmie' /><channel name='=emmie' /> Emmie channel on. Hi! #SA</font>
]n$=#(emmie�v|#戟H
```

**Output: Disabled**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000015.png' alt='=emmie' /><channel name='=emmie' /> Emmie channel off. Bye! #SA</font>
]n$=#(emmieav|#戟H
```

-------------------------------------------------------------------------------

### "=sd
Toggle the Second Dreaming channel

**Syntax**
```
"=sd
```

**Output: Enabled**
```
#TODO
```

**Output: Disabled**
```
#TODO
```

**Output: No Access**
```
(<font color='error'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='=sd' /><channel name='=sd' /> Sorry, you don't have access to the Sd channel. Please contact the group Rah to obtain access.</font>
```

-------------------------------------------------------------------------------

### "=news
Toggle the News channel

**Syntax**
```
"=news
```

**Output: Enabled**
```
(<font color='success'><img src='fsh://system.fsh:82' alt='=news' /><channel name='=news' /> News channel on.</font>
]n$=#'Newsݕ�ሟH
```

**Output: Disabled**
```
(<font color='success'><img src='fsh://system.fsh:82' alt='=news' /><channel name='=news' /> News channel off.</font>
]n$=#'News]��ሟH
```

-------------------------------------------------------------------------------

### "=event
Toggle the Events channel

**Syntax**
```
"=event
```

**Output: Enabled**
```
(<font color='success'><img src='fsh://system.fsh:83' alt='=event' /><channel name='=event' /> Event channel on.</font>
]n$=#(Eventݕ�∟H
```

**Output: Disabled**
```
(<font color='success'><img src='fsh://system.fsh:83' alt='=event' /><channel name='=event' /> Event channel off.</font>
]n$=#(Event]��∟H
```

-------------------------------------------------------------------------------

### "=fun
Toggle the Fun channel

**Syntax**
```
"=fun
```

**Output: Enabled**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000150.png' alt='=fun' /><channel name='=fun' /> Fun channel on.</font>
]n$=#&fun�v|#���H
```

**Output: Disabled**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000150.png' alt='=fun' /><channel name='=fun' /> Fun channel off.</font>
]n$=#&funVv|#���H
```

-------------------------------------------------------------------------------

### "=spice
Toggle the Spice channel (M16+, A18+ and AO dreams only)

**Syntax**
```
"=spice
```

**Output: Enabled**
```
(<font color='success'><img src='fsh://system.fsh:102' alt='=spice' /><channel name='=spice' /> Spice channel on.</font>
]n$=#(SpiceI��䈟H
```

**Output: Disabled**
```
(<font color='success'><img src='fsh://system.fsh:102' alt='=spice' /><channel name='=spice' /> Spice channel off.</font>
]n$=#(Spice���䈟H
```

-------------------------------------------------------------------------------

### "={group}
Toggle the broadcast channel for a registered group, or broadcast a message

**Syntax**
```
"={group}
"={group} {message}
```

**Usage Examples**
```
"=dragons
"=dragons Rawr there!
```

**Comments**
1. Attempts to enable a group one has no access to will produce no response from the server!

**Output: Enabled**
```
#TODO
```

**Output: Disabled**
```
#TODO
```


---------------------------------------------------------------------------------------------------

## Channels - Chat Channels
| Command                   | Description                                                       |
| :------------------------ | ----------------------------------------------------------------- |
| [chat](#chat)             | Send a message to the current chat channel                        |
| [clearnews](#clearnews)   | Clear all messages in the current chat channel                    |
| [jg](#jg)                 | Join a chat channel                                               |
| [kick](#kick)             | Kick a furre from a chat channel                                  |
| [leave](#leave)           | Leave current chat channel                                        |
| [listf](#listf)           | List furres currently on the chat channel                         |
| [listgroups](#listgroups) | List all available chat channels                                  |
| [news](#news)             | Add a message to be displayed when a furre joins the chat channel |
| [tellgroup](#tellgroup)   | Send a message to all members of a registered group               |

**Reference**
* [Channel Commands](https://cms.furcadia.com/help/commands/keycommands/generalcommands/channelcommands)

---------------------------------------------------------------------------------------------------

### chat
Send a message to the current chat channel

**Syntax**
```
chat {message}
chat @{channel} {message}
```

**Usage Examples**
```
chat Here be dragons!
chat @direhounds Here be dragons!
```

**Comments**
1. Attempts to chat without joining a group will produce no response from the server!

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### clearnews
Clear all messages in the current chat channel

**Syntax**
```
clearnews
clearnews {channel}
clearnews @{channel}
```

**Usage Examples**
```
clearnews
clearnews direhounds
clearnews @direhounds
```

**Comments**
1. Attempts to use this command without joining a group will produce no response from the server!

**Output: Response**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> Channel news cleared.</font>
```

-------------------------------------------------------------------------------

### jg
Join a chat channel

**Syntax**
```
jg
jg {beekin_group}
jg @{channel}
```

**Usage Examples**
```
jg
jg bugges
jg direhounds
jg @dragons
```

**Comments**
1. Without any arguments, this command joins your first beekin channel.
2. Attempts to use this command on a group one has no access to will produce no response from the server!
3. It is possible to join beekin groups via the @ prefix as well, if you have access to them.

**Output: You Join**
```
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> Direhound channel opened.</font>
]-<img src='http://apollo.furcadia.com/cache/400000085.png' />
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> <name shortname='artex'>Artex</name> has joined the Second Dreaming channel.</font>
]n$@#-DirehoundsJ;�&P��H
```

**Output: Someone Joins**
```
#TODO
```

-------------------------------------------------------------------------------

### kick
Kick a furre from a chat channel

**Syntax**
```
kick {name} {reason}
kick @{channel} {name} {reason}
```

**Usage Examples**
```
kick artex being a dumbass
kick @direhounds artex being a dumbass
```

**Comments**
1. **IMPORTANT**: The kicked user WILL see the kick reason!
2. The kicked user WILL NOT see who kicked them.
3. Attempts to use this command on a group one has no access to will produce no response from the server!

**Output: You Ejected A Furre**
```
(<font color='warning'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> You ejected <name shortname='artex' forced src='helper'>Artex</name> from the Second Dreaming channel.</font>
```

**Output: You Were Ejected**
```
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> Direhound channel closed.</font>
(<font color='error'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> You were ejected from the Second Dreaming channel for being a dumbass.</font>
]n$@#-Direhounds�ډ#P��H
```

**Output: A Furre Was Ejected**
```
#TODO (3rd party observer)
```

-------------------------------------------------------------------------------

### leave
Leave current chat channel

**Syntax**
```
leave
leave {channel}
leave @{channel}
```

**Usage Examples**
```
leave
leave direhounds
leave @direhounds
```

**Comments**
1. Attempts to use this command on a group one has no access to will produce no response from the server!

**Output: You Left**
```
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> Direhound channel closed.</font>
]n$@#-Direhounds�ډ#P��H
```

**Output: Someone Left**
```
#TODO
```

-------------------------------------------------------------------------------

### listf
List furres currently on the chat channel

**Syntax**
```
listf
listf {channel}
listf @{channel}
```

**Syntax**
```
listf
listf direhounds
listf @direhounds
```

**Comments**
1. Attempts to use this command on a group one has no access to will produce no response from the server!

**Output: Response**
```
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> There is 1 Second Dreaming group member on the channel: <name shortname='artex' forced src='helper'>Artex</name></font>
```

-------------------------------------------------------------------------------

### listgroups
List all available chat channels

**Syntax**
```
listgroups
```

**Comments**
1. This command opens up a GUI list on the client!

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### news
Add a message to be displayed when a furre joins the chat channel

**Syntax**
```
news {message}
```

**Usage Examples**
```
news Here be dragons!
```

**Comments**
1. Attempts to use this command on a group one has no access to will produce no response from the server!

**Output: Response**
```
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> News added.</font>
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> News updated:</font>
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> Here be dragons!</font>
```

**Output: News**
```
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> Direhound channel opened.</font>
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> Here be dragons!</font>
]-<img src='http://apollo.furcadia.com/cache/400000085.png' />
(<font color='channel'><img src='http://apollo.furcadia.com/cache/400000080.png' alt='@direhounds' /><channel name='@direhounds' /> <name shortname='artex'>Artex</name> has joined the Second Dreaming channel.</font>
]n$@#-DirehoundsJ;�&P��H
```
* The news appear as part of the [jg](#jg) procedure.

-------------------------------------------------------------------------------

### tellgroup
Send a message to all members of a registered group

**Syntax**
```
tellgroup {message}
```

**Usage Examples**
```
tellgroup Here be dragons!
```

**Comments**
1. Attempts to use this command on a group one has no access to will produce no response from the server!

**Output: Response**
```
#TODO
```

**Output: Message**
```
#TODO
```


---------------------------------------------------------------------------------------------------

## Navigation
| Command                 | Description                                                     |
| :---------------------- | --------------------------------------------------------------- |
| [decline](#decline)     | Reject a join or summon request from another furre              |
| ["dreamurl](#dreamurl)  | Show the dream URL of the dream you are currently in            |
| [fdl](#fdl)             | Go to a dream with a specified Dream URL (e.g: furc://Allegria) |
| [follow](#follow)       | Follow a furre as they move around in the dream                 |
| [glook](#glook)         | Look (possibly across dreams) at a furre with a given name      |
| [goalleg](#goalleg)     | Go to the Allegria dream (map 3)                                |
| [goback](#goback)       | Go to the previously visited dream                              |
| [gomap](#gomap)         | Go to a main map with a given number (single base95 digit)      |
| [gostart](#gostart)     | Go to the Vinca dream (map 0)                                   |
| [join](#join)           | Request to join a specific furre, or accept a summon request    |
| [l](#l%20(coordinates)) | Look at a furre at specific x,y coordinates                     |
| ["l](#l%20(name))       | Look at a furre with a given name                               |
| [lead](#lead)           | Lead a specific furre around the dream                          |
| [stop](#stop)           | Stop leading/following a specific person (see follow)           |
| [summon](#summon)       | Request to join a specific furre, or accept a summon request    |
| [wmap](#wmap)           | Enter the Welcome Map (initial map of every new character)      |

---------------------------------------------------------------------------------------------------

### decline
Reject a join or summon request from another furre

**Syntax**
```
decline
```

**Comments**
1. This command is normally redundant and ignoring the request is a more convenient (and less "loud") option.

**Output: Confirmation**
```
(<font color='warning'>You decline the request from <name shortname='artex'>Artex</name>.</font>
```

**Output: Incoming Decline**
```
(<font color='warning'>Player <name shortname='artex'>Artex</name> declined your request.</font>
```
* Triggered when another furre uses the `decline` command on our request

**Output: No Requests To Decline**
```
(<font color='error'>There are no requests to decline.</font>
```

-------------------------------------------------------------------------------

### "dreamurl
Show the dream URL of the dream you are currently in

**Syntax**
```
"dreamurl
```

**Comments**
1. First introduced in the **Squirrel Update**.

**Output: Dream URL**
```
(<font color='success'>The Dream URL for this dream is: <A HREF="furc://adream/">furc://adream/</A></font>
```

-------------------------------------------------------------------------------

### fdl
Go to a specific dream specified by a URL (e.g: furc://Allegria)

**Syntax**
```
fdl {dreamurl}
```

**Usage Examples**
```
fdl furc://adream
fdl furc://adream:dreamname
fdl furc://adream:dreamname/6
```

**Comments**
1. First introduced in the **Squirrel Update**

-------------------------------------------------------------------------------

### follow
Follow a furre as they move around in the dream

**Syntax**
```
follow
follow {name}
```

**Usage Examples**
```
follow
follow artex
```

**Comments**
1. First introduced in the **Squirrel Update**.
2. This command requires Silver Sponsorship on the character, or Gold Sponsorship on the account.
3. See opposite command: [lead](#lead)

**Output: Confirmation**
```
(<font color='notify'>Your request has been sent to <name shortname='ruah'>Ruah</name>.</font>
```

**Output: Incoming Request**
```
(<font color='query'><name shortname='cpu'>CPU</name> requests permission to follow you. To accept the request, <a href='command://lead'>click here</a> or type `lead and press &lt;enter&gt;.</font>
```

**Output: Player Not Found**
```
(<font color='error'>Sorry, that furre is not in this dream!  -- Beekin the Help Dragon</font>
```
* Triggered when `follow` is used on a missing furre.

**Output: No Such Player**
```
(<font color='error'>Sorry, that player is not in this dream any longer.</font>
```
* Triggered when `follow` is used without a name and no `lead` request was received.

-------------------------------------------------------------------------------

### glook
Look (possibly across dreams) at a furre with a given name

**Syntax**
```
glook {name}
```

**Usage Examples**
```
glook artex
glook albertquirky
```
**Comments**
1. This is a "global" variant of ["l](#l-name) (which is also typo-safer)
2. In order for this command to work across dreams, some form of contact from the other furre is required! For example: a whisper.

**Output: Positive Match**
```
((You see <name shortname='albertquirky'>Albert|Quirky</name>.)

]fw8807C<<(<(1&$�#Albert|Quirky
]&255485 pp255485

(<desc shortname='albertquirky' />&gt; Rawr, I'm a quirky dragon or cat or something. [AKA Moridin] [ <a href="furc://mandatory:pies/">check out my dream where you have to make pies</a> ] <img src='http://apollo.furcadia.com/cache/400003021.png' alt='Bean Club' /> <img src='http://apollo.furcadia.com/cache/252468773.png'/><img src='http://apollo.furcadia.com/cache/252468773.png'/><img src='http://apollo.furcadia.com/cache/252468773.png'/>  <img src='http://apollo.furcadia.com/cache/610000123.png' alt='Catten' /> <img src='http://apollo.furcadia.com/cache/610000226.png' alt='Bearling' /> <img src='http://apollo.furcadia.com/cache/610000241.png' alt='FireClaw' /> <img src='http://apollo.furcadia.com/cache/610000255.png' alt='Mythical Ferian Unicorn' />

```

**Output: Furre Not Online**
```
(<font color='error'>Sorry, no player matching that name is currently online.</font>
```

**Output: May Not Look**
```
(<font color='error'>Sorry, you may not look at that player right now.</font>
```
* This is returned when the character is in another dream and no sufficient contact was established to permit looking across dreams.

-------------------------------------------------------------------------------

### goalleg
Go to the Allegria dream (map 3)

**Syntax**
```
goalleg
```

-------------------------------------------------------------------------------

### goback
Go to the previously visited dream

**Syntax**
```
goback
```

-------------------------------------------------------------------------------

### gomap
Go to a main map with a given number (single base95 digit)

**Syntax**
```
gomap {b95digit}
```

**Usage Examples**
```
gomap #
gomap "
gomap 0
```

**Comments**
1. The `gomap` command accepts a single base95 digit
2. It is possible to exceed the base95 upper boundary and use characters between 0x80 and 0xFF

-------------------------------------------------------------------------------

### gostart
Go to the Vinca dream (map 0)

**Syntax**
```
gostart
```

-------------------------------------------------------------------------------

### join
Request to join a specific furre, or accept a summon request

**Syntax**
```
join
join {name}
```

**Usage Examples**
```
join
join artex
```

**Comments**
1. See opposite command [summon](#summon).

**Output: Confirmation**
```
(<font color='success'>Your request has been sent to <name shortname='ruah'>Ruah</name>.</font>
```

**Output: Join Without Summon**
```
(<font color='error'>Please use at least one letter (a-z, A-Z, 0-9) of the name so I can tell exactly who you mean!  -- Beekin the Help Dragon</font>
```
* Triggered when using `join` without a name and without an incoming summon request.

**Output: Join Request Accepted**
```
(<font color='success'><name shortname='ruah'>Ruah</name> has accepted your request.</font>
(<font color='success'><name shortname='ruah'>Ruah</name> summons you.</font>
```
* Triggered when your `join` request get accepted.

**Output: Join Request Declined**
```
(<font color='warning'>Player <name shortname='artex'>Artex</name> declined your request.</font>
```
* Triggered when another furre uses the `decline` command on our request

-------------------------------------------------------------------------------

### l (coordinates)
Look at a furre at specific x,y coordinates

**Syntax**
```
l {b95xx}{b95yy}
```

**Usage Examples**
```
l  : H
```

-------------------------------------------------------------------------------

### "l (name)
Look at a furre with a given name

**Syntax**
```
"l {name}
"look {name}
```

**Usage Examples**
```
"l artex
"look artex
```

**Output: Positive Match**
```
((You see <name shortname='artex'>Artex</name>.)

]fw%5K(J;,;;;#;$�#Artex
]&251324 pp251324

]-<img src='http://apollo.furcadia.com/cache/400000085.png' />
(<desc shortname='artex' /> [Telegram: @IceDragon] Black from snout to tail tip, this average-sized midnight drake seemed barely noticeable among the shadows he lounged in. His scales were of the darkest shade of blue, discernible from pure black only by the keenest of eyes, a pair of large half-folded wings rested above him, casting a shade and protecting the dragon from sunlight. His head was adorned with a pair of black horns - one at each side, with a silvery dark mane starting between them and going down to his tailtip. A silver collar could be seen around his neck, reflecting the light that touches it. His calm posture indicated no sign of hostility. // Open for casual chat; whisper me if I don't respond. <img src='http://apollo.furcadia.com/cache/400001411.png' alt='Dragon�s Den' /> <img src='http://apollo.furcadia.com/cache/400000617.png' alt='Team Dragon' /> <img src='http://apollo.furcadia.com/cache/400002398.png' alt='Dragons' />  #C' <img src='http://apollo.furcadia.com/cache/610000102.png' alt='Dragon' /> <img src='http://apollo.furcadia.com/cache/610000145.png' alt='Mythical Ferian Dragon' /> <img src='http://apollo.furcadia.com/cache/610000150.png' alt='Kirikin' /> <img src='http://apollo.furcadia.com/cache/610000161.png' alt='Dragonling' /> <img src='http://apollo.furcadia.com/cache/610000163.png' alt='Seahorse' /> <img src='http://apollo.furcadia.com/cache/610000179.png' alt='Mythical Gargoyle' /> <img src='http://apollo.furcadia.com/cache/610000184.png' alt='Fleer Seasonal' /> <img src='http://apollo.furcadia.com/cache/610000189.png' alt='AngelCat' /> <img src='http://apollo.furcadia.com/cache/610000193.png' alt='Mythical Ferian Gryffe' /> <img src='http://apollo.furcadia.com/cache/610000204.png' alt='Skunken Ferian' /> <img src='http://apollo.furcadia.com/cache/610000207.png' alt='Angelfish Seasonal' /> <img src='http://apollo.furcadia.com/cache/610000267.png' alt='Mythical Ferian Icewing' /> <img src='fsh://desctags.fsh:148' /> <img src='http://apollo.furcadia.com/cache/252468913.png' alt="For Life" /> <img src='http://apollo.furcadia.com/cache/252469049.png' /> <img src='http://apollo.furcadia.com/cache/252469236.png' /> <img src='http://apollo.furcadia.com/cache/252469291.png' />
```

**Output: Furre Not Present**
```
(<font color='error'>Sorry, that furre is not in this dream!  -- Beekin the Help Dragon</font>
```

-------------------------------------------------------------------------------

### lead
Lead a specific furre around the dream

**Syntax**
```
lead
lead {name}
```

**Usage Examples**
```
lead
lead artex
```

**Comments**
1. First introduced in the **Squirrel Update**.
2. This command requires Silver Sponsorship on the character, or Gold Sponsorship on the account.
3. See opposite command: [follow](#follow).

**Output: Confirmation**
```
(<font color='notify'>Your request has been sent to <name shortname='cpu'>CPU</name>.</font>
```

**Output: Incoming Request**
```
(<font color='query'><name shortname='ruah'>Ruah</name> requests permission to lead you. To accept the request, <a href='command://follow'>click here</a> or type `follow and press &lt;enter&gt;.</font>
```

**Output: Player Not Found**
```
(<font color='error'>Sorry, that furre is not in this dream!  -- Beekin the Help Dragon</font>
```
* Triggered when `lead` is used on a missing furre.

**Output: No Such Player**
```
(<font color='error'>Sorry, that player is not in this dream any longer.</font>
```
* Triggered when `lead` is used without a name and no `follow` request was received.

**Output: Player Started Following**
```
(<font color='success'><name shortname='ruah'>Ruah</name> begins to follow you. To break off, <a href='command://stop'>click here</a> or type `stop and press &lt;enter&gt;.</font>
```

**Output: Player Stopped Following**
```
(<font color='notify'><name shortname='ruah'>Ruah</name> stops following you.</font>
```
* Triggered when a furre stops following you (e.g., after you leave the dream as a leader).

-------------------------------------------------------------------------------

### stop
#ss-only 
Stop leading/following a specific person (see follow)

**Syntax**
```
stop
```

**Output: Confirmation**
```
(<font color='notify'>Stopped following <name shortname='cpu'>CPU</name>.</font>
```
* Triggered when following or leading a furre. DOES NOT trigger if NOT following/leading!

**Output: Incoming Stop**
```
(<font color='notify'><name shortname='ruah'>Ruah</name> stops following you.</font>
```
* Triggered when a furre stops following you (e.g., when you leave dream).

-------------------------------------------------------------------------------

### summon
Request to join a specific furre, or accept a summon request

**Syntax**
```
join
join {name}
```

**Usage Examples**
```
join
join artex
```

**Comments**
1. See opposite command [join](#join).

**Output: Confirmation**
```
(<font color='success'>Your request has been sent to <name shortname='ruah'>Ruah</name>.</font>
```

**Output: Join Without Summon**
```
(<font color='error'>Please use at least one letter (a-z, A-Z, 0-9) of the name so I can tell exactly who you mean!  -- Beekin the Help Dragon</font>
```
* Triggered when using `join` without a name and without an incoming summon request.

**Output: Join Request Accepted**
```
(<font color='success'><name shortname='ruah'>Ruah</name> has accepted your request.</font>
(<font color='success'><name shortname='ruah'>Ruah</name> summons you.</font>
```
* Triggered when your `join` request get accepted.

**Output: Join Request Declined**
```
(<font color='warning'>Player <name shortname='artex'>Artex</name> declined your request.</font>
```
* Triggered when another furre uses the `decline` command on our request

-------------------------------------------------------------------------------

### wmap
Enter the Welcome Map (initial map of every new character)

**Syntax**
```
wmap
```

**Output: Response**
```
^  

]M% *$�#�k&#)$�#j`&#+$�#ެ%#)$�#��,#/$�$��(#,$�#`T'#*$�#//'#)$�#��'#+$�#��&#,$�#4�.#+$�#s�-#/$�#��&#+$�#�`%#/$�#��+#3$�#�((#.$�#Y+&#*$�#rb'#0$�#��)#/$�#��0#0$�#6l*#4$�#�I)#0#�#�n##*$�#C�&#+$�#��)#\$�#�1(#/$�#v�'#($�#G#%#6$�#��%#3$�#�0)#-$�#aK%#-$�#G�*#($�#YY(#($�#p�*#'#�#}�##)$�#T�&#+$�$[�%#-$�#d�-#*$�#y@%#($�#DP'#)$�#<a&#+$�#��$#1$�#��&#-$�#�1(#-$�#q�,#,$�#��*#)$�#��*#)#�#B�##.$�#��(#,$�#��)#+$�#��&#0$�#X6*#+$�$Y�%#*$�#Ɉ)#-$�#��*#)$�#��%#,$�#ݙ'#/$�#��)#-$�#Q�+#-$�#{�+#*$�#�h%#+$�#��&#($�#P�(#'#�#g�##*$�#�b&#+$�#�b.#)$�#��$#.$�#tn%#+$�#}�'#+$�#f�'#)$�#��%#-$�#�%#)$�#�v&#,$�#��%#*$�#�4&#*$�#2�'#*$�#�/*#)#�#Q�##)$�#5�)#'#�#��##,$�$�A&#-$�#K�(#)$�#�0'#-$�#�'#+$�#��'#,$#&Y4%#*$$%8G(#)$%%`�$#>$&%��%#,$'%7�&#+$(%��)#,$)%Ys&#-$*%�[&#+$+%�()#)$,%I�(#*$-%��&#,$.%2�%#+$/%;�&#($0%_�&#)$1%��/#*$2&U�)#)#2%W�##,$4%��%#+$5%9n'#,$6%��&#($7%�A&#,$8%�&+#.$9%��)#)$:%��)#,$;%��%#-$<%Vg(#*$=%9�&#/$>%��)#/$?%�@0#+$@%��%#)$A&�q)#0$B%��.#+$C%<$'#-$D%c�*#0$E%%V)#)$F%h:*#)$G%Y�%#+$H%Z�-#.$I%�+,#,$J%�,-#*$K%��*#%$L%�1#)$M%})*#'$N%�U-#%$O%$�)#)$P%_�*#'$Q%P�(#)$R%$�1#'$S%��5#'$T%XP+#%$U%��%#'$V%OE)#)$W%�E+#($X%#�*#%$Y%t�(#'$Z%��*#&$[%�x+#&$\&,�'#'$]%��+#&$^%��(#%$_%�M)#&$`%Zj*#&$a%��*#'$b%��)#%$c%��%#'$d%�]6#&$e%��*#)$f%�h&#%$g&�3.#&$h%��(#($i%��*#%$j&�W&#($k%��)#&$l%�y0#)$m%�[)#%$n%D�##%$o%��%#($p%yx(#&$q%f7&#'$r%�W,#'$s%��*#*$t%m9)#&$u%T�*#+$v&b�)#'$w%�j*#'$x%#�*#'$y%�F)#'$z%#�(#%${%��&#%$|%��'#&$}%�g*#&$~&h�%#%$&,b%#&$�%/))#%$�%s�$#%$�%��%#%$�%��6#($�%˂'#%$�%Ņ'#%$�%υ(#'$�%�Q5#($�%}�(#%$�%y�&#%$�%�s)#&$�&u�(#&$�%?�'#%$�%/v(#
]|0
^  
%  
]ccmarbled.pcx
(<img src='fsh://system.fsh:86' /> Dream Standard: <a href='http://www.furcadia.com/standards/'>T+ Environment</a>
(<img src='fsh://system.fsh:86' /> <a href='http://www.facebook.com/sharer.php?u=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Ft%3D4%26x%3D498528348'><img src='http://apollo.furcadia.com/cache/7-dt-share-fb.png' /></a> <a href='http://twitter.com/share?text=%23Furcadia%20dream&url=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Ft%3D4%26x%3D498528348'><img src='http://apollo.furcadia.com/cache/10-dt-share-t-sml.png' /></a> Share this dream with your friends.
]omainmap4
~
]q pmchallengeresort 1287740434   modern
]}w%5K(J;,;;;#;$�#
```


---------------------------------------------------------------------------------------------------

## Character
| Command                             | Description                                                   |
| :---------------------------------- | ------------------------------------------------------------- |
| [< (turn CCW)](#-turn-ccw)          | Turn counter-clockwise                                        |
| [> (turn CW)](#-turn-cw)            | Turn clockwise                                                |
| [afk](#afk)                         | Enter AFK state                                               |
| ["awaymessage](#awaymessage)        | (UNKNOWN)                                                     |
| [cuddle](#cuddle)                   | Request to cuddle an adjacent furre, or accept such a request |
| [get](#get)                         | Pick up or drop an object                                     |
| [lie](#lie)                         | Cycle through positions: laying >> sitting >> standing        |
| [liedown](#liedown)                 | Switch into a laying position                                 |
| [m](#m)                             | Move                                                          |
| [sit](#sit)                         | Switch into a sitting position                                |
| [stand](#stand)                     | Switch into a standing position                               |
| [unafk](#unafk)                     | Leave AFK state                                               |
| [use](#use)                         | Use the object you are currently holding                      |

**Reference**
* [Movement Commands](https://cms.furcadia.com/help/commands/keycommands/generalcommands/movementcommands)

---------------------------------------------------------------------------------------------------

### `<` (turn CCW)
Turn counter-clockwise

**Syntax**
```
<
```

-------------------------------------------------------------------------------

### `>` (turn CW)
Turn clockwise

**Syntax**
```
>
```

-------------------------------------------------------------------------------

### afk
Enable AFK state

**Syntax**
```
afk
afk {reason}
```

**Usage Examples**
```
afk
afk Back soon
```

**Comments**
1. Displays an "AFK" symbol next to your name.
2. Changes your description to a preconfigured AFK description, with the reason plugged in (see output examples).
3. Use [unafk](#unafk) to leave AFK mode.

**Output: Response**
```
<&N�&.#D##)&CPUw8807C<<(<(1&$�#%$###�
]H&N�&O$?$
]Hf��&?$O$
```
* This is sent by the server after you enter AFK state

-------------------------------------------------------------------------------

### "awaymessage
(UNKNOWN)

**Syntax**
```
"awaymessage
```

**Comments**
1. PURPOSE UNKNOWN!
2. Mentioned in the client as a string.
3. The server does not respond to the command (even as regular speech)
	* proof that this is a special string on the server's end as well!

-------------------------------------------------------------------------------

### cuddle
Request to cuddle an adjacent furre, or accept such a request

**Syntax**
```
cuddle
cuddle {name}
```

**Usage Examples**
```
cuddle
cuddle artex
```

**Output: Cuddle Request Sent**
```
(<font color='success'>Your request has been sent to <name shortname='artex'>Artex</name>.</font>
```

**Output: Cuddle Request Received**
```
(<font color='query'><name shortname='artex'>Artex</name> asks you to cuddle with them. To accept the request, <a href='command://cuddle'>click here</a> or type `cuddle and press &lt;enter&gt;.</font>
```

**Output: Cuddle Accepted**
```
]H&N�&O$?$
]Hf��&?$O$
```
* These instructions adjust character positions after cuddle request is accepted

-------------------------------------------------------------------------------

### get
Pick up or drop an object

**Syntax**
```
get
```

-------------------------------------------------------------------------------

### lie
Cycle through positions: laying -> sitting -> standing

**Syntax**
```
lie
```

-------------------------------------------------------------------------------

### liedown
Switch into a laying position

```
liedown
```

-------------------------------------------------------------------------------

### m
Move

**Syntax**
```
m {direction}
```
* Directions:
	* `1` - South-West
	* `3` - South-East
	* `7` - North-West
	* `9` - North-East
* Hint: the direction numbers correspond to their direction on the number pad

**Usage Examples**
```
m 1
m 3
m 7
m 9
```

-------------------------------------------------------------------------------

### sit
Switch into a sitting position

**Syntax**
```
sit
```

-------------------------------------------------------------------------------

### stand
Switch into a standing position

**Syntax**
```
stand
```

-------------------------------------------------------------------------------

### unafk
Leave AFK mode and mark yourself as active again

**Syntax**
```
unafk
```

**Comments**
1. This command undoes the [afk](#afk) command.
2. Removes the "AFK" symbol next to your name.
3. Reverts your description to what it was before you entered AFK state.

**Output: Response**
```
<&N�&.#D##)&CPUw8807C<<(<(1&$�#%####�
]H&N�&O$?$
]Hf��&?$O$
```
* This is sent by the server after you leave AFK state

-------------------------------------------------------------------------------

### use
Use the object you are currently holding

**Syntax**
```
use
```

---------------------------------------------------------------------------------------------------

## Information
| Command             | Description                                                                  |
| ------------------- | ---------------------------------------------------------------------------- |
| ["help](#help)      | Request help from the Beekin help channel                                    |
| [info](#info)       | Request information on current character from the server                     |
| [onln](#onln)       | Request the online status of a specific person (the name has to be complete) |
| [onlnprx](#onlnprx) | Ignore all commands from the client except for `onln`                        |
| ["time](#time)      | Request Furcadia Standard Time (FST)                                         |
| [which](#which)     | Request server-side information related to your current session              |
| [who](#who)         | Request a list of users in current dream, server uptime and global usercount |

---------------------------------------------------------------------------------------------------

### "help
Request help from the Beekin help channel

**Syntax**
```
"help {message}
```

**Usage Examples**
```
"help How do you whisper?
```

**Output: Confirmation**
```
(<font color='success'><img src='fsh://system.fsh:99' alt='@help' /><channel name='@help' /> Your help request was sent, and someone from the Help channel should contact you shortly. If no one contacts you soon, please <a href='https://support.furcadia.com'>submit a support ticket</a> to get assistance.</font>
```

-------------------------------------------------------------------------------

### info
Request information on current character from the server

**Syntax**
```
info
"info
```

**Output: Info**
```
(Player info: CPU (artex@rawr.com)
(Furcadia UID: 38266613
(Furcadia account ID: 666
(Created on: 2004-06-17/10:55:25/Thu 
(Logged in: 5946 times
(Time spent in Furcadia: 13890 days, 4 hours, 29 minutes, 57 seconds
(Extra: Gold Sponsorship (account)
(Extra: Dragon <img src='http://apollo.furcadia.com/cache/610000102.png' />
(Extra: Mythical Ferian Dragon <img src='http://apollo.furcadia.com/cache/610000145.png' />
(Portraits: 0 active, 1 inactive, 0 waiting for review
(Item: cookies (0 active, 12 inactive)
(DragonScales Balance: 0 GD, 0 SD, 0 CD (total $0.00 USD)
```

-------------------------------------------------------------------------------

### onln
Request the online status of a specific person (the name has to be complete)

**Syntax**
```
onln {name}
```

**Usage Examples**
```
onln artex
onln albertquirky
onln Albert|Quirky
```

**Comments**
1. A complete name that resolves into a shortname must be supplied - NOT a partial!
	* `albertquirky` - is a shortname
	* `AlbertQuirky` - resolves into `albertquirky` shortname (not a display name)
	* `Albert|Quirky` - resolves into `albertquirky` shortname (and is a display name)

**Output: User Online**
```
]%1Albert|Quirky
```
* The formal display name is returned even if the input name was short.

**Output: User Offline**
```
]%0ruah
```
* The input name is returned: the server doesn't know the display name of offline users.

-------------------------------------------------------------------------------

### onlnprx
Ignore all commands from the client except for `onln`

**Syntax**
```
onlnprx
```

**Comments**
1. First introduced in the **Squirrel Update**.
2. The server does not provide a response for this command.
3. The server keeps sending information over to the client (DragonSpeak events, etc.)
4. The character remains inside the dream it was in prior to this command.
5. The server DOES NOT process any commands other than [onln](#onln) (not even `quit`)!

-------------------------------------------------------------------------------

### "time
Request Furcadia Standard Time (FST)

**Syntax**
```
"time
```

**Output: Response**
```
(<img src='fsh://system.fsh:86' /> Furcadia Standard Time: 1:31:24 PM
```

-------------------------------------------------------------------------------

### which
Request server-side information related to your current session

**Syntax**
```
which
```

**Output: Response**
```
(<img src='fsh://system.fsh:86' /> You are connected to Heimdall [6500:2] (QTEMP 13218). There are 75 players on this Heimdall, of which you are player index 74 with globalid 8735, and you are on map 7
```
* Beekins and staff have three additional lines with more information on Horton and Tribble IDs

-------------------------------------------------------------------------------

### who
Request a list of users in current dream, server uptime and global usercount

**Syntax**
```
who
```

**Output: Response**
```
(<img src='fsh://system.fsh:86' /> Dream Standard: <a href='http://www.furcadia.com/standards/'>M16+ Environment</a>
(<img src='fsh://system.fsh:86' /> <a href='http://www.facebook.com/sharer.php?u=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Ft%3D7%26x%3D1426600272'><img src='http://apollo.furcadia.com/cache/7-dt-share-fb.png' /></a> <a href='http://twitter.com/share?text=%23Furcadia%20dream&url=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Ft%3D7%26x%3D1426600272'><img src='http://apollo.furcadia.com/cache/10-dt-share-t-sml.png' /></a> Share this dream with your friends.
(<img src='fsh://system.fsh:86' /> Current players: <name shortname='celescheresm' forced>Celes|Chere#SM</name>, <name shortname='marro' forced>Marro</name>, <name shortname='artex' forced>Artex</name>, <name shortname='seismograph' forced>Seismograph</name>, <name shortname='jaialai' forced>Jai|Alai</name>, <name shortname='albertquirky' forced>Albert|Quirky</name>, <name shortname='tanloc' forced>Tan|Loc</name>, <name shortname='neotheone' forced>NeoTheOne</name>, <name shortname='eclipsemoonflower' forced>Eclipse|Moonflower</name>, <name shortname='iskierkakiryu' forced>Iskierka|Kiryu</name>, <name shortname='nyaih' forced>Nyaih</name>, <name shortname='cpu' forced>CPU</name>.
(<img src='fsh://system.fsh:86' /> 12 players in this dream.
```
...the output example is extremely messy here, but it's essentially this:
```
450 total players online. Uptime 374 days 23:33
Max players this session: 631
Max players today: 451
Dream Standard: (URL: http://www.furcadia.com/standards/) M16+ Environment
(URL: http://www.facebook.com/sharer.php?u=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Ft%3D7%26x%3D433810370) (URL: http://twitter.com/share?text=%23Furcadia%20dream&url=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Ft%3D7%26x%3D433810370) Share this dream with your friends.
Current players: Albert|Quirky, Artex, Celes|Chere # , CPU, Eclipse|Moonflower, Iskierka|Kiryu, Jai|Alai, Marro, NeoTheOne, Nyaih, Seismograph, Tan|Loc
12 players in this dream.
```


---------------------------------------------------------------------------------------------------

## Dream Control

| Command                            | Description                                                                         |
| ---------------------------------- | ----------------------------------------------------------------------------------- |
| [art-party](#art-party)            | Toggle "art party" mode, or initiate art party with a given furre                   |
| [art-watcher](#art-watcher)        | Initiate art party in watch mode with a given furre                                 |
| ["banish](#banish)                 | Banish a furre from your dream                                                      |
| ["banish-off](#banish-off)         | Unbanish a furre from your dream (also: **"unbanish**)                              |
| ["banish-off-all](#banish-off-all) | Unbanish all furres banished from your dream                                        |
| ["banish-list](#banish-list)       | List all furres banished from your dream                                            |
| ["eject](#eject)                   | Remove unwanted furre from your dream                                               |
| ["emit](#emit)                     | Show a message to all furres within listening distance                              |
| ["emitloud](#emitloud)             | Show a message to all furres in the dream                                           |
| ["entrymusic](#entrymusic)         | Set a midi file that will be played for all furres who enter your dream             |
| ["entrytext](#entrytext)           | Set a text that will be shown to all furres who enter your dream                    |
| [live-edit](#live-edit)            | Toggle live editing of the dream                                                    |
| [noendurance](#noendurance)        | Turn off the "throat is tired" flood check for a given furre                        |
| ["notify-toggle](#notify-toggle)   | Toggle notification that discloses the name of whoever emits or ejects              |
| ["notify](#notify)                 | Change the name of the recipient for the ["notify-toggle](#notify-toggle) messages  |
| ["pads-all](#pads-all)             | Allow all furres to upload to any dream upload pad                                  |
| ["pads-owner](#pads-owner)         | Allow allow only dream owner to upload to dream upload pads                         |
| ["pads-shared](#pads-shared)       | Allow allow only dream owner and shared furres to upload to pads                    |
| ["pads-ss](#pads-ss)               | Allow allow only dream owner and Silver Sponsors to upload to pads                  |
| [parental](#parental)              | Toggle parental controls for the current dream                                      |
| ["share](#share)                   | Share control over current dream with another furre                                 |
| [share-edit](#share-edit)          | Share editing of the current dream with another furre (live-edit)                   |
| [shield](#shield)                  | Toggle summoning anywhere other than dream entrance                                 |
| [shieldurl](#shieldurl)            | Toggle the option that prevents accessing your dream through a URL                  |
| ["tempbanish](#tempbanish)         | Banish a furre from your dream for three days                                       |
| [unload](#unload)                  | Unload dreams (dream portals) from the map you are currently on                     |
| [unparty](#unparty)                | End "art party" with a given furre                                                  |
| ["unshare](#unshare)               | Revoke shared control access from a given furre in the current dream                |
| [unshare-edit](#unshare-edit)      | Stop sharing editing of current dream with another furre                            |
| ["uploads-all](#uploads-all)       | Allow all furres to upload to any empty spot in the current dream                   |
| ["unloads-owner](#uploads-owner)   | Allow only dream owner to upload to empty spots (default state)                     |
| ["uploads-shared](#uploads-shared) | Allow all furres to upload to empty spots                                           |
| ["uploads-ss](#uploads-ss)         | Allow only dream owner and Sponsors to upload to empty spots                        |

---------------------------------------------------------------------------------------------------

### art-party
Toggle "art party" mode in the current dream, or initiate art party with a given furre

**Syntax**
```
art-party
art-party {name}
```

**Usage Examples**
```
art-party
art-party artex
```

**Comments**
1. Use [art-watcher](#art-watcher) command to initiate art party in watch mode.
2. Use [unparty](#unparty) command to end art party.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only start an art party in your own dreams.</font>
```

-------------------------------------------------------------------------------

### art-watcher
Initiate art party in watch mode with a given furre

**Syntax**
```
art-watcher {name}
```

**Usage Examples**
```
art-watcher artex
```

**Comments**
1. Use [art-party](#art-party) command to initiate art party in edit mode.
2. Use [unparty](#unparty) command to end art party.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only start an art party in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "banish
Banish a furre from your dream

**Syntax**
```
"banish {name}
```

**Usage Examples**
```
"banish artex
```

**Output: Response**
```
(<font color='success'>Artex has been banished from your dreams.</font>
```

**Output: Furre Not Online**
```
(<font color='error'> There are no furres around right now with a name starting with artex.</font>
```

**Output: Cannot Banish Yourself**
```
(<font color='error'>Sorry, you cannot banish yourself.</font>
```
* This message is returned when you try to banish another character on your account.

-------------------------------------------------------------------------------

### "banish-off
Unbanish a furre from your dream (also: **"unbanish**)

**Syntax**
```
"banish-off {name}
"unbanish {name}
```

**Usage Examples**
```
"banish-off artex
"unbanish artex
```

**Output: Response**
```
(<font color='notify'>The banishment of player artex has ended.</font>
```

**Output: Not Banished**
```
(<font color='error'>Sorry, this player has not been banished from your dreams.</font>
```

-------------------------------------------------------------------------------

### "banish-off-all
Unbanish all furres banished from your dream

**Syntax**
```
"banish-off-all
```

**Output: Response**
```
(<font color='success'>You have canceled all banishments from your dreams.</font>
```

**Output: Banish List Empty**
```
(<font color='error'>You have not banished anyone.</font>
```

-------------------------------------------------------------------------------

### "banish-list
List all furres banished from your dream

**Syntax**
```
"banish-list
```

**Output: Response**
```
(<font color='notify'>Players banished from your dreams: Albert|Quirky, Artex</font>
```

**Output: Response (empty list)**
```
(<font color='notify'>Players banished from your dreams: </font>
```

-------------------------------------------------------------------------------

### "eject
Remove unwanted furre from your dream

**Syntax**
```
"eject {name}
```

**Usage Examples**
```
"eject artex
```

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only eject furres from your own dreams.</font>
```

-------------------------------------------------------------------------------

### "emit
Show a message to all furres within listening distance

**Syntax**
```
"emit {message}
```

**Usage Examples**
```
"emit Rawr rawr!
```

**Comments**
1. Use the ["emitloud](#emitloud) command to emit the message to all furres in the dream.
2. This command requires you to have "share" access to the dream, or being its owner.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only emit text in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "emitloud
Show a message to all furres in the dream

**Syntax**
```
"emit {message}
```

**Usage Examples**
```
"emit Rawr rawr!
```

**Comments**
1. Use the ["emit](#emit) command to emit the message to all furres in listening distance.
2. This command requires you to have "share" access to the dream, or being its owner.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only emit text in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "entrymusic
Set a midi file that will be played for all furres who enter your dream

**Syntax**
```
"entrymusic {num}
```

**Usage Examples**
```
"entrymusic 5
```

**Output: Response**
```
#TODO
```

**Output: Not Dream Owner**
```
(<font color='error'>Only the dream owner can change the entry music.</font>
```

-------------------------------------------------------------------------------

### "entrytext
Set a text that will be shown to all furres who enter your dream

**Syntax**
```
"entrytext {text}
```

**Usage Examples**
```
"entrytext Welcome to the dream! Rawr.
```

**Output: Response**
```
#TODO
```

**Output: Not Dream Owner**
```
(<font color='error'>Only the dream owner can change the entry text.</font>
```

-------------------------------------------------------------------------------

### live-edit
Toggle live editing of the dream

**Syntax**
```
live-edit
```

**Comments**
1. Use [share-edit](#share-edit) command to edit the dream with someone else.
2. The server will not respond if live-editing of current dream is not allowed!

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### noendurance
Turn off the "throat is tired" flood check for a given furre

**Syntax**
```
noendurance {name}
```

**Usage Examples**
```
noendurance artex
```

**Comments**
1. Dream owner MUST have Sponsorship to use this feature

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only turn endurance off in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "notify-toggle
Toggle notification that discloses the name of whoever emits or ejects

**Syntax**
```
"notify-toggle
```

**Comments**
1. Use the ["notify](#notify) command to change the name of the recipient.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only use this command in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "notify
Change the name of the recipient for the ["notify-toggle](#notify-toggle) messages

**Syntax**
```
"notify {name}
```

**Usage Example**
```
"notify artex
```

**Comments**
1. Use the ["notify-toggle](#notify-toggle) command to toggle the feature on or off.
2. For now, the targeted furre must have Sponsorship!

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only use this command in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "pads-all
Allow all furres to upload to any "Upload your dream here" pad (default state)

**Syntax**
```
"pads-all
```

**Comments**
1. Use ["pads-owner](#pads-owner) to allow only the dream owner to upload to upload pads.
2. Use ["pads-shared](#pads-shared) to allow the dream owner and shared furres to use upload pads.
3. Use ["pads-ss](#pads-ss) to allow only the dream owner and Sponsors to upload to upload pads.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only change the settings in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "pads-owner
Allow allow only the dream owner to upload to "Upload your dream here" pads

**Syntax**
```
"pads-owner
```

**Comments**
1. Use ["pads-all](#pads-all) to allow all furres to upload to upload pads (i.e., default state).
2. Use ["pads-shared](#pads-shared) to allow the dream owner and shared furres to use upload pads.
3. Use ["pads-ss](#pads-ss) to allow only the dream owner and Sponsors to upload to upload pads.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only change the settings in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "pads-shared
Allow only the dream owner and shared furres to upload to "Upload your dream here" pads

**Syntax**
```
"pads-shared
```

**Comments**
1. Use ["pads-all](#pads-all) to allow all furres to upload to upload pads (i.e., default state).
2. Use ["pads-owner](#pads-owner) to allow only the dream owner to upload to upload pads.
3. Use ["pads-ss](#pads-ss) to allow only the dream owner and Sponsors to upload to upload pads.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only change the settings in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "pads-ss
Allow only the dream owner and Sponsors to upload to "Upload your dream here" pads

**Syntax**
```
"pads-ss
```

**Comments**
1. First introduced in the **Squirrel Update**.
2. Use ["pads-all](#pads-all) to allow all furres to upload to upload pads (i.e., default state).
3. Use ["pads-owner](#pads-owner) to allow only the dream owner to upload to upload pads.
4. Use ["pads-shared](#pads-shared) to allow the dream owner and shared furres to use upload pads.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only change the settings in your own dreams.</font>
```

-------------------------------------------------------------------------------

### parental
Toggle parental controls for the current dream

**Syntax**
```
parental
```

**Comments**
1. This feature is responsible for preventing furres from entering your dream if their parental controls are set to prevent access to R-rated areas.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>Only the dream owner can change the parental controls setting.</font>
```

-------------------------------------------------------------------------------

### "share
Share control over current dream with another furre

**Syntax**
```
"share {name}
```

**Usage Examples**
```
"share artex
```

**Comments**
1. Using `"share` without arguments just says the word "share" out loud.
2. Use ["unshare](#unshare) to revoke said control.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only share control of your own dreams.</font>
```

-------------------------------------------------------------------------------

### share-edit
Share editing of the current dream with another furre (live-edit)

**Syntax**
```
share-edit {name}
```

**Usage Examples**
```
share-edit artex
```

**Comments**
1. Use [live-edit](#live-edit) to toggle live editing of the dream.
2. Use [unshare-edit](#unshare-edit) to stop share-editing the dream with another furre.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only share editing of your own dreams.</font>
```

-------------------------------------------------------------------------------

### shield
Toggle the option that prevents summoning anywhere other than dream entrance

**Syntax**
```
shield
```

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only shield your own dreams.</font>
```

-------------------------------------------------------------------------------

### shieldurl
Toggle the option that prevents accessing your dream through a URL

**Syntax**
```
shieldurl
```

**Comments**
1. First introduced in the **Squirrel Update**.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only shield your own dreams.</font>
```

-------------------------------------------------------------------------------

### "tempbanish
Banish a furre from your dream for three days

**Syntax**
```
"tempbanish {name}
```

**Usage Examples**
```
"tempbanish artex
```

**Output: Response**
```
(<font color='success'>Artex has been temporarily banished from your dreams.</font>
```

**Output: Furre Not Online**
```
(<font color='error'> There are no furres around right now with a name starting with artex.</font>
```

**Output: Cannot Banish Yourself**
```
(<font color='error'>Sorry, you cannot banish yourself.</font>
```
* This message is returned when you try to banish another character on your account.

-------------------------------------------------------------------------------

### unload
Unload dreams (dream portals) from the map you are currently on

**Syntax**
```
unload
unload all
unload {name}
```

**Usage Examples**
```
unload
unload all
unload artex
unload albertquirky
```

**Comments**
1. `unload` unloads all of your own dream portals from the current dream.
2. `unload all` unloads all dream portals in the current dream.
3. `unload {name}` unload dream portals of a specific furre from current dream.

**Output: Response (unload)**
```
(<font color='success'>You unload all your dreams from this dream.</font>
```

**Output: No Allowed**
```
(<font color='error'>You cannot unload other furres dreams here, only your own.</font>
```

-------------------------------------------------------------------------------

### unparty
End "art party" with a given furre

**Syntax**
```
unparty {name}
```

**Usage Examples**
```
unparty artex
```

**Comments**
1. Use [art-party](#art-party) command to initiate art party in edit mode.
2. Use [art-watcher](#art-watcher) command to initiate art party in watch mode.

**Output: Response**
```
(<font color='success'>You are no longer in the art party.</font>
]Z0
```
* This is always returned when the command is executed - against anyone...

-------------------------------------------------------------------------------

### "unshare
Revoke shared control access from a given furre in the current dream

**Syntax**
```
unshare {name}
```

**Usage Examples**
```
unshare artex
```

**Comments**
1. Counteracts the ["share](#share) command.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only unshare control of your own dreams.</font>
```

-------------------------------------------------------------------------------

### unshare-edit
Stop sharing editing of current dream with another furre

**Syntax**
```
unshare-edit {name}
```

**Usage Examples**
```
unshare-edit artex
```

**Comments**
1. Counter-acts the [share-edit](#share-edit) command.
2. Use [live-edit](#live-edit) to toggle live editing of the dream.
3. The server will not respond to this command if not share-editing anyone.

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "uploads-all
Allow all furres to upload to any empty spot in the current dream

**Syntax**
```
"uploads-all
```

**Comments**
1. Use ["uploads-owner](#uploads-owner) to allow only the dream owner to upload to any empty spot (default state).
2. Use ["uploads-shared](#uploads-shared) to allow only the dream owner or shared furres to upload to any empty spot.
3. Use ["uploads-ss](#uploads-ss) to allow only the dream owner and Sponsors to upload to any empty spot.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only change the settings in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "uploads-owner
Allow only the dream owner to upload to any empty spot in the current dream (default state)

**Syntax**
```
"uploads-owner
```

**Comments**
1. This is the default state for the upload restriction mechanism.
2. Use ["uploads-all](#uploads-all) to allow only the dream owner to upload to any empty spot.
3. Use ["uploads-shared](#uploads-shared) to allow only the dream owner or shared furres to upload to any empty spot.
4. Use ["uploads-ss](#uploads-ss) to allow only the dream owner and Sponsors to upload to any empty spot.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only change the settings in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "uploads-shared
Allow all furres to upload to any empty spot in the current dream

**Syntax**
```
"uploads-shared
```

**Comments**
1. Use ["uploads-all](#uploads-all) to allow only the dream owner to upload to any empty spot.
2. Use ["uploads-owner](#uploads-owner) to allow only the dream owner to upload to any empty spot (default state).
3. Use ["uploads-ss](#uploads-ss) to allow only the dream owner and Sponsors to upload to any empty spot.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only change the settings in your own dreams.</font>
```

-------------------------------------------------------------------------------

### "uploads-ss
Allow only the dream owner and Sponsors to upload to any empty spot in the current dream

**Syntax**
```
"uploads-ss
```

**Comments**
1. First introduced in the **Squirrel Update**.
2. Use ["uploads-all](#uploads-all) to allow only the dream owner to upload to any empty spot.
3. Use ["uploads-owner](#uploads-owner) to allow only the dream owner to upload to any empty spot (default state).
4. Use ["uploads-shared](#uploads-shared) to allow only the dream owner or shared furres to upload to any empty spot.

**Output: Response**
```
#TODO
```

**Output: Not Your Dream**
```
(<font color='error'>You can only change the settings in your own dreams.</font>
```


---------------------------------------------------------------------------------------------------

## Digos - General

| Command                 | Description                                          |
| ----------------------- | ---------------------------------------------------- |
| [chcol](#chcol)         | Change avatar colors in-game as a Sponsor            |
| [chdesc](#chdesc)       | Change description in-game as a Sponsor              |
| [portrait](#portrait)   | Change to a specific portrait                        |
| [portrchng](#portrchng) | Change to the next portrait                          |
| [remap](#remap)         | Remap the colors of a portrait to a given color code |
| [wings](#wings)         | Cycle through any wings that you own                 |

**Reference**
* [Digo Commands](https://cms.furcadia.com/help/commands/keycommands/digocommands)

---------------------------------------------------------------------------------------------------

### chcol
Change avatar colors in-game as a Sponsor

**Syntax**
```
chcol {colors}
```

**Usage Examples**
```
chcol w8807C<<(<(1&$�#
chcol w%5K(J;,;;;#;$�#
```

**Comments**
1. This command requires Silver Sponsorship on the character, or Gold Sponsorship on the account.

**Output: Response**
```
B&N�&&(w8807C<<(<(1&$�#
```

-------------------------------------------------------------------------------

### chdesc
Change description in-game as a Sponsor

**Syntax**
```
chdesc {description}
```

**Usage Examples**
```
chdesc New description here
```

**Comments**
1. This command requires Silver Sponsorship on the character, or Gold Sponsorship on the account.
2. The server does not respond to the command (at least not when it's successful)

-------------------------------------------------------------------------------

### portrait
Change to a specific portrait

**Syntax**
```
portrait 0
portrait {portrait_index}
```

**Usage Examples**
```
portrait 0
portrait 2
```

**Comments**
1. `portrait 0` turns portraits off and makes your portrait appear as your species default.
2. Portrait indexes start from 1 up until the number of active portrait spaces you have.
3. If portrait index is out of range, portrait 1 is used.

**Output: No Portraits**
```
(<font color='error'>To get your personal portraits today, visit http://furcadia.com/digomarket/ (press F8 now to open the page in your web browser)</font>
]fw8807C<<(<(1&$�#CPU
```
* This includes `portrait 0` when you have no active portrait spaces!

**Output: Portraits Off**
```
#TODO
```

**Output: Change Portrait**
```
#TODO
```

-------------------------------------------------------------------------------

### portrchng
Change to the next portrait

**Syntax**
```
portrchng
```

**Comments**
1. This command cycles upwards, then resets to 0 (i.e., "default portrait")

**Output: No Portraits**
```
(<font color='error'>To get your personal portraits today, visit http://furcadia.com/digomarket/ (press F8 now to open the page in your web browser)</font>
```
* Note that unlike [portrait](#portrait) - this command does not send `]f` after the error!

**Output: Portraits Off
```
#TODO
```

**Output: Change Portrait**
```
#TODO
```

-------------------------------------------------------------------------------

### remap
Remap the colors of a portrait to a given color code

**Syntax**
```
remap {portrait_index} {colors}
```

**Usage Examples**
```
remap 1 w%5K(J;,;;;#;$'#
```

**Comments**
1. Allows personal portraits to change colors if base colors are used in the making of the portrait.
2. Portrait indexes start from 1 up until the number of active portrait spaces you have.
3. The server does not respond to this command if it cannot be run!

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### wings
Cycle through any wings that you own

**Syntax**
```
wings
```

**Output: No Wings**
```
(<font color='error'>You do not have wings. To order a pair, go to http://www.furcadia.com/digomarket/ (Press F8 now)</font>
```


---------------------------------------------------------------------------------------------------

## Digos - Species
| Command               | Description                            |
| --------------------- | -------------------------------------- |
| [dragon](#dragon)     | Toggle the Dragon form                 |
| [mfdragon](#mfdragon) | Toggle the Mythical Ferian Dragon form |
| [phoenix](#phoenix)   | Toggle the Phoenix form                |

> **MISSING COMMANDS**
> Due to sheer ever-growing amount of species (most of which have the same core behavior), only a few of these are listed here!
> 
> For a full list of desctags, check out the reference links below!

**Reference**
* [Digo Commands](https://cms.furcadia.com/help/commands/keycommands/digocommands)

---------------------------------------------------------------------------------------------------

### dragon
Toggle the Dragon form

**Syntax**
```
dragon
```

**Output: Reaction**
```
B&N�&%)w%5K(J;,;;;#;$�#
]}w%5K(J;,;;;#;$�#
```

**Output: Not A Dragon**
```
#TODO
```

-------------------------------------------------------------------------------

### mfdragon
Toggle the Mythical Ferian Dragon form

**Syntax**
```
mfdragon
```

**Output: Reaction**
```
B&N�&%)w%5K(J;,;;;#;$�#
]}w%5K(J;,;;;#;$�#
```

**Output: Not A Mythical Ferian Dragon**
```
#TODO
```

-------------------------------------------------------------------------------

### phoenix
Toggle the Phoenix form

**Syntax**
```
phoenix
```

**Output: Reaction**
```
#TODO
```

**Output: Not a Phoenix**
```
(<font color='error'>You are not a phoenix. Please visit http://www.furcadia.com/digomarket/ for information about how to order one.</font>
```


---------------------------------------------------------------------------------------------------

## Digos - Magic
| Command                   | Description                                                      |
| ------------------------- | ---------------------------------------------------------------- |
| [breath](#breath)         | Trigger the dragon breath (must be done as a Dragon)             |
| [flame](#flame)           | Trigger the phoenix flame (must be done as a Phoenix)            |
| [fly](#fly)               | Toggle "flying" mode for digos that support it                   |
| [glamour](#glamour)       | Use the unicorn glamour effect                                   |
| [gloam](#gloam)           | Change the brightness of your avatar ("the gloaming")            |
| [kirincloud](#kirincloud) | Toggle the kirin cloud                                           |
| [kittersize](#kittersize) | Change the size of your avatar ("kittersize dust")               |
| [magic](#magic)           | Use any magic your current digo has available                    |
| [purify](#purify)         | Use the mythical ferian unicorn "purify" effect on another furre |
| [splash](#splash)         | Use the naga splash effect                                       |
| [stone](#stone)           | Toggle the gargoyle "stone" mode                                 |
| [twixt](#twixt)           | Switch places with another furre (Jackalope ability)             |

**Reference**
* [Digo Commands](https://cms.furcadia.com/help/commands/keycommands/digocommands)

---------------------------------------------------------------------------------------------------

### breath
Trigger the dragon breath (must be done as a Dragon)

**Syntax**
```
breath
```

**Output: Response**
```
]va * @ #
```
* Dragon breath effect at coordinates 10,32 (` * @`) in direction 3 (` #`) - North-East

**Output: Not a Dragon**
```
(<font color='error'>You are not a dragon. Please visit our online store for information about how to order one. http://www.furcadia.com/digomarket/</font>
```

-------------------------------------------------------------------------------

### flame
Trigger the phoenix flame (must be done as a Phoenix)

**Syntax**
```
flame
```

**Output: Response**
```
]vb * @ !
```
* Dragon breath effect at coordinates 10,32 (` * @`) in direction 1 (` !`) - South-East

**Output: Not a Phoenix**
```
(<font color='error'>You are not a phoenix. Please visit our online store for information about how to order one. http://www.furcadia.com/digomarket/</font>
```

-------------------------------------------------------------------------------

### fly
Toggle "flying" mode for digos that support it

**Syntax**
```
fly
```

**Output: Fly Enabled**
```
B&N�&%%w%5K(J;,;;;#;$�#
]}w%5K(J;,;;;#;$�#
```

**Output: Fly Disabled**
```
B&N�&%%w%5K(J;,;;;#;$�#
]}w%5K(J;,;;;#;$�#
```
* There may be a difference in non-printable characters

**Output: Not Supported**
```
(<font color='error'>This command does nothing in your current form. Check <a href='http://www.furcadia.com/digomarket/'>Furcadia Digo Market</a> for avatars that might let you use this command.</font>
```

-------------------------------------------------------------------------------

### glamour
Create unicorn glamour effect

**Syntax**
```
glamour
```

**Output: Response**
```
#TODO
```

**Output: Not A Unicorn**
```
(<font color='error'>You are not a Unicorn. Please visit our online store for information about how to order one. http://www.furcadia.com/digomarket/</font>
```

-------------------------------------------------------------------------------

### gloam
Change the brightness of your avatar ("the gloaming")

**Syntax**
```
gloam {delta}
```

**Usage Examples**
```
gloam -3
gloam -2
gloam -1
gloam 0
gloam 1
gloam 2
gloam 3
```

**Comments**
1. You must have access to this feature in order to use it! Not everybody does!
2. The server does not respond in any way if you have no access to this feature!
3. `gloam 0` is the default (original) value.
4. The value can go between -3 and 3.
5. Furres with special access can push pass these boundaries into a solid shade (value -254 or 254)!

**Output: Out of Range**
```
#TODO
```

**Output: Gloam Enabled**
```
#TODO
```
* Text: "The Gloaming rises up from within, affecting your entire being.  To return to normal, click here or type \`gloam 0 and press enter."

**Output: Gloam Disabled**
```
#TODO
```
* Text: "With force of will you suppress your Gloaming, keeping it at bay, for now."

-------------------------------------------------------------------------------

### kirincloud
Toggle the kirin cloud

**Syntax**
```
kirincloud
```

**Output: Response**
```
#TODO
```

**Output: Not A Kirin**
```
(<font color='error'>You are not a Kirin. Check <a href='http://www.furcadia.com/digomarket/'>Furcadia Digo Market</a> for information about how to order one.</font>
```

-------------------------------------------------------------------------------

### kittersize
Change the size of your avatar ("kittersize dust")

**Syntax**
```
kittersize {percentage}
```

**Usage Examples**
```
kittersize 20
kittersize 100
kittersize 200
```

**Comments**
1. You must have access to this feature in order to use it! Not everybody does!
2. The server does not respond in any way if you have no access to this feature!
3. `kittersize 100` is the default (original) size.

-------------------------------------------------------------------------------

### magic
Use any magic your current digo has available

**Syntax**
```
magic
```

**Comments**
1. This is a general catch-all command for special abilities of the currently worn species.
2. If your species does not support this command, there will be no response from the server!

**Output: Response**
```
B&N�&%)w%5K(J;,;;;#;$�#
]}w%5K(J;,;;;#;$�#
```
* This response may be limited to Mythical Ferian Dragons

-------------------------------------------------------------------------------

### purify
Use the mythical ferian unicorn "purify" effect on another furre

**Syntax**
```
purify
```

**Output: Response**
```
#TODO
```

**Output: Not A Mythical Ferian Unicorn**
```
(<font color='error'>You are not a mythical ferian unicorn. Please visit our online store for information about how to order one. http://www.furcadia.com/digomarket/</font>
```

-------------------------------------------------------------------------------

### splash
Use the naga splash effect

**Syntax**
```
splash
```

**Output: Response**
```
#TODO
```

**Output: Not A Naga**
```
(<font color='error'>You are not a naga. Please visit our online store for information about how to order one. http://www.furcadia.com/digomarket/</font>
```

-------------------------------------------------------------------------------

### stone
Toggle the gargoyle "stone" mode

**Syntax**
```
stone
```

**Comments**
1. Using this command while not a Naga produces no response from the server!

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### twixt
Switch places with another furre (Jackalope ability)

**Syntax**
```
twixt {name}
```

**Usage Examples**
```
twixt Artex
```

**Output: Response**
```
#TODO
```

**Output: Not A Mythical Ferian Jackalope**
```
(<font color='error'>You are not a Mythical Ferian Jackalope. Please visit our online store for information about how to order one. http://www.furcadia.com/digomarket/</font>
```


---------------------------------------------------------------------------------------------------

## Digos - Roses
| Command                                      | Description                                                     |
| -------------------------------------------- | --------------------------------------------------------------- |
| ["discard-rose](#discard-rose)               | An alias to the ["discard-red-rose](#discard-red-rose) command  |
| ["discard-black-rose](#discard-black-rose)   | Permanently remove a black rose that someone gave you           |
| ["discard-purple-rose](#discard-purple-rose) | Permanently remove a purple rose that someone gave you          |
| ["discard-red-rose](#discard-red-rose)       | Permanently remove a red rose that someone gave you             |
| ["discard-white-rose](#discard-white-rose)   | Permanently remove a white rose that someone gave you           |
| ["discard-yellow-rose](#discard-yellow-rose) | Permanently remove a yellow rose that someone gave you          |
| ["give-rose](#give-rose)                     | An alias to the ["give-red-rose](#give-red-rose) command        |
| ["give-black-rose](#give-black-rose)         | Give another furre a black rose                                 |
| ["give-purple-rose](#give-purple-rose)       | Give another furre a purple rose                                |
| ["give-red-rose](#give-red-rose)             | Give another furre a red rose                                   |
| ["give-white-rose](#give-white-rose)         | Give another furre a white rose                                 |
| ["give-yellow-rose](#give-yellow-rose)       | Give another furre a yellow rose                                |

> **MISSING COMMANDS**
> The [Roses and Gifts](https://cms.furcadia.com/help/commands/keycommands/digocommands/roses)
> page contains items not listed in this section that you can `give-` and `discard-` the same
> way as you can roses! To avoid over-inflating this file (and to save time) these additional
> items will not be included here.

**Reference**
* [Roses and Gifts](https://cms.furcadia.com/help/commands/keycommands/digocommands/roses)

---------------------------------------------------------------------------------------------------

### "discard-rose
An alias to the ["discard-red-rose](#discard-red-rose) command

-------------------------------------------------------------------------------

### "discard-black-rose
Permanently remove a black rose that someone gave you

**Syntax**
```
"discard-black-rose
```

**Comments**
1. Black roses were introduced in the **Squirrel Update**.

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "discard-purple-rose
Permanently remove a purple rose that someone gave you

**Syntax**
```
"discard-purple-rose
```

**Comments**
1. Purple roses were introduced in the **Squirrel Update**.

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "discard-red-rose
Permanently remove a red rose that someone gave you

**Syntax**
```
"discard-red-rose
```

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "discard-white-rose
Permanently remove a white rose that someone gave you

**Syntax**
```
"discard-white-rose
```

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "discard-yellow-rose
Permanently remove a yellow rose that someone gave you

**Syntax**
```
"discard-yellow-rose
```

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "give-rose
An alias to the ["give-red-rose](#give-red-rose) command

-------------------------------------------------------------------------------

### "give-black-rose
Give another furre a black rose

**Syntax**
```
"give-black-rose {name}
"give-black-rose {name} {message}
```

**Usage Examples**
```
"give-black-rose artex
"give-black-rose artex Rawr! #SI
```

**Comments**
1. Black roses were first introduced in the **Squirrel Update**

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "give-purple-rose
Give another furre a purple rose

**Syntax**
```
"give-purple-rose {name}
"give-purple-rose {name} {message}
```

**Usage Examples**
```
"give-purple-rose artex
"give-purple-rose artex Rawr! #SI
```

**Comments**
1. Purple roses were first introduced in the **Squirrel Update**

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "give-red-rose
Give another furre a red rose

**Syntax**
```
"give-red-rose {name}
"give-red-rose {name} {message}
```

**Usage Examples**
```
"give-red-rose artex
"give-red-rose artex Rawr! #SI
```

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "give-white-rose
Give another furre a red rose

**Syntax**
```
"give-white-rose {name}
"give-white-rose {name} {message}
```

**Usage Examples**
```
"give-white-rose artex
"give-white-rose artex Rawr! #SI
```

**Output: Response**
```
#TODO
```

-------------------------------------------------------------------------------

### "give-yellow-rose
Give another furre a yellow rose

**Syntax**
```
"give-yellow-rose {name}
"give-yellow-rose {name} {message}
```

**Usage Examples**
```
"give-yellow-rose artex
"give-yellow-rose artex Rawr! #SI
```

**Output: Response**
```
#TODO
```


---------------------------------------------------------------------------------------------------

## Digos - Gifts

| Command                      | Description                                         |
| ---------------------------- | --------------------------------------------------- |
| ["gift-{item}](#gift-{item}) | Give an item you possess to another furre as a gift |
| ["gift-scales](#gift-scales) | Give DragonScales to another furre as a gift        |

**Reference**
* [Gift Commands](https://cms.furcadia.com/den/service/trade/27-gift-commands)

---------------------------------------------------------------------------------------------------

### "gift-{item}
Give an item you possess to another furre as a gift

**Syntax**
```
"gift-{item} {name}
"gift-{item} {name} {message}
"gift-{item} {name} %{message}
```

**Usage Examples**
```
"gift-triwings albertquirky
"gift-triwings albertquirky Rawr! #SI
"gift-triwings albertquirky %Rawr! #SI
```

**Comments**
1. Spaces in names should be omitted!
2. Your gift will be anonymous without a message.
3. Prefix your message with `%` for your gift (and the message) to remain anonymous!
4. For an up-to-date list of items, visit the [Items](https://cms.furcadia.com/den/service/trade/items) page on Furcadia.
5. For DragonScales gifting use the ["gift-scales](#gift-scales) command.

**Output: Response/Warning**
```
(<font color='warning'>*WARNING*  You are about to gift ownership of your Tri-Colored Wings to <b>artex</b>. If you do this, the Tri-Colored Wings will be under their control, and only they can give them to anyone else in the future.  Also, they will not be able to gift the Tri-Colored Wings to anyone for 30 days - not even back to you.  If you are SURE you want to do this, type "gift-triwings artex" again to confirm the gift.</font>
```
* Example command: `gift-triwings artex`
* This warning appears even if you don't have the item!

**Output: Item Missing**
```
(<font color='error'><img src='fsh://system.fsh:100' /> Cannot gift Tri-Colored Wings: You do not have Tri-Colored Wings.</font>
```
* Example command: `gift-triwings artex` (twice)

**Output: Incorrect Name**
```
(<font color='error'>Error: Incorrect name. Use gift-triwings &lt;name&gt; (&lt;message&gt;)</font>
```

-------------------------------------------------------------------------------

### "gift-scales
Give DragonScales to another furre as a gift

**Syntax**
```
gift-scales {name} {amount} {GD|SD|CD}
gift-scales {name} {amount} {GD|SD|CD} {message}
```

**Usage Examples**
```
gift-scales artex 5 GD
gift-scales artex 30 SD Rawr! #SI
```

**Comments**
1. The amount HAS to be an integer!
2. 1GD = 10SD = 100CD

**Output: Response/Warning**
```
(<font color='warning'>*WARNING*  You are about to gift the equivalent of 0.01 USD in Game Currency (DragonScales) to <b>artex</b>.  If you do this, the DragonScales will be under their control, and only they can give it to anyone else in the future. If you're SURE you want to do this, type "gift-scales artex 1 CD Rawr" again to confirm the gift.</font>
```
* Example command: `gift-scales artex 1 CD Rawr`
* This warning appears even if you don't have the item!

**Output: Missing Scales**
```
(<font color='error'><img src='fsh://system.fsh:100' /> Cannot gift DragonScales: Internal server error 4.</font>
```
* Example command: `gift-scales artex 1 CD Rawr` (twice)


---------------------------------------------------------------------------------------------------

## Digos - Description Tags (desctags)

| Command                              | Description                                        |
| ------------------------------------ | -------------------------------------------------- |
| ["accept-desctags](#accept-desctags) | Allow other furres to throw desctags at you        |
| ["desctags](#desctags)               | Enable or disable description tags                 |
| ["reject-desctags](#reject-desctags) | Prevent other furres from throwing desctags at you |

> **MISSING COMMANDS**
> Due to sheer ever-growing amount of desctags (most of which have the same core behavior),
> only a few of these are listed here!
> 
> For a full list of desctags, check out the reference links below!

**Reference**
* [Desctag Visibility Settings](https://cms.furcadia.com/desctag/settings#desctags)
* [Digo Commands](https://cms.furcadia.com/help/commands/keycommands/digocommands)

---------------------------------------------------------------------------------------------------

### "accept-desctags
Allow other furres to throw desctags at you

**Syntax**
```
"accept-desctags
```

**Comments**
1. Use ["reject-desctags](#reject-desctags) command to reject desctags.

**Output: Response**
```
(<font color='success'>You are now accepting desctags.</font>
```

-------------------------------------------------------------------------------

### "desctags
Enable or disable description tags

**Syntax**
```
"desctags
```

**Comments**
1. Not all your description tags disappear! There are different types of them...

**Output: Desctags Off**
```
(<font color='success'>Description tags off.</font>
```

**Output: Desctags On**
```
(<font color='success'>Description tags on.</font>
```

-------------------------------------------------------------------------------

### "reject-desctags
Prevent other furres from throwing desctags at you

**Syntax**
```
"reject-desctags
```

**Comments**
1. Use ["accept-desctags](#accept-desctags) command to accept desctags again.

**Output: Response**
```
(<font color='success'>You are now rejecting desctags.</font>
```

---------------------------------------------------------------------------------------------------

## Digos - Secure Trade
| Command                        | Description                                           |
| ------------------------------ | ----------------------------------------------------- |
| ["trade-add](#trade-add)       | Add an item to the trade                              |
| ["trade-accept](#trade-accept) | Finalize the trade                                    |
| ["trade-end](#trade-end)       | End the trade session (no item exchange takes place)  |
| ["trade-reason](#trade-reason) | Set a trade reason for the record                     |
| ["trade-reject](#trade-reject) | Reject the trade offer (without ending trade session) |
| ["trade-remove](#trade-remove) | Remove an item from the trade                         |
| ["trade-start](#trade-start)   | Start a trade session with a given furre              |
| ["trade-status](#trade-status) | Show the status of the current trade                  |

**Reference**
* [Gifting and Secure Trading](https://cms.furcadia.com/den/service/trade)

---------------------------------------------------------------------------------------------------

### "trade-add
Add an item to the trade

**Syntax**
```
"trade-add {item}
```

**Usage Examples**
```
"trade-add dragon
"trade-add triwings
"trade-add GD 5
```

**Output: Confirmation (your end)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> Dragonling added to your proposed trade with Artex.</font>
```

**Output: Confirmation (their end)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> Artex has added Dragonling to their current offer.</font>
```
* Example command: `"trade-add dragonling`

**Output: Recipient Already Has Item**
```
(<font color='error'><img src='fsh://system.fsh:100' /> Cannot trade Dragon: Artex already has Dragon.</font>
```
* Example command: `"trade-add dragon`

**Output: Not In Session**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You can only use this command while trading. Try trade-start &lt;name&gt;.</font>
```

**Output: No Item**
```
(<font color='error'><img src='fsh://system.fsh:100' /> Cannot trade Naga: You do not have Naga.</font>
```
* Example command: `"trade-add naga`

**Output: Not Enough GD**
```
(<font color='error'><img src='fsh://system.fsh:100' /> Sorry, you do not have enough Golden DragonScales for that.</font>
```
* Example command: `"trade-add GD 5`

**Output: Missing Argument**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You must follow "trade-add" with one of the following words: bat, batwings, butterflywings, catten, chinchilla, classicwings, dragon, flox, foxen, furling, gloaming, gryffe, kirin, kittersize, kitterwing, kiwi, leonen, lovebird, naga, noble-canine, noble-equine, noble-feline, noble-rodent, noble-hyooman, owlen, panooki, penguin, phoenix, primewings, portrait (unused portrait space), animated-portrait, rabben, reindeer, toaster, toytle, triwings, tusker, tygard, unicorn, werewolf, wolven, woolie, black-rose (black rosebud), bouquet (inactive flower bouquet), purple-rose (purple rosebud), red-rose (red rosebud), white-rose (white rosebud), yellow-rose (yellow rosebud), candy-cane, flaming-sword, friendship-bracelet, magic-wand, snug, sword, valentine, valentine-fancy, GD <i>x</i> (<i>x</i> Golden DragonScales), SD <i>x</i> (<i>x</i> Silver DragonScales), or CD <i>x</i> (<i>x</i> Copper DragonScales).</font>
```

-------------------------------------------------------------------------------

### "trade-accept
Finalize the trade

**Syntax**
```
"trade-accept
```

**Comments**
1. The trade is finalized when both sides `"trade-accept`.
2. To change your mind and "un-accept" a trade, use ["trade-reject](#trade-reject).

**Output: Confirmation**
```
#TODO
```

**Output: Response (your side)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> You accept the current offer. If Artex accepts also, the trade will be performed. If you change your mind, type trade-reject.</font>
```

**Output: Response (their side)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> Artex has accepted the offer. If you agree, type trade-accept - but be certain, once you agree there's no taking it back! Type trade-status if you want to make sure you know exactly what's being traded first.</font>
```

**Output: Not In Session**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You can only use this command while trading. Try trade-start &lt;name&gt;.</font>
```

-------------------------------------------------------------------------------

### "trade-end
End the trade session (no item exchange takes place)

**Syntax**
```
"trade-end
```

**Output: Confirmation (your end)**
```
(<font color='success'><img src='fsh://system.fsh:100' /> You end the trading session.</font>
```

**Output: Confirmation (their end)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> Your trading session has ended.</font>
```

**Output: Not In Session**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You are not trading with anyone right now!</font>
```

-------------------------------------------------------------------------------

### "trade-reason
Set a trade reason for the record

**Syntax**
```
"trade-reason {reason}
```

**Usage Examples**
```
"trade-reason Dragon in exchange for a portrait space
```

**Comments**
1. First introduced in the **Squirrel Update**.
2. Gives a better idea of the nature of the trade in case of a dispute.

**Output: Response (your side)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> You set your trade reason to 'Rawr!'.</font>
```

**Output: Response (their side)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> Artex sets their trade reason to 'Rawr!'.</font>
```

**Output: Not In Session**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You can only use this command while trading. Try trade-start &lt;name&gt;.</font>
```

-------------------------------------------------------------------------------

### "trade-reject
Reject the trade offer (without ending trade session)

**Syntax**
```
"trade-reject
```

**Comments**
1. Counteracts the ["trade-accept](#trade-accept) command, if previously executed.

**Output: Rejected (our end)***
```
(<font color='error'><img src='fsh://system.fsh:100' /> You reject the current offer.</font>
```

**Output: Rejected (their end)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> Artex has changed their mind and rejected the offer.</font>
```

**Output: Not Accepted**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You have not accepted the current offer.</font>
```

-------------------------------------------------------------------------------

### "trade-remove
Remove an item from the trade

**Syntax**
```
"trade-remove {item}
```

**Usage Examples**
```
"trade-remove dragon
"trade-remove triwings
"trade-remove GD 5
```

**Output: Confirmation (your end)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> You have removed Dragonling from your current offer.</font>
```
* Example command: `"trade-remove dragonling`

**Output: Confirmation (their end)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> Artex has removed Dragonling from their current offer.</font>
```
* Example command: `"trade-remove dragonling`

**Output: Not In Session**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You can only use this command while trading. Try trade-start &lt;name&gt;.</font>
```

**Output: No Item**
```
(<font color='error'><img src='fsh://system.fsh:100' /> Cannot trade Naga: You do not have Naga.</font>
```
* Example command: `"trade-add naga`

**Output: Not Enough GD**
```
(<font color='error'><img src='fsh://system.fsh:100' /> Sorry, you do not have enough Golden DragonScales for that.</font>
```
* Example command: `"trade-add GD 5`

**Output: Missing Argument**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You must follow "trade-add" with one of the following words: bat, batwings, butterflywings, catten, chinchilla, classicwings, dragon, flox, foxen, furling, gloaming, gryffe, kirin, kittersize, kitterwing, kiwi, leonen, lovebird, naga, noble-canine, noble-equine, noble-feline, noble-rodent, noble-hyooman, owlen, panooki, penguin, phoenix, primewings, portrait (unused portrait space), animated-portrait, rabben, reindeer, toaster, toytle, triwings, tusker, tygard, unicorn, werewolf, wolven, woolie, black-rose (black rosebud), bouquet (inactive flower bouquet), purple-rose (purple rosebud), red-rose (red rosebud), white-rose (white rosebud), yellow-rose (yellow rosebud), candy-cane, flaming-sword, friendship-bracelet, magic-wand, snug, sword, valentine, valentine-fancy, GD <i>x</i> (<i>x</i> Golden DragonScales), SD <i>x</i> (<i>x</i> Silver DragonScales), or CD <i>x</i> (<i>x</i> Copper DragonScales).</font>
```

-------------------------------------------------------------------------------

### "trade-start
Start a trade session with a given furre

**Syntax**
```
"trade-start
"trade-start {name}
```

**Usage Examples**
```
"trade-start
"trade-start artex
```

**Comments**
1. The initiating side MUST specify a name.
2. The receiving side (which must accept the trade request) - doesn't have to specify a name.

**Output: Response (your end)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> Your request has been sent to <name shortname='artex'>Artex</name>.</font>
```

**Output: Response (their end)**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> <name shortname='artex'>Artex</name> asks you to have a trading session. To accept the request, type trade-start and press &lt;enter&gt;.</font>
```

**Output: Trade Started**
```
(<font color='trade'><img src='fsh://system.fsh:100' /> You and Artex have begun a trading session. Commands available: trade-status, trade-add <item>, trade-remove <item>, trade-reason <reason>, trade-accept, trade-reject, trade-end</font>
```
* This is returned when trade request gets accepted by the recipient.

**Output: Session Already Established**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You are already trading with Artex. You must end this trading session with trade-end before you can start another one.</font>
```

-------------------------------------------------------------------------------

### "trade-status
Show the status of the current trade

**Syntax**
```
"trade-status
```

**Output: Response**
```
( 
(<font color='trade'><img src='fsh://system.fsh:100' /> Current trade status:</font>
(<font color='trade'><img src='fsh://system.fsh:100' /> CPU offers:</font>
(<font color='trade'><img src='fsh://system.fsh:100' />   (No items offered yet.)</font>
(<font color='trade'><img src='fsh://system.fsh:100' /> You have not accepted the current trade.</font>
(<font color='trade'><img src='fsh://system.fsh:100' /> Artex offers: </font>
(<font color='trade'><img src='fsh://system.fsh:100' />   Dragonling, for-life </font>
(<font color='trade'><img src='fsh://system.fsh:100' /> Artex has not accepted the current trade.</font>
(<font color='trade'><img src='fsh://system.fsh:100' /> Commands available: trade-status, trade-add <item>, trade-remove <item>, trade-reason <reason>, trade-accept, trade-reject, trade-end</font>
( 
```

**Output: No Session**
```
(<font color='error'><img src='fsh://system.fsh:100' /> You are not trading with anyone right now. Try trade-start &lt;name&gt;.</font>
```


---------------------------------------------------------------------------------------------------

## Server & Session
| Command                     | Description                                                             |
| --------------------------- | ----------------------------------------------------------------------- |
| [account](#account)         | Log into a character from a given account                               |
| [color](#color)             | Set the colors of a logging in avatar                                   |
| [connect](#connect)         | #legacy Log into a character (succeeded by [account](#account))         |
| [create](#create)           | #obsolete Create a new character (succeeded by web creation)            |
| [desc](#desc)               | Temporarily change or set the character's description                   |
| [gdlgt](#gdlgt)             | (UNKNOWN)                                                               |
| [iamhere](#iamhere)         | Keepalive string to prevent TCP timeout mechanism from kicking in       |
| [ping](#ping)               | Check connection by pinging the server                                  |
| [marco](#marco)             | (UNCLEAR) Responded to by [polon](#polon)                               |
| [mvrwm](#mvrwm)             | Request a globally unique integer from the server; purpose unclear      |
| [polon](#polon)             | (UNCLEAR) Response command to `]marco` instruction                      |
| [quit](#quit)               | Disconnect (gracefully) from the server                                 |
| [repq](#repq)               | Respond to a server query dialog box (instruction `]#`)                 |
| [rgate](#rgate)             | Request to upload a dream                                               |
| ["setemail](#setemail)      | #legacy Change the e-mail address on the current character              |
| [tdgate](#tdgate)           | Register a dream portal for a given dream ID (after [rgate](#rgate))    |
| [uid](#uid)                 | Request a globally unique integer from the server; purpose unclear      |
| [vascodagama](#vascodagama) | Notify the server of patch/dream download completion                    |
| [version](#version)         | Report your Furcadia client version to the server (may trigger updates) |
| [Winver](#Winver)           | Report your Windows version to the server                               |

---------------------------------------------------------------------------------------------------

### account
Log into a character from a given account

**Syntax**
```
account {email} {character} {account_password}
```

**Usage Examples**
```
account artex@draax.net Artex br34k^me!
account artex@draax.net CPU br34k^me!
```

**Comments**
1. This command only works when logging in!
2. This command succeeds the legacy [connect](#connect) command.

**Output: Success**
```
]M% *$�#�k&#)$�#j`&#+$�#ެ%#)$�#��,#/$�$��(#,$�#`T'#*$�#//'#)$�#��'#+$�#��&#,$�#4�.#+$�#s�-#/$�#��&#+$�#�`%#/$�#��+#3$�#�((#.$�#Y+&#*$�#rb'#0$�#��)#/$�#��0#0$�#6l*#4$�#�I)#0#�#�n##*$�#C�&#+$�#��)#\$�#�1(#/$�#v�'#($�#G#%#6$�#��%#3$�#�0)#-$�#aK%#-$�#G�*#($�#YY(#($�#p�*#'#�#}�##)$�#T�&#+$�$[�%#-$�#d�-#*$�#y@%#($�#DP'#)$�#<a&#+$�#��$#1$�#��&#-$�#�1(#-$�#q�,#,$�#��*#)$�#��*#)#�#B�##.$�#��(#,$�#��)#+$�#��&#0$�#X6*#+$�$Y�%#*$�#Ɉ)#-$�#��*#)$�#��%#,$�#ݙ'#/$�#��)#-$�#Q�+#-$�#{�+#*$�#�h%#+$�#��&#($�#P�(#'#�#g�##*$�#�b&#+$�#�b.#)$�#��$#.$�#tn%#+$�#}�'#+$�#f�'#)$�#��%#-$�#�%#)$�#�v&#,$�#��%#*$�#�4&#*$�#2�'#*$�#�/*#)#�#Q�##)$�#5�)#'#�#��##,$�$�A&#-$�#K�(#)$�#�0'#-$�#�'#+$�#��'#,$#&Y4%#*$$%8G(#)$%%`�$#>$&%��%#,$'%7�&#+$(%��)#,$)%Ys&#-$*%�[&#+$+%�()#)$,%I�(#*$-%��&#,$.%2�%#+$/%;�&#($0%_�&#)$1%��/#*$2&U�)#)#2%W�##,$4%��%#+$5%9n'#,$6%��&#($7%�A&#,$8%�&+#.$9%��)#)$:%��)#,$;%��%#-$<%Vg(#*$=%9�&#/$>%��)#/$?%�@0#+$@%��%#)$A&�q)#0$B%��.#+$C%<$'#-$D%c�*#0$E%%V)#)$F%h:*#)$G%Y�%#+$H%Z�-#.$I%�+,#,$J%�,-#*$K%��*#%$L%�1#)$M%})*#'$N%�U-#%$O%$�)#)$P%_�*#'$Q%P�(#)$R%$�1#'$S%��5#'$T%XP+#%$U%��%#'$V%OE)#)$W%�E+#($X%#�*#%$Y%t�(#'$Z%��*#&$[%�x+#&$\&,�'#'$]%��+#&$^%��(#%$_%�M)#&$`%Zj*#&$a%��*#'$b%��)#%$c%��%#'$d%�]6#&$e%��*#)$f%�h&#%$g&�3.#&$h%��(#($i%��*#%$j&�W&#($k%��)#&$l%�y0#)$m%�[)#%$n%D�##%$o%��%#($p%yx(#&$q%f7&#'$r%�W,#'$s%��*#*$t%m9)#&$u%T�*#+$v&b�)#'$w%�j*#'$x%#�*#'$y%�F)#'$z%#�(#%${%��&#%$|%��'#&$}%�g*#&$~&h�%#%$&,b%#&$�%/))#%$�%s�$#%$�%��%#%$�%��6#($�%˂'#%$�%Ņ'#%$�%υ(#'$�%�Q5#($�%}�(#%$�%y�&#%$�%�s)#&$�&u�(#&$�%?�'#%$�%/v(#
&&&&&&&&&&&&&
]k2
]w
]marco 99
]B38245463 CPU
(<font color='success'><img src='fsh://system.fsh:83' alt='@events' /><channel name='@events' /> Event channel on.</font>
(<font color='success'><img src='fsh://system.fsh:82' alt='@news' /><channel name='@news' /> News channel on.</font>
(<font color='success'><img src='fsh://system.fsh:102' alt='@spice' /><channel name='@spice' /> Spice channel on.</font>
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000016.png' /> Talz channel on. Mrrelcome!</font>
^  
%  
]ccmarbled.pcx
(<img src='fsh://system.fsh:86' /> Lines of DragonSpeak: 109
(<img src='fsh://system.fsh:86' /> Dream Standard: <a href='http://www.furcadia.com/standards/'>M16+ Environment</a>
(<img src='fsh://system.fsh:86' /> <a href='http://www.facebook.com/sharer.php?u=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Fo%3DSylenvie%26x%3D1385536487'><img src='http://apollo.furcadia.com/cache/7-dt-share-fb.png' /></a> <a href='http://twitter.com/share?text=%23Furcadia%20dream%20-%20Sylenvie&url=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Fo%3DSylenvie%26x%3D1385536487'><img src='http://apollo.furcadia.com/cache/10-dt-share-t-sml.png' /></a> Share this dream with your friends.
]!M16
]}w#############�#
]n$=$'Newsݕ�ሟH(Eventݕ�∟H(SpiceI��䈟H&funVv|#���H&felav|#刟H'talz�v|#爟H(emmieav|#戟H
]N0
```

**Output: Wrong Password**
```
]#xxxx 0 Whoops! The username and password do not match -- please check your spelling.
]]
```
* The server will not accept any new attempts to log in from this session afterwards.

**Output: Banned**
```
#TODO
```

-------------------------------------------------------------------------------

### color
Set the colors of a logging in avatar

**Syntax**
```
color {color_string}
```

**Usage Examples**
```
color w%5K(J;,;;;#;$�#
color w8807C<<(<(1&$�#
```

**Comments**
1. This command only works when logging in!
2. Sponsors can use [chcol](#chcol) to change their colors online.
3. This color code is remembered by the system! From that point on, using a regular Furcadia client to log in will restore these colors!

**Output: Response**
```
]osylenvie
~
]q td2809994990 2809994990   modern
]}w8807C<<(<(1&$�#
]fw8807C<<(<(1&$�#CPU
```
* "sylenvie" is the shortname of the dream owner

-------------------------------------------------------------------------------

### connect
Log into a character (legacy method)

**Syntax**
```
connect {character} {password}
connect {character} {password} {machine_id}
```

**Usage Examples**
```
connect Artex br34k^me!
connect CPU br34k^me!

#TODO machine_id example
```

**Comments**
1. This command is considered #legacy
2. Use the [account](#account) command instead, unless your character is not bound to an account!
3. This command only works when logging in!

**Output: Success**
```
]M% *$�#�k&#)$�#j`&#+$�#ެ%#)$�#��,#/$�$��(#,$�#`T'#*$�#//'#)$�#��'#+$�#��&#,$�#4�.#+$�#s�-#/$�#��&#+$�#�`%#/$�#��+#3$�#�((#.$�#Y+&#*$�#rb'#0$�#��)#/$�#��0#0$�#6l*#4$�#�I)#0#�#�n##*$�#C�&#+$�#��)#\$�#�1(#/$�#v�'#($�#G#%#6$�#��%#3$�#�0)#-$�#aK%#-$�#G�*#($�#YY(#($�#p�*#'#�#}�##)$�#T�&#+$�$[�%#-$�#d�-#*$�#y@%#($�#DP'#)$�#<a&#+$�#��$#1$�#��&#-$�#�1(#-$�#q�,#,$�#��*#)$�#��*#)#�#B�##.$�#��(#,$�#��)#+$�#��&#0$�#X6*#+$�$Y�%#*$�#Ɉ)#-$�#��*#)$�#��%#,$�#ݙ'#/$�#��)#-$�#Q�+#-$�#{�+#*$�#�h%#+$�#��&#($�#P�(#'#�#g�##*$�#�b&#+$�#�b.#)$�#��$#.$�#tn%#+$�#}�'#+$�#f�'#)$�#��%#-$�#�%#)$�#�v&#,$�#��%#*$�#�4&#*$�#2�'#*$�#�/*#)#�#Q�##)$�#5�)#'#�#��##,$�$�A&#-$�#K�(#)$�#�0'#-$�#�'#+$�#��'#,$#&Y4%#*$$%8G(#)$%%`�$#>$&%��%#,$'%7�&#+$(%��)#,$)%Ys&#-$*%�[&#+$+%�()#)$,%I�(#*$-%��&#,$.%2�%#+$/%;�&#($0%_�&#)$1%��/#*$2&U�)#)#2%W�##,$4%��%#+$5%9n'#,$6%��&#($7%�A&#,$8%�&+#.$9%��)#)$:%��)#,$;%��%#-$<%Vg(#*$=%9�&#/$>%��)#/$?%�@0#+$@%��%#)$A&�q)#0$B%��.#+$C%<$'#-$D%c�*#0$E%%V)#)$F%h:*#)$G%Y�%#+$H%Z�-#.$I%�+,#,$J%�,-#*$K%��*#%$L%�1#)$M%})*#'$N%�U-#%$O%$�)#)$P%_�*#'$Q%P�(#)$R%$�1#'$S%��5#'$T%XP+#%$U%��%#'$V%OE)#)$W%�E+#($X%#�*#%$Y%t�(#'$Z%��*#&$[%�x+#&$\&,�'#'$]%��+#&$^%��(#%$_%�M)#&$`%Zj*#&$a%��*#'$b%��)#%$c%��%#'$d%�]6#&$e%��*#)$f%�h&#%$g&�3.#&$h%��(#($i%��*#%$j&�W&#($k%��)#&$l%�y0#)$m%�[)#%$n%D�##%$o%��%#($p%yx(#&$q%f7&#'$r%�W,#'$s%��*#*$t%m9)#&$u%T�*#+$v&b�)#'$w%�j*#'$x%#�*#'$y%�F)#'$z%#�(#%${%��&#%$|%��'#&$}%�g*#&$~&h�%#%$&,b%#&$�%/))#%$�%s�$#%$�%��%#%$�%��6#($�%˂'#%$�%Ņ'#%$�%υ(#'$�%�Q5#($�%}�(#%$�%y�&#%$�%�s)#&$�&u�(#&$�%?�'#%$�%/v(#
&&&&&&&&&&&&&
]k2
]w
]marco 99
]B38245463 CPU
(<font color='success'><img src='fsh://system.fsh:83' alt='@events' /><channel name='@events' /> Event channel on.</font>
(<font color='success'><img src='fsh://system.fsh:82' alt='@news' /><channel name='@news' /> News channel on.</font>
(<font color='success'><img src='fsh://system.fsh:102' alt='@spice' /><channel name='@spice' /> Spice channel on.</font>
(<font color='success'><img src='http://apollo.furcadia.com/cache/400000016.png' /> Talz channel on. Mrrelcome!</font>
^  
%  
]ccmarbled.pcx
(<img src='fsh://system.fsh:86' /> Lines of DragonSpeak: 109
(<img src='fsh://system.fsh:86' /> Dream Standard: <a href='http://www.furcadia.com/standards/'>M16+ Environment</a>
(<img src='fsh://system.fsh:86' /> <a href='http://www.facebook.com/sharer.php?u=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Fo%3DSylenvie%26x%3D1385536487'><img src='http://apollo.furcadia.com/cache/7-dt-share-fb.png' /></a> <a href='http://twitter.com/share?text=%23Furcadia%20dream%20-%20Sylenvie&url=http%3A%2F%2Fwww.furcadia.com%2Fservices%2Flike%2Fdream.php%3Fo%3DSylenvie%26x%3D1385536487'><img src='http://apollo.furcadia.com/cache/10-dt-share-t-sml.png' /></a> Share this dream with your friends.
]!M16
]}w#############�#
]n$=$'Newsݕ�ሟH(Eventݕ�∟H(SpiceI��䈟H&funVv|#���H&felav|#刟H'talz�v|#爟H(emmieav|#戟H
]N0
```

**Output: Wrong Password**
```
]#xxxx 0 Whoops! The username and password do not match -- please check your spelling.
]]
```
* The server will not accept any new attempts to log in from this session afterwards.

-------------------------------------------------------------------------------

### create
Create a new character (OBSOLETE)

**Syntax**
```
create {character} {password} {email} N Y
```

**Usage Examples**
```
create Artex br34k^me! artex@draax.net N Y
```

**Comments**
1. This command is OBSOLETE! It no longer works as specified!
2. Characters are now created via the web!

**Output: Obsolete**
```
N{NAME}You are using an old version of Furcadia. To continue playing, please download the latest version from http://www.furcadia.com.
```

-------------------------------------------------------------------------------

### desc
Temporarily change or set the character's description

**Syntax**
```
desc {description}
```

**Usage Examples**
```
desc Black from snout to tail tip, this average-sized midnight drake seemed barely noticeable among the shadows he lounged in. His scales were of the darkest shade of blue, discernible from pure black only by the keenest of eyes, a pair of large half-folded wings rested above him, casting a shade and protecting the dragon from sunlight. His head was adorned with a pair of black horns - one at each side, with a silvery dark mane starting between them and going down to his tailtip. A silver collar could be seen around his neck, reflecting the light that touches it. His calm posture indicated no sign of hostility.
```

**Comments**
1. This command works after logging in, too!
2. The server does not respond in any way to this command!

-------------------------------------------------------------------------------

### gdlgt
(UNKNOWN)

**Syntax**
```
gdlgt {???}
```

**Usage Examples**
```
#TODO
```

**Comments**
1. INADEQUATELY DOCUMENTED
2. Sent only once by a client, some time after logging in.
3. The server does not respond in any way to this command!

-------------------------------------------------------------------------------

### iamhere
Keepalive string, periodically sent to prevent TCP timeout mechanism from kicking in

**Syntax**
```
iamhere
```

**Comments**
1. Special string sent by the client to keep the TCP session fresh.
2. Without any user interaction, and without this string - the server would time out the connection after 30 minutes, disconnecting the client.
3. In reality, any string would work - not necessarily `iamhere`.
4. The server does not respond in any way to this command!

-------------------------------------------------------------------------------

### ping
Check connection by pinging the server

**Syntax**
```
ping
```

**Output: Response**
```
(Pong.
```

-------------------------------------------------------------------------------

### marco
(UNKNOWN)

**Syntax**
```
marco {num}
```

**Usage Examples**
```
#TODO
```

**Comments**
1. INADEQUATELY DOCUMENTED
2. The server does not respond in any way to this command!
3. Related to [polon](#polon)

-------------------------------------------------------------------------------

### mvrwm
Request a globally unique integer from the server

**Syntax**
```
mvrwm
```

**Comments**
1. PURPOSE UNCLEAR!
2. Response is delivered via the `]{` instruction.
3. The number increments every time __anybody__ uses this command!
4. See similar command: [uid](#uid)

**Output: Response**
```
]{42288111
```

-------------------------------------------------------------------------------

### vascodagama
Notify the server of patch/dream download completion

**Syntax**
```
vascodagama
```

**Comments**
1. Send this command when requested to download a dream package by the server.
2. The server will hold you in "limbo" while you download until this command is provided.

-------------------------------------------------------------------------------

### polon
Response command to `]marco` instruction

**Syntax**
```
polon {num}
```

**Usage Examples**
```
polon 99
polon 1
polon 1-a
```

**Comments**
1. INADEQUATELY DOCUMENTED
2. Server response to this command may vary.
3. Seems to play a part in an old client update procedure (see below).
4. Related to [marco](#marco)

**Transaction Example**
```
polon 99
~
(<font color='notify'>Furcadia has been updated, Beekin dragon will now download you the new update.</font>
]marco 1-a

polon 1-a
]i1UPDATER.EXE
(<font color='warning'>If this auto-update does not work or it works slowly, you can download the update from http://www.furcadia.com/update/</font>
(Sent 0/0 packets, file 1/1.
]hUPDATER.EXE
```

-------------------------------------------------------------------------------

### quit
Disconnect (gracefully) from the server

**Syntax**
```
quit
```

**Comments**
1. The connection closure itself seems to be somewhat unclean: your character will disappear from the game, but the connection itself won't fully close (at least that's what happened when I tested with `netcat`)

-------------------------------------------------------------------------------

### repq
Respond to a server query dialog box (instruction `]#`)

**Syntax**
```
repq {dialog_id} {response}
```

**Usage Examples**
```
#TODO
```

**Comments**
1. Informs the server of a response to a query/dialogbox previously delivered via `]#`.
2. Popular transaction example: buying cookies for DragonScales.
3. Server response to this command highly depends on the query.
4. #TODO Map `{response}` numerics to dialogbox buttons somehow...

-------------------------------------------------------------------------------

### rgate
Request to upload a dream

**Syntax**
```
rgate
```

**Output: Accepted**
```
]u0_11 0 0 
```

**Comments**
1. See related command: [tdgate](#tdgate)

**Output: Rejected**
```
(<font color='error'>You cannot conjure up your dream here.  You can do so in Allegria, Imaginarium, Acropolis, or Furrabia - or on dream pads in some dreams, or almost anywhere in others.</font>
```

-------------------------------------------------------------------------------

### "setemail
Change the e-mail address on the currently logged in character

**Syntax**
```
"setemail {email}
```

**Usage Examples**
```
"setemail artex@draax.net
```

**Comments**
1. The character MUST be fully logged in (i.e., after passing [color][#color] to the server)
2. This command is mostly used to transfer characters between accounts.

**Output: Response**
```
(<font color='success'>Your email address has been changed to <B>artex@draax.net</B>. Within the next hour, you will receive a confirmation email. Please make sure to click on the verification link on it, or go to http://www.furcadia.com/services/confirm/ and enter the password provided. If you do not confirm your email address within a few days, your Furcadia character may be temporarily frozen until you do confirm it.</font>
```

-------------------------------------------------------------------------------

### tdgate
Register a dream portal for a given dream ID (after [rgate](#rgate))

**Syntax**
```
tdgate {id}
```

**Usage Examples**
```
#TODO
```

**Comments**
1. See related command: [rgate](#rgate)

**Output: Accepted**
```
#TODO
```

**Output: Rejected**
```
(<font color='error'>You can't conjure up your map here.</font>
```

-------------------------------------------------------------------------------

### uid
Request a globally unique integer from the server

**Syntax**
```
uid
```

**Comments**
1. PURPOSE UNCLEAR! Unique indexes?
2. Response is delivered via the `]z` instruction.
3. The number increments every time __anybody__ uses this command!
4. See similar command: [mvrwm](#mvrwm)

**Output: Response**
```
]z8479060
```

-------------------------------------------------------------------------------

### version
Report your Furcadia client version to the server

**Syntax**
```
version {version}
```

**Usage Examples**
```
#TODO
```

**Comments**
1. May trigger an update instruction from the server!
2. The server normally does not respond to this command.

-------------------------------------------------------------------------------

### Winver
Report your Windows version to the server

**Syntax**
```
Winver {version}
```

**Usage Examples**
```
#TODO
```

**Comments**
1. The server normally does not respond to this command.


---------------------------------------------------------------------------------------------------

## Beekin Commands
| Command                | Description                                                              |
| ---------------------- | ------------------------------------------------------------------------ |
| bb                     | #legacy Join the Beekin channel (see [jg](#jg))                          |
| chat {message}         | Send a message to the beekin channel (see [chat](#chat))                 |
| claim {name}           | Claim a help request (also `c {name}`)                                   |
| clear {name}           | Clear a help request from the queue                                      |
| isbeek {name}          | Display beekin access level for a specific furre                         |
| jg {group}             | Join a specific beekin group (see [jg](#jg))                             |
| leave                  | Leave current beekin group (see [leave](#leave))                         |
| "list                  | #obsolete List the available beekin commands                             |
| listf                  | List furres requesting help and beekins on-duty (see [listf](#listf))    |
| ob                     | #legacy Join the Guardians channel (see [jg](#jg))                       |
| onduty                 | List how many beekins are currently in beekin groups                     |
| que                    | Show queued help requests in the current beekin channel                  |
| sendb {name} {comment} | Send a furre to the Bugge Hunters channel                                |
| sendd {name} {comment} | Send a furre to the Dream (Mason, Pixel, Scribe) channel                 |
| sendg {name} {comment} | Send a furre to the Guardians channel                                    |
| sendh {name} {comment} | Send a furre to the Helpers channel                                      |
| sendw {name} {comment} | Send a furre to the Welcomers channel                                    |
| transb {name}          | Transfer existing help request to the Bugge Hunters channel              |
| transd {name}          | Transfer existing help request to the Dream channel                      |
| transg {name}          | Transfer existing help request to the Guardians channel                  |
| transh {name}          | Transfer existing help request to the Helpers channel                    |
| transw {name}          | Transfer existing help request to the Welcomers channel                  |
| tellgroup {text}       | Send a message to all beekin group members (see [tellgroup](#tellgroup)) |
| telltrainees {text}    | Tell something to all the beekin trainees                                |

> **CONFIDENTIALITY NOTE**
> 
> While beekin and staff commands are considered to be confidential, and are unlikely to be featured in this file, the commands above have been circulating in public documentation for at least two decades! As such - they are "fair game".
> 
> Please don't expand the "Beekin Commands" section without your information having a provable clearance from DEP or some form of proof that the information is public, or has been obtained from public sources (e.g., code, public conversation logs, Furcadia website or other documentation sources)!
