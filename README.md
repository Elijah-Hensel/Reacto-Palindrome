# Palindrome Check


## Learning Objective
* Analyze and compare recursive and iterative approaches


## Interviewer Prompt
Given an string `str`, create a function that returns a boolean, corresponding to whether that string is a palindrome (spelled the same backwards and forwards). Our palindrome check should be case-insensitive. 

## Examples

```js
isPal('car') => false
isPal('racecar') => true
isPal('RaCecAr') => true
isPal('!? 100 ABCcba 001 ?!') => true
```


## Iterative Solution 

### Approach

Implement a `while` loop that continues running if the string has a length >1. Slice off the first and last chars of the string and ensure they match. If they do not, break out of the loop and return false. If we are able to whittle the string down to 0 or 1 characters, return true

### Code

```js
function isPalIterative(str){
  while(str.length > 1){
    let first = str[0].toLowerCase();
    let last = str[str.length - 1].toLowerCase();
    if(first != last) return false
    str = str.slice(1, str.length - 1);
  }
  return true
}

/* For loop using pointers to avoid String.prototype.slice */
function isPalIterative2(str) {
  for (let i = 0; i < Math.floor(str.length / 2); i++) {
    let left = str[i].toLowerCase()
    let right = str[str.length - 1 - i].toLowerCase()
    if (left != right) return false
  } 
  return true
}
```

### Performance analysis

### Time Complexity: __O(n)__

* We must loop through the string n/2 times in order to return false.

### Space Complexity: __O(1)__

- We create a constant number of new variables (first and last) to solve the problem

## Recursive Solution 

### Approach

Check the length of the string. If it is <= 1 characters, return true. If not, check if the first and last characters of the string match. If they do not, return false. If they match, slice them off the string and recurse. 

### Code

```js
function isPalRecursive(str){
  if(str.length <= 1) {
    return true
  } else if (str[0].toLowerCase() !== str[str.length -1 ].toLowerCase()) {
    return false
  } else {
    str = str.slice(1, str.length - 1);
    return isPalRecursive(str)
  }
}
```

### Performance analysis

### Time Complexity: __O(n)__

* We must recurse through the string n/2 times in order to return false.

### Space Complexity: __O(n)__

- We create n/2 additional calls on the recursive call stack, each time we slice of the first/last characters and recurse. 


## Resources
_Feel free to PR any useful resources! :)_

* [Sample Slides](https://docs.google.com/presentation/d/1y3vNaW3uR1U96W_JdZtMA9vJvpccGtaHUF-yWwnS1EA/edit?usp=sharing)
* [Leetcode Link](https://leetcode.com/problems/valid-palindrome/)
