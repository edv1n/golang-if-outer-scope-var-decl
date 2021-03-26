# Golang proposal for declearing variable in outer scope in `if` statement 
Golang proposal for declaring variable for the outer scope in an "if" statement

## Example

```go
func f() (string, error) {
    return "aaa", nil
}

if a, b := f(); b != nil; outerVar := a {
    return errors.Wrap(b, "error"}
}

fmt.Printf("%v", a) //undefined
fmt.Printf("%v", b) //undefined
fmt.Printf("%v", outerVar) // print "aaa"
```
