# uplab
Радиф Сиразетдинов
____
# Задание 1
This code does not execute properly. Try to figure out why.(Multiply)
# Код
```html
function multiply(a, b){
  return a * b
}
```
____
# Задание 2
Your task is to write a function which returns the sum of following series upto nth term(parameter).
```html
function SeriesSum(n) {
  let result = 0;
  let reverage = 1;
  for (let i = 0; i < n; i += 1) {
    if (i === 0) {
      result = 1;
    } else {
      reverage += 3;
      result = result + (1 / reverage);
    }
  }
  return result.toFixed(2);
};
```
____
# Задание 3
You will be given a number and you will need to return it as a string in Expanded Form.
```html
function expandedForm(num) {
      // Your code here
      let numStr = num.toString().split('');
      
      for(let i = 0 ; i < numStr.length; i++ ){
          
          for(let y = numStr.length - i; y > 1; y--){
             numStr[i] += '0'; 
             // console.log(y);  use this to debug y, and no y value print out from console
          }
      }
      
     
      numStr = numStr.filter(value => !value.startsWith(0));
      return numStr.join(' + ')
    }

    console.log(expandedForm(23));
```
____
# Задание 4
The new "Avengers" movie has just been released! There are a lot of people at the cinema box office standing in a huge line. Each of them has a single 100, 50 or 25 dollar bill. An "Avengers" ticket costs 25 dollars.

Vasya is currently working as a clerk. He wants to sell a ticket to every single person in this line.

Can Vasya sell a ticket to every person and give change if he initially has no money and sells the tickets strictly in the order people queue?

Return YES, if Vasya can sell a ticket to every person and give change with the bills he has at hand at that moment. Otherwise return NO.
```html
function tickets(peopleInLine){
  
  changeNotes = 
    {
      '25' : 0,
      '50' : 0,
      '100' : 0,
    };
  
  for (i=0; i < peopleInLine.length; i++)
  {
    if(peopleInLine[i] === 25)
    {
      changeNotes['25'] += 1;
    }
    else if(peopleInLine[i] === 50)
    {
      if(changeNotes['25'] > 0)
      {
        changeNotes['50'] += 1;
        changeNotes['25'] -= 1;
      }
      else
      {
        return 'NO';
      }
    }
    else
    {
      if(changeNotes['50'] > 0 && changeNotes['25'] > 0)
      {
        changeNotes['50'] -= 1;
        changeNotes['25'] -= 1;
        changeNotes['100'] += 1;
      }
      else if(changeNotes['25'] >= 3)
      {
        changeNotes['25'] -= 3;
        changeNotes['100'] += 1;
      }
      else
      {
        return 'NO';
      }
    }
  }
  return 'YES';
}
```
____
# Задание 5
ATM machines allow 4 or 6 digit PIN codes and PIN codes cannot contain anything but exactly 4 digits or exactly 6 digits.

If the function is passed a valid PIN string, return true, else return false.
```html
function validatePIN (pin) {
    return /^(\d{4}|\d{6})$/.test(pin);
}

console.log(validatePIN('1234')); // > true
console.log(validatePIN('123456')); // > true
console.log(validatePIN('123')); // > false
console.log(validatePIN('12345')); // > false
```
____
# Задание 6
For building the encrypted string:
Take every 2nd char from the string, then the other chars, that are not every 2nd char, and concat them as new String.
Do this n times!
```html
function encrypt(text, n) {
  
 if(text === null || text === '' || n <= 0 ){
   return text
 }
   
  n--;
  
    let split = text.split('')
  
    let first = []
    let second = []
  
  for(let i = 0; i < split.length; i ++){
    if(i % 2 !== 0){
      first.push(split[i]);
    }else if(i % 2 === 0){ 
      second.push(split[i]);
    }
  } 
  
  let encrypted = first.concat(second).join('')

  if(!n == 1){
    return encrypted;
  }else {
    return encrypt(encrypted, n)
  }
}


function decrypt(encryptedText, n) {
     if(encryptedText === null || encryptedText === '' || n <= 0 ){
   return encryptedText
 }
   
   n--;
   
    let length = []
    let result = []

   let split = encryptedText.split('')
   
   for(let i = 1; i <= encryptedText.length; i++){
     
     if(i % 2 === 0 ){
       length.push(i)
     }
   }
   
   let odds = split.slice(length.length)
   let evens = split.slice(0, length.length)
   console.log(odds)
   console.log(evens)
   
   for(let i = 0; i < odds.length; i++){
     result.push(odds[i] , evens[i])
   }
   
    if(!n == 1){
    return result.join('')
  }else {
    return decrypt(result.join(''), n)
    }
 }
```
____
# Задание 7
There is an array with some numbers. All numbers are equal except for one. Try to find it!
```html
function stray(numbers) {
let strayChar = numbers[0];

 for(let i = 1; i < numbers.length; i++){
  if(strayChar !== numbers[i]){
  return strayChar = numbers[i];
   }
 }
       return 0;
 } 
```
____
# Задание 8
Some numbers have funny properties. For example:

89 --> 8¹ + 9² = 89 * 1

695 --> 6² + 9³ + 5⁴= 1390 = 695 * 2

46288 --> 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51

Given a positive integer n written as abcd... (a, b, c, d... being digits) and a positive integer p

we want to find a positive integer k, if it exists, such as the sum of the digits of n taken to the successive powers of p is equal to k * n.
In other words:

Is there an integer k such as : (a ^ p + b ^ (p+1) + c ^(p+2) + d ^ (p+3) + ...) = n * k

If it is the case we will return k, if not return -1.

Note: n and p will always be given as strictly positive integers.
```html
function digPow(n, p){
  let string = n.toString();
  let len = string.length;
  let result = 0;
  for(var i = 0; i < len ; i++) {
    var numberser = parseInt(string.charAt(i),10);
    result +=  Math.pow(numberser, p + i)
  }
  var x = Math.pow(n,p);
  if(result === x){
    return p;
    } else if(result%n === 0) {
    return result / n;
  }else {
    return -1  
  }
}
```
____
# Задание 9
Given a string of words, you need to find the highest scoring word.
Each letter of a word scores points according to its position in the alphabet: a = 1, b = 2, c = 3 etc.
You need to return the highest scoring word as a string.
If two words score the same, return the word that appears earliest in the original string.
All letters will be lowercase and all inputs will be valid.
```html
function high(x) {
  const words = x.split(' ');
  const alphabetMap = {};
  for (let i='a'.charCodeAt(), j = 1; i <= 'z'.charCodeAt(); i++, j++) {
    alphabetMap[i] = j;
  }
  let highestScoringWord = { word: '', score: 0 };
  words.forEach(w => {
    const chars = w.split('');
    const sumOfChars = chars.reduce((count, char) => count + alphabetMap[char.charCodeAt()], 0);
    if (sumOfChars > highestScoringWord.score) {
      highestScoringWord = { word: w, score: sumOfChars };
    }
  });

  return highestScoringWord.word;
}

console.log(high('what time are we climbing up the volcano')) // volcano ;)
```
____
# Задание 10
Move the first letter of each word to the end of it, then add "ay" to the end of the word. Leave punctuation marks untouched.
```html
function pigIt(str){
  let strArr = str.split(' ');
  let pigLatin = [];

  for(let word of strArr){
    if((/([a-zA-Z])/).test(word)){
      pigLatin.push(word.substring(1) + word[0] + "ay");
    }else{
      pigLatin.push(word);
    }
  }
  return pigLatin.join(" ");
}
```
