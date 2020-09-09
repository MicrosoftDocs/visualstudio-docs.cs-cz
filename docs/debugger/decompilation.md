---
title: Dekompilovat kód .NET při ladění | Microsoft Docs
ms.date: 2/2/2020
ms.topic: how-to
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
ms.openlocfilehash: 87f8fbec389e3735b6f1c39cdd671a391c7334d7
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600113"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Generovat zdrojový kód ze sestavení .NET během ladění

Při ladění aplikace .NET můžete zjistit, že chcete zobrazit zdrojový kód, který nemáte. Například přerušení na výjimku nebo použití zásobníku volání k přechodu na zdrojové umístění.

> [!NOTE]
> * Generování zdrojového kódu (dekompilace) je k dispozici pouze pro aplikace .NET a je založené na open source projektu [ILSpy](https://github.com/icsharpcode/ILSpy) .
> * Dekompilace je k dispozici pouze v aplikaci Visual Studio 2019 16,5 a novější.
> * Použití atributu [SuppressIldasmAttribute](/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) na sestavení nebo modul brání aplikaci Visual Studio v pokusu o dekompilaci.

## <a name="generate-source-code"></a>Generovat zdrojový kód

Když ladíte a není k dispozici žádný zdrojový kód, Visual Studio zobrazí dokument **Nenalezený zdrojem** , nebo pokud nemáte symboly pro sestavení, **nenačtený dokument žádné symboly** . Oba dokumenty mají možnost **dekompilovat zdrojový kód** , která generuje kód C# pro aktuální umístění. Generovaný kód jazyka C# lze potom použít stejně jako jakýkoliv jiný zdrojový kód. Můžete zobrazit kód, kontrolovat proměnné, nastavit zarážky a tak dále.

### <a name="no-symbols-loaded"></a>Nebyly načteny žádné symboly

Následující obrázek znázorňuje zprávu, že **nejsou načteny žádné symboly** .

![Snímek obrazovky s dokumentem nenačteného symbolu](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Zdroj nebyl nalezen.

Následující obrázek znázorňuje zprávu **zdroj nebyl nalezen** .

![Snímek obrazovky se zdrojovým dokumentem nebyl nalezen](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Generování a vložení zdrojů pro sestavení

Kromě generování zdrojového kódu pro konkrétní umístění můžete vygenerovat všechen zdrojový kód pro dané sestavení .NET. Provedete to tak, že přejdete do okna **moduly** a z kontextové nabídky sestavení .NET a pak vyberete příkaz **dekompilovat zdrojový kód** . Visual Studio vygeneruje soubor symbolů pro sestavení a poté vloží zdroj do souboru symbolů. V pozdějším kroku můžete [extrahovat](#extract-and-view-the-embedded-source-code) vložený zdrojový kód.

![Snímek kontextové nabídky sestavení v okně modulů s dekompilací zdrojového příkazu](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extrakce a zobrazení vloženého zdrojového kódu

Zdrojové soubory, které jsou vloženy do souboru symbolů, můžete extrahovat pomocí příkazu **extrahovat zdrojový kód** v kontextové nabídce okna **moduly** .

![Snímek kontextové nabídky sestavení v okně moduly s příkazem extrahovat zdroje](media/decompilation-extract-source-code.png)

Extrahované zdrojové soubory jsou přidány do řešení jako [jiné soubory](../ide/reference/miscellaneous-files.md). Funkce různé soubory je ve výchozím nastavení v aplikaci Visual Studio vypnutá. Tuto funkci můžete povolit z **Tools**  >  **Options**  >  **dokumentu prostředí**možnosti nástrojů  >  **Documents**  >  **Zobrazit různé soubory v Průzkumník řešení** zaškrtávací políčko. Bez povolení této funkce nebudete moci otevřít extrahovaný zdrojový kód.

![Snímek obrazovky se stránkou možností nástroje s možnostmi různé soubory je povolený.](media/decompilation-tools-options-misc-files.png)

Extrahované zdrojové soubory se zobrazí v různých souborech v **Průzkumník řešení**.

![Snímek obrazovky Průzkumníka řešení s různými soubory](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Známá omezení

### <a name="requires-break-mode"></a>Vyžaduje režim přerušení.

Generování zdrojového kódu pomocí dekompilace je možné pouze v případě, že je ladicí program v režimu pozastavení a aplikace je pozastavena. Například Visual Studio vstoupí do režimu přerušení, pokud narazí na zarážku nebo na výjimku. Aplikaci Visual Studio můžete snadno aktivovat, aby se při příštím spuštění kódu přerušit pomocí příkazu **Break All** ( ![ přerušit všechny ikony ](media/decompilation-break-all.png) ).

### <a name="decompilation-limitations"></a>Omezení dekompilace

Generování zdrojového kódu z mezilehlého formátu (IL), který je používán v sestaveních .NET, má určitá omezení. V takovém případě generovaný zdrojový kód nevypadá jako původní zdrojový kód. Většina rozdílů je uvedena v místech, kde informace v původním zdrojovém kódu nejsou za běhu potřeba. Například informace, jako jsou prázdné znaky, komentáře a názvy místních proměnných, nejsou za běhu potřeba. Pro pochopení, jak se program spouští, a nikoli jako náhrada původního zdrojového kódu, doporučujeme použít vygenerovaný zdroj.

### <a name="debug-optimized-or-release-assemblies"></a>Ladit optimalizované nebo vydaná sestavení

Při ladění kódu, který byl dekompilován ze sestavení, které bylo zkompilováno pomocí optimalizací kompilátoru, může docházet k následujícím problémům:
- Zarážky se nemusí vždy navazovat na umístění odpovídajícího zdroje.
- Krokování nemusí vždy krokovat se správným umístěním.
- Místní proměnné nemohou mít přesné názvy.
- Některé proměnné nemusí být k dispozici pro vyhodnocení.

Další podrobnosti najdete v problému GitHubu: [integrace ICSharpCode. Decompiler do ladicího programu vs](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Spolehlivost dekompilace

Poměrně malé procento pokusů o dekompilaci může vést k selhání. Důvodem je chyba referenčního bodu sekvence null v ILSpy.  Toto selhání jsme zmírnili zachycením těchto problémů a řádným selháním pokusu o dekompilaci.

Další podrobnosti najdete v problému GitHubu: [integrace ICSharpCode. Decompiler do ladicího programu vs](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Omezení s asynchronním kódem

Výsledky dekompilace modulů s modifikátory kódu Async/await mohou být neúplné nebo selžou zcela. Implementace ILSpy typu Async/await a yield – počítače jsou pouze částečně implementovány. 

Další podrobnosti najdete v problému GitHubu: [stav generátoru PDB](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Pouze můj kód

Nastavení [pouze můj kód (JMC)](./just-my-code.md) umožňuje Visual Studiu krokovat se systémem, architekturou, knihovnou a dalšími neuživatelskými voláními. Během relace ladění zobrazuje okno **moduly** , které kódové moduly ladicí program zpracovává jako můj kód (uživatelský kód).

Dekompilace optimalizovaných nebo vydaných modulů vytváří jiný než uživatelský kód. Pokud ladicí program přeruší v kódu nekompilovaného uživatele, například, nezobrazí se **žádné okno zdroje** . Pokud chcete pouze můj kód zakázat, přejděte **Tools**k  >  **Možnosti** nástroje (nebo **Debug**  >  **Možnosti**ladění) > obecné **ladění**  >  **General**a potom zrušte zaškrtnutí **Povolit pouze můj kód**.

### <a name="extracted-sources"></a>Extrahované zdroje

Zdrojový kód extrahovaný ze sestavení má následující omezení:
- Název a umístění generovaných souborů se nedají konfigurovat.
- Soubory jsou dočasné a budou smazány pomocí aplikace Visual Studio.
- Soubory jsou umístěny v jedné složce a v hierarchii složek, které původní zdroje nepoužívaly.
- Název souboru pro každý soubor obsahuje hodnotu hash kontrolního součtu souboru.

### <a name="generated-code-is-c-only"></a>Generovaný kód je pouze C#
Dekompilace pouze generuje soubory zdrojového kódu v jazyce C#. Neexistuje žádný způsob, jak vygenerovat soubory v jiném jazyce.