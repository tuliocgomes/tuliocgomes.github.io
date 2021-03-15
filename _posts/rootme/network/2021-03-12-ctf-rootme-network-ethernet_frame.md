---
layout: post
title: "[CTF]-[ROOT-ME]-[CHALLENGES]-[NETWORK] - Ethernet frame "
date: 2021-03-12
excerpt: "Challenge Ethernet frame - Root-me.org"
tags: [ctf, rootme, network, challenge]
---

## Enunciado

> Find the (supposed to be) confidential data in this ethernet frame.

## Ethernet Frame

O Challenge nos leva direto para um **txt** com vários bytes em hexadecimais. Poderiamos então traduzir byte a byte e seguindo conforme a construção do cabeçalho ethernet para ter a informação, mas não vou abordar o estrutura do protocolo e recomendo dar uma olhada na [rfc1042](http://repository.root-me.org/RFC/EN%20-%20rfc1042.txt), mas aqui vou trazer uma resolução bem mais direta e rápida.

![Ethernet - Frame](/img_posts/ctf/rootme/network/ethernet-frame-1.png)

Apesar da dica ser sobre o header ethernet, já mandei direto a saída **hex to ASCII**, assim foi possivel observar se existia algum texto relevante e sim, existe o conteúdo de uma requisição http com uma string encodada em base64, bem suspeito. Só realizar o decode e temos a chave.

![Ethernet - Frame](/img_posts/ctf/rootme/network/ethernet-frame-2.png)
