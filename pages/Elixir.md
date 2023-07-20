- ```elixir
  IO.puts("Hello world !") 
  
  # Same as IO.puts but do not add a new line at the end
  IO.write("Hello world !")
  ```
- Interactive [[Elixir]] Session
  collapsed:: true
	- ``iex``
- Help
	- ``h``
- Kernel is [[Elixir]]'s default environment
- In [[Elixir]], (almost) everything is a function
- ```elixir 
  # To know the type of something
  i("toto")
  ```
-
- ### A REVOIR
	- iex(40)> Enum.with_index(list, fn(element, index) -> IO.puts("Voici le #{index} #{element}") end)
- ----
- #### Reading values
	- ```elixir 
	  name = IO.gets("Salut, comment tu t'appelles ? ")
	  IO.write("Salut " <> name)
	  ```
- ----
- #### Atom (unique)
	- An ***atom*** type represents a fixed constant. The ***atom*** value is simply its own name.
	  id:: 6448c94a-d81d-46fa-a2ab-70f84d0b624b
	- ```elixir 
	  # All atoms are preceded with a ':'
	  variable = :an_atom
	  ```
- #### Cond
	- ***Cond*** follows the first path that evaluates to `true`. If no path evaluates to `true`, an error is raised by the runtime.
	- ```elixir 
	  cond do
	    x > 10 -> :this_might_be_the_way
	    y < 7 -> :or_that_might_be_the_way
	    true -> :this_is_the_default_way
	  end
	  ```
- #### _ (Underscore)
	- When there is a `_` instead of a variable or a value, it means the value will be ignored and any value will be accepted
	- ```elixir
	  {_, denominator} = Float.ratio(0.25)
	  # => {1, 4}
	  # the variable `denominator` is bounded to the value 4
	  ```
	- ```elixir 
	  [1, _, 3] = [1, "toto", 3]
	  # => [1, "toto", 3]
	  ```
- #### Sigils ( symbols with magical powers )
	- >A sigil is an alternative syntax for representing and working with literals
	- >A sigil starts with a tilde (~), followed by an upper- or lowercase letter, some delimited content, and perhaps some options
	- > The delimiters can be <...>, {...}, [...], (...), |...|, /.../, "...", and '...'
	- >The letter determines the sigil’s type:
	  ~***C*** character [[list]] with no escaping or interpolation
	  ~***c*** character [[list]], escaped and interpolated just like a single-quoted string
	  ~***D*** Date in the format yyyy-mm-dd
	  ~***N*** naive (raw) DateTime in the format yyyy-mm-dd hh:mm:ss[.ddd]
	  ~***R*** regular expression with no escaping or interpolation
	  ~***r*** regular expression, escaped and interpolated
	  ~***S*** string with no escaping or interpolation
	  ~***s*** string, escaped and interpolated just like a double-quoted string
	  ~***T*** Time in the format hh:mm:ss[.dddd]
	  ~***W*** [[list]] of whitespace-delimited words, with no escaping or interpolation
	  ~***w*** [[list]] of whitespace-delimited words, with escaping and interpolation
	  ~***H*** is for writing [[HEEx]] templates inside source files
- #### Capture operator
	- ```elixir 
	  greeting = fn (name) -> "Hello #{name}!" end
	  # Same as
	  captured_greeting = &("Hello #{&1}!")
	  ```
	- ```elixir 
	  greeting = fn (name, gender, age) ->
	  	"Hello, #{name}! I see you're #{gender} and you're #{age} years old."
	  end
	  # Same as
	  captured_greeting = &("Hello, #{&1}! I see you're #{&2} and you're #{&3} years old.")
	  ```
- ----
- > In [[Elixir]], values are not modified. Values are transformed on output.
	- Example :
	- ```elixir
	  name = "Toto"
	   
	  if (name == "Toto") do
	    IO.puts("Inside condition before being changed: " <> name)
	    name = "Robin"
	    IO.puts("Inside condition after being changed: " <> name)
	  end
	   
	  IO.puts("Outside condition after being changed: " <> name)
	  ```
	- Output :
	- ```elixir
	  Inside condition before being changed: Toto
	  Inside condition after being changed: Robin
	  Outside condition after being changed: Toto
	  ```
	- Example with date :
	- ```elixir
	  d1 = ~D[2023-04-25]
	   
	  IO.puts(d1)
	  IO.puts(Date.add(d1, 5))
	  IO.puts(d1)
	  ```
	- Output :
	- ```elixir
	  2023-04-25
	  2023-04-30
	  2023-04-25
	  ```
- > Functions not only differ by name, but also by the number of arguments that they take.
- ----
- ### [[list]] VS [[tuple]]
	- ```elixir
	  [1, 2, "a"]	# list
	  {1, 2, "a"}	# tuple
	  ```
- ----
- #### Multiple clause functions
	- ```elixir 
	  defmodule GuessingGame do
	    # Default argument, if no guess value is given
	    def compare(secret_number, guess \\ :no_guess)
	    def compare(_secret_number, :no_guess), do: "Make a guess"
	    
	    def compare(secret_number, guess) when guess == secret_number, do: "Correct"
	    def compare(secret_number, guess) when abs(guess - secret_number) == 1, do: "So close"
	    def compare(secret_number, guess) when guess > secret_number, do: "Too high"
	    def compare(secret_number, guess) when guess < secret_number, do: "Too low"
	  end
	  ```
- ----
- ### A COMPLETER
- ### Pattern matching
	- https://thinkingelixir.com/course/pattern-matching/
-
- ----
-