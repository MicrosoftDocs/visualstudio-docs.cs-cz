---
title: Ladění vláken a procesů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df9bc7cdb185edd27d7572c1436db442514d38e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202567"
---
# <a name="debug-threads-and-processes"></a>Ladění vláken a procesů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vlákna * a *procesy* jsou související koncepty v oblasti počítačové vědy. Obě reprezentují sekvence instrukcí, které se musí provést v určitém pořadí. Pokyny v samostatných vláknech nebo procesech ale mohou být spouštěny paralelně.  
  
 Procesy existují v operačním systému a odpovídají uživatelům, kteří se zobrazí jako programy nebo aplikace. Na druhé straně existuje vlákno v rámci procesu. Z tohoto důvodu se vlákna někdy označují jako procesy v *lehkém poměru*. Každý proces se skládá z jednoho nebo více vláken.  
  
 Existence více procesů umožňuje počítači najednou provádět více než jeden úkol. Existence více vláken umožňuje procesu oddělit činnost, která se má provádět paralelně. V počítači s více procesory můžou být procesy nebo vlákna spuštěné v různých procesorech. To umožňuje pravdivé paralelní zpracování.  
  
 Dokonalé paralelní zpracování není vždy možné. Vlákna se někdy musí synchronizovat. Jedno vlákno může vyžadovat, aby čekal na výsledek z jiného vlákna, nebo jedno vlákno může potřebovat výhradní přístup k prostředku, který používá jiné vlákno. Problémy s synchronizací jsou běžnou příčinou chyb v aplikacích s více vlákny. Někdy mohou vlákna skončit čekáním na prostředek, který nikdy nebude k dispozici. Výsledkem je podmínka s názvem *zablokování*.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ladicí program poskytuje výkonné, ale snadno použitelné nástroje pro ladění vláken a procesů.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Nástroje pro ladění vláken a procesů v aplikaci Visual Studio  
 Primární nástroje pro práci s procesy v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jsou dialogové okno **připojit k procesu** , okno **procesy** a panel nástrojů **umístění ladění** . Primární nástroje pro ladění vláken jsou okno **vlákna** , značky vláken ve zdrojových oknech a panel nástrojů **umístění ladění** .  
  
 Primární nástroje pro ladění aplikací s více vlákny jsou **paralelní zásobníky** a **Paralelní úlohy**, **paralelní sledování**a **vlákna GPU** .  
  
 V následující tabulce jsou uvedené informace, které jsou k dispozici, a akce, které můžete provádět v každém z těchto umístění:  
  
|Uživatelské rozhraní|Dostupné informace|Akce, které můžete provádět|  
|--------------------|---------------------------|-----------------------------|  
|Dialogové okno **připojit k procesu**|Dostupné procesy, ke kterým se můžete připojit:<br /><br /> -Název procesu (. exe)<br />– Číslo ID procesu<br />– Název řádku nabídek<br />-Type (spravované v 4.0; Managed v 2.0, v 1.1, v 1.0; architektur platformě SYSTÉMY<br />-Uživatelské jméno (název účtu)<br />– Číslo relace|Vyberte proces, ke kterému se chcete připojit.<br /><br /> Vybrat vzdálený počítač<br /><br /> Změnit typ přenosu pro připojení ke vzdáleným počítačům|  
|Okno **procesů**|Připojené procesy:<br /><br /> – Název procesu<br />– Číslo ID procesu<br />-Cesta ke zpracování. exe<br />– Název řádku nabídek<br />-State (Break. Instalovanou<br />-Ladění (nativní, spravované atd.)<br />-Transport – typ (výchozí, nativní bez ověřování)<br />– Kvalifikátor přenosu (vzdálený počítač)|Nástroje<br /><br /> – Připojit<br />– Odpojit<br />– Ukončit<br /><br /> Místní nabídka:<br /><br /> – Připojit<br />– Odpojit<br />-Odpojit při zastavení ladění<br />– Ukončit|  
|Okno **vláken**|Vlákna v aktuálním procesu:<br /><br /> – ID vlákna<br />– Spravované ID<br />-Kategorie (hlavní vlákno, vlákno rozhraní, obslužná rutina vzdáleného volání procedury nebo pracovní vlákno)<br />– Název vlákna<br />– Umístění, kde se vytvoří vlákno<br />-Priorita<br />– Maska spřažení<br />-Počet pozastavených<br />– Název procesu<br />-Příznak – indikátor<br />– Indikátor pozastavení|Nástroje<br /><br /> – Search<br />-Vyhledat zásobník volání<br />– Příznak Pouze můj kód<br />-Flag – výběr vlastního modulu<br />– Seskupit podle<br />-Columns<br />-Rozbalit/sbalit zásobníky volání<br />-Rozbalit/sbalit skupiny<br />– Zablokovat/uvolnit vlákna<br /><br /> Místní nabídka:<br /><br /> -Zobrazit vlákna ve zdroji<br />– Přepnout na vlákno<br />– Zmrazení běžícího vlákna<br />– Uvolnění zmrazeného vlákna<br />-Označit vlákno pro další studii<br />-Zrušit označení vlákna<br />-Přejmenovat vlákno<br />-Zobrazit a skrýt vlákna<br /><br /> Další akce:<br /><br /> -Zobrazení zásobníku volání pro vlákno v DataTip|  
|Okno zdroje|Indikátory vlákna v levém hřbetu naznačují jedno nebo více vláken (ve výchozím nastavení vypnuté, zapnuté pomocí místní nabídky v okně **vláken** ).|Místní nabídka:<br /><br /> – Přepnout na vlákno<br />-Označit vlákno pro další studii<br />-Zrušit označení vlákna|  
|Panel nástrojů **umístění ladění**|– Aktuální proces<br />-Pozastavit aplikaci<br />– Obnovení aplikace<br />– Pozastavit a vypnout aplikaci<br />– Aktuální vlákno<br />-Přepnout stav příznaku aktuálního vlákna<br />-Zobrazit pouze vlákna označená příznakem<br />-Zobrazit pouze aktuální proces<br />– Aktuální rámec zásobníku|– Přepnout na jiný proces<br />– Pozastavení, obnovení nebo ukončení aplikace<br />– Přepne na jiné vlákno v aktuálním procesu.<br />– Přepnout na jiný rámec zásobníku v aktuálním vlákně<br />– Příznak nebo odoznačení aktuálního vlákna<br />-Zobrazit pouze vlákna označená příznakem<br />-Zobrazit pouze aktuální proces|  
|Okno **paralelní zásobníky**|-Zásobníky volání pro více vláken v jednom okně.<br />– Aktivní rámec zásobníku pro každé vlákno.<br />– Volající a volané pro jakoukoliv metodu.|– Filtrování zadaných vláken<br />– Přepne do zobrazení Paralelní úlohy.<br />– Příznak nebo odoznačení vlákna<br />– Lupa|  
|Okno **Paralelní úlohy**|-Zobrazit informace o <xref:System.Threading.Tasks.Task> objektech včetně ID úlohy, stavu úlohy (naplánované, spuštěné, čekání, zablokované) a který podproces je přiřazen k úloze.<br />– Aktuální umístění v zásobníku volání.<br />-Delegát byl předán do úlohy v okamžiku vytvoření.|– Přepnout na aktuální úlohu<br />– Příznak nebo odoznačení úlohy<br />– Zmrazení nebo odmrazení úlohy|  
|Okno **paralelního sledování**|– Sloupec příznak, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.<br />– Sloupec Frame, ve kterém šipka indikuje vybraný snímek.<br />– Konfigurovatelný sloupec, který může zobrazit počítač, proces, dlaždici, úlohu a vlákno.|– Příznak nebo odoznačení vlákna<br />-Zobrazit pouze vlákna označená příznakem<br />-Switch – snímky<br />-Řazení sloupce<br />-Seskupit vlákna<br />– Zmrazení nebo odmrazení vláken<br />-Exportujte data v paralelním okno Kukátko|  
|Okno **vláken GPU**|– Sloupec příznak, ve kterém můžete označit vlákno, kterému chcete věnovat zvláštní pozornost.<br />– Aktivní sloupec vlákna, ve kterém žlutá šipka označuje aktivní vlákno. Šipka označuje vlákno, ve kterém se provádění podařilo přerušit do ladicího programu.<br />– Sloupec **počet vláken** , který zobrazuje počet vláken ve stejném umístění.<br />– Sloupec **line** , který zobrazuje řádek kódu, kde se nachází každá skupina vláken.<br />– Sloupec **adresa** , který zobrazuje adresu instrukcí, kde se nachází každá skupina vláken.<br />– Sloupec **Location (umístění** ), což je umístění v kódu adresy.<br />– Sloupec **Status (stav** ), který ukazuje, zda je vlákno aktivní nebo blokované.<br />– Sloupec **dlaždice** , ve kterém se zobrazuje index dlaždice pro vlákna na řádku.|– Změna na jiné aktivní vlákno<br />-Zobrazit konkrétní dlaždici a vlákno<br />-Zobrazit nebo skrýt sloupec<br />– Řazení podle sloupce<br />-Seskupit vlákna<br />– Zmrazení nebo odmrazení vláken<br />– Příznak nebo odoznačení vlákna<br />-Zobrazit pouze vlákna označená příznakem|  
  
## <a name="see-also"></a>Viz také  
 [Připojit ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Ladění vícevláknových aplikací](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Ladění kódu GPU](../debugger/debugging-gpu-code.md)
