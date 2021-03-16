---
layout: post
title: "[CTF]-[ROOT-ME]-[CHALLENGES]-[NETWORK] - Twitter Authentication "
date: 2021-03-12
excerpt: "Challenge Twitter Authentication - Root-me.org"
tags: [ctf, rootme, network, challenge]
---

## Enunciado

> A twitter authentication session has been captured, you have to retrieve the password.

## Twitter Authentication

O desafio nos fornece um arquivo **ch3.pcap** e temos que descobrir uma senha.

![Wireshark - ch3.pcap](/img_posts/ctf/rootme/network/twitter-auth-1.png)

Como só tinha um único pacote, nesse eu decidi ter uma abordagem diferente e já utilizei a ferramenta **strings** para me mostrar algo logo de cara, qualquer coisa escondida ou seria escovar bytes ou observar o payload do protocolo http. Em **Authorization**, deduzi que estava encodado em base64 e consegui a flag.

![Just base64](/img_posts/ctf/rootme/network/twitter-auth-2.png)
