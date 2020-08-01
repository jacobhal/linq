# C# tips

## yield return
The yield keyword signals to the compiler that the method in which it appears is an iterator block.  The compiler generates a class to implement the behavior that is expressed in the iterator block. In the iterator block, the yield keyword is used together with the return keyword to provide a value to the enumerator object. This is the value that is returned, for example, in each loop of a foreach statement. The yield keyword is also used with break to signal the end of iteration.

> yield creates a state machine "under the covers" that remembers where you were on each additional cycle of the function and picks up from there.

```cs
// BEFORE
public static IEnumerable func(int start, int number) {
    int[] _number = new int[number];
    for (int i = 0; i < number; i++) {
        _number[i] = start + 2 * i
    }

    return _number;
}

// AFTER
public static IEnumerable func(int start, int number) {
    for (int i = 0; i < number; i++) {
        yield return start + 2 * i
    }
}

```
