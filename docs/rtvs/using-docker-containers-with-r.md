---
title: Kontejnery R a Docker
description: Jak nastavit kontejnery Docker pro R a připojit se k nim pomocí sady Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 01048bc9b21287eb62693096b34a1ea8305e0ee9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851865"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Použití kontejnerů Docker s Nástroje R pro Visual Studio

Nástroje R pro Visual Studio (RTVS) verze 1.3 + společně s instalací [Docker for Windows](https://www.docker.com/docker-windows)podporuje práci s kontejnery Docker.

## <a name="create-a-container"></a>Vytvoření kontejneru

1. Vyberte tlačítko **kontejnery** v pravém horním rohu okna **pracovní prostory** (**nástroje R**  >    >  **pracovní prostory** Windows). Okno vás informuje, pokud nemáte nainstalovaný Docker for Windows a obsahuje odkaz na stažení. Instalace Docker může vyžadovat restart počítače.

    ![Okno pracovních prostorů v Nástroje R pro Visual Studio (VS2017) pomocí příkazu Containers](media/container-workspaces-window.png)

1. V okně **kontejnery** vyberte **vytvořit**:

    ![Vytvořit příkaz v okně kontejnery](media/containers-window-create.png)

1. V dialogovém okně dokončete požadované informace a vyberte **vytvořit**. Přihlašovací údaje, které zadáte, se použijí také k vytvoření účtu v systému Linux, se kterým se přihlašujete později.

    ![Zadání názvu kontejneru a přihlašovacích údajů při vytváření kontejneru](media/containers-window-create-fill.png)

1. RTVS sestavení image může nějakou dobu trvat. V okně **výstup** v aplikaci Visual Studio se zobrazuje průběh, ale může se zdát, že během zdlouhavého stahování obrázků nebude provádět mnoho změn; Připravte se na pacienta. Po sestavení image RTVS spustí kontejner a zobrazí se v okně **kontejneru** . Ovládací prvky pro správné zastavení, odebrání nebo restartování kontejneru.

    ![Okno kontejnery znázorňující dokončený kontejner](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Připojit ke kontejneru

1. V části **místní spuštěné kontejnery** v okně **pracovní prostory** se zobrazí kontejnery, na kterých běží démon RTVS na portu 5444. (Podrobnosti o tom, jak je démon nakonfigurovaný, najdete v tématu [vzdálené R Server pro Linux](setting-up-remote-r-service-on-linux.md) .)

    ![Okno pracovní prostory zobrazující dostupné kontejnery](media/workspaces-window-running-containers.png)

1. Pokud se chcete připojit ke kontejneru, poklikejte na název kontejneru nebo vyberte tlačítko se šipkou doprava. Po připojení se zobrazí okno **interaktivní R** (viz [práce s interaktivní R oknem](interactive-repl-for-r-in-visual-studio.md)):

    ![Okno pracovních prostorů a okno REPL otevřené pro kontejner](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Použití vlastních vestavěných imagí

RTVS detekuje a umožňuje správu kontejnerů vytvořených pomocí vlastních bitových kopií, jako je například Image Microsoft/RTVS, která je popsána v souboru Docker níže. Základní image, kterou tady používáte, má předinstalované balíčky RTVS-daemon, R 3.4.2 a Common R. **Poznámka**: podle potřeby změňte zde zobrazované uživatelské jméno a heslo.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Pomocí následujícího příkazu Sestavte image, změňte název kontejneru ( `--name` argument) podle potřeby:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444`Argument mapuje port 6056 na interní port 5444, který RTVS používá k detekci RTVS-démon. Všechny kontejnery, které zveřejňují port kontejneru 5444, jsou uvedeny v okně **pracovní prostory** . Pak můžete pomocí okna **pracovní prostory** připojit ke kontejneru pomocí `<<unix>>\ruser1` jako uživatelské jméno a "panel" jako heslo, pokud neurčíte jiné přihlašovací údaje v souboru Docker.
