## An electronic wallet
w := Wallet new.
w money = 0.
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Wallet'
	| w |
	w := Wallet new.
	self assert: w money = 0
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'Wallet'	
   ^ 0
	| w |
	w := Wallet new.
	w add: 2 coinsOfValue: 0.50.
	w add: 3 coinsOfValue: 0.20.
	self assert: w coinNumber = 5
aFruitBag := Bag new.
aFruitBag size.
>>> 0
aFruitBag size.
>>> 3
aFruitBag size.
>>> 13
>>> 10
aFruitBag occurrencesOf: #Banana.
>>> 4
aFruitBag do: [ :each |  each logCr ].
#Banana
#Banana
#Banana
#Apple
#Apple
#Apple
'There is 10 Apple'
	bagCoins := Bag new
	"Add to the receiver, anInteger times a coin of value aNumber"
	
	... Your solution ...

	^ ... Your solution ...
	| w |
	w := Wallet new.
	w add: 2 coinsOfValue: 0.50.
	w add: 3 coinsOfValue: 0.20.
	self assert: (w coinsOfValue: 0.5) = 2
	| w |
	w := Wallet new.
	w add: 2 coinsOfValue: 0.50.
	w add: 6 coinsOfValue: 0.50.
	self assert: (w coinsOfValue: 0.5) = 8
	| w |
	w := Wallet new.
	w add: 2 coinsOfValue: 0.50.
	w add: 3 coinsOfValue: 0.20.
	w add: 1 coinsOfValue: 0.02.
	self assert: w money = 1.62
	| w |
	w := Wallet new.
	w add: 2 coinsOfValue: 0.50.
	w add: 3 coinsOfValue: 0.20.
	w add: 1 coinsOfValue: 0.02.
	w add: 5 coinsOfValue: 0.05.
	self assert: w money = 1.87

	^ ... Your solution ...
	| w |
	w := Wallet new.
	w add: 2 coinsOfValue: 0.50.
	w add: 3 coinsOfValue: 0.20.
	w add: 1 coinsOfValue: 0.02.
	w add: 5 coinsOfValue: 0.05.
	self assert: (w canPay: 2) not.
	self assert: (w canPay: 0.50).
	"returns true when we can pay the amount of money"
	
	^ ... Your solution ...
	| w |
	w := Wallet new.
	w add: 10 coinsOfValue: 0.50.
	w add: 10 coinsOfValue: 0.20.
	w add: 10 coinsOfValue: 0.10.
	self assert: w biggest equals: 0.50.
	"Returns the biggest coin. For example, {(3 -> 0.5) . (3 -> 0.2) . (5-> 0.1)} biggest -> 0.5"

	^ ... Your solution ...
	| w |
	w := Wallet new.
	w add: 10 coinsOfValue: 0.50.
	w add: 10 coinsOfValue: 0.20.
	w add: 10 coinsOfValue: 0.10.
	self assert: (w biggestBelow: 1) equals: 0.50.
	self assert: (w biggestBelow: 0.5) equals: 0.20.
	self assert: (w biggestBelow: 0.48) equals: 0.20.
	self assert: (w biggestBelow: 0.20) equals: 0.10.
	self assert: (w biggestBelow: 0.10) equals: 0.
	"Returns the biggest coin with a value below anAmount. For example, {(3 -> 0.5) . (3 -> 0.2) . (5-> 0.1)} biggestBelow: 0.40 -> 0.2"
	
	^ ... Your solution ...
	super printOn: aStream.
	aStream nextPutAll: ' (', self money asString, ')'
	| w |
	w := Wallet new.
	w addCoin: 0.50.
	self assert: (w coinsOfValue: 0.5) = 1.
	self assert: w money equals: 0.5
	"Add to the receiver a coin of value aNumber"
	
	... Your solution ...
	| w |
	w := Wallet new.
	w add: 2 coinsOfValue: 0.50.
	w add: 3 coinsOfValue: 0.20.
	w add: 1 coinsOfValue: 0.02.
	w add: 5 coinsOfValue: 0.05.
	w removeCoin: 0.5.
	self assert: w money = 1.37
	"Remove from the receiver a coin of value aNumber"
	
	... Your solution ...
	| w |
	w := Wallet new.
	
	... Your solution ...
	"Remove from the receiver, anInteger times a coin of value aNumber"

	bagCoins add: aCoin withOccurrences: anInteger 
	| b |
	b := self biggest.
	self removeCoin: b.
	^ b	

	| w paid |
	w := Wallet new.
	w add: 10 coinsOfValue: 0.50.
	w add: 10 coinsOfValue: 0.20.
	w add: 10 coinsOfValue: 0.10.
	paid := (w coinsFor: 2.5).
	self assert: paid money equals: 2.5.
	self assert: (paid coinsOfValue: 0.5) equals: 5 
	"Returns a wallet with the largest coins to pay a certain amount and an empty wallet if this is not possible"
	
	| res |
	res := self class new.
	^ (self canPay: aValue)
		ifFalse: [ res ]
		ifTrue: [ self coinsFor: aValue into: res ] 

	... Your solution ...
	
	[ accuWallet money < self money ]
			whileTrue: [ accuWallet addCoin: self biggestAndRemove ].
	^ accuWallet
	| w paid |
	w := Wallet new.
	w add: 1 coinsOfValue: 0.50.
	w add: 10 coinsOfValue: 0.20.
	w add: 10 coinsOfValue: 0.10.
	paid := (w coinsFor: 2.4).
	self assert: paid money equals: 2.4.
	self assert: (paid coinsOfValue: 0.5) equals: 1.
	self assert: (paid coinsOfValue: 0.2) equals: 9.
	"Returns a wallet with the largest coins to pay a certain amount and an empty wallet if this is not possible"
	| res |
	res := self class new.
	^ (self canPay: aValue)
		ifFalse: [ res ]
		ifTrue: [ self coinsFor: aValue into2: res ] 
	| w paid | 
	w := Wallet new.
	w add: 1 coinsOfValue: 0.50.
	w add: 10 coinsOfValue: 0.20.
	w add: 10 coinsOfValue: 0.10.
	paid := (w coinsFor: 0.6).
	self assert: paid money equals: 0.6.
	self assert: (paid coinsOfValue: 0.5) equals: 1.
	self assert: (paid coinsOfValue: 0.1) equals: 1.
	| w paid | 
	w := Wallet new.
	w add: 2 coinsOfValue: 0.50.
	w add: 10 coinsOfValue: 0.20.
	w add: 10 coinsOfValue: 0.10.
	paid := (w coinsFor: 0.6).
	self assert: paid money equals: 0.6.
	self assert: (paid coinsOfValue: 0.5) equals: 1.
	self assert: (paid coinsOfValue: 0.1) equals: 1.
	| w paid | 
	w := Wallet new.
	w add: 1 coinsOfValue: 1.
	w add: 2 coinsOfValue: 0.50.
	w add: 10 coinsOfValue: 0.20.
	w add: 10 coinsOfValue: 0.10.
	paid := (w coinsFor: 0.6).
	self assert: paid money equals: 0.6.
	self assert: (paid coinsOfValue: 0.5) equals: 1.
	self assert: (paid coinsOfValue: 0.1) equals: 1.