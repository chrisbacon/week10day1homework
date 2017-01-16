#JS Day 1 Homework

Go through each sample code and work out what the output will be and explain what happened.

### Episode 1
```js
var name = 'Keith';

var printName = function() {
  console.log('My name is ' + name );
};

printName();

```

The function printName has access to the name variable since it has been defined in a containing scope. Therefore the output will be "My name is Keith".

### Episode 2
```js
score = 5;

var result = function() {
  var score = 3;
  return score;
};

console.log(result());

```

Score is initially defined globally as 5, but inside the result function score is defined as 3, which is the value that is returned. Therefore the output will be 5.

### Episode 3
```js
var myAnimals = ['Chickens', 'Cats', 'Rabbits'];

var listAnimals = function() {
  myAnimals = ['Ducks', 'Dogs', 'Lions'];
  for(var i=0;i<myAnimals.length; i++){
    console.log(i + ": " + myAnimals[i]);
  }
}

listAnimals();

```
As above, myAnimals is redefined inside the listAnimals function. Therefore the for loop will iterate through Ducks, Dogs and Lions and print each one out to the log.

### Episode 4
```js
var suspectOne = 'Jay';
var suspectTwo = 'Val';
var suspectThree = 'Keith';
var suspectFour = 'Rick';

var allSuspects = function() {
  var suspectThree = 'Harvey'
  console.log('Suspects include: ' + suspectOne + ', ' + suspectTwo + ', ' + suspectThree + ', ' + suspectFour)
};

allSuspects();
console.log( 'Suspect three is:' + suspectThree );
```

suspectThree is redefined inside allSuspects, therefore allSuspects will print out "Suspects include: Jay, Val, Harvey, Rick". But since it was only redifined locally within the function, outside the function suspectThree remains Keith, and line 63 will produce "Suspect three is: Keith".

### Episode 5

```js
var detective = {
  name : 'Ace Ventura',
  pet : 'monkey'
};

var printName = function(detective) {
  return detective.name
};

var detectiveInfo = function() {
  detective['name'] = 'Poirot'
  return printName(detective);
};

console.log(detectiveInfo());
```

detectiveInfo will redefine the name property of the detective object to Poirot. printName(detective) will therefore return Poirot, which will be returned by detectiveInfo and printed to the log.

### Episode 6
```js
var murderer = 'rick';

var outerFunction = function() {
  var murderer = 'marc';

  var innerFunction = function() {
    murderer = 'valerie';
  }

  innerFunction();
}

outerFunction();
console.log('the murderer is ', murderer);
```

murderer is initially declared as rick. outerFunction redefines it locally as marc, and then calls innerFunction which redefines it as valarie but only within outerFunctions scope. Therefore the murderer is rick.

### Episode 7 - Make up your own episode/s!

Make up your own episode which can be whatever you wish and the rest of the class will work out together what happened and what the output will be.

```js
killer = "son in line for inheritence";

function columbo() {
  function columboAsksQuestions() {
    var killer = "estranged wife";
  }

  function columboAsksMoreQuestions() {
    var killer = "workplace rival";
  }

  function columboFiguresItOut() {
    console.log("Just one more thing...");
  }

  columboAsksQuestions();
  columboAsksMoreQuestions();
  columboFiguresItOut();
}

columbo();
console.log(killer);
