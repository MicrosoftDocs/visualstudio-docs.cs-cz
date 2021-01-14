---
title: Vzdálené ladění | Microsoft Docs
description: Ladění aplikace sady Visual Studio, která byla nasazena v jiném počítači pomocí vzdáleného ladicího programu sady Visual Studio.
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
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
ms.openlocfilehash: e97fd8979235f8ea89b43c6466b3119debe5b3ca
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205668"
---
# <a name="remote-debugging"></a>Vzdálené ladění
Můžete ladit aplikaci Visual Studio, která byla nasazena v jiném počítači. K tomu je potřeba použít Visual Studio Remote Debugger.

Podrobné pokyny pro vzdálené ladění najdete v těchto tématech.

|Scénář|Odkaz|
|-|-|-|
|Azure App Service|[Vzdálené ladění ASP.NET v Azure](../debugger/remote-debugging-azure.md) nebo pro Visual Studio Enterprise [Snapshot Debugger](../debugger/debug-live-azure-applications.md)|
|Virtuální počítač Azure|[Vzdálené ladění ASP.NET ve službě Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Ladění aplikace Service Fabric Azure](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Vzdálené ladění ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) nebo [vzdálené ladění ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# nebo Visual Basic|[Vzdálené ladění projektu v jazyce C# nebo Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Vzdálené ladění projektu v jazyce C++](../debugger/remote-debugging-cpp.md)|
|Univerzální aplikace pro Windows (UWP)|[Spouštění aplikací pro UWP na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md) nebo [ladění nainstalovaného balíčku aplikace](../debugger/debug-installed-app-package.md)|

Pokud chcete stáhnout a nainstalovat vzdálený ladicí program a nepotřebujete žádné další pokyny pro váš scénář, postupujte podle kroků v tomto článku.

## <a name="download-and-install-the-remote-tools"></a>Stažení a instalace nástrojů Remote Tools

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Požadavků

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> Volitelné Spuštění vzdáleného ladicího programu ze sdílené složky

Vzdálený ladicí program (*msvsmon.exe*) najdete na počítači, který je už nainstalovaný pro Visual Studio Community, Professional nebo Enterprise. V některých scénářích nejjednodušší způsob, jak nastavit vzdálené ladění, je spuštění vzdáleného ladicího programu (msvsmon.exe) ze sdílené složky. Omezení použití najdete na stránce s nápovědu pro vzdálený ladicí program (**nápovědu > používání** ve vzdáleném ladicím programu).

1. Najít *msvsmon.exe* v adresáři, který odpovídá vaší verzi sady Visual Studio:

   ::: moniker range=">=vs-2019"

   *Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Nasdílejte složku **vzdáleného ladícího programu** na počítači se systémem Visual Studio.

3. Na vzdáleném počítači spusťte *msvsmon.exe* ze sdílené složky. Postupujte podle [pokynů k instalaci](#bkmk_setup).

> [!TIP]
> Informace o instalaci a příkazovém řádku na příkazovém řádku najdete na stránce s nápovědu pro *msvsmon.exe* zadáním ``msvsmon.exe /?`` do příkazového řádku v počítači s nainstalovanou sadou Visual Studio (nebo přejděte na **nápovědu > použití** ve vzdáleném ladicím programu).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Nastavení vzdáleného ladicího programu

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Konfigurace vzdáleného ladicího programu
Po prvním spuštění můžete změnit některé aspekty konfigurace vzdáleného ladicího programu.

- Pokud potřebujete přidat oprávnění ostatním uživatelům pro připojení ke vzdálenému ladicímu programu, vyberte **nástroje > oprávnění**. K udělení nebo odebrání oprávnění je potřeba mít oprávnění správce.

     > [!IMPORTANT]
     > Vzdálený ladicí program lze spustit pod uživatelským účtem, který se liší od uživatelského účtu, který používáte v počítači se systémem Visual Studio, ale je nutné přidat jiný uživatelský účet do oprávnění vzdáleného ladicího programu.

     Alternativně můžete spustit vzdálený ladicí program z příkazového řádku s parametrem **/Allow \<username>** : **msvsmon/Allow \<username@computer>**.

- Pokud potřebujete změnit režim ověřování nebo číslo portu nebo zadat hodnotu časového limitu pro nástroje Remote Tools: zvolte **nástroje > možnosti**.

     Seznam čísel portů, která se používají ve výchozím nastavení, najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Můžete také spustit nástroje Remote Tools v režimu bez ověřování, ale tento režim se rozhodně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Režim bez ověřování vyberte pouze v případě, že jste si jistí, že síť není ohrožena škodlivým nebo nepřátelským provozem.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Volitelné Konfigurace vzdáleného ladicího programu jako služby
Pro ladění v ASP.NET a dalších serverových prostředích musíte buď spustit vzdálený ladicí program jako správce, nebo pokud chcete, aby byl vždy spuštěný, spusťte vzdálený ladicí program jako službu.

 Pokud chcete nakonfigurovat vzdálený ladicí program jako službu, postupujte podle těchto kroků.

1. Najděte **Průvodce konfigurací vzdáleného ladicího programu** (rdbgwiz.exe). (Jedná se o samostatnou aplikaci ze vzdáleného ladicího programu.) Je k dispozici pouze při instalaci nástrojů Remote Tools. Není nainstalován se sadou Visual Studio.

2. Začněte s Průvodcem konfigurací. Jakmile se zobrazí první stránka, klikněte na tlačítko **Další**.

3. Zaškrtněte políčko **Spustit vzdálený ladicí program sady Visual Studio 2015 jako službu** .

4. Přidejte název uživatelského účtu a hesla.

    K tomuto účtu možná budete muset přidat uživatelské právo **Přihlásit se jako služba** **(na** **úvodní** stránce nebo v okně zadejte příkaz **secpol** na příkazovém řádku). Po zobrazení okna poklikejte na **přiřazení uživatelských práv** a pak v pravém podokně vyhledejte možnost **Přihlásit se jako služba** . Poklikejte na ni. Přidejte uživatelský účet do okna **vlastnosti** a klikněte na tlačítko **OK**). Klikněte na **Next** (Další).

5. Vyberte typ sítě, se kterou mají nástroje Remote Tools komunikovat. Musí být vybrán alespoň jeden typ sítě. Pokud jsou počítače připojené přes doménu, měli byste zvolit první položku. Pokud jsou počítače připojené přes pracovní skupinu nebo domácí skupinu, měli byste zvolit druhou nebo třetí položku. Klikněte na **Next** (Další).

6. Pokud je možné službu spustit, uvidíte, že **jste úspěšně dokončili Průvodce konfigurací Visual Studio Remote Debugger**. Pokud službu spustit nemůžete, zobrazí **se neúspěšné dokončení Průvodce konfigurací Visual Studio Remote Debugger**. Stránka také obsahuje několik tipů, které vám pomohou postupovat při spuštění služby.

7. Klikněte na **Finish** (Dokončit).

   V tomto okamžiku je vzdálený ladicí program spuštěn jako služba. To můžete ověřit tak, že v **Ovládacích panelech > služby** a vyhledáte **vzdálený ladicí program sady Visual Studio 2015**.

   Službu vzdáleného ladicího programu můžete zastavit a spustit z **ovládacích panelů > služby**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení ladění pomocí vzdálených symbolů

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET Core na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)