# Try Elixir
##

## Level 1
- What is Elixer: .. Is a programming language created in 2012 designed to build scalable and maintainable applications.
- Main features:
	- Functions and modules.
	- No objects nor classes
	- Dynamic Languages
	- Compiled
	- Distributed and Concurrent
	- Runs on the Earlang VM ( *Beam* )
- .. is a general purpose language that can be used for:
	- Data processing.
	- Networking Applications.
	- High Availability systems.
- Functional programming is all about computations of functions on data.
- All named functions in .. must be contained inside of a enclosing module.
- Files end with .exs.
- You declare a new module using `defmodule`.
- You declare a new function using `def`.
- An example function is:
```elixir
def balance( initial, spending) do
	initial - spending
end
```
- Elixer does not have a return call and uses the last line in a function instead.
- Named functions are called using the dot notation.
- You can write to the console using `IO.puts "stuff to dump"`
- Elixer inserts a variable into a string using the format `#{variable_name}`.
- In order to determine if a function is pure, we look for:
	1. Return values must only depend on arguments it receives.
	2. No side effects.
- Pure functions make reasoning about programs easier.

## Level 2
- A common mistake is to write too many nested functions.
- `defmodule` acts as a **collector of a subset of functions**.
- Elixir minimizes readability issues by using a pipe operator `|>`.
- It passes the left side computed value to the first argument to the call on the right.
- For readability, it is best to break each pipe onto its own line with the pipe operator on the start of the line.
- Creating a range in Elixir can be done using `1..10`.

## Level 3
- `=` is calle the *Match Operator* in Elixir and behaves different.
- `<>` is for string concatination in Elixir.
```elixir
"Jose " <> last_name = "Jose Valim"
IO.put last_name # returns "Valim"
```
- Use `[]` to specify a list.
- Elixir has something called *Atoms* which are a datatype similar to strings but more memory efficient.
- The format for an atom is `:atom`.
- You can include the atom in a function definition so that Elixir does efficient "overloading".