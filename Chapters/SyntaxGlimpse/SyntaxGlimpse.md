## Pharo's syntax overview
>>> $A
>>> 'Hello'
>>> $A
>>> 'Hello Pharoers'
>>> #'Hello Pharoers'
>>> false
>>> #(1 + 2 3)
>>> #(3)
>>> #(3 7)
sum := 0
sum := 0.
sum := sum + 1.
^ sum 
a := #(11 22 33).
a at: 2 put: 66.
a
>>>#(11 66 33)
>>> 2432902008176640000
>>> 27
 - / \ * ~ < > = @ % | & ? ,
>>>22
a := #(11 22 33).
a at: 2 put: 66.
a
>>>#(11 66 33)
>>> true
>>> true
messages**. Pharo distinguishes such three types of messages to minimize the number of parentheses. 
>>> 40
>>> 128
>>> 9
>>> 7
Transcript show: 'hello world'.
Transcript cr
  cr;
  show: 'hello world';
  cr
>>> 3
>>> 33
>>> 3
[ :x :y | x + y ] value: 1 value: 2 
>>> 3
	| z |
	z := x + y.
	z ] value: 1 value: 2 
>>> 3
x := 1.
[ :y | x + y ] value: 2 
>>> 3
	"Answer the number of lines represented by the receiver, where every cr adds one line."

	| cr count |
	cr := Character cr.
	count := 1 min: self size.
	self do: [:c | c == cr ifTrue: [count := count + 1]].
	^ count
	ifTrue: [ 'bigger' ]
	ifFalse: [ 'smaller' ] 
>>>'bigger'
	ifFalse: [ 'smaller' ]
	ifTrue: [ 'bigger' ]
>>>'bigger'
[ n < 1000 ] whileTrue: [ n := n*2 ].
n 
>>> 1024
[ n > 1000 ] whileFalse: [ n := n*2 ].
n 
>>> 1024
10 timesRepeat: [ n := n*2 ].
n 
>>> 1024
1 to: 10 do: [:n | result := result, n printString, ' '].
result 
>>> '1 2 3 4 5 6 7 8 9 10'
(1 to: 10) do: [:n | result := result, n printString, ' '].
result 
>>> '1 2 3 4 5 6 7 8 9 10 '
>>> #(1 4 9 16 25 36 49 64 81 100)
>>> 'eoee'
'hello there' reject: [ :char | char isVowel ] 
>>> 'hll thr'
'hello there' detect: [ :char | char isVowel ] 
>>> $e