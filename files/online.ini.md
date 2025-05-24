---
classification: public
---

# online.ini - Pounce Data File
## Location
Pounce stores all its information on disk in a single file called `online.ini`.
It can be found in the following paths:

| OS         | Path                                                                                                           |
| ---------- | -------------------------------------------------------------------------------------------------------------- |
| XP         | %USERPROFILE%\Local Settings\Application Data\Dragon’s Eye Productions\Furcadia\                               |
| Vista+     | %USERPROFILE%\AppData\Local\Dragon’s Eye Productions\Furcadia\                                                 |
| Linux/Wine | ~/.wine/drive_c/windows/profiles/$USER/Local\ Settings/Application\ Data/Dragon\’s\ Eye\ Productions/Furcadia/ |

## Update Procedure
Pounce updates the data file under following conditions:
* On exit – when Pounce is told to close
* When the player list is modified. This includes:
  * Adding/Removing a new player, dream or group to the list
  * Changing the settings of an existing player/dream/group
* Possibly after a certain amount of time (*UNVERIFIED*)

Temporary entries such as “unknown” furres or visited dreams (with an orange
question mark icon) are not saved to the data file and disappear within the
hour from their addition, or when Pounce is closed.

## File Format / Syntax
```
FurcadiaOn  1.00
ShowOffline 1
ShowOnline  1
ShowUnknown 0
ShowUploadedDreams  1
ShowOfflineDreams   1   
ShowBookmarkedDreams    1   
ShowVisitedDreams   1   
ShowChat    1   
ShowBcast   1   
Sounds  0
WindowPos   1693    39  1924    556 1
Furre   Albert Quirky       1   0   0   1   1738672645  artex   0   
Furre   Ezoa        1   0   0   1   1731499744  artex   0   
Furre   Kiryu Vetra     1   0   1   1   1738693824  artex   0   
Dream   furc://bramblebrook:        1   0   0       0
Group   Recent  1   2   
```
* `online.ini` is a TSV-like non-tabular text file:
  * items in every line are separated by a TAB character (`\t`, 0x09); but
  * the file IS NOT a table
* Each line ends with the `\r\n` (0x0d 0x0a) combination
* First line serves as a magic number and specifies its version

-------------------------------------------------------------------------------

### Section: Pounce Configuration
* `FurcadiaOn	1.00` - magic number & format version
* `ShowOffline	0|1`
  * Show offline furres in the Pounce list? (0 = Hide / 1 = Show)
* `ShowOnline	0|1`
  * Show online furres in the Pounce list? (0 = Hide / 1 = Show)
* `ShowUnknown	0|1`
  * Show temporarily saved furres in the list? (0 = Hide / 1 = Show)
* `ShowUploadedDreams	0|1`
  * Show uploaded (online) dreams in the Pounce list? (0 = Hide / 1 = Show)
* `ShowOfflineDreams	0|1`
  * Show unavailable (offline) dreams in the Pounce list? (0 = Hide / 1 = Show)
* `ShowBookmarkedDreams	0|1`
  * Show bookmarked (online or offline) dreams in the list? (0 = Hide / 1 = Show)
* `ShowVisitedDreams	0|1`
  * Show recently visited (recent) dreams in the Pounce list? (0 = Hide / 1 = Show)
* `Sounds	0|1`
  * Toggle Pounce sounds (online/offline/chat) (0 = Off / 1 = On)
* `WindowPos	<X1>	<Y1>	<X2>	<Y2>	<ShowOnLoad>`
  * **X1** / **Y1** - (coordinates) upper-left corner of the Pounce window
  * **X2** / **Y2** - (coordinates) lower-right corner of the Pounce window
  * **ShowOnLoad**
    * `0` - keep Pounce in tray on startup until opened by the user
    * `1` - show the Pounce window on startup

### Section: Furre List
```
Furre <DisplayName> <Note> <SLI> <SLO> <SS> <SW> <LastSeen> <LC> <GroupID>
```
* **DisplayName** - furre's display name; may contain regular space characters
* **Note** - optional note about the furre (usually empty)
* **SLI** (Sound on Log In) - play a sound when furre logs in? (0 = No / 1 = Yes)
* **SLO** (Sound on Log Out) - play a sound when furre logs out? (0 = No / 1 = Yes)
* **SS** (Sound on Speech) - play a sound when furre says something? (0 = No / 1 = Yes)
* **SW** (Sound on Whisper) - play a sound when furre whispers you? (0 = No / 1 = Yes)
* **LastSeen** - UNIX timestamp of when the furre was last seen (0 = Never)
* **LC** (Last Contact) - shortname of the last furre (on this machine) to
    whisper them, or receive a whisper from them. Empty if this furre was never
	whispered or vice-versa.
* **GroupID** - ID of the Pounce group this furre belongs to (0 = No Group)

### Section: Dream List
```
Dream <DreamUrl> <Note> <SUP> <SDN> <LastSeen> <LC> <GroupID>
```
* **DreamURL** - dream URL; always starts with `furc://`
* **Note** - optional note about the dream (usually empty)
* **SUP** (Sound when Up) - play a sound when the dream goes up? (0 = No / 1 = Yes)
* **SDN** (Sound when Down) - play a sound when the dream goes down? (0 = No / 1 = Yes)
* **LastSeen** - UNIX timestamp of when the dream was last seen up (0 = Never)
* **LC** (Last Contact?) - (*UNCLEAR*)
  * possibly related to the `Furre` record syntax
  * always empty?
* **GroupID** - ID of the Pounce group this dream belongs to (0 = No Group)

### Section: Group List
```
Group <GroupName> <GroupID> <GroupState>
```
* **GroupName** - name of the group
* **GroupID** - unique ID number of this group that represent it in the `Furre` and `Dream` records.
  * the number starts from 1 and goes up
  * ID 0 is reserved to "No Group" and cannot be used
* **GroupState** - the state that this group should be in when Pounce starts
  * (0 = ??? / 1 = Collapsed / 2 = Expanded)
