---
title: Kontejnery R a Dockeru
description: Jak nastavit kontejnery Dockeru pro R a připojit se k nim pomocí sady Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c5b4278ab50aac96703f03e74c014d29831f22e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62810141"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Použití kontejnerů Dockeru s nástroji R pro Visual Studio

Nástroje R pro Visual Studio (RTVS) verze 1.3+ spolu s instalací [Dockeru pro Windows](https://www.docker.com/docker-windows)podporují práci s kontejnery Dockeru.

## <a name="create-a-container"></a>Vytvoření kontejneru

1. V pravém rohu okna **Pracovní prostory pracovních prostorů** vyberte tlačítko **Kontejnery** **(R Tools** > **Windows** > **Workspaces).** Okno vás informuje, pokud nemáte nainstalovaný Docker pro Windows a poskytuje odkaz ke stažení. Instalace Dockeru může vyžadovat restartování počítače.

    ![Okno pracovních prostorů v nástrojích R pro Visual Studio (VS2017) s příkazem Kontejnery](media/container-workspaces-window.png)

1. V okně **Kontejnery** vyberte **Vytvořit**:

    ![Příkaz Vytvořit v okně Kontejnery](media/containers-window-create.png)

1. Vyplňte požadované informace v dialogovém okně a vyberte **Vytvořit**. Zadávaná pověření se také používají k vytvoření účtu v Systému Linux, pomocí kterého se přihlásíte později.

    ![Zadání názvu kontejneru a pověření při vytváření kontejneru](media/containers-window-create-fill.png)

1. Může trvat nějakou dobu pro RTVS k vytvoření bitové kopie. **Okno Výstup** v sadě Visual Studio zobrazuje průběh, ale může se zdát, že během zdlouhavého stahování obrázků neprovádí mnoho; být připraveni být trpěliví. Po dokončení bitové kopie rtvs spustí kontejner a zobrazí se v okně **Kontejner.** Ovládací prvky na pravé zastavení, odebrání nebo restartování kontejneru.

    ![Okno kontejnerů zobrazující dokončený kontejner](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Připojení ke kontejneru

1. V části **Místní spuštěné kontejnery** v okně **Pracovní prostory** se zobrazí kontejnery s daemonem RTVS na portu 5444. (Podrobnosti o konfiguraci daemonu naleznete v tématu [Remote R Server for Linux.)](setting-up-remote-r-service-on-linux.md)

    ![Okno pracovních prostorů zobrazující dostupné kontejnery](media/workspaces-window-running-containers.png)

1. Chcete-li se připojit ke kontejneru, poklepejte na název kontejneru nebo vyberte tlačítko šipky vpřed vpravo. Při připojení se zobrazí interaktivní okno **R** (viz [Práce s interaktivním oknem R):](interactive-repl-for-r-in-visual-studio.md)

    ![Okno pracovních prostorů a okno REPL otevřené pro kontejner](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Použití vlastních obrazů

RTVS detekuje a umožňuje správu kontejnerů vytvořených pomocí vlastních bitových kopií, jako je například image Microsoft/RTVS popsaná v souboru dockeru níže. Základní obrázek zde použitý má rtvs-daemon, R 3.4.2 a běžné balíčky R předinstalované. **Poznámka:** Změňte uživatelské jméno a heslo zde zobrazené podle potřeby.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

K vytvoření bitové kopie použijte následující příkaz, `--name` který podle potřeby změní název kontejneru (argument):

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

Argument `-p 6056:5444` mapuje port 6056 na interní port 5444, který RTVS používá k detekci rtvs-daemon. Všechny kontejnery, které zpřístupňuje port kontejneru 5444 je uveden v okně **pracovníprostory.** Potom můžete použít okno **Pracovní prostory** pro `<<unix>>\ruser1` připojení ke kontejneru pomocí jako uživatelské jméno a "foobar" jako heslo, pokud jste zadali různá pověření v souboru dockeru.
