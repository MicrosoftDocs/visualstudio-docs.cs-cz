---
title: Kontejnery R a Dockeru
description: Jak nastavit kontejnery Dockeru pro R a připojit se k nim pomocí Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3aefba3880443269dbdb1c933e2c12b2f8001469
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2021
ms.locfileid: "111551277"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Použití kontejnerů Dockeru s Nástroje R pro Visual Studio

Verze Nástroje R pro Visual Studio (RTVS) 1.3 nebo novější spolu s instalací [Docker for Windows](https://www.docker.com/docker-windows)podporuje práci s kontejnery Dockeru.

## <a name="create-a-container"></a>Vytvoření kontejneru

1. V pravém **rohu** okna Pracovní prostory vyberte tlačítko **Kontejnery** ( Pracovní prostory Windows v nástrojích  >    >  R). Okno vás informuje, pokud nemáte nainstalované Docker for Windows, a poskytne odkaz ke stažení. Instalace Dockeru může vyžadovat restartování počítače.

    ![Okno Pracovní prostory v Nástroje R pro Visual Studio (VS2017) s příkazem Containers](media/container-workspaces-window.png)

1. V okně **Kontejnery** vyberte **Vytvořit:**

    ![Příkaz Create v okně Kontejnery](media/containers-window-create.png)

1. V dialogovém okně vyplňte požadované informace a vyberte **Vytvořit.** Přihlašovací údaje, které zadáte, se také používají k vytvoření účtu v Linuxu, pomocí kterého se přihlásíte později.

    ![Zadání názvu kontejneru a přihlašovacích údajů při vytváření kontejneru](media/containers-window-create-fill.png)

1. Vytvoření image pomocí rtvs může nějakou dobu trvat. Okno **Výstup** v okně Visual Studio zobrazuje průběh, ale může se zdát, že během zdlouhavých stahování obrázků příliš neustupuje. Buďte připraveni na trpělivost. Jakmile je image sestavená, rtvs spustí kontejner a zobrazí se v **okně Kontejner.** Ovládací prvky napravo zastaví, odeberou nebo restartují kontejner.

    ![Okno Kontejnery zobrazující dokončený kontejner](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Připojení ke kontejneru

1. Část **Local Running Containers (Místní** spuštěné kontejnery) okna Workspaces (Pracovní **prostory)** zobrazuje kontejnery s démonem RTVS na portu 5444. (Podrobnosti o R Server pro Linux procesu démon najdete v tématu Remote [R Server pro Linux.)](setting-up-remote-r-service-on-linux.md)

    ![Okno Pracovní prostory zobrazující dostupné kontejnery](media/workspaces-window-running-containers.png)

1. Pokud se chcete připojit ke kontejneru, dvakrát klikněte na název kontejneru nebo vyberte tlačítko se šipkou vpřed vpravo. Po připojení se zobrazí **okno Interaktivní R** (viz Práce [s oknem Interaktivní R dat):](interactive-repl-for-r-in-visual-studio.md)

    ![Okno Pracovní prostory a otevřené okno REPL pro kontejner](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Použití vlastních imagí

RTVS detekuje a umožňuje správu kontejnerů vytvořených pomocí vlastních imagí, jako je image microsoft/rtvs popsaná v níže popsaném souboru Dockeru. Základní image použitá tady má předinstalovaný nástroj rtvs-daemon, R 3.4.2 a běžné balíčky R. **Poznámka:** Podle potřeby změňte uživatelské jméno a heslo, které se tady zobrazuje.

```docker
FROM mcr.microsoft.com/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Pomocí následujícího příkazu sestavte image a podle potřeby změň název kontejneru `--name` (argument):

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

Argument `-p 6056:5444` mapuje port 6056 na interní port 5444, který RTVS používá ke zjištění procesu rtvs-daemon. Všechny kontejnery, které zpřístupňuje port 5444 kontejneru, se zobrazí v **okně Pracovní prostory.** Pak se můžete pomocí okna **Pracovní** prostory připojit ke kontejneru pomocí uživatelského jména a "foobar" jako hesla, pokud jste v souboru Dockeru nezadáte jiné přihlašovací `<<unix>>\ruser1` údaje.
