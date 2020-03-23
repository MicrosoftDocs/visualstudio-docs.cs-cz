---
title: Poradce při potížích s chybami klientů Dockeru v systému Windows | Dokumenty společnosti Microsoft
description: Poradce při potížích, se kterými se setkáte při vytváření a nasazování webových aplikací do Dockeru v Systému Windows pomocí Sady Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: d8aa3028a12bcfb49f2663b2bea688baf14fd7f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027272"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Řešení potíží při vývoji v sadě Visual Studio pomocí Dockeru

Při práci s visual studio kontejneru nástroje, může dojít k problémům při vytváření nebo ladění aplikace. Níže jsou uvedeny některé běžné kroky řešení potíží.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Sdílení svazků není povoleno. Povolení sdílení svazků v nastavení Dockeru CE pro Windows (jenom linuxové kontejnery)

Řešení tohoto problému:

1. V oznamovací oblasti klepněte pravým tlačítkem myši na **Docker pro Windows** a pak vyberte **Nastavení**.
1. Vyberte **Sdílené jednotky** a sdílejte systémovou jednotku spolu s jednotkou, na které se projekt nachází.

> [!NOTE]
> Pokud se soubory zobrazují jako sdílené, může být stále nutné kliknout na tlačítko Obnovit přihlašovací údaje. v dolní části dialogového okna, aby bylo možné znovu povolit sdílení svazků. Chcete-li pokračovat po obnovení pověření, bude pravděpodobně nutné restartovat visual studio.

![sdílené jednotky](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Verze sady Visual Studio novější než Visual Studio 2017 verze 15.6 se zobrazí výzva, když nejsou **nakonfigurovány sdílené jednotky.**

### <a name="container-type"></a>Typ kontejneru

Při přidávání podpory Dockeru do projektu zvolíte kontejner Windows nebo Linux. Hostitel Dockeru musí mít stejný typ kontejneru. Chcete-li změnit typ kontejneru v spuštěné instanci Dockeru, klikněte pravým tlačítkem myši na ikonu Dockeru na systémové majebru a zvolte **Přepnout do kontejnerů Windows...** nebo **Přepnout na linuxové kontejnery...**.

## <a name="unable-to-start-debugging"></a>Nejde spustit ladění

Jedním z důvodů může souviset s tím, že zastaralé ladění komponenty ve složce profilu uživatele. Spusťte následující příkazy k odebrání těchto složek tak, aby nejnovější ladicí součásti byly staženy na další relaci ladění.

- del %uživatelský profil%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Chyby specifické pro síť při ladění aplikace

Zkuste spustit skript ke stažení z [programu Cleanup Container Host Networking ,](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)který aktualizuje součásti související se sítí v hostitelském počítači.

## <a name="mounts-denied"></a>Připojení byla odepřena.

Při použití Dockeru pro macOS se může vyskytnat chyba odkazující na složku /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Přidání složky na kartu Sdílení souborů v Dockeru

## <a name="docker-users-group"></a>Skupina uživatelů Dockeru

Při práci s kontejnery se může v sadě Visual Studio vyskytnut následující chyba:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Abyste měli oprávnění k práci s kontejnery Dockeru, musíte být členem skupiny uživatelů dockeru.  Pokud se chcete přidat do skupiny ve Windows 10, postupujte takto:

1. V nabídce Start otevřete **položku Správa počítače**.
1. Rozbalte **položku Místní uživatelé a skupiny**a zvolte **Skupiny**.
1. Najděte skupinu **uživatelů dockeru,** klikněte pravým tlačítkem myši a zvolte **Přidat do skupiny**.
1. Přidejte svůj uživatelský účet nebo účty.
1. Tyto změny se projeví až znovu odhlaste a znovu se přihlaste.

Pomocí příkazu `net localgroup` na příkazovém řádku Správce můžete také přidat uživatele do určitých skupin.

```cmd
net localgroup docker-users DOMAIN\username /add
```

V Prostředí PowerShell použijte funkci [Add-LocalGroupMember.](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)

## <a name="low-disk-space"></a>Nedostatek místa na disku

Ve výchozím nastavení docker ukládá bitové kopie do složky *%ProgramData%/Docker/,* která je obvykle\*na systémové jednotce* C:\ProgramData\Docker . Chcete-li zabránit tomu, aby obrázky zabírají cenné místo na systémové jednotce, můžete změnit umístění složky obrázku.  Na ikoně Dockeru na hlavním panelu otevřete nastavení Dockeru, zvolte **Daemon**a přepněte ze **základního** na **rozšířený**. V podokně úprav přidejte nastavení `graph` vlastností s hodnotou požadovaného umístění pro image Dockeru:

```json
    "graph": "D:\\mypath\\images"
```

![Snímek obrazovky s nastavením umístění obrázku Dockeru](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Kliknutím na **Použít** restartujte Docker. Tyto kroky upravují konfigurační soubor na adrese *%ProgramData%\docker\config\daemon.json*. Dříve vytvořené obrazy nejsou přesunuty.

## <a name="microsoftdockertools-github-repo"></a>Úložiště Microsoft/DockerTools GitHub

Jakékoli další problémy, se kterými se setkáte, naleznete v tématu [Problémy microsoft/DockerTools.](https://github.com/microsoft/dockertools/issues)