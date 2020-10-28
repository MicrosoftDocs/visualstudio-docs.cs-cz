---
title: Vzdálené ladění .NET Core v systému Linux | Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d66181f5e6720348e18c34b735ef29e24c0111a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796300"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Vzdálené ladění .NET Core na platformě Linux pomocí SSH

Od sady Visual Studio 2017 se můžete připojit k procesům .NET Core běžícím na Linux přes SSH. Tento článek popisuje, jak nastavit ladění a jak ladit.

## <a name="prerequisites"></a>Předpoklady

V počítači se systémem Visual Studio je potřeba nainstalovat jak úlohu **vývoj pro ASP.NET, tak webové** prostředí a **vývoj aplikací .NET Core pro různé platformy** .

Na serveru se systémem Linux je nutné nainstalovat server SSH, rozbalit a nainstalovat buď s kudrlinkou, nebo wget. Například na Ubuntu můžete to provést spuštěním:

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Sestavení a nasazení aplikace

Příprava aplikace pro ladění:

- Zvažte použití konfigurace ladění při sestavování aplikace. Je mnohem obtížnější ladit kód kompilovaný v maloobchodě (konfigurace vydané verze) než ladicí kód kompilovaný. Pokud potřebujete použít konfiguraci vydané verze, nejdřív zakažte Pouze můj kód. Chcete-li toto nastavení zakázat, zvolte možnost **nástroje**  >  **Options**  >  **ladění** a potom zrušte zaškrtnutí možnosti **Povolit pouze můj kód** .

- Ujistěte se, že je projekt nakonfigurován tak, aby vytvořil [přenosné soubory PDB](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) (což je výchozí nastavení), a ujistěte se, že je PBDs ve stejném umístění jako knihovna DLL. Pokud chcete tuto možnost nakonfigurovat v aplikaci Visual Studio, klikněte pravým tlačítkem na projekt a pak zvolte **vlastnosti**  >  **sestavit**  >  **Pokročilé**  >  **ladicí informace** .

K nasazení aplikace před laděním můžete použít několik metod. Můžete například:

- Zkopírujte zdroje do cílového počítače a sestavte ```dotnet build``` je v počítači se systémem Linux.

- Sestavte aplikaci ve Windows a pak přeneste artefakty sestavení do počítače se systémem Linux. (Artefakty sestavení se skládají z samotné aplikace, všechny běhové knihovny, na kterých může záviset, a *.deps.jsv* souboru.)

## <a name="attach-the-debugger"></a>Připojit ladicí program

Po nakonfigurování počítačů spusťte aplikaci na počítači se systémem Linux a potom jste připraveni připojit ladicí program.

1. V aplikaci Visual Studio vyberte možnost **ladění**  >  **připojit k procesu...** .

1. V seznamu **Typ připojení** vyberte **SSH** .

1. Změňte **cíl připojení** na IP adresu nebo název hostitele cílového počítače.

1. Vyhledejte proces, který chcete ladit.

   Váš kód běží buď v jedinečném názvu procesu, nebo v procesu s názvem dotnet. Pokud chcete zjistit, který proces vás zajímá, podívejte se do sloupce **název** , který zobrazuje argumenty příkazového řádku pro daný proces.

   V následujícím příkladu se zobrazí seznam procesů ze vzdáleného počítače se systémem Linux přes přenos SSH zobrazený v dialogovém okně **připojit k procesu** .

   ![Připojit k procesu Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Klikněte na tlačítko **připojit** .

1. V dialogovém okně, které se zobrazí, vyberte typ kódu, který chcete ladit. Vyberte možnost **Managed (.NET Core pro UNIX)** .

1. K ladění aplikace použijte funkce ladění sady Visual Studio.

   V následujícím příkladu vidíte, že ladicí program sady Visual Studio byl zastaven na zarážce v kódu spuštěném na vzdáleném počítači se systémem Linux.

   ![Stiskněte zarážku](media/remote-debug-linux-over-ssh-hit-breakpoint.png)