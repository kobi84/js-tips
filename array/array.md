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

## 3. Update value (primitive) in array

To update specific value we can use findIndex() method.

```javascript
const oldValue = 'James',
  newValue = 'Arthur',
  names = [
    'Alice',
    'Tom',
    'Mark',
    'Joan',
    'Luke',
    'James',
    'Eve'
  ];

const index = names.findIndex(item => item === oldValue);

  names[index] = newValue;
```

## 4. Update object in array

To update specific object in array we can use map() method.

```javascript
const updated = { id: 4, name: 'Gandalf', lastName: 'The White' },
  array = [
    { id: 1, name: 'Tom', lastName: 'Bombadil' },
    { id: 2, name: 'Frodo', lastName: 'Baggins' },
    { id: 3, name: 'Bilbo', lastName: 'Baggins' },
    { id: 4, name: 'Gandalf', lastName: 'The Grey' }
  ];

const updatedArray = array.map(item => item.id === updated.id ? updated : item);
```

## 5. Using array for condition checking

We can use array include() method in condition checking.

```javascript
const input = 'cat',
  animals = ['dog', 'cat', 'bird', 'fish', 'spider'];

  if(animals.includes(input)) {
    console.log('Animal');
  } else {
    console.log('Other');
  }
```
