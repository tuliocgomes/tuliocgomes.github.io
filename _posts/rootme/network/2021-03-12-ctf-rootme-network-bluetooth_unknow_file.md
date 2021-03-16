---
layout: post
title: "[CTF]-[ROOT-ME]-[CHALLENGES]-[NETWORK] - Bluetooth Unknow File "
date: 2021-03-12
excerpt: "Challenge Bluetooth Unknow File - Root-me.org"
tags: [ctf, rootme, network, challenge]
---

## Enunciado

>Your friend working at NSA recovered an unreadable file in a hacker’s computer. The only thing he knows is that it comes from a communication between a computer and a phone.
>The answer is the sha-1 hash of the concatenation of the MAC address (uppercase) and the name of the phone.

## Bluetooth Unknow File

**Esse aqui deu trabalho ein, então se prepare.** O desafio nos fornece um arquivo **ch18.bin** e temos que descobrir o **MAC Adress** e o **nome do telefone**. O arquivo tem **1.4kb** e tem a extensão **bin**, nunca me deparei com algum log nesse formato, então abri ele com o **cat** pra ver o que tinha dentro e com o **file** pra ver que tipo de cabeçalho tinha esse arquivo. Após uma busca, o arquivo do tipo **BTSnoop** armazena tráfego **Bluetooth® HCI** e é muito semelhante a estrutura do **snoop** ([RFC1761](https://tools.ietf.org/html/rfc1761)). A string **GT-S7390G** revela que é um modelo de celular da Samsung, com o nome comercial de **Samsung Galaxy Trend Lite**.

![ch18.bin](/img_posts/ctf/rootme/network/bluetooth-unf-1.png)

Usando um **lookup mac address**, confirma-se que **0C:B3:19** são os 3 bytes iniciais do mac adress dos dispositivos samsung, o que nos dá um norte para saber o que procurar.

![Lookup MAC](/img_posts/ctf/rootme/network/bluetooth-unf-2.png)

Abri o ch18.bin no **wireshark**, utilizando as opções **wireless > bluetooth devices**, aparece um menu que exibe algumas informações sobre o tráfego da comunicação. Eu não sabia dessa funcionalidade do wireshark, então até descobrir que ele podia ler este tipo de arquivo, eu penei um pouco. Agora tá 90% pronto o sorvetinho, já temos o modelo do celular e o inicio do mac, agora é só escovar byte.

![Wireshark - Bluetooth Devices](/img_posts/ctf/rootme/network/bluetooth-unf-3.png)

Sabemos que esse mac address exibido, **0c:0c:0c:0c:0c:0c**, não é o que estamos buscando, mas ele já nos informa o nome do aparelho: **SamsungE**.

![Not This MAC, bro](/img_posts/ctf/rootme/network/bluetooth-unf-4.png)

Analisando os pacotes com maior tamanho, é possivel encontrar o mac address do celular alvo.

![This MAC, bro](/img_posts/ctf/rootme/network/bluetooth-unf-5.png)

Conforme pedido no challenge, todo o mac em maiúsculo com o nome do dispositivo no final, **depois aplica o sha1**.

![Sha1 for the win](/img_posts/ctf/rootme/network/bluetooth-unf-6.png)

Este challenge foi bem interessante, não conhecia nada sobre análise de tráfego de bluetooth, como ele armazena os dados e muito menos sobre o BTSnoop. **Grande aprendizado!**
