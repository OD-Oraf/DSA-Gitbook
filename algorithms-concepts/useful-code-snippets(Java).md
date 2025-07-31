# Useful Code Snippets 

## String

``` java
// Sort String as character array
char[] chars = s2.toCharArray();
Arrays.sort(chars);
//Create String from chararray
String sorted = new String(chars);

//Check value of string for equality
String c = "D"
c.equals("D") // true

//Convert string representation of int to integer
String c = "5"
Integer.valueOf(c) // = 5
```

## Character

```java
//Covert char to ascii value
char character = 'a'
int ascii = int character;

//Check value of string for equality
String c = "D";
c.equals("D"); // true

//Convert string representation of int to integer
String c = "5";
Integer.valueOf(c); // = 5
```

## Arrays

```java
// Sort 2D array for intervals questions
Arrays.sort(intervals, (a,b) -> Integer.compare(a[0], b[0]));

// Convet linked list to 2D array
LinkedList<int[]> merged = new LinkedList();
merged.toArray(new int[merged.size()][]);

//Check arrays for equality
Arrays.equals(arr1, arr2);
Arrays.compare(arr1, arr2); // return 0 if arrays are equal

//Print value of array
Arrays.toString();

//Slice of Array
Arrays.copyOfRange(nums,1,nums.length);

//Add new ArrayList<T> object to to List<List<T>>
List<List<Integer>> ans = new ArrayList<>();
ans.add(Arrays.asList(1,2,3));

//Print ArrayList object to console
System.out.println(Arrays.toString(ans.toArray()));
```

## HashMap

```java
// Some code
//Add hashmap values to arraylist
List<List<String>> res = new ArrayList<>();
res.addAll(map.values());
```

##
