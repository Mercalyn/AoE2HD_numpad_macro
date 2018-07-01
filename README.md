# AoE2HD_numpad_macro
USE VIEW RAW


SetBatchLines, -1 ; Waiting-time script does not need to run super fast
defSleep := 20
longSleep := 40
lastKey := ""
autoTimeout := 0

; loop encompasses all except for exit
loop {
	;autotimeout section to reset last keydown
	if(autoTimeout > 200){
		lastKey := ""
		autoTimeout := 0
	}
	autoTimeout++

	; fast click, this one is getkeystate because that detects keydown while the :: detects only keyup
	if GetKeyState("Numpad0", "P"){
		if GetKeyState("a", "P"){
			lastKey := "a"
		}
		if GetKeyState("s", "P"){
			lastKey := "s"
		}
		if GetKeyState("d", "P"){
			lastKey := "d"
		}
		if GetKeyState("f", "P"){
			lastKey := "f"
		}
		if GetKeyState("g", "P"){
			lastKey := "g"
		}
		;it needs to do it this way, if it tries to send the key while anything other than numpad0 is held, it won't repeat
		send {%lastKey%}
	}
	continue
	
	Numpad0::
	if GetKeyState("a", "P"){
		send {a}
	}
	continue
	
	; stag defense
	Numpad1::
	send {c}
	sleep, %defSleep%
	send {s}
	continue
	
	; build lumber
	Numpad4::
	send {a}
	sleep, %defSleep%
	send {r}
	continue
	
	; build house array
	Numpad5::
	MouseGetPos, xpos, ypos
	send {a}
	sleep, %defSleep%
	send {q}
	loop, 20{
		send +{LButton}
		xpos -= 36
		ypos += 18
		MouseMove, xpos, ypos
	}
	continue
	
	; build mining
	Numpad6::
	send {a}
	sleep, %defSleep%
	send {e}
	continue
	
	; build palisade
	Numpad7::
	send {s}
	sleep, %defSleep%
	send {s}
	continue
	
	; build farm
	Numpad8::
	send {a}
	sleep, %defSleep%
	send {a}
	continue
	
	; build mill
	Numpad9::
	send {a}
	sleep, %defSleep%
	send {w}
	continue

	;sleep, %defSleep%
	return
}

Numpad3::exitapp




