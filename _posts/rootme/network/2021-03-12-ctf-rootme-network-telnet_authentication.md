---
layout: post
title: "[CTF]-[ROOT-ME]-[CHALLENGES]-[NETWORK] - Telnet Authentication "
date: 2021-03-12
excerpt: "Challenge Telnet Authentication - Root-me.org"
tags: [ctf, rootme, network, challenge]
---

## Enunciado

> Find the user password in this TELNET session capture.

## Telnet - Authentication
O desafio nos fornece um arquivo **ch2.pcap** e temos que descobrir a senha utilizada pelo usuário.

![Wireshark - ch2.pcap](/img_posts/ctf/rootme/network/telnet-auth-1.png)

Assim como no desafio [FTP - Atuthentication](https://0xnymerio.github.io/ctf-rootme-network-ftp_authentication/), aqui vamos também seguir a flag **psh**.

![Seguindo o pacote](/img_posts/ctf/rootme/network/telnet-auth-2.png)

Como resolução alternativa, também é possível utilizar o **dsniff**, um sniffer de password. No caso, foi utilizado a sintaxe **$ dsniff -p ch2.pcap** e ele trouxe 4 resultados, mas dá pra visualizar que apenas os dois primeiros são interessantes para identificarmos qual a senha correta.

![Dsniff](/img_posts/ctf/rootme/network/telnet-auth-3.png)
