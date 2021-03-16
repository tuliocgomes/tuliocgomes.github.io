---
layout: post
title: "[CTF]-[ROOT-ME]-[CHALLENGES]-[NETWORK] - DNS Zone Transfer "
date: 2021-03-12
excerpt: "Challenge DNS Zone Transfer - Root-me.org"
tags: [ctf, rootme, network, challenge]
---

## Enunciado

> A not really dutiful administrator has set up a DNS service for the "ch11.challenge01.root-me.org" domain...
>
> Challenge connection informations: Host challenge01.root-me.org, Protocol DNS and Port 54011

## DNS Zone Transfer

Como o adm criou um dns para **ch11.challenge01.root-me.org**, bora perguntar pro seu “master” na porta 54011 quem é o **ch11** e se é possivel realizar uma transferência de zona. Neste exemplo, eu utilizei o **dig**.

![Dig - Transfer Zone](/img_posts/ctf/rootme/network/dns-zt-1.png)
