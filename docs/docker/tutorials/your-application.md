---
title: 'Kurz Docker – část 1: sestavení a spuštění ukázkové aplikace seznamu úkolů'
description: Přehled ukázkové aplikace seznamu úkolů, která běží v Node.js.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: b8470c8d7708bc51916a6f57f5aa135c3267e355
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039020"
---
# <a name="build-and-run-the-todo-sample-app"></a>Sestavení a spuštění ukázkové aplikace todo

V ostatních částech tohoto kurzu budete pracovat s jednoduchým manažerem seznamu úkolů, který běží v Node.js. Pokud nejste obeznámeni s Node.js, nedělejte si starosti! Není potřeba žádné reálné prostředí JavaScriptu.

V tomto okamžiku je váš vývojový tým poměrně malý a Vy jednoduše vytváříte aplikaci, která vám ukáže svůj MVP (minimální životaschopný produkt). Chcete Ukázat, jak funguje a co je možné dělat, aniž byste museli myslet na to, jak bude fungovat pro velký tým, více vývojářů atd.

![Snímek obrazovky správce seznamu TODO](media/todo-list-sample.png)

## <a name="get-the-app"></a>Získat aplikaci

Než budete moct aplikaci spustit, musíte na svém počítači získat zdrojový kód aplikace. Pro skutečné projekty budete obvykle klonovat úložiště. Pro tento kurz ale vytvoříte soubor ZIP obsahující aplikaci.

1. [Stáhněte si soubor zip](/assets/app.zip). Otevřete soubor ZIP a zajistěte extrakci obsahu.

1. Po extrakci otevřete projekt pomocí svého oblíbeného editoru kódu. Pokud budete potřebovat editor, můžete použít [Visual Studio Code](https://code.visualstudio.com/). Měli byste vidět `package.json` a dva podadresáře ( `src` a `spec` ).

    ![Snímek obrazovky s Visual Studio Code otevřeli v načtené aplikaci](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>Sestavení image kontejneru aplikace

Aby bylo možné aplikaci sestavit, je nutné použít `Dockerfile` . Souboru Dockerfile je jednoduchý textový skript s pokyny, který se používá k vytvoření image kontejneru. Pokud jste vytvořili fázemi dříve, může se v souboru Dockerfile níže zobrazit několik vad. Ale nedělejte si starosti! Přejdoume na ně.

1. Vytvořte soubor s názvem `Dockerfile` ve stejné složce jako soubor `package.json` s následujícím obsahem.

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    Zkontrolujte prosím, že soubor `Dockerfile` nemá žádnou příponu souboru jako `.txt` . Některé editory můžou tuto příponu souboru automaticky připojit a to by vedlo k chybě v dalším kroku.

1. Pokud jste to ještě neudělali, otevřete terminál a přejděte do `app` adresáře s `Dockerfile` . Teď vytvořte image kontejneru pomocí `docker build` příkazu.

    ```bash
    docker build -t getting-started .
    ```

    Tento příkaz použil souboru Dockerfile k sestavení nové image kontejneru. Možná jste si všimli, že se stáhla spousta "vrstev". Důvodem je, že jste tvůrcem pokyn, který jste chtěli začít z `node:12-alpine` obrázku. Ale vzhledem k tomu, že jste na počítači neměli tento obrázek, je potřeba ho stáhnout.

    Po stažení obrázku jste zkopírovali aplikaci a použili `yarn` k instalaci závislostí aplikace. `CMD`Direktiva určuje výchozí příkaz, který se spustí při spuštění kontejneru z tohoto obrázku.

    Nakonec `-t` příznak označí obrázek. Tuto hodnotu si můžete představit jednoduše jako název pro finální Image jako čitelný. Vzhledem k tomu, že jste pojmenovali obrázek `getting-started` , můžete na tuto image odkazovat při spuštění kontejneru.

    Na `.` konci `docker build` příkazu informuje, že Docker by měl hledat `Dockerfile` v aktuálním adresáři.

## <a name="starting-an-app-container"></a>Spuštění kontejneru aplikace

Teď, když máte image, spusťte aplikaci! K tomu použijte `docker run` příkaz (Nezapomeňte, že v minulosti).

1. Spusťte kontejner pomocí `docker run` příkazu a zadejte název bitové kopie, kterou jste právě vytvořili:

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    Zapamatujte `-d` si `-p` příznaky a? Nový kontejner spouštíte v režimu "Odpojeno" (na pozadí) a vytváříte mapování mezi portem hostitele 3000 na port 3000 kontejneru. Bez mapování portů nebudete mít přístup k aplikaci.

1. Po několika sekundách otevřete webový prohlížeč na [http://localhost:3000](http://localhost:3000) .
    Měla by se zobrazit aplikace.

    ![Prázdný seznam todo](media/todo-list-empty.png)

1. Pokračujte a přidejte položku nebo dvě a podívejte se, že funguje podle očekávání. Můžete označit položky jako dokončené a odebrat položky. Vaše front-end úspěšně ukládá položky do back-endu. Hodně rychlá a jednoduchá, huh?

V tomto okamžiku byste měli mít spuštěného správce seznamu úkolů s několika položkami, které jste vytvořili. Teď provedeme několik změn a naučíte se spravovat vaše kontejnery.

Pokud se podíváte na rozšíření VS Code, měli byste vidět vaše dva kontejnery teď (Tento kurz a váš nově spuštěný kontejner aplikací)!

![Rozšíření Docker s kurzem a kontejnery aplikací se systémem](media/vs-two-containers.png)

## <a name="recap"></a>Rekapitulace

V této krátké části jste se seznámili se základními informacemi o vytváření image kontejneru a vytvořením souboru Dockerfile. Po vytvoření image jste spustili kontejner a viděli běžící aplikaci.

V dalším kroku provedete úpravy aplikace a naučíte se, jak aktualizovat spuštěnou aplikaci pomocí nové image. Na cestě se naučíte několik dalších užitečných příkazů.

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Aktualizuje se vaše aplikace.](update-your-app.md)