# __Hashtabels__

## What is a Hashtable?

<br>

__Hash__ - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.

<br>

__Buckets__ - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.

<br>

__Collisions__ - A collision is what happens when more than one key gets hashed to the same location of the hashtable.

---

<br>

## We use them for?

1. Hold unique values
2. Dictionary
3. Library

---

## What Are they

Hashtables are a data structure that utilize key value pairs. This means every Node or Bucket has both a key, and a value.

The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value. This is done through what we call a hash. A hash is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.

Since we are able to hash our key and determine the exact location where our value is stored, we can do a lookup in an O(1) time complexity. This is ideal when quick lookups are required.

---

<br>

## Structure

### Hashing

Basically, a hash code turns a key into an integer. It’s very important that hash codes are deterministic: their output is determined only by their input. Hash codes should never have randomness to them. The same key should always produce the same hash code.

<br>

### Creating a Hash

A hashtable traditionally is created from an array. I always like the size 1024. this is important for index placement. After you have created your array of the appropriate size, do some sort of logic to turn that “key” into a numeric number value. Here is a simplistic hashing algorithm:

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.

Example:

    Key = "Cat"
    Value = "Josie"

    67 + 97 + 116 = 280

    280 * 599 = 69648

    69648 % 1024 = 16

    Key gets placed in index of 16. 

We now know that our key Cat maps to index 16 of the array. We can view into this index and find “Josie”, our value quickly.

NOTE: Production systems will have much more robust hashing algorithms that ensure even distribution of values across all buckets and avoid unnecessary collisions.

Let’s dive a bit deeper into HOW the key/values are stored in the array.

Each index of the array can hold many types of values. The trick is how the values are stored in comparison to efficiency. Each Index of the array contain “buckets”. Each of these “buckets” holds one key/value pair combination. When there is no entry in a specific bucket, the buckets (each index of the array) all start null. The hash table starts each bucket empty and overwrites their value once a key generates a hashCode that corresponds with an index.