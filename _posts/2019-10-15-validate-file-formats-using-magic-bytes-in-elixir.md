---
title: Validate file formats in Elixir
tags:
desc: Validate file formats using magic bytes in elixir.
layout: post
---

You can validate an image by the binary to determine what format is. For example:
<!-- more -->

```elixir
defmodule MyApp.ImageValidation do

  # Helper functions to read the binary to determine the image extension

  def is_png?(<<0x89, 0x50, 0x4E, 0x47, 0x0D, 0x0A, 0x1A, 0x0A, _::binary>>), do: true

  def is_png?(_image), do: false

  def is_jpg?(<<0xff, 0xD8, _::binary>>), do: true

  def is_jpg?(_image_), do: false

end
```

See more in [File signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)
