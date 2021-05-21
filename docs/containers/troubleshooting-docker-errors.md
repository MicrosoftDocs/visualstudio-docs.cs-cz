---
title: Poradce při potížích s chybami klienta Docker ve Windows | Microsoft Docs
description: Řešení problémů, ke kterým dochází při používání sady Visual Studio k vytvoření a nasazení webových aplikací do Docker ve Windows pomocí sady Visual Studio.
ms.technology: vs-azure
author: ghogen
manager: jmartens
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 5f48b5c06e91b9c05e6edc7e2a1738aeb677a7ba
ms.sourcegitcommit: 69456d802203d21dabc3ae8662547a3241c24f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2021
ms.locfileid: "110235908"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Řešení potíží při vývoji v sadě Visual Studio pomocí Dockeru

Při práci s nástroji kontejneru sady Visual Studio může při sestavování nebo ladění aplikace dojít k problémům. Níže jsou uvedeny některé běžné kroky při řešení potíží.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Sdílení svazků není povoleno. Povolit sdílení svazků v nastaveních Docker CE for Windows (jenom kontejnery Linux)

Sdílení souborů je potřeba spravovat jenom v případě, že používáte Hyper-V s Docker. Pokud používáte WSL 2, následující kroky nejsou nutné a možnost sdílení souborů nebude viditelná. Řešení tohoto problému:

1. V oznamovací oblasti klikněte pravým tlačítkem na **Docker for Windows** a pak vyberte **Nastavení**.
1. Vyberte **prostředky**  >  **sdílení souborů** a nasdílejte složku, ke které je potřeba mít přístup. Sdílení celé systémové jednotky je možné, ale nedoporučuje se.

    :::image type="content" source="media//troubleshooting-docker-errors/docker-settings-image.png" alt-text="Sdílené jednotky":::

> [!TIP]
> Verze sady Visual Studio vyšší než Visual Studio 2017 verze 15,6 se zobrazí výzva, když nejsou nakonfigurovány **sdílené jednotky** .

## <a name="unable-to-start-debugging"></a>Nejde spustit ladění

Jedním z důvodů může souviset se zastaralými součástmi ladění ve složce profilu uživatele. Spusťte následující příkazy, abyste tyto složky odebrali, aby se nejnovější ladicí komponenty stáhly do další relace ladění.

- del%USERPROFILE%\vsdbg
- del%USERPROFILE%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Chyby specifické pro sítě při ladění aplikace

Zkuste provést stažení skriptu z části [vyčistit síťové hostitele kontejneru](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), čímž aktualizujete součásti související se sítí na hostitelském počítači.

## <a name="mounts-denied"></a>Připojení byla zamítnuta.

Při použití Dockeru pro macOS může dojít k chybě odkazující na složku /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Přidejte složku na kartu Sdílení souborů v Dockeru.

## <a name="docker-users-group"></a>Skupina uživatelů Dockeru

Při práci s kontejnery se může Visual Studio následující chyba:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Abyste mohli pracovat s kontejnery Dockeru, musíte být členem skupiny docker-users.  Pokud se chcete přidat do skupiny v Windows 10, postupujte takto:

1. V nabídka Start otevřete Správu **počítače**.
1. Rozbalte **Místní uživatelé a skupiny** a zvolte **Skupiny.**
1. Vyhledejte **skupinu docker-users,** klikněte pravým tlačítkem a zvolte **Přidat do skupiny**.
1. Přidejte svůj uživatelský účet nebo účty.
1. Odhlásit se a znovu se přihlásit, aby se tyto změny projeví.

K přidání uživatelů do konkrétních skupin můžete také použít příkaz na příkazovém řádku `net localgroup` správce.

```cmd
net localgroup docker-users DOMAIN\username /add
```

V PowerShellu použijte [funkci Add-LocalGroupMember.](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)

## <a name="low-disk-space"></a>Nedostatek místa na disku

Docker ve výchozím nastavení ukládá image do *složky %ProgramData%/Docker/,* která je obvykle na systémové jednotce, *C:\ProgramData\Docker. \* Pokud chcete zabránit tomu, aby image zabraňy zachytát cenné místo na systémové jednotce, můžete změnit umístění složky image. Postupujte následovně:

 1. Klikněte pravým tlačítkem na ikonu Dockeru na hlavním panelu a vyberte **Nastavení**.
 1. Vyberte **Docker Engine**. 
 1. V podokně pro úpravy přidejte `graph` nastavení vlastnosti s hodnotou požadovaného umístění pro image Dockeru:

```json
    "graph": "D:\\mypath\\images"
```

:::image type="content" source="media/troubleshooting-docker-errors/docker-daemon-settings.png" alt-text="Snímek obrazovky se sdílením souborů Dockeru":::

Klikněte na **použít & restartovat**. Tyto kroky upraví konfigurační soubor v umístění *% Složka ProgramData% \docker\config\daemon.jsna*. Dříve sestavené obrázky nejsou přesunuty.

## <a name="container-type-mismatch"></a>Neshoda typu kontejneru

Když do projektu přidáte podporu Docker, zvolíte buď kontejner Windows, nebo Linux. Pokud hostitel serveru Docker není nakonfigurován tak, aby spouštěl stejný typ kontejneru jako cíl projektu, pravděpodobně se zobrazí chyba podobná té:

:::image type="content" source="media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png" alt-text="Snímek obrazovky hostitele Docker a projektu nesouhlasí":::

Řešení tohoto problému:

- Na hlavním panelu systému klikněte pravým tlačítkem na ikonu Docker for Windows a vyberte **Přepnout na kontejnery Windows...** nebo **Přepnout na kontejnery platformy Linux..**..

## <a name="microsoftdockertools-github-repo"></a>Úložiště GitHub pro Microsoft/DockerTools

Další problémy, se kterými se setkáte, najdete v článku problémy s  [Microsoftem a DockerTools](https://github.com/microsoft/dockertools/issues) .

## <a name="see-also"></a>Viz také

- [Řešení potíží s Visual Studiem](/troubleshoot/visualstudio/welcome-visual-studio/)
