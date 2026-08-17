# Exercise - Filter

**TIP:**  
You can use the online JavaScript compiler linked below and complete the following tasks.  
<https://www.programiz.com/javascript/online-compiler>

**Task Description -** Copy each code block listed below, paste it into the compiler, and replace `// your code here` with the actual solution. Then, compare your output with the expected results provided.

### **1) Given an array of numbers, return a new array that has only the numbers that are 5 or greater**

code

```
function fiveAndGreaterOnly(arr) {
  // your code here
}
// test
console.log(fiveAndGreaterOnly([3, 6, 8, 2]));
```

**Expected Output:**

code

```
[6, 8]
```

### **2) Given an array of numbers, return a new array that only includes the even numbers**

code

```
function evensOnly(arr) {
  // your code here
}
// test
console.log(evensOnly([3, 6, 8, 2]));
```

**Expected Output:**

code

```
[6, 8, 2]
```

### **3) Given an array of strings, return a new array that only includes those that are 5 characters or fewer in length**

code

```
function fiveCharactersOrFewerOnly(arr) {
  // your code here
}
// test
console.log(fiveCharactersOrFewerOnly(["dog", "wolf", "by", "family", "eaten", "camping"]));
```

**Expected Output:**

code

```
["by", "dog", "wolf", "eaten"]
```

### **4) Given an array of people objects, return a new array that has filtered out all those who don't belong to the club.**

code

```
function peopleWhoBelongToTheIlluminati(arr){
  // your code here
}
// test
console.log(peopleWhoBelongToTheIlluminati([
    { name: "Angelina Jolie", member: true },
    { name: "Eric Jones", member: false },
    { name: "Paris Hilton", member: true },
    { name: "Kayne West", member: false },
    { name: "Bob Ziroll", member: true }
]));
```

**Expected Output:**

code

```
[{ name: 'Angelina Jolie', member: true },
{ name: 'Paris Hilton', member: true },
{ name: 'Bob Ziroll', member: true }]
```
