---
title: Dekompilace kódu .NET při ladění | Dokumenty společnosti Microsoft
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508742"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generovat zdrojový kód ze sestavení .NET při ladění

Při ladění aplikace .NET můžete zjistit, že chcete zobrazit zdrojový kód, který nemáte. Například rozdělení na výjimku nebo pomocí zásobníku volání přejít do zdrojového umístění.

> [!NOTE]
> * Generování zdrojového kódu (dekompilace) je k dispozici pouze pro aplikace .NET a je založeno na projektu [ILSpy](https://github.com/icsharpcode/ILSpy) s otevřeným zdrojovým kódem.
> * Dekompilace je k dispozici pouze v sadě Visual Studio 2019 16.5 a novější.
> * Použití atributu [SuppressIldasmAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) na sestavení nebo modul zabrání visual studio v pokusu o dekompilaci.

## <a name="generate-source-code"></a>Generovat zdrojový kód

Když ladíte a není k dispozici žádný zdrojový kód, Visual Studio zobrazí **dokument Zdroj nebyl nalezen** nebo pokud nemáte symboly pro sestavení, dokument Bez **načtených symbolů.** Oba dokumenty mají možnost **Decompile zdrojového kódu,** který generuje kód Jazyka C# pro aktuální umístění. Generovaný kód Jazyka C# lze pak použít stejně jako jakýkoli jiný zdrojový kód. Můžete zobrazit kód, zkontrolovat proměnné, nastavit zarážky a tak dále.

### <a name="no-symbols-loaded"></a>Nejsou načteny žádné symboly.

Na následujícím obrázku je zobrazena zpráva **Bez načtených symbolů.**

![Snímek obrazovky s žádným načteným dokumentem se symbolem](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Zdroj nebyl nalezen.

Následující obrázek znázorňuje zprávu **Zdroj nebyl nalezen.**

![Snímek obrazovky se zdrojovým dokumentem nebyl nalezen](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generování a vložení zdrojů pro sestavení

Kromě generování zdrojového kódu pro určité umístění můžete vygenerovat veškerý zdrojový kód pro dané sestavení .NET. Chcete-li to provést, přejděte do okna **Moduly** a z kontextové nabídky sestavení .NET a vyberte příkaz **Dekompilovat zdrojový kód.** Visual Studio vygeneruje soubor symbolů pro sestavení a potom vloží zdroj do souboru symbolů. V pozdějším kroku můžete [extrahovat](#extract-and-view-the-embedded-source-code) vložený zdrojový kód.

![Snímek obrazovky kontextové nabídky sestavení v okně modulů s příkazem dekompilovat zdroj.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extrahovat a zobrazit vložený zdrojový kód

Zdrojové soubory, které jsou vloženy do souboru symbolů, můžete extrahovat pomocí příkazu **Extrahovat zdrojový kód** v kontextové nabídce okna **Moduly.**

![Snímek obrazovky kontextové nabídky sestavení v okně modulů s příkazem Extrahovat zdroje.](media/decompilation-extract-source-code.png)

Extrahované zdrojové soubory jsou přidány do roztoku jako [různé soubory](../ide/reference/miscellaneous-files.md). Funkce různé soubory je ve výchozím nastavení vypnutá v sadě Visual Studio. Tuto funkci můžete povolit v**Environment** > **Documents** > zaškrtávacím **boxu** > **Options** > Průzkumník a**údržby** nástrojů. Bez povolení této funkce nebudete moci extrahovaný zdrojový kód otevřít.

![Snímek obrazovky s možností nástroje se zapnutou možností různé soubory](media/decompilation-tools-options-misc-files.png)

Extrahované zdrojové soubory se zobrazují v různé soubory v **Průzkumníku řešení**.

![Snímek obrazovky průzkumníka řešení s různé soubory](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Známá omezení

### <a name="requires-break-mode"></a>Vyžaduje režim přerušení

Generování zdrojového kódu pomocí dekompilace je možné pouze v případě, že ladicí program je v režimu přerušení a aplikace je pozastavena. Například Visual Studio přejde do režimu přerušení, když narazí na zarážku nebo výjimku. Můžete snadno spustit Visual Studio přerušit při příštím spuštění kódu pomocí![ **příkazu Přerušit vše** (Přerušit všechny ikonu).](media/decompilation-break-all.png)

### <a name="decompilation-limitations"></a>Omezení dekompilace

Generování zdrojového kódu z meziformátu (IL), který se používá v sestaveních .NET, má některá vlastní omezení. Jako takový generovaný zdrojový kód nevypadá jako původní zdrojový kód. Většina rozdílů je v místech, kde informace v původním zdrojovém kódu není potřeba za běhu. Například informace, jako jsou mezery, komentáře a názvy místních proměnných nejsou potřeba za běhu. Doporučujeme použít generovaný zdroj k pochopení způsobu provádění programu a nikoli jako náhrada původního zdrojového kódu.

### <a name="debug-optimized-or-release-assemblies"></a>Ladění optimalizovaných nebo uvolnění sestavení

Při ladění kódu, který byl dekompilován z sestavení, které bylo zkompilován pomocí optimalizace kompilátoru, můžete narazit na následující problémy:
- Zarážky nemusí vždy vázat na odpovídající umístění zdroje.
- Krokování nemusí vždy krok do správného umístění.
- Místní proměnné nemusí mít přesné názvy.
- Některé proměnné nemusí být k dispozici pro hodnocení.

Další podrobnosti naleznete v problému GitHub: [ICSharpCode.Decompiler integrace do VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Dekompilace spolehlivost

Relativně malé procento pokusů o dekompilaci může mít za následek selhání. To je způsobeno chybou sekvenčního bodu null-reference v ILSpy.  Jsme zmírnilselhání zachycením těchto problémů a řádně selhání pokus o dekompilaci.

Další podrobnosti naleznete v problému GitHub: [ICSharpCode.Decompiler integrace do VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Omezení s asynchronním kódem

Výsledky z dekompilace modulů s async/await vzory kódu může být neúplné nebo zcela nezdaří. IlSpy implementace async/await a výnos stav-stroje je implementována pouze částečně. 

Další podrobnosti naleznete v problému GitHub: [Stav generátoru PDB](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Pouze můj kód

Nastavení [Jen můj kód (JMC)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) umožňuje Visual Studio krokování systému, frameworku, knihovny a dalších volání mimo uživatele. Během relace ladění okno **Moduly** zobrazuje, které moduly kódu ladicí program považuje za můj kód (uživatelský kód).

Dekompilace optimalizovaných nebo uvolňovacích modulů vytváří neuživatelský kód. Pokud ladicí program rozdělí v dekompilovaném kódu bez uživatele, například se zobrazí okno **Žádný zdroj.** Chcete-li zakázat pouze můj kód, přejděte **Debugging** > na**možnosti** **nástrojů** > (nebo**možnosti** **ladění** > ) >**obecné**ladění a potom zrušte zaškrtnutí **políčka Povolit pouze můj kód**.

### <a name="extracted-sources"></a>Extrahované zdroje

Zdrojový kód extrahovaný ze sestavení má následující omezení:
- Název a umístění generovaných souborů nelze konfigurovat.
- Soubory jsou dočasné a budou odstraněny visual studio.
- Soubory jsou umístěny v jedné složce a všechny hierarchie složek, které původní zdroje měl se nepoužívá.
- Název souboru pro každý soubor obsahuje kontrolní součet hash souboru.

### <a name="generated-code-is-c-only"></a>Generovaný kód je pouze c#
Dekompilace generuje pouze soubory zdrojového kódu v c#. Neexistuje žádná možnost generovat soubory v jiném jazyce.
