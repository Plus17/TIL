---
title: Generate Azure SAS Token with elixir
tags:
- Azure
desc: Generate Azure SAS Token with elixir for access blob resources.
layout: post
---

This example assumes that you use ex_azure and arc_azure libraries.

<!-- more -->
```elixir
defp _generate_sas_token() do
  account_name = Application.get_env(:ex_azure, :account)
  signed_permissions = "r" # read
  signed_service = "b" # blob
  signed_resource_type = "o" # container
  signed_start = Date.utc_today() |> Date.to_iso8601()
  signed_expiry = Date.utc_today() |> Date.add(1) |> Date.to_iso8601()
  signed_ip = ""
  signed_protocol = "https,http"
  signed_version = "2018-03-28"

  parameters = [
    account_name,
    signed_permissions,
    signed_service,
    signed_resource_type,
    signed_start,
    signed_expiry,
    signed_ip,
    signed_protocol,
    signed_version
  ]

  azure_key =  Application.get_env(:ex_azure, :access_key)
  azure_container =  Application.get_env(:arc_azure, :container)

  string_to_sign = Enum.join(parameters, "\n") <> "\n"

  signature = :crypto.hmac(:sha256, :base64.decode(azure_key), string_to_sign)

  sig = signature |> :base64.encode() |> URI.encode_www_form()

  "sv=#{signed_version}&ss=#{signed_service}&srt=#{signed_resource_type}&sp=#{signed_permissions}&se=#{signed_expiry}&st=#{signed_start}&spr=#{signed_protocol}&sig=#{sig}"
end
```
