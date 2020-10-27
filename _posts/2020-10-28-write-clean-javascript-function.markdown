---
layout: post
title:  "Write Clean Javascript Function"
date:   2020-10-28 00:15:00 +0700
categories: javascript
---
- Always write declarative function as long as you can.

```
# Good
# It's easier to read
function sum(x,y) {
    return x + y
}

# Bad
# Function expression is just non sense.
const sum = function(x,y) {
    return x + y
}

# Bad
# Arrow function is cool but we can't trade readability off 
# shorter line of code.
const sum = (x,y) => x + y
```

- Function must be the first class citizen, avoid declaring function inside a function. Not only it's not nercessary but also hard to do unit test.

```
# Good
function sum(a,b) {
    return a + b
}

function average(a,b) {
    return sum(a,b) / 2
}

# Bad
function average(a,b) {
    function sum(a,b) {
        return a + b
    }

    return sum(a,b) / 2
}
```

- Avoid declarative function in callback argument.

```
# Great
[1,2,3,4].map((v) => {
    console.log(v)
})

# Good
[1,2,3,4].map(function(v) {
    console.log(v)
})

# Bad
function print(v) {
    console.log(v)
}

[1,2,3,4].map(print)
```