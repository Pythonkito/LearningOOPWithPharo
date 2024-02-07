## A simple network simulator
    instanceVariableNames: ''
    classVariableNames: ''
    category: 'NetworkSimulator-Tests'
    | src dest payload packet |
    src := Object new.
    dest := Object new.
    payload := Object new.

    packet := KANetworkPacket from: src to: dest payload: payload.

    self assert: packet sourceAddress equals: src.
    self assert: packet destinationAddress equals: dest.
    self assert: packet payload equals: payload
    instanceVariableNames: 'sourceAddress destinationAddress payload'
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
    ... Your code ...
    ... Your code ...
	... Your code ...
KANetworkPacket >> destinationAddress
	... Your code ...
KANetworkPacket >> payload
	... Your code ...
    | address node |
    address := Object new.
    node := KANetworkNode withAddress: address.
    self assert: node address equals: address
    instanceVariableNames: 'address'
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
    ^ self new
        initializeAddress: aNetworkAddress
	... Your code ...
	... Your code ...
    | node1 node2 link |
    node1 := KANetworkNode withAddress: #address1.
    node2 := KANetworkNode withAddress: #address2.
    link := KANetworkLink from: node1 to: node2.

    link attach.

    self assert: (node1 hasLinkTo: node2)
    instanceVariableNames: 'source destination'
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
    ^ self new
        initializeFrom: sourceNode to: destinationNode
	... Your code ...
KANetworkLink >> source
	... Your code ...
KANetworkLink >> destination
	... Your code ...
    source attach: self
    outgoingLinks add: anOutgoingLink
    outgoingLinks := Set new.
    ... Your code ...
	| node1 node2 link |
	node1 := KANetworkNode withAddress: #address1.
	node2 := KANetworkNode withAddress: #address2.
	link := KANetworkLink from: node1 to: node2.
	link attach.
	self halt.
	self assert: (node1 hasLinkTo: node2)
	aStream nextPutAll: 'Node ('.
	aStream nextPutAll: address , ')'
	aStream nextPutAll: 'Link'.
	source
		ifNotNil: [ aStream
				nextPutAll: ' ';
				nextPutAll: source address ].
	destination
		ifNotNil: [ aStream
				nextPutAll: ' -> ';
				nextPutAll: destination address ]
    | srcNode destNode link packet |
    srcNode := KANetworkNode withAddress: #src.
    destNode := KANetworkNode withAddress: #dest.
    link := (KANetworkLink from: srcNode to: destNode) attach; yourself.
    packet := KANetworkPacket from: #address to: #dest payload: #payload.

    srcNode send: packet via: link.
    self assert: (link isTransmitting: packet).
    self deny: (destNode hasReceived: packet).

    link transmit: packet.
    self deny: (link isTransmitting: packet).
    self assert: (destNode hasReceived: packet)
    aLink emit: aPacket
    instanceVariableNames: 'source destination packetsToTransmit'
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
    packetsToTransmit := OrderedCollection new
    "Packets are not transmitted right away, but stored.
    Transmission is explicitly triggered later by sending #transmit:."

    packetsToTransmit add: aPacket
    ... Your code ...
    aPacket destinationAddress = address
        ifTrue: [
            self consume: aPacket.
            arrivedPackets add: aPacket ]
        ifFalse: [ self notYetImplemented ]
    "Default handling is to do nothing."
	... Your code ...
    "Transmit aPacket to the destination node of the receiver link."
    ... Your code ...
    | node packet |
    node := KANetworkNode withAddress: #address.
    packet := KANetworkPacket from: #address to: #address payload: #payload.

    node send: packet.
    node loopback transmit: packet.

    self assert: (node hasReceived: packet).
    self deny: (node loopback isTransmitting: packet)
    instanceVariableNames: 'address outgoingLinks loopback arrivedPackets'
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
    ... Your code ...
    ^ loopback
    "Send aPacket, leaving the responsibility for routing to the node."
    self
        linksTowards: aPacket destinationAddress
        do: [ :link | self send: aPacket via: link ]
    "Simple flood algorithm: route via all outgoing links.
    However, just loopback if the receiver node is the routing destination."
    ... Your code ...
    instanceVariableNames: 'net hub alone'
    classVariableNames: ''
    category: 'NetworkSimulator-Tests'
    super setUp.
    self buildNetwork
    self
        assert: (net nodeAt: hub address ifNone: [ self fail ])
        equals: hub
	alone := KANetworkNode withAddress: #alone.
	net := KANetwork new.
	hub := KANetworkNode withAddress: #hub.
	#( mac pc1 pc2 impr ) do: [ :addr | 
		| node |
		node := KANetworkNode withAddress: addr.
		net connect: node to: hub ].
	net
		connect: (KANetworkNode withAddress: #ping)
		to: (KANetworkNode withAddress: #pong)
    instanceVariableNames: 'nodes links'
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
    ... Your code ...
	^ KANetworkLink from: aNode to: anotherNode
	nodes add: aNode
	^ nodes includes: aNode
	| netw hubb mac pc1 |
	netw := KANetwork new.
	hubb := KANetworkNode withAddress: #hub.
	mac := KANetworkNode withAddress: #mac.
	pc1 := KANetworkNode withAddress: #pc1.

	netw connect: hubb to: mac.
	self assert: (hubb hasLinkTo: mac).
	self assert: (mac hasLinkTo: hubb).
	self assert: (netw doesRecordNode: hubb).
	self assert: (netw doesRecordNode: mac).

	netw connect: hubb to: pc1.
	self assert: (hubb hasLinkTo: pc1).
	self assert: (mac hasLinkTo: hubb)
    ... Your code ...
    ... Your code ...
    self
        should: [ net nodeAt: alone address ]
        raise: NotFound
    ^ self
        nodeAt: anAddress
        ifNone: [ NotFound signalFor: anAddress in: self ]
    | link |
    self
        shouldnt: [ link := net linkFrom: #pong to: #ping ]
        raise: NotFound.
    self
        assert: link source
        equals: (net nodeAt: #pong).
    self
        assert: link destination
        equals: (net nodeAt: #ping)
    ... Your code ...
    | packet |
    packet := KANetworkPacket
        from: alone address
        to: alone address
        payload: #something.
    self assert: (packet isAddressedTo: alone).
    self assert: (packet isOriginatingFrom: alone).

    alone send: packet.
    self deny: (alone hasReceived: packet).
    self assert: (alone loopback isTransmitting: packet).

    alone loopback transmit: packet.
    self deny: (alone loopback isTransmitting: packet).
    self assert: (alone hasReceived: packet)
    ^ destinationAddress = aNode address
    ^ sourceAddress = aNode address
    | packet ping pong link |
    packet := KANetworkPacket from: #ping to: #pong payload: #ball.
    ping := net nodeAt: #ping.
    pong := net nodeAt: #pong.
    link := net linkFrom: #ping to: #pong.

    ping send: packet.
    self assert: (link isTransmitting: packet).
    self deny: (pong hasReceived: packet).

    link transmit: packet.
    self deny: (link isTransmitting: packet).
    self assert: (pong hasReceived: packet)
    | hello mac pc1 firstLink secondLink |
    hello := KANetworkPacket from: #mac to: #pc1 payload: 'Hello!'.
    mac := net nodeAt: #mac.
    pc1 := net nodeAt: #pc1.
    firstLink := net linkFrom: #mac to: #hub.
    secondLink := net linkFrom: #hub to: #pc1.

    self assert: (hello isAddressedTo: pc1).
    self assert: (hello isOriginatingFrom: mac).

    mac send: hello.
    self deny: (pc1 hasReceived: hello).
    self assert: (firstLink isTransmitting: hello).

    firstLink transmit: hello.
    self deny: (pc1 hasReceived: hello).
    self assert: (secondLink isTransmitting: hello).

    secondLink transmit: hello.
    self assert: (pc1 hasReceived: hello).
    aPacket destinationAddress = address
        ifTrue: [
            self consume: aPacket.
            arrivedPackets add: aPacket ]
        ifFalse: [ self forward: aPacket from: aLink ]
    | hello mac pc1 firstLink secondLink |
    hello := KANetworkPacket from: #mac to: #pc1 payload: 'Hello!'.
    mac := net nodeAt: #mac.
    pc1 := net nodeAt: #pc1.
    firstLink := net linkFrom: #mac to: #hub.
    secondLink := net linkFrom: #hub to: #pc1.
    backLink := net linkFrom: #hub to: #mac.

    self assert: (hello isAddressedTo: pc1).
    self assert: (hello isOriginatingFrom: mac).

    mac send: hello.
    self deny: (pc1 hasReceived: hello).
    self assert: (firstLink isTransmitting: hello).

    firstLink transmit: hello.
    self deny: (pc1 hasReceived: hello).
    self deny: (backLink isTransmitting: hello).
    self assert: (secondLink isTransmitting: hello).

    secondLink transmit: hello.
    self assert: (pc1 hasReceived: hello).
    "Do nothing. Normal nodes do not route packets."
    instanceVariableNames: ''
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
   ... Your code ...
    instanceVariableNames: 'receivedCount'
    classVariableNames: ''
    category: 'NetworkSimulator-Nodes'
    super initialize.
    receivedCount := 0
    receivedCount := receivedCount + 1
    instanceVariableNames: 'supply output'
    classVariableNames: ''
    category: 'NetworkSimulator-Nodes'
    supply > 0 ifFalse: [ ^ self "no paper, do nothing" ].

    supply := supply - 1.
    output add: aPacket payload
    super initialize.
    supply := 0.
    tray := OrderedCollection new
    supply := supply + paperSheets
    ^ (self withAddress: anAddress)
        resupply: paperSheets;
        yourself
    instanceVariableNames: ''
    classVariableNames: ''
    category: 'NetworkSimulator-Nodes'
    | response |
    response := aPacket payload asUppercase.
    self send: (KANetworkPacket
        from: self address
        to: aPacket sourceAddress
        payload: response)
    | routers |
    net := KANetwork new.

    routers := #(A B C) collect:
        [ :each | KANetworkHub withAddress: each ].
    net connect: routers first to: routers second.
    net connect: routers second to: routers third.
    net connect: routers third to: routers first.

    #(a1 a2) do: [ :addr |
        net connect: routers first
            to: (KANetworkNode withAddress: addr) ].
    #(b1 b2 b3) do: [ :addr |
        net connect: routers second
            to: (KANetworkNode withAddress: addr) ].
    net connect: routers third
        to: (KANetworkNode withAddress: #c1)