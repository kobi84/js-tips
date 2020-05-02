# Object tips

## 1. Detect changes in JavaScript objects

We can use JavaScript Proxy to detect changes in object.

```javascript
const handler = {
  get: (obj, prop) => {
    console.log(
      `Gettting value '${obj[prop]}' from ${obj} by property '${prop}'`
    );
    return obj[prop];
  },
  set: (obj, prop, value) => {
    console.log(
      `Setting value '${value}' in ${obj} object for property '${prop}'`
    );
    obj[prop] = value;
  }
};

var p = new Proxy({}, handler);

p.name = 'test';
console.log(p.name);
```
