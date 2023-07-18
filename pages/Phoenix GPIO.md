- https://github.com/elixir-circuits/circuits_gpio
- https://github.com/nerves-project/nerves_examples/blob/main/hello_gpio/README.md
-
- Droits -> acdsn dans groupe gpio
-
- Put in mix.exs file
	- ```elixir 
	    def deps do
	      [{:circuits_gpio, "~> 1.0"}]
	    end
	  ```
-
- {:ok, gpio26} = Circuits.GPIO.open(26, :output)
- Circuits.GPIO.write(gpio26, 0)