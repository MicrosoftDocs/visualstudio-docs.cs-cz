---
title: Vzdálené ladění | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302075"
---
# <a name="remote-debugging"></a>Vzdálené ladění
Můžete ladit aplikaci sady Visual Studio, která byla nasazena v jiném počítači. Chcete-li tak učinit, použijte vzdálený ladicí program sady Visual Studio.

Podrobné pokyny pro vzdálené ladění naleznete v těchto tématech.

|Scénář|Odkaz|
|-|-|-|
|Azure App Service|[Ladicí program snímek](../debugger/debug-live-azure-applications.md) nebo [ASP.NET vzdálenéladění](../debugger/remote-debugging-azure.md) v Azure|
|Virtuální počítač Azure|[Vzdálené ladění ASP.NET ve službě Azure](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Ladění aplikace Azure Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Vzdálené ladění ASP.NET jádra](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) nebo [vzdálené holadění ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# nebo Visual Basic|[Vzdálené ladění projektu v jazyce C# nebo Visual Basic](../debugger/remote-debugging-csharp.md)|
|C++|[Vzdálené ladění projektu jazyka C++](../debugger/remote-debugging-cpp.md)|
|Univerzální aplikace pro Windows (UPW)|[Spuštění aplikací UPW na vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md) nebo [ladění nainstalovaného balíčku aplikace](../debugger/debug-installed-app-package.md)|

Pokud chcete stáhnout a nainstalovat vzdálený ladicí program a nepotřebujete žádné další pokyny pro váš scénář, postupujte podle kroků v tomto článku.

## <a name="download-and-install-the-remote-tools"></a>Stažení a instalace vzdálených nástrojů

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a>Požadavky

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a>(Nepovinné) Spuštění vzdáleného ladicího programu ze sdílené složky

Vzdálený ladicí program (*msvsmon.exe)* najdete v počítači s již nainstalovanou komunitou Visual Studio, Professional nebo Enterprise. V některých případech je nejjednodušším způsobem nastavení vzdáleného ladění spuštění vzdáleného ladicího programu (msvsmon.exe) ze sdílené složky. Omezení použití naleznete na stránce nápovědy vzdáleného ladicího programu **(Nápověda > použití** ve vzdáleném ladicím programu).

1. Vyhledejte *soubor msvsmon.exe* v adresáři odpovídajícím vaší verzi sady Visual Studio:

   ::: moniker range=">=vs-2019"

   *Programové soubory (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Vzdálený debugger\x86\msvsmon.exe*

   *Programové soubory (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Vzdálený debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Programové soubory (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Vzdálený debugger\x86\msvsmon.exe*

   *Programové soubory (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Vzdálený debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Sdílejte složku **Vzdálené ladicí program** v počítači sady Visual Studio.

3. Ve vzdáleném počítači spusťte *soubor msvsmon.exe* ze sdílené složky. Postupujte [podle pokynů k nastavení](#bkmk_setup).

> [!TIP]
> Instalace příkazového řádku a odkaz na příkazový řádek naleznete na stránce nápovědy ``msvsmon.exe /?`` pro *soubor msvsmon.exe* zadáním příkazového řádku v počítači s nainstalovaným souborem Visual Studio (nebo přejděte na **nápovědu > použití** ve vzdáleném ladicím programu).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Nastavení vzdáleného ladicího programu

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a>Konfigurace vzdáleného ladicího programu
Po prvním spuštění vzdáleného ladicího programu můžete změnit některé aspekty konfigurace vzdáleného ladicího programu.

- Pokud potřebujete přidat oprávnění pro ostatní uživatele, aby se připojili ke vzdálenému ladicímu programu, zvolte **Nástroje > oprávnění**. K udělení nebo odebrání oprávnění je potřeba mít oprávnění správce.

     > [!IMPORTANT]
     > Vzdálený ladicí program můžete spustit pod uživatelským účtem, který se liší od uživatelského účtu, který používáte v počítači sady Visual Studio, ale musíte přidat jiný uživatelský účet k oprávněním vzdáleného ladicího programu.

     Případně můžete spustit vzdálený ladicí program z příkazového řádku s parametrem ** \</allow username>:** **msvsmon /allow \< username@computer>**.

- Pokud potřebujete změnit režim ověřování nebo číslo portu nebo zadat hodnotu časového času pro vzdálené nástroje: zvolte **Nástroje > Možnosti**.

     Seznam čísel portů používaných ve výchozím nastavení naleznete v [tématu Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Můžete také spustit nástroje Remote Tools v režimu bez ověřování, ale tento režim se rozhodně nedoporučuje. Při spuštění v tomto režimu není žádné zabezpečení sítě. Režim Bez ověřování zvolte pouze v případě, že jste si jisti, že síť není ohrožena škodlivým nebo nepřátelským provozem.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a>(Nepovinné) Konfigurace vzdáleného ladicího programu jako služby
Pro ladění v ASP.NET a jiných serverových prostředích musíte spustit vzdálený ladicí program jako správce nebo, pokud chcete, aby byl vždy spuštěn, spustit vzdálený ladicí program jako službu.

 Pokud chcete nakonfigurovat vzdálený ladicí program jako službu, postupujte takto.

1. Najděte **Průvodce konfigurací vzdáleného ladicího programu** (rdbgwiz.exe). (Toto je samostatná aplikace z vzdáleného ladicího programu.) Je k dispozici pouze při instalaci vzdálených nástrojů. Není nainstalován s Visual Studio.

2. Spusťte průvodce konfigurací. Až se objeví první stránka, klikněte na **Další**.

3. Zaškrtněte políčko **Spustit vzdálený ladicí program Visual Studia 2015 jako službu.**

4. Přidejte název uživatelského účtu a heslo.

    K tomuto účtu může být nutné přidat právo **uživatele Přihlásit** se jako služba (Najít **místní zásady zabezpečení** (secpol.msc) na **úvodní** stránce nebo v okně (nebo zadat **secpol** na příkazovém řádku). Po vytvoření okna poklikejte na **přiřazení uživatelských práv**a v pravém podokně **vyhledejte možnost Přihlásit se jako služba.** Poklepejte na něj. Přidejte uživatelský účet do okna **Vlastnosti** a klepněte na tlačítko **OK**). Klikněte na **Další**.

5. Vyberte typ sítě, se kterou mají vzdálené nástroje komunikovat. Musí být vybrán alespoň jeden typ sítě. Pokud jsou počítače připojeny prostřednictvím domény, měli byste zvolit první položku. Pokud jsou počítače připojeny prostřednictvím pracovní skupiny nebo domácí skupiny, měli byste zvolit druhou nebo třetí položku. Klikněte na **Další**.

6. Pokud lze službu spustit, zobrazí se, že **jste úspěšně dokončili Průvodce konfigurací vzdáleného ladicího programu sady Visual Studio**. Pokud službu nelze spustit, zobrazí se, že **průvodce konfigurací vzdáleného ladicího programu sady Visual Studio**se nezdařilo . Stránka také poskytuje několik tipů, které je třeba sledovat, aby se služba spustila.

7. Klikněte na **Finish** (Dokončit).

   V tomto okamžiku je vzdálený ladicí program spuštěn jako služba. Můžete to ověřit tak, že přejdete na **Ovládací panely > služby** a **hledáte visual studio 2015 vzdálené debugger**.

   Službu vzdáleného ladicího programu můžete zastavit a spustit z **Ovládacích panelů > služby**.

## <a name="set-up-debugging-with-remote-symbols"></a>Nastavení ladění pomocí vzdálených symbolů

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md)
- [Vzdálené ladění ASP.NET jádra ve vzdáleném počítači služby IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Chyby a řešení potíží se vzdáleným laděním](../debugger/remote-debugging-errors-and-troubleshooting.md)