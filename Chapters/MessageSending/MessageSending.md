## Sending a message is making a choice
>>> false
>>> true
>>> false
>>> true
   "Negation--answer false since the receiver is true."
   ^ false
   "Negation--answer true since the receiver is false."
   ^ true
>>> true
>>> true
>>> false
>>> true
>>> true
>>> true
   "Evaluating Or -- answer true since the receiver is true."
   ^ true
>>> true
>>> false
>>> anything
   "Evaluating Or -- answer with the argument, aBoolean."
   ^ aBoolean
	ifTrue: [ 'bigger' ]
	ifFalse: [ 'smaller' ]
>>> 'bigger'
>>> 4
       asMorph openInWindow ] value
   ^ trueAlternativeBlock value
   ^ falseAlternativeBlock value
	self == PRList
		ifTrue: [ ... ]
		self == PRParagraph 
			ifTrue: [ ... ]
			...
        PRDocumentItem #(''counter'')
                PRDocumentGroup #(''children'')
                        PRDocument #()
                        PRHeader #(''level'')
                        PRList #()
                                PROrderedList #()
                                PRUnorderedList #()
                        PRParagraph #()
                        PRReference #(''reference'' ''parameters'')
                                PRFigure #()
                        PRSlide #(''title'' ''label'')
                PRText #(''text'')'