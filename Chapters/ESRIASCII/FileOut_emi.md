```
	instanceVariableNames: ''
	classVariableNames: ''
	poolDictionaries: ''
	category: 'ESRI'

	| lines parser |
	parser := ESRIParser new.
	parser cutLines: 'NCOLS xxx
NROWS xxx
XLLCORNER xxx
YLLCORNER xxx'. 
	self assert: parser lines first equals: 'NCOLS xxx'.
	self assert: parser lines size equals: 4.

	| lines parser |
	parser := ESRIParser new.
	parser cutLines: 'NCOLS xxx
NROWS xxx
XLLCORNER xxx
YLLCORNER xxx'. 
	self assert: parser lines first equals: 'NCOLS xxx'.
	self assert: parser lines size equals: 4.

	| parser |
	parser := ESRIParser new.
	parser cutLines: 'NCOLS xxx
NROWS xxx
XLLCORNER xxx
YLLCORNER xxx'. 
	self assert: parser lines first equals: 'NCOLS xxx'.
	self assert: parser lines size equals: 4.
	self shouldBeImplemented.
	instanceVariableNames: 'lines'
	classVariableNames: ''
	poolDictionaries: ''
	category: 'ESRI'
	| str | 
	lines := OrderedCollection new. 
	str := aString readStream.
	[ str atEnd ] whileFalse: 
		[ lines add: (str upTo: Character cr) ].
	^ lines
	
	^ lines
	instanceVariableNames: ''
	classVariableNames: ''
	poolDictionaries: ''
	category: 'ESRI'

	| parser |
	parser := ESRIParser new.
	parser parser handeline: 'NCOLS 2'
	self assert: parser raster numberOfColumns equals: 2

	| parser |
	parser := ESRIParser new.
	parser parser handeline: 'NCOLS 2'
	self assert: parser raster numberOfColumns equals: 2

	| parser |
	parser := ESRIParser new.
	parser cutLines: 'NCOLS xxx
NROWS xxx
XLLCORNER xxx
YLLCORNER xxx'. 
	self assert: parser lines first equals: 'NCOLS xxx'.
	self assert: parser lines size equals: 4.

	| parser |
	parser := ESRIParser new.
	parser parser handeline: 'NCOLS 2'.
	self assert: parser raster numberOfColumns equals: 2

	| parser |
	parser := ESRIParser new.
	parser handeline: 'NCOLS 2'.
	self assert: parser raster numberOfColumns equals: 2
	self shouldBeImplemented.
	instanceVariableNames: 'lines raster'
	classVariableNames: ''
	poolDictionaries: ''
	category: 'ESRI'
	instanceVariableNames: 'lines raster builderMapping'
	classVariableNames: ''
	poolDictionaries: ''
	category: 'ESRI'
	
	| contents |
	contents := (aString splitOn: Character space).
	raster perform: (builderMapping at: contents first lowercase asSymbol) with: contents second asNumber. 
	
	instanceVariableNames: 'numberOfColumns numberOfRows xllcenter yllcenter cellSize noData rows'
	classVariableNames: ''
	poolDictionaries: ''
	category: 'ESRI'
	^ numberOfColumns
	numberOfColumns := anObject
	^ numberOfRows
	numberOfRows := anObject
	^ xllcenter
	xllcenter := anObject
	^ yllcenter
	yllcenter := anObject
	^ cellSize
	cellSize := anObject
	^ noData
	noData := anObject
	^ rows
	rows := anObject
	super initialize. 
	raster := ESRIRaster new.
	super initialize. 
	raster := ESRIRaster new.
	
	| contents |
	contents := (aString splitOn: Character space).
	raster 
		perform: (builderMapping at: contents first lowercase asSymbol) 
		with: contents second asNumber. 
	
	super initialize. 
	raster := ESRIRaster new.
	self initializeBuilderMapping

	

	builderMapping := Dictionary new. 
	builderMapping at: #ncols put: #numberOfColumns:.
	builderMapping at: #nrows put: #numberOfRows:.
	builderMapping at: #xllcenter put: #xllcenter:.
	builderMapping at: #yllcenter put: #xllcenter:.
	builderMapping at: #cellsize put: #cellSize:.
	builderMapping at: #nodata_value put: #noData:.
	

	super initialize. 
	noData := -9999

	super initialize. 
	noData := -9999
	
	| contents |
	contents := (aString splitOn: Character space).
	raster 
		perform: (builderMapping at: contents first asLowercase asSymbol) 
		with: contents second asNumber. 
	
	^ raster

	| parser |
	parser := ESRIParser new.
	parser handeline: 'nrows 2'.
	self assert: parser raster numberOfRows equals: 2

	| parser |
	parser := ESRIParser new.
	parser handeline: 'xllcorner 378923'.
	self assert: parser raster numberOfRows equals: 378923
	instanceVariableNames: 'numberOfColumns numberOfRows xllcenter yllcenter xllcorner yllcorner cellSize noData rows'
	classVariableNames: ''
	poolDictionaries: ''
	category: 'ESRI'
	^ xllcorner
	xllcorner := anObject
	^ yllcorner
	yllcorner := anObject

	builderMapping := Dictionary new. 
	builderMapping at: #ncols put: #numberOfColumns:.
	builderMapping at: #nrows put: #numberOfRows:.
	builderMapping at: #xllcenter put: #xllcenter:.
	builderMapping at: #yllcenter put: #xllcenter:.
	builderMapping at: #xllcorner put: #xllcorner:.
	builderMapping at: #yllcorner put: #xllcorner:.
	builderMapping at: #cellsize put: #cellSize:.
	builderMapping at: #nodata_value put: #noData:.
	

	| parser |
	parser := ESRIParser new.
	parser handeline: 'xllcorner 378923'.
	self assert: parser raster xllcorner equals: 378923

	super initialize. 
	noData := -9999.

	super initialize. 
	noData := -9999.
	numberOfColumns := 0.
	numberOfRows := 0. 
	xllcenter := 0. 
	yllcenter := 0. 
	xllcorner := 0. 
	yllcorner := 0. 
	cellSize := 0.
	rows := OrderedCollection new. 

	| parser |
	parser := ESRIParser new.
	parser handeline: 'CELLSIZE 30'.
	self assert: parser raster cellSize equals: 30
	| str | 
	str := aString readStream.
	[ str atEnd ] whileFalse: 
		[ self handleline: (str upTo: Character cr) ].

	
	
	| contents |
	contents := (aString splitOn: Character space).
	raster 
		perform: (builderMapping at: contents first asLowercase asSymbol) 
		with: contents second asNumber. 
	

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'CELLSIZE 30'.
	self assert: parser raster cellSize equals: 30

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'nrows 2'.
	self assert: parser raster numberOfRows equals: 2

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'xllcorner 378923'.
	self assert: parser raster xllcorner equals: 378923

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'NCOLS 2'.
	self assert: parser raster numberOfColumns equals: 2
	
	| contents |
	contents := (aString splitOn: Character space).
	raster 
		perform: (builderMapping at: contents first asLowercase asSymbol) 
		with: contents second asNumber. 
	
	| str | 
	str := aString readStream.
	[ str atEnd ] whileFalse: 
		[ self handleLine: (str upTo: Character cr) ].

	
	| str | 
	str := aString readStream.
	[ str atEnd ] whileFalse: 
		[ self handleLine: (str upTo: Character cr) ].

	

	| parser |
	parser := ESRIParser new.
	parser parse: 'NCOLS xxx
NROWS xxx
XLLCORNER xxx
YLLCORNER xxx'. 
	self assert: parser lines first equals: 'NCOLS xxx'.
	self assert: parser lines size equals: 4.
	| str | 
	str := aString readStream.
	[ str atEnd ] whileFalse: 
		[ self handleLine: (str upTo: Character cr) ].

	
	| str | 
	self initializeRaster.
	str := aString readStream.
	[ str atEnd ] whileFalse: 
		[ self handleLine: (str upTo: Character cr) ].

	
	raster := ESRIRaster new
	super initialize.
	self initializeRaster.
	self initializeBuilderMapping

	| parser |
	parser := ESRIParser new.
	parser parse: 'NCOLS 20
NROWS 30
XLLCORNER 2
YLLCORNER 3'. 
	self assert: parser raster numberOfColumns equals: 20.
	self assert: parser lines xllcorner equals: 2.
	self assert: parser lines yllcorner equals: 3.

	| parser |
	parser := ESRIParser new.
	parser parse: 'NCOLS 20
NROWS 30
XLLCORNER 2
YLLCORNER 3'. 
	self assert: parser raster numberOfColumns equals: 20.
	self assert: parser raster xllcorner equals: 2.
	self assert: parser raster yllcorner equals: 3.

	| parser |
	parser := ESRIParser new.
	parser parse: 'NCOLS 20
NROWS 30
XLLCORNER 2
YLLCORNER 3'. 
	self assert: parser raster numberOfColumns equals: 20.
	self assert: parser raster numberOfRows equals: 30.
	self assert: parser raster xllcorner equals: 2.
	self assert: parser raster yllcorner equals: 3.

	| parser |
	parser := ESRIParser new.
	parser parse: 'NCOLS xxx
NROWS xxx
XLLCORNER xxx
YLLCORNER xxx'. 
	self assert: parser lines first equals: 'NCOLS xxx'.
	self assert: parser lines size equals: 4.

	builderMapping := Dictionary new. 
	builderMapping at: #ncols put: #numberOfColumns:.
	builderMapping at: #nrows put: #numberOfRows:.
	builderMapping at: #xllcenter put: #xllcenter:.
	builderMapping at: #yllcenter put: #yllcenter:.
	builderMapping at: #xllcorner put: #xllcorner:.
	builderMapping at: #yllcorner put: #yllcorner:.
	builderMapping at: #cellsize put: #cellSize:.
	builderMapping at: #nodata_value put: #noData:.
	

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'nrows 2'.
	self assert: parser raster numberOfRows equals: 2

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'xllcorner 378923'.
	self assert: parser raster xllcorner equals: 378923

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'CELLSIZE 30'.
	self assert: parser raster cellSize equals: 30

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'NCOLS 2'.
	self assert: parser raster numberOfColumns equals: 2

	| parser |
	parser := ESRIParser new.
	parser parse: 'NCOLS 20
NROWS 30
XLLCORNER 2
YLLCORNER 3'. 
	self assert: parser raster numberOfColumns equals: 20.
	self assert: parser raster numberOfRows equals: 30.
	self assert: parser raster xllcorner equals: 2.
	self assert: parser raster yllcorner equals: 3.

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'nrows 2'.
	self assert: parser raster numberOfRows equals: 2

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'xllcorner 378923'.
	self assert: parser raster xllcorner equals: 378923

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'CELLSIZE 30'.
	self assert: parser raster cellSize equals: 30

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'NCOLS 2'.
	self assert: parser raster numberOfColumns equals: 2

	| parser |
	parser := ESRIParser new.
	parser parse: 'NCOLS 20
NROWS 30
XLLCORNER 2
YLLCORNER 3'. 
	self assert: parser raster numberOfColumns equals: 20.
	self assert: parser raster numberOfRows equals: 30.
	self assert: parser raster xllcorner equals: 2.
	self assert: parser raster yllcorner equals: 3.

	

	| parser |
	parser := ESRIParser new.
	parser handleLine: 'CELLSIZE 30'.
	self assert: parser raster cellSize equals: 30

	

	| parser |
	parser := ESRIParser new.
	parser raster cellSize: 3.
	parser raster numberOfColumns: 4. 
	parser handleLine: '1 1 1 2 2 2 3 3 3 4 4 4 '.
	parser raster rows first equals: #(( 1 1 1) (2 2 2 ) (3 3 3) (4 4 4 ))
	
	| contents isHeader |
	contents := (aString splitOn: Character space).
	isHeader := contents size = 2 and: [ contents first isNumber not ].
	isHeader
		ifTrue: [   
			raster 
				perform: (builderMapping at: contents first asLowercase asSymbol) 
				with: contents second asNumber. ]
			
	
	raster
		perform: (builderMapping at: contents first asLowercase asSymbol)
		with: contents second asNumber
	| contents isHeader |
	contents := aString splitOn: Character space.
	isHeader := contents size = 2 and: [ contents first isNumber not ].
	isHeader
		ifTrue:
			[ self handleHeader: contents ]
	"anArray = #(string number)"
	raster
		perform: (builderMapping at: anArray first asLowercase asSymbol)
		with: anArray second asNumber
	| contents isHeader |
	contents := aString splitOn: Character space.
	isHeader := contents size = 2 and: [ contents first isNumber not ].
	isHeader
		ifTrue:
			[ self handleHeader: contents ]
		ifFalse: 
			[ self handleData: contents ]

	| parser |
	parser := ESRIParser new.
	parser raster cellSize: 3.
	parser raster numberOfColumns: 4. 
	parser handleData: '1 1 1 2 2 2 3 3 3 4 4 4 '.
	parser raster rows first equals: #(( 1 1 1) (2 2 2 ) (3 3 3) (4 4 4 ))
	""
	raster
		perform: (builderMapping at: anArray first asLowercase asSymbol)
		with: anArray second asNumber
	"anArray = #(string numberizedString)"
	raster
		perform: (builderMapping at: anArray first asLowercase asSymbol)
		with: anArray second asNumber

	| parser |
	parser := ESRIParser new.
	parser raster numberOfColumns: 4. 
	parser handleData: '-9999 -9999 5 2'.
	parser raster rows first equals: #(-9999 -9999 5 2)
	
	| row |
	row := Array new: raster numbersOfColumns.
	"doing it this way I cut extra values that would overflow the columns numbers.
	I could have just iterated on the argument and change its contents too."
	1 to: raster numbersOfColumns do: [ :e | row at: e put: (anArray at: e) asNumber].
	raster addRow: row.
	
	| row |
	row := Array new: raster numberOfColumns.
	"doing it this way I cut extra values that would overflow the columns numbers.
	I could have just iterated on the argument and change its contents too."
	1 to: raster numberOfColumns do: [ :e | row at: e put: (anArray at: e) asNumber].
	raster addRow: row.

	rows add: aRow

	| parser |
	parser := ESRIParser new.
	parser raster numberOfColumns: 4. 
	parser handleData: #('-9999' '-9999' '5' '2').
	parser raster rows first equals: #(-9999 -9999 5 2)

	| parser |
	parser := ESRIParser new.
	parser raster numberOfColumns: 4. 
	parser handleData: #('-9999' '-9999' '5' '2').
	self assert: parser raster rows first equals: #(-9999 -9999 5 2)
	^ lines
	instanceVariableNames: 'raster builderMapping'
	classVariableNames: ''
	poolDictionaries: ''
	category: 'ESRI'

	| parser |
	parser := ESRIParser new.
	parser raster numberOfColumns: 4. 
	parser handleData: #('-9999' '-9999' '5' '2').
	self assert: parser raster rows first equals: #(-9999 -9999 5 2)

	| parser |
	parser := ESRIParser new.
	parser raster numberOfColumns: 4. 
	parser handleData: #('-9999' '-9999' '5' '2').
	self assert: parser raster rows first equals: #(-9999 -9999 5 2)

	| parser |
	parser := ESRIParser new.
	parser parse: 'ncols         4
nrows         6
xllcorner     0.0
yllcorner     0.0
cellsize      50.0
NODATA_value  -9999
-9999 -9999 5 2
-9999 20 100 36
3 8 35 10
32 42 50 6
88 75 27 9
13 5 1 -9999'.
	self assert: parser raster numberOfRows equals: 6.
	self assert: parser raster rows size equals: 6.
	
	self halt.
	numberOfRows := anObject

	| parser |
	parser := ESRIParser new.
	parser parse: 'ncols 4
nrows 6
xllcorner 0.0
yllcorner 0.0
cellsize 50.0
NODATA_value -9999
-9999 -9999 5 2
-9999 20 100 36
3 8 35 10
32 42 50 6
88 75 27 9
13 5 1 -9999'.
	self assert: parser raster numberOfRows equals: 6.
	self assert: parser raster rows size equals: 6.
	
	numberOfRows := anObject

	| parser |
	parser := ESRIParser new.
	parser parse: 'ncols 4
nrows 6
xllcorner 0.0
yllcorner 0.0
cellsize 50.0
NODATA_value -9999
-9999 -9999 5 2
-9999 20 100 36
3 8 35 10
32 42 50 6
88 75 27 9
13 5 1 -9999'.
	self assert: parser raster numberOfRows equals: 6.
	self assert: parser raster rows size equals: 6.
	self assert: parser raster rows last equals: #(13 5 1 -9999)
	