+++
title="2021-12-22"
date=2021-12-22
+++

I've been interested in using Machine Learning to extract text reliably from
a web page for archival purposes (adding to my personal knowlegebase). So
today, I'm collecting some links to prior art in this area for some 
inspiration:

[A Machine Learning Approach to Webpage Content
Extraction](https://cs229.stanford.edu/proj2013/YaoZuo-AMachineLearningApproachToWebpageContentExtraction.pdf). This paper
uses support vector machines to train a model that uses some specific 
features in the text block:

* number of words in this block and thee quotient to its previous block
* average sentence length in this block and the quotient to its previous block
* text density in this block and the quotient to its previous block
* link density in this block

[Readability.js](https://github.com/mozilla/readability). This is an node
library that contains the readability library used for the FireFox Reader
view. In a web browser, you must directly pass the `document` object from the
browser DOM to the library. If used in a node application, you'll need to use
an [external DOM library like jsdom](https://github.com/jsdom/jsdom). Either
way the code is simple:

```js
var article = new Readability(document).parse();
```

or in the case of a node app:

```js
var { Readability } = require('@mozilla/readability');
var { JSDOM } = require('jsdom');
var doc = new JSDOM("<body>Look at this cat: <img src='./cat.jpg'></body>", {
  url: "https://www.example.com/the-page-i-got-the-source-from"
});
let reader = new Readability(doc.window.document);
let article = reader.parse();
```

Ideally I should create an API that accepts a URI as a parameter and returns
the parsed document to the caller. Invoking this from a Chrome extension 
should make it very straightforward to "clip" a web page into a personal
knowledgebase.

Large language models like GPT-3 show real promise in this area as well. In
this
[article](https://www.pragnakalp.com/question-answering-using-gpt3-examples/), 
the authors use GPT-3 to answer questions based on text extracted from a 
document. Starting at 2:47 in the video below is a great demo of this working


{{ youtube(id="8psgEDhT1MM")}}
