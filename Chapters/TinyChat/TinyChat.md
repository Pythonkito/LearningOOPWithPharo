## TinyChat: a fun and small chat client/server
	baseline: 'Teapot';
	repository: 'github://zeroflag/teapot:master/source';
	load.
	instanceVariableNames: 'sender text separator'
	classVariableNames: ''
	category: 'TinyChat'
	^ sender

TCMessage >> sender: anObject
	sender := anObject

TCMessage >> text
	^ text

TCMessage >> text: anObject
	text := anObject
	super initialize.
	separator := '>'.
	^ self new sender: aSender; text: aText; yourself
	| instance |
	instance := self new.
	instance sender: aSender; text: aText.
	^ instance

	aStream 
		<< self sender; << separator; 
		<< self text; << String crlf
	"Compose a message from a string of this form 'sender>message'."
	| items |
	items := aString substrings: separator.
	self sender: items first.
	self text: items second.
	^ self new 
		fromString: aString;
		yourself
	instanceVariableNames: 'messages'
	classVariableNames: ''
	category: 'TinyChat-server'
	super initialize.
	messages := OrderedCollection new.
	messages add: aMessage 

TCMessageQueue >> reset
	messages removeAll

TCMessageQueue >> size
	^ messages size
	^ (aIndex > 0 and: [ aIndex <= messages size]) 
		ifTrue: [ messages copyFrom: aIndex to: messages size ]
		ifFalse: [ #() ]
	
	^ String streamContents: [ :formattedMessagesStream |  
		(self listFrom: aMessageNumber) 
			do: [ :m | formattedMessagesStream << m printString ] 
		]
	instanceVariableNames: 'teapotServer messagesQueue'
	classVariableNames: ''
	category: 'TinyChat-Server'
	super initialize.
	messagesQueue := TCMessageQueue new.
	teapotServer := Teapot configure: { 
		#defaultOutput -> #text.
		#port -> anInteger.
		#debugMode -> true
	}.
	teapotServer start.
	teapotServer
		GET: '/messages/count' -> (Send message: #messageCount to: self);
		GET: '/messages/<id:IsInteger>' -> (Send message: #messagesFrom: to: self);
		POST: '/messages/add' -> (Send message: #addMessage: to: self)
	teapotServer
		exception: KeyNotFound -> (TeaResponse notFound body: 'No such message')
	^self new
		initializePort: aPortNumber;
		registerRoutes;
		registerErrorHandlers;
		yourself
	teapotServer stop.
	messagesQueue reset.
	self allInstancesDo: #stop
	messagesQueue add: (TCMessage from: (aRequest at: #sender) text: (aRequest at: #text)).
	^ messagesQueue size
	^ messagesQueue formattedMessagesFrom: (request at: #id)  
	url: 'http://localhost:8181/messages/add';
	formAt: 'sender' put: 'olivier';
	formAt: 'text' put: 'Super cool ce tinychat' ; post
	instanceVariableNames: 'url login exit messages console lastMessageIndex'
	classVariableNames: ''
	category: 'TinyChat-client'
	super initialize.
	exit := false.
	lastMessageIndex := 0.
	messages := OrderedCollection new.
	^'{1}{2}' format: { url . aPath }

TinyChat >> command: aPath argument: anArgument
	^'{1}{2}/{3}' format: { url . aPath . anArgument asString }
	^ self command: '/messages/count'

TinyChat >> cmdNewMessage
	^self command: '/messages/add'

TinyChat >> cmdMessagesFromLastIndexToEnd
	"Returns the server messages from my current last index to the last one on the server."
	^ self command: '/messages' argument: lastMessageIndex
	| id |
	id := (ZnClient new url: self cmdLastMessageID; get) asInteger.
	id = 0 ifTrue: [ id := 1 ].
	^ id
	"Gets the new messages that have been posted since the last request."
	| response receivedMessages |
	response := (ZnClient new url: self cmdMessagesFromLastIndexToEnd; get).
	^ response 
		ifNil: [ 0 ]
		ifNotNil: [  
			receivedMessages := response substrings: String crlf.
			receivedMessages do: [ :msg | messages add: (TCMessage fromString: msg) ].
			receivedMessages size.
		].
	[  
		[ exit ] whileFalse: [  
			(Delay forSeconds: 2) wait.
			lastMessageIndex := lastMessageIndex + (self readMissingMessages).
			console print: messages.
		]
	] fork
	^ ZnClient new
		url: self cmdNewMessage;
		formAt: 'sender' put:  (aMessage sender);
		formAt: 'text' put: (aMessage text);
		post
	"When we send a message, we push it to the server and in addition we update the local list of posted messages."
	
	| msg |
	msg := TCMessage from: login text: aString.
	self sendNewMessage: msg.
	lastMessageIndex := lastMessageIndex + (self readMissingMessages).
	console print: messages.
	self sendNewMessage: (TCMessage from: login text: 'I exited from the chat room.').
	exit := true

	^ self new
		host: aHost port: aPort login: aLogin;
		start
	url := 'http://' , aHost , ':' , aPort asString.
	login := aLogin
	console := TCConsole attach: self.
	self sendNewMessage: (TCMessage from: login text: 'I joined the chat room').
	lastMessageIndex := self readLastMessageID.
	self refreshMessages.
	instanceVariableNames: 'chat list input'
	classVariableNames: ''
	category: 'TinyChat-client'
	^ input

TCConsole >> list
	^ list

TCConsole >> chat: anObject
	chat := anObject
	^ 'TinyChat'
	<spec: #default>

	^ SpecLayout composed
		newColumn: [ :c | 
			c add: #list; add: #input height: 30 ]; yourself

	list := ListModel new.
	input := TextInputFieldModel new 
		ghostText: 'Type your message here...';
		enabled: true;
		acceptBlock: [ :string |  
			chat send: string. 
			input text: '' ].
	self focusOrder add: input.
	list items: (aCollectionOfMessages collect: [  :m |  m printString ])
	| window |
	window := self new chat: aTinyChat.
	window openWithSpec whenClosedDo: [ aTinyChat disconnect ].
	^ window
TCServer stopAll.
TCServer startOn: 8080.
tco := TinyChat connect: 'localhost' port: 8080 login: 'olivier'.
tco send: 'hello'.
tcs := TinyChat connect: 'localhost' port: 8080 login: 'Stef'.	
tcs send: 'salut olivier'