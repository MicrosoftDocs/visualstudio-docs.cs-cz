---
title: Řešení potíží s chybami klienta Docker ve Windows | Dokumentace Microsoftu
description: Řešení problémů, ke kterým dochází při používání sady Visual Studio k vytvoření a nasazení webových aplikací do Docker ve Windows pomocí sady Visual Studio.
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
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027272"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Řešení potíží při vývoji v sadě Visual Studio pomocí Dockeru

Při práci s nástroji kontejneru sady Visual Studio může při sestavování nebo ladění aplikace dojít k problémům. Níže jsou některé běžné kroků pro řešení potíží.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Sdílení svazků není povolené. Povolte sdílení svazků v nastavení Dockeru CE pro Windows (pouze pro kontejnery Linuxu)

K vyřešení tohoto problému:

1. V oznamovací oblasti klikněte pravým tlačítkem na **Docker for Windows** a pak vyberte **Nastavení**.
1. Vyberte **sdílené jednotky** a nasdílejte systémovou jednotku společně s jednotkou, ve které se nachází projekt.

> [!NOTE]
> Pokud se zdá, že sdílené soubory, můžete stále chcete-li znovu povolit sdílení svazků, klikněte na odkaz "Resetovat přihlašovací údaje …" v dolní části dialogového okna. Chcete-li pokračovat po resetování přihlašovacích údajů, budete muset restartovat Visual Studio.

![sdílené jednotky](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Verze sady Visual Studio novější než Visual Studio 2017 verze 15,6 se zobrazí výzva, když nejsou nakonfigurovány **sdílené jednotky** .

### <a name="container-type"></a>Typ kontejneru

Když do projektu přidáte podporu Docker, zvolíte buď kontejner Windows, nebo Linux. Hostitel Docker musí používat stejný typ kontejneru. Chcete-li změnit typ kontejneru v běžící instanci Docker, klikněte pravým tlačítkem myši na ikonu Docker panelu systému a vyberte možnost **Přepnout na kontejnery Windows...** nebo **Přepnout na kontejnery platformy Linux..** ..

## <a name="unable-to-start-debugging"></a>Nelze spustit ladění

Jedním z důvodů může souviset s tím, že komponenty zastaralé ladění ve složce profilu uživatele. Spusťte následující příkazy k odebrání těchto složek tak, aby se stáhnou nejnovější ladění komponenty na příští relaci ladění.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Chyby specifické pro sítě při ladění aplikace

Zkuste provést stažení skriptu z části [vyčistit síťové hostitele kontejneru](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), čímž aktualizujete součásti související se sítí na hostitelském počítači.

## <a name="mounts-denied"></a>Připojení byl odepřen

Při použití Dockeru pro macOS, pravděpodobně dojde k chybě odkazující na složku /usr/local/share/dotnet/sdk/NuGetFallbackFolder. Přidat složku na kartě Sdílení souborů v Dockeru

## <a name="docker-users-group"></a>Skupina uživatelů Docker

Při práci s kontejnery může dojít k následující chybě v aplikaci Visual Studio:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Abyste mohli mít oprávnění k práci s kontejnery Docker, musíte být členem skupiny Docker-Users.  Pokud se chcete do skupiny ve Windows 10 přidat sami, postupujte takto:

1. V nabídce Start otevřete položku **Správa počítače**.
1. Rozbalte položku **místní uživatelé a skupiny**a klikněte na možnost **skupiny**.
1. Vyhledejte skupinu **Docker-Users** , klikněte pravým tlačítkem myši a vyberte **Přidat do skupiny**.
1. Přidejte svůj uživatelský účet nebo účty.
1. Odhlaste se a znovu se přihlaste, aby se tyto změny projevily.

K přidání uživatelů do konkrétních skupin můžete použít také příkaz `net localgroup` na příkazovém řádku správce.

```cmd
net localgroup docker-users DOMAIN\username /add
```

V PowerShellu použijte funkci [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) .

## <a name="low-disk-space"></a>Nedostatek místa na disku

Ve výchozím nastavení Docker ukládá obrázky do složky *% Složka ProgramData%/Docker/* , která se obvykle nachází na systémové jednotce * C:\ProgramData\Docker\*. Pokud nechcete, aby obrázky zabíraly cenné místo na systémové jednotce, můžete změnit umístění složky s obrázkem.  Z ikony Docker na panelu úloh otevřete nastavení Docker, klikněte na **démon**a přepněte ze **základního** na **Upřesnit**. V podokně úpravy přidejte nastavení vlastnosti `graph` s hodnotou požadovaného umístění pro Image Docker:

```json
    "graph": "D:\\mypath\\images"
```

![Snímek obrazovky s nastavením umístění bitové kopie Docker](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Klikněte na **použít** a restartujte Docker. Tyto kroky upraví konfigurační soubor na adrese *%ProgramData%\docker\config\daemon.JSON*. Dříve sestavené obrázky nejsou přesunuty.

## <a name="microsoftdockertools-github-repo"></a>Úložiště GitHub Microsoft/DockerTools

Další problémy, se kterými se setkáte, najdete v článku problémy s [Microsoftem a DockerTools](https://github.com/microsoft/dockertools/issues) .