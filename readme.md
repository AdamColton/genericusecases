## Specific Use Cases for Generics in Go
Taken from [this thread](https://www.reddit.com/r/golang/comments/6nh418/generics_specific_use_cases/?ref=share&ref_source=link).

If you wish to add anything consistent with the guidelines in that thread,
either post it there or open a pull request.

### GoDS
Nominated by floatdouble: [Go Data Structures](https://github.com/emirpasic/gods)

#### Example
Provided by callcifer
```Go
type Set<T> struct {
    Add(element T)
    Remove(element T)
    Contains(elements T) bool
}

func main() {
    mySet := new(Set<int>)

    mySet.Add(1) // works
    mySet.Add("1") // compile error

    var foo interface{}
    foo = 1
    mySet.Add(foo) // also compile error

    mySet.Add(foo.(int)) // compiles and works fine, but potentially a panic risk at runtime
}
```