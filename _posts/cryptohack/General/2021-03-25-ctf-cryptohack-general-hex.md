---
layout: post
title: "[CTF]-[CRYPTOHACK]-[CHALLENGES]-[GENERAL] - Hex "
date: 2021-03-12
excerpt: "Challenge Hex - cryptohack.org"
tags: [ctf, cryptohack, challenge, general]
---

## Enunciado

> When we encrypt something the resulting ciphertext commonly has bytes which are not printable ASCII characters. If we want to share our encrypted data, it's common to encode it into something more user-friendly and portable across different systems.

>Included below is a flag encoded as a hex string. Decode this back into bytes to get the flag.
> **63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e
67735f615f6c6f747d**

## Hex

Suave suave. Só utilizarmos o **bytearray**, especificamente o método **fromhex**, onde ela vai retornar um novo objeto bytearray inicializado a partir de uma string de números hexadecimais. Se aplicarmos então o método **decode**, podemos exibir o resultado em **ASCII** e obter a flag do desafio.

~~~ python
key = "63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974
        685f6865785f737472696e67735f615f6c6f747d"
print(bytearray.fromhex(key).decode())
~~~
