### Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target. You may assume that each input would have exactly one solution, and you may not use the same element twice.
```
var twoSum = function(nums, target) {
  const hashMap = new Map()

  for (let i = 0; i < nums.length; i ++) {
    const temp = target - nums[i]

    if (hashMap.has(temp)) {
      return [hashMap.get(temp), i]
    }
    hashMap.set(nums[i], i)
  }
};
```
### Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid
```
var isValid = function(s) {
const stack = [];

  const bracketsMap = {
    '(': ')',
    '{': '}',
    '[': ']',
  };

  for (let i = 0; i < s.length; i++) {
    const char = s[i];

    if (bracketsMap.hasOwnProperty(char)) {
      stack.push(char);
    } else {
      if (stack.length === 0 || bracketsMap[stack.pop()] !== char) {
        return false;
      }
    }
  }
  return stack.length === 0;
  }
}
```
```
function isValid(str) {
  const stack = [];

  for (let i = 0; i < str.length; i++) {
    const char = str[i];

    if (char === '(' || char === '{' || char === '[') {
      stack.push(char);
    } else if (char === ')' || char === '}' || char === ']') {
      if (stack.length === 0) {
        return false; 
      }

      const top = stack.pop();
      if (
        (char === ')' && top !== '(') ||
        (char === '}' && top !== '{') ||
        (char === ']' && top !== '[')
      ) {
        return false; 
      }
    }
  }

  return stack.length === 0; 
}
```
### Given an integer x, return true if x is a palindrome, and false otherwise.
```
var isPalindrome = function(x) {
    if(x < 0 || (x !== 0 && x % 10 === 0)) return false

    let reversed = 0
    let original = x

    while (original > 0) {
        const digit = original % 10
        reversed = reversed * 10 + digit
        original = Math.floor(original / 10)
    }

    if (x === reversed) return true
    else return false
};
```
### Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct
```
var containsDuplicate = function(nums) {
    const hashMap = new Map()

    for (let i = 0; i < nums.length; i++) {
        if (hashMap.has(nums[i])) {
            return true
        }
        hashMap.set(nums[i], i)
    }

    return false
};
```
### You are given an integer array nums. Let product be the product of all values in the array nums. Return signFunc(product).
```
var arraySign = function(nums) {
    let product = nums[0]

    for (let i = 1; i < nums.length; i++) {
        product = product * nums[i]    
    }

    const sign = Math.sign(product)

    return sign
};
```
