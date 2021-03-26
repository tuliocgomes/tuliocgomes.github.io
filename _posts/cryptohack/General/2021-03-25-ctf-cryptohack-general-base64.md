---
layout: post
title: "[CTF]-[CRYPTOHACK]-[CHALLENGES]-[GENERAL] - Base64 "
date: 2021-03-25
excerpt: "Challenge Base64 - cryptohack.org"
tags: [ctf, cryptohack, challenge, general]
---

## Enunciado

> Another common encoding scheme is Base64, which allows us to represent binary data as an ASCII string using 64 characters. One character of a Base64 string encodes 6 bits, and so 4 characters of Base64 encodes three 8-bit bytes. Base64 is most commonly used online, where binary data such as images can be easy included into html or css files.

> Take the below hex string, decode it into bytes and then encode it into Base64.
> **72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf**

## Base64

Um desafio levemente mais elaborado, mas mesmo assim bem divertido. Temos que transformar a string em **hex** para **bytes** e então encodar para **Base64**.

Primeiramente vamos importar a lib **base64**, já que vamos utilizar no código para encodar a string. A classe **bytes** já se encontra por padrão em qualquer instalação do python, então vamos utilizar o método **fromhex** para transformar nosso **hex em bytes** e salvar o conteudo na variavel **bytes_string**. A saída dessa variavel se dá pelo seguinte formato: **b'r\xbc\xa9\xb6\x8f\xc1j\xc7\xbe\xeb\x8f\x84\x9d\xca\x1d\x8ax>\x8a\xcf\x96y\xbf\x92i\xf7\xbf'**, onde o **b'r** no **python3** representa que é uma string de **bytes**.

Com a **bytes_string**, agora é apenas encodar em **base64** utilizando o método **b64encode**.

~~~ python
import base64

hex_string = "72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf"
bytes_string = bytes.fromhex(hex_string)
encoded = base64.b64encode(bytes_string)
print(encoded)
~~~

**Atenção**, se atente no formato da flag, pois é diferente das demais!
