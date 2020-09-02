---
title: 'Kurz Docker – část 3: sdílení vaší aplikace'
description: Popisuje, jak sdílet image Docker pomocí registru Docker Hub.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d5bd7a2d79bf6da710fd0f5803c2415781160143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89178245"
---
# <a name="share-your-app"></a>Sdílení aplikace

Teď, když jsme sestavili image, můžeme se dát do sdílení! Pokud chcete sdílet image Docker, musíte použít registr Docker. Výchozím registrem je Docker Hub a tam, kde všechny image, které jsme použili, pochází.

## <a name="create-a-repo"></a>Vytvoření úložiště

Pro nahrání obrázku nejdřív musíte vytvořit úložiště v Docker Hub.

1. Pokud potřebujete, můžete přejít do [centra Docker](https://hub.docker.com) a přihlásit se.

1. Klikněte na tlačítko **vytvořit úložiště** .

1. Pro název úložiště použijte `getting-started` . Ujistěte se, že je viditelnost `Public` .

1. Klikněte na tlačítko **vytvořit** .

Pokud se podíváte na pravou stranu stránky, zobrazí se část s názvem **příkazy Docker**. To poskytuje příklad příkazu, který budete muset spustit pro vložení do tohoto úložiště.

![Příkaz Docker s příkladem push](media/push-command.png)

## <a name="push-the-image"></a>Vložení obrázku

1. V příkazovém řádku zkuste spustit příkaz push, který vidíte v Docker Hub. Všimněte si, že váš příkaz bude používat váš obor názvů, nikoli "Docker".

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    Proč to nebylo úspěšné? Příkaz push hledal obrázek s názvem Docker/Začínáme, ale nenašel ho. Pokud spustíte `docker image ls` , nezobrazí se žádné.

    Pokud to chcete opravit, musíte si "označit" svou stávající image, kterou jsme vytvořili, abychom jí poskytli jiný název.

1. Přihlaste se k centru Docker pomocí příkazu `docker login -u <username>` .

1. Pomocí `docker tag` příkazu dejte `getting-started` obrázku nový název. Nezapomeňte se zaměňovat `<username>` s ID Docker.

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. Nyní zkuste znovu spustit příkaz pro vložení. Pokud kopírujete hodnotu z Docker Hub, můžete ji vyřadit `tagname` , protože jste do názvu image nepřidali značku. Pokud nezadáte značku, Docker použije značku s názvem `latest` .

    ```bash
    docker push <username>/getting-started
    ```

## <a name="run-the-image-on-a-new-instance"></a>Spustit image na nové instanci

Teď, když je image vytvořená a vložená do registru, zkuste aplikaci spustit na nové instanci, která tuto image kontejneru nikdy neviděla! K tomu budete používat Play s Docker.

1. Otevřete prohlížeč a [začněte používat Docker](http://play-with-docker.com).

1. Přihlaste se pomocí účtu Docker Hub.

1. Až budete přihlášeni, klikněte na odkaz "+ Přidat novou instanci" na levém panelu. (Pokud ho nevidíte, udělejte si prohlížeč trochu širším.) Po několika sekundách se v prohlížeči otevře okno terminálu.

    ![Přehrát pomocí Docker Add New instance](media/pwd-add-new-instance.png)

1. V terminálu spusťte aplikaci čerstvou vloženou.

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    Měli byste vidět, že se image vypnula a nakonec začít.

1. Po zobrazení výzvy klikněte na označení 3000 a aplikaci byste měli vidět s vašimi změnami. Radostných! Pokud se nezobrazí znak 3000, můžete kliknout na tlačítko **otevřít port** a zadat 3000.

## <a name="recap"></a>Rekapitulace

V této části jste zjistili, jak sdílet image jejich vložením do registru. Pak jste přešli na značku nové instance a mohli jste spustit čerstvou vloženou image. To je poměrně běžné v kanálech CI, kde kanál vytvoří image a nahraje ji do registru a v produkčním prostředí může použít nejnovější verzi image.

Teď, když jste tuto aplikaci restartovali, odvoláte ji na konci poslední části, ztratíte všechny položky seznamu úkolů. To je zjevně Skvělé uživatelské prostředí, takže se dozvíte další informace o tom, jak můžete uchovávat data v rámci restartování.

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Uchování databáze](persist-your-data.md)