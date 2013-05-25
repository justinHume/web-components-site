---
layout: page
title: "API Reference"
date: 2013-05-22 15:50
comments: true
sharing: true
footer: true
author: Justin Hume
---

## List of Modules
This page describes the API for each javascript module in the Readium Web Components library. 

A list - and example of use - is provided for the custom styles, events and methods of each module.

*** 

### [EPUB-Parser](#parser-api)
_Parse an EPUB 3.0 XML Package Document into javascript objects._

#### Methods
* [EpubParserModule](#parser-init)
* [parse](#parser-parse)

***

### [EPUB](#epub-api)
_Expose useful information about an EPUB and it's resources._

#### Methods
* [EpubModule](#epub-init)
* [getSpineInfo](#epub-getSpineInfo)
* [isFixedLayout](#epub-isFixedLayout)
* [getManifestItemById](#epub-getManifestItemById)
* [getManifestItemByIdref](#epub-getManifestItemByIdref)
* [getSpineItemByIdref](#epub-getSpineItemByIdref)
* [getSpineItemByIndex](#epub-getSpineItemByIndex)
* [spineLength](#epub-spineLength)
* [getNextLinearSpinePosition](#epub-getNextLinearSpinePosition)
* [getPrevLinearSpinePosition](#epub-getPrevLinearSpinePosition)
* [hasNextSection](#epub-hasNextSection)
* [hasPrevSection](#epub-hasPrevSection)
* [pageProgressionDirection](#epub-pageProgressionDirection)
* [getSpineIndexByHref](#epub-getSpineIndexByHref)
* [getPackageDocumentDOM](#epub-getPackageDocumentDOM)
* [getToc](#epub-getToc)

***

### [EPUB-Reader]("#epub-reader")
_Manage the loading, rendering and interaction with EPUB 3.0 content._

#### Events
* [epubLoaded]("")

#### Methods
* [new EpubReaderModule(readerBoundElement, epubSpineInfo, viewerSettings, packageDocumentDOM)]("")
* [render()]("")
* [showSpineItem(spineIndex)]("")
* [showPageByCFI(CFI)]("")
* [showPageByElementId(spineIndex, hashFragmentId)]("")
* [nextPage()]("")
* [previousPage()]("")
* [setFontSize(fontSize)]("")
* [setMargin()]("")
* [setTheme()]("")
* [setSyntheticLayout(isSynthetic)]("")
* [getNumberOfPages()]("")
* [getCurrentPage()]("")
* [on(eventName, callback, callbackContext)]("")
* [off(eventName)]("")
* [getViewerSettings()]("")

***

### [EPUB-Reflowable]("#epub-reflowable")
_Paginates a reflowable EPUB content document and provides an interface._

#### Events
* [contentDocumentLoaded]()

#### Methods
* [new EpubReflowableModule(spineObject, viewerSettingsObject, CFIAnnotations, bindings)]("")
* [render()]("")
* [nextPage()]("")
* [previousPage()]("")
* [showPageByHashFragment(hashFragmentId)]("")
* [showPageByNumber(pageNumber)]("")
* [showPageByCFI(CFI)]()
* [onFirstPage()]()
* [onLastPage()]()
* [showPagesView()]()
* [hidePagesView()]()
* [numberOfPages()]()
* [currentPage()]()
* [setFontSize(fontSize)]()
* [setMargin(margin)]()
* [setTheme(theme)]()
* [setSyntheticLayout(isSynthetic)]()
* [on(eventName, callback, callbackContext)]()
* [off(eventName)]()

***

### [EPUB-Fixed]("#epub-fixed")
_Load and render a set of fixed layout pages, and provides an interface for them._

#### Events
* [contentDocumentLoaded]()

#### Methods
* [new EpubFixedModule(spineObjects, viewerSettingsObject)]()
* [render()]()
* [nextPage()]()
* [previousPage()]()
* [showPageByHashFragment(hashFragmentId)]()
* [showPageByNumber(pageNumber)]()
* [showPageByCFI(CFI)]()
* [onFirstPage()]()
* [onLastPage()]()
* [showPagesView()]()
* [hidePagesView()]()
* [numberOfPages()]()
* [currentPage()]()
* [setFontSize(fontSize)]()
* [setMargin(margin)]()
* [setTheme(theme)]()
* [setSyntheticLayout(isSynthetic)]()
* [on(eventName, callback, callbackContext)]()
* [off(eventName)]()

***

### [EPUB-CFI]("#epub-cfi")
_De-reference and generate Canonical Fragement Identifiers (CFIs)._

#### Methods
* [new EpubCFIModule()]("")
* [getContentDocHref(CFI, packageDocument)]("")
* [injectElement(CFI, contentDocument, elementToInject)]("")
* [getTargetElement(CFI, contentDocument)]("")
* [getTargetElementWithPartialCFI(contentDocumentCFI, contentDocument)]("")
* [getTextTerminusInfoWithPartialCFI(contentDocumentCFI, contentDocument)]("")
* [generateCharacterOffsetCFIComponent(startTextNode, charOffset)]("")
* [generateElementCFIComponent(startElement)]("")
* [generatePackageDocumentCFIComponent(contentDocumentName, packageDocument)]("")
* [generatePackageDocumentCFIComponentWithSpineIndex(spineIndex, packageDocument)]("")
* [generateCompleteCFI(packageDocumentCFIComponent, contentDocumentCFIComponent)]("")
* [injectElementAtOffset($textNodeList, textOffset, elementToInject)]("")
* [injectRangeElements(rangeCFI, contentDocument, startElementToInject, endElementToInject)]("")
* [getRangeTargetElements(rangeCFI, contentDocument)]("")
* [generateCharOffsetRangeComponent(rangeStartElement, startOffset, rangeEndElement, endOffset)]("")
* [generateElementRangeComponent(rangeStartElement, rangeEndElement)]("")

***

<a id="parser-api"></a>
## Parser API

<a id="parser-init"></a>
#### EpubParserModule
Instantiate a new parser module. Use a constructor method invocation. The surrounding application is responsible for retrieving the package document XML.

This is a stateful module. State is the _path to the package document_ and the _package document XML_.

{% codeblock new EpubParserModule() lang:javascript %}

var pathToPackageDocument = "path/to/EPUB/packageDocument.xml" // A string
var packageDocumentXML = yourApp.getPackageDocumentXML(pathToPackageDocument); // A string

var epubParser = new EpubParserModule({ 
    packageDocumentURI : pathToPackageDocument,
    packageDocumentXML : packageDocumentXML
});

{% endcodeblock %}

<a id="parser-parse"></a>
#### parse
Parse the package document into a javascript object. 

{% codeblock .parse() lang:javascript %}

var packageDocumentObject = epubParser.parse();
// Returns a javascript object representation of the package document

{% endcodeblock %}

<a id="epub-api"></a>
## EPUB

<a id="epub-init"></a>
#### EpubModule
Instantiate the epub module. Use a constructor method invocation.

This is a stateful module. State is the _path to the package document_ and the _package document_.

_EXPECTED API CHANGE_: At the moment, the EPUB-Parser module must be used to create a javascript object representation of the package document; this will be changed. The parser will simply be included in the EPUB module. 

{% codeblock new EpubModule(packageDocumentObject, packageDocumentXML) lang:javascript %}

var packageDocumentXML = yourApp.getPackageDocumentXML(pathToPackageDocument); // A string
var packageDocumentObject = anInstantiatedEpubParser.parse();

var theEpub = new EpubModule(packageDocumentObject, packageDocumentXML);

{% endcodeblock %}

<a id="epub-getSpineInfo"></a>
#### getSpineInfo
Get the spine info object. The spine info object contains three arrays: An _array of each [itemref]()_ in the [spine](), an _array of [bindings]()_.

{% codeblock .getSpineInfo() lang:javascript %}

var spineInfo = theEpub.getSpineInfo();
// Returns the spineInfo object {
//      spine : [itemrefs],
//      bindings : [bindings]
// }

{% endcodeblock %}

<a id="epub-isFixedLayout"></a>
#### isFixedLayout
Indicates if the _entire_ EPUB is fixed layout. 

This will only return true if the [fixed layout meta property]() is set. If the EPUB
is mixed (contains both reflowable and fixed layout content documents), or entirely reflowable, this will return false. 

{% codeblock %}

var isFXL = theEpub.isFixedLayout();
// Returns true or false

{% endcodeblock %}

<a id="epub-getManifestItemById"></a>
#### getManifestItemById
Get a [manifest item]() object using it's XML id. 

{% codeblock .getManifestItemById(id) lang:javascript %}

var id = "valid-XML-id";
var manifestItemObject = theEpub.getManifestItemById(id)
// Returns an object {
//      href : "package document-relative path to the manifest item resource",
//      id : "the XML id",
//      media_overlay : "mo.smil",
//      media_type : "the MIME type of the resource",
//      properties : "the EPUB property string for the manifest item"
// }

{% endcodeblock%}

<a id="epub-getManifestItemByIdref"></a>
#### getManifestItemByIdref
Get a [manifest item]() object by using the [spine itemref idref]() that refers to it.

{% codeblock .getManifestItemByIdref(idref) lang:javascript %}

var idref = "idref-to-manifest-item";
var manifestItemObject = theEpub.getManifestItemByIdref(idref)
// Returns an object {
//      href : "package document-relative path to the manifest item resource",
//      id : "the XML id",
//      media_overlay : "mo.smil",
//      media_type : "the MIME type of the resource",
//      properties : "the EPUB property string for the manifest item"
// }

{% endcodeblock %}

<a id="epub-getSpineItemByIdref"></a>
#### getSpineItemByIdref
Get an [itemref]() object by using the itemref's idref. 

_EXPECTED API CHANGE_: This method will likely be renamed to getSpineItem___ref___ByIdref.

{% codeblock .getSpineItemByIdref(idref) lang:javascript %}

var idref = "idref-to-spine-itemref";
var spineItemrefObject = theEpub.getSpineItemByIdref(idref)
// Returns an object {
//      id : "ch9",
//      idref : "ch9",
//      properties : "the EPUB 3.0 property string for the spine itemref",
//      linear : "the is linear string"
// }

{% endcodeblock %}

<a id="epub-getSpineItemByIndex"></a>
#### getSpineItemByIndex
Get an [itemref]() object by using the itemref's index in the package document [spine](). 

_EXPECTED API CHANGE_: This method will likely be renamed to getSpineItem___ref___ByIndex.

{% codeblock .getSpineItemByIndex(spineIndex) lang:javascript %}

var spineIndex = 0; // integer; zero-indexed
var spineItemrefObject = theEpub.getSpineItemByIndex(spineIndex)
// Returns an object {
//      id : "ch9",
//      idref : "ch9",
//      properties : "the EPUB 3.0 property string for the spine itemref",
//      linear : "the is linear string"
// }

{% endcodeblock %}

<a id="epub-getSpineIndexByHref"></a>
#### getSpineIndexByHref
Get the spine index of the [itemref]() using it's associated manifest [item]() href.

{% codeblock .getSpineIndexByHref(manifestItemHref) %}
    
    var manifestItemHref = "item-href"; // A string
    var spineIndexOfItemref = theEpub.getSpineIndexByHref(manifestItemHref); 
    // Returns an integer; zero-indexed

{% endcodeblock %}

<a id="epub-spineLength"></a>
#### spineLength
Get the number of [itemrefs]() in the [spine]().

_EXPECTED API CHANGE_: This method will be renamed to something like _getNumberOfItemrefs_.

{% codeblock %}

var numSpineItemrefs = theEpub.spineLength();
// Returns an integer; one-indexed

{% endcodeblock %}

<a id="epub-getNextLinearSpinePosition"></a>
#### getNextLinearSpinePosition
Get the index in the spine of the next [primary]() spine itemref.

_EXPECTED API CHANGE_: This method will be renamed to something like _getNextPrimarySpineIndex_. This method may also be changed to actually return the itemref object. 

{% codeblock .getNextLinearSpinePosition(startSpineIndex) lang:javascript %}

var startSpineIndex = 0; // integer; zero-indexed
var nextPrimarySpineIndex = theEpub.getNextLinearSpinePosition(startSpineIndex);
// Returns an integer; zero-indexed

{% endcodeblock %}

<a id="epub-getPrevLinearSpinePosition"></a>
#### getPrevLinearSpinePosition
Get the index in the spine of the previous [primary]() spine itemref.

_EXPECTED API CHANGE_: This method will be renamed to something like _getPreviousPrimarySpineIndex_. This method may also be changed to actually return the itemref object. 

{% codeblock .getPrevLinearSpinePosition(startSpineIndex) lang:javascript %}

var startSpineIndex = 0; // integer; zero-indexed
var nextPrimarySpineIndex = theEpub.getPrevLinearSpinePosition(startSpineIndex);
// Returns an integer; zero-indexed

{% endcodeblock %}

<a id="epub-hasNextSection"></a>
#### hasNextSection
Indicates if the EPUB has another [primary]() itemref.

_EXPECTED API CHANGE_: This method will likely be renamed to _hasNextItemref_.

{% codeblock .hasNextSection() lang:javascript %}

var startSpineIndex = 0; // integer; zero-indexed
var hasNextItemref = theEpub.hasNextSection(startSpineIndex);
// Returns true or false

{% endcodeblock %} 

<a id="epub-hasPrevSection"></a>
#### hasPrevSection
Indicates if the EPUB has a previous [primary]() itemref.

_EXPECTED API CHANGE_: This method will likely be renamed to _hasPreviousItemref_.

{% codeblock .hasPrevSection() lang:javascript %}

var startSpineIndex = 0; // integer; zero-indexed
var hasNextItemref = theEpub.hasPrevSection(startSpineIndex);
// Returns true or false

{% endcodeblock %} 

<a id="epub-pageProgressionDirection"></a>
#### pageProgressionDirection
Gets the [page progression direction]() of the EPUB.

_EXPECTED API CHANGE_: This method will be renamed to something like _getPageProgressionDirection_.

{% codeblock .pageProgressionDirection() lang:javascript %}

var pageProgDir = theEpub.pageProgressionDirection();
// Returns "ltr", "default", or "rtl"

{% endcodeblock %}

<a id="epub-getPackageDocumentDOM"></a>
#### getPackageDocumentDOM
Gets a Document Object Model representation of the package document.

{% codeblock .getPackageDocumentDOM() lang:javascript %}

var packageDocumentDOM = theEpub.getPackageDocumentDOM();
// Returns a DOM object with the <package> element as the root of the object.

{% endcodeblock %}

<a id="epub-getToc"></a>
#### getToc
Gets the URL of the [table of contents]() manifest [item]().

_EXPECTED API CHANGE_: This method will be renamed to something like _getTocHref_.

{% codeblock .getToc() lang:javascript %}

var tocHref = theEpub.getToc();
// Returns a string; the href for the table of contents manifest item

{% endcodeblock %}

### EPUB Reader

### Reflowable Pages View

### Fixed Pages View

### EPUB Canonical Fragment Identifiers

