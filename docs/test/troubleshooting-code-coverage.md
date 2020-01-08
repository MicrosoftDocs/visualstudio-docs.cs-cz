---
title: Poradce při potížích s pokrytím kódu
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd70394262a2dd19ebf32f57549b9d2b3e8ee92a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565972"
---
# <a name="troubleshoot-code-coverage"></a>Řešení problémů s pokrytím kódu

Analytické nástroje pokrytí kódu v sadě Visual Studio shromažďuje data pro nativní a spravovaná sestavení ( *.dll* nebo *.exe* soubory). V některých případech se ale v okně **výsledky pokrytí kódu** zobrazí chyba podobná "vygenerované prázdné výsledky:...". K dispozici je několik důvodů, proč můžete získat prázdné výsledky. Tento článek pomůže při řešení těchto problémů.

## <a name="what-you-should-see"></a>Co byste měli vidět

Pokud se rozhodnete **analyzovat pokrytí kódu** příkaz **testovací** nabídky a pokud sestavení a testy proběhnou úspěšně, pak by měl zobrazit seznam výsledků v **pokrytí kódu** okno. Pro zobrazení podrobností je možno položky rozbalit.

![Výsledky pokrytí kódu s barevné zvýrazňování](../test/media/codecoverage1.png)

Další informace najdete v tématu [použití pokrytí kódu k určení, kolik kódu je právě testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Možné příčiny zobrazení žádných nebo starých výsledků

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Máte správnou verzi sady Visual Studio?

Je třeba Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nebyly provedeny žádné testy

Analýza&mdash;zkontrolujte výstupní okno. V **zobrazit výstup z** rozevíracího seznamu, zvolte **testy**. Zjistěte, zda zde nejsou zaznamenána nějaká varování nebo chyby.

Vysvětlení&mdash;analýzy pokrytí kódu se provádí v průběhu testů. Zahrnuje pouze sestavení, která jsou načtena do paměti v průběhu testů. Pokud žádný z testů jsou spouštěny, neexistuje žádné informace pro hlášení o pokrytí kódu.

Rozlišení&mdash;v Průzkumníku testů, zvolte **spustit všechny** k ověření, že testy se spustily úspěšně. Opravte všechny chyby před použitím **analyzovat pokrytí kódu**.

### <a name="youre-looking-at-a-previous-result"></a>Je zobrazen předchozí výsledek

Když změníte a znovu spustit testy, můžete se předchozí výsledek pokrytí kódu dál zobrazovat, včetně barevného zvýraznění kódu z minulého spuštění testu.

1. Spusťte **analýzu pokrytí kódu**.

2. Ujistěte se, zda jste vybrali nejnovější sadu výsledků **výsledky pokrytí kódu** okna.

### <a name="pdb-symbol-files-are-unavailable"></a>Nejsou k dispozici soubory typu .pdb (symbol)

Analýza&mdash;otevřete cílovou složku kompilace (obvykle *bin\debug*) a ověřte, že pro každé sestavení, je *PDB* ve stejném adresáři jako soubor *.dll*nebo *.exe* souboru.

Vysvětlení&mdash;nástroj pokrytí kódu vyžaduje, aby všechna sestavení měla jeho přidruženého *PDB* soubor přístupný během spuštění testu. Pokud není žádný *PDB* soubor pro konkrétní sestavení, sestavení se neanalyzuje.

*PDB* souboru je nutné vygenerovat ze stejného sestavení, jako *.dll* nebo *.exe* soubory.

Rozlišení&mdash;Ujistěte se, že nastavení sestavení generuje *PDB* souboru. Pokud *PDB* nejsou aktualizovány soubory při sestavení projektu, otevřete vlastnosti projektu, vyberte **sestavení** zvolte **Upřesnit**a zkontrolujte **Ladicí informace modulu**.

V C++ případě projektů zajistěte, aby generované soubory. pdb měly úplné informace o ladění. Otevřete vlastnosti projektu a ověřte, že **Linker** > **ladění** > **vygenerovat informace o ladění** je nastaveno na **generovat ladicí informace optimalizované pro sdílení a publikování (/debug: Full)** .

Pokud *PDB* a *.dll* nebo *.exe* jsou na různých místech, zkopírujte soubory *PDB* soubor do stejného adresáře. Je také možné nakonfigurovat nástroj pokrytí kódu pro hledání *PDB* soubory v jiném umístění. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

### <a name="use-an-instrumented-or-optimized-binary"></a>Použití instrumentovaného nebo optimalizovaného binárního souboru

Analýza&mdash;zjistit, zda binární soubor podstoupil jakoukoliv formu pokročilé optimalizace, jako je optimalizace na základě profilu nebo byl instrumentován pomocí nástroje pro profilaci, jako *vsinstr.exe* nebo  *vsperfmon.exe*.

Vysvětlení&mdash;Pokud sestavení již bylo instrumentováno nebo optimalizováno pomocí jiného nástroje pro profilaci, pak je sestavení vynecháno z analýzy pokrytí kódu. Analýza pokrytí kódu nemůže být na takovýchto sestavení provedena.

Rozlišení&mdash;vypnout optimalizaci a použijte nové sestavení.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kód není spravovaný (.NET) nebo nativní (C++) kód

Analýza&mdash;ověřte, zda jsou testy spuštěny na spravované nebo kódu jazyka C++.

Vysvětlení&mdash;analýzy pokrytí kódu v sadě Visual Studio je dostupná pouze pro spravovaný a nativní (C++) kód. Pokud pracujete s nástroji třetích stran, některé nebo všechny kódu může spustit na jiné platformě.

Rozlišení&mdash;nic není k dispozici.

### <a name="assembly-has-been-installed-by-ngen"></a>Sestavení bylo nainstalováno pomocí technologie NGen

Analýza&mdash;ověřte, že sestavení není načteno z mezipaměti nativních bitových kopií.

Vysvětlení&mdash;z důvodů výkonu nejsou sestavení nativní bitové kopie analyzovány. Další informace najdete v tématu [Ngen.exe (Generátor nativních obrázků)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Rozlišení&mdash;použít verzi jazyka MSIL sestavení. Nezpracovávat ho pomocí technologie NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Chybná syntaxe vlastního souboru .runsettings

Analýza&mdash;Pokud používáte vlastní *s příponou .runsettings* souboru může obsahovat chybu syntaxe. Pokrytí kódu není spuštěn a neotevře buď se okno pokrytí kódu na konci testovacího běhu, nebo zobrazí staré výsledky.

Vysvětlení&mdash;můžete spustit testování částí s vlastním *s příponou .runsettings* souboru k nakonfigurování možností pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

Rozlišení&mdash;existují dva typy možných chyb:

- **XML došlo k chybě**

     Otevřít *s příponou .runsettings* souboru v editoru XML pro Visual Studio. Hledejte označení chyb.

- **Chyba regulárního výrazu**

  Každý řetězec v souboru je regulární výraz. Zkontrolujte každé z nich nejsou chyby a hledejte zejména:

  - Neshoda závorek (...) nebo závorky \\(...) \\). Pokud ve vyhledávacím řetězci chcete najít závorky, musíte je přeskočit. Chcete-li například funkci, použijte: `.*MyFunction\(double\)`

  - Hvězdička nebo plus na začátku výrazu. Pro vyhledání libovolného řetězce znaků, použijte tečku následovanou hvězdičkou: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Nesprávná vyloučení ve vlastním souboru .runsettings

Analýza&mdash;Pokud používáte vlastní *s příponou .runsettings* souboru, ujistěte se, že obsahuje vaše sestavení.

Vysvětlení&mdash;můžete spustit testování částí s vlastním *s příponou .runsettings* souboru k nakonfigurování možností pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

Rozlišení&mdash;odebrat všechny `Include` uzly z *s příponou .runsettings* souboru a potom odeberte všechny `Exclude` uzly. Pokud to vyřeší daný problém, vracejte je zpět ve fázích.

Zkontrolujte, že uzel DataCollectors určuje pokrytí kódu. Porovnejte jej s ukázkou v [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Nějaký kód je vždy zobrazen jako nepokrytý

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Ještě před instrumentací je provedena inicializace kódu v nativní knihovně DLL

Analýza&mdash;ve staticky propojeném nativním kódu, část inicializační funkce **zpracování funkce DllMain** a kód, který volá v některých případech se zobrazí jako nepokryté i když byl proveden kód.

Vysvětlení&mdash;nástroj pokrytí kódu funguje pomocí vložení instrumentace do sestavení těsně před zahájením spuštění aplikace. V libovolném sestavení načtena předem, inicializační kód v **DllMain** provádí co nejdříve po načtení sestavení a před spuštěním aplikace. Tento kód se zobrazí jako nepokrytý, kterou obvykle platí pro staticky načtená sestavení.

Rozlišení&mdash;None.

## <a name="see-also"></a>Viz také:

- [Použití pokrytí kódu k určení, kolik kódu je právě testováno.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
