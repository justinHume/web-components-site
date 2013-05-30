---
layout: post
title: "Readium.js development"
date: 2013-05-28 13:48
comments: true
categories: 
author: <a href="http://github.com/justinHume">Justin Hume</a>
---

This post discusses Readium.js development priorities up to now, as well as how you can get involved with the project. 

## Motivation

Readium.js is designed as a set of modular javascript components <!--more-->that can be used [together](/Readium-Web-Components/get-started/download.html#simple-download) to embed EPUB publications in a web application, or [independently](/Readium-Web-Components/get-started/download.html#readium-js-download) to build custom web applications with EPUB support. 

#### Fix things that are painful
When a developer is looking for projects, it's not uncommon to hear the suggestion that they work on a pain point. At [Evident Point](http://evidentpoint.com), I've been involved in building a number of web-based EPUB 3 readers. The original [Readium](http://github.com/readium/readium) project often served as a template for these efforts. 

While the original Readium provided a good demonstration of an EPUB 3 reader, I (and others, I believe) found it quite painful as developers to adapt the source to projects that were new, custom, or had more stringent requirements for performance, features etc. 

By designing the Readium.js library it was my hope that Readium.js could, in typically-modern-web-javascript fashion, make it painless for developers to build a whole variety of web-based EPUB applications.

#### Keep improving
It's also my hope that from here we can build a community around Readium.js to get the [API](/Readium-Web-Components/get-started/api.html) right, build in additional features and improve digital publishing on the web. 

The original Readium project was successful due to the [involvement](https://github.com/readium/readium/issues) of a [community](https://github.com/readium/readium/contributors). Much of Readium.js is built on the contributions of this community - either code, wisdom, or lessons learned. I hope this can continue. 

## Development Priorities

During the development of Readium.js, I prioritized the things engineers like: The API design, a reasonable standard of engineering and solid documentation.

I felt it was important to get to a point where community members could reason about the design of the library and API, test the library, and get involved with the source code. I think getting the library 'right' will depend on early feeback and iteration.

#### Someone get the polish...
As a result of this priority, some EPUB 3 feature support was lost in the design and refactoring. Getting these features back is in some cases just a matter of "turning" them back on. In some cases, it'll be a bit more work. However, I think Readium.js will be back up to feature-completeness pretty quickly. 

## How you can help

I think Readium.js has some decent abstractions, encapsulation and documentation (in addition to some... rough naming), so the [code base](http://github.com/readium/Readium-Web-Components) should be fairly accessible for contributors. I'll also be able to help point you to where and how you can tackle certain things. Feedback and [issue reports](http://github.com/readium/Readium-Web-Components/issues) are also very welcome.

If you know of something you'd like to contribute, feel free to get in touch (justinh@evidentpoint.com). If you're looking for something (small or large) to contribute, you can choose from a list of things that need doing. 

I hope you get involved.

