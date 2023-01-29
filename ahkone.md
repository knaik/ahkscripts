```
; AHK v2 forced me to clean up some scripts but fast speed created, essentially race conditions before I figured out proper way to manage refernces
; & ref var operator is what I was misunderstanding for hours
; script directory shouldn't be used and doesn't matter, cmd working directory specified via var

#SingleInstance Off ;not 100$ sure if necessary 
#Warn All, Off

; script needs to make var called "complete" from parameters and clipboard that will be passed later


directory = // starting script/ it a cd so I know where it starts and /K to keep window open
Run A_ComSpec directory ,,, &cmd_pid ; capturing pid !!!!!

;Pause ;debug/can remove

WinWait "ahk_pid " cmd_pid ;"ahk_exe cmd.exe" ;wait for process to exist
WinActivate ;activates only process created from win wait. before proper cmd_pid was specified, only caputred first created cmd instance
; even when newer instances were made, don't understand how priority was assigned
; PID numbers created randomly, title was eqivalent when using comspec, PID/AHKPID not assigned or incremented to respect chronological instance creations

SendInput complete ; complete  is a previously concated string built using clipboard contents so each instance will be unique
Send "{Enter}" ; easy to toggle and sendinput expects raw, not 100% if enter key can be sent via SendInput ? ;; potentially good to refractor?
```

Need better but I don't want to look at this anymore today, spent 4 hours migrating all AHK scripts to v2 ☠☠

ptrs and * and % and &
