# Asterisk 14 Dialplan Applications

## ChanSpy()
### Synopsis
Слушать канал и опционально шептать в него.
### Описание
Это приложение используется для прослушивания аудио с канала Asterisk. Оно включает в себя звук входящий и исходящий из канала, на котором ведется прослушка. Если указан параметр `chan prefix`, то будут отслеживаться только каналы, начинающиеся с этой строки.
Во время прослушивания могут быть выполнены следующие действия:
* При наборе `#` уровень громкости изменяется.
* Набрав `*` вы перестанете шпионить и будете искать другой канал для слежки.
* Набор серии цифр, за которыми следует `#` создает имя канала для добавления к `chanprefix`. Например, выполнение ChanSpy(Agent) и
затем набрав цифры '1234#', в то время как шпионаж начнет шпионить за каналом 'Agent/1234'. Обратите внимание, что эта функция будет переопределена, если используются опции 'd' или 'u'.

Примечание
Опция _X_ заменяет три функции выше в том, что если допустимое одноразрядное расширение существует в правильном контексте, ChanSpy выйдет из него. Это также отключает выбор канала на основе `chanprefix` и последовательности цифр.

### Синтаксис
```
ChanSpy([chanprefix,[options]])
```
#### Аргументы
* chanprefix
* options
  - b - Только прослушивать каналы, участвующие в вызове.
  - B - вместо того, чтобы шептать одному каналу, говорить в оба канала, участвующих в вызове.
  - c
    - digit - Укажите цифру DTMF, которая может использоваться для слежки за следующим доступным каналом.
  - d - Переопределить типичные функции числового DTMF и вместо того, чтобы использовать DTMF для переключения между режимами шпионажа.
    - 4 - режим шпионажа
    - 5 - режим шопота
    - 6 - режим "врывания"
  - e - Enable enforced mode, so the spying channel can only monitor extensions whose name is in the ext : delimited list.
    - ext
  - E - Exit when the spied-on channel hangs up.
  - g
    - grp - Only spy on channels in which one or more of the groups listed in grp matches one or more groups from the `SPYGROUP` variable set on the channel to be spied upon.
  - l - Allow usage of a long queue to store audio frames.
  - n - Say the name of the person being spied on if that person has recorded his/her name. If a context is specified, then that voicemail context will be searched when retrieving the name, otherwise the default context be used when searching for the name (i.e. if SIP/1000 is the channel being spied on and no mailbox is specified, then 1000 will be used when searching for the name).
    - mailbox
    - context
  - o - Only listen to audio coming from this channel.
  - q - Don't play a beep when beginning to spy on a channel, or speak the selected channel name.
  - r - Record the session to the monitor spool directory. An optional base for the filename may be specified. The default is `chanspy`.
    - basename
  - s - Skip the playback of the channel type (i.e. SIP, IAX, etc) when speaking the selected channel name.
  - S - Stop when no more channels are left to spy on.
  - u - The chanprefix parameter is a channel uniqueid or fully specified channel name.
  - v - Adjust the initial volume in the range from -4 to 4. A negative value refers to a quieter setting.
    - `value`
  - w - Enable whisper mode, so the spying channel can talk to the spied-on channel.
  - W - Enable private whisper mode, so the spying channel can talk to the spied-on channel but cannot listen to that channel.
  - x
    - digit - Specify a DTMF digit that can be used to exit the application while actively spying on a channel. If there is no channel being spied on, the DTMF digit will be ignored.
  - X - Allow the user to exit ChanSpy to a valid single digit numeric extension in the current context or the context specified by the `SPY_EXIT_CONTEXT` channel variable. The name of the last channel that was spied on will be stored in the SPY_CHANNEL variable.

### Смотри также

[Asterisk 14 Application_ExtenSpy](#ExtenSpy)

[Asterisk 14 ManagerEvent_ChanSpyStart](ami_events.md#chanspystart)

[Asterisk 14 ManagerEvent_ChanSpyStop](ami_events.md#chanspystop)
