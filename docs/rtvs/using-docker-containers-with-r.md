---
title: R a kontejnery Dockeru
description: Jak nastavit kontejnery Dockeru pro R a připojit se k nim pomocí sady Visual Studio.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: aeb6026bf7f90d07147ef559bdad9feb03e2c005
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35667129"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>Použití kontejnerů Dockeru pomocí nástrojů R pro Visual Studio

Nástroje R pro Visual Studio (RTVS) verzi 1.3 +, společně s instalace [Docker pro Windows](https://www.docker.com/docker-windows), podporuje práci s kontejnery Dockeru.

## <a name="create-a-container"></a>Vytvoření kontejneru

1. Vyberte **kontejnery** tlačítko v pravém horním rohu **pracovní prostory** okno (**nástroje R** > **Windows**  >  **Pracovní prostory**). V okně vás upozorní, pokud nemáte nainstalovaný Docker pro Windows a poskytuje odkaz pro stažení. Instalace Dockeru může vyžadovat restartování počítače.

    ![Okno pracovní prostory v nástroje jazyka R pro Visual Studio (VS2017) pomocí příkazu kontejnery](media/container-workspaces-window.png)

1. V **kontejnery** okně **vytvořit**:

    ![Vytvoření příkazu v okně kontejnery](media/containers-window-create.png)

1. Zadejte požadované informace do dialogového okna a vyberte **vytvořit**. Přihlašovací údaje, které zadáte slouží také k vytvoření účtu v Linuxu, pomocí kterého můžete přihlásit později.

    ![Zadání názvu kontejneru a přihlašovací údaje při vytváření kontejneru](media/containers-window-create-fill.png)

1. Může trvat nějakou dobu RTVS k sestavení image. **Výstup** okna v sadě Visual Studio zobrazí průběh, ale může zdát, že nebudou dělat většinu během dlouhých image stáhne; buďte připraveni buďte prosím trpěliví. Jakmile se image se sestavuje, RTVS spustí kontejner a zobrazí se v **kontejneru** okna. Ovládací prvky vpravo stop, odebrat nebo restartujte kontejneru.

    ![Okno kontejner dokončené kontejnery](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>Připojte se ke kontejneru

1. **Místní spouštění kontejnerů** část **pracovní prostory** v okně se zobrazí kontejnery spuštěné na portu 5444 RTVS démona. (Viz [vzdálené R Server pro Linux](setting-up-remote-r-service-on-linux.md) podrobnosti o konfiguraci démona.)

    ![Pracovní prostory okno zobrazující dostupné kontejnery](media/workspaces-window-running-containers.png)

1. K připojení do kontejneru, dvakrát klikněte na název kontejneru nebo vyberte šipku vpřed tlačítka vpravo. Když se připojí, zobrazí **interaktivní R** okno (naleznete v tématu [pracovat interaktivní okno R](interactive-repl-for-r-in-visual-studio.md)):

    ![Okno pracovní prostory a okno REPL otevřené pro kontejner](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>Použití vlastními silami sestavených imagí

RTVS detekuje a umožňuje správu kontejnerů vytvořené pomocí uživatelské Image, jako jsou image microsoft/rtvs popsané v následující soubor docker. Základní image se tady použít má rtvs démonů, R 3.4.2 a běžné balíčky R, které jsou předem nainstalované. **Poznámka:**: Změna uživatelského jména a hesla je vidět tady podle potřeby.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Použijte následující příkaz k sestavení image, mění se název kontejneru ( `--name` argument) podle potřeby:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444` Argument mapování portů 6056 na interní port 5444, která RTVS využívá ke zjištění rtvs démona. Každý kontejner, který zpřístupňuje port kontejneru 5444 je uveden v **pracovní prostory** okna. Pak můžete použít **pracovní prostory** okno pro připojení k kontejneru pomocí `<<unix>>\ruser1` jako uživatelské jméno a "panel" jako heslo, pokud zadáte jiné přihlašovací údaje v souboru docker.
