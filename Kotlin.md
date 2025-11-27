- printing a simple line:
```kotlin
fun main() {
    println("Hello, world!")
    // Hello, world!
}
```
- fun in used to declare a function
- Read-only variable: val (cant change it)
- mutable(changable) variable: var
- To evaluate a piece of code in a template expression, place the code within curly braces `{}` after the dollar sign `$`.
```kotlin
val customers = 10
println("There are $customers customers")
// There are 10 customers

println("There are ${customers + 1} customers")
// There are 11 customers
```
