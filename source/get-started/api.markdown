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

### [SimpleReadium](#simple-api)
_A module that wires together all of Readium.js into one object and exposes a reduced, simplified, API._

#### [Events](#simple-events-example)
* [epubLoaded](#simple-epub-loaded)
* [atNextPage](#simple-at-next-page)
* [atPreviousPage](#simple-at-previous-page)
* [atFirstPage](#simple-at-first-page)
* [atLastPage](#simple-at-last-page)
* [epubLinkClicked](#simple-epub-link-clicked)
* [layoutChanged](#simple-layout-changed)
* [displayedContentChanged](#simple-displayed-content-changed)

#### [Customizable styles](#simple-custom-styles-example)
* [epub-border](#simple-epub-border)
* [spine-divider](#simple-spine-divider)
* [page-border](#simple-page-border)
* [margin](#simple-margin)
* [fontSize](#simple-font-size)
* [reflowable-epub-border](#simple-reflowable-epub-border)
* [reflowable-spine-divider](#simple-reflowable-spine-divider)
* [reflowable-page-border](#simple-reflowable-page-border)
* [reflowable-page-theme](#simple-reflowable-page-theme)
* [fixed-epub-border](#simple-epub-border)
* [fixed-spine-divider](#simple-spine-divider)
* [fixed-page-border](#simple-page-border)
* [fixed-page-border-left](#simple-page-border-left)
* [fixed-page-border-right](#simple-page-border-right)

#### Methods
* [SimpleRWC](#simple-init)
* [showSpineItem](#simple-show-spine-item)
* [showPageByCFI](#simple-show-page-by-cfi)
* [showPageByElementId](#simple-show-page-by-element-id)
* [previousPage](#simple-previous-page)
* [nextPage](#simple-next-page)
* [setSyntheticLayout](#simple-set-synthetic-layout)
* [setMargin](#simple-set-margin)
* [setTheme](#simple-set-theme)
* [resizeContent](#simple-resize-content)
* [customize](#simple-customize)

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

#### [Events](#reader-events-example)
* [epubLoaded](#reader-epub-loaded)
* [atNextPage](#reader-at-next-page)
* [atPreviousPage](#reader-at-previous-page)
* [atFirstPage](#reader-at-first-page)
* [atLastPage](#reader-at-last-page)
* [epubLinkClicked](#reader-epub-link-clicked)
* [layoutChanged](#reader-layout-changed)
* [displayedContentChanged](#reader-displayed-content-changed)

#### [Customizable styles](#reader-custom-styles-example)
* [epub-border](#reader-epub-border)
* [spine-divider](#reader-spine-divider)
* [page-border](#reader-page-border)
* [margin](#reader-margin)
* [fontSize](#reader-font-size)
* [reflowable-epub-border](#reader-epub-border)
* [reflowable-spine-divider](#reader-spine-divider)
* [reflowable-page-border](#reader-page-border)
* [reflowable-page-theme](#reader-page-theme)
* [fixed-epub-border](#reader-epub-border)
* [fixed-spine-divider](#reader-spine-border)
* [fixed-page-border](#reader-page-border)
* [fixed-page-border-left](#reader-page-border-left)
* [fixed-page-border-right](#reader-page-border-right)

#### Methods
* [EpubReaderModule](#reader-init)
* [render](#reader-render)
* [showSpineItem](#reader-show-spine-item)
* [showPageByCFI](#reader-show-page-by-cfi)
* [showPageByElementId](#reader-show-page-by-element-id)
* [nextPage](#reader-next-page)
* [previousPage](#reader-previous-page)
* [setSyntheticLayout](#reader-set-synthetic-layout)
* [getNumberOfPages](#reader-get-number-of-pages)
* [getCurrentPage](#reader-get-current-page)
* [on](#reader-on)
* [off](#reader-off)
* [getViewerSettings](#reader-get-viewer-settings)
* [resizeContent](#reader-resize-content)
* [customize](#reader-customize)

***

### [EPUB-Reflowable](#reflowable-api)
_Paginates a reflowable EPUB [content document](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#sec-overview) and provides an interface._

#### [Events](#reflowable-events-example)
* [epubLoaded](#reflowable-epub-loaded)
* [atNextPage](#reflowable-at-next-page)
* [atPreviousPage](#reflowable-at-previous-page)
* [atFirstPage](#reflowable-at-first-page)
* [atLastPage](#reflowable-at-last-page)
* [epubLinkClicked](#reflowable-epub-link-clicked)
* [layoutChanged](#reflowable-layout-changed)
* [displayedContentChanged](#reflowable-displayed-content-changed)

#### [Customizable styles](#reflowable-custom-styles-example)
* [epub-border](#reflowable-epub-border)
* [spine-divider](#reflowable-spine-divider)
* [page-border](#reflowable-page-border)
* [margin](#reflowable-margin)
* [fontSize](#reflowable-font-size)
* [reflowable-epub-border](#reflowable-reflowable-epub-border)
* [reflowable-spine-divider](#reflowable-reflowable-spine-divider)
* [reflowable-page-border](#reflowable-reflowable-page-border)
* [reflowable-page-theme](#reflowable-reflowable-page-theme)

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
* [setSyntheticLayout](#reflowable-set-synthetic-layout)
* [on](#reflowable-on)
* [off](#reflowable-off)
* [resizeContent](#reflowable-resize-content)
* [customize](#reflowable-customize)

***

### [EPUB-Fixed](#fixed-api)
_Loads and renders a set of fixed layout pages, and provides an interface for them._

#### [Events](#fixed-events-example)
* [epubLoaded](#fixed-epub-loaded)
* [atNextPage](#fixed-at-next-page)
* [atPreviousPage](#fixed-at-previous-page)
* [atFirstPage](#fixed-at-first-page)
* [atLastPage](#fixed-at-last-page)
* [epubLinkClicked](#fixed-epub-link-clicked)
* [layoutChanged](#fixed-layout-changed)
* [displayedContentChanged](#fixed-displayed-content-changed)

#### [Customizable styles](#fixed-custom-styles-example)
* [epub-border](#fixed-epub-border)
* [spine-divider](#fixed-spine-divider)
* [page-border](#fixed-page-border)
* [fixed-epub-border](#fixed-fixed-epub-border)
* [fixed-spine-divider](#fixed-fixed-spine-divider)
* [fixed-page-border](#fixed-fixed-page-border)
* [fixed-page-border-left](#fixed-fixed-page-border-left)
* [fixed-page-border-right](#fixed-fixed-page-border-right)

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
* [setSyntheticLayout](#fixed-set-synthetic-layout)
* [on](#fixed-on)
* [off](#fixed-off)
* [resizeContent](#fixed-resize-content)
* [customize](#fixed-customize)

***

### [EPUB-CFI](#cfi-api)
_De-reference and generate Canonical Fragement Identifiers (CFIs)._

#### Methods
* [new EpubCFIModule()](#epub-cfi)
* [getContentDocHref(CFI, packageDocument)](#epub-cfi)
* [injectElement(CFI, contentDocument, elementToInject)](#epub-cfi)
* [getTargetElement(CFI, contentDocument)](#epub-cfi)
* [getTargetElementWithPartialCFI(contentDocumentCFI, contentDocument)](#epub-cfi)
* [getTextTerminusInfoWithPartialCFI(contentDocumentCFI, contentDocument)](#epub-cfi)
* [generateCharacterOffsetCFIComponent(startTextNode, charOffset)](#epub-cfi)
* [generateElementCFIComponent(startElement)](#epub-cfi)
* [generatePackageDocumentCFIComponent(contentDocumentName, packageDocument)](#epub-cfi)
* [generatePackageDocumentCFIComponentWithSpineIndex(spineIndex, packageDocument)](#epub-cfi)
* [generateCompleteCFI(packageDocumentCFIComponent, contentDocumentCFIComponent)](#epub-cfi)
* [injectElementAtOffset($textNodeList, textOffset, elementToInject)](#epub-cfi)
* [injectRangeElements(rangeCFI, contentDocument, startElementToInject, endElementToInject)](#epub-cfi)
* [getRangeTargetElements(rangeCFI, contentDocument)](#epub-cfi)
* [generateCharOffsetRangeComponent(rangeStartElement, startOffset, rangeEndElement, endOffset)](#epub-cfi)
* [generateElementRangeComponent(rangeStartElement, rangeEndElement)](#epub-cfi)

***

<!-- ==========================================================================================================
        SIMPLEREADIUM API DESCRIPTION
     ========================================================================================================== -->

<a id="simple-api"></a>
## SimpleReadium.js

<a id="simple-events-example"></a>
### Events

Handlers for each of the events triggered by SimpleReadium can set, as follows:

{% codeblock .on() lang:javascript %}
    simpleReadium.on("eventName", function () {
        console.log("Something is done when: eventName is triggered");
    }, this);
{% endcodeblock %}

Refer to the [on](#reader-on) API documentation for the method definition. 

<a id="simple-epub-loaded"></a>
#### epubLoaded
A _specified_ set of EPUB resources have completed rendering.

The specified set of resources depends on the rendering strategy. For example, if a lazy rendering strategy is used the epubLoaded event will be triggered when a single content document has completed rendering. 

<a id="simple-at-next-page"></a>
#### atNextPage
The reader has rendered the next page in the reading order. 

<a id="simple-at-previous-page"></a>
#### atPreviousPage
The reader has rendered the previous page in the reading order.

<a id="simple-at-first-page"></a>
#### atFirstPage
The reader has reached the first page in the EPUB publication.

<a id="simple-at-last-page"></a>
#### atLastPage
The reader has reached the last page in the EPUB publication.

<a id="simple-epub-link-clicked"></a>
#### epubLinkClicked
A link _within_ a content document has been clicked.

<a id="simple-layout-changed"></a>
#### layoutChanged
The layout has been changed from single-page to a two-page spread, or vice-versa.

<a id="simple-displayed-content-changed"></a>
#### displayedContentChanged
The displayed content has changed, for any reason. This event will be triggered on page changes, 
repagination, resizing, etc. 

<a id="simple-custom-styles-example"></a>
### Customizable styles

Custom styles can be set as follows:

{% codeblock .customize() lang:javascript %}
    // Setting a default custom style provided with the library
    simpleReadium.customize("customStyleName", "box-shadow");

    // Setting a default custom style with CSS
    simpleReadium.customize("customStyleName", {
        "border-style" : "solid",
        "border-color" : "red"
    });

    // Styles can also be chained
    simpleReadium
        .customize("spine-divider", "box-shadow")
        .customize("fixed-page-border-left", "box-shadow")
        .customize("fixed-page-border-right", "box-shadow");
{% endcodeblock %}

Refer to the API documentation of [customize](#simple-customize) for the method definition.

<a id="simple-epub-border"></a>
#### epub-border
A border that bounds the visible pages, for both fixed and reflowable content documents.

_Defaults_:
"box-shadow", "none"

<a id="simple-spine-divider"></a>
#### spine-divider
The spine divider shown in a two-page spread, for both fixed and reflowable content documents.

_Defaults_:
"box-shadow", "none"

<a id="simple-page-border"></a>
#### page-border
The border of each visible page, for both fixed and reflowable content documents. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="simple-margin"></a>
#### margin
The margin from the edge of the embedded reading container to the beginning of text. For reflowable content documents only, at the moment.

This custom style takes the place of the setMargin() method, so at present it only accepts integers in string format: "1", "2"..etc.

_Defaults_:
"1", ..., "5"

<a id="simple-font-size"></a>
#### fontSize
Sets the font size for reflowable content documents only. 

This custom style takes the place of the setFontSize() method, so at present it only accepts integers in string format: "1", "2"..etc.

_Defaults_:
"1", ..., "20"

<a id="simple-reflowable-epub-border"></a>
#### reflowable-epub-border
A border that bounds visible pages in a reflowable content document.

_Defaults_:
"box-shadow", "none"

<a id="simple-reflowable-spine-divider"></a>
#### reflowable-spine-divider
A spine divider shown in a two-page spread in a reflowable content document.

_Defaults_:
"box-shadow", "none"

<a id="simple-reflowable-page-border"></a>
#### reflowable-page-border
The border of each visible page, for reflowable content documents. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="simple-reflowable-page-theme"></a>
#### reflowable-page-theme
This custom style replaces the setTheme() method, and is used to provide a "theme" for reflowable content documents. Essentially, this can be any styling of the content document itself.

_Defaults_:
"night", "vancouver", "none"

<a id="simple-epub-border"></a>
#### fixed-epub-border 
A border that bounds visible pages for fixed content.

_Defaults_:
"box-shadow", "none"

<a id="simple-spine-divider"></a>
#### fixed-spine-divider
A spine divider shown in a two-page spread for fixed content.

_Defaults_:
"box-shadow", "none"

<a id="simple-page-border"></a>
#### fixed-page-border
The border of each visible page, for fixed content documents. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="simple-page-border-left"></a>
#### fixed-page-border-left
The border of each visible page that has a page-spread property value of "left," for fixed content. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="simple-page-border-right"></a>
#### fixed-page-border-right
The border of each visible page that has a page-spread property value of "right," for fixed content. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

### Methods

<a id="simple-init"></a>
#### SimpleRWC
Instantiate a new SimpleReadium object. Use a constructor method invocation. 

SimpleReadium requires a DOM element to bind EPUB content to, a url to the EPUB publication [package document](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-package-def), a viewer settings object, the package document XML, and a render strategy. 

This is a stateful module. State is the set of arguments, above. 

The element to bind must be given a fixed height, for the moment.

{% codeblock new EpubReaderModule(readerBoundElement, epubSpineInfo, viewerSettings, packageDocumentDOM) lang:javascript %}

    var elementToBindTo = $("#element-id")[0]; // A DOM element; jquery is not required
    var viewerSettings = {
            fontSize : 12, // integer
            syntheticLayout : false, // boolean
            currentMargin : 3, // integer
            tocVisible : false, // boolean
            currentTheme : "default" // "default", "vancouver-theme", "desert-theme"
        };
    var packageDocumentURL = "path/to/package/package.opf";
    var packageDocumentXML = "<package>...</package>";
    var renderStrategy = "lazy"; // "lazy" or "eager"

    simpleReadium = new SimpleRWC(
        elementToBindTo, viewerSettings, packageDocumentURL, packageDocumentXML, renderStrategy
    );

{% endcodeblock %} 

<a id="simple-show-spine-item"></a>
#### showSpineItem
Show EPUB content using its index in the spine.

A callback must be supplied, as the content referenced by the spine index may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock showSpineItem(spineIndex) lang:javascript %}

    var spineIndexToShow = 0; // integer; zero-indexed
    var callback = function () {
        console.log("Spine index shown: " + spineIndexToShow);
    };
    var callbackContext = this;
    simpleReadium.showSpineItem(spineIndexToShow, callback, callbackContext);

{% endcodeblock %}

<a id="simple-show-page-by-cfi"></a>
#### showPageByCFI
Show the page on which content indexed by a [CFI](http://www.idpf.org/epub/linking/cfi/#sec-epubcfi-def) can be found. 

A callback must be supplied, as the content referenced by the CFI may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock showPageByCFI(CFI) lang:javascript %}
    
    var CFI = "epubcfi(/2/6!/4/2/10)";
    var callback = function () {
        console.log("Spine index shown: " + spineIndexToShow);
    };
    var callbackContext = this;
    simpleReadium.showPageByCFI(CFI, callback, callbackContext);

{% endcodeblock %}

<a id="simple-show-page-by-element-id"></a>
#### showPageByElementId
Show the page that contains the element with the specified ID. 

The spine index must also be supplied, as each [spine itemref](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-itemref-elem) is likely an XHTML document, and the uniqueness of id's in the entire EPUB publication is not assured. 

A callback must be supplied, as the content referenced by the spine index may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock showPageByElementId(spineIndex, hashFragmentId) lang:javascript %}

    var spineIndexThatContainsTheId = 0; // integer; zero-indexed
    var elementId = "XML-id";
    var callback = function () {
        console.log("Spine index shown: " + spineIndexToShow);
    };
    var callbackContext = this;
    simpleReadium.showPageByElementId(spineIndexThatContainsTheId, elementId, callback, callbackContext);

{% endcodeblock %}

<a id="simple-next-page"></a>
#### nextPage
Show the next page(s) in the EPUB publication. 

A callback must be supplied, as the next set of content may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock .nextPage() lang:javascript %}

    var callback = function () {
        console.log("navigated to next page");
    };
    var callbackContext = this;
    simpleReadium.nextPage(callback, callbackContext);

{% endcodeblock %}

<a id="simple-previous-page"></a>
#### previousPage
Show the previous page(s) in the EPUB publication.

A callback must be supplied, as the previous set of content may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock .previousPage() lang:javascript %}

    var callback = function () {
        console.log("navigated to previous page");
    };
    var callbackContext = this;
    simpleReadium.previousPage(callback, callbackContext);

{% endcodeblock %}

<a id="simple-set-synthetic-layout"></a>
#### setSyntheticLayout
Set SimpleReadium to display a synthetic layout (two pages), or a single-page layout. 

{% codeblock .setSyntheticLayout(isSynthetic) lang:javascript %}

    // Show a two page layout
    simpleReadium.setSyntheticLayout(true);

    // Show a single page layout 
    simpleReadium.setSyntheticLayout(false);

{% endcodeblock %}

<a id="simple-resize-content"></a>
#### resizeContent
Resize EPUB content based on the current size of the HTML element container.

{% codeblock .resizeContent() lang:javascript %}

    // Resizes content based on the container's size
    simpleReadium.resizeContent();

{% endcodeblock %}

<a id="simple-customize"></a>
#### customize

Set custom styles provided by Readium.js

{% codeblock .customize(customStyleName, defaultOrCSSObject) lang:javascript %}
    // Setting a default custom style provided with the library
    var styleName = "epub-border"; // string: one of the custom styles provided by Readium.js
    var defaultOrCSSObject = "box-shadow"; //string: one of the defaults provided by Readium.js for the custom style
    simpleReadium.customize(styleName, defaultOrCSSObject);

    // Setting a default custom style with CSS
    var defaultOrCSSObject = {      // object: a string CSS property name, followed by a string CSS property value
        "border-style" : "solid",
        "border-color" : "red"
    }
    simpleReadium.customize(styleName, defaultOrCSSObject);

    // Styles can also be chained
    simpleReadium
        .customize("spine-divider", "box-shadow")
        .customize("fixed-page-border-left", "box-shadow")
        .customize("fixed-page-border-right", "box-shadow");
{% endcodeblock %}

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
Get the spine info object. The spine info object contains three arrays: An _array of each [itemref](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-itemref-elem)_ in the [spine](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-spine-elem), an _array of [bindings](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-bindings-elem)_.

{% codeblock .getSpineInfo() lang:javascript %}

var spineInfo = theEpub.getSpineInfo();
// Returns the spineInfo object {
//      spine : [itemrefs],
//      bindings : [bindings]
// }

{% endcodeblock %}

<a id="epub-isFixedLayout"></a>
#### isFixedLayout
Indicates if the _entire_ EPUB is [fixed layout](http://www.idpf.org/epub/fxl/#overview). 

This will only return true if the [fixed layout meta properties](http://www.idpf.org/epub/fxl/#property-defs) are set. If the EPUB
is mixed (contains both reflowable and fixed layout [content documents](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#sec-overview)), or entirely reflowable, this will return false. 

{% codeblock %}

var isFXL = theEpub.isFixedLayout();
// Returns true or false

{% endcodeblock %}

<a id="epub-getManifestItemById"></a>
#### getManifestItemById
Get a [manifest item](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-item-elem) object using it's XML id. 

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
Get a [manifest item](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-item-elem) object by using the [spine itemref idref](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-itemref-elem) that refers to it.

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
Get an [itemref](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-itemref-elem) object by using the itemref's idref. 

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
Get an [itemref](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-itemref-elem) object by using the itemref's index in the package document [spine](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-spine-elem). 

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
Get the spine index of the [itemref](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-itemref-elem) using it's associated manifest [item](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-item-elem) href.

{% codeblock .getSpineIndexByHref(manifestItemHref) %}
    
    var manifestItemHref = "item-href"; // A string
    var spineIndexOfItemref = theEpub.getSpineIndexByHref(manifestItemHref); 
    // Returns an integer; zero-indexed

{% endcodeblock %}

<a id="epub-spineLength"></a>
#### spineLength
Get the number of [itemrefs](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-itemref-elem) in the [spine](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-spine-elem).

_EXPECTED API CHANGE_: This method will be renamed to something like _getNumberOfItemrefs_.

{% codeblock %}

var numSpineItemrefs = theEpub.spineLength();
// Returns an integer; one-indexed

{% endcodeblock %}

<a id="epub-getNextLinearSpinePosition"></a>
#### getNextLinearSpinePosition
Get the index in the spine of the next [primary](http://www.idpf.org/epub/30/spec/epub30-publications.html#attrdef-itemref-linear) spine itemref.

_EXPECTED API CHANGE_: This method will be renamed to something like _getNextPrimarySpineIndex_. This method may also be changed to actually return the itemref object. 

{% codeblock .getNextLinearSpinePosition(startSpineIndex) lang:javascript %}

var startSpineIndex = 0; // integer; zero-indexed
var nextPrimarySpineIndex = theEpub.getNextLinearSpinePosition(startSpineIndex);
// Returns an integer; zero-indexed

{% endcodeblock %}

<a id="epub-getPrevLinearSpinePosition"></a>
#### getPrevLinearSpinePosition
Get the index in the spine of the previous [primary](http://www.idpf.org/epub/30/spec/epub30-publications.html#attrdef-itemref-linear) spine itemref.

_EXPECTED API CHANGE_: This method will be renamed to something like _getPreviousPrimarySpineIndex_. This method may also be changed to actually return the itemref object. 

{% codeblock .getPrevLinearSpinePosition(startSpineIndex) lang:javascript %}

var startSpineIndex = 0; // integer; zero-indexed
var nextPrimarySpineIndex = theEpub.getPrevLinearSpinePosition(startSpineIndex);
// Returns an integer; zero-indexed

{% endcodeblock %}

<a id="epub-hasNextSection"></a>
#### hasNextSection
Indicates if the EPUB has another [primary](http://www.idpf.org/epub/30/spec/epub30-publications.html#attrdef-itemref-linear) itemref.

_EXPECTED API CHANGE_: This method will likely be renamed to _hasNextItemref_.

{% codeblock .hasNextSection() lang:javascript %}

var startSpineIndex = 0; // integer; zero-indexed
var hasNextItemref = theEpub.hasNextSection(startSpineIndex);
// Returns true or false

{% endcodeblock %} 

<a id="epub-hasPrevSection"></a>
#### hasPrevSection
Indicates if the EPUB has a previous [primary](http://www.idpf.org/epub/30/spec/epub30-publications.html#attrdef-itemref-linear) itemref.

_EXPECTED API CHANGE_: This method will likely be renamed to _hasPreviousItemref_.

{% codeblock .hasPrevSection() lang:javascript %}

var startSpineIndex = 0; // integer; zero-indexed
var hasNextItemref = theEpub.hasPrevSection(startSpineIndex);
// Returns true or false

{% endcodeblock %} 

<a id="epub-pageProgressionDirection"></a>
#### pageProgressionDirection
Gets the [page progression direction](http://www.idpf.org/epub/30/spec/epub30-publications.html#attrdef-spine-page-progression-direction) of the EPUB.

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
Gets the URL of the [table of contents](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#sec-xhtml-nav) manifest [item](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-item-elem).

_EXPECTED API CHANGE_: This method will be renamed to something like _getTocHref_.

{% codeblock .getToc() lang:javascript %}

var tocHref = theEpub.getToc();
// Returns a string; the href for the table of contents manifest item

{% endcodeblock %}

<!-- ==========================================================================================================
        READER API DESCRIPTION
     ========================================================================================================== -->

<a id="reader-api"></a>
## EPUB Reader API

<a id="reader-events-example"></a>
### Events

Handlers for each of the events triggered by the reader can set, as follows:

{% codeblock .on() lang:javascript %}
    theEpub.on("eventName", function () {
        console.log("Something is done when: eventName is triggered");
    }, this);
{% endcodeblock %}

Refer to the [on](#reader-on) API documentation for the method definition. 

<a id="reader-epub-loaded"></a>
#### epubLoaded
A _specified_ set of EPUB resources have completed rendering.

The specified set of resources depends on the rendering strategy. For example, if a lazy rendering strategy is used the epubLoaded event will be triggered when a single content document has completed rendering. 

<a id="reader-at-next-page"></a>
#### atNextPage
The reader has rendered the next page in the reading order. 

<a id="reader-at-previous-page"></a>
#### atPreviousPage
The reader has rendered the previous page in the reading order.

<a id="reader-at-first-page"></a>
#### atFirstPage
The reader has reached the first page in the EPUB publication.

<a id="reader-at-last-page"></a>
#### atLastPage
The reader has reached the last page in the EPUB publication.

<a id="reader-epub-link-clicked"></a>
#### epubLinkClicked
A link _within_ a content document has been clicked.

<a id="reader-layout-changed"></a>
#### layoutChanged
The layout has been changed from single-page to a two-page spread, or vice-versa.

<a id="reader-displayed-content-changed"></a>
#### displayedContentChanged
The displayed content has changed, for any reason. This event will be triggered on page changes, 
repagination, resizing, etc. 

<a id="reader-custom-styles-example"></a>
### Customizable styles

Custom styles can be set as follows:

{% codeblock .customize() lang:javascript %}
    // Setting a default custom style provided with the library
    theEpub.customize("customStyleName", "box-shadow");

    // Setting a default custom style with CSS
    theEpub.customize("customStyleName", {
        "border-style" : "solid",
        "border-color" : "red"
    });

    // Styles can also be chained
    theEpub
        .customize("spine-divider", "box-shadow")
        .customize("fixed-page-border-left", "box-shadow")
        .customize("fixed-page-border-right", "box-shadow");
{% endcodeblock %}

Refer to the API documentation of [customize](#reader-customize) for the method definition.

<a id="reader-epub-border"></a>
#### epub-border
A border that bounds the visible pages, for both fixed and reflowable content documents.

_Defaults_:
"box-shadow", "none"

<a id="reader-spine-divider"></a>
#### spine-divider
The spine divider shown in a two-page spread, for both fixed and reflowable content documents.

_Defaults_:
"box-shadow", "none"

<a id="reader-page-border"></a>
#### page-border
The border of each visible page, for both fixed and reflowable content documents. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="reader-margin"></a>
#### margin
The margin from the edge of the embedded reading container to the beginning of text. For reflowable content documents only, at the moment.

This custom style takes the place of the setMargin() method, so at present it only accepts integers in string format: "1", "2"..etc.

_Defaults_:
"1", ..., "5"

<a id="reader-font-size"></a>
#### fontSize
Sets the font size for reflowable content documents only. 

This custom style takes the place of the setFontSize() method, so at present it only accepts integers in string format: "1", "2"..etc.

_Defaults_:
"1", ..., "20"

<a id="reader-reflowable-epub-border"></a>
#### reflowable-epub-border
A border that bounds visible pages in a reflowable content document.

_Defaults_:
"box-shadow", "none"

<a id="reader-reflowable-spine-divider"></a>
#### reflowable-spine-divider
A spine divider shown in a two-page spread in a reflowable content document.

_Defaults_:
"box-shadow", "none"

<a id="reader-reflowable-page-border"></a>
#### reflowable-page-border
The border of each visible page, for reflowable content documents. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="reader-reflowable-page-theme"></a>
#### reflowable-page-theme
This custom style replaces the setTheme() method, and is used to provide a "theme" for reflowable content documents. Essentially, this can be any styling of the content document itself.

_Defaults_:
"night", "vancouver", "none"

<a id="reader-epub-border"></a>
#### fixed-epub-border 
A border that bounds visible pages for fixed content.

_Defaults_:
"box-shadow", "none"

<a id="reader-spine-divider"></a>
#### fixed-spine-divider
A spine divider shown in a two-page spread for fixed content.

_Defaults_:
"box-shadow", "none"

<a id="reader-page-border"></a>
#### fixed-page-border
The border of each visible page, for fixed content documents. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="reader-page-border-left"></a>
#### fixed-page-border-left
The border of each visible page that has a page-spread property value of "left," for fixed content. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="reader-page-border-right"></a>
#### fixed-page-border-right
The border of each visible page that has a page-spread property value of "right," for fixed content. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

### Methods

<a id="reader-init"></a>
#### EpubReaderModule
Instantiate a new reader module. Use a constructor method invocation. 

The reader requires a DOM element to bind EPUB content to, the EPUB publication [spine info]() object, a viewer settings object, and a [DOM representation](#getPackageDocumentDOM) of the package document.

This is a stateful module. State is the _DOM element to bind to_, the epub resources referenced by the _epub spine info_ object, and _viewer settings_. 

The binding element must have a fixed sized set, at present. 

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
Load and render EPUB publication resources. When render() is called, RWC will inject DOM elements as children of the [binding element](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-bindings-elem) passed on initialization. 

By default, all EPUB resources will be hidden. A show method must be called to display a part of the EPUB publication.

The EPUB-Reader module will trigger an "epubLoaded" event when all the resources of the EPUB are loaded. Use the [on](#reader-on) method to handle the event. 

_EXPECTED API CHANGE_: Loading and rendering settings, eager vs lazy loading

{% codeblock .render() lang:javascript %}

    epubReader.on("epubLoaded", function () {
        epubReader.showSpineItem(0, function () { console.log("showed first page"); }, this);
    }, this);

    epubReader.render();

{% endcodeblock %}

<a id="reader-show-spine-item"></a>
#### showSpineItem
Show EPUB content using it's index in the spine.

A callback must be supplied, as the content referenced by the spine index may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock showSpineItem(spineIndex) lang:javascript %}

    var spineIndexToShow = 0; // integer; zero-indexed
    var callback = function () {
        console.log("Showed spine index: " + spineIndexToShow);
    };
    var callbackContext = this;
    epubReader.showSpineItem(spineIndexToShow, callback, callbackContext);

{% endcodeblock %}

<a id="reader-show-page-by-cfi"></a>
#### showPageByCFI
Show the page on which content indexed by a [CFI](http://www.idpf.org/epub/linking/cfi/#sec-epubcfi-def) can be found. 

A callback must be supplied, as the content referenced by the CFI may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock showPageByCFI(CFI) lang:javascript %}
    
    var CFI = "epubcfi(/2/6!/4/2/10)";
    var callback = function () {
        console.log("Showed page by CFI");
    };
    var callbackContext = this;
    epubReader.showPageByCFI(CFI, callback, callbackContext);

{% endcodeblock %}

<a id="reader-show-page-by-element-id"></a>
#### showPageByElementId
Show the page that contains the element with the specified ID. 

The spine index must also be supplied, as each spine itemref is likely an XHTML document, and the uniqueness of id's in the EPUB publication is not assured. 

A callback must be supplied, as the content referenced by the spine index may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock showPageByElementId(spineIndex, hashFragmentId) lang:javascript %}

    var spineIndexThatContainsTheId = 0; // integer; zero-indexed
    var elementId = "XML-id";
    var callback = function () {
        console.log("Showed element ID");
    };
    var callbackContext = this;
    epubReader.showPageByElementId(spineIndexThatContainsTheId, elementId, callback, callbackContext);

{% endcodeblock %}

<a id="reader-next-page"></a>
#### nextPage
Show the next page(s) in the EPUB publication. 

A callback must be supplied, as the next set of content may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock .nextPage() lang:javascript %}

    var callback = function () {
        console.log("navigated to next page");
    };
    var callbackContext = this;
    epubReader.nextPage(callback, callbackContext);

{% endcodeblock %}

<a id="reader-previous-page"></a>
#### previousPage
Show the previous page(s) in the EPUB publication.

A callback must be supplied, as the previous set of content may not have been loaded by the browser - this depends on the [render strategy]().

{% codeblock .previousPage() lang:javascript %}

    var callback = function () {
        console.log("navigated to previous page");
    };
    var callbackContext = this;
    epubReader.previousPage(callback, callbackContext);

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

This method is delegating to the [backbone.js on(...)](http://backbonejs.org/#Events-on) method, so the interface and semantics will conform closely. 

{% codeblock on(eventName, callback, callbackContext) lang:javascript %} 

    // Bind a callback to the "epubLoaded" event
    epubReader.on("epubLoaded", function () {
        console.log("the EPUB publication resources are now loaded and rendered");
    }, this);

{% endcodeblock %}

<a id="reader-off"></a>
#### off
Remove all callbacks bound to the module object for the given event name. 

This method is delegating to the [backbone.js off(...)](http://backbonejs.org/#Events-off) method, so the interface and semantics will conform closely.

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

<a id="reader-resize-content"></a>
#### resizeContent
Resize EPUB content based on the current size of the HTML element container.

{% codeblock .resizeContent() lang:javascript %}

    // Resizes content based on the container's size
    epubReader.resizeContent();

{% endcodeblock %}

<a id="reader-customize"></a>
#### customize

Set custom styles provided by Readium.js

{% codeblock .customize(customStyleName, defaultOrCSSObject) lang:javascript %}
    // Setting a default custom style provided with the library
    var styleName = "epub-border"; // string: one of the custom styles provided by Readium.js
    var defaultOrCSSObject = "box-shadow"; //string: one of the defaults provided by Readium.js for the custom style
    epubReader.customize(styleName, defaultOrCSSObject);

    // Setting a default custom style with CSS
    var defaultOrCSSObject = {      // object: a string CSS property name, followed by a string CSS property value
        "border-style" : "solid",
        "border-color" : "red"
    }
    epubReader.customize(styleName, defaultOrCSSObject);

    // Styles can also be chained
    epubReader
        .customize("spine-divider", "box-shadow")
        .customize("fixed-page-border-left", "box-shadow")
        .customize("fixed-page-border-right", "box-shadow");
{% endcodeblock %}

<!-- ==========================================================================================================
        REFLOWABLE PAGE SET API DESCRIPTION
     ========================================================================================================== -->

<a id="reflowable-api"></a>
## Reflowable Page Set

<a id="reflowable-events-example"></a>
### Events

Handlers for each of the events triggered by a reflowable page set can set, as follows:

{% codeblock .on() lang:javascript %}
    reflowablePages.on("eventName", function () {
        console.log("Something is done when: eventName is triggered");
    }, this);
{% endcodeblock %}

Refer to the [on](#reader-on) API documentation for the method definition. 

<a id="reflowable-epub-loaded"></a>
#### epubLoaded
A _specified_ set of EPUB resources have completed rendering.

The specified set of resources depends on the rendering strategy. For example, if a lazy rendering strategy is used the epubLoaded event will be triggered when a single content document has completed rendering. 

<a id="reflowable-at-next-page"></a>
#### atNextPage
The reader has rendered the next page in the reading order. 

<a id="reflowable-at-previous-page"></a>
#### atPreviousPage
The reader has rendered the previous page in the reading order.

<a id="reflowable-at-first-page"></a>
#### atFirstPage
The reader has reached the first page in the EPUB publication.

<a id="reflowable-at-last-page"></a>
#### atLastPage
The reader has reached the last page in the EPUB publication.

<a id="reflowable-epub-link-clicked"></a>
#### epubLinkClicked
A link _within_ a content document has been clicked.

<a id="reflowable-layout-changed"></a>
#### layoutChanged
The layout has been changed from single-page to a two-page spread, or vice-versa.

<a id="reflowable-displayed-content-changed"></a>
#### displayedContentChanged
The displayed content has changed, for any reason. This event will be triggered on page changes, 
repagination, resizing, etc. 

<a id="reflowable-custom-styles-example"></a>
### Customizable styles

Custom styles can be set as follows:

{% codeblock .customize() lang:javascript %}
    // Setting a default custom style provided with the library
    reflowablePages.customize("customStyleName", "box-shadow");

    // Setting a default custom style with CSS
    reflowablePages.customize("customStyleName", {
        "border-style" : "solid",
        "border-color" : "red"
    });

    // Styles can also be chained
    reflowablePages
        .customize("spine-divider", "box-shadow")
        .customize("fixed-page-border-left", "box-shadow")
        .customize("fixed-page-border-right", "box-shadow");
{% endcodeblock %}

Refer to the API documentation of [customize](#reflowable-customize) for the method definition.

<a id="reflowable-epub-border"></a>
#### epub-border
A border that bounds the visible pages.

_Defaults_:
"box-shadow", "none"

<a id="reflowable-spine-divider"></a>
#### spine-divider
The spine divider shown in a two-page spread.

_Defaults_:
"box-shadow", "none"

<a id="reflowable-page-border"></a>
#### page-border
The border of each visible page. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="reflowable-margin"></a>
#### margin
The margin from the edge of the embedded reading container to the beginning of text.

This custom style takes the place of the setMargin() method, so at present it only accepts integers in string format: "1", "2"..etc.

_Defaults_:
"1", ..., "5"

<a id="reflowable-font-size"></a>
#### fontSize
Sets the font size. 

This custom style takes the place of the setFontSize() method, so at present it only accepts integers in string format: "1", "2"..etc.

_Defaults_:
"1", ..., "20"

<a id="reflowable-reflowable-epub-border"></a>
#### reflowable-epub-border
A border that bounds visible pages in a reflowable content document.

_Defaults_:
"box-shadow", "none"

<a id="reflowable-reflowable-spine-divider"></a>
#### reflowable-spine-divider
A spine divider shown in a two-page spread in a reflowable content document.

_Defaults_:
"box-shadow", "none"

<a id="reflowable-reflowable-page-border"></a>
#### reflowable-page-border
The border of each visible page, for reflowable content documents. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="reflowable-reflowable-page-theme"></a>
#### reflowable-page-theme
This custom style replaces the setTheme() method, and is used to provide a "theme" for reflowable content documents. Essentially, this can be any styling of the content document itself.

_Defaults_:
"night", "vancouver", "none"

### Methods

<a id="reflowable-init"></a>
#### EpubReflowableModule
Initialize the set of reflowable pages.

This is a stateful module. State is the _[content document](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#sec-overview)_, _viewer settings_, and _[bindings](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-bindings-elem)_ for the content document. 

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
Paginate the [content document](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#sec-overview).

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
Show the page on which content indexed by a [CFI](http://www.idpf.org/epub/linking/cfi/#sec-epubcfi-def) can be found. 

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

This method is delegating to the [backbone.js on(...)](http://backbonejs.org/#Events-on) method, so the interface and semantics will conform closely. 

{% codeblock on(eventName, callback, callbackContext) lang:javascript %} 

    // Bind a callback to the "epubLoaded" event
    reflowablePages.on("epubLoaded", function () {
        console.log("the EPUB publication resources are now loaded and rendered");
    }, this);

{% endcodeblock %}

<a id="reflowable-off"></a>
#### off
Remove all callbacks bound to the module object for the given event name. 

This method is delegating to the [backbone.js off(...)](http://backbonejs.org/#Events-off) method, so the interface and semantics will conform closely.

{% codeblock .off(eventName) lang:javascript %}

    reflowablePages.off("epubLoaded");

{% endcodeblock %}

<a id="reflowable-resize-content"></a>
#### resizeContent
Resize EPUB content based on the current size of the HTML element container.

{% codeblock .resizeContent() lang:javascript %}

    // Resizes content based on the container's size
    reflowablePages.resizeContent();

{% endcodeblock %}

<a id="reflowable-customize"></a>
#### customize

Set custom styles provided by Readium.js

{% codeblock .customize(customStyleName, defaultOrCSSObject) lang:javascript %}
    // Setting a default custom style provided with the library
    var styleName = "epub-border"; // string: one of the custom styles provided by Readium.js
    var defaultOrCSSObject = "box-shadow"; //string: one of the defaults provided by Readium.js for the custom style
    reflowablePages.customize(styleName, defaultOrCSSObject);

    // Setting a default custom style with CSS
    var defaultOrCSSObject = {      // object: a string CSS property name, followed by a string CSS property value
        "border-style" : "solid",
        "border-color" : "red"
    }
    reflowablePages.customize(styleName, defaultOrCSSObject);

    // Styles can also be chained
    reflowablePages
        .customize("spine-divider", "box-shadow")
        .customize("fixed-page-border-left", "box-shadow")
        .customize("fixed-page-border-right", "box-shadow");
{% endcodeblock %}

<!-- ==========================================================================================================
        FIXED PAGE SET API DESCRIPTION
     ========================================================================================================== -->

<a id="fixed-api"></a>
## Fixed Page Set

<a id="fixed-events-example"></a>
### Events

Handlers for each of the events triggered by a fixed page set can set, as follows:

{% codeblock .on() lang:javascript %}
    fixedPages.on("eventName", function () {
        console.log("Something is done when: eventName is triggered");
    }, this);
{% endcodeblock %}

Refer to the [on](#reader-on) API documentation for the method definition. 

<a id="fixed-epub-loaded"></a>
#### epubLoaded
A _specified_ set of EPUB resources have completed rendering.

The specified set of resources depends on the rendering strategy. For example, if a lazy rendering strategy is used the epubLoaded event will be triggered when a single content document has completed rendering. 

<a id="fixed-at-next-page"></a>
#### atNextPage
The reader has rendered the next page in the reading order. 

<a id="fixed-at-previous-page"></a>
#### atPreviousPage
The reader has rendered the previous page in the reading order.

<a id="fixed-at-first-page"></a>
#### atFirstPage
The reader has reached the first page in the EPUB publication.

<a id="fixed-at-last-page"></a>
#### atLastPage
The reader has reached the last page in the EPUB publication.

<a id="fixed-epub-link-clicked"></a>
#### epubLinkClicked
A link _within_ a content document has been clicked.

<a id="fixed-layout-changed"></a>
#### layoutChanged
The layout has been changed from single-page to a two-page spread, or vice-versa.

<a id="fixed-displayed-content-changed"></a>
#### displayedContentChanged
The displayed content has changed, for any reason. This event will be triggered on page changes, 
repagination, resizing, etc. 

<a id="fixed-custom-styles-example"></a>
### Customizable styles

Custom styles can be set as follows:

{% codeblock .customize() lang:javascript %}
    // Setting a default custom style provided with the library
    fixedPages.customize("customStyleName", "box-shadow");

    // Setting a default custom style with CSS
    fixedPages.customize("customStyleName", {
        "border-style" : "solid",
        "border-color" : "red"
    });

    // Styles can also be chained
    fixedPages
        .customize("spine-divider", "box-shadow")
        .customize("fixed-page-border-left", "box-shadow")
        .customize("fixed-page-border-right", "box-shadow");
{% endcodeblock %}

Refer to the API documentation of [customize](#fixed-customize) for the method definition.

<a id="fixed-epub-border"></a>
#### epub-border
A border that bounds the visible pages.

_Defaults_:
"box-shadow", "none"

<a id="fixed-spine-divider"></a>
#### spine-divider
The spine divider shown in a two-page spread.

_Defaults_:
"box-shadow", "none"

<a id="fixed-page-border"></a>
#### page-border
The border of each visible page. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="fixed-epub-border"></a>
#### fixed-epub-border 
A border that bounds visible pages for fixed content.

_Defaults_:
"box-shadow", "none"

<a id="fixed-spine-divider"></a>
#### fixed-spine-divider
A spine divider shown in a two-page spread for fixed content.

_Defaults_:
"box-shadow", "none"

<a id="fixed-page-border"></a>
#### fixed-page-border
The border of each visible page, for fixed content documents. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="fixed-page-border-left"></a>
#### fixed-page-border-left
The border of each visible page that has a page-spread property value of "left," for fixed content. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

<a id="fixed-page-border-right"></a>
#### fixed-page-border-right
The border of each visible page that has a page-spread property value of "right," for fixed content. This should not be used in conjunction with the "epub-border."

_Defaults_:
"box-shadow", "none"

### Methods

<a id="fixed-init"></a>
#### EpubFixedModule

Initialize a set of fixed pages.

This is a stateful module. State is the _set of [fixed layout pages](http://www.idpf.org/epub/fxl/#overview)_ passed to the module, and the _viewer settings_;

The spineObject is an array of objects that contain information about a [spine itemref](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-itemref-elem). The number of spine objects passed to the module can be anything greater than 1, within system/language limits.

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

Render and size the [fixed layout pages](http://www.idpf.org/epub/fxl/#overview).

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
Show the page on which content indexed by a [CFI](http://www.idpf.org/epub/linking/cfi/#sec-epubcfi-def) can be found. 

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

This method is delegating to the [backbone.js on(...)](http://backbonejs.org/#Events-on) method, so the interface and semantics will conform closely. 

{% codeblock on(eventName, callback, callbackContext) lang:javascript %} 

    // Bind a callback to the "epubLoaded" event
    fixedPages.on("epubLoaded", function () {
        console.log("the EPUB publication resources are now loaded and rendered");
    }, this);

{% endcodeblock %}

<a id="fixed-off"></a>
#### off
Remove all callbacks bound to the module object for the given event name. 

This method is delegating to the [backbone.js off(...)](http://backbonejs.org/#Events-off) method, so the interface and semantics will conform closely.

{% codeblock .off(eventName) lang:javascript %}

    fixedPages.off("epubLoaded");

{% endcodeblock %}

<a id="fixed-resize-content"></a>
#### resizeContent
Resize EPUB content based on the current size of the HTML element container.

{% codeblock .resizeContent() lang:javascript %}

    // Resizes content based on the container's size
    fixedPages.resizeContent();

{% endcodeblock %}

<a id="fixed-customize"></a>
#### customize

Set custom styles provided by Readium.js

{% codeblock .customize(customStyleName, defaultOrCSSObject) lang:javascript %}
    // Setting a default custom style provided with the library
    var styleName = "epub-border"; // string: one of the custom styles provided by Readium.js
    var defaultOrCSSObject = "box-shadow"; //string: one of the defaults provided by Readium.js for the custom style
    fixedPages.customize(styleName, defaultOrCSSObject);

    // Setting a default custom style with CSS
    var defaultOrCSSObject = {      // object: a string CSS property name, followed by a string CSS property value
        "border-style" : "solid",
        "border-color" : "red"
    }
    fixedPages.customize(styleName, defaultOrCSSObject);

    // Styles can also be chained
    fixedPages
        .customize("spine-divider", "box-shadow")
        .customize("fixed-page-border-left", "box-shadow")
        .customize("fixed-page-border-right", "box-shadow");
{% endcodeblock %}

<!-- ==========================================================================================================
        EPUB CFI API DESCRIPTION
     ========================================================================================================== -->

<a id="cfi-api"></a>
## EPUB Canonical Fragment Identifiers

*Coming soon*

This module exists, but the API naming is very ... utilitarian. The methods need to be renamed, after which they'll be put on here.

