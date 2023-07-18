- #Elixir
- ```elixir 
  {1, 2, "a"}
  ```
- [[Elixir]] tuples are stored contiguously in memory. Accessing any element is fast. On the down-side, inserting or deleting an element involves copying the entire [[tuple]], which is slow.
- Remember, like everything else in the language, Tuples are immutable!
-
- Definition of a [[tuple]]
	- > A [[tuple]] is a data structure which organizes data. They are not usually used when elements may need to be added/removed but rather for memory read-intensive operations, since read-access of an element is a constant-time operation.