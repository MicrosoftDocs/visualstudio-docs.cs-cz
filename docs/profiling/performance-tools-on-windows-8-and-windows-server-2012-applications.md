---
title: Nástroje pro sledování výkonu v aplikacích pro Windows 8 & WS 2012
description: Přečtěte si, jak rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým nástroj pro výkon sady Visual Studio shromažďuje data.
ms.custom: SEO-VS-2020
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a6060b61f388b4db4e9284a96f5d924a84a76210
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922057"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012

Rozšířené funkce zabezpečení spouštěné ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým nástroje pro výkon sady Visual Studio shromažďují data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Toto téma popisuje změny pro nástroje pro sledování výkonu, které začínají na platformách Windows 8 a Windows Server 2012.

> [!NOTE]
> Nástroje výkonu pro jiné podporované verze systému Windows (Windows 7, Windows Server 2008 R2) se nezměnily.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Shromažďování dat aplikací pro UWP z integrovaného vývojového prostředí (IDE) sady Visual Studio

Při profilování aplikace pro UWP, která je napsaná v JavaScriptu a HTML 5, shromažďujete data instrumentace pro kód JavaScriptu. Při profilování aplikace pro UWP nebo komponenty, která je napsaná v Visual C++, Visual C# nebo Visual Basic, shromažďujete data vzorkování pro nativní a spravovaný kód. Svou aplikaci můžete profilovat lokálně nebo na vzdáleném počítači.

Tyto funkce profilování a možnosti se při profilování aplikací pro UWP nepodporují:

- Profilování aplikací JavaScriptu pomocí metody vzorkování.
- Profilace spravovaného a nativního kódu pomocí metody instrumentace.
- Profilace souběžného zpracování
- Profilace paměti .NET
- Profilace interakce vrstev (TIP)
- Možnosti vzorkování, jako je například nastavení události vzorkování a intervalu časování nebo shromažďování dalších dat čítače výkonu.
- Možnosti instrumentace, jako je například shromažďování výkonu a dat čítače systému Windows nebo určení dalších možností příkazového řádku.

Další informace o profilování aplikací pro UWP najdete v následujících článcích:

- [Spouštění aplikací pro UWP v místním počítači](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
- [Spouštění aplikací pro UWP ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [První seznámení s nástroji pro profilaci](profiling-feature-tour.md)
- [Paměť JavaScriptu](../profiling/javascript-memory.md)
- [Visual C++ profilů, kódu v jazyce Visual C# a Visual Basic v aplikacích pro UWP na místním počítači](/previous-versions/hh696631(v=vs.140))
- [Profilování Visual C++, Visual C# a kódu Visual Basic v aplikacích pro UWP na vzdáleném zařízení](/previous-versions/hh972878(v=vs.140))
- [Analýza údajů o výkonu pro Visual C++, Visual C# a kód Visual Basic v aplikacích pro UWP](/previous-versions/hh780914(v=vs.140))

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Shromažďovat data o aplikacích spuštěných na desktopu Windows 8 nebo na Windows Serveru 2012 z integrovaného vývojového prostředí (IDE) sady Visual Studio

Profilace pomocí metody instrumentace se pro systém Windows 8 nezměnila.

Profilace interakce vrstev (TIP) není podporována pomocí metody vzorkování.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Shromažďování dat z aplikací běžících na desktopu Windows 8 nebo na Windows Serveru 2012 pomocí vzorkování z integrovaného vývojového prostředí (IDE) sady Visual Studio

Tyto funkce profilování a možnosti se nepodporují při profilování aplikací pro stolní počítače s Windows 8 nebo Windows Server 2012 pomocí metody vzorkování:

- Profilace interakce vrstev (TIP). Shromažďování dat s tipem je podporované pomocí instrumentace.

- Možnosti vzorkování, jako je například nastavení události vzorkování a intervalu časování nebo shromažďování dalších dat čítače výkonu.

## <a name="profile-from-the-command-line"></a>Profil z příkazového řádku

K shromažďování dat profilování na zařízeních se systémem Windows 8 a Windows Server 2012 můžete použít dva nástroje příkazového řádku, včetně zařízení, která nemají instalaci sady Visual Studio:

|Název nástroje|Description|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Shromažďuje data profilování z aplikací pro UWP a shromažďuje ukázková data profilování z aplikací pro stolní počítače s Windows 8 a aplikací Windows Server 2012.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Shromažďuje data profilace, souběžnosti a interakce vrstev z aplikací, které běží v theWindows 8 Desktop nebo Windows Serveru 2012. Shromažďuje všechny typy dat profilování z předchozích verzí Windows.|

Oba nástroje jsou nainstalovány se sadou Visual Studio pro použití v místním počítači.

Chcete-li Profilovat aplikace na zařízeních, ve kterých není nainstalována aplikace Visual Studio, proveďte jednu z následujících akcí:

- Stáhněte si nástroje jako součást Remote Tools for Visual Studio z webu [MSDN](https://visualstudio.microsoft.com/#downloads+d-additional-software).

- Zkopírujte a spusťte instalační program nástrojů samostatného profileru z počítače se systémem Visual Studio. Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Vyberte instalační program operačního systému (x86/x64) vzdáleného počítače.

> [!NOTE]
> Chcete-li shromáždit data profilování, je nutné nainstalovat samostatný Profiler z počítače se systémem Visual Studio na vzdáleném počítači.

Tyto funkce a možnosti profilování nejsou podporované při profilování aplikací Windows 8 a Windows Server 2012 z příkazového řádku:

- Shromažďování dat z webových aplikací Windows 8 a Windows Server 2012 pomocí režimu vzorkování s [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md).

- Shromažďování dat vzorkování pomocí VsPerfCmd.exe.

- Možnosti vzorkování, jako je například nastavení události vzorkování a intervalu časování nebo shromažďování dalších dat čítače výkonu.

## <a name="collect-tier-interaction-tip-data"></a>Shromáždit data interakce vrstev (TIP)

Profilace interakce vrstev poskytuje další informace o době spuštění funkcí vícevrstvých aplikací, které komunikují s databázemi prostřednictvím služby ADO.NET Services. Data jsou shromažďována pouze pro volání synchronních funkcí.

**Edice sady Visual Studio**

Data profilování interakce vrstev je možné shromažďovat pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstev ale můžete zobrazit jenom v Visual Studio Enterprise.

**Windows 8 a Windows Server 2012**

1. Chcete-li shromáždit data interakce vrstev z aplikací, které jsou spuštěny v počítači se systémem Windows 8 nebo Windows Server 2012, je nutné použít metodu instrumentace.

2. Nemůžete shromažďovat data interakce vrstev pro aplikace pro UWP.

3. Data interakce vrstev můžete zahrnout do všech metod profilování v jiné podporované verzi systému Windows.

**Průvodce výkonem a Prohlížeč výkonu**

Je nutné přidat možnost shromažďování dat interakce vrstev ke spuštění profilace z Prohlížeč výkonu. Také je nutné přidat projekt, spustitelný soubor nebo web do cílového uzlu Prohlížeč výkonu. Viz [shromáždění dat interakce vrstev](../profiling/collecting-tier-interaction-data.md).

**Shromažďování dat s tipem na vzdáleném počítači**

Pokud chcete shromažďovat data interakce vrstev na vzdáleném počítači, musíte zkopírovat soubor **vs \_ Profiler \_** _\<Platform>_ **\_** _\<Language>_ **. exe** ze složky *%VSINSTALLDIR%\Team Tools\Performance Tools\Setups* počítače sady Visual Studio do vzdáleného počítače a nainstalovat ho. Nástroje pro profilaci nelze použít v balíčku pro stažení [vzdáleného ladění](../debugger/remote-debugging.md) .

K shromažďování dat profilace můžete použít [VSPerfCmd](../profiling/vsperfcmd.md) nebo [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) .

**Sestavy tipů**

Data interakce vrstev se dají zobrazit jenom v Visual Studio Enterprise. Sestavy interakce na úrovni souborů prostřednictvím [VSPerfReport](../profiling/vsperfreport.md) nejsou k dispozici.

## <a name="see-also"></a>Viz také

[Prohlížeč výkonu](../profiling/performance-explorer.md) 
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md) 
 [Profil z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)