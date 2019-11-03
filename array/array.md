# Array tips

## 1. Filter unique values from array

This will work only with primitives.

```javascript
const arrayWithDuplicates = [1, 5, 3, 1, 5, 6, 8, 2, 1, 3, 1],
  uniqueValues = [...new Set(arrayWithDuplicates)],
  uniqueValues2 = Array.from(new Set(arrayWithDuplicates));
```

## 2. Filter unique values from array of objects

As Set works only with primitives we have to modify above example.
We are converting our array to primitives using map (arrays with ids).
After this we can map arrays of ids to array of object by using find method.

```javascript
const arrayWithDuplicates = [
  { id: 1, name: 'Tom', lastName: 'Bombadil' },
  { id: 2, name: 'Frodo', lastName: 'Baggins' },
  { id: 3, name: 'Bilbo', lastName: 'Baggins' },
  { id: 4, name: 'Gandalf', lastName: 'The Grey' },
  { id: 1, name: 'Tom', lastName: 'Bombadil' },
  { id: 1, name: 'Tom', lastName: 'Bombadil' },
  { id: 2, name: 'Frodo', lastName: 'Baggins' },
  { id: 1, name: 'Tom', lastName: 'Bombadil' },
  { id: 4, name: 'Gandalf', lastName: 'The Grey' },
  { id: 1, name: 'Tom', lastName: 'Bombadil' },
  { id: 3, name: 'Bilbo', lastName: 'Baggins' }
];

const uniqueArray = Array.from(
  new Set(arrayWithDuplicates.map(item => item.id))
).map(id => arrayWithDuplicates.find(item => item.id === id));
```

Or without iterating twice by array.

```javascript
const arrayWithDuplicates = [
    { id: 1, name: 'Tom', lastName: 'Bombadil' },
    { id: 2, name: 'Frodo', lastName: 'Baggins' },
    { id: 3, name: 'Bilbo', lastName: 'Baggins' },
    { id: 4, name: 'Gandalf', lastName: 'The Grey' },
    { id: 1, name: 'Tom', lastName: 'Bombadil' },
    { id: 1, name: 'Tom', lastName: 'Bombadil' },
    { id: 2, name: 'Frodo', lastName: 'Baggins' },
    { id: 1, name: 'Tom', lastName: 'Bombadil' },
    { id: 4, name: 'Gandalf', lastName: 'The Grey' },
    { id: 1, name: 'Tom', lastName: 'Bombadil' },
    { id: 3, name: 'Bilbo', lastName: 'Baggins' }
  ],
  ids = new Set();

const uniqueArray = arrayWithDuplicates.filter(item => {
  const isAdded = ids.has(item.id);
  ids.add(item.id);
  return !isAdded;
});
```
