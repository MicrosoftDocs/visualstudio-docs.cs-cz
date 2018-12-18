---
title: Obecné vzory pro vícevláknové aplikace s nevhodným chováním | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9929fc5acfe58d51de9142abc7addd539cf2b74e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34549003"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Obecné vzory pro vícevláknové aplikace s nevhodným chováním

Vizualizér souběžnosti pomáhá vývojářům vizualizovat chování aplikace s více vlákny. Tento nástroj obsahuje galerii obecné vzory pro vícevláknové aplikace, které se chovají chybně. Galerie obsahuje typické a rozpoznatelném visual vzorů, které jsou k dispozici prostřednictvím nástroje, společně s vysvětlení chování, která je reprezentována každý vzor, pravděpodobně výsledkem tohoto chování a nejběžnější přístup při řešení.

## <a name="lock-contention-and-serialized-execution"></a>Uzamčení kolize a serializovaných provádění

![Zamknout výsledné serializovaných provádění kolize](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Někdy parallelized aplikace stubbornly bude pokračovat v provádění sériově i když má několik vláken a má počítač dostatečný počet logických jader. První symptomem je nízký vícevláknové výkon možná i trochu nižší než sériové implementace. V zobrazení vláken nevidíte více vláken paralelně; Místo toho uvidíte, že kdykoli je prováděna pouze jedno vlákno. V tomto okamžiku Pokud klepnete na segment synchronizace v podprocesu, najdete v zásobníku volání pro blokované vlákno (blokování zásobník volání) a vlákno, které odebrat blokování podmínku (odblokování zásobníku volání). Kromě toho pokud v procesu, který analýze dojde k odblokování zásobníku volání, se zobrazí konektor připravené pro přístup z více vláken. Z tohoto bodu můžete přejít na váš kód z zásobníky volání blokování a odblokování zjistěte příčinu serializace i další.

Jak je znázorněno na následujícím obrázku, vizualizér souběžnosti můžete také zveřejnit tento příznak v zobrazení využití procesoru, kde, bez ohledu na přítomnost více vláken, aplikace využívá jenom jednoho logického jádra.

Další informace najdete v tématu "výkonu vzor 1: identifikace zámků" v Hazim Shafi [paralelní nástroje pro sledování výkonu pro systém Windows](http://go.microsoft.com/fwlink/?LinkID=160569) příspěvku na blogu webu MSDN.

![Zamknout kolizí](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Rozdělení nerovnoměrné pracovního vytížení

![Nevyrovnaná zatížení](../profiling/media/unevenworkload_1.png "UnevenWorkLoad_1")

V případě jako nestandardní distribučního práce přes několik paralelních vláken v aplikaci typické schody vzor objeví jako každé vlákno nedokončí svoji práci, jak je vidět na předchozím obrázku. Vizualizér souběžnosti nejčastěji ukazuje velmi zavřít počáteční časy pro každou souběžných vláken. Ale tyto vláken obvykle ukončení nesprávným způsobem místo ukončení současně. Tento vzor označuje jako nestandardní distribučního práce mezi skupinu paralelních vláken, které by mohla vést ke snížení výkonu. Nejlepší metodou k těmto potížím je přehodnocovat algoritmus, podle kterého, pracovní rozdělena mezi paralelních vláken.

Jak je znázorněno na následujícím obrázku, vizualizér souběžnosti také zveřejnit tento příznak v zobrazení využití procesoru jako postupná step-down využití procesoru.

![Nevyrovnaná zatížení](../profiling/media/unevenworkload_2.png "UnevenWorkload_2")

## <a name="oversubscription"></a>Překryvný odběr

![Překryvný odběr](../profiling/media/oversubscription.png "Překryvný odběr")

V případě Překryvný odběr počet aktivních vláken v procesu je větší než počet dostupných logických jader v systému. Na předchozím obrázku výsledky Překryvný odběr s významné přerušování řazení do pásem ve všech aktivních podprocesů. Kromě toho legendu ukazuje, že je vysoké procento času stráveného v přerušení (v procentech 84 v tomto příkladu). To může znamenat, že je proces žádostí spuštění více souběžných vláken než počet logických jader v systému. Ale to může také indikovat, že prostředky, které se předpokládá, že k dispozici pro tento proces používají jiné procesy v systému.

Při hodnocení tohoto problému je třeba zvážit následující:

- Může být oversubscribed celého systému. Zvažte, zda jiné procesy v systému může preempting vaše vláken. Při přesunutí ukazatele myši nad segment přerušení v zobrazení vláken, bude popisek identifikovat vlákno a proces, který zrušené vlákno. Tento proces nutně není ta, která spouští ve druhém po celou dobu, která byla zrušené váš proces, ale poskytuje nápovědu o co vytvořili přerušování tlak na váš proces.

- Vyhodnoťte, určuje, jak váš proces odpovídající počet podprocesů pro spuštění v průběhu této fáze práce. Pokud váš proces přímo vypočítá počet aktivních podprocesů paralelní, zvažte, jestli tento algoritmus k lepší účtu pro počet jader dostupné logické v systému. Pokud používáte Concurrency Runtime, Task Parallel Library a PLINQ, proveďte tyto knihovny práci při výpočtu počet vláken.

## <a name="inefficient-io"></a>Neefektivní vstupně-výstupních operací

![Neefektivní I&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

Nadměrné využití nebo zneužití vstupně-výstupních operací je obvyklou příčinou toho umožňuje zvýšit efektivitu v aplikacích. Vezměte v úvahu na předchozím obrázku. Profil viditelné časové osy ukazuje, že 44 procent času viditelné vlákno spotřebovávají vstupně-výstupní operace. Časová osa ukazuje velké objemy vstupně-výstupních operací, které označuje, že aplikace PROFILOVANÉHO je často blokována vstupně-výstupní operace. Chcete-li zobrazit podrobnosti o typech vstupně-výstupních operací a kde je váš program zablokuje, zvětšení problematických oblastí, zkontrolujte profil viditelné časové osy a klikněte blok konkrétní vstupně-výstupních operací zobrazíte aktuální zásobníky volání.

## <a name="lock-convoys"></a>Zámek sestavy

![Zamknout sestavy](../profiling/media/lock_convoys.png "Lock_Convoys")

Při zámky v pořadí dřív přijde, dřív získá aplikace, a jestliže je míra přijetí na zámek vyšší než počet pořízení dojde k uzamčení sestavy. Kombinace těchto dvou případů způsobí, že žádosti o zámek spusťte zálohování. Jedním ze způsobů boje proti tomuto problému se má používat "nekalé" zámky nebo zámky, která umožňují přístup k první vlákno, kde je najít v odemknout stavy. Toto chování convoy na předchozím obrázku. Chcete-li problém vyřešit, zkuste zmenšit kolizí pro objekty synchronizace a zkuste to pomocí nekalé zámky.

## <a name="see-also"></a>Viz také:

[Zobrazení vláken](../profiling/threads-view-parallel-performance.md)