---
title: Ladění .NET Core v Linuxu
description: K ladění .NET Core v systému Linux použijte Secure Shell (SSH) připojením k procesu. Připravte aplikaci pro ladění. Sestavte a nasaďte aplikaci. Připojte ladicí program.
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bde5bb8722e0f95a10991019bdc9cba9c8a48ec3
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204888"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Ladění .NET Core v systému Linux pomocí SSH připojením k procesu

Od sady Visual Studio 2017 se můžete připojit k procesům .NET Core běžícím na místním nebo vzdáleném nasazení Linux přes SSH. Tento článek popisuje, jak nastavit ladění a jak ladit. Pro scénáře ladění pomocí kontejnerů Docker použijte místo toho příkaz [připojit k procesu spuštěnému v kontejneru Docker](../debugger/attach-to-process-running-in-docker-container.md) .

## <a name="prerequisites"></a>Požadavky

- V počítači se systémem Visual Studio je potřeba nainstalovat jak úlohu **vývoj pro ASP.NET, tak webové** prostředí a **vývoj aplikací .NET Core pro různé platformy** .

- Na serveru se systémem Linux je nutné nainstalovat server SSH, rozbalit a nainstalovat buď s kudrlinkou, nebo wget. Například na Ubuntu můžete to provést spuštěním:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- Na serveru Linux [nainstalujte modul runtime .NET v systému Linux](/dotnet/core/install/linux)a Najděte stránku, která odpovídá distribuci systému Linux (například Ubuntu). Sada .NET SDK není povinná.

- Podrobné pokyny pro ASP.NET Core najdete v tématu [hostitelská ASP.NET Core v systému Linux s Nginx](/aspnet/core/host-and-deploy/linux-nginx) a [Host ASP.NET Core v systému Linux s Apache](/aspnet/core/host-and-deploy/linux-apache).

## <a name="prepare-your-application-for-debugging"></a>Příprava aplikace pro ladění

Příprava aplikace pro ladění:

- Zvažte použití konfigurace ladění při sestavování aplikace. Je mnohem obtížnější ladit kód kompilovaný v maloobchodě (konfigurace vydané verze) než ladicí kód kompilovaný. Pokud potřebujete použít konfiguraci vydané verze, nejdřív zakažte Pouze můj kód. Chcete-li toto nastavení zakázat, zvolte možnost **nástroje**  >    >  **ladění** a potom zrušte zaškrtnutí možnosti **Povolit pouze můj kód**.

- Ujistěte se, že je projekt nakonfigurován tak, aby vytvořil [přenosné soubory PDB](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (což je výchozí nastavení), a ujistěte se, že je soubory PDB ve stejném umístění jako knihovna DLL. Pokud chcete tuto možnost nakonfigurovat v aplikaci Visual Studio, klikněte pravým tlačítkem na projekt a pak zvolte **vlastnosti**  >  **sestavit**  >  **Pokročilé**  >  **ladicí informace**.

## <a name="build-and-deploy-the-application"></a>Sestavení a nasazení aplikace

K nasazení aplikace před laděním můžete použít několik metod. Můžete například:

- Zkopírujte zdroje do cílového počítače a sestavte ```dotnet build``` je v počítači se systémem Linux.

- Sestavte aplikaci ve Windows a pak přeneste artefakty sestavení do počítače se systémem Linux. (Artefakty sestavení se skládají z samotné aplikace, přenosných soubory PDB, knihoven za běhu, na kterých může záviset, a *.deps.jsv* souboru.)

Po nasazení aplikace spusťte aplikaci.

## <a name="attach-the-debugger"></a>Připojit ladicí program

Když je aplikace spuštěna v počítači se systémem Linux, jste připraveni k připojení ladicího programu.

1. V aplikaci Visual Studio vyberte možnost **ladění**  >  **připojit k procesu...**.

1. V seznamu **Typ připojení** vyberte **SSH**.

1. Změňte **cíl připojení** na IP adresu nebo název hostitele cílového počítače.

   Pokud jste ještě nezadali přihlašovací údaje, zobrazí se výzva k zadání hesla nebo souboru privátního klíče.

   Nejsou k dispozici žádné požadavky na port ke konfiguraci, s výjimkou portu, ve kterém je spuštěný Server SSH.

1. Vyhledejte proces, který chcete ladit.

   Váš kód běží buď v jedinečném názvu procesu, nebo v procesu s názvem dotnet. Pokud chcete zjistit, který proces vás zajímá, podívejte se do sloupce **název** , který zobrazuje argumenty příkazového řádku pro daný proces.

   V následujícím příkladu se zobrazí seznam procesů ze vzdáleného počítače se systémem Linux přes přenos SSH zobrazený v dialogovém okně **připojit k procesu** .

   ![Připojit k procesu Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Klikněte na tlačítko **připojit**.

1. V dialogovém okně, které se zobrazí, vyberte typ kódu, který chcete ladit. Vyberte možnost **Managed (.NET Core pro UNIX)**.

1. K ladění aplikace použijte funkce ladění sady Visual Studio.

   V následujícím příkladu vidíte, že ladicí program sady Visual Studio byl zastaven na zarážce v kódu spuštěném na vzdáleném počítači se systémem Linux.

   ![Stiskněte zarážku](media/remote-debug-linux-over-ssh-hit-breakpoint.png)