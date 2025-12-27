# Client-Side Storage

While we have discussed and worked with server-side persistent storage, we will now explore the capabilities of client-side storage through **local storage** and **IndexedDB**.

## Local Storage

One of the most easy storage systems to use within javascript is `localStorage` or `sessionStorage`.

This storage mechanism is fairly simple as you are able to treat it as a `Map` where the key and value are both strings. This does require serialising the data when saving it.

### Set Item

To access local storage, we are able to access it through the `window` object and refer to it as `localStorage`.

We will look at the following example and examine what has occurred.

```js
const obj = { id: 10, name: "Jeff" };

const serialised = JSON.stringify(obj);

localStorage.setItem("user", serialised);
```

The above snippet takes a javascript object and translates it into a string. This makes it suitable to be saved and we are able to set the value and later retrieve it using the same key.

### Get Item

Retrieving an item from local storage is a matter of knowing the key and also checking if the key maps to a value.

You should be defensive and ensure to check if the value is not `undefined` or `null`.

```js
const serialisedObj = localStorage.getItem('user');
if(serialisedObj) {
  const obj = JSON.parse(serialisedObj);

  console.log(`${obj.id}: ${obj.name}`);
} else {
  console.log("unable to retrieve item");
} 
```

Since the data is serialised, we will need to deserialise it and turn it back to a JSON object.

### Removing an Item

We may want to clear the data from local storage. Assuming you have access to the key, you are able to call `removeItem` on local storage.

```js
localStorage.remoteItem('user');
```

This is useful if need to reset tokens or if a user logs off your platform.


## IndexedDB

IndexedDB is a more significant database system for the browser. It is akin to a NoSQL database system and also similar to `localStorage` where it contains keys and values.

### Constructing a database

You are able to call `open` using `indexedDB` and name the database what you believe suitable.

```js
// Name of DB and version, 1 is the version number by default
const request = indexedDB.open("userdb", 1);
  
```

This is a request however, since the browser may deny access to the program to use it. You will need to also ensure that the version you are accessing is the highest as well.

The version change itself is useful to perform as it may be a reason to consider the previous DB data to be stale.

### Events to handle

You will need to handle the folowing events with indexedDB.

```js
let databaseRef = null;

request.onerror = function(event) {
  console.error("Unable to open the database");
};

request.onsuccess = function(event) {

  databaseRef = event.target.result;
  
  databaseRef.onerror = function(event) {
    const error = event.target.error;
    console.error(`DB Error: ${error ? error.message : "Unknown Erorr"}`);
  };
};
```

If the request is successful, we need to provide a way to update a reference to the database. The above snippet will update `databaseRef` which is a global variable in this case.

### Storing Data

The database mechnaism is able to create **collections** which are known as **Object Stores** and **create an index** for them.

```js
const userStore = databaseRef.createObjectStore(
  "users",
  { keyPath: "userno" });

userStore.createIndex("email", "email",
  { unique: true });

let storeRequest = userStore.add({ userno: '1122', email: 'jeff@jeff.co', name: "Jeffrey" });


storeRequest.onsuccess = function(event) {
  // Will trigger when the data is added
}

```

The above snippet is doing a lot of work. However, we are adding objects to our database using `storeRequest`. This will be returned from add and we are able to build a response into the transaction.

#### Why are indexes important?

Indexes are a way to create unique information that can be search efficiently. Referring to the data structures chapter, you may observe the difference in time/performance between binary search and linear search. Indexing will achieve a similar effect, however there is a difference between indexing field which are unique and not.


### Retrieving elements from a database

Retrieving data from indexedDB is varied, as outlined, indexes play an important role. `.get` will allow someone to query a store and use it.

You are able to use the following.

* `get`
* `getAll`
* `getKey`
* `getAllKeys`

The above methods are ordered by their granularity with their search. You are able to tailor the retrieval here.

```js
const result = userStore.get("1122"); //Looks for it using the key
```

You are able to to use `IDBKeyRange` that allows you to bound the search as well.

```js
const result1 = userStore
  .get(IDBKeyRange.only('1122'));

// Gets more interesting with ranges
// Gets users between 1122 and 2244 inclusive
const result2 = userStore
  .get(IDBKeyRange.bound("1122", "2244"));
```

It is recommended you explore this further after working with the initial set up and basic transactions as there is a whole topic on databases that will need to be explored further here.

## Other Methods

You can use another kind of storage mechanism called **OPFS**. This mechanism is more like a filesystem and will require you to use the File API that is accessible as part of the browser API.
