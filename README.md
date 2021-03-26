# Golang proposal for declearing variable in outer scope in `if` statement 
Golang proposal for declaring variable for the outer scope in an "if" statement

## Spec

```
IfStmt = "if" ( [ SimpleStmt ";" ] Expression | SimpleStmt ";" Expression ";" ShortVarDecl ) Block [ "else" ( IfStmt | Block ) ] .
```

## Usage

### Scoping `error` within `if` statement when invoking functions that return more than one result

```go
if t, err := time.Parse(time.RFC3339, "2006-01-02T15:04:05Z"); err != nil; t := t{
    return nil, err
}

fmt.Prinln(t) // 2006-01-02 15:04:05 +0000 UTC
fmt.Println(err) // undefined
```

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

## Short handed var decl

```go
func f() (string, error) {
    return "aaa", nil
}

if a, b := f(); b != nil; a {
    return errors.Wrap(b, "error"}
}

fmt.Printf("%v", a) //print "aaa"
fmt.Printf("%v", b) //undefined
```
