---
title: Nástroje pro výkon v aplikacích pro Windows 8 & Windows Server 2012
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3938e7dc1b3ec33c8a4cf74b6957067bbdfd6185
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778424"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012

Rozšířené funkce zabezpečení počínaje windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým nástroje visual studia pro výkon shromažďují data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Toto téma popisuje změny nástrojů pro výkon, které začínají na platformách Windows 8 a Windows Server 2012.

> [!NOTE]
> Nástroje pro výkon pro jiné podporované verze systému Windows (Windows 7, Windows Server 2008 R2) se nezměnily.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Shromažďování dat o aplikacích UPW z ide Visual Studia

Když profilujete aplikaci UPW, která je napsána v JavaScriptu a HTML 5, shromažďujete data instrumentace pro kód JavaScriptu. Když profilujete aplikaci nebo součást UPW, která je napsaná v jazyce Visual C++, Visual C# nebo Visual Basic, shromažďujete vzorkovací data pro nativní a spravovaný kód. Aplikaci můžete profilovat místně nebo na vzdáleném počítači.

Tyto funkce profilování a možnosti nejsou podporovány při profilování aplikací UPW:

- Profilování javascriptových aplikací pomocí metody vzorkování.
- Profilování spravované a nativní kód pomocí metody instrumentace.
- Profilování souběžnosti
- Profilování paměti .NET
- Profilování interakce úrovně (TIP)
- Možnosti vzorkování, jako je například nastavení události vzorkování a interval časování nebo shromažďování dalších dat čítače výkonu.
- Možnosti instrumentace, jako je například shromažďování dat čítače výkonu a oken nebo určení dalších možností příkazového řádku.

Další informace o profilování aplikací UPW naleznete v následujících článcích:

- [Spouštění aplikací pro UWP v místním počítači](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
- [Spouštění aplikací pro UWP ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [První seznámení s nástroji pro profilaci](profiling-feature-tour.md)
- [Paměť JavaScriptu](../profiling/javascript-memory.md)
- [Profil visual c++, visual c# a kódu Visual Basic v aplikacích UPW v místním počítači](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [Profil visual c++, visual c# a kódu Visual Basic v aplikacích UPW na vzdáleném zařízení](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [Analýza dat o výkonu pro kódY Visual C++, Visual C# a Visual Basic v aplikacích UPW](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Shromažďování dat o aplikacích spuštěnéch na ploše Windows 8 nebo windows serveru 2012 z prostředí IDE Sady Visual Studio

Profilování pomocí metody instrumentace se pro systém Windows 8 nezměnilo.

Profilování interakce úrovně (TIP) není podporováno metodou vzorkování.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Shromažďování dat o aplikacích spuštěnéch na ploše Windows 8 nebo windows serveru 2012 pomocí vzorkování z prostředí IDE sady Visual Studio

Tyto funkce profilování a možnosti nejsou podporovány při profilování aplikací pro stolní počítače systému Windows 8 nebo windows server 2012 pomocí metody vzorkování:

- Profilování interakce úrovně (TIP). Shromažďování dat TIP je podporováno pomocí instrumentace.

- Možnosti vzorkování, jako je například nastavení události vzorkování a interval časování nebo shromažďování dalších dat čítače výkonu.

## <a name="profile-from-the-command-line"></a>Profil z příkazového řádku

Ke shromažďování dat profilování na zařízeních se systémem Windows 8 a Windows Server 2012, včetně zařízení, která nemají instalaci sady Visual Studio, se používají dva nástroje příkazového řádku:

|Název nástroje|Popis|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Shromažďuje data profilování z aplikací UPW a shromažďuje ukázková data profilování z desktopových aplikací pro Windows 8 a aplikací pro Windows Server 2012.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Shromažďuje instrumentace, souběžnost a profilování vrstev z aplikací spuštěných na ploše Windows 8 nebo Windows Server 2012. Shromažďuje všechny typy dat profilování z předchozích verzí systému Windows.|

Oba nástroje jsou nainstalovány s Visual Studio pro použití v místním počítači.

Chcete-li profilovat aplikace na zařízeních, na kterých není nainstalována sada Visual Studio, proveďte jednu z následujících akcí:

- Stáhněte si nástroje jako součást vzdálenénástroje pro visual studio z [webu MSDN](https://visualstudio.microsoft.com/#downloads+d-additional-software).

- Zkopírujte a spusťte instalační program samostatného profileru z počítače sady Visual Studio. Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Zvolte instalační program pro operační systém (x86/x64) vzdáleného počítače.

> [!NOTE]
> Chcete-li shromažďovat data profilování TIP, je nutné nainstalovat samostatný profiler z počítače sady Visual Studio do vzdáleného počítače.

Tyto funkce profilování a možnosti nejsou podporovány při profilování aplikací systému Windows 8 a Windows Server 2012 z příkazového řádku:

- Shromažďování dat z webových aplikací pro Windows 8 a Windows Server 2012 pomocí režimu vzorkování pomocí [aplikace VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).

- Shromažďování vzorkovacích dat pomocí vsPerfCmd.exe.

- Možnosti vzorkování, jako je například nastavení události vzorkování a interval časování nebo shromažďování dalších dat čítače výkonu.

## <a name="collect-tier-interaction-tip-data"></a>Shromažďování dat interakce s úrovní (TIP)

Profilování interakce vrstvy poskytuje další informace o době provádění funkcí vícevrstvých aplikací, které komunikují s databázemi prostřednictvím ADO.NET služeb. Data jsou shromažďována pouze pro synchronní volání funkcí.

**Edice Visual Studia**

Data profilování interakce úrovně lze shromažďovat pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstvy však lze zobrazit pouze v sadě Visual Studio Enterprise.

**Windows 8 a Windows Server 2012**

1. Chcete-li shromažďovat data interakce vrstvy z aplikací spuštěných na ploše Windows 8 nebo Windows Server 2012, musíte použít metodu instrumentace.

2. Pro aplikace UPW nelze shromažďovat data interakce vrstvy.

3. Data interakce vrstvy můžete zahrnout do všech metod profilování v jiné podporované verzi systému Windows.

**Průvodce výkonem a Průzkumník výkonu**

Je nutné přidat možnost shromažďování dat interakce vrstvy do profilování spustit z Průzkumníka výkonu. Je také nutné přidat projekt, spustitelný soubor nebo web do cílového uzlu Průzkumníka výkonu. Viz [Shromáždit data interakce vrstvy](../profiling/collecting-tier-interaction-data.md).

**Shromažďování dat TIP ve vzdáleném počítači**

Chcete-li shromažďovat data interakce vrstvy ve vzdáleném počítači, musíte do vzdáleného počítače zkopírovat **\_** **vs\_profiler\_**_\<platformu>_ _ \<jazyk>_ soubor **exe** ze složky *%VSInstallDir%\Team Tools\Performance Tools\Setups* počítače Visual Studio do vzdáleného počítače a nainstalovat jej. Nástroje pro profilování nelze použít v balíčku pro stažení [vzdáleného ladění.](../debugger/remote-debugging.md)

Můžete použít [VSPerfCmd](../profiling/vsperfcmd.md) nebo [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) shromažďovat data profilování.

**Zprávy TIP**

Data interakce úrovně lze zobrazit pouze v sadě Visual Studio Enterprise. Sestavy interakce na základě vrstvy založené na souborech prostřednictvím [vsperfreportu](../profiling/vsperfreport.md) nejsou k dispozici.

## <a name="see-also"></a>Viz také

[Průzkumník](../profiling/performance-explorer.md)
výkonu[Konfigurace profilu výkonových relací](../profiling/configuring-performance-sessions.md)
[z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)
