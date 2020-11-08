# Understanding functions and it's ways in JavaScript

### References

- [javascript.info](https://javascript.info/function-basics)

- #### Function Declaration

```
function showMessage() {
  alert( 'Hello everyone!' );
}
```

- #### Functions with default parameters

```
function showMessage(from, text = "no text given") {
  alert( from + ": " + text );
}

showMessage("Ann"); // Ann: no text given
```
