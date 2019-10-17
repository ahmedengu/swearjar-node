# swearjar-extended

Profanity detection and filtering library.

[![Build Status](https://travis-ci.org/raymondjavaxx/swearjar-node.svg?branch=master)](https://travis-ci.org/raymondjavaxx/swearjar-node)

## Installation

    npm install --save swearjar-extended

## Usage

### swearjar.profane(text)

Returns true if the given string contains profanity.

    var swearjar = require('swearjar');
    swearjar.profane("hello there"); // false
    swearjar.profane("hello mother f-bomb"); // true

### swearjar.censor(text)

Replaces profanity with asterisks.

    var clean = swearjar.censor("f-bomb you"); // **** you

### swearjar.words(text)

Get the words alongside there categories.

    swearjar.words('fuck you john doe'); // { fuck: ['sexual'] }

### swearjar.scorecard(text)

Generates a report from the given text.

    swearjar.scorecard("f-bomb you"); // {sexual: 1, inappropriate: 1}

### swearjar.loadBadWords(path)

Loads a dictionary of words to be used as filter.

NOTE: A US English default list located in the config directory is included and loaded by default.

    swearjar.loadBadWords('./config/profanity.json');

A dictionary is just a plain JSON file containing an object where its keys are the words to check for and the values are arrays of categories where the words fall in.

```
{
  "regex": {
    "\\w*fuck\\w*": [
      "category1",
      "category2"
    ],
    "word2": [
      "category1"
    ],
    "word3": [
      "category2"
    ]
  },
  "simple": {
    "word1": [
      "category1",
      "category2"
    ],
    "word2": [
      "category1"
    ],
    "word3": [
      "category2"
    ]
  },
  "emoji": {
    "1f4a9": [
      "category1",
      "category2"
    ],
    "word2": [
      "category1"
    ],
    "word3": [
      "category2"
    ]
  }
}
```


## Acknowledgements

`swearjar-node` is based on [Swearjar](https://github.com/joshbuddy/swearjar) (Ruby) and [Swearjar PHP](https://github.com/raymondjavaxx/swearjar-php).
