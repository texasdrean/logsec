- > `HEEx` stands for "HTML + [[EEx]]"
  * It is a Phoenix extension of [[EEx]] that is HTML aware, with support for HTML validation, components, and automatic escaping of values. The latter protects you from security vulnerabilities like Cross-Site-Scripting with no extra work on your part.
- > It provides:
  * Built-in handling of HTML attributes
  * An HTML-like notation for injecting function components
  * Compile-time validation of the structures of the template
  * The ability to minimize the amount of data sent over the wire
  * Out-of-the-box code formatting via mix format
- #### Example
	- ```elixir 
	  ~H"""
	  <div title="My div" class={@class}>
	    <p>Hello <%= @name %></p>
	    <MyApp.Weather.city name="Kraków"/>
	  </div>
	  """
	  ```