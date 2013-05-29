---
layout: page
title: "API Reference"
date: 2013-05-22 15:50
comments: true
sharing: true
footer: true
author: <a href="http://github.com/justinHume">Justin Hume</a>
---

## List of Modules
This page describes the API for each javascript module in the Readium.js library. 

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
* [EpubReaderModule](#reader-init)
* [render](#reader-render)
* [showSpineItem](#reader-show-spine-item)
* [showPageByCFI](#reader-show-page-by-cfi)
* [showPageByElementId](#reader-show-page-by-element-id)
* [nextPage](#reader-next-page)
* [previousPage](#reader-previous-page)
* [setFontSize](#reader-set-font-size)
* [setMargin](#reader-set-margin)
* [setTheme](#reader-set-theme)
* [setSyntheticLayout](#reader-set-synthetic-layout)
* [getNumberOfPages](#reader-get-number-of-pages)
* [getCurrentPage](#reader-get-current-page)
* [on](#reader-on)
* [off](#reader-off)
* [getViewerSettings](#reader-get-viewer-settings)

***

### [EPUB-Reflowable](#reflowable-api)
_Paginates a reflowable EPUB content document and provides an interface._

#### Events
* [contentDocumentLoaded]()

#### Methods
* [EpubReflowableModule](#reflowable-init)
* [render](#reflowable-render)
* [nextPage](#reflowable-next-page)
* [previousPage](#reflowable-previous-page)
* [showPageByHashFragment](#reflowable-show-page-by-hash-fragment)
* [showPageByNumber](#reflowable-show-page-by-number)
* [showPageByCFI](#reflowable-show-page-by-cfi)
* [onFirstPage](#reflowable-on-first-page)
* [onLastPage](#reflowable-on-last-page)
* [showPagesView](#reflowable-show-pages-view)
* [hidePagesView](#reflowable-hide-pages-view)
* [numberOfPages](#reflowable-number-of-pages)
* [currentPage](#reflowable-current-page)
* [setFontSize](#reflowable-set-font-size)
* [setMargin](#reflowable-set-margin)
* [setTheme](#reflowable-set-theme)
* [setSyntheticLayout](#reflowable-set-synthetic-layout)
* [on](#reflowable-on)
* [off](#reflowable-off)

***

### [EPUB-Fixed](#fixed-api)
_Load and render a set of fixed layout pages, and provides an interface for them._

#### Events
* [contentDocumentLoaded]()

#### Methods
* [EpubFixedModule](#fixed-init)
* [render](#fixed-render)
* [nextPage](#fixed-next-page)
* [previousPage](#fixed-previous-page)
* [showPageByHashFragment](#fixed-show-page-by-hash-fragment)
* [showPageByNumber](#fixed-show-page-by-number)
* [showPageByCFI](#fixed-show-page-by-cfi)
* [onFirstPage](#fixed-on-first-page)
* [onLastPage](#fixed-on-last-page)
* [showPagesView](#fixed-show-pages-view)
* [hidePagesView](#fixed-hide-pages-view)
* [numberOfPages](#fixed-number-of-pages)
* [currentPage](#fixed-current-page)
* [setFontSize](#fixed-set-font-size)
* [setMargin](#fixed-set-margin)
* [setTheme](#fixed-set-theme)
* [setSyntheticLayout](#fixed-set-synthetic-layout)
* [on](#fixed-on)
* [off](#fixed-off)

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

<!-- ==========================================================================================================
        PARSER API DESCRIPTION
     ========================================================================================================== -->

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

<!-- ==========================================================================================================
        EPUB API DESCRIPTION
     ========================================================================================================== -->

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

<!-- ==========================================================================================================
        READER API DESCRIPTION
     ========================================================================================================== -->

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
    epubReader.setTheme(themeName);

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

<!-- ==========================================================================================================
        REFLOWABLE PAGES VIEW API DESCRIPTION
     ========================================================================================================== -->

<a id="reflowable-api"></a>
### Reflowable Pages View

<a id="reflowable-init"></a>
#### EpubReflowableModule
Initialize the set of reflowable pages.

This is a stateful module. State is the _[content document]()_, _viewer settings_, and _[bindings]()_ for the content document. 

{% codeblock .EpubReflowableModule() lang:javascript %}

    var contentDocumentInfo = {
        contentDocumentURI : "epub_content/moby_dick/OPS/chapter_002.xhtml", // path to content document
        title : "Title of the EPUB publication", 
        firstPageIsOffset : false, // boolean
        pageProgressionDirection : "ltr", // "ltr" or "rtl"
        spineIndex : 1, // integer; zero-indexed
        isFixedLayout : false // boolean
    };

    var viewerSettings = {
        fontSize : 12, // integer; one-indexed
        syntheticLayout : true, // boolean
        currentMargin : 3, // integer; one-indexed
        tocVisible : false, // boolean
        currentTheme : "default" // "default", "vancouver-theme", "desert-theme"
    };

    this.view = new EpubReflowableModule(
        contentDocumentInfo,
        viewerSettings,
        bindings
    );

{% endcodeblock %}

<a id="reflowable-render"></a>
#### render
Paginate the [content document]().

This method returns a DOM element that must be injected into the DOM for the rendering process to complete. This is because EPUB content is rendered in an iframe, which only fetches and loads once it's a part of the DOM.

{% codeblock .render(goToLastPage, elementId) lang:javascript %}

    var $domElementToAppendTo = $("#container-id"); // jQuery not required
    var goToLastPage = false; // boolean
    var elementIdToShow = undefined; // Either an ID or undefined
    var pagesElement = reflowablePages.render(false, undefined);
    // Returns a DOM element

    // Inject the element in the DOM
    $domElementToAppendTo.append(pagesElement);

{% endcodeblock %}

<a id="reflowable-next-page"></a>
#### nextPage
Show the next page(s). 

{% codeblock .nextPage() lang:javascript %}

    reflowablePages.nextPage();

{% endcodeblock %}

<a id="reflowable-previous-page"></a>
#### previousPage
Show the previous page(s).

{% codeblock .previousPage() lang:javascript %}

    reflowablePages.previousPage();

{% endcodeblock %}

<a id="reflowable-show-page-by-hash-fragment"></a>
#### showPageByElementId
Show the page that contains the element with the specified ID. 

The spine index must also be supplied, as each spine itemref is likely an XHTML document, and the uniqueness of id's in the EPUB publication is not assured. 

_EXPECTED API CHANGE_: This will be renamed to something like _showPageByElementId_.

{% codeblock .showPageByHashFragment(hashFragmentId) lang:javascript %}

    var elementId = "XML-id";
    reflowablePages.showPageByHashFragment(elementId);

{% endcodeblock %}

<a id="reflowable-show-page-by-number"></a>
#### showPageByNumber
Show the specified page number.

{% codeblock .showPageByNumber(pageNumber) lang:javascript %}

    var pageNumberToShow = 1; // integer; one-indexed
    reflowablePages.showPageByNumber(pageNumberToShow);

{% endcodeblock %}

<a id="reflowable-show-page-by-cfi"></a>
#### showPageByCFI
Show the page on which content indexed by a [CFI]() can be found. 

{% codeblock .showPageByCFI(CFI) lang:javascript %}
    
    var CFI = "epubcfi(/2/6!/4/2/10)";
    reflowablePages.showPageByCFI(CFI);

{% endcodeblock %}

<a id="reflowable-on-first-page"></a>
#### onFirstPage
Indicates if the set of pages is currently showing the first page. 

{% codeblock .onFirstPage() lang:javascript %}

    var onFirstPage = reflowablePages.onFirstPage();
    // Returns a boolean

{% endcodeblock %}

<a id="reflowable-on-last-page"></a>
#### onLastPage
Indicates if the set of pages is currently showing the last page.

{% codeblock .onLastPage() lang:javascript %}

    var onLastPage = reflowablePages.onLastPage();
    // Returns a boolean

{% endcodeblock %}

<a id="reflowable-show-pages-view"></a>
#### showPagesView
Show the set of pages. 

{% codeblock .showPagesView() lang:javascript %}
    
    reflowablePages.showPagesView();

{% endcodeblock %}

<a id="reflowable-hide-pages-view"></a>
#### hidePagesView
Hide the set of pages.

{% codeblock .hidePagesView() lang:javascript %}
    
    reflowablePages.hidePagesView();

{% endcodeblock %}

<a id="reflowable-number-of-pages"></a>
#### numberOfPages
Get the number of pages in the set.

{% codeblock .numberOfPages() lang:javascript %}

    var numberOfPages = reflowablePages.numberOfPages();
    // Returns an integer; one-indexed

{% endcodeblock %}

<a id="reflowable-current-page"></a>
#### currentPage
Get the current page.

{% codeblock .currentPage() lang:javascript %}

    var currentPage = reflowablePages.currentPage();
    // Returns the current page

{% endcodeblock %}

<a id="reflowable-set-font-size"></a>
#### setFontSize
Set the font size for text.

{% codeblock .setFontSize(fontSize) lang:javascript %}

    fontSize = 12; // integer; 1-indexed
    reflowablePages.setFontSize(fontSize);

{% endcodeblock %}

<a id="reflowable-set-margin"></a>
#### setMargin
Set the margin for each page. 

{% codeblock .setMargin(margin) lang:javascript %}

    var margin = 4; // integer; zero-indexed
    reflowablePages.setMargin(margin);

{% endcodeblock %}

<a id="reflowable-set-theme"></a>
#### setTheme
Set the theme for the XHTML content document. 

_EXPECTED API CHANGE_: The way themes are set will likely be changed to give developers more flexibility over which elements are styled.

{% codeblock .setTheme(theme) lang:javascript %}

    var themeName = "default"; // "default", "vancouver-theme", "desert-theme"
    reflowablePages.setTheme(themeName);

{% endcodeblock %}

<a id="reflowable-set-synthetic-layout"></a>
#### setSyntheticLayout
Set a synthetic layout (two pages), or a single-page layout. 

{% codeblock .setSyntheticLayout(isSynthetic) lang:javascript %}

    // Show a two page layout
    reflowablePages.setSyntheticLayout(true);

    // Show a single page layout 
    reflowablePages.setSyntheticLayout(false);

{% endcodeblock %}

<a id="reflowable-on"></a>
#### on
Bind a callback to one of the [events]() fired by the reflowable object. The callback will be invoked whenever the event is triggered. 

This method is delegating to the [backbone.js on(...)]() method, so the interface and semantics will conform closely. 

{% codeblock on(eventName, callback, callbackContext) lang:javascript %} 

    // Bind a callback to the "epubLoaded" event
    reflowablePages.on("epubLoaded", function () {
        console.log("the EPUB publication resources are now loaded and rendered");
    }, this);

{% endcodeblock %}

<a id="reflowable-off"></a>
#### off
Remove all callbacks bound to the module object for the given event name. 

This method is delegating to the [backbone.js of(...)]() method, so the interface and semantics will conform closely.

{% codeblock .off(eventName) lang:javascript %}

    reflowablePages.off("epubLoaded");

{% endcodeblock %}

<!-- ==========================================================================================================
        FIXED PAGES VIEW API DESCRIPTION
     ========================================================================================================== -->

<a id="fixed-api"></a>
## Fixed Pages View

<a id="fixed-init"></a>
#### EpubFixedModule

Initialize a set of fixed pages.

This is a stateful module. State is the _set of [fixed layout pages]()_ passed to the module, and the _viewer settings_;

The spineObject is an array of objects that contain information about a [spine itemref](). The number of spine objects passed to the module can be anything greater than 1, within system/language limits.

{% codeblock .EpubFixedModule(spineObjects, viewerSettingsObject) lang:javascript %}

    var spineObjects = [
        {
            contentDocumentURI: "epub_content/page-blanche-20121022/EPUB/Content/cover.xhtml",
            firstPageIsOffset: false,
            fixedLayoutType: "xhtml",
            isFixedLayout: true,
            mediaType: "application/xhtml+xml",
            pageProgressionDirection: "ltr",
            pageSpread: "left",
            spineIndex: 0,
            title: "Page Blanche"
        },
        ...
        {
            contentDocumentURI: "epub_content/page-blanche-20121022/EPUB/Content/PageBlanche_Page_008.xhtml",
            firstPageIsOffset: false,
            fixedLayoutType: "xhtml",
            isFixedLayout: true,
            mediaType: "application/xhtml+xml",
            pageProgressionDirection: "ltr",
            pageSpread: "right",
            spineIndex: 9,
            title: "Page Blanche"
        }
    ];

    var viewerSettings = {
        fontSize : 12,
        syntheticLayout : false,
        currentMargin : 3,
        tocVisible : false,
        currentTheme : "default"
    };

    var fixedPages = new EpubFixedModule(
        spineObjects,
        viewerSettings
    );

{% endcodeblock %}

<a id="fixed-render"></a>
#### render

Render and size the [fixed layout pages]().

This method returns a DOM element that must be injected into the DOM for the rendering process to complete. This is because EPUB content is rendered in an iframe, which only fetches and loads once it's a part of the DOM.

{% codeblock .render(goToLastPage, elementId) lang:javascript %}

    var $domElementToAppendTo = $("#container-id"); // jQuery not required
    var goToLastPage = false; // boolean
    var elementIdToShow = undefined; // Either an ID or undefined
    var pagesElement = fixedPages.render(false, undefined);
    // Returns a DOM element

    // Inject the element in the DOM
    $domElementToAppendTo.append(pagesElement);

{% endcodeblock %}

<a id="fixed-next-page"></a>
#### nextPage
Show the next page(s). 

{% codeblock .nextPage() lang:javascript %}

    fixedPages.nextPage();

{% endcodeblock %}

<a id="fixed-previous-page"></a>
#### previousPage
Show the previous page(s).

{% codeblock .previousPage() lang:javascript %}

    fixedPages.previousPage();

{% endcodeblock %}

<a id="fixed-show-page-by-hash-fragment"></a>
#### showPageByElementId
Show the page that contains the element with the specified ID. 

The spine index must also be supplied, as each spine itemref is likely an XHTML document, and the uniqueness of id's in the EPUB publication is not assured. 

_EXPECTED API CHANGE_: This will be renamed to something like _showPageByElementId_.

{% codeblock .showPageByHashFragment(hashFragmentId) lang:javascript %}

    var elementId = "XML-id";
    fixedPages.showPageByHashFragment(elementId);

{% endcodeblock %}

<a id="fixed-show-page-by-number"></a>
#### showPageByNumber
Show the specified page number.

{% codeblock .showPageByNumber(pageNumber) lang:javascript %}

    var pageNumberToShow = 1; // integer; one-indexed
    fixedPages.showPageByNumber(pageNumberToShow);

{% endcodeblock %}

<a id="fixed-show-page-by-cfi"></a>
#### showPageByCFI
Show the page on which content indexed by a [CFI]() can be found. 

{% codeblock .showPageByCFI(CFI) lang:javascript %}
    
    var CFI = "epubcfi(/2/6!/4/2/10)";
    fixedPages.showPageByCFI(CFI);

{% endcodeblock %}
<a id="fixed-on-first-page"></a>
#### onFirstPage
Indicates if the set of pages is currently showing the first page. 

{% codeblock .onFirstPage() lang:javascript %}

    var onFirstPage = fixedPages.onFirstPage();
    // Returns a boolean

{% endcodeblock %}

<a id="fixed-on-last-page"></a>
#### onLastPage
Indicates if the set of pages is currently showing the last page.

{% codeblock .onLastPage() lang:javascript %}

    var onLastPage = fixedPages.onLastPage();
    // Returns a boolean

{% endcodeblock %}

<a id="fixed-show-pages-view"></a>
#### showPagesView
Show the set of pages. 

{% codeblock .showPagesView() lang:javascript %}
    
    fixedPages.showPagesView();

{% endcodeblock %}

<a id="fixed-hide-pages-view"></a>
#### hidePagesView
Hide the set of pages.

{% codeblock .hidePagesView() lang:javascript %}
    
    fixedPages.hidePagesView();

{% endcodeblock %}

<a id="fixed-number-of-pages"></a>
#### numberOfPages
Get the number of pages in the set.

{% codeblock .numberOfPages() lang:javascript %}

    var numberOfPages = fixedPages.numberOfPages();
    // Returns an integer; one-indexed

{% endcodeblock %}

<a id="fixed-current-page"></a>
#### currentPage
Get the current page.

{% codeblock .currentPage() lang:javascript %}

    var currentPage = fixedPages.currentPage();
    // Returns the current page

{% endcodeblock %}

<a id="fixed-set-font-size"></a>
#### setFontSize
Set the font size for text.

{% codeblock .setFontSize(fontSize) lang:javascript %}

    fontSize = 12; // integer; 1-indexed
    fixedPages.setFontSize(fontSize);

{% endcodeblock %}

<a id="fixed-set-margin"></a>
#### setMargin
Set the margin for each page. 

{% codeblock .setMargin(margin) lang:javascript %}

    var margin = 4; // integer; zero-indexed
    fixedPages.setMargin(margin);

{% endcodeblock %}

<a id="fixed-set-theme"></a>
#### setTheme
Set the theme for the XHTML content document. 

_EXPECTED API CHANGE_: The way themes are set will likely be changed to give developers more flexibility over which elements are styled.

{% codeblock .setTheme(theme) lang:javascript %}

    var themeName = "default"; // "default", "vancouver-theme", "desert-theme"
    fixedPages.setTheme(themeName);

{% endcodeblock %}

<a id="fixed-set-synthetic-layout"></a>
#### setSyntheticLayout
Set a synthetic layout (two pages), or a single-page layout. 

{% codeblock .setSyntheticLayout(isSynthetic) lang:javascript %}

    // Show a two page layout
    fixedPages.setSyntheticLayout(true);

    // Show a single page layout 
    fixedPages.setSyntheticLayout(false);

{% endcodeblock %}

<a id="fixed-on"></a>
#### on
Bind a callback to one of the [events]() fired by the fixed object. The callback will be invoked whenever the event is triggered. 

This method is delegating to the [backbone.js on(...)]() method, so the interface and semantics will conform closely. 

{% codeblock on(eventName, callback, callbackContext) lang:javascript %} 

    // Bind a callback to the "epubLoaded" event
    fixedPages.on("epubLoaded", function () {
        console.log("the EPUB publication resources are now loaded and rendered");
    }, this);

{% endcodeblock %}

<a id="fixed-off"></a>
#### off
Remove all callbacks bound to the module object for the given event name. 

This method is delegating to the [backbone.js of(...)]() method, so the interface and semantics will conform closely.

{% codeblock .off(eventName) lang:javascript %}

    fixedPages.off("epubLoaded");

{% endcodeblock %}


<!-- ==========================================================================================================
        EPUB CFI API DESCRIPTION
     ========================================================================================================== -->

### EPUB Canonical Fragment Identifiers

