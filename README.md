# C# Type Traits

Exploration of an idea of C# Type Traits (type functions that return values, as in C++).

## Suggested Interface

```
  T Reduce<T>(T[] data)
  {
      return data.Aggregate(Traits<T>.Zero, Traits<T>.Add);
  }
  
  T[] Iota<T>(T start, int count)
  {
      var result = new T[count];
      for (int i = 0; i < result.Length; i++)
      {
          result[i] = start;
          start = Traits<T>.Increment(start);
      }
      return result;
  }
```

## Possible Traits

* Default value AKA default(T)
* Multiplicative 1
* Basic arithmetic (incr, decr, +-/*, comparison)
* Read to/from byte array
* Size?
* ???

## Examples (todo)

* Develop a fast exponentiation mechanism and use it on integers, matrices, and maybe strings?
* Generic LCD algorithm

## Concepts (WIP)

* Not all data types have all traits defined. We want algorithms to check this before execution.
We can put related traits in groups called Concepts, and algorithms can concept-check the types before running.
