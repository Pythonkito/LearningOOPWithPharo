## Summing and converting money
   | clp1 eur1 clp2 eur2 |
   clp1 := CLP new value: 3500.
   eur1 := EUR new value: 10.
   clp2 := CLP new value: 5000.
   eur2 := EUR new value: 20.

   self assert: clp1 + clp2 equals: (CLP new value: 8500). 
   self assert: clp1 + eur1 equals: (CLP new value: 3500 + 6620).
   
   self assert: eur1 + eur2 equals: (EUR new value: 30).
   self assert: eur1 + clp2 equals: (EUR new value: 5000 / 662 + 10).
	instVarNames: ‘value’ 
   self subclassResponsibility 
   super printOn: str.
   str nextPut: $<.
   str nextPutAll: self value asString.
   str nextPut: $>.
   self subclassResponsibility 
   self subclassResponsibility 
  ^ self class == anotherCurrency class and: [ self value = anotherCurrency value ]

Currency subclass: #CLP 
   ^ anotherCurrency sumWithEUR: self
   ^ EUR new value: self value + money value
   ^ CLP new value: (self value * 662) + money value
   ^ anotherCurrency sumWithCLP: self
   ^ EUR new value: (self value / 662) + money value
  ^ CLP new value: self value + money value