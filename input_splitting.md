# Input Splitting

How will Printdown see words? How will it separate input into words? I think I should keep it as simple as possible, so I am going to have PrintDown just split at white space. 


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
                throw "Unknown word";
            }
        }
    };
}
```