In the Java programming language, heap pollution is a situation that arises when a variable of a parameterized type refers to an object that is not of that parameterized type. This situation is normally detected during compilation and indicated with an unchecked warning. Later, during runtime heap pollution will often cause a ClassCastException.

Heap pollution in Java can occur when type arguments and variables are not reified at run-time. As a result, different parameterized types are implemented by the same class or interface at run time. All invocations of a given generic type declaration share a single run-time implementation. This results in the possibility of heap pollution.

Under certain conditions, a variable of a parameterized type may refer to an object that is not of that parameterized type. The variable will always refer to an object that is an instance of a class that implements the parameterized type.

Example:

````
static String firstOfFirst(List<String>... strings) {
    List<Integer> ints = Collections.singletonList(42);
    Object[] objects = strings;
    objects[0] = ints; // Heap pollution

    return strings[0].get(0); // ClassCastException
}
````

2.

````
    static <T> T[] toArray(T... arguments) {
        return arguments;
    }

    static <T> T[] returnAsIs(T a, T b) {
        return toArray(a, b);
    }

    String[] args = returnAsIs("One", "Two"); => // ClassCastException
````

Explain:
- To pass a and b to the toArray method, Java needs to create an array
- Since the Object[] can hold items of any type, the compiler creates one
- The toArray method returns the given Object[] to the caller
- Since the call site expects a String[], the compiler tries to cast the Object[] to the expected String[], hence the ClassCastException

3.
````
public class HeapPollutionDemo
{
    public static void main(String[] args)
    {
        Set s = new TreeSet<Integer>();
        Set<String> ss = s;              // unchecked warning
        s.add(new Integer(42));          // another unchecked warning
        Iterator<String> iter = ss.iterator();

        while (iter.hasNext())
        {
            String str = iter.next();    // ClassCastException thrown
            System.out.println(str);
        }
    }
}
````
