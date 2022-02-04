---
title: Register atoms with on_load hook
tags: elixir
desc: Register atoms with on_load hook in Elixir
layout: post
---

Using [@on_load](https://hexdocs.pm/elixir/1.13/Module.html#module-on_load) hook we can “register” atoms.  This is useful for example when you use `:atoms!` for `keys` option in `Jason.decode/2`. This uses  `String.to_existing_atom/1` that raise if atom doesn’t exists.

```elixir
Jason.decode(json_string, keys: :atoms!)
```

If you expect to decode some keys not used yet in other parts of your app you can register them in a module:

```elixir
defmodule MyModule do
  @moduledoc false

  @on_load :load_atoms

  def load_atoms() do
    Enum.each [:unused, :keys], &Code.ensure_loaded?/1
    :ok
  end
end
```
