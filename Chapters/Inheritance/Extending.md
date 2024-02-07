## Extending superclass behavior
	ifFalse: [ parent printOn: aStream ].
aStream << name
	parent isNil 
		ifFalse: [ parent printOn: aStream ].
	aStream << name.
	aStream << '/'
	parent isNil 
		ifFalse: [ parent printOn: aStream ].
	aStream << name
	parent isNil 
		ifFalse: [ parent printOn: aStream ].
	aStream << name
	parent isNil 
		ifFalse: [ parent printOn: aStream ].
	aStream << name.
	aStream << '/'
	self printOn: aStream.
	aStream << '/'
p := MFDirectory new name: 'comics'.
el1 := MFFile new name: 'babar'; contents: 'Babar et Celeste'.
p addElement: el1.
el2 := MFFile new name: 'astroboy'; contents: 'super cool robot'.
p addElement: el2.
String streamContents: [:s | p printOn: s ]
	super printOn: aStream.
	aStream << '/'
p := MFDirectory new name: 'comics'.
el1 := MFFile new name: 'babar'; contents: 'Babar et Celeste'.
p addElement: el1.
el2 := MFFile new name: 'astroboy'; contents: 'super cool robot'.
p addElement: el2.
String streamContents: [:s | p printOn: s ]
	| sum |
	sum := 0.
	files do: [ :each | sum := sum + each size ].
	sum := sum + name size.
	sum := sum + 2.
	^ sum
	^ contents size + name size
	^ name size
	^ contents size + super size
	| sum |
	sum := 0.
	files do: [ :each | sum := sum + each size ].
	sum := sum + super size.
	sum := sum + 2.
	^ sum
	^ super == self
>>> true
>>> ...
C new bar
>>> ...
D new bar
>>> ...
>>> 10
C new bar
>>> 20
D new bar
>>> 100