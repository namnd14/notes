Varargs Java 5

=> support an arbitrary number of parameters of one type.

public String formatWithVarArgs(String... values) {
    // ...
}

formatWithVarArgs();
formatWithVarArgs("a", "b", "c", "d");
// both are valid

Rule:
- Each method can only have one varargs parameter
- The varargs argument must be the last parameter

Using varargs can lead to so-called Heap Pollution
=> Refer heap-pollution-java page for more detailed