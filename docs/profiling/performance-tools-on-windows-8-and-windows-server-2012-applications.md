---
title: Nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 404a8a3f40d5d84d60fe4822fb692e4f48a57503
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220798"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012

Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 požadované významných změnách v nástroji Sledování výkonu sady Visual Studio způsob, jak shromažďovat data na těchto platformách. U aplikací pro UPW také vyžadují nové techniky kolekce. Toto téma popisuje změny pro nástroje pro měření výkonu spouští na platformách systému Windows 8 a Windows Server 2012.

> [!NOTE]
> Sada Performance tools for ostatní podporované verze Windows (Windows 7, Windows Server 2008 R2) se nezměnily.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Shromažďování dat v aplikacích pro UWP v integrovaném vývojovém prostředí sady Visual Studio

Při profilování aplikace pro UPW, která je napsána v jazyce JavaScript a HTML 5, shromažďování dat instrumentace pro kód jazyka JavaScript. Při profilování aplikace pro UPW nebo komponenty, která je napsána v jazyce Visual C++, Visual C# nebo Visual Basic, shromažďování dat vzorkování pro nativního a spravovaného kódu. Aplikace můžete Profilovat, místně nebo ve vzdáleném počítači.

Tyto profilování funkce a možnosti nejsou podporovány při profilování aplikací pro UPW:

- Profilace aplikací jazyka JavaScript pomocí metody odběru vzorků.
- Profilace spravovaného a nativního kódu pomocí metody instrumentace.
- Profilace souběžnosti
- Profilování paměti .NET
- Interakce vrstev (TIP) pro profilaci
- Možnosti vzorkování, například nastavit událost odběru vzorků a interval časování nebo shromažďování dat čítače výkonu Další.
- Instrumentace možnosti, jako je shromažďování dat čítačů windows a výkonu nebo zadání další možnosti příkazového řádku.

Další informace o vytváření profilů aplikací pro UWP najdete v následujících článcích:

- [Spouštění aplikací pro UWP v místním počítači](../debugger/run-windows-store-apps-on-the-local-machine.md)
- [Spouštění aplikací pro UWP ve vzdáleném počítači](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Nejdřív se podívejte na nástroje pro profilaci](profiling-feature-tour.md)
- [Paměti jazyka JavaScript](../profiling/javascript-memory.md)
- [Kód profilu Visual C++, Visual C# a Visual Basic v aplikacích pro UWP v místním počítači](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [Kód profilu Visual C++, Visual C# a Visual Basic v aplikacích pro UWP ve vzdáleném zařízení](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [Analýza výkonnostních dat pro kód jazyka Visual C++, Visual C# a Visual Basic v aplikacích pro UWP](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Shromažďování dat na aplikace, které běží na ploše systému Windows 8 nebo Windows serveru 2012 z integrovaného vývojového prostředí sady Visual Studio

Profilace pomocí metody instrumentace nedošlo ke změně pro systém Windows 8.

Interakce vrstev (TIP) profilace není podporováno pomocí metody vzorkování.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Shromažďování dat na aplikace, které běží na ploše systému Windows 8 nebo Windows Server 2012 s použitím vzorkování z integrovaného vývojového prostředí sady Visual Studio

Tyto profilování funkce a možnosti nejsou podporovány při profilování desktopových aplikací Windows 8 nebo Windows Server 2012 aplikace pomocí metody vzorkování:

- Profilace sledováním interakce vrstev (TIP). Shromažďování dat TIP je podporován pomocí instrumentace.

- Možnosti, jako je nastavení událost odběru vzorků a interval časování nebo shromažďování dat čítače výkonu Další vzorkování.

## <a name="profile-from-the-command-line"></a>Profil z příkazového řádku

Ke shromažďování dat profilace na zařízeních s Windows 8 a Windows Server 2012, včetně zařízení, která není nutné instalaci sady Visual Studio, použijte dva nástroje příkazového řádku:

|Název nástroje|Popis|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|Shromažďuje data profilace z aplikací pro UWP a shromažďuje data profilace vzorku z aplikací klasické pracovní plochy systému Windows 8 a Windows Server 2012 aplikace...|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Shromažďuje instrumentace, souběžnost a data z aplikací, které jsou spuštěny na ploše sadě Windows 8 nebo Windows Server 2012 profilace interakce vrstev. Shromažďuje všechny typy dat profilování z předchozích verzí Windows.|

Oba nástroje jsou nainstalovány se sadou Visual Studio pro použití v místním počítači.

Do profilu aplikace na zařízeních, které nemají nainstalované, Visual Studio proveďte jednu z následujících akcí:

- Stáhněte si nástroje jako součást nástrojů Remote Tools for Visual Studio z [webu MSDN](http://go.microsoft.com/fwlink/?LinkID=219549).

- Kopírování a spusťte instalační program nástroje samostatného profileru z počítače Visual Studio. Instalační programy jsou v *%VSInstallDir%\Team nástroje Tools\Setups* složky. Zvolte instalační program pro operační systém (x86/x64) vzdáleného počítače.

> [!NOTE]
> Chcete-li shromažďovat data profilování TIP, musí instalace samostatného profileru z vašeho počítače Visual Studio na vzdáleném počítači.

Tyto profilování funkce a možnosti nejsou podporovány při profilování aplikací Windows 8 a Windows Server 2012 z příkazového řádku:

- Shromažďování dat z webových aplikací systému Windows 8 a Windows Server 2012 pomocí režimu vzorkování s [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md).

- Shromažďování dat vzorkování pomocí VsPerfCmd.exe.

- Možnosti, jako je nastavení událost odběru vzorků a interval časování nebo shromažďování dat čítače výkonu Další vzorkování.

## <a name="collect-tier-interaction-tip-data"></a>Shromažďování dat (TIP) interakce vrstev

Profilování interakce vrstev poskytuje další informace o spuštění s úspěšností funkce víceúrovňových aplikací, které komunikují s databázemi prostřednictvím služeb ADO.NET. Data se shromažďují pouze pro synchronní volání.

**Edice sady Visual Studio**

Data profilace interakce vrstev lze shromažďovat pomocí libovolné edice sady Visual Studio. Nicméně data profilace interakce vrstev lze zobrazit pouze v sadě Visual Studio Enterprise.

**Windows 8 a Windows Server 2012**

1. Ke shromažďování dat interakce vrstev z aplikací, které jsou spuštěny na ploše systému Windows 8 nebo Windows Server 2012, musíte použít metody instrumentace.

2. Nelze shromažďování dat interakce vrstev pro aplikace pro UPW.

3. Dat interakce vrstev můžete zahrnout všechny metody profilování na ostatní podporované verze systému Windows.

**Průvodce výkonu a prohlížeč výkonu**

Je nutné přidat možnost kolekce dat interakce vrstvy do běhu profilování z prohlížeče výkonu. Musíte také přidat projekt, spustitelný soubor nebo web na cílový uzel prohlížeč výkonu. Zobrazit [shromažďování dat interakce vrstev](../profiling/collecting-tier-interaction-data.md).

**Shromažďování dat TIP na vzdáleném počítači**

Ke shromažďování dat interakce vrstev ve vzdáleném počítači, je nutné zkopírovat **vs\_profiler\_**_\<platformy >_ **\_**  _\<Jazyk >_**.exe** soubor *%VSInstallDir%\Team Tools\Setups nástroje* složky počítače do sady Visual Studio vzdáleném počítači a nainstalujte ho. Nelze použít v nástrojů pro profilaci [vzdálené ladění](../debugger/remote-debugging.md) stažení balíčku.

Můžete použít [VSPerfCmd](../profiling/vsperfcmd.md) nebo [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) ke shromažďování dat profilování.

**TIP sestavy**

Dat interakce vrstev lze zobrazit pouze v sadě Visual Studio Enterprise. Interakce vrstev souborovému sestavy prostřednictvím [VSPerfReport](../profiling/vsperfreport.md) nejsou k dispozici.

## <a name="see-also"></a>Viz také:

[Prohlížeč výkonu](../profiling/performance-explorer.md)
[konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)
[profilu z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)