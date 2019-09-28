---
title: Load ENV vars
tags:
desc: Load ENV vars in local terminal session.
layout: post
---

To load ENV vars into the terminal simply execute

`export $(cat .env | xargs)`

Note: if you close the terminal, you will have to execute the command again.
