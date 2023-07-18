- On [[Phoenix]] - [[Elixir]], to display the changeset errors :
	- On view
		- ```elixir 
		  <%= form_for @changeset, ~p"/posts", fn f -> %>
		    <%= if @changeset.errors[:title] do %>
		      <.error :if={@changeset.action}>
		        <%= @changeset.errors[:title] |> elem(0) %>
		      </.error>
		    <% end %>
		  
		    <label class="posts" for="title">
		      Title : <%= text_input(f, :title) %>
		    </label>
		  
		    <%= if @changeset.errors[:description] do %>
		      <.error :if={@changeset.action}>
		        <%= @changeset.errors[:description] |> elem(0) %>
		      </.error>
		    <% end %>
		  
		    <label class="posts" for="description">
		      Description : <%= text_input(f, :description) %>
		    </label>
		  
		    <%= submit("Submit") %>
		  <% end %>
		  
		  ```