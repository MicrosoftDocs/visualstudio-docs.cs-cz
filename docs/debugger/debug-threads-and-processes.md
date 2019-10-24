---
title: Nástroje pro ladění vláken a procesů | Microsoft Docs
ms.date: 04/21/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcdaf083462b75485449cae05894681e2bb5c900
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738383"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Nástroje pro ladění vláken a procesů v aplikaci Visual Studio
*Vlákna* a *procesy* jsou související koncepty v oblasti počítačové vědy. Obě reprezentují sekvence instrukcí, které se musí provést v určitém pořadí. Pokyny v samostatných vláknech nebo procesech ale mohou být spouštěny paralelně.

 Procesy existují v operačním systému a odpovídají uživatelům, kteří se zobrazí jako programy nebo aplikace. Na druhé straně existuje vlákno v rámci procesu. Z tohoto důvodu se vlákna někdy označují jako procesy v *lehkém poměru*. Každý proces se skládá z jednoho nebo více vláken.

 Existence více procesů umožňuje počítači najednou provádět více než jeden úkol. Existence více vláken umožňuje procesu oddělit činnost, která se má provádět paralelně. V počítači s více procesory můžou být procesy nebo vlákna spuštěné v různých procesorech. To umožňuje pravdivé paralelní zpracování.

 Dokonalé paralelní zpracování není vždy možné. Vlákna se někdy musí synchronizovat. Jedno vlákno může vyžadovat, aby čekal na výsledek z jiného vlákna, nebo jedno vlákno může potřebovat výhradní přístup k prostředku, který používá jiné vlákno. Problémy s synchronizací jsou běžnou příčinou chyb v aplikacích s více vlákny. Někdy mohou vlákna skončit čekáním na prostředek, který nikdy nebude k dispozici. Výsledkem je podmínka s názvem *zablokování*.

 Ladicí program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poskytuje výkonné, ale snadno použitelné nástroje pro ladění vláken a procesů.

## <a name="tools-and-features"></a>Nástroje a funkce
Nástroje, které je třeba použít v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] závisí na typu kódu, který se pokoušíte ladit:

- Pro procesy jsou primární nástroje v dialogovém okně **připojit k procesu** , v okně **procesy** a na panelu nástrojů **umístění ladění** .

- Pro vlákna jsou primární nástroje pro ladění vláken okno **vlákna** , značky vláken v okně zdrojové okna, **paralelní zásobníky** , okno **paralelního sledování** a panel nástrojů **umístění ladění** .

- Pro kód, který používá <xref:System.Threading.Tasks.Task> v [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/) (nativní kód), jsou primární nástroje pro ladění vícevláknových aplikací okno **paralelní zásobníky** , **paralelní sledování** okno a okno **úlohy** (okno **úlohy** také podporuje objekt Promise JavaScriptu).

- Pro ladění vláken na GPU je primárním nástrojem okna **vláken GPU** .

  V následující tabulce jsou uvedené informace, které jsou k dispozici, a akce, které můžete provádět v každém z těchto umístění:

|Uživatelské rozhraní|Dostupné informace|Akce, které můžete provádět|
|--------------------|---------------------------|-----------------------------|
|Dialogové okno **připojit k procesu**|Dostupné procesy, ke kterým se můžete připojit:<br /><br /> -Název procesu (. exe)<br />– Číslo ID procesu<br />– Název řádku nabídek<br />-Type (spravované v 4.0; Managed v 2.0, v 1.1, v 1.0; architektur platformě SYSTÉMY<br />-Uživatelské jméno (název účtu)<br />– Číslo relace|Vyberte proces, ke kterému se chcete připojit.<br /><br /> Vybrat vzdálený počítač<br /><br /> Změnit typ přenosu pro připojení ke vzdáleným počítačům|
|Okno **procesů**|Připojené procesy:<br /><br /> – Název procesu<br />– Číslo ID procesu<br />-Cesta ke zpracování. exe<br />– Název řádku nabídek<br />-State (Break. Instalovanou<br />-Ladění (nativní, spravované atd.)<br />-Transport – typ (výchozí, nativní bez ověřování)<br />– Kvalifikátor přenosu (vzdálený počítač)|Nástroje<br /><br /> – Připojit<br />– Odpojit<br />– Ukončit<br /><br /> Místní nabídka:<br /><br /> – Připojit<br />– Odpojit<br />-Odpojit při zastavení ladění<br />– Ukončit|
|Okno **vláken**|Vlákna v aktuálním procesu:<br /><br /> – ID vlákna<br />– Spravované ID<br />-Kategorie (hlavní vlákno, vlákno rozhraní, obslužná rutina vzdáleného volání procedury nebo pracovní vlákno)<br />– Název vlákna<br />– Umístění, kde se vytvoří vlákno<br />-Priorita<br />– Maska spřažení<br />-Počet pozastavených<br />– Název procesu<br />-Příznak – indikátor<br />– Indikátor pozastavení|Nástroje<br /><br /> – Search<br />-Vyhledat zásobník volání<br />– Příznak Pouze můj kód<br />-Flag – výběr vlastního modulu<br />– Seskupit podle<br />-Columns<br />-Rozbalit/sbalit zásobníky volání<br />-Rozbalit/sbalit skupiny<br />– Zablokovat/uvolnit vlákna<br /><br /> Místní nabídka:<br /><br /> -Zobrazit vlákna ve zdroji<br />– Přepnout na vlákno<br />– Zmrazení běžícího vlákna<br />– Uvolnění zmrazeného vlákna<br />-Označit vlákno pro další studii<br />-Zrušit označení vlákna<br />-Přejmenovat vlákno<br />-Zobrazit a skrýt vlákna<br /><br /> Další akce:<br /><br /> -Zobrazení zásobníku volání pro vlákno v DataTip|
|Okno zdroje|Indikátory vlákna v levém hřbetu naznačují jedno nebo více vláken (ve výchozím nastavení vypnuté, zapnuté pomocí místní nabídky v okně **vláken** ).|Místní nabídka:<br /><br /> – Přepnout na vlákno<br />-Označit vlákno pro další studii<br />-Zrušit označení vlákna|
|Panel nástrojů **umístění ladění**|– Aktuální proces<br />-Pozastavit aplikaci<br />– Obnovení aplikace<br />– Pozastavit a vypnout aplikaci<br />– Aktuální vlákno<br />-Přepnout stav příznaku aktuálního vlákna<br />-Zobrazit pouze vlákna označená příznakem<br />-Zobrazit pouze aktuální proces<br />– Aktuální rámec zásobníku|– Přepnout na jiný proces<br />– Pozastavení, obnovení nebo ukončení aplikace<br />– Přepne na jiné vlákno v aktuálním procesu.<br />– Přepnout na jiný rámec zásobníku v aktuálním vlákně<br />– Příznak nebo odoznačení aktuálního vlákna<br />-Zobrazit pouze vlákna označená příznakem<br />-Zobrazit pouze aktuální proces|
|Okno **paralelní zásobníky**|-Zásobníky volání pro více vláken v jednom okně.<br />– Aktivní rámec zásobníku pro každé vlákno.<br />– Volající a volané pro jakoukoliv metodu.|– Filtrování zadaných vláken<br />– Přepnout na zobrazení úkolů<br />– Příznak nebo odoznačení vlákna<br />– Lupa|
|Okno **paralelního sledování**|– Sloupec příznak, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.<br />– Sloupec Frame, ve kterém šipka indikuje vybraný snímek.<br />– Konfigurovatelný sloupec, který může zobrazit počítač, proces, dlaždici, úlohu a vlákno.|– Příznak nebo odoznačení vlákna<br />-Zobrazit pouze vlákna označená příznakem<br />-Switch – snímky<br />-Řazení sloupce<br />-Seskupit vlákna<br />– Zmrazení nebo odmrazení vláken<br />-Exportujte data v paralelním okno Kukátko|
|Okno **úlohy**|-Zobrazit informace o <xref:System.Threading.Tasks.Task> objektů včetně ID úlohy, stavu úlohy (naplánované, spuštěné, čekání, zablokované) a který podproces je přiřazen k úloze.<br />– Aktuální umístění v zásobníku volání.<br />-Delegát byl předán do úlohy v okamžiku vytvoření.|– Přepnout na aktuální úlohu<br />– Příznak nebo odoznačení úlohy<br />– Zmrazení nebo odmrazení úlohy|
|Okno **vláken GPU**|– Sloupec příznak, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.<br />– Aktuální sloupec vlákna, ve kterém žlutá šipka indikuje aktuální vlákno.<br />– Sloupec **počet vláken** , který zobrazuje počet vláken ve stejném umístění.<br />– Sloupec **line** , který zobrazuje řádek kódu, kde se nachází každá skupina vláken.<br />– Sloupec **adresa** , který zobrazuje adresu instrukcí, kde se nachází každá skupina vláken.<br />– Sloupec **Location (umístění** ), což je umístění v kódu adresy.<br />– Sloupec **Status (stav** ), který ukazuje, zda je vlákno aktivní nebo blokované.<br />– Sloupec **dlaždice** , ve kterém se zobrazuje index dlaždice pro vlákna na řádku.|– Změna na jiné vlákno<br />-Zobrazit konkrétní dlaždici a vlákno<br />-Zobrazit nebo skrýt sloupec<br />– Řazení podle sloupce<br />-Seskupit vlákna<br />– Zmrazení nebo odmrazení vláken<br />– Příznak nebo odoznačení vlákna<br />-Zobrazit pouze vlákna označená příznakem|

## <a name="see-also"></a>Viz také:

- [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Ladění kódu GPU](../debugger/debugging-gpu-code.md)