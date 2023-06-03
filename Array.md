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
