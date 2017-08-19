# Mixing It Up With Elixir
##


## Level 1
- Functions are first class citizens
- Which means:
	1. Functins can be assigne to varibales
	2. Functions can be passed around to other arguments.
- *Anonymous Functions* have no name and no module.
- These are declared using `fn -> ....    end`.
- `fn( .., .., ..)` is how you pass variables to the anonymous function
- To call an anonymous function, you use `func_name.(.., .., ..)`
- Anonymous functions can allow be conditioned on atoms.
- Since anonymous functions are used so often, there is a short hand version of declaring them.
```elixir
deposit = fn( balance, amount ) -> balance + amount end # this is equal to
deposit = &(&1 + &2)                                    # this.
```
- Anonymous functions can be declared inline.

## Level 2
- The *Cons* operator splits a list into two parts: head, tail where head is the first element of the list.
- You can use `_` to collect the tail and ignore it.
- There are no for loops in Elixir.
- I know what recursion is.

## Level 3
- We use `{}` to represent *Tuples*.
- Tuples can be multi-data typed.
- The most common type of tuple is where elemnt one is an atom and element two is variable.
- ` {status, content} = {:ok, "content"}
- Elixir allows one to pass Keyword lists at the end of functions.
- The format is `atom: "value"` and is converted to `[{:atom, value}]` internally.
- The internal key-list pair is list is called options.
- You can assign a default value using `\\` in a call to a function.
- Logical OR is the same as most languages.
- Maps are what would be refered to in Python as a dictionary.
- They're the structure of key,value pairs.
- The definition looks like `%{ "name" => "Brooke", "Age" = 49}`.
- You can read maps with `Map.fetch()`.
- If you call `Map.fetch!( map, 'key')` then you only get the value back.
- if the key is not found then you get an explicit error message.
- Unlike tuples, we don't need to refer to elements we don't care about in a map.
- You can imbed maps inside maps.

## Level 4
- Elixir has case statements.
- Syntax is:
```elixir
case variable do
	:ok -> "do something"
	:error -> "do something else"
end
```
- case can accept functions to test and tuples as cases.
- case statements also have something called *Guards* which act like conditional limits on case statements.
- So, an input can match but fail the guard passing on to a similar but different expression.
```elixir
...
{:ok, content }
	when byte_size( content ) > 10 -> ...
{:ok, content }
```
- You can get the hour of the day using `hourOfDay = Datetime.utc_now.hour`.
- The `cond` statement checks multiple conditions and uses the first true value it finds.
```elixir
cond do
	hourOfDay < 12 -> ...
	hourOFDay < 18 -> ...
	true -> ...
end
```
- It is common practice to have the last statement be a explicit `true ->` statement to ensure cond does not error out.

## Level 5
- Elixir has it's own build tool called *Mix*.
- The command to create a new project is `mix new <project>`.
- You can run code in the context of the application using `mix run -e "command to run"`.
- .ex files are for production; .exs are for scripts.
- `Budget.Conversion` just means "look in folder Budget for .ex file called Conversion".
- You declare dependencies inside of the mix.exs file.
```elixir
# ...
defp deps do
	[{:httpoison, "~> 0.10.0"}, {:poison, "~> 3.0"}]
end
```
- To then install the dependencies listed call `mix deps.get`.
- `defp` means private function.
- `raise` is how you request a full stop error.



## Reseach 
- mix help

## Resources
- elixir-lang.org
- dave