---
title: Poradce při potížích s pokrytím kódu
description: Naučte se řešit chybné prázdné zprávy výsledků, pokud očekáváte, že Visual Studio shromáždí data pro nativní a spravovaná sestavení.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: troubleshooting
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d99dcc3a141bc3734c5c356601d0e1e7474f06a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967966"
---
# <a name="troubleshoot-code-coverage"></a>Řešení problémů s pokrytím kódu

Nástroj Analýza pokrytí kódu v aplikaci Visual Studio shromažďuje data pro nativní a spravovaná sestavení (soubory *. dll* nebo *. exe* ). V některých případech se ale v okně **výsledky pokrytí kódu** zobrazí chyba podobná "vygenerované prázdné výsledky:...". K dispozici je několik důvodů, proč můžete získat prázdné výsledky. Tento článek vám pomůže tyto problémy vyřešit.

## <a name="what-you-should-see"></a>Co byste měli vidět

Pokud zvolíte příkaz **Analyzovat pokrytí kódu** v nabídce **test** a pokud se sestavení a testy úspěšně spustí, měli byste zobrazit seznam výsledků v okně **pokrytí kódu** . Pro zobrazení podrobností je možno položky rozbalit.

::: moniker range=">=vs-2019"
![Výsledky pokrytí kódu s barvou](../test/media/vs-2019/codecoverage1.png)
::: moniker-end
::: moniker range="vs-2017"
![Výsledky pokrytí kódu s barvou](../test/media/codecoverage1.png)
::: moniker-end

Další informace naleznete v tématu [Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Možné příčiny zobrazení žádných nebo starých výsledků

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Máte správnou verzi sady Visual Studio?

Potřebujete Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nebyly provedeny žádné testy

Analýza &mdash; zkontroluje okno výstup. V rozevíracím seznamu **Zobrazit výstup z** vyberte možnost **testy**. Zjistěte, zda zde nejsou zaznamenána nějaká varování nebo chyby.

&mdash;Analýza pokrytí kódu je prováděna během testů, které jsou spuštěny. Zahrnuje pouze sestavení, která jsou načtena do paměti v průběhu testů. Pokud není proveden žádný z testů, není pro sestavu k dispozici žádný kód.

Řešení &mdash; v Průzkumníku testů vyberte možnost **Spustit vše** a ověřte, zda byly testy úspěšně spuštěny. Před použitím **analýzy pokrytí kódu** opravte případné chyby.

### <a name="youre-looking-at-a-previous-result"></a>Můžete si prohlédnout předchozí výsledek.

Když upravíte a znovu spustíte testy, může být předchozí výsledek pokrytí kódu stále viditelný, včetně barevného zbarvení z tohoto starého běhu.

1. Spusťte **analýzu pokrytí kódu**.

2. Ujistěte se, že jste v okně **výsledky pokrytí kódu** vybrali nejnovější sadu výsledků.

### <a name="pdb-symbol-files-are-unavailable"></a>Nejsou k dispozici soubory typu .pdb (symbol)

Analýza &mdash; otevře cílovou složku kompilace (obvykle *bin\Debug*) a ověří, zda pro každé sestavení existuje soubor *. pdb* ve stejném adresáři jako soubor *. dll* nebo *. exe* .

Vysvětlení &mdash; modulu pokrytí kódu vyžaduje, aby každé sestavení mělo během testovacího běhu k dispozici přidružený soubor *. pdb* . Pokud neexistuje žádný soubor *PDB* pro konkrétní sestavení, sestavení není analyzováno.

Soubor *. pdb* musí být vygenerován ze stejného sestavení jako soubory *. dll* nebo *. exe* .

Řešení se &mdash; ujistěte, že vaše nastavení sestavení generuje soubor *. pdb* . Pokud se soubory *. pdb* po sestavení projektu neaktualizují, otevřete vlastnosti projektu, vyberte stránku **sestavení** , zvolte možnost **Upřesnit** a zkontrolujte **informace o ladění**.

Pro projekty v jazyce C++ zajistěte, aby generované soubory. pdb měly úplné informace o ladění. Otevřete vlastnosti projektu a ověřte, že **ladění linkeru**  >    >  **generovat informace o ladění** je nastaveno na **generovat ladicí informace optimalizované pro sdílení a publikování (/debug: Full)**.

Pokud jsou soubory *. pdb* a *. dll* nebo *. exe* na různých místech, zkopírujte soubor *. pdb* do stejného adresáře. Je také možné nakonfigurovat modul pokrytí kódu pro hledání souborů *. pdb* v jiném umístění. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Použití instrumentované nebo optimalizovaného binárního souboru

Analýza &mdash; Určuje, jestli binární soubor prošl libovolným způsobem pokročilé optimalizace, jako je optimalizace na základě profilu, nebo se instrumentoval nástrojem pro profilaci, jako je *vsinstr.exe* nebo *vsperfmon.exe*.

Vysvětlení &mdash; Pokud již bylo sestavení instrumentované nebo optimalizované jiným nástrojem pro profilaci, sestavení je vynecháno z analýzy pokrytí kódu. Analýza pokrytí kódu nemůže být na takových sestaveních provedena.

Rozlišení &mdash; spínače vypnuto a použití nového buildu.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kód není spravovaný (.NET) nebo nativní (C++) kód

Analýza &mdash; ověřuje, že spouštíte některé testy na spravovaném nebo C++ kódu.

Vysvětlení &mdash; analýzy pokrytí kódu v aplikaci Visual Studio je k dispozici pouze pro spravovaný a nativní kód (C++). Pokud pracujete s nástroji třetích stran, může se stát, že se některý nebo celý kód spustí na jiné platformě.

Řešení &mdash; není k dispozici.

### <a name="assembly-has-been-installed-by-ngen"></a>Sestavení bylo nainstalováno pomocí technologie NGen

Analýza &mdash; ověří, že sestavení není načteno z mezipaměti nativní bitové kopie.

Vysvětlení &mdash; z důvodů výkonu se neanalyzují sestavení nativní bitové kopie. Další informace najdete v tématu [Ngen.exe (generátor nativních imagí)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Řešení &mdash; použijte verzi sestavení MSIL. Neprovádějte zpracování pomocí NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Chybná syntaxe vlastního souboru .runsettings

Analýza &mdash; Pokud používáte vlastní soubor *. runsettings* , může to obsahovat syntaktickou chybu. Pokrytí kódu není spuštěno a buď není otevřeno okno pokrytí kódu na konci testovacího běhu, nebo se zobrazí staré výsledky.

Vysvětlení &mdash; můžete spustit testy jednotek pomocí vlastního souboru *. runsettings* a nakonfigurovat tak možnosti pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

Řešení &mdash; existují dva možné typy chyb:

- **Chyba XML**

     Otevřete soubor *. runsettings* v editoru XML sady Visual Studio. Hledejte označení chyb.

- **Chyba regulárního výrazu**

  Každý řetězec v souboru je regulární výraz. Podívejte se na každou z nich a vyhledejte chyby, zejména:

  - Neshoda závorek (...) nebo neřídicích závorek \\ (... \\ ). Pokud ve vyhledávacím řetězci chcete najít závorky, musíte je přeskočit. Například pro vyhledání použití funkce: `.*MyFunction\(double\)`

  - Hvězdička nebo plus na začátku výrazu. Chcete-li vyhledat libovolný řetězec znaků, použijte tečku následovanou hvězdičkou: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Nesprávná vyloučení ve vlastním souboru .runsettings

Analýza &mdash; Pokud používáte vlastní soubor *. runsettings* , ujistěte se, že obsahuje vaše sestavení.

Vysvětlení &mdash; můžete spustit testy jednotek pomocí vlastního souboru *. runsettings* a nakonfigurovat tak možnosti pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

Řešení &mdash; odeberte všechny `Include` uzly ze souboru *. runsettings* a pak odeberte všechny `Exclude` uzly. Pokud to vyřeší daný problém, vracejte je zpět ve fázích.

Zkontrolujte, že uzel DataCollectors určuje pokrytí kódu. Porovnejte ji s ukázkou v části [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Nějaký kód je vždy zobrazen jako nepokrytý

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Ještě před instrumentací je provedena inicializace kódu v nativní knihovně DLL

Analýza &mdash; v staticky propojeném nativním kódu, součást inicializační funkce **DllMain** a kód, který volá, se někdy zobrazuje tak, jak se nezabývá, i když byl kód proveden.

Vysvětlení &mdash; nástroje pokrytí kódu funguje tak, že se do sestavení vloží instrumentace těsně před tím, než se aplikace začne spouštět. V jakémkoli načteném sestavení se inicializační kód v **DllMain** spustí hned po načtení sestavení a před spuštěním aplikace. Zdá se, že tento kód se nezabývá, což obvykle platí pro staticky načtená sestavení.

Řešení není k dispozici &mdash; .

## <a name="see-also"></a>Viz také

- [Určení rozsahu testovaného kódu pomocí pokrytí kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
