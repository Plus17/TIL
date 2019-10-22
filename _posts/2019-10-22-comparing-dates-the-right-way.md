---
title: Comparing Dates the right way in Elixir
tags:
desc: Comparing Dates the right way
layout: post
---

What's the wrong way? is use the operator `<` or `>`
<!-- more -->


```elixir
late_january = ~D[2019-01-30]
early_may = ~D[2019-02-01]
```

if you compare this using `<` the result is:

```elixir
iex(1)> early_may < late_january
true
```

the result is clearly incorrect.

The rigth way

```elixir
iex(39)>  Date.compare(early_may, late_january)
:gt
```

`early_may` is greater than `late_january`

The same apply for DateTime or NaiveDateTime.
