# Simple JavaScript Speed Test Class

While `console.time()` can be used to measure the speed of an operation, it has two inherent problems.

1. It lacks the ability to perform a truly accurate test, in that the results will vary each time the code is run.

2. The execution of `console.time()` itself can greatly add to the overall execution time.

This class provides a more efficient alternative, as well as providing a more accurate result by returning an average execution time based on a given number of repetitions.

### Usage

Say you wanted to measure the execution time of the code to add new members to a list of current members:

```js
var membersNew = ["Cristen Banton", "Kirsten Thiede", "Cyril Punch", "Layne Perillo", "Faviola Leaver"],
    membersCurrent = ["Regan Padillo", "Jay Shuford", "Ferne Amey", "Garrett Hem", "Delila Embrey"];

for (var i = 0; i < membersNew.length; i++) {
  membersCurrent.push(new Member(membersNew[i], 1));
}
```
You would create a new list referencing the member lists:

```js
var listsForTests = [membersNew, membersCurrent];
```
Then create a function expression that contains the code to be tested, changing any references to the original lists to reference the new listOfParams argument passed in to the anonymous function:

```js
var addMembers = function(listOfParams) {
  for (var i = 0; i < listOfParams[0].length; i++) {
    listOfParams[1].push(new Member(listOfParams[0][i], 1));
  }
};
```

Now instantiate the `SpeedTest` class, passing in as parameters the function expression, the list of member lists, and optionally the number of repetitions to execute the code. If you don't specify the number of repetitions, it defaults to 10,000.

```js
var speedTest = new SpeedTest(addMembers, listsForTests);
```
-or-
```js
var speedTest = new SpeedTest(addMembers, listsForTests, 100000);
```

Finally call the startTest method of the `SpeedTest` class instance:

```js
speedTest.startTest();
```

Your finished  code would look like this:

```js
var membersNew = ["Cristen Banton", "Kirsten Thiede", "Cyril Punch", "Layne Perillo", "Faviola Leaver"],
    membersCurrent = ["Regan Padillo", "Jay Shuford", "Ferne Amey", "Garrett Hem", "Delila Embrey"],
    listsForTests = [membersNew, membersCurrent];

var addMembers = function(listOfParams) {
  for (var i = 0; i < listOfParams[0].length; i++) {
    listOfParams[1].push(new Member(listOfParams[0][i], 1));
  }
};

var speedTest = new SpeedTest(addMembers, listsForTests, 100000);
speedTest.startTest();
```

The result would be logged to the console as such:
```console
> Average execution across 100000: .0043ms
```

### License

[BSD license](http://opensource.org/licenses/bsd-license.php)
