---
classification: public
---

INI - Character File
===============================================================================

Overview
-------------------------------------------------------------------------------
Character (.ini) files contain login credentials, and other information on a
single Furcadia character. Such files can be used to make the Furcadia client
log into a character directly (rather than going through an account).

It is considered a legacy login method, as characters are grouped by their
account, and by default no longer have a password assigned to them, but it is
possible to have a password assigned through the
[Change lost password](https://www.furcadia.com/services/pw/oblivion.php4)
service if you really wish to do so.


Location
-------------------------------------------------------------------------------

Character .ini files can be stored under the following paths:

| OS         | Path                                                                                                                                                       |
| ---------- | -----------------------------------------------------------------------------------------------------------------------------------------------------------|
| XP         | c:\Documents and Settings\\`username`\\My Documents\Furcadia\Furcadia Characters\\`name`.ini<br>c:\Program Files\Furcadia\\`name`.ini                      |
| Vista+     | c:\Users\\`username`\\Documents\Furcadia\Furcadia Characters\\`name`.ini<br>c:\Program Files (x86)\Furcadia\\`name`.ini                                    |
| Linux/Wine | ~/.wine/drive_c/windows/profiles/`$USER`/My\ Documents/Furcadia/Furcadia Characters/`name`.ini<br>~/.wine/drive_c/Program\ Files (x86)/Furcadia/`name`.ini |

> Note: `name` can be any name you choose, so long as the suffix at the end of
>       the file is `.ini`. The client does not take it into consideration when
>       displaying the character list.


File Format / Syntax
-------------------------------------------------------------------------------

### Example (V3.0)
```ini
V3.0 character
Colors=t%5K(J;,;;;$%ø
Name=Artex
Password=
Desc=Here be description [<a href=draax.net/artex>Info</a>] &laquo;Example&raquo;
Logins=7700
LastLogin=1287669722
AutoResponse=0
AutoResponseMessage=Thank you for whispering! This is my automatic response message. #SA
AFKTime=100
AFKMessage=[<B>AUTO</B>] User is idle or not available: <I>[afkreason]</I> (<B>[afkhours]h [afkminutes]m</B>)
AFKDescription=[#SP] [afkreason] (<B>[afkhours]h [afkminutes]m</B>)
AFKPortrait=3
DefaultPortrait=2
AFKDisconnectTime=0
```

### Example (V2.0)
```ini
V2.0 character
Colors=t%+68%@81-5%%$
Name=CPU
Password=MuhPassword
Desc=//Central Processing Unit//
Logins=4
LastLogin=1202209092
```

### Parameters

| Parameter           | Example              | Ver. | Comment                                |
|---------------------|----------------------|------|----------------------------------------|
| Colors              | `t%5K(J;,;;;$%ø`     | V1.0 | Character colors                       |
| Name                | Artex                | V1.0 | Character name                         |
| Password            | abc123               | V1.0 | Character password (not account!)      |
| Desc                | Here be description! | V2.0 | Description (set upon login)           |
| Logins              | 7700                 | V2.0 | Login counter (set by client)          |
| LastLogin           | 1287669722           | V2.0 | Last login time (UNIX time)            |
| AutoResponse        | 0                    | V3.0 | (0 or 1) Enable whisper auto-response? |
| AutoResponseMessage | Rawr!                | V3.0 | Response whisper (if AutoResponse=1)   |
| AFKTime             | 100                  | V3.0 | Amount of minutes before setting AFK   |
| AFKMessage          | User is idle         | V3.0 | AFK auto-response whisper message      |
| AFKDescription      | [#SP] [afkreason]    | V3.0 | AFK character description              |
| AFKPortrait         | 3                    | V3.0 | AFK portrait index                     |
| DefaultPortrait     | 2                    | V3.0 | Portrait index when existing AFK mode  |
| AFKDisconnectTime   | 0                    | V3.0 | Amount of minutes until disconnect     |

#### Placeholders
The **AFKMessage** and **AFKDescription** parameters support the following
placeholders:
* `[afkreason]`  - the reason fed into the AFK command
* `[afkhours]`   - amount of hours spent away
* `[afkminutes]` - (0..59) amount of minutes spent away 
