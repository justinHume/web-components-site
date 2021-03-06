---
layout: page
title: "A history lesson in... Readium"
date: 2013-06-11 14:00
comments: true
sharing: true
footer: true
author: Bill McCoy, Justin Hume
---

### Inception and goals

The [Readium](http://readium.org) project began [in early 2012](http://idpf.org/news/readium-open-source-initiative-launched-to-accelerate-adoption-of-epub-3) as a web-based demonstration of [EPUB 3](http://idpf.org/epub/30), approved as a standard by the [International Digital Publishing Forum (IDPF)](http://idpf.org) in October, 2011. The initial goal of the project was to produce a simple browser-based "reference system" reader application that fully implemented the new specification.

### Success! EPUB 3 Reference Implementation

[Evident Point Software Corp.](http://evidentpoint.com/) was contracted by the IDPF to seed development of the reader and run the open-source project, and many [organizations and individuals](https://github.com/readium/readium/contributors) contributed. 

The inital deployment was a Google Chrome Packaged App. The packaged-app is a 100% dedicated client-side (browser) solution, allowing users to load, read and save publications in the EPUB format. This application, deployed on the [Chrome Web Store](https://chrome.google.com/webstore/detail/empty-title/fepbnnnkkadjhjahcafoaglimekefifl?hl=en-US), now has over 60,000 users. It supports all major EPUB 3 features including fixed layout as well as dynamic pagination of reflow content, media overlays, interactivity, video, audio, global language support, embedded fonts, SVG, etc.

### The next steps...

Having satisfied the "demonstration" goals of the original project, it was apparent that support was needed for production-level EPUB 3 deployment both for native apps and browser-based "cloud" readers. This need was made more pressing by the lack of EPUB 3 support in the most commonly used embedded EPUB engine, Adobe Reader Mobile SDK (RMSDK), which does not support fixed-layout, interactivity, video, or most other EPUB 3 features.

#### Readium.js: Simple, light-weight, web-focused
Several organizations created custom variants of the original Readium Chrome Web Application that were completely web-served "cloud readers" rather than installed client-side browser extensions. This included an experimental implementation by [Evident Point](http://evidentpoint.com/) and a more production-focused implementation deployed by Benetech as the nucleus of a new browser-based reader for the [Benetech Bookshare](https://www.bookshare.org/) service. 

##### _Readium =%$&*@=> Readium.js!_
This work led to a desire to rewrite the Readium codebase into a set of light-weight components optimized for web-deployed EPUB files and purely browser-based reading. [Evident Point Software](http://evidentpoint.com/) took the first steps to rewrite the original Readium codebased into the new [Readium.js](/) project, and other organizations including Benetech and DAISY have pledged to contribute to Readium.js in areas of their expertise, such as accessibility support including screen-reader integration. 

##### _Readium.js going forward_
Readium.js consists of a set of [javascript modules](/Readium-Web-Components/get-started/download.html) that can be dropped into any new or existing web application, and can be composed to support a variety of different types of application. This includes the simple case of deploying EPUB files onto a basic static web server to be consumed in any modern (HTML5) browser. The Chrome Packaged App configuration will continue to be maintained, but the primary focus is now cross-browser implementations for reading server-based content.

#### Readium-SDK: High-performance, industrial-strength, EPUB 3 for native mobile and desktop apps

In parallel with the beginning of Readium.js, the [Readium-SDK](http://readium.org/projects/readium-sdk) project began in early 2013. This project is developing a performant, mobile-focused, industry-strength EPUB 3 SDK (software development kit). 

This project has a dual license approach to facilitate commercial adoption. Readium-SDK combines a browser engine (e.g. WebKit) with optimized native code libraries that help support various EPUB 3 features and requirements of native apps. This project will share JS-level modules with Readium.js where appropriate. Readium-SDK configurations and sample apps for iOS (iPhone/iPad), Android, Mac OS/X, and Windows are presently under active development.

#### Readium Foundation

[Readium Foundation](http://readium.org/readium-foundation-announced) was formed in February 2013 as a non-profit organization to oversee and facilitate development of Readium.js, Readium-SDK, and other open source projects that will advance EPUB and the overall Open Web Platform for the needs of digital pubilshing. Over two dozen organizations have already joined Readium Foundation. 

### The future

The expectation is that Readium-SDK and Readium.js will develop in tandem to support the evolving EPUB standard, enabling both high-performance native desktop and mobile applications, and browser-based web applications. Contributors are needed for both projects, and organizations building solutions around the EPUB standard are encouraged to consider [membership in the Readium Foundation](http://readium.org/membership).