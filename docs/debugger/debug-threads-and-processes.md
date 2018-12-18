---
title: Nástroje pro ladění vláken a procesů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/21/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb8c8abab1dc4b8f5778ed4b76688f8a3946e461
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888824"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Nástroje pro ladění vláken a procesů v sadě Visual Studio
*Vlákna* a *procesy* jsou v informatice související koncepty. Obě představují sekvence pokynů, které musí být provedeny v určitém pořadí. Pokyny v oddělených vláknech či procesy lze však spustit paralelně.  
  
 Procesy v operačním systému existují a odpovídají co uživatelé vidí jako programy nebo aplikace. Vlákno, na druhé straně existuje v rámci procesu. Z tohoto důvodu vlákna jsou někdy označovány jako *procesy LWP*. Každý proces se skládá z jednoho nebo více vláken.  
  
 Existence více procesů umožňuje počítači provádět více úkolů současně. Existence více vláken umožňuje procesu pro oddělení práce, kterou můžou provádět souběžně. Na počítači s více procesory mohou procesy nebo vlákna běžet na různých procesorech. To umožňuje pravé paralelní zpracování.  
  
 Perfektní paralelní zpracování není vždy možné. Vlákna v některých případech musí být synchronizovány. Jedno vlákno může muset čekat na výsledky z jiného vlákna, nebo jedno vlákno může potřebovat výhradní přístup k prostředku, který používá jiné vlákno. Potíže se synchronizací jsou běžnou příčinou chyb ve vícevláknových aplikacích. Vlákna mohou někdy skončit čekáním na prostředek, který nikdy nebude k dispozici. Výsledkem je stav nazývaný *zablokování*.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ladicí program poskytuje výkonné, ale snadno použitelné nástroje pro ladění vláken a procesů.  
  
## <a name="tools-and-features"></a>Nástroje a funkce
Nástroje, které potřebujete pro použití v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] závisí na typu kódu, se snažíte ladit:

- Pro procesy, jsou primární nástroje **připojit k procesu** dialogovém okně **procesy** okně a **umístění ladění** nástrojů.

- Vlákna, jsou primární nástroje pro ladění vláken **vlákna** okna, značky vlákna ve zdrojových oknech, **paralelní zásobníky** okně **paralelního sledování** okno, a **umístění ladění** nástrojů.  
  
- Pro kód, který se používá <xref:System.Threading.Tasks.Task> v [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/) (nativní kód), primární nástroje pro ladění aplikací s více vlákny jsou **Paralelní zásobníky** okně **paralelního sledování** okně a **úlohy** okno ( **úlohy** okna podporuje také Objekt promise jazyka JavaScript).

- Pro ladění vláken v GPU je primárním nástrojem **vlákna GPU** systému windows.  
  
  Následující tabulka uvádí dostupné informace a akce, které můžete provádět v každém z těchto míst:  
  
|Uživatelské rozhraní|Informace, které jsou k dispozici|Akce, které můžete provést|  
|--------------------|---------------------------|-----------------------------|  
|**Připojit k procesu** dialogové okno|Dostupné procesy, které lze připojit k:<br /><br /> -Název procesu (.exe)<br />-Zpracování identifikační číslo<br />– Nadpis řádku nabídek<br />– Typ (Managed v4.0; Managed v2.0, v1.1, v1.0; x86; x64; IA64)<br />-Uživatelské jméno (název účtu)<br />– Číslo relace|Vyberte proces pro připojení<br /><br /> Výběr vzdáleného počítače<br /><br /> Změnit typ spojení na připojení ke vzdáleným počítačům|  
|**Procesy** okna|Připojené procesy:<br /><br /> -Proces název<br />-Zpracování identifikační číslo<br />– Cesta ke zpracování .exe<br />– Nadpis řádku nabídek<br />– Stav (Break. Spuštění)<br />-Ladění (nativní, spravované atd.)<br />-Typ přenosu (výchozí, nativní bez ověření)<br />-Kvalifikátor transport (vzdálený počítač)|Nástroje:<br /><br /> – Připojení<br />– Odpojení<br />-Ukončit<br /><br /> Místní nabídka:<br /><br /> – Připojení<br />– Odpojení<br />-Odpojit při zastavení ladění<br />-Ukončit|  
|**Vlákna** okna|Vlákna v aktuálním procesu:<br /><br /> – ID vlákna<br />-Spravované ID<br />-Kategorie (hlavní vlákno, vlákno rozhraní, vzdálené volání rutiny procedury nebo pracovní vlákno)<br />-Název vlákna<br />-Umístění, kde bylo vlákno vytvořeno<br />-Priority<br />-Maska příbuznosti<br />-Pozastavený počet<br />-Proces název<br />-Indikátor příznaku<br />– Indikátor pozastavení|Nástroje:<br /><br /> – Hledání<br />– Zásobník volání hledání<br />-Označit jen můj kód<br />-Volba vlastního modulu příznaků<br />-Seskupit podle<br />-Sloupců<br />-Rozbalit/sbalit zásobníky volání<br />-Rozbalit/sbalit skupiny<br />-Zmrazit/odblokovat vlákna<br /><br /> Místní nabídka:<br /><br /> -Zobrazit vlákna ve zdroji<br />-Přepnout na vlákno<br />-Zmrazit spuštěné vlákno<br />-Povolit zmrazené vlákno<br />-Označit vlákno pro další studie<br />-Zrušit označení vlákna<br />-Přejmenovat vlákno<br />– Zobrazení a skrytí vláken<br /><br /> Další akce:<br /><br /> – Zobrazení zásobníku volání pro vlákno v DataTip|  
|Okno zdroje|Indikátory vláken v levém hřbetu označují jedno nebo více vláken (vypnuté ve výchozím nastavení, zapnuté pomocí místní nabídky v **vlákna** okna)|Místní nabídka:<br /><br /> -Přepnout na vlákno<br />-Označit vlákno pro další studie<br />-Zrušit označení vlákna|  
|**Ladit umístění** nástrojů|-Aktuální proces<br />-Pozastaví aplikaci<br />-Obnovte chod aplikace<br />-Pozastavit a vypnout aplikaci<br />-Aktuální vlákno<br />– Přepnout aktuální značku stavu vlákna<br />-Zobrazit pouze vlákna označená příznakem<br />-Zobrazit pouze aktuální proces<br />-Aktuální rámec zásobníku|-Přepnout na jiný proces<br />-Pozastavit, pokračovat nebo vypnout aplikaci<br />-Přepnout do jiného vlákna v aktuálním procesu<br />-Přepnout do jiného zásobníku v aktuálním vlákně<br />-Příznak nebo odstranění označení aktuálních vláken<br />-Zobrazit pouze vlákna označená příznakem<br />-Zobrazit pouze aktuální proces|  
|**Paralelní zásobníky** okna|-Zásobníky volání pro více vláken v jednom okně.<br />-Aktivní zásobník snímků pro každé vlákno.<br />-Volající a volané pro libovolnou metodu.|-Odfiltrovat zadaná vlákna<br />-Přepnout do zobrazení úlohy<br />-Označit nebo zrušit označení vlákna<br />-Přiblížení|   
|**Paralelní sledování** okna|-Sloupec příznaku, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.<br />-Sloupec rámce, ve kterém šipka označuje vybraný rámec.<br />-Konfigurovatelný sloupec, který může zobrazit počítač, proces, dlaždici, úloh a vlákna.|-Označit nebo zrušit označení vlákna<br />-Zobrazit pouze vlákna označená příznakem<br />-Rámce přepínačů<br />-Řazení sloupce<br />-Skupiny vláken<br />-Zmrazit nebo odblokovat vlákna<br />-export dat v okně paralelního sledování| 
|**Úlohy** okna|– Zobrazení informací o <xref:System.Threading.Tasks.Task> objektů včetně ID úkolu, stavu úkolu (naplánované, spuštěný, čekající, zablokována), a které vlákno je přiřazeno k úkolu.<br />-Aktuální umístění v zásobníku volání.<br />-Delegát předaný do úlohy v okamžiku vytvoření|-Přepnout do aktuální úlohy<br />-Příznak nebo odznačit úlohu<br />-Zmrazit nebo odblokovat úkol|  
|**Vlákna GPU** okna|-Sloupec příznaku, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.<br />-Aktuální vlákno sloupec, ve kterém žlutá šipka označuje aktuální vlákno.<br />– **Počet vláken** sloupec, který zobrazuje počet vláken ve stejném umístění.<br />– **Řádku** sloupec, který zobrazuje řádek kódu, kde je každá skupina vlákna umístěna.<br />– **Adresu** sloupec, který zobrazuje adresu instrukce, kde je každá skupina vlákna umístěna.<br />– **Umístění** sloupec, který je umístěním v kódu adresy.<br />– **Stav** sloupec, který ukazuje, zda je podproces aktivní nebo blokován.<br />– **Dlaždici** sloupec, který zobrazuje indexu dlaždice pro podprocesy v řádku.|– Změnit na jiném vlákně<br />– Zobrazení konkrétní pole a vlákno<br />-Zobrazit nebo skrýt sloupec<br />-Řazení podle sloupce<br />-Skupiny vláken<br />-Zmrazit nebo odblokovat vlákna<br />-Označit nebo zrušit označení vlákna<br />-Zobrazit pouze vlákna označená příznakem|  
  
## <a name="see-also"></a>Viz také  
 [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Ladění kódu GPU](../debugger/debugging-gpu-code.md)