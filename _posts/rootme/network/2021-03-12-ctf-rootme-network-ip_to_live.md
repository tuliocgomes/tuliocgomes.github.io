---
layout: post
title: "[CTF]-[ROOT-ME]-[CHALLENGES]-[NETWORK] - IP To Live "
date: 2021-03-12
excerpt: "Challenge IP To Live - Root-me.org"
tags: [ctf, rootme, network, challenge]
---

## Enunciado

> Find the TTL used to reach the targeted host in this ICMP exchange.

## IP To Live

O desafio nos fornece um arquivo **ch7.pcap** e temos que descobrir o valor de **TTL** (Time To Live) de um determinado host. Se observarmos o **pcap**, existem diversas requisições que retornam com **"no response found"** com o erro de **"tempo de vida excedido"**.

![Wireshark - ch7.pcap](/img_posts/ctf/rootme/network/ip-ttl-1.png)

Observando a primeira requisição que possui um **icmp.replay**, ou seja, não ultrapassou o tempo de vida (ou saltos), é possivel constatar no header dela o seu valor de **TTL**.

![IP - TTL](/img_posts/ctf/rootme/network/ip-ttl-2.png)
