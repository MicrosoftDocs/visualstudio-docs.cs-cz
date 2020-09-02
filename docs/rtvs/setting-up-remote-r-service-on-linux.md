---
title: Nastavení vzdálené služby R v systému Linux
description: Jak nastavit vzdálenou službu R v Ubuntu a subsystému Windows pro Linux.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c4d65388db0ef90f807ec85b8c9216d717c2b571
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62809554"
---
# <a name="remote-r-service-for-linux"></a>Vzdálená služba R pro Linux

Vzdálená služba R pro Linux je aktuálně zabalená jako RTVS-démon. Démon je podporován a testován v Ubuntu 16,04, 16,10 LTS Desktop, server a Windows pro Linux se systémem Ubuntu. Hromadný článek poskytuje pokyny pro nastavení vzdálené služby R v těchto různých systémech.

Po nakonfigurování vzdáleného počítače připojí následující postup Nástroje R pro Visual Studio (RTVS) k této službě:

1. Vyberte **nástroje R**  >  **Windows**  >  **pracovní prostory** Windows pro otevření okna **pracovní prostory** .
1. Vyberte **Přidat připojení**.
1. Zadejte název připojení a zadejte jeho adresu URL, například `https://localhost:5444` (subsystém Windows pro Linux) nebo `https://public-ip:5444` (kontejner Azure). Po dokončení vyberte **Uložit** .
1. Vyberte ikonu připojení nebo dvakrát klikněte na položku připojení.
1. Zadejte přihlašovací údaje. Uživatelské jméno musí být s předponou `<<unix>>\` (podle `<<unix>>\ruser1` potřeby pro všechna připojení ke vzdáleným počítačům se systémem Linux).
1. Pokud používáte certifikát podepsaný svým držitelem, může se zobrazit upozornění. Zpráva poskytuje pokyny k opravě upozornění.

## <a name="set-up-remote-r-service"></a>Nastavení vzdálené služby R

Tato část popisuje následující možnosti:

- [Fyzický Ubuntu počítač](#physical-ubuntu-computer)
- [Virtuální počítač Ubuntu serveru nebo Data Science VM v Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Místní nebo vzdálený kontejner Docker (Vyčištění sestavení)](#local-or-remote-docker-container-clean-build)
- [Kontejner běžící na Azure Container Instances](#container-running-on-azure-container-instances)

V každém případě musí mít vzdálený počítač nainstalovanou jednu z následujících překladačů R:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R pro Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Fyzický Ubuntu počítač

1. Po přihlášení k počítači stáhněte RTVS-démon tarballu:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Spusťte instalační skript:

    ```bash
    sudo ./rtvs-install
    ```

    Pro tichou automatizaci použijte `sudo ./rtvs-install -s` .

1. Povolte a spusťte službu:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Nakonfigurujte certifikát SSL (vyžaduje se pro produkční prostředí). Ve výchozím nastavení používá RTVS-démon rozhraní `ssl-cert-snakeoil.pem` a `ssl-cert-snakeoil.pem` generované `ssl-cert` balíčkem. Během instalace se sloučí do `ssl-cert-snakeoil.pfx` . Pro produkční účely použijte certifikát SSL poskytnutý vaším správcem. Certifikát SSL se dá nakonfigurovat tak, že poskytuje soubor *. pfx* a volitelné heslo pro import v: */etc/RTVS/rtvsd.config.jszapnuté*.

1. Volitelné Ověřte, že je služba spuštěná:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Pokud se pod uživatelským jménem nezobrazuje proces, který je spuštěný `rtvssvc` . Spusťte ji pomocí následujícího příkazu:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Další konfiguraci RTVS-démon naleznete v tématu `man rtvsd` .

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Virtuální počítač Ubuntu serveru nebo Data Science VM v Azure

#### <a name="create-a-vm"></a>Vytvoření virtuálního počítače

1. Přihlaste se na web [Azure Portal](https://portal.azure.com).
1. Přejděte na Virtual Machines a pak vyberte **Přidat**.
1. V seznamu dostupných imagí virtuálních počítačů vyhledejte a vyberte jednu z následujících možností:
    - Ubuntu Server: `Ubuntu Server 16.04 LTS`
    - Data Science VM: `Linux Data Science` (podrobnosti najdete v [Virtual Machines pro datové vědy](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) )
1. Nastavte model nasazení na `Resource manager` a vyberte **vytvořit**.
1. Vyberte název virtuálního počítače, zadejte uživatelské jméno a heslo (vyžaduje se heslo, protože přihlášení k veřejnému klíči SSH není podporované).
1. Proveďte v konfiguraci virtuálního počítače jakékoli další požadované změny.
1. Zvolte velikost virtuálního počítače, ověřte konfiguraci a vyberte **vytvořit**. Až se virtuální počítač vytvoří, přejděte k další části.

#### <a name="configure-the-vm"></a>Nakonfigurování virtuálního počítače

1. V části **síť** virtuálního počítače přidejte 5444 jako povolený port pro příchozí spojení. Chcete-li použít jiný port, změňte nastavení v konfiguračním souboru démona RTVS (*/etc/rtvs/rtvsd.config.json*).
1. Volitelné Nastavit název DNS; Můžete také použít IP adresu.
1. Připojte se k virtuálnímu počítači pomocí klienta SSH, jako je například výstup pro systém WIndows.
1. Postupujte podle pokynů pro [fyzický počítač Ubuntu](#physical-ubuntu-computer) výše.

### <a name="windows-subsystem-for-linux-wsl"></a>Subsystém Windows pro Linux (WSL)

1. Postupujte podle pokynů k instalaci WSL buď pro [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) nebo [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Spusťte bash ve Windows a postupujte podle předchozích pokynů pro [fyzický Ubuntu počítač](#physical-ubuntu-computer) s jednou výjimkou. V kroku 3 Spusťte službu pomocí příkazu, `rtvsd` protože WSL aktuálně nepodporuje rozhraní systemed/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Místní nebo vzdálený kontejner Docker (Vyčištění sestavení)

1. Vytvořte soubor Docker s níže uvedeným obsahem, který nainstaluje démona vzdálené služby R a nejnovější verzi R. **Poznámka**: Tento skript vytvoří uživatele s názvem "ruser1" s heslem "panel", který můžete v posledních dvou příkazech upravit podle potřeby `RUN` .

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

1. Sestavte a spusťte soubor Docker:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Pokud se chcete připojit k adresáři Contains z RTVS, použijte `https://localhost:5444` jako cestu, uživatelské jméno `<<unix>>\ruser1` a heslo `foobar` . Pokud je kontejner spuštěn ve vzdáleném počítači, použijte `https://remote-host-name:5444` místo toho jako cestu. Port lze změnit aktualizací *rtvsd.config.js/etc/RTVS/on*.

### <a name="container-running-on-azure-container-instances"></a>Kontejner běžící na Azure Container Instances

1. Pokud chcete vytvořit image, postupujte podle pokynů v [místním nebo vzdáleném kontejneru Docker (Vyčištění sestavení)](#local-or-remote-docker-container-clean-build) .
1. Nahrajte kontejner do Docker Hub nebo do úložiště kontejnerů Azure.
1. Spusťte rozhraní příkazového řádku Azure a přihlaste se pomocí `az login` příkazu.
1. Pomocí `az container create` příkazu vytvořte kontejner, a to pomocí, pokud jste nevytvořili `--command-line "rtvsd"` kontejner pro spuštění `rtvsd` jako `systemd` služba. V následujícím příkazu se očekává, že obrázek bude v Docker Hub. Úložiště kontejnerů Azure můžete také použít tak, že do příkazového řádku přidáte argumenty pro přihlašovací údaje úložiště kontejnerů.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. `az container list`Ke kontrole stavu použijte příkaz. Hledat `provisioningState` : `Succeeded` .
1. Pokud se zřizování podařilo, můžete se nyní připojit ke kontejneru. Vyhledejte veřejnou IP adresu v `ipAddress` poli, které použijete s přihlašovacími údaji v souboru Docker pro připojení ke kontejneru z RTVS.
