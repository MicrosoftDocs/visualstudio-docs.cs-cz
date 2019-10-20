---
title: Řešení potíží s pokrytím kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bf21286143b2b9543c834f00ed31ddaa4cef63
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660379"
---
# <a name="troubleshooting-code-coverage"></a>Poradce při potížích s pokrytím kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analytické nástroje pokrytí kódu v aplikaci Visual Studio shromažďují data pro nativní a spravovaná sestavení (soubory .dll nebo .exe). V některých případech se ale v okně výsledky pokrytí kódu zobrazí chyba podobná "vygenerované prázdné výsledky:...". Existuje několik možných důvodů, proč k tomu může dojít. Toto téma je určeno pro pomoc při řešení těchto problémů.

## <a name="what-you-should-see"></a>Co byste měli vidět
 Pokud zvolíte příkaz **Analyzovat pokrytí kódu** v nabídce Test a pokud se sestavení a testy úspěšně spustí, měli byste zobrazit seznam výsledků v okně pokrytí kódu. Pro zobrazení podrobností je možno položky rozbalit.

 ![Výsledky pokrytí kódu s barvou](../test/media/codecoverage1.png "CodeCoverage1")

 Další informace naleznete v tématu [Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Možné příčiny zobrazení žádných nebo starých výsledků

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Máte správnou verzi sady Visual Studio?
 Potřebujete Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nebyly provedeny žádné testy
 Analýza zkontroluje okno výstup. V rozevíracím seznamu **Zobrazit výstup z** vyberte možnost **testy**. Zjistěte, zda zde nejsou zaznamenána nějaká varování nebo chyby.

 Analýza pokrytí kódu je prováděna během testů, které jsou spuštěny. Zahrnuje pouze sestavení, která jsou načtena do paměti v průběhu testů. Jestliže nebyl proveden žádný z testů, pak nejsou k dispozici žádné informace pro hlášení o pokrytí kódu.

 Řešení v Průzkumníku testů vyberte možnost **Spustit vše** a ověřte, zda byly testy úspěšně spuštěny. Před použitím **analýzy pokrytí kódu**opravte případné chyby.

### <a name="youre-looking-at-a-previous-result"></a>Je zobrazen předchozí výsledek
 Při úpravě a opětovném spuštění testů může být stále zobrazen předchozí výsledek pokrytí kódu včetně barevného zvýraznění kódu z minulého spuštění testu.

1. Spusťte analýzu pokrytí kódu.

2. Ujistěte se, že jste v okně Výsledky pokrytí kódu vybrali nejaktuálnější sadu výsledků.

### <a name="pdb-symbol-files-are-unavailable"></a>Nejsou k dispozici soubory typu .pdb (symbol)
 Analýza otevře cílovou složku kompilace (obvykle bin\Debug) a ověří, že pro každé sestavení je soubor. pdb ve stejném adresáři jako soubor. dll nebo. exe.

 Vysvětlení modulu pokrytí kódu vyžaduje, aby každé sestavení mělo během testovacího běhu k dispozici přidružený soubor. pdb. Pokud nemá konkrétní sestavení přístupný žádný soubor typu .pdb, nebude analyzováno.

 Soubor typu .pdb je nutné vygenerovat ze stejného sestavení jako soubory typu .dll nebo .exe.

 Řešení se ujistěte, že vaše nastavení sestavení generuje soubor. pdb. Pokud se soubory. pdb po sestavení projektu neaktualizují, otevřete vlastnosti projektu, vyberte stránku **sestavení** , zvolte **Upřesnit** a zkontrolujte **informace o ladění**.

 Pokud jsou soubory typu .pdb a .dll nebo .exe na různých místech, zkopírujte soubor typu .pdb do stejného adresáře. Je také možné nakonfigurovat nástroj pokrytí kódu tak, aby hledal soubory typu .pdb v jiném umístění. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>Použití instrumentovaného nebo optimalizovaného binárního souboru
 Analýza určuje, zda binární soubor prošl jakoukoli formou rozšířené optimalizace, jako je optimalizace na základě profilu, nebo který byl instrumentací vybaven nástrojem pro profilaci, jako je VSInstr. exe nebo VSPerfMon. exe.

 Vysvětlení Pokud již bylo sestavení instrumentované nebo optimalizované jiným nástrojem pro profilaci, sestavení je vynecháno z analýzy pokrytí kódu.

 Analýza pokrytí kódu nemůže být na takovýchto sestavení provedena.

 Rozlišení spínače vypnuto a použití nového buildu.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kód není spravovaný (.NET) nebo nativní (C++) kód
 Analýza ověřuje, že spouštíte některé testy na spravovaném C++ nebo kódu.

 Vysvětlení analýzy pokrytí kódu v aplikaci Visual Studio je k dispozici pouze pro spravovanýC++a nativní () kód. Při práci s nástroji třetích stran může být část kódu nebo veškerý kód proveden na jiné platformě.

 Řešení není k dispozici.

### <a name="assembly-has-been-installed-by-ngen"></a>Sestavení bylo nainstalováno pomocí technologie NGen
 Analýza ověří, že sestavení není načteno z mezipaměti nativní bitové kopie.

 Vysvětlení z důvodů výkonu se neanalyzují sestavení nativní bitové kopie. Další informace naleznete v tématu [Ngen. exe (generátor nativních imagí)](https://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).

 Řešení použijte verzi sestavení MSIL. Nezpracovávejte jej pomocí technologie NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Chybná syntaxe vlastního souboru .runsettings
 Analýza Pokud používáte vlastní soubor. runsettings, může to obsahovat syntaktickou chybu.

 V důsledku toho se vůbec nespustí pokrytí kódu. Buď se okno pokrytí kódu na konci testu vůbec neotevře, nebo zobrazí staré výsledky.

 Vysvětlení můžete spustit testy jednotek pomocí vlastního souboru. runsettings a nakonfigurovat tak možnosti pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

 Řešení existují dva možné typy chyb:

- **Chyba XML**

     Otevřete soubor .runsettings v editoru jazyka XML sady Visual Studio. Hledejte označení chyb.

- **Chyba regulárního výrazu**

  Každý řetězec v souboru je regulární výraz. Zkontrolujte všechny, zda v nich nejsou chyby, a hledejte zejména:

  - Neshoda závorek (...) nebo neřídicích závorek \\ (... \\). Pokud ve vyhledávacím řetězci chcete najít závorky, musíte je přeskočit. Například pro vyhledání použití funkce: `.*MyFunction\(double\)`

  - Hvězdička nebo plus na začátku výrazu. Chcete-li vyhledat libovolný řetězec znaků, použijte tečku následovanou hvězdičkou: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Nesprávná vyloučení ve vlastním souboru .runsettings
 Analýza Pokud používáte vlastní soubor. runsettings, ujistěte se, že obsahuje vaše sestavení.

 Vysvětlení můžete spustit testy jednotek pomocí vlastního souboru. runsettings a nakonfigurovat tak možnosti pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

 Řešení odeberte všechny uzly `Include` ze souboru. runsettings a pak odeberte všechny uzly `Exclude`. Pokud to vyřeší daný problém, vracejte je zpět ve fázích.

 Zkontrolujte, že uzel DataCollectors určuje pokrytí kódu. Porovnejte ji s ukázkou při [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Nějaký kód je vždy zobrazen jako nepokrytý

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Ještě před instrumentací je provedena inicializace kódu v nativní knihovně DLL
 Analýza v staticky propojeném nativním kódu, součást inicializační funkce **DllMain** a kód, který volá, se někdy zobrazuje tak, jak se nezabývá, i když byl kód proveden.

 Vysvětlení nástroje pokrytí kódu funguje tak, že se do sestavení vloží instrumentace těsně před tím, než se aplikace začne spouštět. V jakémkoli sestavení načteném před tímto časem se inicializační kód v **DllMain** spustí hned po načtení sestavení a před spuštěním aplikace. Tento kód se jeví jako nepokrytý.

 Obvykle to platí pro staticky načtená sestavení.

 Řešení není k dispozici.

## <a name="see-also"></a>Viz také
 [Použití pokrytí kódu k určení rozsahu testovaného kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
