# KOTLIN TO ANDROID DEVELOPMENT

## Complete Handbook: From Beginner to Building a Weather App

[![Kotlin](https://img.shields.io/badge/Kotlin-1.9+-purple.svg)](https://kotlinlang.org/)
[![Android](https://img.shields.io/badge/Android-API%2024+-green.svg)](https://developer.android.com/)
[![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-1.5+-blue.svg)](https://developer.android.com/jetpack/compose)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> A comprehensive guide to learn Kotlin and build modern Android applications using Jetpack Compose, MVVM architecture, and Retrofit. Perfect for beginners and intermediate developers.

### 📱 What You'll Build

By the end of this handbook, you'll have built a **fully functional Weather App** that:

- 🌤️ Fetches real-time weather data from OpenWeather API
- 🎨 Uses Material Design 3 components
- 🏗️ Implements MVVM architecture
- 🔄 Handles loading states and errors gracefully
- 📱 Provides a beautiful, responsive UI

### ✨ What You'll Learn

### ✨ What You'll Learn

- ✅ Master Kotlin programming fundamentals
- ✅ Understand Android architecture and components
- ✅ Build modern UIs with Jetpack Compose
- ✅ Implement MVVM architecture pattern
- ✅ Make network calls using Retrofit
- ✅ Create a complete Weather App

### 🚀 Quick Start

1. **Prerequisites**: Install [Android Studio](https://developer.android.com/studio) (latest version)
2. **Get API Key**: Sign up at [OpenWeather](https://openweathermap.org/api) for a free API key
3. **Follow Along**: Each chapter builds on the previous one
4. **Code Examples**: All code is tested and ready to use

### 📖 How to Use This Handbook

- **Beginners**: Start from Chapter 1 and work through sequentially
- **Experienced Developers**: Jump to specific chapters using the Table of Contents
- **Quick Reference**: Use the Appendix for Kotlin and Compose cheat sheets

---

## Table of Contents

### Part 1: Kotlin Fundamentals

1. [Introduction to Kotlin](#chapter-1-introduction-to-kotlin)
2. [Kotlin Basics](#chapter-2-kotlin-basics)
3. [Functions and Lambdas](#chapter-3-functions-and-lambdas)
4. [Object-Oriented Programming](#chapter-4-object-oriented-programming-in-kotlin)
5. [Collections and Sequences](#chapter-5-collections-and-sequences)
6. [Kotlin Coroutines](#chapter-6-kotlin-coroutines)

### Part 2: Android Fundamentals

7. [Understanding Android Architecture](#chapter-7-understanding-android-architecture)

### Part 3: Jetpack Compose

8. [Introduction to Jetpack Compose](#chapter-8-introduction-to-jetpack-compose)
9. [Layouts in Compose](#chapter-9-layouts-in-jetpack-compose)
10. [State Management](#chapter-10-state-management-in-compose)
11. [Material Design 3](#chapter-11-material-design-3-in-compose)

### Part 4: Architecture Components

12. [MVVM Architecture Pattern](#chapter-12-mvvm-architecture-pattern)
13. [Repository Pattern](#chapter-13-repository-pattern)

### Part 5: Networking with Retrofit

14. [Introduction to Retrofit](#chapter-14-introduction-to-retrofit)
15. [Making API Calls](#chapter-15-making-api-calls)

### Part 6: Final Project - Weather App

16. [Project Setup](#chapter-16-project-setup)
17. [Complete Implementation](#chapter-17-complete-weather-app-implementation)
18. [Testing and Deployment](#chapter-18-testing-and-deployment)
19. [Next Steps and Enhancements](#chapter-19-next-steps-and-enhancements)

---

# PART 1: KOTLIN FUNDAMENTALS

**In This Part:**

- [Chapter 1: Introduction to Kotlin](#chapter-1-introduction-to-kotlin)
- [Chapter 2: Kotlin Basics](#chapter-2-kotlin-basics)
- [Chapter 3: Functions and Lambdas](#chapter-3-functions-and-lambdas)
- [Chapter 4: Object-Oriented Programming](#chapter-4-object-oriented-programming-in-kotlin)
- [Chapter 5: Collections and Sequences](#chapter-5-collections-and-sequences)
- [Chapter 6: Kotlin Coroutines](#chapter-6-kotlin-coroutines)

---

## Chapter 1: Introduction to Kotlin

### 1.1 What is Kotlin?

Kotlin is a modern, statically-typed programming language that runs on the Java Virtual Machine (JVM). Developed by JetBrains and officially supported by Google for Android development since 2017, Kotlin is designed to be:

- **Concise**: Reduces boilerplate code significantly
- **Safe**: Built-in null safety prevents NullPointerException
- **Interoperable**: 100% compatible with Java
- **Modern**: Combines OOP and functional programming features
- **Tool-friendly**: Excellent IDE support

### 1.2 Why Kotlin for Android?

**Advantages over Java:**

- Less verbose - write 40% less code
- Null safety by default
- Extension functions
- Coroutines for asynchronous programming
- Smart casts
- Data classes
- Official Google support

**Industry Adoption:**

- Google's preferred language for Android
- Used by over 95% of top 1000 Android apps
- Strong community and ecosystem

### 1.3 Setting Up Your Development Environment

**Prerequisites:**

1. **Download Android Studio** (latest version) from developer.android.com
2. **Install JDK 17** or higher (bundled with Android Studio)
3. **Configure Android SDK** through SDK Manager
4. **Create your first project** using "Empty Activity" template

**System Requirements:**

- Windows 10/11, macOS 10.14+, or Linux
- 8 GB RAM minimum (16 GB recommended)
- 8 GB available disk space
- 1280 x 800 minimum screen resolution

---

## Chapter 2: Kotlin Basics

### 2.1 Variables and Data Types

Kotlin uses two keywords for variable declaration:

- `val` - immutable (read-only) variable
- `var` - mutable variable

```kotlin
// Immutable variable (preferred when possible)
val name: String = "John"
val age = 25  // Type inference

// Mutable variable
var count: Int = 0
count = 10  // OK

// Basic data types
val myInt: Int = 42
val myLong: Long = 42L
val myFloat: Float = 3.14f
val myDouble: Double = 3.14159
val myBoolean: Boolean = true
val myChar: Char = 'A'
val myString: String = "Hello, Kotlin!"
```

**Type Inference:**
Kotlin can automatically determine the type based on the assigned value.

**Naming Conventions:**

- Use camelCase for variables
- Use descriptive names
- Constants use UPPER_SNAKE_CASE

### 2.2 Null Safety

One of Kotlin's most powerful features is built-in null safety.

```kotlin
// Non-nullable type (default)
var name: String = "Alice"
// name = null  // Compilation error!

// Nullable type
var nullableName: String? = "Bob"
nullableName = null  // OK

// Safe call operator (?.)
val length = nullableName?.length  // Returns null if nullableName is null

// Elvis operator (?:) - provides default value
val len = nullableName?.length ?: 0

// Not-null assertion (!!) - use carefully!
val forcedLength = nullableName!!.length  // Throws exception if null

// Safe casting
val str: String? = value as? String  // Returns null if cast fails
```

**Best Practices:**

- Prefer non-nullable types when possible
- Use safe call operators instead of null checks
- Avoid `!!` operator unless absolutely necessary

### 2.3 Control Flow

#### If-Else Expressions

In Kotlin, `if` is an expression, not a statement.

```kotlin
val max = if (a > b) {
    println("a is greater")
    a  // Last expression is returned
} else {
    println("b is greater")
    b
}

// Single line
val min = if (a < b) a else b
```

#### When Expression

`when` is Kotlin's replacement for switch statements, but much more powerful.

```kotlin
when (x) {
    1 -> println("One")
    2, 3 -> println("Two or Three")
    in 4..10 -> println("Between 4 and 10")
    !in 10..20 -> println("Outside 10-20")
    else -> println("Unknown")
}

// As expression
val result = when (x) {
    1 -> "One"
    2 -> "Two"
    else -> "Other"
}

// Without argument (like if-else chain)
when {
    x.isOdd() -> println("Odd")
    x.isEven() -> println("Even")
    else -> println("Unknown")
}
```

### 2.4 Loops

```kotlin
// For loop with range
for (i in 1..5) {
    println(i)  // 1, 2, 3, 4, 5
}

// For loop with step
for (i in 1..10 step 2) {
    println(i)  // 1, 3, 5, 7, 9
}

// For loop backwards
for (i in 10 downTo 1) {
    println(i)  // 10, 9, 8, ... 1
}

// Iterating over collection
val fruits = listOf("Apple", "Banana", "Orange")
for (fruit in fruits) {
    println(fruit)
}

// Iterating with index
for ((index, fruit) in fruits.withIndex()) {
    println("$index: $fruit")
}

// While loop
var x = 5
while (x > 0) {
    println(x)
    x--
}

// Do-while loop
do {
    println("Executed at least once")
} while (false)

// Repeat function
repeat(3) {
    println("Hello")
}
```

### 2.5 String Templates

```kotlin
val name = "Alice"
val age = 30

// Simple template
println("My name is $name")

// Expression in template
println("In 5 years, I'll be ${age + 5}")

// Complex expression
println("Name length: ${name.length}")

// Raw string (triple quotes)
val text = """
    This is a multi-line string
    It preserves formatting
    No need for escape characters
""".trimIndent()
```

---

## Chapter 3: Functions and Lambdas

### 3.1 Function Declaration

```kotlin
// Basic function
fun greet(name: String): String {
    return "Hello, $name!"
}

// Single-expression function
fun add(a: Int, b: Int) = a + b

// Function with no return value (Unit)
fun printSum(a: Int, b: Int) {
    println("Sum is ${a + b}")
}

// Default parameters
fun log(message: String, level: String = "INFO", tag: String = "App") {
    println("[$tag][$level] $message")
}

// Usage
log("Error occurred", level = "ERROR")

// Named arguments
log(level = "ERROR", message = "Something went wrong", tag = "MainActivity")

// Vararg parameters
fun sum(vararg numbers: Int): Int {
    return numbers.sum()
}

val total = sum(1, 2, 3, 4, 5)  // 15
```

### 3.2 Lambda Expressions

Lambdas are anonymous functions that can be passed as arguments.

```kotlin
// Lambda syntax: { parameters -> body }
val square: (Int) -> Int = { x -> x * x }
println(square(5))  // 25

// Lambda with multiple parameters
val multiply = { a: Int, b: Int -> a * b }

// Lambda with no parameters
val greet = { println("Hello!") }

// Lambda as last parameter (trailing lambda)
val numbers = listOf(1, 2, 3, 4, 5)
val doubled = numbers.map { it * 2 }  // 'it' is implicit parameter

// Multiple parameters
numbers.forEachIndexed { index, value ->
    println("$index: $value")
}

// Lambda with explicit return
val sumPositive = { numbers: List<Int> ->
    numbers.filter { it > 0 }.sum()
}
```

### 3.3 Higher-Order Functions

Functions that take other functions as parameters or return functions.

```kotlin
// Function that takes a function as parameter
fun calculate(x: Int, y: Int, operation: (Int, Int) -> Int): Int {
    return operation(x, y)
}

// Usage
val sum = calculate(5, 3) { a, b -> a + b }
val product = calculate(5, 3) { a, b -> a * b }

// Function returning a function
fun makeMultiplier(factor: Int): (Int) -> Int {
    return { number -> number * factor }
}

val doubler = makeMultiplier(2)
val tripler = makeMultiplier(3)

println(doubler(5))  // 10
println(tripler(5))  // 15
```

### 3.4 Extension Functions

Add new functions to existing classes without modifying them.

```kotlin
// Extension function for String
fun String.addExclamation(): String {
    return this + "!"
}

val message = "Hello".addExclamation()  // "Hello!"

// Extension function for Int
fun Int.isEven(): Boolean = this % 2 == 0
fun Int.isOdd(): Boolean = this % 2 != 0

println(10.isEven())  // true
println(7.isOdd())    // true

// Extension function with parameters
fun String.repeat(times: Int): String {
    return this.repeat(times)
}

println("Ha".repeat(3))  // "HaHaHa"
```

### 3.5 Scope Functions

Kotlin provides several scope functions for executing code in the context of an object.

```kotlin
// let - execute lambda with 'it' as argument
val name: String? = "Alice"
name?.let {
    println("Name length: ${it.length}")
}

// apply - configure object and return it
val person = Person().apply {
    name = "Alice"
    age = 30
}

// also - perform additional operations
val numbers = mutableListOf(1, 2, 3).also {
    println("List before: $it")
}.apply {
    add(4)
}

// run - execute lambda and return result
val result = "Hello".run {
    println("Length: $length")
    uppercase()  // Returns "HELLO"
}

// with - non-extension function
val length = with("Hello") {
    println("Processing: $this")
    length
}
```

---

## Chapter 4: Object-Oriented Programming

### 4.1 Classes and Objects

```kotlin
// Basic class
class Person(val name: String, var age: Int) {
    // Member function
    fun greet() {
        println("Hi, I'm $name and I'm $age years old")
    }
}

// Creating an instance
val person = Person("Alice", 30)
person.greet()

// Class with init block
class User(val email: String) {
    init {
        println("User created: $email")
        require(email.contains("@")) { "Invalid email" }
    }
}

// Primary and secondary constructors
class Rectangle(val width: Int, val height: Int) {
    // Secondary constructor
    constructor(side: Int) : this(side, side) {
        println("Creating a square with side $side")
    }

    fun area() = width * height
    fun perimeter() = 2 * (width + height)
}

val square = Rectangle(5)
val rect = Rectangle(4, 6)
```

### 4.2 Properties

```kotlin
class Person(val firstName: String, val lastName: String) {
    // Custom getter
    val fullName: String
        get() = "$firstName $lastName"

    // Property with backing field
    var age: Int = 0
        set(value) {
            if (value >= 0) {
                field = value
            }
        }

    // Lazy property
    val expensiveValue: String by lazy {
        println("Computing expensive value...")
        "Result"
    }
}
```

### 4.3 Data Classes

Data classes automatically generate useful methods.

```kotlin
data class User(
    val id: Int,
    val name: String,
    val email: String
)

val user1 = User(1, "John", "john@example.com")
val user2 = user1.copy(name = "Jane")

// Auto-generated toString()
println(user1)  // User(id=1, name=John, email=john@example.com)

// Auto-generated equals()
println(user1 == user2)  // false

// Destructuring
val (id, name, email) = user1
```

### 4.4 Inheritance

```kotlin
// Classes are final by default - use 'open' to allow inheritance
open class Animal(val name: String) {
    open fun makeSound() {
        println("Some generic sound")
    }

    fun sleep() {
        println("$name is sleeping")
    }
}

class Dog(name: String) : Animal(name) {
    override fun makeSound() {
        println("Woof! Woof!")
    }

    fun fetch() {
        println("$name is fetching the ball")
    }
}

class Cat(name: String) : Animal(name) {
    override fun makeSound() {
        println("Meow!")
    }
}

val dog = Dog("Buddy")
dog.makeSound()  // Woof! Woof!
dog.sleep()      // Buddy is sleeping
```

### 4.5 Interfaces

```kotlin
interface Clickable {
    fun click()  // Abstract function
    fun showInfo() = println("Clickable")  // Default implementation
}

interface Draggable {
    fun drag()
}

// Implementing multiple interfaces
class Button : Clickable, Draggable {
    override fun click() {
        println("Button clicked")
    }

    override fun drag() {
        println("Button dragged")
    }
}
```

### 4.6 Object Declarations and Companion Objects

```kotlin
// Singleton object
object DatabaseConfig {
    const val URL = "jdbc:mysql://localhost:3306/mydb"
    const val USER = "root"

    fun connect() {
        println("Connecting to $URL")
    }
}

DatabaseConfig.connect()

// Companion object (like static in Java)
class MyClass {
    companion object {
        const val TAG = "MyClass"

        fun create(): MyClass {
            return MyClass()
        }
    }
}

val tag = MyClass.TAG
val instance = MyClass.create()
```

### 4.7 Sealed Classes

Sealed classes restrict class hierarchies.

```kotlin
sealed class Result<out T> {
    data class Success<T>(val data: T) : Result<T>()
    data class Error(val exception: Exception) : Result<Nothing>()
    object Loading : Result<Nothing>()
}

fun handleResult(result: Result<String>) {
    when (result) {
        is Result.Success -> println("Data: ${result.data}")
        is Result.Error -> println("Error: ${result.exception.message}")
        is Result.Loading -> println("Loading...")
    }
}
```

---

## Chapter 5: Collections and Sequences

### 5.1 Lists

```kotlin
// Immutable list (read-only)
val fruits = listOf("Apple", "Banana", "Orange")

// Mutable list
val mutableFruits = mutableListOf("Apple", "Banana")
mutableFruits.add("Orange")
mutableFruits.removeAt(0)
mutableFruits[0] = "Mango"

// Accessing elements
val first = fruits[0]
val firstOrNull = fruits.getOrNull(10)
val firstOrDefault = fruits.getOrElse(10) { "Default" }

// Common operations
val size = fruits.size
val isEmpty = fruits.isEmpty()
val contains = "Apple" in fruits
val index = fruits.indexOf("Banana")
```

### 5.2 Sets

```kotlin
// Immutable set (no duplicates, no order)
val numbers = setOf(1, 2, 3, 2, 1)  // [1, 2, 3]

// Mutable set
val mutableNumbers = mutableSetOf(1, 2, 3)
mutableNumbers.add(4)
mutableNumbers.remove(1)

// Set operations
val set1 = setOf(1, 2, 3)
val set2 = setOf(3, 4, 5)

val union = set1 union set2        // [1, 2, 3, 4, 5]
val intersection = set1 intersect set2  // [3]
val difference = set1 subtract set2     // [1, 2]
```

### 5.3 Maps

```kotlin
// Immutable map
val ages = mapOf(
    "Alice" to 30,
    "Bob" to 25,
    "Charlie" to 35
)

// Mutable map
val mutableAges = mutableMapOf("Alice" to 30)
mutableAges["Bob"] = 25
mutableAges.put("Charlie", 35)
mutableAges.remove("Alice")

// Accessing values
val aliceAge = ages["Alice"]
val defaultAge = ages.getOrDefault("Dave", 0)
val davidAge = ages.getOrElse("David") { 0 }

// Iterating
for ((name, age) in ages) {
    println("$name is $age years old")
}

ages.forEach { (name, age) ->
    println("$name: $age")
}
```

### 5.4 Collection Operations

```kotlin
val numbers = listOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

// Transformations
val doubled = numbers.map { it * 2 }
val strings = numbers.map { "Number $it" }
val flatMapped = listOf(listOf(1, 2), listOf(3, 4)).flatten()

// Filtering
val evens = numbers.filter { it % 2 == 0 }
val odds = numbers.filterNot { it % 2 == 0 }
val notNulls = listOf(1, null, 2, null, 3).filterNotNull()

// Aggregation
val sum = numbers.sum()
val max = numbers.maxOrNull()
val min = numbers.minOrNull()
val average = numbers.average()
val count = numbers.count { it % 2 == 0 }

// Grouping
val grouped = numbers.groupBy { it % 3 }
// {1=[1, 4, 7, 10], 2=[2, 5, 8], 0=[3, 6, 9]}

// Partitioning
val (evens2, odds2) = numbers.partition { it % 2 == 0 }

// Sorting
val sorted = numbers.sortedDescending()
val sortedBy = numbers.sortedBy { -it }

// Take and drop
val first3 = numbers.take(3)
val last3 = numbers.takeLast(3)
val withoutFirst2 = numbers.drop(2)

// Any, all, none
val hasEven = numbers.any { it % 2 == 0 }
val allPositive = numbers.all { it > 0 }
val noneNegative = numbers.none { it < 0 }

// Find
val firstEven = numbers.find { it % 2 == 0 }
val firstOrNull = numbers.firstOrNull { it > 100 }

// Reduce and fold
val product = numbers.reduce { acc, i -> acc * i }
val sumWithInitial = numbers.fold(10) { acc, i -> acc + i }
```

### 5.5 Sequences

Sequences are lazy evaluated collections, better for large datasets.

```kotlin
// Creating a sequence
val sequence = sequenceOf(1, 2, 3, 4, 5)
val fromList = listOf(1, 2, 3).asSequence()

// Lazy evaluation example
val result = listOf(1, 2, 3, 4, 5)
    .asSequence()
    .map { println("Map $it"); it * 2 }
    .filter { println("Filter $it"); it > 5 }
    .toList()  // Only now are the operations executed

// Infinite sequence
val fibonacci = generateSequence(1 to 1) { (a, b) -> b to (a + b) }
    .map { it.first }
    .take(10)
    .toList()
```

---

## Chapter 6: Kotlin Coroutines

### 6.1 Introduction to Coroutines

Coroutines are Kotlin's way of handling asynchronous programming. They allow you to write asynchronous code that looks synchronous.

**Benefits:**

- Lightweight threads
- Structured concurrency
- Easy error handling
- Better resource management

### 6.2 Basic Coroutine

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello,")
}

// Output:
// Hello,
// World!
```

### 6.3 Coroutine Builders

```kotlin
// launch: Fire and forget
val job = GlobalScope.launch {
    delay(1000L)
    println("Background task")
}

// async: Returns a result
val deferred = GlobalScope.async {
    delay(1000L)
    "Result"
}
val result = deferred.await()

// runBlocking: Blocks the current thread
runBlocking {
    delay(1000L)
    println("Blocking")
}

// coroutineScope: Creates a scope
suspend fun doWork() = coroutineScope {
    launch {
        delay(1000L)
        println("Work 1")
    }
    launch {
        delay(2000L)
        println("Work 2")
    }
}
```

### 6.4 Coroutine Context and Dispatchers

```kotlin
// Dispatchers.Main - UI thread (Android)
launch(Dispatchers.Main) {
    updateUI()
}

// Dispatchers.IO - I/O operations
launch(Dispatchers.IO) {
    val data = fetchDataFromNetwork()
}

// Dispatchers.Default - CPU-intensive work
launch(Dispatchers.Default) {
    val result = performHeavyComputation()
}

// Switching contexts
launch {
    val data = withContext(Dispatchers.IO) {
        fetchData()  // Runs on IO dispatcher
    }
    updateUI(data)  // Back to original context
}
```

### 6.5 Structured Concurrency

```kotlin
class MyRepository {
    private val scope = CoroutineScope(Dispatchers.IO)

    fun loadData() {
        scope.launch {
            val data = fetchData()
            processData(data)
        }
    }

    fun cancel() {
        scope.cancel()  // Cancels all coroutines
    }
}
```

### 6.6 Exception Handling

```kotlin
// Using try-catch
launch {
    try {
        val result = withContext(Dispatchers.IO) {
            fetchData()
        }
    } catch (e: Exception) {
        handleError(e)
    }
}

// Using CoroutineExceptionHandler
val handler = CoroutineExceptionHandler { _, exception ->
    println("Caught $exception")
}

val scope = CoroutineScope(Dispatchers.Main + handler)
scope.launch {
    throw Exception("Error!")
}
```

---

[↑ Back to Top](#table-of-contents)

---

# PART 2: ANDROID FUNDAMENTALS

## Chapter 7: Understanding Android Architecture

### 7.1 Android Application Components

Android apps are built using four main components:

**1. Activities**

- Represents a single screen with a user interface
- Entry point for user interaction
- Manages UI lifecycle

**2. Fragments**

- Reusable portions of UI within an activity
- Can be combined to create multi-pane UIs
- Has its own lifecycle

**3. Services**

- Runs operations in the background
- No user interface
- Types: Foreground, Background, Bound

**4. Broadcast Receivers**

- Responds to system-wide broadcast announcements
- Examples: battery low, network changed

**5. Content Providers**

- Manages shared app data
- Provides data to other apps

### 7.2 Activity Lifecycle

Understanding the activity lifecycle is crucial:

```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        // Initialize activity
        // Set content view
    }

    override fun onStart() {
        super.onStart()
        // Activity visible to user
    }

    override fun onResume() {
        super.onResume()
        // Activity in foreground
        // Start animations, audio
    }

    override fun onPause() {
        super.onPause()
        // Activity losing focus
        // Pause ongoing operations
    }

    override fun onStop() {
        super.onStop()
        // Activity no longer visible
        // Release resources
    }

    override fun onDestroy() {
        super.onDestroy()
        // Activity being destroyed
        // Final cleanup
    }
}
```

**Lifecycle States:**

- Created → Started → Resumed → Paused → Stopped → Destroyed

### 7.3 Android Manifest

The AndroidManifest.xml declares app components and requirements:

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp">

    <!-- Permissions -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/Theme.MyApp">

        <!-- Main activity -->
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

### 7.4 Project Structure

```
app/
├── manifests/
│   └── AndroidManifest.xml
├── java/
│   └── com.example.app/
│       ├── data/
│       ├── ui/
│       └── MainActivity.kt
├── res/
│   ├── drawable/     # Images
│   ├── layout/       # XML layouts
│   ├── mipmap/       # App icons
│   ├── values/       # Strings, colors, themes
│   └── xml/          # Other XML files
└── build.gradle.kts  # Build configuration
```

---

[↑ Back to Top](#table-of-contents)

---

# PART 3: JETPACK COMPOSE

**In This Part:**

- [Chapter 8: Introduction to Jetpack Compose](#chapter-8-introduction-to-jetpack-compose)
- [Chapter 9: Layouts in Compose](#chapter-9-layouts-in-jetpack-compose)
- [Chapter 10: State Management](#chapter-10-state-management-in-compose)
- [Chapter 11: Material Design 3](#chapter-11-material-design-3-in-compose)

---

## Chapter 8: Introduction to Jetpack Compose

### 8.1 What is Jetpack Compose?

Jetpack Compose is Android's modern toolkit for building native UI. It simplifies and accelerates UI development with:

- Declarative UI
- Less code
- Intuitive Kotlin APIs
- Powerful tooling
- Live previews

### 8.2 Setting Up Compose

In your app-level `build.gradle.kts`:

```kotlin
android {
    buildFeatures {
        compose = true
    }
    composeOptions {
        kotlinCompilerExtensionVersion = "1.5.8"
    }
}

dependencies {
    val composeBom = platform("androidx.compose:compose-bom:2024.01.00")
    implementation(composeBom)

    implementation("androidx.compose.ui:ui")
    implementation("androidx.compose.ui:ui-graphics")
    implementation("androidx.compose.ui:ui-tooling-preview")
    implementation("androidx.compose.material3:material3")
    implementation("androidx.activity:activity-compose:1.8.2")

    debugImplementation("androidx.compose.ui:ui-tooling")
    debugImplementation("androidx.compose.ui:ui-test-manifest")
}
```

### 8.3 Your First Composable

```kotlin
@Composable
fun Greeting(name: String) {
    Text(text = "Hello, $name!")
}

// In MainActivity
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            MyAppTheme {
                Greeting(name = "Android")
            }
        }
    }
}

// Preview
@Preview(showBackground = true)
@Composable
fun GreetingPreview() {
    MyAppTheme {
        Greeting("Preview")
    }
}
```

### 8.4 Basic Compose Components

```kotlin
@Composable
fun BasicComponents() {
    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(16.dp)
    ) {
        // Text
        Text(
            text = "Hello Compose",
            fontSize = 24.sp,
            fontWeight = FontWeight.Bold,
            color = Color.Blue
        )

        Spacer(modifier = Modifier.height(8.dp))

        // Button
        Button(onClick = { /* Action */ }) {
            Text("Click Me")
        }

        // Image
        Image(
            painter = painterResource(id = R.drawable.ic_launcher),
            contentDescription = "App Icon",
            modifier = Modifier.size(100.dp)
        )

        // TextField
        var text by remember { mutableStateOf("") }
        TextField(
            value = text,
            onValueChange = { text = it },
            label = { Text("Enter text") },
            modifier = Modifier.fillMaxWidth()
        )

        // Icon
        Icon(
            imageVector = Icons.Default.Favorite,
            contentDescription = "Favorite",
            tint = Color.Red
        )
    }
}
```

### 8.5 Modifiers

Modifiers allow you to decorate or augment composables:

```kotlin
@Composable
fun ModifierExamples() {
    Box(
        modifier = Modifier
            .size(200.dp)
            .background(Color.LightGray)
            .padding(16.dp)
            .border(2.dp, Color.Black)
            .clickable { /* Click action */ }
    ) {
        Text("Box with modifiers")
    }

    // Chain order matters!
    Text(
        "Order matters",
        modifier = Modifier
            .padding(16.dp)      // Padding applied first
            .background(Color.Yellow)  // Then background
    )
}
```

---

## Chapter 9: Layouts in Jetpack Compose

### 9.1 Column - Vertical Layout

```kotlin
@Composable
fun VerticalLayout() {
    Column(
        modifier = Modifier
            .fillMaxWidth()
            .padding(16.dp),
        verticalArrangement = Arrangement.spacedBy(8.dp),
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text("Item 1")
        Text("Item 2")
        Text("Item 3")
    }
}
```

**Vertical Arrangements:**

- `Arrangement.Top`
- `Arrangement.Bottom`
- `Arrangement.Center`
- `Arrangement.SpaceBetween`
- `Arrangement.SpaceAround`
- `Arrangement.SpaceEvenly`
- `Arrangement.spacedBy(8.dp)`

### 9.2 Row - Horizontal Layout

```kotlin
@Composable
fun HorizontalLayout() {
    Row(
        modifier = Modifier
            .fillMaxWidth()
            .padding(16.dp),
        horizontalArrangement = Arrangement.SpaceBetween,
        verticalAlignment = Alignment.CenterVertically
    ) {
        Icon(Icons.Default.Home, contentDescription = "Home")
        Text("Title", fontWeight = FontWeight.Bold)
        Icon(Icons.Default.Settings, contentDescription = "Settings")
    }
}
```

### 9.3 Box - Overlapping Layout

```kotlin
@Composable
fun OverlappingLayout() {
    Box(
        modifier = Modifier
            .size(200.dp)
            .background(Color.LightGray)
    ) {
        Text(
            text = "Top Left",
            modifier = Modifier.align(Alignment.TopStart)
        )
        Text(
            text = "Center",
            modifier = Modifier.align(Alignment.Center)
        )
        Text(
            text = "Bottom Right",
            modifier = Modifier.align(Alignment.BottomEnd)
        )
    }
}
```

### 9.4 LazyColumn - Scrollable Lists

```kotlin
@Composable
fun ScrollableList() {
    LazyColumn {
        items(100) { index ->
            ListItem(index = index)
        }
    }
}

@Composable
fun ListItem(index: Int) {
    Card(
        modifier = Modifier
            .fillMaxWidth()
            .padding(8.dp)
    ) {
        Text(
            text = "Item #$index",
            modifier = Modifier.padding(16.dp)
        )
    }
}
```

### 9.5 LazyRow - Horizontal Scrolling

```kotlin
@Composable
fun HorizontalScrollList() {
    LazyRow(
        horizontalArrangement = Arrangement.spacedBy(8.dp),
        contentPadding = PaddingValues(16.dp)
    ) {
        items(20) { index ->
            Card(
                modifier = Modifier.size(100.dp)
            ) {
                Box(contentAlignment = Alignment.Center) {
                    Text("$index")
                }
            }
        }
    }
}
```

---

## Chapter 10: State Management in Compose

### 10.1 Remember and MutableState

```kotlin
@Composable
fun Counter() {
    var count by remember { mutableStateOf(0) }

    Column(
        modifier = Modifier.padding(16.dp),
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text(
            text = "Count: $count",
            fontSize = 24.sp
        )

        Spacer(modifier = Modifier.height(16.dp))

        Row(horizontalArrangement = Arrangement.spacedBy(8.dp)) {
            Button(onClick = { count-- }) {
                Text("-")
            }
            Button(onClick = { count++ }) {
                Text("+")
            }
        }
    }
}
```

### 10.2 State Hoisting

State hoisting is moving state to a composable's caller:

```kotlin
@Composable
fun StatefulCounter() {
    var count by remember { mutableStateOf(0) }
    StatelessCounter(
        count = count,
        onIncrement = { count++ },
        onDecrement = { count-- }
    )
}

@Composable
fun StatelessCounter(
    count: Int,
    onIncrement: () -> Unit,
    onDecrement: () -> Unit
) {
    Column(horizontalAlignment = Alignment.CenterHorizontally) {
        Text("Count: $count", fontSize = 24.sp)
        Row {
            Button(onClick = onDecrement) { Text("-") }
            Spacer(Modifier.width(8.dp))
            Button(onClick = onIncrement) { Text("+") }
        }
    }
}
```

### 10.3 ViewModel Integration

```kotlin
class CounterViewModel : ViewModel() {
    private val _count = MutableStateFlow(0)
    val count: StateFlow<Int> = _count.asStateFlow()

    fun increment() {
        _count.value++
    }

    fun decrement() {
        _count.value--
    }
}

@Composable
fun CounterScreen(viewModel: CounterViewModel = viewModel()) {
    val count by viewModel.count.collectAsState()

    Column(horizontalAlignment = Alignment.CenterHorizontally) {
        Text("Count: $count", fontSize = 24.sp)
        Row {
            Button(onClick = { viewModel.decrement() }) { Text("-") }
            Spacer(Modifier.width(8.dp))
            Button(onClick = { viewModel.increment() }) { Text("+") }
        }
    }
}
```

---

## Chapter 11: Material Design 3 in Compose

### 11.1 Theme Setup

```kotlin
// ui/theme/Color.kt
val Purple80 = Color(0xFFD0BCFF)
val PurpleGrey80 = Color(0xFFCCC2DC)
val Pink80 = Color(0xFFEFB8C8)

val Purple40 = Color(0xFF6650a4)
val PurpleGrey40 = Color(0xFF625b71)
val Pink40 = Color(0xFF7D5260)

// ui/theme/Theme.kt
private val DarkColorScheme = darkColorScheme(
    primary = Purple80,
    secondary = PurpleGrey80,
    tertiary = Pink80
)

private val LightColorScheme = lightColorScheme(
    primary = Purple40,
    secondary = PurpleGrey40,
    tertiary = Pink40
)

@Composable
fun MyAppTheme(
    darkTheme: Boolean = isSystemInDarkTheme(),
    content: @Composable () -> Unit
) {
    val colorScheme = if (darkTheme) DarkColorScheme else LightColorScheme

    MaterialTheme(
        colorScheme = colorScheme,
        typography = Typography,
        content = content
    )
}
```

### 11.2 Material Components

```kotlin
@Composable
fun MaterialComponents() {
    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(16.dp),
        verticalArrangement = Arrangement.spacedBy(16.dp)
    ) {
        // Card
        Card(
            modifier = Modifier.fillMaxWidth(),
            elevation = CardDefaults.cardElevation(4.dp)
        ) {
            Text(
                text = "Card Content",
                modifier = Modifier.padding(16.dp)
            )
        }

        // Buttons
        Button(onClick = {}) {
            Text("Filled Button")
        }

        OutlinedButton(onClick = {}) {
            Text("Outlined Button")
        }

        TextButton(onClick = {}) {
            Text("Text Button")
        }

        // FloatingActionButton
        FloatingActionButton(onClick = {}) {
            Icon(Icons.Default.Add, contentDescription = "Add")
        }

        // Switch
        var checked by remember { mutableStateOf(false) }
        Switch(
            checked = checked,
            onCheckedChange = { checked = it }
        )

        // Checkbox
        Checkbox(
            checked = checked,
            onCheckedChange = { checked = it }
        )

        // Slider
        var sliderValue by remember { mutableStateOf(0f) }
        Slider(
            value = sliderValue,
            onValueChange = { sliderValue = it },
            valueRange = 0f..100f
        )

        // CircularProgressIndicator
        CircularProgressIndicator()

        // LinearProgressIndicator
        LinearProgressIndicator(
            modifier = Modifier.fillMaxWidth()
        )
    }
}
```

---

[↑ Back to Top](#table-of-contents)

---

# PART 4: ARCHITECTURE COMPONENTS

## Chapter 12: MVVM Architecture Pattern

### 12.1 What is MVVM?

MVVM (Model-View-ViewModel) separates concerns:

- **Model**: Data layer (repositories, data sources)
- **View**: UI layer (Composables)
- **ViewModel**: Holds UI state, handles business logic

**Benefits:**

- Separation of concerns
- Testability
- Lifecycle awareness
- Data persistence

### 12.2 Creating a ViewModel

```kotlin
// Data class (Model)
data class User(
    val id: Int,
    val name: String,
    val email: String
)

// UI State
data class UserUiState(
    val users: List<User> = emptyList(),
    val isLoading: Boolean = false,
    val error: String? = null
)

// ViewModel
class UserViewModel : ViewModel() {
    private val _uiState = MutableStateFlow(UserUiState())
    val uiState: StateFlow<UserUiState> = _uiState.asStateFlow()

    init {
        loadUsers()
    }

    private fun loadUsers() {
        viewModelScope.launch {
            _uiState.update { it.copy(isLoading = true) }

            try {
                // Simulate API call
                delay(1000)
                val users = listOf(
                    User(1, "Alice", "alice@example.com"),
                    User(2, "Bob", "bob@example.com")
                )

                _uiState.update {
                    it.copy(
                        users = users,
                        isLoading = false
                    )
                }
            } catch (e: Exception) {
                _uiState.update {
                    it.copy(
                        error = e.message,
                        isLoading = false
                    )
                }
            }
        }
    }
}
```

### 12.3 Using ViewModel in Compose

```kotlin
@Composable
fun UserScreen(viewModel: UserViewModel = viewModel()) {
    val uiState by viewModel.uiState.collectAsState()

    when {
        uiState.isLoading -> LoadingScreen()
        uiState.error != null -> ErrorScreen(uiState.error!!)
        else -> UserList(users = uiState.users)
    }
}

@Composable
fun UserList(users: List<User>) {
    LazyColumn {
        items(users) { user ->
            UserItem(user = user)
        }
    }
}

@Composable
fun UserItem(user: User) {
    Card(
        modifier = Modifier
            .fillMaxWidth()
            .padding(8.dp)
    ) {
        Column(modifier = Modifier.padding(16.dp)) {
            Text(
                text = user.name,
                fontWeight = FontWeight.Bold,
                fontSize = 18.sp
            )
            Text(
                text = user.email,
                color = Color.Gray
            )
        }
    }
}

@Composable
fun LoadingScreen() {
    Box(
        modifier = Modifier.fillMaxSize(),
        contentAlignment = Alignment.Center
    ) {
        CircularProgressIndicator()
    }
}

@Composable
fun ErrorScreen(message: String) {
    Box(
        modifier = Modifier.fillMaxSize(),
        contentAlignment = Alignment.Center
    ) {
        Text(
            text = "Error: $message",
            color = Color.Red
        )
    }
}
```

---

## Chapter 13: Repository Pattern

### 13.1 What is the Repository Pattern?

The Repository pattern provides a clean API for data access, abstracting the data sources.

**Benefits:**

- Centralized data access
- Easier testing
- Separation of concerns
- Single source of truth

### 13.2 Repository Implementation

```kotlin
// Repository Interface
interface UserRepository {
    suspend fun getUsers(): List<User>
    suspend fun getUserById(id: Int): User?
    suspend fun createUser(user: User): User
}

// Repository Implementation
class UserRepositoryImpl(
    private val apiService: ApiService,
    private val userDao: UserDao
) : UserRepository {

    override suspend fun getUsers(): List<User> {
        return try {
            // Try to fetch from network
            val users = apiService.getUsers()
            // Cache in database
            userDao.insertAll(users)
            users
        } catch (e: Exception) {
            // Fallback to local database
            userDao.getAllUsers()
        }
    }

    override suspend fun getUserById(id: Int): User? {
        // Try database first
        return userDao.getUserById(id)
            ?: apiService.getUserById(id)  // Fallback to API
    }

    override suspend fun createUser(user: User): User {
        val createdUser = apiService.createUser(user)
        userDao.insert(createdUser)
        return createdUser
    }
}
```

---

[↑ Back to Top](#table-of-contents)

---

# PART 5: NETWORKING WITH RETROFIT

## Chapter 14: Introduction to Retrofit

### 14.1 What is Retrofit?

Retrofit is a type-safe HTTP client for Android and Java. It makes it easy to consume RESTful web services.

**Features:**

- Type-safe API calls
- Easy JSON parsing
- Support for various converters
- Request/response interceptors
- Coroutine support

### 14.2 Adding Dependencies

In your app-level `build.gradle.kts`:

```kotlin
dependencies {
    // Retrofit
    implementation("com.squareup.retrofit2:retrofit:2.9.0")
    implementation("com.squareup.retrofit2:converter-gson:2.9.0")

    // OkHttp (for logging)
    implementation("com.squareup.okhttp3:okhttp:4.12.0")
    implementation("com.squareup.okhttp3:logging-interceptor:4.12.0")

    // Gson
    implementation("com.google.code.gson:gson:2.10.1")
}
```

### 14.3 Creating Data Models

```kotlin
data class WeatherResponse(
    val name: String,
    val main: Main,
    val weather: List<Weather>,
    val wind: Wind,
    val sys: Sys
)

data class Main(
    val temp: Double,
    @SerializedName("feels_like")
    val feelsLike: Double,
    @SerializedName("temp_min")
    val tempMin: Double,
    @SerializedName("temp_max")
    val tempMax: Double,
    val pressure: Int,
    val humidity: Int
)

data class Weather(
    val id: Int,
    val main: String,
    val description: String,
    val icon: String
)

data class Wind(
    val speed: Double
)

data class Sys(
    val country: String
)
```

### 14.4 Creating API Service

```kotlin
interface WeatherApiService {
    @GET("weather")
    suspend fun getCurrentWeather(
        @Query("q") cityName: String,
        @Query("appid") apiKey: String,
        @Query("units") units: String = "metric"
    ): WeatherResponse

    @GET("weather")
    suspend fun getWeatherByCoordinates(
        @Query("lat") latitude: Double,
        @Query("lon") longitude: Double,
        @Query("appid") apiKey: String,
        @Query("units") units: String = "metric"
    ): WeatherResponse
}
```

### 14.5 Setting Up Retrofit Instance

```kotlin
object RetrofitInstance {
    private const val BASE_URL = "https://api.openweathermap.org/data/2.5/"

    private val loggingInterceptor = HttpLoggingInterceptor().apply {
        level = HttpLoggingInterceptor.Level.BODY
    }

    private val client = OkHttpClient.Builder()
        .addInterceptor(loggingInterceptor)
        .connectTimeout(30, TimeUnit.SECONDS)
        .readTimeout(30, TimeUnit.SECONDS)
        .writeTimeout(30, TimeUnit.SECONDS)
        .build()

    val api: WeatherApiService by lazy {
        Retrofit.Builder()
            .baseUrl(BASE_URL)
            .client(client)
            .addConverterFactory(GsonConverterFactory.create())
            .build()
            .create(WeatherApiService::class.java)
    }
}
```

---

## Chapter 15: Making API Calls

### 15.1 Repository with Retrofit

```kotlin
sealed class Result<out T> {
    data class Success<T>(val data: T) : Result<T>()
    data class Error(val message: String) : Result<Nothing>()
    object Loading : Result<Nothing>()
}

class WeatherRepository(
    private val apiService: WeatherApiService
) {
    suspend fun getWeatherByCity(
        city: String,
        apiKey: String
    ): Result<WeatherResponse> {
        return try {
            val response = apiService.getCurrentWeather(city, apiKey)
            Result.Success(response)
        } catch (e: Exception) {
            Result.Error(e.message ?: "An unknown error occurred")
        }
    }

    suspend fun getWeatherByCoordinates(
        latitude: Double,
        longitude: Double,
        apiKey: String
    ): Result<WeatherResponse> {
        return try {
            val response = apiService.getWeatherByCoordinates(
                latitude, longitude, apiKey
            )
            Result.Success(response)
        } catch (e: Exception) {
            Result.Error(e.message ?: "An unknown error occurred")
        }
    }
}
```

### 15.2 ViewModel with Repository

```kotlin
data class WeatherUiState(
    val weather: WeatherResponse? = null,
    val isLoading: Boolean = false,
    val error: String? = null
)

class WeatherViewModel(
    private val repository: WeatherRepository
) : ViewModel() {

    private val _uiState = MutableStateFlow(WeatherUiState())
    val uiState: StateFlow<WeatherUiState> = _uiState.asStateFlow()

    companion object {
        const val API_KEY = "YOUR_API_KEY_HERE"
    }

    fun searchWeather(city: String) {
        if (city.isBlank()) return

        viewModelScope.launch {
            _uiState.update { it.copy(isLoading = true, error = null) }

            when (val result = repository.getWeatherByCity(city, API_KEY)) {
                is Result.Success -> {
                    _uiState.update {
                        it.copy(
                            weather = result.data,
                            isLoading = false,
                            error = null
                        )
                    }
                }
                is Result.Error -> {
                    _uiState.update {
                        it.copy(
                            isLoading = false,
                            error = result.message
                        )
                    }
                }
                is Result.Loading -> {
                    _uiState.update { it.copy(isLoading = true) }
                }
            }
        }
    }
}
```

---

[↑ Back to Top](#table-of-contents)

---

# PART 6: BUILDING THE WEATHER APP

**In This Part:**

- [Chapter 16: Project Setup](#chapter-16-project-setup)
- [Chapter 17: Complete Implementation](#chapter-17-complete-weather-app-implementation)
- [Chapter 18: Testing and Deployment](#chapter-18-testing-and-deployment)
- [Chapter 19: Next Steps and Enhancements](#chapter-19-next-steps-and-enhancements)

---

## Chapter 16: Project Setup

### 16.1 Project Structure

```
com.example.weatherapp/
├── data/
│   ├── model/
│   │   └── WeatherResponse.kt
│   ├── remote/
│   │   ├── WeatherApiService.kt
│   │   └── RetrofitInstance.kt
│   └── repository/
│       └── WeatherRepository.kt
├── ui/
│   ├── screen/
│   │   └── WeatherScreen.kt
│   ├── components/
│   │   ├── WeatherCard.kt
│   │   └── SearchBar.kt
│   └── theme/
│       ├── Color.kt
│       ├── Theme.kt
│       └── Type.kt
├── viewmodel/
│   └── WeatherViewModel.kt
└── MainActivity.kt
```

### 16.2 Getting OpenWeather API Key

1. Visit https://openweathermap.org/
2. Create a free account
3. Navigate to API Keys section
4. Copy your API key
5. Note: New API keys may take a few hours to activate

### 16.3 Complete build.gradle.kts

```kotlin
plugins {
    id("com.android.application")
    id("org.jetbrains.kotlin.android")
}

android {
    namespace = "com.example.weatherapp"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.example.weatherapp"
        minSdk = 24
        targetSdk = 34
        versionCode = 1
        versionName = "1.0"
    }

    buildFeatures {
        compose = true
    }

    composeOptions {
        kotlinCompilerExtensionVersion = "1.5.8"
    }

    kotlinOptions {
        jvmTarget = "17"
    }
}

dependencies {
    // Compose BOM
    val composeBom = platform("androidx.compose:compose-bom:2024.01.00")
    implementation(composeBom)

    // Compose
    implementation("androidx.compose.ui:ui")
    implementation("androidx.compose.material3:material3")
    implementation("androidx.compose.ui:ui-tooling-preview")
    implementation("androidx.activity:activity-compose:1.8.2")
    implementation("androidx.compose.material:material-icons-extended")

    // Lifecycle
    implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.7.0")
    implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.7.0")

    // Retrofit
    implementation("com.squareup.retrofit2:retrofit:2.9.0")
    implementation("com.squareup.retrofit2:converter-gson:2.9.0")
    implementation("com.squareup.okhttp3:logging-interceptor:4.12.0")

    // Coroutines
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.7.3")

    // Coil for image loading
    implementation("io.coil-kt:coil-compose:2.5.0")

    // Debug
    debugImplementation("androidx.compose.ui:ui-tooling")
}
```

### 16.4 AndroidManifest.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:theme="@style/Theme.WeatherApp"
        tools:targetApi="31">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

---

## Chapter 17: Complete Weather App Implementation

### 17.1 Data Models

Create `data/model/WeatherResponse.kt`:

```kotlin
package com.example.weatherapp.data.model

import com.google.gson.annotations.SerializedName

data class WeatherResponse(
    @SerializedName("name")
    val cityName: String,
    @SerializedName("main")
    val main: MainWeather,
    @SerializedName("weather")
    val weather: List<Weather>,
    @SerializedName("wind")
    val wind: Wind,
    @SerializedName("sys")
    val sys: Sys
)

data class MainWeather(
    @SerializedName("temp")
    val temperature: Double,
    @SerializedName("feels_like")
    val feelsLike: Double,
    @SerializedName("temp_min")
    val tempMin: Double,
    @SerializedName("temp_max")
    val tempMax: Double,
    @SerializedName("pressure")
    val pressure: Int,
    @SerializedName("humidity")
    val humidity: Int
)

data class Weather(
    @SerializedName("id")
    val id: Int,
    @SerializedName("main")
    val main: String,
    @SerializedName("description")
    val description: String,
    @SerializedName("icon")
    val icon: String
)

data class Wind(
    @SerializedName("speed")
    val speed: Double
)

data class Sys(
    @SerializedName("country")
    val country: String
)
```

### 17.2 API Service

Create `data/remote/WeatherApiService.kt`:

```kotlin
package com.example.weatherapp.data.remote

import com.example.weatherapp.data.model.WeatherResponse
import retrofit2.http.GET
import retrofit2.http.Query

interface WeatherApiService {
    @GET("weather")
    suspend fun getCurrentWeather(
        @Query("q") cityName: String,
        @Query("appid") apiKey: String,
        @Query("units") units: String = "metric"
    ): WeatherResponse
}
```

### 17.3 Retrofit Instance

Create `data/remote/RetrofitInstance.kt`:

```kotlin
package com.example.weatherapp.data.remote

import okhttp3.OkHttpClient
import okhttp3.logging.HttpLoggingInterceptor
import retrofit2.Retrofit
import retrofit2.converter.gson.GsonConverterFactory
import java.util.concurrent.TimeUnit

object RetrofitInstance {
    private const val BASE_URL = "https://api.openweathermap.org/data/2.5/"

    private val loggingInterceptor = HttpLoggingInterceptor().apply {
        level = HttpLoggingInterceptor.Level.BODY
    }

    private val client = OkHttpClient.Builder()
        .addInterceptor(loggingInterceptor)
        .connectTimeout(30, TimeUnit.SECONDS)
        .readTimeout(30, TimeUnit.SECONDS)
        .writeTimeout(30, TimeUnit.SECONDS)
        .build()

    val api: WeatherApiService by lazy {
        Retrofit.Builder()
            .baseUrl(BASE_URL)
            .client(client)
            .addConverterFactory(GsonConverterFactory.create())
            .build()
            .create(WeatherApiService::class.java)
    }
}
```

### 17.4 Repository

Create `data/repository/WeatherRepository.kt`:

```kotlin
package com.example.weatherapp.data.repository

import com.example.weatherapp.data.model.WeatherResponse
import com.example.weatherapp.data.remote.WeatherApiService

sealed class Result<out T> {
    data class Success<T>(val data: T) : Result<T>()
    data class Error(val message: String) : Result<Nothing>()
    object Loading : Result<Nothing>()
}

class WeatherRepository(
    private val apiService: WeatherApiService
) {
    suspend fun getWeatherByCity(
        city: String,
        apiKey: String
    ): Result<WeatherResponse> {
        return try {
            val response = apiService.getCurrentWeather(city, apiKey)
            Result.Success(response)
        } catch (e: Exception) {
            Result.Error(e.message ?: "An unknown error occurred")
        }
    }
}
```

### 17.5 ViewModel

Create `viewmodel/WeatherViewModel.kt`:

```kotlin
package com.example.weatherapp.viewmodel

import androidx.lifecycle.ViewModel
import androidx.lifecycle.viewModelScope
import com.example.weatherapp.data.model.WeatherResponse
import com.example.weatherapp.data.remote.RetrofitInstance
import com.example.weatherapp.data.repository.Result
import com.example.weatherapp.data.repository.WeatherRepository
import kotlinx.coroutines.flow.MutableStateFlow
import kotlinx.coroutines.flow.StateFlow
import kotlinx.coroutines.flow.asStateFlow
import kotlinx.coroutines.flow.update
import kotlinx.coroutines.launch

data class WeatherUiState(
    val weather: WeatherResponse? = null,
    val isLoading: Boolean = false,
    val error: String? = null
)

class WeatherViewModel : ViewModel() {
    private val repository = WeatherRepository(RetrofitInstance.api)

    private val _uiState = MutableStateFlow(WeatherUiState())
    val uiState: StateFlow<WeatherUiState> = _uiState.asStateFlow()

    companion object {
        const val API_KEY = "YOUR_API_KEY_HERE" // Replace with your API key
    }

    fun searchWeather(city: String) {
        if (city.isBlank()) return

        viewModelScope.launch {
            _uiState.update { it.copy(isLoading = true, error = null) }

            when (val result = repository.getWeatherByCity(city, API_KEY)) {
                is Result.Success -> {
                    _uiState.update {
                        it.copy(
                            weather = result.data,
                            isLoading = false,
                            error = null
                        )
                    }
                }
                is Result.Error -> {
                    _uiState.update {
                        it.copy(
                            isLoading = false,
                            error = result.message
                        )
                    }
                }
                is Result.Loading -> {
                    _uiState.update { it.copy(isLoading = true) }
                }
            }
        }
    }
}
```

### 17.6 Weather Screen UI

Create `ui/screen/WeatherScreen.kt`:

```kotlin
package com.example.weatherapp.ui.screen

import androidx.compose.foundation.layout.*
import androidx.compose.foundation.rememberScrollState
import androidx.compose.foundation.verticalScroll
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.filled.Search
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.text.font.FontWeight
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import androidx.lifecycle.viewmodel.compose.viewModel
import com.example.weatherapp.data.model.WeatherResponse
import com.example.weatherapp.viewmodel.WeatherViewModel
import kotlin.math.roundToInt

@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun WeatherScreen(
    viewModel: WeatherViewModel = viewModel()
) {
    var searchQuery by remember { mutableStateOf("") }
    val uiState by viewModel.uiState.collectAsState()

    Scaffold(
        topBar = {
            TopAppBar(
                title = { Text("Weather App") },
                colors = TopAppBarDefaults.topAppBarColors(
                    containerColor = MaterialTheme.colorScheme.primary,
                    titleContentColor = MaterialTheme.colorScheme.onPrimary
                )
            )
        }
    ) { paddingValues ->
        Column(
            modifier = Modifier
                .fillMaxSize()
                .padding(paddingValues)
                .padding(16.dp)
                .verticalScroll(rememberScrollState())
        ) {
            // Search Bar
            OutlinedTextField(
                value = searchQuery,
                onValueChange = { searchQuery = it },
                modifier = Modifier.fillMaxWidth(),
                label = { Text("Enter city name") },
                trailingIcon = {
                    IconButton(
                        onClick = { viewModel.searchWeather(searchQuery) }
                    ) {
                        Icon(Icons.Default.Search, "Search")
                    }
                },
                singleLine = true
            )

            Spacer(modifier = Modifier.height(24.dp))

            // Content
            when {
                uiState.isLoading -> {
                    Box(
                        modifier = Modifier.fillMaxSize(),
                        contentAlignment = Alignment.Center
                    ) {
                        CircularProgressIndicator()
                    }
                }

                uiState.error != null -> {
                    ErrorMessage(message = uiState.error!!)
                }

                uiState.weather != null -> {
                    WeatherContent(weather = uiState.weather!!)
                }

                else -> {
                    EmptyState()
                }
            }
        }
    }
}

@Composable
fun WeatherContent(weather: WeatherResponse) {
    Card(
        modifier = Modifier.fillMaxWidth(),
        elevation = CardDefaults.cardElevation(4.dp)
    ) {
        Column(
            modifier = Modifier
                .fillMaxWidth()
                .padding(24.dp),
            horizontalAlignment = Alignment.CenterHorizontally
        ) {
            // City name
            Text(
                text = "${weather.cityName}, ${weather.sys.country}",
                fontSize = 32.sp,
                fontWeight = FontWeight.Bold
            )

            Spacer(modifier = Modifier.height(8.dp))

            // Weather description
            Text(
                text = weather.weather.firstOrNull()?.description
                    ?.replaceFirstChar { it.uppercase() } ?: "",
                fontSize = 18.sp,
                color = MaterialTheme.colorScheme.onSurfaceVariant
            )

            Spacer(modifier = Modifier.height(24.dp))

            // Temperature
            Text(
                text = "${weather.main.temperature.roundToInt()}°C",
                fontSize = 72.sp,
                fontWeight = FontWeight.Bold
            )

            Spacer(modifier = Modifier.height(8.dp))

            Text(
                text = "Feels like ${weather.main.feelsLike.roundToInt()}°C",
                fontSize = 16.sp
            )

            Spacer(modifier = Modifier.height(32.dp))

            // Additional info
            Row(
                modifier = Modifier.fillMaxWidth(),
                horizontalArrangement = Arrangement.SpaceEvenly
            ) {
                WeatherInfoItem(
                    label = "Min",
                    value = "${weather.main.tempMin.roundToInt()}°C"
                )
                WeatherInfoItem(
                    label = "Max",
                    value = "${weather.main.tempMax.roundToInt()}°C"
                )
                WeatherInfoItem(
                    label = "Humidity",
                    value = "${weather.main.humidity}%"
                )
            }

            Spacer(modifier = Modifier.height(16.dp))

            Row(
                modifier = Modifier.fillMaxWidth(),
                horizontalArrangement = Arrangement.SpaceEvenly
            ) {
                WeatherInfoItem(
                    label = "Pressure",
                    value = "${weather.main.pressure} hPa"
                )
                WeatherInfoItem(
                    label = "Wind",
                    value = "${weather.wind.speed} m/s"
                )
            }
        }
    }
}

@Composable
fun WeatherInfoItem(label: String, value: String) {
    Column(
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text(
            text = label,
            fontSize = 14.sp,
            color = MaterialTheme.colorScheme.onSurfaceVariant
        )
        Text(
            text = value,
            fontSize = 18.sp,
            fontWeight = FontWeight.SemiBold
        )
    }
}

@Composable
fun ErrorMessage(message: String) {
    Card(
        modifier = Modifier.fillMaxWidth(),
        colors = CardDefaults.cardColors(
            containerColor = MaterialTheme.colorScheme.errorContainer
        )
    ) {
        Text(
            text = message,
            modifier = Modifier.padding(16.dp),
            color = MaterialTheme.colorScheme.onErrorContainer
        )
    }
}

@Composable
fun EmptyState() {
    Column(
        modifier = Modifier.fillMaxWidth(),
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Text(
            text = "Search for a city to see the weather",
            fontSize = 18.sp,
            color = MaterialTheme.colorScheme.onSurfaceVariant
        )
    }
}
```

### 17.7 MainActivity

```kotlin
package com.example.weatherapp

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.Surface
import androidx.compose.ui.Modifier
import com.example.weatherapp.ui.screen.WeatherScreen
import com.example.weatherapp.ui.theme.WeatherAppTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            WeatherAppTheme {
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = MaterialTheme.colorScheme.background
                ) {
                    WeatherScreen()
                }
            }
        }
    }
}
```

---

## Chapter 18: Testing and Deployment

### 18.1 Running the App

**Steps:**

1. **Replace API Key**: Open `WeatherViewModel.kt` and replace `YOUR_API_KEY_HERE` with your actual OpenWeather API key

2. **Connect Device/Emulator**:
   - Physical device: Enable USB debugging
   - Emulator: Start from AVD Manager

3. **Run**: Click the green play button in Android Studio

4. **Test**: Enter a city name and press search

### 18.2 Common Issues and Solutions

**Network Error:**

- Ensure INTERNET permission is in AndroidManifest.xml
- Check your internet connection
- Verify Retrofit configuration

**API Key Error:**

- Verify your API key is correct
- Wait a few hours after generating a new API key
- Check OpenWeather API status

**Build Errors:**

- Sync project with Gradle files (File → Sync Project)
- Clean and rebuild (Build → Clean Project, then Build → Rebuild)
- Invalidate caches (File → Invalidate Caches / Restart)

**App Crashes:**

- Check Logcat for error messages
- Verify all dependencies are correct
- Ensure minimum SDK is 24 or higher

### 18.3 Debugging Tips

```kotlin
// Add logging to track API calls
private val loggingInterceptor = HttpLoggingInterceptor().apply {
    level = HttpLoggingInterceptor.Level.BODY
}

// Add try-catch in ViewModel
try {
    val result = repository.getWeatherByCity(city, API_KEY)
    Log.d("WeatherViewModel", "Result: $result")
} catch (e: Exception) {
    Log.e("WeatherViewModel", "Error: ${e.message}", e)
}
```

---

## Chapter 19: Next Steps and Enhancements

### 19.1 Potential Enhancements

**Feature Enhancements:**

1. **Location Support**
   - Add location permission
   - Get weather for current location
   - Auto-detect city

2. **5-Day Forecast**
   - Use OpenWeather forecast API
   - Display forecast in LazyRow
   - Show hourly temperatures

3. **Favorite Cities**
   - Implement Room database
   - Save/delete favorite cities
   - Quick access to saved locations

4. **Weather Icons**
   - Load icons from OpenWeather API
   - Use Coil for image loading
   - Custom weather animations

5. **Unit Conversion**
   - Toggle between Celsius/Fahrenheit
   - Save user preference
   - Update UI dynamically

6. **Pull to Refresh**
   - Implement SwipeRefresh
   - Auto-refresh every N minutes
   - Show last update time

7. **Dark Mode**
   - Implement dynamic theming
   - System theme detection
   - Manual theme toggle

8. **Animations**
   - Add transition animations
   - Animated weather icons
   - Smooth state changes

### 19.2 Code Quality Improvements

**Testing:**

```kotlin
class WeatherViewModelTest {
    @Test
    fun `searchWeather updates state correctly`() = runTest {
        val viewModel = WeatherViewModel()
        viewModel.searchWeather("London")

        val state = viewModel.uiState.value
        assert(state.isLoading || state.weather != null || state.error != null)
    }
}
```

**Dependency Injection:**

```kotlin
// Using Hilt
@HiltViewModel
class WeatherViewModel @Inject constructor(
    private val repository: WeatherRepository
) : ViewModel()
```

**Error Handling:**

```kotlin
sealed class UiState<out T> {
    object Idle : UiState<Nothing>()
    object Loading : UiState<Nothing>()
    data class Success<T>(val data: T) : UiState<T>()
    data class Error(val message: String, val throwable: Throwable? = null) : UiState<Nothing>()
}
```

### 19.3 Learning Resources

**Official Documentation:**

- Android Developers: developer.android.com
- Kotlin: kotlinlang.org
- Jetpack Compose: developer.android.com/jetpack/compose
- Retrofit: square.github.io/retrofit

**Online Courses:**

- Android Basics with Compose (Google)
- Kotlin for Android Developers (Udacity)
- Advanced Android Development (Coursera)

**Community:**

- r/androiddev on Reddit
- Stack Overflow
- Android Dev Discord
- Kotlin Slack

**Best Practices:**

- Follow Material Design guidelines
- Write clean, maintainable code
- Use meaningful variable names
- Comment complex logic
- Test your code
- Keep dependencies updated

### 19.4 Performance Optimization

**Tips:**

- Use LazyColumn for large lists
- Implement pagination
- Cache network responses
- Optimize images
- Minimize recompositions
- Use remember and derivedStateOf
- Profile with Android Profiler

---

## Conclusion

🎉 **Congratulations!** You've completed the Kotlin to Android Development Handbook. You've learned:

✅ Kotlin fundamentals (variables, functions, OOP, coroutines)  
✅ Android architecture and components  
✅ Jetpack Compose for modern UI development  
✅ MVVM architecture pattern  
✅ Networking with Retrofit  
✅ Building a complete Weather App

### 🎯 Your Journey Doesn't End Here

**Next Steps:**

1. ⭐ **Star this repo** if you found it helpful!
2. 🔨 Build more projects to practice
3. 📚 Explore advanced topics (Room, WorkManager, Navigation)
4. 🤝 Contribute to open-source projects
5. 💬 Join the Android community
6. 🔄 Keep learning and stay updated

### 🔗 Useful Links

**Official Documentation:**

- [Android Developers](https://developer.android.com/) - Official Android documentation
- [Kotlin Language](https://kotlinlang.org/) - Kotlin programming language
- [Jetpack Compose](https://developer.android.com/jetpack/compose) - Modern UI toolkit
- [Retrofit](https://square.github.io/retrofit/) - Type-safe HTTP client

**Learning Resources:**

- [Android Codelabs](https://developer.android.com/courses) - Hands-on tutorials
- [Kotlin Koans](https://play.kotlinlang.org/koans) - Interactive Kotlin exercises
- [Compose Pathway](https://developer.android.com/courses/pathways/compose) - Compose learning path

**Community:**

- [r/androiddev](https://www.reddit.com/r/androiddev/) - Reddit community
- [Stack Overflow](https://stackoverflow.com/questions/tagged/android) - Q&A
- [Android Dev Discord](https://discord.gg/android) - Chat community
- [Kotlin Slack](https://kotlinlang.slack.com/) - Kotlin discussions

### 📝 Contributing

Found a typo or want to improve this handbook? Contributions are welcome!

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

### 💡 Remember

> "The best way to learn programming is by building projects. Don't just read the code—type it out, break it, fix it, and make it your own!"

**Happy Coding! 🚀**

---

### 📄 License

This handbook is open-source and available under the MIT License.

---

**Made with ❤️ for the Android community**

[↑ Back to Top](#table-of-contents)

---

## Appendix: Quick Reference

### A. 📝 Kotlin Cheat Sheet

```kotlin
// Variables
val immutable = "value"
var mutable = 0

// Functions
fun greet(name: String) = "Hello, $name"

// Null Safety
val nullable: String? = null
val length = nullable?.length ?: 0

// Collections
val list = listOf(1, 2, 3)
val map = mapOf("key" to "value")

// Coroutines
viewModelScope.launch {
    withContext(Dispatchers.IO) {
        // Background work
    }
}
```

### B. 🎨 Compose Cheat Sheet

```kotlin
// Basic Components
Text("Hello")
Button(onClick = {}) { Text("Click") }
Image(painter = painterResource(R.drawable.icon), contentDescription = null)

// Layouts
Column { /* Vertical */ }
Row { /* Horizontal */ }
Box { /* Overlapping */ }

// State
var count by remember { mutableStateOf(0) }
val state by viewModel.uiState.collectAsState()

// LazyColumn
LazyColumn {
    items(list) { item ->
        Text(item)
    }
}
```

### C. 📦 Common Gradle Dependencies

```kotlin
// Compose
implementation("androidx.compose.ui:ui")
implementation("androidx.compose.material3:material3")
implementation("androidx.activity:activity-compose")

// Lifecycle
implementation("androidx.lifecycle:lifecycle-viewmodel-compose")

// Retrofit
implementation("com.squareup.retrofit2:retrofit")
implementation("com.squareup.retrofit2:converter-gson")

// Coroutines
implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android")
```

---

**Version:** 1.0  
**Last Updated:** February 2026  
**Author:** Android Development Community

---
