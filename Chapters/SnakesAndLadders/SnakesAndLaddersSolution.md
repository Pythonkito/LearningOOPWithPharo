## Snake and ladder solutions

	tiles := Array new: aNumber.
	1 to: aNumber do: [ :i |
		tiles at: i put: (SLTile new position: i) ]
	
	^ tiles size

	^ tiles at: aNumber
	name := aString
	instanceVariableNames: 'position players'
	classVariableNames: ''
	package: 'SnakesAndLadders'
	players := OrderedCollection new. 
	players add: aPlayer
	^ players
	aStream << '<' << name << '>'
	^ players includes: aPlayer
	^ position
	position := anInteger
	instanceVariableNames: 'name position'
	classVariableNames: ''
	package: 'SnakesAndLadders'
	aPlayer position: 1.
	(tiles at: 1) addPlayer: aPlayer
	
	^ self tileAt: (aPlayer position + aNumber)
	^ tiles at: aSLPlayer position
	players remove: aPlayer
	| targetTile | 
	targetTile := self tileFor: aPlayer atDistance: anInteger.
	(self tileOfPlayer: aPlayer) removePlayer: aPlayer.
	targetTile addPlayer: aPlayer. 
	aPlayer position: targetTile position. 

	aStream << '['.
	self printInsideOn: aStream.
	aStream << ']'	

	super printInsideOn: aStream.
	aStream << '->'.
	targetTile position printOn: aStream

	tiles 
		at: aSourcePosition 
		put: (SLSnakeTile new 
				position: aSourcePosition; 
				to: (tiles at: aTargetPosition) ; yourself)

	tiles 
		at: aSourcePosition 
		put: (SLLadderTile new 
				position: aSourcePosition ; 
				to: (tiles at: aTargetPosition) ; yourself)
	targetTile acceptPlayer: aPlayer
	instanceVariableNames: 'tiles players turn'
	classVariableNames: ''
	package: 'SnakesAndLadders'
	players := OrderedCollection new. 
	turn := 0

	^ players anySatisfy: [ :each | each position = tiles size ]
	"We can only move if we stay within the game.
	This implies that the player should draw an exact number to land on the finish tile."
	
	^ aNumber <= tiles size