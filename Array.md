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
### You are given an array prices where prices[i] is the price of a given stock on the ith day. You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock. Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
```
var maxProfit = function(prices) {
    let minPrice = Infinity
    let maxProfit = 0

    for (let i = 0; i < prices.length; i++) {
        if (prices[i] < minPrice) {
            minPrice = prices[i]
        } else if (prices[i] - minPrice > maxProfit) {
            maxProfit = prices[i] - minPrice
        }
    }

    return maxProfit
};
```
### You are given an array of unique integers salary where salary[i] is the salary of the ith employee. Return the average salary of employees excluding the minimum and maximum salary. Answers within 10-5 of the actual answer will be accepted.
```
var average = function(salary) {
    salary.sort((a,b) => a - b)

    let sum = 0

    for (let i = 1; i < salary.length - 1; i++) {
        sum += salary[i]
    }

    const avg = sum / (salary.length - 2)

    return avg
};
```
### Given two strings s and t, return true if t is an anagram of s, and false otherwise. An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
```
var isAnagram = function(s, t) {
    const sortedS = s.split('').sort().join('');
    const sortedT = t.split('').sort().join('');

    if (sortedS === sortedT) return true
    else return false
};
```
### Given an integer num, repeatedly add all its digits until the result has only one digit, and return it
```
var addDigits = function(num) {
    while(num >= 10) {
        let sum = 0
        while (num > 0) {
            sum += num % 10
            num = Math.floor(num / 10)
        }
        num = sum
    }
    return num
};
```
```
var addDigits = function(num) {
  if (num === 0) {
    return 0;
  } else {
    return 1 + (num - 1) % 9;
  }
};
```
### Given a square matrix mat, return the sum of the matrix diagonals. Only include the sum of all the elements on the primary diagonal and all the elements on the secondary diagonal that are not part of the primary diagonal
```
var diagonalSum = function(mat) {
    let sum = 0
    let n = mat.length

    for (let i = 0; i < n; i++) {
      sum += mat[i][i]

      if (i !== n - 1 - i) {
        sum += mat[i][n - 1 - i]
      }
    }

    return sum
};
```
