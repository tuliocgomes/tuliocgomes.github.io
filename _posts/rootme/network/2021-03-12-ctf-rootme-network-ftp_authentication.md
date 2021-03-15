---
layout: post
title: "[CTF]-[ROOT-ME]-[CHALLENGES]-[NETWORK] - FTP Authentication "
date: 2021-03-12
excerpt: "Challenge FTP Authentication - Root-me.org"
tags: [ctf, rootme, network, challenge]
---

## Enunciado

> An authenticated file exchange achieved through FTP. Recover the password used by the user.

## FTP - authentication

O desafio nos fornece um **ch1.pcap** e temos que descobrir a senha utilizada pelo usuário.

![Wireshark - ch1.pcap](/img_posts/ctf/rootme/network/ftp-auth-1.png)

Como a senha é o usuário realizando um envio de valores, podemos então procurar pelas **flags tcp** que são relevantes. A flag **psh** indica que contém dados da aplicação e é seguida pela flag **ack**, confirmando então o recebimento. No Wireshark, agora é só seguir a flag **psh/ack** que envia as informações do usuário e a senha do alvo.

![Seguindo o pacote](/img_posts/ctf/rootme/network/ftp-auth-2.png)

Strings: **$ tshark -r ch1.pcap -Y  'ftp.request.command == "PASS"'**.
Achei bacana utilizar o filtro pelos comandos pra cada protocolo, existe uma lista com os commands e assim é possivel no **== COMANDO** por um comando específico do **ftp**, veja mais detalhes dos comandos [aqui](https://en.wikipedia.org/wiki/List_of_FTP_commands).
