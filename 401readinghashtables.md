# Hashtables

## What is a Hashtable?

[Reading](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html)

* Hash - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.

* Buckets - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.

* Collisions - A collision is what happens when more than one key gets hashed to the same location of the hashtable.

Hash maps take advantage of an array’s O(1) read access. Instead of adding elements to an array from beginning to end, a hash map uses a “hash function” to place each item at a precise index location, based off it’s key.

Basically, the hash function takes a key and returns an integer. We use the integer to determine where the key/value pair should be placed in the array. The hash code is calculated in constant time and writing to an array at one index is O(1) so the hash map has O(1) access.

The hash code is used again to read something from the hash map. Take the key, run it through the hash code to get a number, use that number to index the array. Calculating the hash code and reading an array at that index is all constant time to the hash map has O(1) read access!

Hashing
Basically, a hash code turns a key into an integer. It’s very important that hash codes are deterministic: their output is determined only by their input. Hash codes should never have randomness to them. The same key should always produce the same hash code.

Creating a Hash
A hashtable traditionally is created from an array. I always like the size 1024. this is important for index placement. After you have created your array of the appropriate size, do some sort of logic to turn that “key” into a numeric number value. Here is a possible suggestion:

Add or multiply all the ASCII values together.
Multiply it by a prime number such as 599.
Use modulo to get the remainder of the result, when divided by the total size of the array.
Insert into the array at that index.

Example from reading:
```
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16

Key gets placed in index of 16. 
```

We now know that our key Cat maps to index 16 of the array. We can view into this index and find “Josie”, our value quickly.

Let’s dive a bit deeper into HOW the key/values are stored in the array.

Each index of the array can hold many types of values. The trick is how the values are stored in comparison to efficiency. Each Index of the array contain “buckets”. Each of these “buckets” holds one key/value pair combination. When there is no entry in a specific bucket, the buckets (each index of the array) all start null. The hash table starts each bucket empty and overwrites their value once a key generates a hashCode that corresponds with an index.

Since different keys can lead to the same bucket it’s important to store the entire key/value pair in the bucket, not just the value. The key must be stored with the value! If only values were stored in buckets then it would be impossible to determine which value to return when a key led you to a bucket.

Example:
```
hashMap.Add("Pioneer Square", 98104);
hashMap.Add("Alki Beach", 98116);

-> Bucket 92: [{Pioneer Square: 98104} --> {Alki Beach: 98116}]
```

If we didn’t store the key, the bucket would look like this. Accessing `.get("Pioneer Square")` or `.get("Alki Beach")` would hash the keys and still lead to bucket 92, but it would be impossible to tell which of the zip code values there to return.

`Bucket 92: [{98104} --> {98116}]`

Hash maps do this to store values:

* accept a key
* calculate the hash of the key
* use modulus to convert the hash into an array index
* store the key with the value by appending both to the end of a linked list

Hash maps do this to read value:

* accept a key
* calculate the hash of the key
* use modulus to convert the hash into an array index
* use the array index to access the short LinkedList representing a bucket
* search through the bucket looking for a node with a key/value pair that matches the key you were given

### Internal Methods

`Add()`
When adding a new key/value pair to a hashtable:

1. send the key to the GetHash method.
2. Once you determine the index of where it should be placed, go to that index
3. Check if something exists at that index already, if it doesn’t, add it with the key/value pair.
4. If something does exist, add the new key/value pair to the data structure within that bucket.

`Find()`
The `Find` takes in a key, gets the Hash, and goes to the index location specified. Once at the index location is found in the array, it is then the responsibility of the algorithm the iterate through the bucket and see if the key exists and return the value.

`Contains()`
The `Contains` method will accept a key, and return a bool on if that key exists inside the hashtable. The best way to do this is to have the contains call the `GetHash` and check the hashtable if the key exists in the table given the index returned.

`GetHash()`
The `GetHash` will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.

### Collisions

Collisions are solved by changing the initial state of the buckets. Instead of starting them all as null we can initialize a LinkedList in each one! Now if two keys resolve to the same index in the array then their key/value pairs can be stored as a node in a linked list. Each index in the array is called a “bucket” because it can store multiple key/value pairs.



## What is a hashtable?

[Video](https://www.youtube.com/watch?v=MfhjkfocRR0)

Data structure used for storing information. Has two key components. A key and a value. The example used in the video was a key of his name and a value of his phone number. The core of the hashtable is an array like structure. He makes a hash function that takes in a key and then outputs an index number. Every time you input the same key you should get the same index. In order to avoid collision he does chaining by making a linked list off of the index value.

## Basics of Hash Tables

[Reading](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)


[Back](README.md)