---
layout: post
title: "[CTF]-[ROOT-ME]-[CHALLENGES]-[NETWORK] - Cisco Password "
date: 2021-03-12
excerpt: "Challenge Cisco Password - Root-me.org"
tags: [ctf, rootme, network, challenge]
---

## Enunciado

>Find the "Enable" password.

## Cisco Password
O Challenge nos leva direto para um **txt** que é básicamente um **pcf** (profile configuration file) da Cisco. Como temos que achar a senha **"enable"**, comecei a procurar sobre os padrões de de senhas da Cisco e se existe algum algoritmo conhecido.

![ch15.txt](/img_posts/ctf/rootme/network/cisco-passwd-1.png)

Pesquisando sobre como os equipamentos da cisco encryptam suas senhas, foi possível achar o <https://github.com/axcheron/cisco_pwdecrypt>, que decripta as senhas de arquivos **pcf**. O arquivo contém 5 senhas criptografadas, sendo que 4 delas são reversiveis (as que possuem o parâmetro 7) e uma senha para enable (com parâmetro 5) que só pode ser deduzida ou realizando um brute-force para descobrir. Revertendo as 4 primeiras senhas, temos um padrão onde todas começam com  **6sK0_** , como no próprio subtítulo do challenge **“its not always a hash"**. Coloquei enable no final e por fim consegui a key correta.

![CISCO Crack](/img_posts/ctf/rootme/network/cisco-passwd-2.png)

Fuçando mais um pouco, descobri o salto correto e foi possível confirmar que a senha estava certa, só a dedução nao vale :D

![Openssl](/img_posts/ctf/rootme/network/cisco-passwd-3.png)
