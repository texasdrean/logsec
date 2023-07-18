- #elixir
- ```elixir 
  [1, 2, "a"]
  ```
- [[Elixir]] lists are a series of nodes where each node holds a piece of data and a pointer to the next node. The final node points to nothing.
-
- This has performance implications. In order to read the final element in a list, you must traverse every element from the head to the tail of the list! Prepending an element to the front of the list is cheap, O(1), but accessing an element at the end is O(n)
-
- Definition of a [[list]]
	- > A [[list]] may either be empty or consist of a `head` and a `tail`. The head contains a value and the tail is itself a [[list]]
	- To get the `length` of the [[list]], we take off the `head` and `add` 1 to the length of the `tail` at each step
		- ```elixir 
		  len([11,12,13,14,15])
		  = 1 + len([12,13,14,15])
		  = 1 + 1 + len([13,14,15])
		  = 1 + 1 + 1 + len([14,15])
		  = 1 + 1 + 1 + 1 + len([15])
		  = 1 + 1 + 1 + 1 + 1 + len([]) =1+1+1+1+1+0
		  =5
		  ```
	- `add` several items to a [[list]] :
		- ```elixir 
		  [item | list_name]
		  ```
	- `remove` the first item from a [[list]] :
		- ```elixir
		  List.delete_at(list, 0)
		  ```
	- `get` the first item from a [[list]] :
		- ```elixir 
		  List.first(list)
		  ```
	- `get` the [[list]] length :
		- ```elixir 
		  length(list)
		  ```
	- item in [[list]] :
		- ```elixir 
		  "Elixir" in (list)
		  ```