---
title: Vzdálené ladění | Dokumentace Microsoftu
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9918a2de67693c0232c94a736f12c7af0a0b959c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409260"
---
# <a name="remote-debugging"></a>Vzdálené ladění
Můžete ladit aplikace Visual Studio, který byl nasazen na jiný počítač. K tomu použijete vzdálený ladicí program sady Visual Studio.

Podrobné pokyny pro vzdálené ladění naleznete v následujících tématech.

|Scénář|Odkaz|
|-|-|-|
|Azure App Service|[Snapshot Debugger](../debugger/debug-live-azure-applications.md) nebo [ASP.NET vzdáleného ladění v Azure](../debugger/remote-debugging-azure.md)|
|Virtuální počítač Azure|[Vzdálené ladění ASP.NET ve službě Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Ladění aplikace Service Fabric Azure](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Vzdálené ladění ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) nebo [vzdálené ladění ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# nebo Visual Basic|[Vzdálené ladění projektu v jazyce C# nebo Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Vzdálené ladění projektu v jazyce C++](../debugger/remote-debugging-cpp.md)|
|Aplikace pro Universal Windows (UPW)|[Spouštění aplikací pro UWP na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md) nebo [ladění nainstalovaného balíčku aplikace](../debugger/debug-installed-app-package.md)|

Pokud jenom chcete stáhnout a nainstalovat vzdáleného ladicího programu a není třeba žádné další pokyny pro váš scénář, postupujte podle kroků v tomto článku.

## <a name="download-and-install-the-remote-tools"></a>Stáhněte a nainstalujte nástroje remote tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements_msvsmon"></a>Požadavků

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a>Volitelné Spuštění vzdáleného ladicího programu ze sdílené složky

Vzdálený ladící program (*msvsmon. exe*) najdete na počítači, který je už nainstalovaný v prostředí Visual Studio Community, Professional nebo Enterprise. Pro některé scénáře je nejjednodušší způsob, jak nastavit vzdálené ladění spusťte vzdálený ladící program (msvsmon.exe) ze sdílené složky. Omezení použití najdete na stránce s nápovědu pro vzdálený ladicí program (**nápovědu > používání** ve vzdáleném ladicím programu).

1. Vyhledejte *msvsmon. exe* v adresáři, který odpovídá vaší verzi sady Visual Studio:

   ::: moniker range=">=vs-2019"

   *Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Nasdílejte složku **vzdáleného ladícího programu** na počítači se systémem Visual Studio.

3. Na vzdáleném počítači spusťte *msvsmon. exe* ze sdílené složky. Postupujte podle [pokynů k instalaci](#bkmk_setup).

> [!TIP]
> Informace o instalaci a příkazovém řádku příkazového řádku najdete na stránce s nápovědu pro *msvsmon. exe* zadáním ``msvsmon.exe /?`` v příkazovém řádku počítače s nainstalovanou sadou Visual Studio (nebo v **tématu > použití** ve vzdáleném ladicím programu).

## <a name="bkmk_setup"></a>Nastavení vzdáleného ladicího programu

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a>Konfigurace vzdáleného ladicího programu
Některé aspekty konfigurace vzdáleného ladicího programu můžete změnit po prvním spuštění po spuštění.

- Pokud potřebujete přidat oprávnění ostatním uživatelům pro připojení ke vzdálenému ladicímu programu, vyberte **nástroje > oprávnění**. K udělení nebo odebrání oprávnění je potřeba mít oprávnění správce.

     > [!IMPORTANT]
     > Můžete spustit vzdálený ladicí program uživatelského účtu, který se liší od uživatelského účtu, který používáte na počítači aplikace Visual Studio, ale musíte přidat jiný uživatelský účet oprávnění vzdáleného ladicího programu.

     Alternativně můžete spustit vzdálený ladicí program z příkazového řádku s parametrem **/allow \<username >** parametr: **msvsmon/allow \<username@computer>** .

- Pokud potřebujete změnit režim ověřování nebo číslo portu nebo zadat hodnotu časového limitu pro nástroje Remote Tools: zvolte **nástroje > možnosti**.

     Seznam čísel portů, která se používají ve výchozím nastavení, najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Můžete také spustit nástroje Remote Tools v režimu bez ověřování, ale tento režim se rozhodně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Zvolte režim bez ověřování jenom v případě, že jste si jisti, že síť není ohroženy škodlivými nebo nevyžádanými daty.

## <a name="bkmk_configureService"></a>Volitelné Konfigurace vzdáleného ladicího programu jako služby
Pro ladění v technologii ASP.NET a jiné prostředí serveru, musíte buď spustit vzdálený ladicí program jako správce nebo, je vždy spuštěn, chcete-li spustit vzdálený ladicí program jako službu.

 Pokud chcete nakonfigurovat vzdálený ladicí program jako službu, postupujte podle těchto kroků.

1. Vyhledejte **Průvodce nastavením vzdáleného ladicího programu** (rdbgwiz. exe). (Jedná se o samostatnou aplikaci ze vzdáleného ladicího programu.) Je k dispozici pouze při instalaci nástrojů Remote Tools. Nenainstaluje se sadou Visual Studio.

2. Spustíte Průvodce konfigurací. Jakmile se zobrazí první stránka, klikněte na tlačítko **Další**.

3. Zaškrtněte políčko **Spustit vzdálený ladicí program sady Visual Studio 2015 jako službu** .

4. Přidáte název uživatelského účtu a hesla.

    K tomuto účtu možná budete muset přidat uživatelské právo **Přihlásit se jako služba** **(na** **úvodní** stránce nebo v okně zadejte příkaz **secpol** na příkazovém řádku). Po zobrazení okna poklikejte na **přiřazení uživatelských práv**a pak v pravém podokně vyhledejte možnost **Přihlásit se jako služba** . Poklepejte na něj. Přidejte uživatelský účet do okna **vlastnosti** a klikněte na tlačítko **OK**). Klikněte na **Další**.

5. Vyberte typ sítě, mají komunikovat nástroje remote tools. Musí být vybrán alespoň jeden typ sítě. Pokud jsou počítače připojené do domény, měli byste zvolit první položku. Pokud jsou tyto počítače připojeny přes domácí nebo pracovní skupině, měli byste zvolit položky druhý nebo třetí. Klikněte na **Další**.

6. Pokud je možné službu spustit, uvidíte, že **jste úspěšně dokončili Průvodce konfigurací Visual Studio Remote Debugger**. Pokud službu spustit nemůžete, zobrazí **se neúspěšné dokončení Průvodce konfigurací Visual Studio Remote Debugger**. Stránce se zobrazuje také několik tipů pro získání služba spustí.

7. Klikněte na **Finish** (Dokončit).

   V tomto okamžiku vzdálený ladicí program je spuštěn jako služba. To můžete ověřit tak, že v **Ovládacích panelech > služby** a vyhledáte **vzdálený ladicí program sady Visual Studio 2015**.

   Službu vzdáleného ladicího programu můžete zastavit a spustit z **ovládacích panelů > služby**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení ladění pomocí vzdálených symbolů

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také:

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány firewall ve Windows pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET Core na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)