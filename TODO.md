# TODO
- round numbers to 2 decimal places only in the output, not during runtime calculations
- solve the issue of topological cycle in
```
agent entity 1 {
    property a: 0 = b + 1;
    property b = a + 2;
}
```
