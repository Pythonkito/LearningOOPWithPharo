## Some collection katas with words
>>> $c
>>> $u
>>>'ouou'
>>>	 'uocuoc' 
>>> 2
>>> 5
>>> a Set($u $c $o)
>>> 6
>>> 3
s1 := Set new. 
'coucou' do: [ :aChar | s1 add: aChar ].
s1 
>>> a Set($u $c $o)
s := 'pharo'.
s size = s asSet size 
>>> true
s := 'phaoro'.
s size = s asSet size 
>>> false
	"Returns true if the receiver is an isogram, i.e., a word using no repetitive character."
	"'pharo' isIsogramSet
	>>> true"
	"'phaoro' isIsogramSet
	>>> false"
	
	... Your solution here ... 
>>> true
>>> false
	instanceVariableNames: ''
	classVariableNames: ''
	package: 'LoopStarGram'
	self assert: 'pharo' isIsogramSet.
	self deny: 'phaoro' isIsogramSet.
	self deny: 'phaoro' isIsogramSet.
	^ #('pharo' 'pathfinder' 'xavier' 'francois' 'lumberjacks' 'altruisme' 'antipode')
	
	self isograms do: [ :word |
		self assert: word isIsogramSet ]
	^ #('phaoro' 'stephane' 'idiot' 'freedom')
	
	self isograms do: [ :word |
		self assert: word isIsogramSet ].
	self notIsograms do: [ :word |
		self deny: word isIsogramSet ]
    get: 'https://raw.githubusercontent.com/SquareBracketAssociates/
	LearningOOPWithPharo/
	master/resources/listeDeMotsAFrancaisUTF8.txt') lines

(ZnClient new 
    get: 'https://raw.githubusercontent.com/SquareBracketAssociates/
	LearningOOPWithPharo/
	master/resources/listeDeMotsFrancaisFrGutUTF8.txt') lines

	self assert: 'The quick brown fox jumps over the lazy dog' isEnglishPangram.
	self deny: 'The quick brown fox jumps over the  dog' isEnglishPangram
>>> true
'The quick brown fox jumps over the dog' isEnglishPangram
>>> false
	"Returns true is the receiver is a pangram i.e., that it uses all the characters of a given alphabet."
	
	| isPangram |
	isPangram := true. 
	'abcdefghijklmnopqrstuvwxyz' do: [ :aChar |
		(self includes: aChar)
			ifFalse: [ isPangram := false ]
		].
	^ isPangram
	"Returns true is the receiver is a pangram i.e., that it uses all the characters of a given alphabet."
	
	'abcdefghijklmnopqrstuvwxyz' do: [ :aChar |
		(self includes: aChar)
			ifFalse: [ ^ false ]
		].
	^ true

	self assert: ('The quick brown fox jumps over the lazy dog' isPangramIn: 'abcdefghijklmnopqrstuvwxyz').
	self assert: ('les poux papas et les poux pas papas' isPangramIn: 'apouxetl').
	"Returns true is the receiver is a pangram i.e., that it uses all the characters of a given alphabet."
	"'The quick brown fox jumps over the lazy dog' isPangramIn: 'abcdefghijklmnopqrstuvwxyz'
	>>> true"
	"'tata' isPangramIn: 'at'
	>>> true"

	... Your solution ...
	"Returns true is the receiver is a pangram i.e., that it uses all the characters of a given alphabet."
	"'The quick brown fox jumps over the lazy dog' isEnglishPangram
	>>> true"
	"'The quick brown fox jumps over the dog' isEnglishPangram
	>>> false"

	... Your solution ...
>>> true

'portons dix bons whiskys à l''avocat goujat qui fume au zoo.' isEnglishPangram
>>> true

	self assert: ('the quick brown fox jumps over the lzy dog' 
		detectFirstMissingLetterFor: 'abcdefghijklmnopqrstuvwxyz') equals: $a.
	self assert: ('the uick brown fox jumps over the lazy dog' 
		detectFirstMissingLetterFor: 'abcdefghijklmnopqrstuvwxyz') equals: $q.
	"Return the first missing letter to make a pangram of the receiver in the context of a given alphabet. 
	Return '' otherwise"
	
	... Your solution ...
	
	"Return the first missing letter to make a pangram of the receiver in the context of a given alphabet. 
	Return '' otherwise"
	
	alphabet do: [ :aChar |
		(self includes: aChar)
			ifFalse: [ ^ aChar asString ]
		].
	^ ''
	"Return the first missing letter to make a pangram of the receiver in the context of a given alphabet. 
	Return '' otherwise"
	
	alphabet do: [ :aChar |
		(self includes: aChar)
			ifFalse: [ ^ aChar ]
		].
	^ Character space

	self assert: ('the quick brown fox jumps over the lzy do' 
		detectAllMissingLettersFor: 'abcdefghijklmnopqrstuvwxyz') equals: #($a $g).
	self assert: ('the uick brwn fx jumps ver the lazy dg' 
		detectAllMissingLettersFor: 'abcdefghijklmnopqrstuvwxyz') equals: #($q $o).
	
	... Your solution ...

	self assert: ('the quick brown fox jumps over the lzy do' 
		detectAllMissingLettersFor: 'abcdefghijklmnopqrstuvwxyz') equals: (Set withAll: #($a $g)).
	self assert: ('the uick brwn fx jumps ver the lazy dg' 
		detectAllMissingLettersFor: 'abcdefghijklmnopqrstuvwxyz') equals: #($q $o) asSet.

	self assert: 'ete' isPalindrome.
	self assert: 'kayak' isPalindrome.
	self deny: 'etat' isPalindrome.
>>> 'tate'
res := OrderedCollection new. 
#(1 2 3) with: #(10 20 30) do: [ :f :s | res add: f * s ].
res
>>> an OrderedCollection(10 40 90)