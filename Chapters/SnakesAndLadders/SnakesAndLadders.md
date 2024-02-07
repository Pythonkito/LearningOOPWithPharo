## Snakes and ladders
game := SLGame new tileNumber: 12.
game 
	setLadderFrom: 2 to: 6;
	setLadderFrom: 7 to: 9;
	setSnakeFrom: 11 to: 5.
game 
	addPlayer: (SLPlayer new name: 'Jill');
	addPlayer: (SLPlayer new name: 'Jack'). 
game play
<Jill>throws 3: [1<Jack>][2->6][3][4<Jill>][5][6][7->9][8][9][10][5<-11][12]
<Jack>throws 6: [1][2->6][3][4<Jill>][5][6][7->9][8][9<Jack>][10][5<-11][12]
<Jill>throws 5: [1][2->6][3][4][5][6][7->9][8][9<Jack><Jill>][10][5<-11][12]
<Jack>throws 1: [1][2->6][3][4][5][6][7->9][8][9<Jill>][10<Jack>][5<-11][12]
<Jill>throws 3: [1][2->6][3][4][5][6][7->9][8][9][10<Jack>][5<-11][12<Jill>]
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'SnakesAndLadders'

	| game |
	game := SLGame new tileNumber: 12.
	self assert: game tileNumber equals: 12
	instanceVariableNames: 'tiles'
	classVariableNames: ''
	package: 'SnakesAndLadders'
	tiles := aNumber
	^ tiles

	| game |
	game := SLGame new tileNumber: 12.
	self 
		assert: game printString 
		equals: '[1][2][3][4][5][6][7][8][9][10][11][12]'
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'SnakesAndLadders'
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'SnakesAndLadders-Test'

	| tile |
	tile := SLTile new position: 6.
	self assert: tile printString equals: '[6]'

	aStream << '['.
	position printOn: aStream.
	aStream << ']'

	tiles do: [ :aTile | 
		aTile printOn: aStream ]
	... Your code ...

	| game |
	game := SLGame new tileNumber: 12.
	self assert: (game tileAt: 6) printString equals: '[6]'
	... Your code ...

	| game jill |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. 
	self assert: ((game tileAt: 1) players includes: jill).
	instanceVariableNames: 'name'
	classVariableNames: ''
	package: 'SnakesAndLadders'
	(tiles at: 1) addPlayer: aPlayer
	...  Your code ...
	... Your code ...

	| game jill jack |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	jack := SLPlayer new name: 'Jack'.
	game addPlayer: jill.
	game addPlayer: jack.
	self assert: ((game tileAt: 1) players includes: jill).
	self assert: ((game tileAt: 1) players includes: jack).

	| game jill |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. 
	self assert: ((game tileAt: 1) players includes: jill).
	... Your code ...

	| game jill |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. 
	self assert: ((game tileAt: 1) includesPlayer: jill).

	| game jill jack |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	jack := SLPlayer new name: 'Jack'.
	game addPlayer: jill.
	game addPlayer: jack.
	self assert: ((game tileAt: 1) includesPlayer: jill).
	self assert: ((game tileAt: 1) includesPlayer: jack).
game := SLGame new tileNumber: 12.
jill := SLPlayer new name: 'Jill'.
jack := SLPlayer new name: 'Jack'.
game addPlayer: jill.
game addPlayer: jack.
game 

	| game jill jack |
	game := SLGame new tileNumber: 12.
	jack := SLPlayer new name: 'Jack'.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. "first player" 
	game addPlayer: jack. 
	self 
		assert: game printString 
		equals: '[1<Jill><Jack>][2][3][4][5][6][7][8][9][10][11][12]'
	... Your code ...
	aStream << '['.
	position printOn: aStream.
	players do: [ :aPlayer | aPlayer printOn: aStream ].
	aStream << ']'
	
	| jill game |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. 
	self assert: (game tileFor: jill atDistance: 4) position equals: 5.

	| game jill |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill.
	self assert: jill position equals: 1.
	... Your code ...
	... Your code ...
	
	| jill game |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. 
	self assert: (game tileOfPlayer: jill) position equals: 1.
	... Your code ...
	
	| jill game |
	game := SLGame new tileNumber: 12.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. 
	game movePlayer: jill distance: 4.
	self assert: jill position equals: 5.
	self assert: (game tileAt: 1) players isEmpty.
	self assert: ((game tileAt: 5) includesPlayer: jill).
	... Your code ...
	... Your code ...
	| targetTile |
	targetTile := self tileFor: aPlayer atDistance: anInteger.
	(self tileOfPlayer: aPlayer) removePlayer: aPlayer.
	targetTile addPlayer: aPlayer.
	aPlayer position: targetTile position.
	instanceVariableNames: 'position'
	classVariableNames: ''
	package: 'SnakesAndLadders'
	aStream << '['.
	position printOn: aStream.
	aStream << ']'
	instanceVariableNames: 'players'
	classVariableNames: ''
	package: 'SnakesAndLadders'
	instanceVariableNames: 'targetTile'
	classVariableNames: ''
	package: 'SnakesAndLadders'
	targetTile := aTile
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'SnakesAndLadders'

	aStream << '['.
	targetTile position printOn: aStream. 
	aStream << '<-'.
	position printOn: aStream.
	aStream << ']'
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'SnakesAndLadders'

	aStream << '['.
	position printOn: aStream.
	aStream << '->'.
	targetTile position printOn: aStream.
	aStream << ']'

	| tile |
	tile := SLLadderTile new position: 2; to: (SLTile new position: 6). 
	self assert: tile printString equals: '[2->6]'

	| tile |
	tile := SLSnakeTile new position: 11; to: (SLTile new position: 5). 
	self assert: tile printString equals: '[5<-11]'

	aStream << '['.
	position printOn: aStream.
	players do: [ :aPlayer | aPlayer printOn: aStream ].
	aStream << ']'

	aStream << '['.
	position printOn: aStream.
	aStream << '->'.
	targetTile position printOn: aStream.
	aStream << ']'

	position printOn: aStream
	... Your code ...

	super printInsideOn: aStream.
	players do: [ :aPlayer | aPlayer printOn: aStream ].
	... Your code ...
	... Your code ...

	targetTile position printOn: aStream. 
	aStream << '<-'.
	super printInsideOn: aStream

	| game |
	game := SLGame new tileNumber: 12.
	game
		setLadderFrom: 2 to: 6;
		setLadderFrom: 7 to: 9;
		setSnakeFrom: 11 to: 5.
	self 
		assert: game printString 
		equals: '[1][2->6][3][4][5][6][7->9][8][9][10][5<-11][12]'
	... Your code ...
	... Your code ...
	| targetTile |
	targetTile := self tileFor: aPlayer atDistance: anInteger.
	(self tileOfPlayer: aPlayer) removePlayer: aPlayer.
	targetTile addPlayer: aPlayer.
	aPlayer position: targetTile position.
	self addPlayer: aPlayer.
	aPlayer position: position.
	self removePlayer: aPlayer
	| targetTile |
	targetTile := self tileFor: aPlayer atDistance: anInteger.
	(self tileOfPlayer: aPlayer) releasePlayer: aPlayer.
	targetTile acceptPlayer: aPlayer.
	aPlayer position: position
	super acceptPlayer: aPlayer.
	self addPlayer: aPlayer
	"Do nothing by default, subclasses may modify this behavior."
	
	| jill game |
	game := SLGame new
			tileNumber: 12;
			setLadderFrom: 2 to: 6;
			setLadderFrom: 7 to: 9;
			setSnakeFrom: 11 to: 5.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill.
	game movePlayer: jill distance: 10.
	self assert: jill position equals: 5.
	self assert: (game tileAt: 1) players isEmpty.
	self assert: ((game tileAt: 5) includesPlayer: jill).
	... Your code ...
	[ self isNotOver ] whileTrue: [
		self playPlayer: (self currentPlayer) roll: 6 atRandom ]
	
	| jack game jill |
	game := SLGame new tileNumber: 12.
	jack := SLPlayer new name: 'Jack'.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jack; addPlayer: jill. 
	game turn: 1.
	self assert: game currentPlayer equals: jack. 
	game turn: 2.
	self assert: game currentPlayer equals: jill. 
	game turn: 3.
	self assert: game currentPlayer equals: jack. 
	... Your code ...
	aPlayer position: 1.
	players add: aPlayer. 
	(tiles at: 1) addPlayer: aPlayer
	turn := aNumber
> {1->1. 2->0. 3->1. 4->0. 5->1. 6->0. 7->1. 8->0. 9->1. 10->0}
> {1->1. 2->2. 3->0. 4->1. 5->2. 6->0. 7->1. 8->2. 9->0. 10->1}

	| rest playerIndex |
	rest := (turn \\ players size).
	playerIndex := (rest isZero
					ifTrue: [ players size ]
					ifFalse: [ rest ]).
	^ players at: 	playerIndex
	
	| jack game |
	game := SLGame new tileNumber: 12.
	jack := SLPlayer new name: 'Jack'.
	game addPlayer: jack. 
	self assert: jack position equals: 1. 
	game movePlayer: jack distance: 11.
	self assert: jack position equals: 12.
	self assert: game isOver.
	... Your code ...
	
	| game |
	game := SLGame new tileNumber: 12.
	self assert: (game canMoveToPosition: 8).
	self assert: (game canMoveToPosition: 12).
	self deny: (game canMoveToPosition: 13).
	... Your code ...
	
	| jill jack game |
	game := SLGame new tileNumber: 12.
	jack := SLPlayer new name: 'Jack'.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill.
	game addPlayer: jack.
	self assert: jill position equals: 1.
	game playOneStepWithRoll: 3.
	self assert: jill position equals: 4.
	self assert: (game tileAt: 1) players size equals: 1.
	self assert: ((game tileAt: 4) includesPlayer: jill)
	
	| jill jack game |
	game := SLGame new tileNumber: 12.
	jack := SLPlayer new name: 'Jack'.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill.
	game addPlayer: jack.
	game playOneStepWithRoll: 3.
	game playOneStepWithRoll: 2.
	"nothing changes for jill"
	self assert: jill position equals: 4.
	self assert: ((game tileAt: 4) includesPlayer: jill).
	"now let us verify that jack moved correctly to tile 3"	
	self assert: (game tileAt: 1) players size equals: 0.
	self assert: jack position equals: 3.
	self assert: ((game tileAt: 3) includesPlayer: jack)
		
	| currentPlayer |
	turn := turn + 1.
	currentPlayer := self currentPlayer. 
	Transcript show: currentPlayer printString, 'drew ', aNumber printString, ': '. 
	(self canMoveToPosition: currentPlayer position + aNumber)
		ifTrue: [ self movePlayer: currentPlayer distance: aNumber ].
	Transcript show: self; cr.
	
	| jill jack game |
	game := SLGame new 
				tileNumber: 12; 
				setLadderFrom: 2 to: 6;
				setLadderFrom: 7 to: 9;
				setSnakeFrom: 11 to: 5.
	jack := SLPlayer new name: 'Jack'.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill.
	game addPlayer: jack.
	game playOneStepWithRoll: 1.
	self assert: jill position equals: 6.
	self assert: (game tileAt: 1) players size equals: 1.
	self assert: ((game tileAt: 6) includesPlayer: jill).
game := SLGame new 
			tileNumber: 12; 
			setLadderFrom: 2 to: 6;
			setLadderFrom: 7 to: 9;
			setSnakeFrom: 11 to: 5.
jack := SLPlayer new name: 'Jack'.
jill := SLPlayer new name: 'Jill'.
game addPlayer: jill.
game addPlayer: jack.
game inspect

	Transcript show: self; cr.
	[ self isOver not ] whileTrue: [
		self playOneStepWithRoll: 6 atRandom ] 
	
	| jill jack game |
	game := SLGame new 
			tileNumber: 12; 
			setLadderFrom: 2 to: 6;
			setLadderFrom: 7 to: 9;
			setSnakeFrom: 11 to: 5.
	jack := SLPlayer new name: 'Jack'.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. 
	game addPlayer: jack. 

	game playOneStepWithRoll: 11.
	"jill lands on the finish tile!"
	self assert: jill position equals: 12.
	self assert: (game tileAt: 1) players size equals: 1. 
	self assert: ((game tileAt: 12) includesPlayer: jill).
	self assert: game isOver.
	
	| jill jack game |
	game := SLGame new 
			tileNumber: 12; 
			setLadderFrom: 2 to: 6;
			setLadderFrom: 7 to: 9;
			setSnakeFrom: 11 to: 5.
	jack := SLPlayer new name: 'Jack'.
	jill := SLPlayer new name: 'Jill'.
	game addPlayer: jill. 
	game addPlayer: jack. 
    "jill moves"
	game playOneStepWithRoll: 9.
	self assert: jill position equals: 10.
	self assert: ((game tileAt: 10) includesPlayers: jill).
	"jack moves"
	game playOneStepWithRoll: 2. 
	"jill tries to move but in fact stays at her place"
	game playOneStepWithRoll: 5.
	self assert: jill position equals: 10.
	self assert: ((game tileAt: 10) includesPlayer: jill).
	self deny: game isOver.