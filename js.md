# Javascripts

* `let` , `const` and `var` 

| Keyword | Scope           | Reassignment | Hoisting |
| ------- | --------------- | ------------ | -------- |
| `const` | Block           | No           | No       |
| `let`   | Block           | Yes          | No       |
| `var`   | Function/Global | Yes          | No       |

* promise

```javascript

```

* Self-definition function for prototype.

```javascript
// example 
Array.prototype.last = function() {
    if (this.length == 0) {
        return -1;
    }
    return this[this.length - 1];
};
```

* The reduce function of prototype Array;