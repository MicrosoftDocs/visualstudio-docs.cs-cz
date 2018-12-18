---
title: Poradce při potížích s pokrytím kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: f7df2f4c83a61c62a7774bea475d54c3deea4c47
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306044"
---
# <a name="troubleshooting-code-coverage"></a>Poradce při potížích s pokrytím kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analytické nástroje pokrytí kódu v aplikaci Visual Studio shromažďují data pro nativní a spravovaná sestavení (soubory .dll nebo .exe). Avšak v některých případech se v okně Výsledky pokrytí kódu zobrazí chyba, jako je „Byly generovány prázdné výsledky: ...“. Existuje několik možných důvodů, proč k tomu může dojít. Toto téma je určeno pro pomoc při řešení těchto problémů.  
  
## <a name="what-you-should-see"></a>Co byste měli vidět  
 Pokud se rozhodnete **analyzovat pokrytí kódu** příkaz v nabídce Test a pokud sestavení a testy proběhnou úspěšně, pak by měl zobrazit seznam výsledků v okně pokrytí kódu. Pro zobrazení podrobností je možno položky rozbalit.  
  
 ![Výsledky pokrytí s barevné zvýraznění kódu](../test/media/codecoverage1.png "CodeCoverage1")  
  
 Další informace najdete v tématu [pomocí pokrytí kódu k určení jak mnohem kódu je právě testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Možné příčiny zobrazení žádných nebo starých výsledků  
  
### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Máte správnou verzi sady Visual Studio?  
 Je třeba Visual Studio Enterprise.  
  
### <a name="no-tests-were-executed"></a>Nebyly provedeny žádné testy  
 Analýza  
 Zkontrolujte výstupní okno. V **zobrazit výstup z** rozevíracího seznamu, zvolte **testy**. Zjistěte, zda zde nejsou zaznamenána nějaká varování nebo chyby.  
  
 Vysvětlení  
 Analýza pokrytí kódu se provádí v průběhu testů. Zahrnuje pouze sestavení, která jsou načtena do paměti v průběhu testů. Jestliže nebyl proveden žádný z testů, pak nejsou k dispozici žádné informace pro hlášení o pokrytí kódu.  
  
 Rozlišení  
 V Průzkumníku testů, zvolte **spustit všechny** k ověření, že testy se spustily úspěšně. Opravte všechny chyby před použitím **analyzovat pokrytí kódu**.  
  
### <a name="youre-looking-at-a-previous-result"></a>Je zobrazen předchozí výsledek  
 Při úpravě a opětovném spuštění testů může být stále zobrazen předchozí výsledek pokrytí kódu včetně barevného zvýraznění kódu z minulého spuštění testu.  
  
1.  Spusťte analýzu pokrytí kódu.  
  
2.  Ujistěte se, že jste v okně Výsledky pokrytí kódu vybrali nejaktuálnější sadu výsledků.  
  
### <a name="pdb-symbol-files-are-unavailable"></a>Nejsou k dispozici soubory typu .pdb (symbol)  
 Analýza  
 Otevřete cílovou složku kompilace (obvykle bin\debug) a ověřte, zda existuje pro každé sestavení soubor typu .pdb ve stejném adresáři, ve kterém se nachází soubor typu .dll nebo .exe.  
  
 Vysvětlení  
 Nástroj pokrytí kódu vyžaduje, aby všechna sestavení měla v průběhu testu přístupný svůj přidružený soubor typu .pdb. Pokud nemá konkrétní sestavení přístupný žádný soubor typu .pdb, nebude analyzováno.  
  
 Soubor typu .pdb je nutné vygenerovat ze stejného sestavení jako soubory typu .dll nebo .exe.  
  
 Rozlišení  
 Ujistěte se, že nastavení sestavení generuje soubor typu .pdb. Pokud se po sestavení projektu nejsou aktualizovány soubory typu .pdb, potom otevřete vlastnosti projektu, vyberte **sestavení** zvolte **Upřesnit** a zkontrolujte **ladicí informace**.  
  
 Pokud jsou soubory typu .pdb a .dll nebo .exe na různých místech, zkopírujte soubor typu .pdb do stejného adresáře. Je také možné nakonfigurovat nástroj pokrytí kódu tak, aby hledal soubory typu .pdb v jiném umístění. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).  
  
### <a name="using-an-instrumented-or-optimized-binary"></a>Použití instrumentovaného nebo optimalizovaného binárního souboru  
 Analýza  
 Zjistěte, zda binární soubor podstoupil jakoukoliv formu pokročilé optimalizace, jako je optimalizace na základě profilu, nebo byl instrumentován pomocí nástroje pro profilaci, jako je vsinstr.exe nebo vsperfmon.exe.  
  
 Vysvětlení  
 Pokud již bylo sestavení instrumentováno nebo optimalizováno pomocí jiného nástroje pro profilaci, pak je sestavení vynecháno z analýzy pokrytí kódu.  
  
 Analýza pokrytí kódu nemůže být na takovýchto sestavení provedena.  
  
 Rozlišení  
 Vypněte optimalizaci a použijte nové sestavení.  
  
### <a name="code-is-not-managed-net-or-native-c-code"></a>Kód není spravovaný (.NET) nebo nativní (C++) kód  
 Analýza  
 Ověřte, zda jsou testy spuštěny na spravovaném kódu, nebo na kódu jazyka C++.  
  
 Vysvětlení  
 Analýza pokrytí kódu v sadě Visual Studio je dostupná pouze pro spravovaný a nativní (C++) kód. Při práci s nástroji třetích stran může být část kódu nebo veškerý kód proveden na jiné platformě.  
  
 Rozlišení  
 Žádný k dispozici.  
  
### <a name="assembly-has-been-installed-by-ngen"></a>Sestavení bylo nainstalováno pomocí technologie NGen  
 Analýza  
 Ověřte, že sestavení není načteno z mezipaměti nativní bitové kopie.  
  
 Vysvětlení  
 Z důvodů výkonu nejsou sestavení nativní bitové kopie analyzovány. Další informace najdete v tématu [Ngen.exe (Generátor nativních obrázků)](http://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).  
  
 Rozlišení  
 Použijte verzi sestavení v jazyce MSIL. Nezpracovávejte jej pomocí technologie NGen.  
  
### <a name="custom-runsettings-file-with-bad-syntax"></a>Chybná syntaxe vlastního souboru .runsettings  
 Analýza  
 Pokud používáte vlastní soubor .runsettings, může tento obsahovat chybu syntaxe.  
  
 V důsledku toho se vůbec nespustí pokrytí kódu. Buď se okno pokrytí kódu na konci testu vůbec neotevře, nebo zobrazí staré výsledky.  
  
 Vysvětlení  
 Můžete spustit testování částí s vlastním souborem .runsettings pro nakonfigurování možností pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).  
  
 Rozlišení  
 Existují dva typy možných chyb:  
  
-   **XML došlo k chybě**  
  
     Otevřete soubor .runsettings v editoru jazyka XML sady Visual Studio. Hledejte označení chyb.  
  
-   **Chyba regulárního výrazu**  
  
     Každý řetězec v souboru je regulární výraz. Zkontrolujte všechny, zda v nich nejsou chyby, a hledejte zejména:  
  
    -   Neshoda závorek (...) nebo závorky \\(...) \\). Pokud ve vyhledávacím řetězci chcete najít závorky, musíte je přeskočit. Chcete-li například funkci, použijte: `.*MyFunction\(double\)`  
  
    -   Hvězdička nebo plus na začátku výrazu. Pro vyhledání libovolného řetězce znaků, použijte tečku následovanou hvězdičkou: `.*`  
  
### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Nesprávná vyloučení ve vlastním souboru .runsettings  
 Analýza  
 Pokud používáte vlastní soubor .runsettings, ujistěte se, že obsahuje vaše sestavení.  
  
 Vysvětlení  
 Můžete spustit testování částí s vlastním souborem .runsettings pro nakonfigurování možností pokrytí kódu. Možnosti umožňují zahrnout nebo vyloučit soubory. Další informace najdete v tématu [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).  
  
 Rozlišení  
 Odebrat vše `Include` ze souboru s příponou .runsettings a potom odeberte všechny uzly `Exclude` uzly. Pokud to vyřeší daný problém, vracejte je zpět ve fázích.  
  
 Zkontrolujte, že uzel DataCollectors určuje pokrytí kódu. Porovnejte jej s ukázkou v [přizpůsobení analýzy pokrytí kódu](../test/customizing-code-coverage-analysis.md).  
  
## <a name="some-code-is-always-shown-as-not-covered"></a>Nějaký kód je vždy zobrazen jako nepokrytý  
  
### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Ještě před instrumentací je provedena inicializace kódu v nativní knihovně DLL  
 Analýza  
 Ve staticky propojeném nativním kódu, část inicializační funkce **DllMain** a kód, který volá v některých případech se zobrazí jako nepokryté i když byl proveden kód.  
  
 Vysvětlení  
 Nástroj pokrytí kódu funguje pomocí vložení instrumentace do sestavení těsně před zahájením spuštění aplikace. V jakékoli dříve načteném sestavení se inicializační kód ve **DllMain** provádí co nejdříve po načtení sestavení a před spuštěním aplikace. Tento kód se jeví jako nepokrytý.  
  
 Obvykle to platí pro staticky načtená sestavení.  
  
 Rozlišení  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Použití pokrytí kódu k určení rozsahu testovaného kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)



