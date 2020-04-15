---
title: Map to Keyword list in Elixir
tags:
desc: How to convert a map into a keyword list with Elixir
layout: post
---

Useful for [Keyword filters](https://hexdocs.pm/ecto/Ecto.Query.html#where/3-keywords-example)

```elixir
iex > map = %{"country" => "Sweden"}
iex > Enum.map(map, fn({key, value}) -> {String.to_atom(key), value} end)
[country: "Sweden"]
```
