ng-new-object-test
==================

Test the memory consumption of different ways of creating objects in javascript for angular Factories. I suggest you to read this article: https://developer.chrome.com/devtools/docs/javascript-memory-profiling

#### About the test
Here we test different approachs of object creation in Javascript using Angular to see the difference between them.
First of all I will say that is better to use 'new' than {}, so then in the Profile you can measure the instances that you have created.

#### Aproach 1: Construct an object with {} (is like do new Object())

```
var point = {
  x: x,
  y: y
};

point.move = function(x,y) {
  this.x += x;
  this.y += y;
};
```

#### Aproach 2: Construct an object with new and with methods attached to the instance.
```
 var Point2 = function(x,y) {
  this.x= x;
  this.y= y;

  this.move = function(x,y) {
    this.x += x;
    this.y += y;
  };

};
```

#### Aproach 3: Construct an object with new and with methods attached to the prototype. (Best option, less memory consumption)
```
 var Point = function(x,y) {
  this.x= x;
  this.y= y;
};

Point.prototype.move = function(x,y) {
  this.x += x;
  this.y += y;
};
```

#### See results
Open the dev tool and go to Profiles. Then take a heap snapshot and see the results. If you read the link that I told you at the beggining you will know what I am talking about.

#### Demo
http://jsfiddle.net/87akyybu/


