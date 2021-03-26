---
layout: post
title: "[CTF]-[CRYPTOHACK]-[CHALLENGES]-[GENERAL] - ASCII "
date: 2021-03-12
excerpt: "Challenge ASCII - cryptohack.org"
tags: [ctf, cryptohack, challenge, general]
---

## Enunciado

> ASCII is a 7-bit encoding standard which allows the representation of text using the integers 0-127. Using the below integer array, convert the numbers to their corresponding ASCII characters to obtain a flag.
> **[99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]**

## ASCII

O challenge é bem tranquilo, dado uma lista de numeros inteiros, converter para **ASCII**. Em **Python3**, podemos utilizar o método **chr()** que nos retorna o caractere correspondente de um numero inteiro dado ao padrão **unicode**.

Chama a lista de numeros inteiros na variavel **key**, realizo um loop onde realizo o método **chr()** para cada **numero em key**, percorrendo então todos os numeros da lista. Pra melhor visualização, utilizei o **join** para melhor visualizar a flag e já colar direto para o envio.

~~~ python
key = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73,
       95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
flag = []
for numero in key:
    flag.append( chr(numero))
print("".join(flag))
~~~
