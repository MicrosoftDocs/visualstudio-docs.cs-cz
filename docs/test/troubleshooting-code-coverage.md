---
title: Poradce při potížích s pokrytím kódu
ms.date: 03/31/2020
ms.topic: troubleshooting
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 39d5d54021e7b8286bd653941d233a73bcf8cfb4
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80527987"
---
# <a name="troubleshoot-code-coverage"></a>Řešení problémů s pokrytím kódu

Nástroj pro analýzu pokrytí kódu v sadě Visual Studio shromažďuje data pro nativní a spravovaná sestavení (*dll* nebo *.exe* soubory). V některých případech však okno **Výsledky pokrytí kódu** zobrazí chybu podobnou "Prázdné výsledky generované: ...." Existuje několik důvodů, proč můžete získat prázdné výsledky. Tento článek vám pomůže tyto problémy vyřešit.

## <a name="what-you-should-see"></a>Co byste měli vidět

Pokud zvolíte **příkaz Analyzovat pokrytí kódu** v nabídce **Test** a pokud sestavení a testy úspěšně spustit, pak byste měli vidět seznam výsledků v okně **Pokrytí kódu.** Pro zobrazení podrobností je možno položky rozbalit.

::: moniker range=">=vs-2019"
![Výsledky pokrytí kódu s vybarvením](../test/media/vs-2019/codecoverage1.png)
::: moniker-end
::: moniker range="vs-2017"
![Výsledky pokrytí kódu s vybarvením](../test/media/codecoverage1.png)
::: moniker-end

Další informace naleznete [v tématu Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Možné příčiny zobrazení žádných nebo starých výsledků

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Máte správnou verzi sady Visual Studio?

Potřebujete Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nebyly provedeny žádné testy

Analýza&mdash;Zkontrolujte výstupní okno. V rozevíracím seznamu **Zobrazit výstup z** zvolte **Testy**. Zjistěte, zda zde nejsou zaznamenána nějaká varování nebo chyby.

Vysvětlení&mdash;Kód pokrytí analýza se provádí při testování jsou spuštěny. Zahrnuje pouze sestavení, která jsou načtena do paměti v průběhu testů. Pokud žádný z testů jsou provedeny, není nic pro pokrytí kódu sestavy.

Řešení&mdash;v Průzkumníku testů, zvolte **Spustit vše** a ověřte, zda testy proběhly úspěšně. Před použitím funkce **Analyzovat pokrytí kódu**opravte všechny chyby .

### <a name="youre-looking-at-a-previous-result"></a>Díváte se na předchozí výsledek

Při úpravě a opětovném spuštění testů může být stále viditelný výsledek pokrytí předchozího kódu, včetně zbarvení kódu z tohoto starého spuštění.

1. Spusťte **analyzovat pokrytí kódu**.

2. Ujistěte se, že jste vybrali poslední sadu výsledků v okně **Výsledky pokrytí kódu.**

### <a name="pdb-symbol-files-are-unavailable"></a>Nejsou k dispozici soubory typu .pdb (symbol)

Analýza:&mdash;Otevřete cílovou složku kompilace (obvykle *bin\debug)* a ověřte, zda pro každé sestavení je ve stejném adresáři jako soubor *DLL* nebo *EXE* soubor *PDB.*

Vysvětlení&mdash;Modul pokrytí kódu vyžaduje, aby každé sestavení mělo přidružený soubor *PDB* přístupný během testovacího běhu. Pokud neexistuje žádný soubor *PDB* pro konkrétní sestavení, sestavení není analyzováno.

Soubor *PDB* musí být generován ze stejného sestavení jako soubory *DLL* nebo *EXE.*

Řešení&mdash;Ujistěte se, že nastavení sestavení generuje soubor *PDB.* Pokud soubory *PDB* nejsou při vytváření projektu aktualizovány, otevřete vlastnosti projektu, vyberte stránku **Sestavení,** zvolte **Upřesnit**a zkontrolujte **informace o ladění**.

U projektů jazyka C++ se ujistěte, že generované soubory PDB mají úplné informace o ladění. Otevřete vlastnosti projektu a **ověřte,** > zda je ladění ladění propojovacího**Debugging** > programu**generovat informace o ladění** nastaveno na generovat informace o ladění **optimalizované pro sdílení a publikování (/DEBUG:FULL).**

Pokud jsou soubory *PDB* a *DLL* nebo *EXE* na různých místech, zkopírujte soubor *PDB* do stejného adresáře. Je také možné nakonfigurovat modul pokrytí kódu pro vyhledávání souborů *.pdb* v jiném umístění. Další informace naleznete v [tématu Customize code coverage analysis](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Použití instrumentovaného nebo optimalizovaného binárního

Analýza&mdash;Zjistěte, zda binární soubor prošel jakoukoli formou pokročilé optimalizace, například optimalizace s asistencí profilu, nebo byl instrumentován nástrojem profilování, například *vsinstr.exe* nebo *vsperfmon.exe*.

Vysvětlení:&mdash;Pokud již byla sestava instrumentována nebo optimalizována jiným nástrojem profilování, je sestavení z analýzy pokrytí kódu vynecháno. Analýzu disponibility kódu nelze provést u takových sestavení.

Rozlišení&mdash;Vypněte optimalizaci a použijte nové sestavení.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kód není spravovaný (.NET) nebo nativní (C++) kód

Analýza&mdash;Ověřte, že používáte některé testy spravovaného kódu nebo kódu Jazyka C++.

Vysvětlení&mdash;Analýza pokrytí kódu v sadě Visual Studio je k dispozici pouze na spravované a nativní (C++) kód. Pokud pracujete s nástroji třetích stran, některé nebo všechny kód y se mohou spustit na jiné platformě.

Rozlišení&mdash;Žádné k dispozici.

### <a name="assembly-has-been-installed-by-ngen"></a>Sestavení bylo nainstalováno pomocí technologie NGen

Analýza&mdash;Ověřte, zda není sestavení načteno z mezipaměti nativníbité bitové kopie.

Vysvětlení&mdash;Z důvodů výkonu nejsou analyzovány nativní sestavení bitových obrázků. Další informace naleznete v [tématu Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Rozlišení&mdash;Použijte verzi msil sestavení. Nezpracovávejte to s NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Chybná syntaxe vlastního souboru .runsettings

Analýza:&mdash;Pokud používáte vlastní soubor *.runsettings,* může obsahovat syntaktickou chybu. Pokrytí kódu není spuštěna a okno pokrytí kódu se neotevře na konci testovacího běhu nebo zobrazí staré výsledky.

Vysvětlení:&mdash;Testy jednotek můžete spustit s vlastním souborem *.runsettings* a konfigurovat možnosti pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace naleznete v [tématu Customize code coverage analysis](../test/customizing-code-coverage-analysis.md).

Řešení&mdash;Existují dva možné typy závad:

- **Chyba XML**

     Otevřete soubor *.runsettings* v editoru XML sady Visual Studio. Hledejte označení chyb.

- **Chyba regulárního výrazu**

  Každý řetězec v souboru je regulární výraz. Zkontrolujte, pro každý z nich pro chyby, a zejména hledat:

  - Neodpovídající závorky (...) nebo neunikaté závorky \\(... \\). Pokud ve vyhledávacím řetězci chcete najít závorky, musíte je přeskočit. Chcete-li například porovnat funkci, použijte:`.*MyFunction\(double\)`

  - Hvězdička nebo plus na začátku výrazu. Chcete-li porovnat libovolný řetězec znaků, použijte tečku následovanou hvězdičkou:`.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Nesprávná vyloučení ve vlastním souboru .runsettings

Analýza:&mdash;Pokud používáte vlastní soubor *.runsettings,* ujistěte se, že obsahuje sestavení.

Vysvětlení:&mdash;Testy jednotek můžete spustit s vlastním souborem *.runsettings* a konfigurovat možnosti pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace naleznete v [tématu Customize code coverage analysis](../test/customizing-code-coverage-analysis.md).

Řešení&mdash;Odeberte všechny `Include` uzly ze souboru *.runsettings* a potom odeberte všechny `Exclude` uzly. Pokud to vyřeší daný problém, vracejte je zpět ve fázích.

Zkontrolujte, že uzel DataCollectors určuje pokrytí kódu. Porovnejte ji s ukázkou v [přizpůsobit analýzu pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Nějaký kód je vždy zobrazen jako nepokrytý

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Ještě před instrumentací je provedena inicializace kódu v nativní knihovně DLL

Analýza&mdash;Ve staticky propojeném nativním kódu je část inicializační funkce **DllMain** a kód, který volá, někdy zobrazena jako nezahrnutá, i když byl kód proveden.

Vysvětlení&mdash;Nástroj pokrytí kódu funguje vložením instrumentace do sestavení těsně před spuštěním aplikace. V každém sestavení naložené předem inicializační kód v **DllMain** provede, jakmile načte sestavení a před spuštěním aplikace. Tento kód se zdá být zahrnuty, což obvykle platí pro staticky načtené sestavení.

Rozlišení&mdash;žádné.

## <a name="see-also"></a>Viz také

- [Určení rozsahu testovaného kódu pomocí pokrytí kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
