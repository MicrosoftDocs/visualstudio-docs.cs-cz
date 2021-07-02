---
title: 'Kurz Dockeru – Část 3: Sdílení aplikace'
description: Popisuje, jak sdílet image Dockeru pomocí Docker Hub registru.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d64d10c7abefc14f31c39c3b8397e95cec67e9f4
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222783"
---
# <a name="share-your-app"></a>Sdílení aplikace

Když jsme teď image sestavili, můžeme ji sdílet. Ke sdílení imagí Dockeru musíte použít registr Dockeru. Výchozí registr je Docker Hub odkud pocházejí všechny image, které jsme použili.

## <a name="create-a-repo"></a>Vytvoření repo

Abyste image nasadili, musíte nejprve ve virtuálním počítači vytvořit Docker Hub.

1. Přejděte na [Docker Hub](https://hub.docker.com/signup/msftedge?utm_source=msftedge) a v případě potřeby se přihlaste.

1. Klikněte na **tlačítko Create Repository (Vytvořit** úložiště).

1. Jako název repo použijte `getting-started` . Ujistěte se, že viditelnost je `Public` .

1. Klikněte na **tlačítko** Vytvořit.

Pokud se podíváte na pravé straně stránky, uvidíte oddíl s názvem **Příkazy Dockeru.** Získáte tak příklad příkazu, který budete muset spustit, aby se do tohoto repo nasa udává.

![Příklad příkazu Dockeru s nabízeným oznámením](media/push-command.png)

## <a name="push-the-image"></a>Nasdílení image

1. Na příkazovém řádku zkuste spustit příkaz push, který vidíte na Docker Hub. Všimněte si, že váš příkaz bude používat váš obor názvů, ne docker.

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Proč se to nepovede? Příkaz push hledal image s názvem docker/getting-started, ale nepodařilo se ji najít. Pokud spustíte `docker image ls` , neuvidíte ani jedno.

    Pokud chcete tento problém vyřešit, musíte stávající image, kterou jsme si právě sestavěli, označit tak, aby ji pojmechla jiným názvem.

1. Přihlaste se k Docker Hub pomocí příkazu `docker login -u <username>` .

1. Pomocí `docker tag` příkazu dejte `getting-started` bitové kopii nový název. Nezapomeňte provést prohození `<username>` s ID Dockeru.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Teď zkuste příkaz push zopakovat. Pokud kopírujete hodnotu z Docker Hub, můžete část vypustit, protože jste k názvu image `tagname` nepřidáte značku. Pokud nezadáte značku, Docker použije značku s názvem `latest` .

    ```bash
    docker push <username>/getting-started
    ```

    Místo příkazového řádku můžete také kliknout pravým tlačítkem  na značku image v části Image v zobrazení Dockeru, zvolit **Push...**(Na push...), pak zvolit **Připojení registry... Docker Hub** **.**

## <a name="run-the-image-on-a-new-instance"></a>Spuštění image v nové instanci

Teď, když je vaše image sestavená a naslaná do registru, zkuste aplikaci běžet na úplně nové instanci, která tuto image kontejneru nikdy neviděla. K tomu použijete Play s Dockerem.

1. Otevřete prohlížeč a [hrajte s Dockerem.](http://play-with-docker.com)

1. Přihlaste se pomocí Docker Hub účtu.

1. Po přihlášení klikněte na levém bočním panelu na odkaz + PŘIDAT NOVOU INSTANCI. (Pokud ji nevidíte, zohlédněte prohlížeč.) Po několika sekundách se v prohlížeči otevře okno terminálu.

    ![Přehrávání s přidáním nové instance Dockeru](media/pwd-add-new-instance.png)

1. V terminálu spusťte novou aplikaci.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Měli byste vidět, jak se obrázek stahuje a nakonec se spustí.

1. Až se zobrazí, klikněte na odznčku 3000 a měli byste vidět aplikaci se svými úpravami. Hurá! Pokud se odznek 3000 neotevře, můžete kliknout na tlačítko **Otevřít port** a zadat text 3000.

## <a name="recap"></a>Rekapitulace

V této části jste zjistili, jak sdílet image jejich nasdílením do registru. Pak jste se vrátili k úplně nové instanci a mohli jste spustit nově naslané image. To je poměrně běžné v kanálech CI, kde kanál vytvoří image a nasoudí ji do registru a produkční prostředí pak může používat nejnovější verzi image.

Teď, když jste to zjistili, vzpomeňte si, že na konci poslední části jste při restartování aplikace ztratili všechny položky seznamu úkolů. To samozřejmě není skvělé uživatelské prostředí, takže se dále dozvíte, jak můžete data zachovat po restartech.

## <a name="next-steps"></a>Další kroky

Pokračujte kurzem!

> [!div class="nextstepaction"]
> [Zachování databáze](persist-your-data.md)
