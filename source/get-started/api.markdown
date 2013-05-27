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

### [EPUB-Reader](#reader-api)
_Manage the loading, rendering and interaction with EPUB 3.0 content._

#### Events
* [epubLoaded]("")

#### Methods
* [new EpubReaderModule(readerBoundElement, epubSpineInfo, viewerSettings, packageDocumentDOM)](#reader-init)
* [render()](#reader-render)
* [showSpineItem(spineIndex)](#reader-show-spine-item)
* [showPageByCFI(CFI)](#reader-show-page-by-cfi)
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

<a id="reader-api"></a>
## EPUB Reader API

<a id="reader-init"></a>
#### EpubReaderModule
Instantiate a new reader module. Use a constructor method invocation. 

The reader requires a DOM element to bind EPUB content to, the EPUB publication [spine info]() object, a viewer settings object, and a [DOM representation]() of the package document.

This is a stateful module. State is the _DOM element to bind to_, the epub resources referenced by the _epub spine info_ object, and _viewer settings_. 


------------- Write something in here about fixed size for the binding element

{% codeblock new EpubReaderModule(readerBoundElement, epubSpineInfo, viewerSettings, packageDocumentDOM) lang:javascript %}

    var elementToBindTo = $("#element-id")[0]; // A DOM element; jquery is not required
    var spineInfo = theEpub.getSpineInfo(); // theEpub is an RWC EPUB module.
    var viewerSettings = {
            fontSize : 12, // integer
            syntheticLayout : false, // boolean
            currentMargin : 3, // integer
            tocVisible : false, // boolean
            currentTheme : "default" // "default", "vancouver-theme", "desert-theme"
        };
    var packageDocumentDOM = theEpub.getPackageDocumentDOM();

    var epubReader = new EpubReaderModule(
            elementToBindTo,
            spineInfo,
            viewerSettings,
            packageDocumentDOM
        ); 

{% endcodeblock %}

<a id="reader-render"></a>
#### render
Load and render EPUB publication resources. When render() is called, RWC will inject DOM elements as children of the [binding element]() passed on initialization. 

By default, all EPUB resources will be hidden. A [show]() method must be called to display a part of the EPUB publication.

The EPUB-Reader module will trigger an "epubLoaded" event when all the resources of the EPUB are loaded. Use the [on]() method to handle the event. 

_EXPECTED API CHANGE_: Loading and rendering settings, eager vs lazy loading

{% codeblock .render() lang:javascript %}

    epubReader.on("epubLoaded", function () {
        epubReader.showSpineItem(0);
    }, this);

    epubReader.render();

{% endcodeblock %}

<a id="reader-show-spine-item"></a>
#### showSpineItem
Show EPUB content using it's index in the spine.

{% codeblock showSpineItem(spineIndex) lang:javascript %}

    var spineIndexToShow = 0; // integer; zero-indexed
    epubReader.showSpineItem(spineIndexToShow);

{% endcodeblock %}

<a id="reader-show-page-by-cfi"></a>
#### showPageByCFI
Show the page on which content indexed by a [CFI]() can be found. 

{% codeblock showPageByCFI(CFI) lang:javascript %}
    
    var CFI = "epubcfi(/2/6!/4/2/10)";
    epubReader.showPageByCFI(CFI);

{% endcodeblock %}

<a id="reader-show-page-by-element-id"></a>
#### showPageByElementId
Show the page that contains the element with the specified ID. 

The spine index must also be supplied, as each spine itemref is likely an XHTML document, and the uniqueness of id's in the EPUB publication is not assured. 

{% codeblock showPageByElementId(spineIndex, hashFragmentId) lang:javascript %}

    var spineIndexThatContainsTheId = 0; // integer; zero-indexed
    var elementId = "XML-id";
    epubReader.showPageByElementId(spineIndexThatContainsTheId, elementId);

{% endcodeblock %}

<a id="reader-next-page"></a>
#### nextPage
Show the next page(s) in the EPUB publication. 

{% codeblock .nextPage() lang:javascript %}

    epubReader.nextPage();

{% endcodeblock %}

<a id="reader-previous-page"></a>
#### previousPage
Show the previous page(s) in the EPUB publication.

{% codeblock .previousPage() lang:javascript %}

    epubReader.previousPage();

{% endcodeblock %}

<a id="reader-set-font-size"></a>
#### setFontSize
Set the font size for text.

{% codeblock .setFontSize(fontSize) lang:javascript %}

    fontSize = 12; // integer; 1-indexed
    epubReader.setFontSize(fontSize);

{% endcodeblock %}

<a id="reader-set-margin"></a>
#### setMargin
Set the margin for each page. 

{% codeblock .setMargin(margin) lang:javascript %}

    var margin = 4; // integer; zero-indexed
    epubReader.setMargin(margin);

{% endcodeblock %}

<a id="reader-set-theme"></a>
#### setTheme
Set the theme for the XHTML content document. 

_EXPECTED API CHANGE_: The way themes are set will likely be changed to give developers more flexibility over which elements are styled. 

{% codeblock .setTheme(theme) lang:javascript %}

    var themeName = "default"; // "default", "vancouver-theme", "desert-theme"

{% endcodeblock %}

<a id="reader-set-synthetic-layout"></a>
#### setSyntheticLayout
Set the reader to display a synthetic layout (two pages), or a single-page layout. 

{% codeblock .setSyntheticLayout(isSynthetic) lang:javascript %}

    // Show a two page layout
    epubReader.setSyntheticLayout(true);

    // Show a single page layout 
    epubReader.setSyntheticLayout(false);

{% endcodeblock %}

<a id="reader-get-number-of-pages"></a>
#### getNumberOfPages
Get the number of pages, which is *potentially* a function of the current screen size, for the entire EPUB publication.

_EXPECTED API CHANGE_: This method is a candidate for removal. I don't really think the meaning of this method can be made clear (or useful), given some of the other design decisions that have been made for this module, as well as some of the general complexity imposed by the EPUB spec.

{% codeblock .getNumberOfPages() lang:javascript %}
    
    var currentNumberOfPages = epubReader.getNumberOfPages();    

{% endcodeblock %}

<a id="reader-get-current-page"></a>
#### getCurrentPage 
Gets an array that contains the currently displayed page(s).

_EXPECTED API CHANGE_: This method is a candidate for removal. I don't really think the meaning of this method can be made clear (or useful), given some of the other design decisions that have been made for this module, as well as some of the general complexity imposed by the EPUB spec.

{% codeblock .getCurrentPage() lang:javascript %}
    
    var currentPage = epubReader.getCurrentPage();
    // Returns an array with one or two elements [page1 [, page2] ]

{% endcodeblock %}

<a id="reader-on"></a>
#### on
Bind a callback to one of the [events]() fired by the reader module. The callback will be invoked whenever the event is triggered. 

This method is delegating to the [backbone.js on(...)]() method, so the interface and semantics will conform closely. 

{% codeblock on(eventName, callback, callbackContext) lang:javascript %} 

    // Bind a callback to the "epubLoaded" event
    epubReader.on("epubLoaded", function () {
        console.log("the EPUB publication resources are now loaded and rendered");
    }, this);

{% endcodeblock %}

<a id="reader-off"></a>
#### off
Remove all callbacks bound to the module object for the given event name. 

This method is delegating to the [backbone.js of(...)]() method, so the interface and semantics will conform closely.

{% codeblock .off(eventName) lang:javascript %}

    epubReader.off("epubLoaded");

{% endcodeblock %}

<a id="reader-get-viewer-settings"></a>
#### getViewerSettings
Get the viewer settings object currently maintained by the reader. 

The reader must preserve viewer settings state internally; this method returns that internal state.

{% codeblock .getViewerSettings() lang:javascript %}
    
    var currViewerSettings = epubReader.getViewerSettings();
    // Returns an object {
    //      fontSize : 12, // integer
    //      syntheticLayout : false, // boolean
    //      currentMargin : 3, // integer
    //      tocVisible : false, // boolean
    //      currentTheme : "default" // "default", "vancouver-theme", "desert-theme"
    //    }

{% endcodeblock %}


### Reflowable Pages View

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

### Fixed Pages View

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

### EPUB Canonical Fragment Identifiers

