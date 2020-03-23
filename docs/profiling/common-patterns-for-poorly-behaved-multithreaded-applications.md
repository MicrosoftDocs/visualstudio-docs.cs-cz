---
title: Běžné vzory pro špatně-choval multithreaded aplikace | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aec033266ccb2a6e6dcd0342669b7c31082488a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62788853"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Obecné vzory pro vícevláknové aplikace s nevhodným chováním

Vizualizér souběžnosti pomáhá vývojářům vizualizovat chování vícevláknové aplikace. Tento nástroj obsahuje galerii běžných vzorů pro vícevláknové aplikace, které se chovají špatně. Galerie obsahuje typické a rozpoznatelné vizuální vzory, které jsou vystaveny prostřednictvím nástroje, spolu s vysvětlením chování, které je reprezentováno každým vzorem, pravděpodobným výsledkem tohoto chování a nejběžnějším přístupem k jeho vyřešení.

## <a name="lock-contention-and-serialized-execution"></a>Konflikty zámků a serializované spuštění

![Konflikty zámků, které vedou k serializovanému spuštění](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

Někdy paralelizované aplikace tvrdohlavě pokračuje v sériovém spuštění, i když má několik podprocesů a počítač má dostatečný počet logických jader. Prvním příznakem je špatný výkon s více vlákny, možná i o něco pomalejší než sériová implementace. V zobrazení vláken nevidíte více vláken spuštěných paralelně; místo toho uvidíte, že pouze jedno vlákno je spuštěna kdykoli. V tomto okamžiku pokud klepnete na segment synchronizace ve vlákně, zobrazí se zásobník volání pro blokované vlákno (blokování zásobníku volání) a vlákno, které odstranilo podmínku blokování (odblokování zásobníku volání). Kromě toho pokud dojde k odblokování zásobníku volání v procesu, který analyzujete, zobrazí se konektor připravený pro přístup pod procesu. Od tohoto okamžiku můžete přejít na váš kód z blokování a odblokování zásobníky volání prozkoumat příčinu serializace ještě více.

Jak je znázorněno na následujícím obrázku, vizualizér souběžnosti může také vystavit tento příznak v zobrazení využití procesoru, kde i přes přítomnost více vláken aplikace spotřebovává pouze jedno logické jádro.

Další informace naleznete v části "Start with the Problem section" v článku časopisu MSDN [Thread Performance - Profilování souběžnosti konfliktů prostředků v sadě Visual Studio 2010](https://msdn.microsoft.com/magazine/ff714587.aspx).

![Konflikty zámků](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>Distribuce nerovnoměrného pracovního vytížení

![Nerovnoměrné pracovní zatížení](../profiling/media/unevenworkload_1.png "UnevenWorkLoad_1")

Dojde-li k nepravidelnému rozdělení práce v několika paralelních vláknech v aplikaci, zobrazí se při dokončení práce každého vlákna typický vzor krok schodiště, jak je znázorněno na předchozím obrázku. Vizualizér souběžnosti nejčastěji zobrazuje velmi blízké časy zahájení pro každé souběžné vlákno. Tato vlákna však obvykle končí nepravidelným způsobem namísto ukončení současně. Tento vzor označuje nepravidelné rozdělení práce mezi skupinou paralelních vláken, což by mohlo vést ke snížení výkonu. Nejlepším přístupem k takovému problému je přehodnotit algoritmus, podle kterého byla práce rozdělena mezi paralelní vlákna.

Jak je znázorněno na následujícím obrázku, vizualizér souběžnosti může také vystavit tento příznak v zobrazení využití procesoru jako postupný krok dolů v využití procesoru.

![Nerovnoměrné pracovní zatížení](../profiling/media/unevenworkload_2.png "UnevenWorkload_2")

## <a name="oversubscription"></a>Přeplatný odběr

![Přeplatný odběr](../profiling/media/oversubscription.png "Přeplatný odběr")

V případě oversubscription počet aktivních podprocesů v procesu je větší než počet dostupných logických jader v systému. Předchozí obrázek znázorňuje výsledky oversubscription, s významným preemption pruhování ve všech aktivních vláken. Kromě toho legenda ukazuje velké procento času stráveného v preemption (84 procent v tomto příkladu). To může znamenat, že proces žádá systém o spuštění více souběžných vláken než počet logických jader. To však může také znamenat, že jiné procesy v systému používají prostředky, o kterých se předpokládalo, že jsou pro tento proces k dispozici.

Při vyhodnocování tohoto problému byste měli zvážit následující:

- Celkový systém může být přepsán. Zvažte, že jiné procesy v systému může být preempting vaše podprocesy. Když pozastavíte preemption segment v zobrazení vláken, popisek identifikuje vlákno a proces, který předběhl vlákno. Tento proces není nutně ten, který byl proveden po celou dobu, že váš proces byl preempted, ale poskytuje nápovědu o tom, co vytvořilo preemption tlak proti procesu.

- Vyhodnoťte, jak proces určuje příslušný počet podprocesů pro spuštění během této fáze práce. Pokud váš proces přímo vypočítá počet aktivních paralelních vláken, zvažte úpravu tohoto algoritmu tak, aby lépe zohledňoval počet dostupných logických jader v systému. Pokud používáte souběžnost Runtime, paralelní knihovna úloh nebo PLINQ, tyto knihovny provádět práci výpočtu počtu podprocesů.

## <a name="inefficient-io"></a>Neefektivní vstupně-nosné

![Neefektivní I&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

Nadměrné používání nebo zneužití vstupně-va je častou příčinou neefektivnosti v aplikacích. Zvažte předchozí obrázek. Profil viditelné časové osy ukazuje, že 44 procent viditelného času vlákna je spotřebováno vstupně-v. Časová osa zobrazuje velké množství vstupně-va, což znamená, že profilované aplikace je často blokován vstupně-v. Chcete-li zobrazit podrobnosti o typech vstupně-va a kde je program blokován, přibližte problematické oblasti, prohlédněte si profil viditelné časové osy a kliknutím na konkrétní blok vstupně-out zobrazilte aktuální zásobníky volání.

## <a name="lock-convoys"></a>Zamknutí konvojů

![Zamknutí konvojů](../profiling/media/lock_convoys.png "Lock_Convoys")

Uzamčení konvoje dojít, když aplikace získá zámky v pořadí kdo dřív přijde, je dřív na řadě, a když je rychlost příjezdu na zámku vyšší než míra pořízení. Kombinace těchto dvou podmínek způsobí, že požadavky na zámek spustit zálohování. Jedním ze způsobů, jak bojovat proti tomuto problému, je použití "nespravedlivé" zámky, nebo zámky, které poskytují přístup k první vlákno najít v odemčených státech. Předchozí obrázek znázorňuje toto chování konvoje. Chcete-li problém vyřešit, zkuste snížit kolize pro objekty synchronizace a zkuste použít nespravedlivé zámky.

## <a name="see-also"></a>Viz také

[Zobrazení vláken](../profiling/threads-view-parallel-performance.md)