---
title: Nastavení vzdálené služby R na Linuxu
description: Jak nastavit vzdálené služby R na Ubuntu a subsystém Windows pro Linux.
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
ms.openlocfilehash: 81a0a5c26e91056e757bc6e6f68cd217e98c7e06
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220804"
---
# <a name="remote-r-service-for-linux"></a>Vzdálená služba R pro Linux

Vzdálená služba R pro Linux je aktuálně podobu rtvs démona. Proces démon se nepodporuje a otestovali na Ubuntu 16.04 16.10 LTS desktop, server a subsystém Windows pro Linux s Ubuntu. Hromadné Tento článek poskytuje pokyny pro nastavení vzdálené služby R na tyto různé systémy.

Po dokončení konfigurace vzdáleného počítače, bude následující postup k této službě připojit nástroje R pro Visual Studio (RTVS):

1. Vyberte **nástroje R** > **Windows** > **pracovní prostory** otevřít **pracovní prostory** okna.
1. Vyberte **přidat připojení**.
1. Zadejte název připojení a zadejte jeho adresu URL jako třeba `https://localhost:5444` (subsystém Windows pro Linux) nebo `https://public-ip:5444` (kontejnerů Azure). Vyberte **Uložit** po dokončení.
1. Vyberte ikonu připojení nebo dvakrát klikněte na položku připojení.
1. Zadejte přihlašovací údaje. Uživatelské jméno musí obsahovat předponu `<<unix>>\` stejně jako v `<<unix>>\ruser1` (podle potřeby pro všechna připojení ke vzdáleným počítačům s Linuxem).
1. Pokud používáte certifikát podepsaný svým držitelem, může se zobrazit upozornění. Zpráva obsahuje pokyny, chcete-li opravit toto upozornění.

## <a name="set-up-remote-r-service"></a>Nastavit vzdálenou službu r.

Tato část popisuje následující možnosti:

- [Fyzický počítač se systémem Ubuntu](#physical-ubuntu-computer)
- [Virtuální počítač s Ubuntu serverem nebo virtuálním počítači v Azure pro datové vědy](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Místním nebo vzdáleném kontejneru Dockeru (čisté sestavení)](#local-or-remote-docker-container-clean-build)
- [Kontejneru spuštěného v Azure Container Instances](#container-running-on-azure-container-instances)

V obou případech vzdálený počítač musí mít jednu z těchto balíčků překladačů R nainstalovaný:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [R server CRAN pro Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Fyzický počítač se systémem Ubuntu

1. Po přihlášení na počítači, stáhněte rtvs démon tarballu:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Spusťte instalační skript:

    ```bash
    sudo ./rtvs-install
    ```

    U bezobslužné automatizaci, použijte `sudo ./rtvs-install -s`.

1. Povolit a spustit službu:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Konfigurace certifikátu SSL (povinné pro produkční prostředí). Ve výchozím nastavení, démonů rtvs používá `ssl-cert-snakeoil.pem` a `ssl-cert-snakeoil.pem` generovaných `ssl-cert` balíčku. Během instalace, jsou sloučeny do `ssl-cert-snakeoil.pfx`. Pro produkční účely používejte certifikát SSL poskytnutých vaším správcem. Certifikát SSL můžete nakonfigurovat tím, že poskytuje *.pfx* souboru a volitelný import heslo: */etc/rtvs/rtvsd.config.json*.

1. (Volitelné) Zkontrolujte, zda je spuštěna služba:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Pokud nevidíte proces běžící pod uživatelské jméno `rtvssvc`. Spusťte ji pomocí následujícího příkazu:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Další konfiguraci démona rtvs, naleznete v tématu `man rtvsd`.

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Virtuální počítač s Ubuntu serverem nebo virtuálním počítači v Azure pro datové vědy

#### <a name="create-a-vm"></a>Vytvoření virtuálního počítače

1. Přihlaste se k [webu Azure portal](https://portal.azure.com).
1. Přejděte na virtuální počítače a pak vyberte **přidat**.
1. V seznamu dostupných imagí virtuálních počítačů vyhledejte a vyberte jednu z následujících akcí:
    - Server se systémem Ubuntu: `Ubuntu Server 16.04 LTS`
    - Virtuální počítač pro datové vědy: `Linux Data Science` (viz [virtuální počítače pro datové vědy](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) podrobnosti)
1. Nastavte na model nasazení `Resource manager` a vyberte **vytvořit**.
1. Zvolte název pro virtuální počítač, zadejte uživatelské jméno a heslo (heslo je povinné, jako SSH veřejného klíče přihlašovací jméno není podporováno).
1. Proveďte další požadované změny v konfiguraci virtuálního počítače.
1. Výběr velikosti virtuálního počítače, zkontrolujte konfiguraci a vyberte **vytvořit**. Po vytvoření virtuálního počítače přejděte k další části.

#### <a name="configure-the-vm"></a>Konfigurace virtuálního počítače

1. Na virtuálním počítači **sítě** části, přidejte 5444 jako povolený příchozí port. Pokud chcete použít jiný port, změňte nastavení v konfiguračním souboru RTVS démon (*/etc/rtvs/rtvsd.config.json*).
1. (Volitelné) Nastavení názvu DNS; Můžete také použít IP adresu.
1. Připojení k virtuálnímu počítači pomocí klienta SSH, jako je například PuTTY pro systém WIndows.
1. Postupujte podle pokynů [Ubuntu fyzické počítače](#physical-ubuntu-computer) výše.

### <a name="windows-subsystem-for-linux-wsl"></a>Subsystém Windows pro Linux (WSL)

1. Postupujte podle pokynů WSL buď [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) nebo [systému Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Spusťte prostředí bash ve Windows a postupujte podle předchozích pokynů [Ubuntu fyzické počítače](#physical-ubuntu-computer) s jednou výjimkou. Krok 3, spusťte službu pomocí příkazu `rtvsd`místo toho protože WSL aktuálně nepodporuje systemd/systemctl rozhraní.

### <a name="local-or-remote-docker-container-clean-build"></a>Místním nebo vzdáleném kontejneru Dockeru (čisté sestavení)

1. Vytvořit soubor Docker s následujícím obsahem, který se nainstaluje služba démona Vzdálená služba R a nejnovější verzi jazyka R. **Poznámka**: Tento skript vytvoří uživatele "ruser1" heslo "panel", který můžete upravit podle potřeby v poslední dvě `RUN` příkazy.

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. Sestavte a spusťte soubor docker:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Pro připojení k obsahuje z RTVS, použijte `https://localhost:5444` jako cestu, uživatelské jméno `<<unix>>\ruser1`a heslo `foobar`. Pokud je kontejner spuštěný na vzdáleném počítači, použijte `https://remote-host-name:5444` jako cestu místo. Port, který lze změnit aktualizováním */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Kontejneru spuštěného v Azure Container Instances

1. Postupujte podle pokynů v [místním nebo vzdáleném kontejneru Dockeru (čisté sestavení)](#local-or-remote-docker-container-clean-build) k vytvoření této image.
1. Nahrání kontejneru do Docker hubu nebo služby kontejneru úložiště Azure.
1. Spuštění rozhraní příkazového řádku Azure a přihlaste se pomocí `az login` příkazu.
1. Použití `az container create` příkaz pro vytvoření kontejneru, pomocí `--command-line "rtvsd"` Pokud jste nenastavili kontejner pro spuštění `rtvsd` jako `systemd` služby. V následujícím příkazu je na obrázku má být v Docker hubu. Kontejner úložiště Azure můžete použít také tak, že přidáte argumenty kontejneru úložiště přihlašovacích údajů do příkazového řádku.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```
1. Použití `az container list` příkaz a zkontrolujte stav. Vyhledejte `provisioningState`: `Succeeded`.
1. Pokud Zřizování proběhlo úspěšně, je možné připojit se ke kontejneru. Vyhledejte veřejnou IP adresu v `ipAddress` pole, který použijete pro připojení ke kontejneru z RTVS s přihlašovacími údaji v souboru docker.

