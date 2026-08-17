# Exercise - Reduce

**TIP:**  
You can use the online JavaScript compiler linked below and complete the following tasks.  
<https://www.programiz.com/javascript/online-compiler>

**Task Description -** Copy each code block listed below, paste it into the compiler, and replace `// your code here` with the actual solution. Then, compare your output with the expected results provided.

### **1) Turn an array of numbers into a total of all the numbers**

code

```
function total(arr) {
   // your code here
}

console.log(total([1,2,3]));
```

**Expected Output:**

code

```
6
```

### **2) Turn an array of numbers into a long string of all those numbers.**

code

```
function stringConcat(arr) {
   // your code here 
}

console.log(stringConcat([1,2,3]));
```

**Expected Output:**

code

```
"123"
```

### **3) Turn an array of voter objects into a count of how many people voted**

code

```
function totalVotes(arr) {
   // your code here    
}

var voters = [
    {name:'Bob' , age: 30, voted: true},
    {name:'Jake' , age: 32, voted: true},
    {name:'Kate' , age: 25, voted: false},
    {name:'Sam' , age: 20, voted: false},
    {name:'Phil' , age: 21, voted: true},
    {name:'Ed' , age:55, voted:true},
    {name:'Tami' , age: 54, voted:true},
    {name: 'Mary', age: 31, voted: false},
    {name: 'Becky', age: 43, voted: false},
    {name: 'Joey', age: 41, voted: true},
    {name: 'Jeff', age: 30, voted: true},
    {name: 'Zack', age: 19, voted: false}
];
console.log(totalVotes(voters));
```

**Expected Output:**

code

```
7
```

### **4) Given an array of all your wishlist items, figure out how much it would cost to just buy everything at once**

code

```
function shoppingSpree(arr) {
   // your code here    
}

var wishlist = [
    { title: "Tesla Model S", price: 90000 },
    { title: "4 carat diamond ring", price: 45000 },
    { title: "Fancy hacky Sack", price: 5 },
    { title: "Gold fidgit spinner", price: 2000 },
    { title: "A second Tesla Model S", price: 90000 }
];

console.log(shoppingSpree(wishlist));
```

**Expected Output:**

code

```
227005
```
