## Fun with Capchas \(not used for now\)
-> 
'grof'
--> 4
-> $f
s := 'frog'.
s at: 1 put: $z.
s
-> zrog
	to: 'frog' size 
	do: [ :i | Transcript show: ('frog' at: i) ; cr ]
sourceString := 'frog'.
targetString := String new: sourceString size.

1 to: targetString size do: [ :i | 
	targetString at: (sourceString size + 1) - i put: (sourceString at: i)
	].
targetString

	| targetString |
	targetString := String new: self size.

	1 to: targetString size do: [ :i | 
		targetString at: (self size + 1) - i put: (self at: i)
		].
	^ targetString
-> 'ipuoy'

	| targetString n |
	targetString := String new: self size.
	n := (self size + 1).
	1 to: targetString size do: [ :i | 
		targetString at: n - i put: (self at: i)
		].
	^ targetString
	]]]

Now looking at how it is implemented in Pharo we see the following definition defined in the superclass of ==String==.


[[[
SequenceableCollection>>reversed
	"Answer a copy of the receiver with element order reversed."
	"Example: 'frog' reversed"

	| n result src |
	n := self size.
	result := self species new: n.
	src := n + 1.
	1 to: n do: [:i | result at: i put: (self at: (src := src - 1))].
	^ result
-> 
'civic'
	"Returns true whether the receiver is an anagram.
	'anna' captchaIsAnagram
		true
	'andna' captchaIsAnagram 
		true
	'avdna' captchaIsAnagram 
		false
	"
	1 
		to: self size//2 
		do: [ :i | (self at: i) = (self at: self size + 1 - i)
						ifFalse: [ ^false ]
				].
	^true
	"Returns true whether the receiver is an anagram.
	'anna' captchaIsAnagram
		true
	'andna' captchaIsAnagram 
		true
	'avdna' captchaIsAnagram 
		false
	"
	| n |
	n := self size + 1.
	1 
		to: self size//2 
		do: [ :i | 
			( self at:  i ) = ( self at:  n - i)
				ifFalse: [ ^false ]
				].
	^true