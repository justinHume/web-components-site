---
layout: page
title: "Getting started with Readium.js"
date: 2013-06-12 14:00
comments: true
sharing: true
footer: true
author: <a href="http://github.com/justinHume">Justin Hume</a>
---

This page describes a small demo that leverages Readium.js to embed EPUB 3 content in a web application. This should help you get familiar with all that Readium.js has to offer. 

If you have any questions, problems, suggestions, you can email me at justinh@evidentpoint.com, find me on [Github](http://github.com/justinHume) or add to the Readium.js [issue tracker](https://github.com/readium/Readium-Web-Components/issues).

<a id="simple-rwc-demo"></a>
## SimpleReadium.js & Demo application

The easiest way to get familiar with Readium.js is to use [SimpleReadium.js](/Readium-Web-Components/get-started/download.html), a javascript module that wires together all the Readium.js modules in one object and exposes a reduced, simplified, [API](/Readium-Web-Components/get-started/api.html#simple-api). 

The following demo application and SimpleReadium.js should help you get started using and understanding Readium.js.

### Instructions for using the demo
There are three ways to try out the demo application:

#### _Zip file_
To use this demo, you need to have a web server. There are four steps to get set up: 

* Download the SimpleReadium.js [demo application](/Readium-Web-Components/downloads/SimpleReadiumJsDemoApp.zip) (~9 MB)
* Unzip the demo file in the folder you intend to serve the application files
* Start your server
* Point your browser to url/to/demo/index.html

#### _Github source_
The [source](http://github.com/readium/readium-viewer-demo1) for the demo is also available on Github, and instructions for using it are provided in the Readme.

#### _Web version_
A Github Pages -hosted version of this demo is available [here](http://readium.github.com/readium-viewer-demo1).

<a id="simple-rwc-description"></a>
## Description of the demo application

### Demo app structure
The demo application contains four important pieces: 

1. _index.html_ - The application HTML
2. _modules_and_dependencies_ - A folder that contains javascript [dependencies]() and SimpleReadium.js
3. _assets/css_ - Styling for the demo
4. _assets/images_ - Images for the demo

### Important parts of the code
Most of the demo application is application-specific code; that is, application layout and styling. There are four important parts of the application that leverage SimpleReadium.js:

#### _An HTML element in which to embed an EPUB publication_
The margin-top style is required to have this container render under the navbar. 

At the moment, this container must have a fixed height set. The height in the demo application is set as a function of the screen size, using the RWCDemoApp.setModuleContainerHeight() method call.
 
{% codeblock Element to contain EPUB publication lang:javascript %}
    <div id="epub-reader-container" style="margin-top:65px;">
    </div>
{% endcodeblock %}

#### _Initializing the SimpleReadium.js object_
The SimpleReadium.js object requires: a reference to the _HTML element to bind to_, an object of _viewer preferences_, a _URL to the EPUB publication package document_, the _package document XML_, and a _rendering strategy_: "eager" or "lazy." 

{% codeblock Initialize SimpleReadium.js object lang:javascript %}

    // Get the HTML element to bind the module reader to
    var elementToBindReaderTo = $("#reader");

    // Create an object of viewer preferences
    var viewerPreferences = {
        fontSize : 12,
        syntheticLayout : false,
        currentMargin : 3,
        tocVisible : false,
        currentTheme : "default"
    };

    ...

    // THE MOST IMPORTANT PART - INITIALIZING THE SIMPLE RWC MODEL
    // packageDocumentURL is defined elsewhere
    // "result" is the package document xml, in this case, the result of an AJAX method call
    RWCDemoApp.epubViewer = new SimpleRWC(
        elementToBindReaderTo, viewerPreferences, packageDocumentURL, result, "lazy"
    );

{% endcodeblock %}

#### _Wire the application to the SimpleReadium.js API_
Once the SimpleReadium.js object has been instantiated, the application developer can wire their application to the API provided by SimpleReadium.js. 

In the case of the demo application, buttons that control next page, previous page, and a library have been wired to object. 

{% codeblock Wire HTML to SimpleReadium.js object lang:javascript %}

    // These are application specific handlers that wire the HTML to the SimpleRWC module API

    // Set handlers for click events

    ...

    $("#prev-page").on("click", function () {
        RWCDemoApp.epubViewer.previousPage();
    });

    ...

    $("#next-page").on("click", function () {
        RWCDemoApp.epubViewer.nextPage();
    });

    ...

    $("#toggle-synthetic-btn").on("click", function () {

        if (currLayoutIsSynthetic) {
            RWCDemoApp.epubViewer.setSyntheticLayout(false);
            currLayoutIsSynthetic = false;
            $("#single-page-ico").show();
            $("#synthetic-page-ico").hide();
        }
        else {
            RWCDemoApp.epubViewer.setSyntheticLayout(true);
            currLayoutIsSynthetic = true;
            $("#single-page-ico").hide();
            $("#synthetic-page-ico").show();
        }
    });

{% endcodeblock %}

#### _Render the EPUB publication_
.render() must be called to start rendering EPUB publication resources. The SimpleReadium.js object will fire an "epubLoaded" event once the EPUB is sufficiently loaded to interact with; this depends on the rendering strategy.

{% codeblock Render and show EPUB publication lang:javascript %}

    // Render the reader
    RWCDemoApp.epubViewer.on("epubLoaded", function () { 
        RWCDemoApp.epubViewer.showSpineItem(0, function () {
            console.log("showed first spine item"); 
        });
    }, that);
    RWCDemoApp.epubViewer.render(0);

{% endcodeblock %}

<a id="next-steps"></a>
## Next steps
If you feel comfortable with SimpleReadium.js and the demo application, feel free to learn more about the [philosophy](/Readium-Web-Components/architecture/philosophy.html), [design](/Readium-Web-Components/architecture/design.html) or [codebase](http://github.com/readium/Readium-Web-Components). 

The [API](/Readium-Web-Components/get-started/api.html) documentation will also help you get familiar with all that Readium.js has to offer.

Finally, if you're ready to start building, you can download [Readium.js](/Readium-Web-Components/get-started/download.html).
