# Android Basics: Multiscreen Apps
- - - -

## Arrays, Lists, Loops & Custom Classes
- - - -

- How to some a list of words in the app (Arrays, ArrayLists)
- Display a list of words
- Display a list of English/Miwok word pairs
- Add the words from all the remaining categories


## Arrays
- - - -

<strong>All variables need a data type.</strong>

<strong>You can have an array of any data type:</strong>

- int
- double
- boolean
- char
- long
- float
- short
- byte
- Objects
	
```java
// Create array
int [] showSizesAvailable = new int[3];

// Initialize elements in an array
shoeSizesAvailable[0] = 5;
shoeSizesAvailable[1] = 7;
shoeSizesAvailable[2] = 10;

// Access elements in an array
shoeSizesAvailable[0] = 5;
shoeSizesAvailable[1] = 7;
shoeSizesAvailable[2] = 10;

// Get the array length
shoeSizesAvailable.length // -> value of 3
```

<html>
<strong><h3>Array vs ArrayList</h3></strong>
<table>
<tr>
<th></th>
<th><strong>Array</strong></th>
<th><strong>ArrayList</strong></th>
</tr>
<tr>
<td>Is it a class?</td>
<td>No</td>
<td>Yes</td>
</tr>
<tr>
<td>Can it change size once created?</td>
<td>No</td>
<td>Yes</td>
</tr>
<tr>
<td>Does it use methods to access and modify elements?</td>
<td>No</td>
<td>Yes</td>
</tr>
</table>
</html>

## ArrayLists
- - - -

1. Documentation: [List | Android Developers](https://developer.android.com/reference/java/util/List.html)
2. Documentation: [AbstractList | Android Developers](https://developer.android.com/reference/java/util/AbstractList.html) 
3. Documentation: [ArrayList | Android Developers](https://developer.android.com/reference/java/util/ArrayList.html)

### <strong>Concrete Class: ArrayList</strong>
```java

public class ArrayList {
	
	int size;
	Object[] elements;

	boolean add(E e) {
		elements[size++] = e;
	}

	E remove(int index){
		elements[--size] = null;
	}

	E get(int index) {
		return(E) elements[index];
	}

...
}
```

### <strong>Abstract Class: AbstractList</strong>
```java
public abstract class AbstractList {

	boolean add(E e) {
		add(size(), e);
		return true;
}

	E get(int index);

...
}


```


### <strong>Interface: List</strong>
```java
// No implementation of its methods
public interface List {

	boolean add(E object);

	E remove(int index);

	E get(int index);
}
```

### Type Parameters

<table>
	<tr>
		<th><strong><u>Symbol</u></strong></th>
		<th><strong><u>Type</u></strong></th>
	</tr>
	<tr>
		<td>E</td>
		<td>Element</td>
	</tr>
	<tr>
		<td>K</td>
		<td>Key</td>
	</tr>
	<tr>
		<td>N</td>
		<td>Number</td>
	</tr>
	<tr>
		<td>T</td>
		<td>Type</td>
	</tr>
	<tr>
		<td>V</td>
		<td>Value</td>
	</tr>
	<tr>
		<td>S, U, V, etc.</td>
		<td>2nd, 3rd, 4th types (when there is more than one parameter)</td>
	</tr>
</table> 

## How to Create and Access Elements in an ArrayList
- - - -

<dl>
	<dt>
		Create an ArrayList
	</dt>
	<dd>
		<pre><code>
			ArrayList&lt;String&gt; musicLibrary = new ArrayList&lt;String&gt;();
		</code></pre>
	</dd>
<br>
	<dt>
		Add elements in an ArrayList
	</dt>
	<dd>
		<pre><code>
			musicLibrary.add(“Yellow Submarine”);<br>
			musicLibrary.add(“Thriller”);<br>
			// Adds an element at a specific index<br>
			musicLibrary.add(0, “Blue Suede Shoes”);	
		</code></pre>
	</dd>
<br>
	<dt>
		Access elements in an ArrayList
	</dt>
	<dd>
		<pre><code>
			musicLibrary.get(0);<br>
			musicLibrary.get(1);<br>
			musicLibrary.get(2);
		</code></pre>
	</dd>
<br>
	<dt>
		Remove elements from an ArrayList
	</dt>
	<dd>
		<pre><code>
			// Remove the element at the specific index<br>
			musicLibrary.remove(2);
		</code></pre>
	</dd>
<br>
	<dt>
		Get ArrayList length or size
	</dt>
	<dd>
		<pre><code>
			musicLibrary.size();
		</code></pre>
	</dd>
</dl>


## Loops
- - - -


### While Loops

The code within the loop will be executed until the condition in parentheses is `false`
```java
while(<condition>){
	<instructions>
}
```

Steps:
1. What is the task to repeat?
	-> <instructions>
2. How many times to repeat? 
3. What is the condition?
	-> Count variable < 3

```java
int count = 0;

while(count < 3){
	playSound();
	count += 1;
}
```

### Counter Shorthands

<table>
<tr>
	<th><strong><u>Shorthand</u></strong></th>
	<th><strong><u>Meaning</u></strong></th>
</tr>
<tr>
	<td>i++</td>
	<td>i = i + 1</td>
</tr>
<tr>
	<td>j--</td>
	<td>j = j - 1</td>
</tr>
<tr>
	<td>j += 3</td>
	<td>j = j +3</td>
</tr>
</table>

### For Loop

```java
for (int index=0; index < 3; index++){
	Log.v("NumbersActivity", "Index: " + index + "Value: " + words.get(index));
}
```


### View Recycling
- - - -

When looking at 1000 contacts, 
Only 5 will appear on the screen at any time.
Instead of creating 1000 TextViews, we create 5, and change the content as the user scrolls.
This is called ~view recycling~.

Using a ListView and an ArrayAdapter, we can create just enough views based on what we need to fill the screen.

We create a bunch of views, and have a pile of ~scrap views~, that aren’t currently being shown on the screen.

When a user scrolls down, and a View goes off of the top of the screen, it gets cycled back around to the top of the screen to be used again.

When a user scrolls up, and a View goes off the bottom of the screen, it gets cycled back around to the bottom of the screen to be used again. 

DEPRECATED: ~~Documentation: [Memory Monitor | Android Studio](https://developer.android.com/studio/profile/am-memory.html?utm_source=udacity&utm_medium=course&utm_campaign=android_basics)~~

~Memory Monitor~ : a feature in Android Studio that keeps track of your application’s memory usage (DEPRECATED)

Documentation: [View the Java Heap and Memory Allocations with Memory Profiler | Android Studio](https://developer.android.com/studio/profile/memory-profiler.html)
~Memory Profiler~ : a feature introduced in Android Studio 3.0 that helps you identify memory leaks and memory churn.








#programming/java/android/beginner/3-multiscreen-apps/2-arrays-lists-loops-custom-classes