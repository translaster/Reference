# AGI Commands
## Asterisk 14 AGICommand_answer
**ANSWER**
### Synopsis
Answer channel
### Description
Answers channel if not already in answer state. Returns -1 on channel failure, or 0 if successful.
### Syntax
```
ANSWER
```
**Arguments**
### See Also
[Asterisk 14 AGICommand_hangup](Asterisk-14-AGICommand_hangup)

## Asterisk 14 AGICommand_asyncagi break
**ASYNCAGI BREAK**
### Synopsis
Interrupts Async AGI
### Description
Interrupts expected flow of Async AGI commands and returns control to previous source (typically, the PBX dialplan).
### Syntax
```
ASYNCAGI BREAK
```
**Arguments**
### See Also
[Asterisk 14 AGICommand_hangup]

## Asterisk 14 AGICommand_channel status
**CHANNEL STATUS**
### Synopsis
Returns status of the connected channel.
### Description
Returns the status of the specified channelname. If no channel name is given then returns the status of the current channel.
Return values:
* `0` - Channel is down and available.
* `1` - Channel is down, but reserved.
* `2` - Channel is off hook.
* `3` - Digits (or equivalent) have been dialed.
* `4` - Line is ringing.
* `5` - Remote end is ringing.
* `6` - Line is up.
* `7` - Line is busy.
### Syntax
```
CHANNEL STATUS CHANNELNAME
```
**Arguments**
channelname
### See Also

## Asterisk 14 AGICommand_control stream file
**CONTROL STREAM FILE**
### Synopsis
Sends audio file on channel and allows the listener to control the stream.
### Description
Send the given file, allowing playback to be controlled by the given digits, if any. Use double quotes for the digits if you wish none to be permitted. If offsetms is provided then the audio will seek to offsetms before play starts. Returns 0 if playback completes without a digit being pressed, or the ASCII numerical value of the digit if one was pressed, or -1 on error or if the channel was disconnected. Returns the position where playback was terminated as endpos.
It sets the following channel variables upon completion:
* `CPLAYBACKSTATUS` - Contains the status of the attempt as a text string
  - SUCCESS
  - USERSTOPPED
  - REMOTESTOPPED
  - ERROR
* CPLAYBACKOFFSET - Contains the offset in ms into the file where playback was at when it stopped. -1 is end of file.
* CPLAYBACKSTOPKEY - If the playback is stopped by the user this variable contains the key that was pressed.
### Syntax
```
CONTROL STREAM FILE FILENAME ESCAPE_DIGITS SKIPMS FFCHAR REWCHR PAUSECHR OFFSETMS
```
**Arguments**
* filename - The file extension must not be included in the filename.
* escape_digits
* skipms
* ffchar - Defaults to #
* rewchr - Defaults to *
* pausechr
* offsetms - Offset, in milliseconds, to start the audio playback
### See Also

## Asterisk 14 AGICommand_database del
**DATABASE DEL**
### Synopsis
Removes database key/value
### Description
Deletes an entry in the Asterisk database for a given family and key.
Returns `1` if successful, `0` otherwise.
### Syntax
```
DATABASE DEL FAMILY KEY
```
**Arguments**
* family
* key
### See Also

## Asterisk 14 AGICommand_database deltree
**DATABASE DELTREE**
### Synopsis
Removes database keytree/value
### Description
Deletes a family or specific keytree within a family in the Asterisk database.
Returns `1` if successful, `0` otherwise.
### Syntax
```
DATABASE DELTREE FAMILY KEYTREE
```
**Arguments**
* family
* keytree
### See Also
