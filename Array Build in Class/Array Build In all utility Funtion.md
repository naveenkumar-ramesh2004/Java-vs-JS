✅ 1. Arrays.copyOf()

Belongs to the java.util.Arrays class.

Creates a new array.

Lets you resize arrays (increase or decrease length).

Simpler and more readable.

Example:

int[] arr = {1, 2, 3, 4, 5};
int[] copy = Arrays.copyOf(arr, 3);  

System.out.println(Arrays.toString(copy));  
// [1, 2, 3]


Here it creates a new array of size 3.

✅ 2. System.arraycopy()

Belongs to the System class.

Copies elements from one array into another existing array.

Faster (since it’s a native method).

Requires more arguments → source array, starting index, destination array, destination index, and length.

Example:

int[] arr = {1, 2, 3, 4, 5};
int[] copy = new int[3];  

System.arraycopy(arr, 0, copy, 0, 3);

System.out.println(Arrays.toString(copy));  
// [1, 2, 3]


🔑 Key Differences

Feature	Arrays.copyOf()	System.arraycopy()
Returns	New array	Copies into an already existing array
Resizing allowed?	✅ Yes	❌ No (destination must be big enough)
Ease of use	Simple	More complex (need multiple parameters)
Performance	Slower (wrapper, creates new array)	Faster (low-level native method)

👉 Use Arrays.copyOf() when you want a new resized array.
👉 Use System.arraycopy() when you already have a destination array and want high performance copy.

✅ 3. This type of any class available in JS

Good question 🚀

In Java, we have helper classes like Arrays that give us methods (copyOf, sort, asList, etc.).
But in JavaScript, arrays are objects with many built-in methods — no separate class like Arrays.

🔹 Examples of JS array methods (similar to Java’s Arrays class):

Copy part of an array (like Arrays.copyOf)

let arr = [1, 2, 3, 4, 5];

// Copy first 3 elements
let copy = arr.slice(0, 3);

console.log(copy); // [1, 2, 3]


👉 slice(start, end) in JS ≈ Arrays.copyOf(arr, length) in Java.

Clone whole array

let arr = [1, 2, 3];
let copy = arr.slice();   // OR [...arr]

console.log(copy); // [1, 2, 3]


Concatenate / Merge

let arr1 = [1, 2];
let arr2 = [3, 4];

let merged = arr1.concat(arr2);

console.log(merged); // [1, 2, 3, 4]


Sort array

let arr = [5, 1, 3, 2];
arr.sort();

console.log(arr); // [1, 2, 3, 5]


Reverse array

let arr = [1, 2, 3];
arr.reverse();

console.log(arr); // [3, 2, 1]


⚡ So in JavaScript, you don’t need a separate Arrays class — arrays themselves already have methods.
If you want utility functions, JS has libraries like Lodash or underscore.js (like Java’s Arrays helper).

✅ 4. Java vs JavaScript Array Methods Table

Java (Arrays class)	JavaScript (Array methods)	Example (Java)	Example (JavaScript)
Arrays.copyOf(arr, n)	arr.slice(0, n)	int[] b = Arrays.copyOf(a, 3);	let b = a.slice(0, 3);
Arrays.copyOfRange(arr, i, j)	arr.slice(i, j)	int[] b = Arrays.copyOfRange(a, 1, 4);	let b = a.slice(1, 4);
Arrays.sort(arr)	arr.sort() (lexical) or arr.sort((a,b)=>a-b) (numeric)	Arrays.sort(a);	arr.sort((a,b)=>a-b);
Arrays.toString(arr)	arr.toString() or JSON.stringify(arr)	System.out.println(Arrays.toString(a));	console.log(arr.toString());
Arrays.equals(a, b)	JSON.stringify(a) === JSON.stringify(b) or manual loop	Arrays.equals(a, b);	JSON.stringify(a) === JSON.stringify(b)
Arrays.fill(arr, val)	arr.fill(val)	Arrays.fill(a, 7);	arr.fill(7);
Arrays.asList(...)	Just [ ... ] array literal	List<Integer> list = Arrays.asList(1,2,3);	let list = [1, 2, 3];
Arrays.binarySearch(arr, key)	No built-in, use arr.indexOf(key) (linear) or manual binary search	Arrays.binarySearch(a, 3);	arr.indexOf(3);
Arrays.stream(arr)	arr.map(...) or arr.filter(...)	Arrays.stream(a).forEach(...)	arr.forEach(...)
Arrays.deepToString(arr2D)	JSON.stringify(arr2D)	System.out.println(Arrays.deepToString(a));	console.log(JSON.stringify(arr2D));
Collections.reverse(list) (for Lists)	arr.reverse()	Collections.reverse(list);	arr.reverse();

✅ 5. copyOf vs copyOfRange

Arrays.copyOf(arr, n)

Copies the first n elements from the original array arr.

If n is larger than arr.length, the extra elements are filled with default values (0 for int, null for objects, etc.).

Example:

int[] arr = {1, 2, 3, 4};
int[] copy = Arrays.copyOf(arr, 2);   // copy = [1, 2]
int[] copy2 = Arrays.copyOf(arr, 6);  // copy2 = [1, 2, 3, 4, 0, 0]


Arrays.copyOfRange(arr, from, to)

Copies elements from index from (inclusive) to index to (exclusive).

You can copy any subrange, not just the beginning.

Example:

int[] arr = {1, 2, 3, 4, 5};
int[] sub = Arrays.copyOfRange(arr, 1, 4);  // sub = [2, 3, 4]


✅ Key difference

Feature	copyOf	copyOfRange
Portion copied	First n elements	Elements from index from to to-1
Extra elements	Fills with default values if n > arr.length	Throws ArrayIndexOutOfBoundsException if from or to invalid
Flexibility	Less flexible	More flexible for subarrays

✅ 6. Lexical vs Numeric sorting in JS

1️⃣ Lexical (default) sort

arr.sort() without a compare function sorts elements as strings.

Works like dictionary order.

Example:

let arr = [10, 2, 33, 4];
arr.sort();
console.log(arr); // Output: [10, 2, 33, 4]


Notice how "10" comes before "2" because it compares first character.

2️⃣ Numeric sort

To sort numbers correctly, you provide a compare function:

let arr = [10, 2, 33, 4];
arr.sort((a, b) => a - b); 
console.log(arr); // Output: [2, 4, 10, 33]


For descending order: (b - a).

✅ Key difference:

Type	How elements are compared
Lexical	Compare as strings
Numeric	Compare as numbers

✅ 7. arr.sort() algorithm (TimSort)

In JavaScript, .sort() doesn’t guarantee a specific algorithm across all engines.

Most modern engines (V8, SpiderMonkey) use TimSort (hybrid of Merge Sort + Insertion Sort).

Step:

Comparator (a, b) => a - b:

Negative → a comes before b

Positive → b comes before a

Zero → order unchanged

Time Complexity:

Worst-case: O(n log n)

Best-case: O(n)

✅ 8. arr.toString()

Converts an array into a string with elements separated by a comma.

Example:

let arr = [1, 2, 3, 4];
console.log(arr.toString()); // "1,2,3,4"


Original array remains unchanged: console.log(arr); // [1,2,3,4]

Works with any type of element:

let arr2 = [1, "hello", true];
console.log(arr2.toString()); // "1,hello,true"


Equivalent to arr.join(",") by default.

✅ 9. join() and JSON.stringify()

join() → converts array to string with custom separator.

let arr = [1, 2, 3, 4];
console.log(arr.join());       // "1,2,3,4"
console.log(arr.join("-"));    // "1-2-3-4"
console.log(arr.join(" "));    // "1 2 3 4"


JSON.stringify() → converts array into JSON string, including brackets and quotes:

let arr = [1, "hi", true];
console.log(JSON.stringify(arr)); // '[1,"hi",true]'

Method	Separator	Keeps array?	Output type
toString()	,	Yes	string
join(separator)	custom	Yes	string
JSON.stringify	N/A	Yes	JSON string

✅ 10. Arrays.equals() / JSON.stringify() / Manual loop

Java Arrays.equals(a, b) → checks same length + same elements

JS JSON.stringify(a) === JSON.stringify(b) → compares stringified arrays

Manual loop → compare element by element

Example in JS:

let a = [1, 2, 3];
let b = [1, 2, 3];
let equal = true;
if(a.length !== b.length) equal = false;
for(let i = 0; i < a.length; i++){
    if(a[i] !== b[i]){
        equal = false;
        break;
    }
}
console.log(equal); // true


✅ 11. Arrays.fill() / arr.fill()

Java:

int[] arr = {1, 2, 3, 4, 5};
Arrays.fill(arr, 7);          // [7, 7, 7, 7, 7]
Arrays.fill(arr, 1, 4, 0);    // partial fill: [1, 0, 0, 0, 5]


JS:

let arr = [1, 2, 3, 4, 5];
arr.fill(0, 1, 4);  // [1, 0, 0, 0, 5]


✅ 12. Arrays.stream(arr) / arr.map / arr.filter / forEach / deepToString

Java Streams → chain operations on array

int[] arr = {1, 2, 3, 4, 5};
int sum = Arrays.stream(arr).sum(); // 15
Arrays.stream(arr).map(x -> x*2).forEach(System.out::println);


JS equivalents:

let arr = [1, 2, 3, 4, 5];
let doubled = arr.map(x => x*2);
let even = arr.filter(x => x % 2 === 0);
arr.forEach(x => console.log(x));


Nested arrays:

int[][] arr2D = {{1,2},{3,4}};
System.out.println(Arrays.deepToString(arr2D)); // [[1,2],[3,4]]

let arr2D = [[1,2],[3,4]];
console.log(JSON.stringify(arr2D)); // [[1,2],[3,4]]


✅ 13. Dry run: Arrays.stream(arr).sum()

int[] arr = {1, 2, 3, 4, 5};
int sum = Arrays.stream(arr).sum();
System.out.println(sum); // 15


Step by step:

arr = [1,2,3,4,5]

Arrays.stream(arr) → stream: 1 → 2 → 3 → 4 → 5

.sum() → 0+1+2+3+4+5 = 15

Prints 15

Equivalent manual:

int total = 0;
for(int i=0; i<arr.length; i++) total += arr[i];


✅ 14. sum() built-in in Java

Built-in function in IntStream

Adds up all integers in the stream

Works with filter/map operations

Example:

int totalEven = Arrays.stream(arr)
                      .filter(x -> x % 2 == 0)
                      .sum(); // 2 + 4 = 6


Cleaner than manual for-loop

Works with parallel streams

Fits functional programming style

✅ 15. Internal working of sum()

Arrays.stream(arr) → creates IntStream

sum() → terminal operation, internally loops through array and adds each element to a running total

Equivalent manual loop:

int sum = 0
