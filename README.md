# Javascript alchemy with Bragadino coding style.

On my programming journey, I have noticed an awesome coding style that I will call "Bragadino". Maybe there is an actual name for it but we'll call it that for now.

Get ready for some serious alchemy here, we will be turning dust into gold.
> Skim through the entire markdown. if you're up for the task, grab the exercise file and try solving as much as you possibly can. Only after some blood, sweat and tears, check the solutions that are pretty much solved with Bragadino's coding style.


To give you a flavor, this is a solution to a problem following the bragadino style.

```Javascript
function swap(string){
	return string.split('').map(function(char) {
		return (char === i.toLowerCase()) ? char.toUpperCase() : char.toLowerCase();
	}).join('');
}

console.log(swap('ObAMa')) // ===> 'oBamA'

```
The style is really helpful when dealing with large projects (500 lines or more). It helps you make your algorigthms (functions) compact and decrease the probability that you will confuse yourself or others. Instead of patching together a bunch of if statements and for loops (what I did on my first months of JS coding). You immediately return the function chaining it with methods to get a predictable and easy to reason with code (while being aware of edge cases). In most cases, you will write less than 3 lines of code to get to your desired outcome.

## Here are the questions and implementations:

#### 1- Write a function that accepts two arguments and returns the remainder after dividing the larger number by the smaller number.

```Javascript
function remainder(a, b){
  return (a > b) ? a % b : b % a;
}

console.log(remainder(55, 3)) // ===> 1
console.log(remainder(30, 3)) // ===> 0


/* --- Deconstruction
* if the condition is true, the first expression is returned
* otherwise the second is returned.
*/
```

#### 2- Write a function that takes a string, then swaps the case for each of the letters.

```Javascript
function swap(string){
	return string.split('').map(function(i) {
		return (i === i.toLowerCase()) ? i.toUpperCase() : i.toLowerCase();
	}).join('');
}

console.log(swap('ObAMa')) // ===> 'oBamA'


/* --- Deconstruction
* .split('') creates an array by seperating all characters in the string
* .map() loops over the array passing the values to the function which
* checks whether the character is upper or not then swaps it
* .join('') concatenates the array into a string
* => try doing the same task with .reduce() instead of map().join()
*/

```

#### 3- Write a function that takes an array and an item, and returns true if the item belongs to the array

```Javascript
function isInArray(array, item) {
	return array.indexOf(item) > -1;
}

console.log(isInArray([1,2,4,5], 3)) // ===> false

/* --- Deconstruction
* .indexOf(item) checks if the item is in the array and returns the index, otherwise
* it returns -1, if the item is not in the array.
* thus with array.indexOf(item) > -1 we can get either true or false.
*/

```

#### 4- Have you ever used .some() in your alchemist gigs? Here's your chance Write a function that takes an array and a function then returns true if the function returns true for any item in the array

```Javascript
function any(arr, fun){
	return arr.some(fun);
}

console.log(any([1,2,3,4], function(v){return v>3} )); // ===> true
console.log(any([1,2,3,4], function(v){return v>4} )); // ===> false

/* --- Deconstruction
* .some() is passing each value in the array to the passed function 
* then returns true if any of the condition is true 
*/

```

#### 5- Write a function that takes an array and a function then returns true if the function returns true for all item in the array

```Javascript
function all(arr, fun) {
	return arr.every(fun);
}

console.log(all([1,2,3,4,5], function(v){return v<6} )); // ===> true
console.log(all([1,2,3,4,5], function(v){return v>9} )); // ===> false


/* --- Deconstruction
* .every() is passing each value in the array to the passed function 
* then returns true if all of the conditions return true
* By the way, this is the power of functional programming (write less, do a lot more)
*/

```

#### 6- Write a function that takes a string then outputs an array containing all the words and their lengths
> ex: addLength('you will win') => ["you 3", "will 4", "win 3"]

```Javascript
function addLength(str){
	return str.split(' ').map(function (i) {
		return i + ' ' + i.length;
	});
}

console.log(addLength('apple ban')) // ===> ["apple 5", "ban 3"]
console.log(addLength('you will win')) // ===> ["you 3", "will 4", "win 3"]

/* --- Deconstruction
* .split(' ') creates an array by splitting each word
* .map() return the word, a space, and the word's length
*/
```

#### 7- reduce is one of the most powerful tools for the alchemist. Let's dive in. Write a function that takes an array containing numbers then returns the sum of the numbers in the array 

```Javascript
function sumArray (array) {
	return array.reduce(function (sum, val) {
		return sum + val;
	}, 0);   
}

console.log(sumArray([3, 5, 6, 8, -9]));    // ===> 13
console.log(sumArray([3, 5, 6, 100, -9]));  // ===> 105



/* --- Deconstruction
* you can think of sum as our store for whatever we add to it
* here reduce is looping over values at every index and adding the values
* it finds to sum then returns it.
* Read Mozilla's article on .reduce() to learn more.
*/

```

#### 8- Write a function that takes a single word (string) as argument then returns the indexes of all capital letters in the string.

```Javascript
function findCapitals(word) {
	return word.split('').reduce(function (sum, val, index) {
		return val === val.toUpperCase() ? sum.concat(index) : sum;
	}, []);
}

console.log(findCapitals('ReMEmbEreD')) // ===> [0, 2, 3, 6, 9]

/* --- Deconstruction
* .split('') is seperating the characters into an array
* .reduce() is traversing the array checking whether the character is uppercased
* then concatenates the index into the sum ([]) array and returns it at the end
*/

```

#### 9- Write a function that squareEveryDigit of passed in number

```Javascript
function squareEveryDigit(num) {
	return ('' + num).split('').map(function (val) {
		return val * 2;
	}).join('')
}

console.log(squareEveryDigit(999)) //===> '181818'

/* --- Deconstruction
* We are coercing the number into a string, split('') then transforms it
* into an array separating every digits
* map multiplies the val on every index by 2.
* note: we are getting a string as a result.
* you can coerce it into a number with Number(result)
* Alchemist's extra practice => sum all digits using .reduce()
*/
```

#### 10- Write a function countVowels that returns the number of vowels in a given String

```Javascript
function countVowels(string) {
	return string.toLowerCase().split('').reduce(function (sum, i) {
		return (i =='a' || i == 'e' || i == 'i' || i == 'o' || i == 'u') ? sum += 1 : sum;
	}, 0)
}

console.log(countVowels('abcedfg')) // ===> 2
console.log(countVowels('Mohamed Hayibor')) // ===> 6 ;)

/* --- Deconstruction
* .split('') => returns an array splitting up all characters in string
* reduce checks if char is a vowel then increments sum if it is
*/

```

#### 11- Scaling up: write a function that takes a string and a number (n) that returns a string that repeats the initial string (n) number of times.

```Javascript
function repeatIt(string, n) {
	return (typeof string == 'string') ? Array(n+1).join(string) : 'not a string';
}

console.log(repeatIt('Mohamed', 3)) // ===> 'MohamedMohamedMohamed'
console.log(repeatIt(30, 3)) // ===> 'not a string'

/* --- Deconstruction
* Array(n+1) creates an array with length (n)
* .join(string) concatenates the array while inserting the string
* at every indices
*/

```

#### 12- Write a function that accepts an array of 10 integers (between 0 and 9) that returns a string of those numbers in the form of a phone number expl: "(123) 456-7890"

```Javascript
function createPhoneNumber(numbers){
	var format = "(xxx) xxx-xxxx";
	return format.split('').reduce(function (str, i) {
		return (i === 'x') ? str += numbers.shift() : str += i;
	}, '')
}

console.log(createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]));
//===> "(123) 456-7890"


/* --- Deconstruction
* .split('') coerces format into an array seperating the values at every indice
* .reduce() checks if the char at an index is equal to 'x', in that case
* it replaces the 'x' by the corresponding number
*/

```

#### 13- Write a function that takes a DNA sequence as a string then swap all elements to it's complement so that: 'A' -> 'T', 'T' -> 'A', 'C' -> 'G' and 'G' -> 'C'

```Javascript
function DNASwap(dna){
    return dna.toUpperCase().split('').reduce(function (sum, elem) {
    	return (elem === 'A') ? sum += 'T' :
    		   (elem === 'T') ? sum += 'A' :
    		   (elem === 'G') ? sum += 'C' :
    		   (elem === 'C') ? sum += 'G' : sum;
    }, '');
}

console.log(DNASwap('ATTGC')); // ===> 'TAACG'

/* --- Deconstruction
* The dna string is uppercased, then the characters are seperated into array with split
* .reduce() goes through all the characters in the array to swap each to it's
* complement. Then returns sum (string) at the end. Again check out Mozilla's article
* on reduce if you are having trouble. 
*/
```

#### 14- How about we attack objects with our alchemy? Write a function that takes an object and generates a human readable string from its key/value pairs

```Javascript
function keyAndValues(obj) {
	return Object.keys(obj).map(function (key) {
		return key + ' = ' + obj[key];
	}).join(',')
}

console.log(keyAndValues({a: 1, b: '2'})) // ===> 'a = 1,b = 2'


/* --- Deconstruction
* Object.keys(obj) returns an array containing the object's properties (keys)
* .map() loops through the array returning the key, equal sign and value at every index
* .join(',') concatenates the array into a string inserting a comma in between
*/
```
#### 15- Write a function that takes an array of booleans and returns the number of trues (boolean value)
```Javascript
function numberOfTrues(array) {
	return array.filter(Boolean).length;
}

var array1 = [true, true, true, false,
              true, false, true, true ];

console.log(numberOfTrues(array1)) // ===> 6


/* --- Deconstruction
* filter does what it means in plain language, it filters the array
* to pick out values that returns true when passed to the callback
* here Boolean could've been replaced by the callback function :
* function(x) { return x == true; }
*/
```

#### 16- Write a function that adds your name or whatever value a 1000 times to an array
```Javascript
function thousandTimes(value) {
	return Array.apply(0, Array(1000)).map(function (i) {
		return value;
	});
}

console.log(thousandTimes('Mo')) // ===> ['Mo', 'Mo'..., 'Mo']

/* --- Deconstruction
* Array.apply(o, Array(1000)) create an array of length 1000
* map returns the value passed in at every index ----------
* Alchemist exercise: Modify the function so that you can pass a second
* argument to make the length of the array variable
*/
```

#### 17- Let's go badass on arguments and arrays write a function that sums all numbers passed as arguments
```Javascript
function sum () {
	return Array.prototype.reduce.call(arguments, function(sum, v) {
		return sum + v;
	}, 0)
}
console.log(sum(1, 45, 5, 56, 56, 56, 9)) // ===> 228

/* --- Deconstruction
* If you're getting lost on this one don't panic,
* We are just taking an array (of all arguments) then applying reduce to it
* for instance one could do: Array.prototype.slice.call(arguments).reduce(callback)
* You could even replace Array.protype with just []:
* => [].reduce.call(arguments, function(sum, v) { return sum + v; }, 0)
*/

```

#### 18- Write a dropCap function that capitalizes the first letter of every word that has length greater than 2 leaving smaller words as they are.
```Javascript
function dropCap(n) {
	return n.toLowerCase().split(' ').map(function (val) {
        return (val.length > 2) ? val.charAt(0).toUpperCase() + val.slice(1) : val;
  	}).join(' ');
}

console.log(dropCap('apple')) // => "Apple"
console.log(dropCap('alexander of macedonia')) //=> "Alexander of Macedonia"

/* --- Deconstruction
* Here, we are lowercasing all letters in the string then dividing every word
* into an Array. Then map check if the word's length is greater than 2
* In that case, the first letter is uppercased.
* .join('') is concatenating all words in the array into a string
*/
```

#### 19- Write a function that compares each pair of integers (same index) from 2 arrays and returns a new array of large numbers. Assumption: Both arrays have the same length
```Javascript
function getLargerNumbers(array1, array2) {
	return array1.map(function (val, index) {
		return Math.max(val, arr2[index]);
	});
}

var arr1 = [13, 100, 15, 17, 40];
var arr2 = [8, 14, 53, 17, 1];

console.log(getLargerNumbers(arr1, arr2)); // ===> [13, 100, 53, 17, 40]


/* --- Deconstruction
* .map() is looping through array1 values, comparing each array1 and array2's
* value at corresponding index then returning the maximum between the two
* - Math.max() returns the maximum when given arguments. "use .apply() with arrays"
* exple: Math.max.apply(null, array1) ===> 100
*/

```

#### 20- Do you use .every() often, let's take a stab at it. Write a function that checks if all arguments passed in are numbers
```Javascript
function allNumbers() {
	return [].every.call(arguments, function (val) {
		return typeof val === 'number' && !isNaN(val);
	})
}

console.log(allNumbers(2, 5, -9, 4)) // ===> true
console.log(allNumbers(873, 0, -9, NaN)) // ===> false
console.log(allNumbers(2, '6', -9, 4)) // ===> false



/* --- Deconstruction
* [].every.call(arguments, callback) is equivalent to
* Array.prototype.slice.call(arguments).every(callback)
* We are creating an array with all arguments passed. Then 
* Check out Mozilla's article on NaN to learn more about it
*/
```

#### 21- Alchemist 1.0.0: Entering the Alchmist dojo. Write a function that a non-negative integer and returns an array of the individual digits.
```Javascript
function digitize(num) {
	return String(num).split('').map(Number);
}

console.log(digitize(457809))   // ===> [4, 5, 7, 8, 0, 9]
console.log(digitize(4223211))  // ===> [4, 2, 2, 3, 2, 1, 1]

/* --- Deconstruction
* As you could imagine the alchemist loves brevity:
* String(num) is coerces num into a string. (could've also used num.toString())
* .split('') is creating a array by separating all the existing characters
* .map(Number) is looping through the array and returning number types
* for instance: .map(Number) is same as .map(function (x) { return Number(x); })
*/
```



#### 22- Write a function that takes an array, find the duplicates in that array and then returns a new array of unique values of the duplicates.
```Javascript
function duplicates(array) {
	return array.filter(function (val, index) {
		return array.indexOf(val) !== array.lastIndexOf(val) &&  index <= array.indexOf(val);
	})
}

console.log(duplicates([1, 2, 4, 4, 3, 3, 1, 5, 3, '5'])) // [1, 4, 3]


/* --- Deconstruction
* .filter() is testing whether our condition is true at every index
* array.indexOf(val) !== array.lastIndexOf(val) gets us all of the duplicates
* Now to get the unique values of the duplicates we can make our condition stricter
* with: index <= array.indexOf(val)
*/
```

#### 23- Your alchemist gigs got you a lot of money, so you decide to invest in a stock. Write a function to know how much your investment is worth with the given arguments:
> - invested(number), the amount of money you initially invested in the given share
> - changes(array of numbers), contains your shares daily movement percentages

***(round your final value using .toFixed(2))
```Javascript
function investmentValue (invested, changes) {
	return changes.reduce(function(sum, i) {
		return sum * (1 + (i/100));
	}, invested).toFixed(2)
}

console.log(investmentValue(1000, [0, 2, 3, 6])) // ===> "1113.64"


/* --- Deconstruction
* .reduce() is looping over the daily changes, computing the investment value
* for that day then storing it into sum which gets returned in the end.
* note that rounding with .toFixed(2) outputs a string.
* => Math.round(finalValue * 100) / 100 is an alternative: returns a number
*/

```

#### 24- Did you know that you could use the index of the array with map, reduce, reduceRight, every, filter, some ... Well, let's dive in an play with it. Write a function such as add(3,4,5); returns 26 => "( 3 * 1 ) + ( 4 * 2 ) + ( 5 * 3 )"
```Javascript
function add() {
	var arr = Array.prototype.slice.call(arguments);
	return arr.reduce(function(sum, val, index) {
		return sum + val * (index + 1);
	}, 0);
}

console.log(add(1, 4, -5, 5)); // ===> 14
console.log(add(9, 1, 5, 7)); // ===> 54


/* --- Deconstruction
* var arr is assigned to an array that grabs all arguments being passed to the function
* .reduce() is looping over each value within the array, computing then storing the 
* value in sum which finally gets returned.
* Asside: Let's refactor the code right below
*/

function add() {
	return [].reduce.call(arguments, function(sum, val, index) {
		return sum + val * (index + 1);
	}, 0);
}

console.log(add(1, 4, -5, 5)); // ===> 14
console.log(add(9, 1, 5, 7)); // ===> 54

/* --- Deconstruction
* The two functions work the same way but this one is much shorter.
* You can check out Mozilla's article on .call() to learn more
*/
```

#### 25- Create function with two arguments that will return a list of length (n) with multiples of (x). Assumptions: n && x > 0
```Javascript
function countBy(x, n){
  return Array.apply(null, Array(n)).map(function(v, i){
    return (i + 1) * x;
  });
}

console.log(countBy(1,10)) // ===> [1,2,3,4,5,6,7,8,9,10]
console.log(countBy(2,5)) // ===> [2,4,6,8,10]

/* --- Deconstruction
* Array.apply(null, Array(n)) => creates an array of length (n)
* map => returns x * (j+1) 'calculates' at every existing indice
* thus replacing all the undefined in the arry
*/

/* -- for the sake of Craziness
* you could replace: Array.apply(null, Array(n)) by Array(n+1).join(x).split('')
* note you could even replace .join(x) with .join(1) or whatever number
* => if you know why you've just started your journey as a badass alchemist.
*/

```

#### 26- Write a function that takes an integer as argument and outputs a string with currency format. ex: 123456 => "123,456"
```Javascript
function toCurrency(price) {
	return price.toString().split('').reverse().reduceRight(function(string, val, index) {
		return (index != 0 && index % 3 == 0) ? string += (val + ',') : string += val;
	}, '')
}


console.log(toCurrency(123456789012)) // ===> "123,456,789,012"
console.log(toCurrency(123456)) // ===> "123,456"

/* --- Deconstruction
* .toString() coerces price into a string
* .split('') creates an array by seperating all characters
* .reduceRight acts like .reduce() but from the right to left
* Sidenote => you could map instead and then reverse() and .join('')
*/

```

#### 27- How about including recursion into our alchemy? Write a function that takes an array of values. Sum every number value in the array, and any nested arrays (to any depth). Ignore all other types of values.
```Javascript
function arraySum(array) {
  	return array.reduce(function (sum, i) {
  		return Array.isArray(i) ? arraySum(i) + sum : sum + 
  			((typeof i == 'number' && !isNaN(i)) ? i : 0);
  	}, 0);
}


console.log(arraySum([1, 2, NaN, [1, 2, '3']])) // ===> 6

/* --- Deconstruction
* .reduce() as we used it before passes all items in the array to the function 
* which first checks if the item passed is an array, if it is, it calls function arraySum
* to that array (recursion), adding the sum when it is done computing on that array.
* If the item is not an array, it takes the sum then add 0 or the item if it is a number
* Woof: that was a lot, you can learn more about Array.isArray, isNaN on Mozilla's site
*/
```

#### 28- Let's have some wild laughs now with our skills. Write a function, mumbling such as:
> mumbling('abcd') => "A-Bb-Ccc-Dddd"

> mumbling('darius') => "D-Aa-Rrr-Iiii-Uuuuu-Ssssss"

```Javascript
function mumbling(str) {
	return str.split('').map(function (val, index) {
		return val.toUpperCase() + Array(index + 1).join(val).toLowerCase();
	}).join('-');
}

console.log(mumbling('Alchemist'));
// ===> 'A-Ll-Ccc-Hhhh-Eeeee-Mmmmmm-Iiiiiii-Ssssssss-Ttttttttt'

/* --- Deconstruction
* After splitting up the characters into an array, we are returning
* the proper amount of mumbles by concatenating the uppercased character (val) and
* the appropritate number of lowercased characters depending on the current index
* at every index. Then we are joining all the values in the array with a dash 
* in between with .join('-')
*/
```
#### 29- Write a function that takes a string and returns the same string with the rules:
> with all even indexed characters in each word upper cased
> all odd indexed characters in each word lower cased. 

```Javascript
function originalCase(string){
	return string.split(' ').map(function (word) {
		return word.split('').map(function (val, index) {
			return (index % 2 === 0) ? val.toUpperCase() : val.toLowerCase();
		}).join('');
	}).join(' ');
}

console.log(originalCase( "Pocahontas" ));  //=> returns "PoCaHoNtAs"
console.log(originalCase( "Marcus Aurelius" ));  //=> returns "MaRcUs AuReLiUs"

/* --- Deconstruction
* Did you know that you could nest map, reduce... (functions for that matter)
* Firstof, we are splitting the string into words:
* Firt map: iterates over the words
* Second map: iterates over the characters returns an upper or lower case letter
* Badass Alchemist => Refactor the code using .reduce()
*/
```

#### 30- Alchemy and a typical interview question: Write an algorithm that takes an array and moves all of the zeros to the end preserving the order of the other elements.
```Javascript
function moveZeros (array) {
	return (array.filter(function (val1) {
		return val1 !== 0;
	})).concat(array.filter(function (val2) {
		return val2 === 0;
	}));
}

console.log(moveZeros([false,1,0,1,2,0,1,3,"a"])) // ===> [false,1,1,2,1,3,"a",0,0]


/* --- Deconstruction
* With all practice we've had, parsing this code should not be a sweat:
* If you have noticed. ().concat() is concatenating two arrays here.
* The first one filters all values not equal to Zero
* The second one filters all the zeros, thus solving the problem easily.
*/

```

#### 31- I want to draw your attention on an insiduous temptation on nesting functions and getting lost in the process. Our goal as an alchemist is to use powerful tools that help us solve problems the easiest way possible, rather than causing confusion. Let's make the case with the following exercise:


>Implement a function (same as algorithm) that determines whether a string is an isogram. An isogram is a word that has no repeating letters, consecutive or non-consecutive. Assume the empty string is an isogram. Ignore letter case.

```Javascript
/*
+----------------------------------------+
 Code 1: correct but hard to understand
+----------------------------------------+
*/

function isIsogram(str){
	return str.toLowerCase().split('').every(function(i, j, k) {
		return !k.some(function (x, y) {
			return i == x && j != y;
		});
	});
}

console.log(isIsogram( "Dermatoglyphics" )) //  ===> true
console.log(isIsogram( "Mohamed" )) // ===> false

/*
+----------------------------------------------+
 Code 2: correct and much easier to understand
+----------------------------------------------+
*/

function isIsogram(string){
	return string.toLowerCase().split('').every(function(val, index, array) {
		return array.indexOf(val) === array.lastIndexOf(val);
	});
}


console.log(isIsogram( "Dermatoglyphics" )) //  ===> true
console.log(isIsogram( "Mohamed" )) // ===> false

/* --- Deconstruction
* Don't sweat it, if you can't parse and understand Code 1. When I wrote it,
* it was the fist "ahah" moment that I was about to confuse myself.
* Code 2 is easy to parse in your mind:
*  - we are lowercasing all letters in the string
*  - spliting the characters into an array
*  - every is checking whether the first and last index of a character
*	 are the same (meaning it is unique) for all characters in the array
*/

```

#### 32- Have you ever wrote an encoder? let's create one. Write a duplicate encoder (function) that takes a word (string) then returns a string composing of "<" if the character is unique or ">" otherwise
> exple: duplicateEncoder('programmer') ===> "<><<><>><>"

```Javascript
function duplicateEncoder(word){
	return word.toLowerCase().split('').reduce(function (sum, val, index, array) {
	    return array.indexOf(val) === array.lastIndexOf(val) ? sum + '<' : sum + '>';
    }, '')
}


console.log(duplicateEncoder('bragadino')); // ===> "<<><><<<<"


/* --- Deconstruction
* We tackled this one. To get more practice with indexOf and lastIndexOf
* However one could solve the problem with .filter(), use .map().join() or a
* bunch of if or for loops. All depends on how the programmer decides to solve
* the problem. Our rule of thumb is "less and easier to reason about" code
* is the gold. The alchimist tries to get to perfection everyday.
*/
```

#### 33- given a string, replace every letter with its position in the alphabet.
> Exple: a being 1, b being 2, etc. Ignore any character that is not a letter.
> Inject a space between the numbers for legibility

```Javascript
function alphabetPosition(string) {
	return string.toLowerCase().split('').reduce(function(sum, val) {
		return (val.charCodeAt() >= 97 && val.charCodeAt() <= 122) ?
			sum += (val.charCodeAt() - 96) + ' ': sum;
	}, '').trim()
}

console.log(alphabetPosition("The sunset sets at twelve o' clock."))
// ===> "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"

/* --- Deconstruction
* This function looks complex from the outside but is easy to understand when
* parsed. The string is lowercased then every seperated into an array
* reduce() is checking if the character is a letter at every index then returning
* its position in the alphabet. "Play widly with it to understand how it works"
* - We used .trim() to remove the space at the end of string
* - You can learn more about charCodeAt() on Mozilla's website
*/
```

#### 34- Write a global flatten method that takes any number of arguments and flattens them into a single array. Any nested arrays, no matter how deep should be flattened into the single array result.
> Exple: flatten(3 , ['John', 7], [NaN, 9], [[4], ['c']]) ===> [ 3, 'John', 7, NaN, 9, 4, 'c' ]

```Javascript
function flatten() {
	return [].reduce.call(arguments, function(sum, val) {
		return Array.isArray(val) ? sum.concat(flatten.apply(null, val)) : sum.concat(val);
	}, []);
}

console.log(flatten(null , ['bragadino', {a: 2}, 7, [['Mo'], ['c']] ], [NaN, 9]));
// ===> [ null, 'bragadino', { a: 2 }, 7, 'Mo', 'c', NaN, 9 ]


/* --- Deconstruction
* One way to tackle this excercise is think about recursion. First let's think about
* what data types we are dealing with. Here we have to think of all the suspects,
* strings, numbers, NaN, null, arrays and objects. Now comes how do we dive down into
* an array. ** finish later ***
* 
*/
```

##### Obviously, the problems can be solved in multiple ways. I have tested the solutions I provided multiple times. Let me know if I have missed some edge cases.

By the way, I chose the name "Bragadino" because of a fascinating story about an Alchemist. You can read more about it on Robert Green's book: 48 laws of power. The story is on law 32.

Anyways, you will acquire alchemist powers once you've worked on more than half of the exercises. Good luck.

![Alchemist](http://res.cloudinary.com/masteryoperation/image/upload/v1450834679/alchemist_mtddlh.png)
