# JavaScript Basics

## Formal definition

JavaScript is a programming language. A programming languages is a formally constructed language designed to communicate instructions to a computer. Programming languages can be used to create programs to control the behavior of a machine/computer or express algorithms. -- Wikipedia

## My definition
JavaScript, and programming languages in general, are tools used to process data.

## Data Types

- Primitive
	- String
	- Number
	- Boolean
	- Undefined
	- Null
- Non-Primitives
	- Object (Object Literal)
	- Array
	- RegEx

## Primitives

### Strings

- ‘This is a string'
- “This is also a string”
- `This is a string too`
- ‘One ' + ‘plus ' + ‘one ‘ + ‘equals ' + ‘two.'

### Numbers

- 42
- 42 + 42 //= 84
- 42 - 42 //= 0
- 42 / 42 //= 1
- 42 * 42 //= 1764
- 42 % 5 //= 2
- var num = 42;
- num++ (or ++num) //= 43
- num—— (or ——num) //= 41

### Booleans

- 1 > 2 or 1 >= 2 //= false
- 1 < 2 or 1 <= 2 //= true
- 1 != 2 or 1 !== 2 true //= true
- 1 == 1 or 1 === 1 //= true
- (10 === 20 || 10 === 10) //= true
- (10 === 20 && 10 === 10) //= false
- !(10 === 20) //= false

### Null and Undefined

- Null: variable has no value
- Undefined: variable value has not been set
- Example:
	- var n = null;
	- var n;

## Exercises

1. Combine your first, middle, as last name using strings and the plus operator(+). Don't forget to add spaces! I.e. var myname = ‘Adam ‘ + ‘Recvlohe'
2. Add a string to a set of numbers, i.e. ‘3' + 4 + 5. Then add a set of numbers to a string, i.e. 4 + 5 + ‘6.' What happens?
3. Take two arithmetic expressions and see if they equal one another, i.e. var num1 = 42 / 42; var num2 = 41 % 5; num1 === num2
4. Write typeof before your variable. What do you get? I.e. typeof myname, typeof num1

## Methods

### String Methods

- length
- toLowerCase()
- toUpperCase()
- trim()
- slice()
- repeat()
- concat()
- charCodeAt()
- includes()

### Number Methods

- parseFloat()
- toFixed()

## Exercises

1. Take your name and find out what the length of it is. Are you including spaces in the length?
2. Take a phrase that you want to shout and write in all lowercase letters. Then call the toUpperCase method on it.
3. Use the slice method to chop that phrase up with a random number written as a string.
4. Take two floating point numbers, i.e. 3.14 and 3.1456, and add them together. Then take the answer and round it to two significant digits.
5.  Add two strings together using concat.
6.  Take a phrase you want to yell, slice the third word of that phrase and repeat that word using the repeat method.
7.  Write your name in unicode using the charCodeAt method.
8.  Check to see if you name includes ‘iron' using the includes method.

## Non-primitives

### Arrays

- []
- created with a set of values;
- var array1 = [];
- var array2 = [1,2,3,4,5,6,7,8,9];
- var array3 = [‘Joe', ‘John', ‘Jacob', ‘Julia', ‘Janice', ‘Jane' ];
- Access values using [] syntax
- For example:
	- array1[0] //= undefined
	- array2[1] //= 2
	- array3[2] //= ‘Jacob'
- You can assign values using this operator at well. For example:
	- array1[0] = 0
	- array2[1] = 0
	- array3[1] = ‘Adam'

## Exercises

1. Create an array of random numbers up to 10. Using the syntax above in how to access values from an array, add up five of those numbers.
2. Create an array of 5 names. Using the syntax above, write a sentence using the + operator and using three of those names. For example: array3[2] + ‘ likes to play basketball, while ' + array3[1] + ‘likes to play baseball.'

### Objects (Object Literals/Hashes)
- {}
- created with a set of key/value pairs
- var object1 = {
	firstName: ‘Adam',
	lastName: ‘Recvlohe',
	middleInitial: ‘E',
	age: '29',
	job: ‘Valpak Developer',
	hometown: ‘St. Pete'
}
- var object2 = {
	0: ‘Bill',
	1: ‘Blake',
	2: ‘Billy',
	3: ‘Bob'
}
- Access values using the [] or . syntax
- For example:
	- object1.firstName //= ‘Adam'
	- object1[‘lastname'] //= ‘Recvlohe'
	- object2[0] //= ‘Bill'
	- As before, you can assign values in the same way. For example:
		- object1.favoriteFood = ‘Mexican'

## Exercises

1. Create an object that describes you as a person. Using the syntax above, write a sentence about yourself and accessing those values. For example: ‘Hello, my name is ‘ + object1.firstName + ‘ ' + object1.lastName + ‘. I am from ' + object1.hometown + ‘.'
2. Create an object of 3 names. Using the syntax above describing how each person finished the race. For example: object2[3] + ‘came in last place.'

## Methods

### Array Methods

pop()
push()
shift()
unshift()
slice()

### Object Methods

Object.keys()
Object.getOwnPropertyNames()
Object.values()

## Exercises

1. Get the object keys of the object that describes you as a person. Then, using the pop method, return the last key.
2. Get the object values of the object that lists persons place in finishing a race. The, using the shift value, return the first person's name that won the race.
