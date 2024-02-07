## Network simulator solutions
    ^ self new
        initializeSource: sourceAddress
        destination: destinationAddress
        payload: anObject
    sourceAddress := source.
    destinationAddress := destination.
    payload := anObject
    ^ sourceAddress
    ^ destinationAddress
    ^ payload
    address := aNetworkAddress
    ^ address
    source := sourceNode.
    destination := destinationNode.
    ^ source
    ^ destination
    instanceVariableNames: 'address outgoingLinks'
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
    ^ outgoingLinks
        anySatisfy: [ :any | any destination == anotherNode ]
    ^ packetsToTransmit includes: aPacket
    "Transmit aPacket to the destination node of the receiver link."
    (self isTransmitting: aPacket)
        ifTrue: [
            packetsToTransmit remove: aPacket.
            destination receive: aPacket from: self ]
    instanceVariableNames: 'address outgoingLinks arrivedPackets'
    classVariableNames: ''
    category: 'NetworkSimulator-Core'
    outgoingLinks := Set new.
    arrivedPackets := OrderedCollection new
    ^ arrivedPackets includes: aPacket
    loopback := KANetworkLink from: self to: self.
    outgoingLinks := Set new.
    arrivedPackets := OrderedCollection new
    "Simple flood algorithm: route via all outgoing links.
    However, just loopback if the receiver node is the routing destination."
    anAddress = address
        ifTrue: [ aBlock value: self loopback ]
        ifFalse: [ outgoingLinks do: aBlock ]
    alone := KANetworkNode withAddress: #alone.

    net := KANetwork new.

    hub := KANetworkNode withAddress: #hub.
    #(mac pc1 pc2 prn) do: [ :addr |
        | node |
        node := KANetworkNode withAddress: addr.
        net connect: node to: hub ].

    net
        connect: (KANetworkNode withAddress: #ping)
        to: (KANetworkNode withAddress: #pong)
    nodes := Set new.
    links := Set new
    self add: aNode.
    self add: anotherNode.
    links add: (self makeLinkFrom: aNode to: anotherNode) attach.
    links add: (self makeLinkFrom: anotherNode to: aNode) attach
    ^ nodes
        detect: [ :any | any address = anAddress ]
        ifNone: noneBlock
    ^ links
        detect: [ :anyLink |
            anyLink source address = sourceAddress
                and: [ anyLink destination address = destinationAddress ] ]
        ifNone: [
            NotFound
                signalFor: sourceAddress -> destinationAddress
                in: self ]
    self
        linksTowards: aPacket destinationAddress
        do: [ :link |
            link destination == arrivalLink source
                ifFalse: [ self send: aPacket via: link ] ]