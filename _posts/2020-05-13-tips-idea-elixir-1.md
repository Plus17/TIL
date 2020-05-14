---
title: Tips to work with elixir in idea part 1
tags:
- idea, elixir
desc: Tips to work with elixir in idea ide part 1
layout: post
---

Snippets (Live Templates)

1.- Define public function. Abbreviation: def
```
@doc """
$DOC$
"""
@spec $NAME$($TYPE$) :: $RETURN$
def $NAME$($ARG$) do
  $END$
end
```

2.- Define private function. Abbreviation: defp
```
# $DOC$
@spec _$NAME$($TYPE$) :: $RETURN$
defp _$NAME$($ARG$) do
  $END$
end
```

3.- Module test when you use ex machina. Abbreviation: defmt
```
defmodule $MODULNAME$Test do
  use $MODULNAME$.DataCase

  import $MODULNAME$.Factory
end
```

4.- Inspect values. Abbreviation: insp
```
|> IO.inspect(label: "$LABEL$")
```
