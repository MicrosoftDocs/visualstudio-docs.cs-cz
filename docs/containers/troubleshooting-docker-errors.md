---
title: Poradce při potížích s chybami klienta Docker ve Windows | Microsoft Docs
description: Řešení problémů, ke kterým dochází při používání sady Visual Studio k vytvoření a nasazení webových aplikací do Docker ve Windows pomocí sady Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 9535a7d88cb375d97867092eddf969095c327329
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729242"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Řešení potíží při vývoji v sadě Visual Studio pomocí Dockeru

Při práci s nástroji kontejneru sady Visual Studio může při sestavování nebo ladění aplikace dojít k problémům. Níže jsou uvedeny některé běžné kroky při řešení potíží.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Sdílení svazků není povoleno. Povolit sdílení svazků v nastaveních Docker CE for Windows (jenom kontejnery Linux)

Sdílení souborů je potřeba spravovat jenom v případě, že používáte Hyper-V s Docker. Pokud používáte WSL 2, následující kroky nejsou nutné a možnost sdílení souborů nebude viditelná. Řešení tohoto problému:

1. V oznamovací oblasti klikněte pravým tlačítkem na **Docker for Windows** a pak vyberte **Nastavení**.
1. Vyberte **prostředky**  >  **sdílení souborů** a nasdílejte složku, ke které je potřeba mít přístup. Sdílení celé systémové jednotky je možné, ale nedoporučuje se.

    ![sdílené jednotky](media/troubleshooting-docker-errors/docker-settings-image.png)

> [!TIP]
> Verze sady Visual Studio vyšší než Visual Studio 2017 verze 15,6 se zobrazí výzva, když nejsou nakonfigurovány **sdílené jednotky** .

## <a name="unable-to-start-debugging"></a>Nejde spustit ladění

Jedním z důvodů může souviset se zastaralými součástmi ladění ve složce profilu uživatele. Spusťte následující příkazy, abyste tyto složky odebrali, aby se nejnovější ladicí komponenty stáhly do další relace ladění.

- del%USERPROFILE%\vsdbg
- del%USERPROFILE%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Chyby specifické pro sítě při ladění aplikace

Zkuste provést stažení skriptu z části [vyčistit síťové hostitele kontejneru](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), čímž aktualizujete součásti související se sítí na hostitelském počítači.

## <a name="mounts-denied"></a>Připojení byla zamítnuta.

Při použití Docker pro macOS se může zobrazit chyba odkazování na složku/usr/local/share/dotnet/sdk/NuGetFallbackFolder. Přidejte složku do karty sdílení souborů v Docker.

## <a name="docker-users-group"></a>Skupina uživatelů Docker

Při práci s kontejnery může dojít k následující chybě v aplikaci Visual Studio:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Abyste mohli mít oprávnění k práci s kontejnery Docker, musíte být členem skupiny Docker-Users.  Pokud se chcete do skupiny ve Windows 10 přidat sami, postupujte takto:

1. V nabídce Start otevřete položku **Správa počítače**.
1. Rozbalte položku **místní uživatelé a skupiny** a klikněte na možnost **skupiny**.
1. Vyhledejte skupinu **Docker-Users** , klikněte pravým tlačítkem myši a vyberte **Přidat do skupiny**.
1. Přidejte svůj uživatelský účet nebo účty.
1. Odhlaste se a znovu se přihlaste, aby se tyto změny projevily.

`net localgroup`K přidání uživatelů do konkrétních skupin můžete použít také příkaz na příkazovém řádku správce.

```cmd
net localgroup docker-users DOMAIN\username /add
```

V PowerShellu použijte funkci [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) .

## <a name="low-disk-space"></a>Nedostatek místa na disku

Ve výchozím nastavení Docker ukládá obrázky do složky *% Složka ProgramData%/Docker/* , která se obvykle nachází na systémové jednotce * C:\ProgramData\Docker \* . Pokud nechcete, aby obrázky zabíraly cenné místo na systémové jednotce, můžete změnit umístění složky s obrázkem. Postupujte následovně:

 1. Klikněte pravým tlačítkem na ikonu Docker na hlavním panelu a vyberte **Nastavení**.
 1. Vyberte **modul Docker**. 
 1. V podokně úpravy přidejte `graph` nastavení vlastnosti s hodnotou požadovaného umístění pro Image Docker:

```json
    "graph": "D:\\mypath\\images"
```

![Snímek obrazovky s sdílením souborů Docker](media/troubleshooting-docker-errors/docker-daemon-settings.png)

Klikněte na **použít & restartovat**. Tyto kroky upraví konfigurační soubor v umístění *% Složka ProgramData% \docker\config\daemon.jsna*. Dříve sestavené obrázky nejsou přesunuty.

## <a name="container-type-mismatch"></a>Neshoda typu kontejneru

Když do projektu přidáte podporu Docker, zvolíte buď kontejner Windows, nebo Linux. Pokud hostitel serveru Docker není nakonfigurován tak, aby spouštěl stejný typ kontejneru jako cíl projektu, pravděpodobně se zobrazí chyba podobná té:

![Snímek obrazovky hostitele Docker a projektu nesouhlasí](media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png)

Řešení tohoto problému:

- Na hlavním panelu systému klikněte pravým tlačítkem na ikonu Docker for Windows a vyberte **Přepnout na kontejnery Windows...** nebo **Přepnout na kontejnery platformy Linux..**..

## <a name="microsoftdockertools-github-repo"></a>Úložiště GitHub pro Microsoft/DockerTools

Další problémy, se kterými se setkáte, najdete v článku problémy s  [Microsoftem a DockerTools](https://github.com/microsoft/dockertools/issues) .

## <a name="see-also"></a>Viz také

- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)
