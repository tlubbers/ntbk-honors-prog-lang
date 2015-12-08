# How do I start developing printdown?

As you may except, there are many aspects to a programming language, and countless issues to consider when making design choices. For the purpose of this report, I've narrowed it down to overviews of the two concepts found at the foundation of any programming language, syntax and semantics. 


# Syntax

How will printdown see words? How will it separate input into words? What should it do if it sees a number?

These design choices are very important to a programming languages usability, as well as it's capabilities. The choices I made can be seen in the following source code (discussed below).

```js
function Printdown () {
    var dict = {};

    this.stack = [];
    
    this.theWords = function (new_dict) {
        for (var word in new_dict)
            dictionary[word.toUpperCase()] = new_dict[word];
    };

    this.run = function (text) {
        var lex = new PrintDownLex(text);
        var word;
        var num_val;

        while (word = lex.nextWord()) {
            word = word.toUpperCase();
            num_val = parseFloat(word);
            if (dict[word]) {
                dict[word](this);
            } else if (!isNaN(num_val)) {
                this.stack.push(num_val);
            } else {
                throw "Invalid word";
            }
        }
    };
}
```

The code above tells us the following things about printdown's syntax. 

- printdown separates input words by white space. 
- printdown has a dictionary of words that is referenced during input, if a word matches its pushed on the stack
- if the word is a number, printdown pushes it onto a stack and then continues with input

## Semantics
The dictionary I talked about above will be pre-populated with words that printdown understands and knows what to do with.

The definitions of the words in the dictionary comprise the semantics of printdown. Semantics can be thought of as the meaning of words and symbols recognized by printdown. 

Here is an example of how printdown's semantics could be defined. 

```js
var BasicSettingWords = {
    // NUMCOPIES means the user is about to tell us how many copies of the document should be printed
    "NUMCOPIES": function (terp) {
        if (terp.stack.length < 1) throw "Not enough items on stack";
        var num_copies = terp.stack.pop();
        // Inform the printer
    },
    // PAPERTYPE means the user is about to tell us what kind of paper to print on
    "PAPERTYPE": function (terp) {
        if (terp.stack.length < 1) throw "Not enough items on stack";
        var paper_type = terp.stack.pop();
    }
};
```

## What does all of this mean? What's next?

The main point of the (extremely rudimentary) syntax and semantics definitions above is to formalize a very simple point about print down. That is, printdown will look through text, split it up into tokens whenever it sees a space, and then go through those tokens and make sure all the tokens are either words it understands or numbers.

This may seem overly simple, and it kind of is, but it is also very powerful. We will see this power in the next section. 
