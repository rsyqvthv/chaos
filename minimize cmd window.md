# minimize cmd window

[windows - How do I minimize the command prompt from my bat file - Stack Overflow](https://stackoverflow.com/questions/9232308/how-do-i-minimize-the-command-prompt-from-my-bat-file)

# start with /min

`start /min C:\Ruby192\bin\setrbvars.bat`

# powershell 

`powershell -window minimized -command "" `

Also `-window hidden` and `-window normal` is available to hide completely or restore.

# cmd /c start

`cmd.exe /c start /min myfile.bat ^& exit `

the `cmd.exe` is needed as start is no windows command that can be executed outside a batch

`/c` = exit after the start is finished

the `^& exit` part ensures that the window closes even if the batch does not end with `exit`

However, the initial cmd is still not minimized.

Only way that worked for me to start a batch file minimized via Windows Task Scheduler.
