
# Sample Teach - Prototyopal Inheritance 

## Recap 
What have we covered so far? 
* We have covered variables, functions, objects, and callbacks in JavaScript. 

## Learning Objectives 
By the end of the lesson, you will be able to do the following: 
* Use the constructor function to create objects
* Use the understanding of prototypes to create an prototype example 
* Understand the prototype chain
* Understand why prototypes are useful

## Opening
Today, we will be covering prototypal inheritance in Javascript! We have already covered variables, functions, objects, and callbacks in JavaScript which on the surface is super powerful, because it allows us to create complicated programs to develop web apps like most websites we visit everyday! So let's take a look under the hood. 


## Constructor Functions! 
By now, you have created an object already, but how did you create it? 
More than likely, it was like this below: 
```javascript
let car = {
	make: 'BMW',
	model: '525i',
	year: '2019'
}
```
Or better known as object literals. Object literals are a simple straight-forward way to create an object with key-value pairs.

Let's try this a new way, using keyword new. 

```javascript
function Car(make, model, year) {
	this.make = make; 
	this.model = model; 
	this.year = year; 
}

let lizCar = new Car('BMW', '525i', '2019'); 

```
Yay! We created an object using the constructor function Car in the code snippet. Then we also created an instance of the Car object using keyword new. Why is this so powerful? It is because we can re-use the Car object to create many more cars. Let's try this out! 


```javascript
function Car(make, model, year) {
	this.make = make; 
	this.model = model; 
	this.year = year; 
}

let lizCar = new Car('BMW', '525i', '2019'); 
let donCar = new Car('VW', 'Golf', '2012'); 
let jenCar = new Car('Nissan', 'Skyline', '2014'); 
console.log(lizCar, donCar, jenCar);
``` 

## Heat Check 1
![](https://media.giphy.com/media/3o6Zt1NkjoYfCEv3CU/giphy.gif)
* We covered how we create objects using object literals which is a straight forward way of creating objects with key value pairs. 
* Second, we introduced the constructor function, that's right, the function Car is the constructor function that creates the Car object in our example! 

## Prototypes
I thought we were learning about prototypal inheritance? Why did we learn about constructor? Answer: inheritance!
Prototypes are how objects in JS inherits its methods and properties. This sounds a lot like classes. What are classes? In JavaScript, constructors are often referred to as "classes". And just our luck, we covered constructor functions! For now, let's think of classes as blueprint for new objects and prototypes are backup or a delegate object. 

### Heat Check 2: What are prototypes?
![](https://media.giphy.com/media/CrnKx2mxUzGiQ/giphy.gif)

Prototypes are saying for this object, use this other object as a backup. 

### Prototypes in ACTION! 
![](https://media.giphy.com/media/8L13IFbMbEwV2/giphy.gif)

In celebration of the upcoming finale episode of Game of Thrones, lets create some direwolves. 

## Example 
```javascript
const direwolf = {
	name: function(name) {
		this.name = name;
	},
	sayHello: function() {
		console.log('woof woof, my name is: ', this.name)
	}
}; 

const robbStark = Object.create(direwolf); 
console.log('robbStark: ', robbStark ); 
console.log('direwolf: ', direwolf); 

```
In the example, the robbStark is an empty object but yet the direwolf object was created with name and sayHello. Let's take it a step further, let's run `direwolf.sayHello("Grey Wind")`. 

It worked? 

When we used Object.create, we set up a link between the prototype object, direwolf, and robbStark which inherits from its prototype. 

## Prototype Chain
We're taking a deeper dive to look at the javascript compiler and what is going on under the hood! 
So what's going on:
* the compiler is looking at the robbStark object to see if there is a sayHello method attached to it but we know that there isn't a setStatus on the robbStark object.
* the compiler now moves one level up the prototype chain, the direwolf. There, it sees the sayHello method and calls it.

## Heat Check - Why are prototypes useful? 
![](https://media.giphy.com/media/l41lVCaNfN7zjhFsc/giphy.gif)

In the example, we can see that:
* Prototypes are much more flexible because it allows the object to inherit from multiple prototypes. 
* To keep it simple, remember that Prototypes are Objects Linking to Other Objects. 


## Extra Resources 
### Objects 
* https://stackoverflow.com/questions/9108925/how-is-almost-everything-in-javascript-an-object

### Constructors
* http://adripofjavascript.com/blog/drips/basic-inheritance-with-javascript-constructors.html

### Prototypes
* https://hackernoon.com/understanding-javascript-prototype-and-inheritance-d55a9a23bde2
