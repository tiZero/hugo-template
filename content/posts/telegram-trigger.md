+++
title = "Integrazione con Telegram"
description = "Un bot che notifica un canale Telegram a ogni nuovo post pubblicato."
date = 2022-03-20T19:50:00+01:00
draft = false
+++

Creato canale Telegram con [invite link](https://t.me/+QcNUYOHdOPxlYWVk) (le richieste vanno approvate dagli admin). L'idea è creare un bot da zero che sia in grado di

1.  notificare il canale di ogni nuovo contenuto pubblicato sul sito;
2.  gestire i commenti degli utenti.

Una soluzione al primo punto è offerta da [IFTTT](https://ifttt.com/) che consente all'applicazione di puntare al file [index.xml](https://tizero.github.io/org-notes/index.xml) e di connettersi a una chat di gruppo o a un canale. Il secondo punto può essere ottenuto direttamente con le funzionalità di Telegram associando al canale una chat dedicata.
