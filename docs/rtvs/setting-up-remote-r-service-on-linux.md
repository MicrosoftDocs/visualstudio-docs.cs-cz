---
title: Nastavení vzdálené služby R na Linuxu
description: Jak nastavit vzdálenou službu R pro Ubuntu a podsystém Windows pro Linux.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c4d65388db0ef90f807ec85b8c9216d717c2b571
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809554"
---
# <a name="remote-r-service-for-linux"></a>Vzdálená služba R pro Linux

Vzdálená služba R pro Linux je v současné době zabalena jako rtvs-daemon. Daemon je podporován a testován na Ubuntu 16.04, 16.10 LTS desktop, server a Podsystém Windows pro Linux se systémem Ubuntu. Převážná část tohoto článku obsahuje pokyny pro nastavení vzdálené služby R v těchto různých systémech.

Po konfiguraci vzdáleného počítače připojte k této službě následující kroky nástroje R pro visual studio (RTVS):

1. Vyberte **Nástroje Nástroje** > **Windows** > **Pracovní prostory** otevřete okno **Pracovní prostory.**
1. Vyberte **Přidat připojení**.
1. Pojmenujte připojení a zadejte jeho `https://localhost:5444` adresu URL, například `https://public-ip:5444` (Podsystém Windows pro Linux) nebo (kontejner Azure). Po dokončení vyberte **Uložit.**
1. Vyberte ikonu připojení nebo poklepejte na položku připojení.
1. Zadejte přihlašovací údaje. Uživatelské jméno musí být `<<unix>>\` předponou jako v `<<unix>>\ruser1` (jak je požadováno pro všechna připojení ke vzdáleným počítačům SIP).
1. Pokud používáte certifikát podepsaný svým držitelem, může se zobrazit upozornění. Zpráva obsahuje pokyny k opravě upozornění.

## <a name="set-up-remote-r-service"></a>Nastavit vzdálenou službu R

Tato část popisuje následující možnosti:

- [Fyzický počítač Ubuntu](#physical-ubuntu-computer)
- [Virtuální počítač Ubuntu Server nebo virtuální počítač pro datové vědy v Azure](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [Místní nebo vzdálený kontejner Dockeru (čisté sestavení)](#local-or-remote-docker-container-clean-build)
- [Kontejner spuštěný v instanci kontejnerů Azure](#container-running-on-azure-container-instances)

V každém případě musí být ve vzdáleném počítači nainstalován jeden z následujících překladačů R:

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R pro Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>Fyzický počítač Ubuntu

1. Po přihlášení do počítače, stáhněte si rtvs-daemon tarball:

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. Spusťte instalační skript:

    ```bash
    sudo ./rtvs-install
    ```

    Pro tichou automatizaci použijte `sudo ./rtvs-install -s`.

1. Povolit a spustit službu:

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. Konfigurace certifikátu SSL (vyžadováno pro produkční prostředí). Ve výchozím nastavení rtvs-daemon používá `ssl-cert-snakeoil.pem` a `ssl-cert` `ssl-cert-snakeoil.pem` generované balíček. Během instalace jsou kombinovány `ssl-cert-snakeoil.pfx`do . Pro produkční účely použijte certifikát SSL poskytnutý správcem. Certifikát SSL lze nakonfigurovat zadáním souboru *.pfx* a volitelného hesla pro import v: */etc/rtvs/rtvsd.config.json*.

1. (Nepovinné) Zkontrolujte, zda je služba spuštěna:

    ```bash
    ps -A -f | grep rtvsd
    ```

    Pokud nevidíte proces spuštěný pod uživatelským jménem `rtvssvc`. Spusťte jej pomocí následujícího příkazu:

    ```bash
    sudo systemctl start rtvsd
    ```

1. Další konfigurace rtvs-daemonu `man rtvsd`naleznete v tématu .

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Virtuální počítač Ubuntu Server nebo virtuální počítač pro datové vědy v Azure

#### <a name="create-a-vm"></a>Vytvoření virtuálního počítače

1. Přihlaste se k [portálu Azure](https://portal.azure.com).
1. Přejděte na Virtuální počítače a pak vyberte **Přidat**.
1. V seznamu dostupných iktovisl virtuálních vás vyhledá a vybere jednu z následujících možností:
    - Ubuntu Server:`Ubuntu Server 16.04 LTS`
    - Virtuální počítač pro `Linux Data Science` datové vědy: (podrobnosti najdete ve [virtuálních počítačích pro datové vědy)](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/)
1. Nastavte model nasazení `Resource manager` na a vyberte **Vytvořit**.
1. Zvolte název virtuálního počítače, zadejte uživatelské jméno a heslo (heslo je povinné, protože přihlášení veřejného klíče SSH není podporováno).
1. Proveďte jakékoli další požadované změny konfigurace virtuálního počítače.
1. Zvolte velikost virtuálního počítače, ověřte konfiguraci a vyberte **Vytvořit**. Po vytvoření virtuálního virtuálního masivu přejděte k další části.

#### <a name="configure-the-vm"></a>Nakonfigurování virtuálního počítače

1. V části **Síť** virtuálního zařízení přidejte 5444 jako povolený příchozí port. Chcete-li použít jiný port, změňte nastavení v konfiguračním souboru daemonu RTVS (*/etc/rtvs/rtvsd.config.json*).
1. (Nepovinné) Nastavte název DNS; můžete také použít IP adresu.
1. Připojte se k virtuálnímu virtuálnímu zařízení pomocí klienta SSH, jako je například PuTTY pro WIndows.
1. Postupujte podle pokynů pro [fyzický počítač Ubuntu](#physical-ubuntu-computer) výše.

### <a name="windows-subsystem-for-linux-wsl"></a>Windows Subsystem pro Linux (WSL)

1. Postupujte podle pokynů k instalaci wsl pro [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) nebo [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl).
1. Spusťte bash na Windows a postupujte podle dřívějších pokynů [fyzický počítač Ubuntu](#physical-ubuntu-computer) s jednou výjimkou. V kroku 3 spusťte `rtvsd`službu pomocí příkazu, protože WSL aktuálně nepodporuje rozhraní systemd/systemctl.

### <a name="local-or-remote-docker-container-clean-build"></a>Místní nebo vzdálený kontejner Dockeru (čisté sestavení)

1. Vytvořte soubor Docker u níže uvedeného obsahu, který nainstaluje daemon služby Remote R a nejnovější verzi R. **Poznámka**: tento skript vytvoří uživatele s názvem `RUN` "ruser1" s heslem "foobar", které můžete upravit podle potřeby v posledních dvou příkazech.

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

1. Vytvořte a spusťte soubor dockeru:

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. Chcete-li se připojit k obsahuje `https://localhost:5444` z RTVS, použijte jako cestu, uživatelské jméno `<<unix>>\ruser1`a heslo `foobar`. Pokud je kontejner spuštěn ve vzdáleném počítači, použijte `https://remote-host-name:5444` místo toho jako cestu. Port lze změnit aktualizací */etc/rtvs/rtvsd.config.json*.

### <a name="container-running-on-azure-container-instances"></a>Kontejner spuštěný v instanci kontejnerů Azure

1. Podle pokynů v [místním nebo vzdáleném kontejneru Dockeru (čisté sestavení)](#local-or-remote-docker-container-clean-build) vytvořte image.
1. Převeličte kontejner do centra Docker u centra nebo úložiště kontejnerů Azure.
1. Spusťte azure cli a `az login` přihlaste se pomocí příkazu.
1. Pomocí `az container create` příkazu vytvořte kontejner `--command-line "rtvsd"` pomocí, pokud jste nenastavili kontejner spustit `rtvsd` jako službu. `systemd` V níže uvedeném příkazu se očekává, že obraz bude v centru Dockeru. Úložiště kontejnerů Azure můžete také použít přidáním argumentů pověření úložiště kontejnerů do příkazového řádku.

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. Pomocí `az container list` příkazu zkontrolujte stav. Podívejte `provisioningState`se `Succeeded`na : .
1. Pokud zřizování proběhlo úspěšně, můžete se nyní připojit ke kontejneru. Vyhledejte veřejnou IP adresu `ipAddress` v poli, které používáte s pověřeními v souboru dockeru pro připojení ke kontejneru z RTVS.
