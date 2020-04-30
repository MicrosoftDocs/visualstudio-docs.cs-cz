---
title: Běžné vzory pro vícevláknové aplikace, které se nesprávně chovají | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
ms.assetid: 00d10629-e20f-4d6d-8643-c59a3879812e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 128de95d347fece01c9177057346b00e412e1e6f
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586639"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>Obecné vzory pro vícevláknové aplikace s nevhodným chováním
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vizualizátor souběžnosti pomáhá vývojářům vizualizovat chování vícevláknové aplikace. Tento nástroj zahrnuje galerii běžných vzorů pro vícevláknové aplikace, které se chovají chybně. Galerie obsahuje typické a rozpoznatelné vizuální vzory, které jsou zpřístupněny prostřednictvím nástroje, spolu s vysvětlením chování, které je reprezentováno jednotlivými vzory, pravděpodobným výsledkem tohoto chování a Nejběžnějším přístupem k jeho vyřešení.  
  
## <a name="lock-contention-and-serialized-execution"></a>Kolize zámků a serializovaného spouštění  
 ![Kolize zámku vyplývající z serializovaného spuštění](../profiling/media/lockcontention-serialized.png "LockContention_Serialized")  
  
 V některých případech je stubbornly paralelní aplikace i nadále spouštěna i v případě, že má několik vláken a počítač má dostatečný počet logických jader. Prvním příznakem je nízký výkon s více vlákny, možná i trochu pomalejší než implementace sériového portu. V zobrazení vláken se nezobrazuje paralelní spuštění více vláken; místo toho vidíte, že pouze jedno vlákno je prováděno v jednom okamžiku. Pokud v tomto okamžiku kliknete na segment synchronizace ve vlákně, můžete zobrazit zásobník volání pro blokované vlákno (blokující zásobník volání) a vlákno, které odebralo podmínku blokování (odblokování zásobníku volání). Kromě toho, pokud dojde k odblokování zásobníku volání v procesu, který analyzujete, je zobrazen konektor připravený pro vlákno. Od tohoto okamžiku můžete přejít k vašemu kódu z zásobníků volání blokující a odblokovat, aby bylo možné zjistit příčinu serializace ještě více.  
  
 Jak je znázorněno na následujícím obrázku, Vizualizér souběžnosti může tento příznak zobrazit také v zobrazení využití procesoru, kde navzdory přítomnosti více vláken aplikace spotřebovává pouze jeden logický jádro.  
  
 Další informace najdete v tématu "vzor výkonu 1: identifikace kolizí zámků" v blogu Hazim Shafi [Parallel Performance Tools for Windows](https://docs.microsoft.com/archive/blogs/hshafi/) na webu blogu MSDN.  
  
 ![Uzamknout spory](../profiling/media/lockcontention-2.png "LockContention_2")  
  
## <a name="uneven-workload-distribution"></a>Nerovnoměrné rozdělení úloh  
 ![Nerovnoměrné zatížení](../profiling/media/unevenworkload-1.png "UnevenWorkLoad_1")  
  
 Pokud dojde k nepravidelné distribuci práce napříč několika paralelními vlákny v aplikaci, typický vzor schodišťového kroku se zobrazí jako každé vlákno dokončí svou práci, jak je znázorněno na předchozím obrázku. Vizualizátor souběžnosti nejčastěji zobrazuje dobu ukončení u každého souběžného vlákna. Nicméně tato vlákna obvykle končí neoprávněným způsobem místo toho, aby bylo souběžně ukončeno. Tento model označuje nepravidelnou distribuci práce mezi skupinou paralelních vláken, což může vést ke snížení výkonu. Nejlepším způsobem, jak tento problém vyřešit, je znovu vyhodnotit algoritmus, podle kterého byla práce rozdělena mezi paralelní vlákna.  
  
 Jak je znázorněno na následujícím obrázku, Vizualizér souběžnosti může tento příznak také vystavit v zobrazení využití procesoru jako postupný krok v využití procesoru.  
  
 ![Nerovnoměrné zatížení](../profiling/media/unevenworkload-2.png "UnevenWorkload_2")  
  
## <a name="oversubscription"></a>Kompenzace  
 ![Kompenzace](../profiling/media/oversubscription.png "Kompenzace")  
  
 V případě nadvýšení předplatného je počet aktivních vláken v procesu větší než počet dostupných logických jader v systému. Na předchozím obrázku vidíte výsledky předaného předplatného s významným pásmem přerušení ve všech aktivních vláknech. Kromě toho legenda zobrazuje velké procento času stráveného přerušením (84 procent v tomto příkladu). To může znamenat, že proces žádá systém, aby provedl více souběžných vláken, než je počet logických jader. To však může také znamenat, že jiné procesy v systému používají prostředky, které byly k dispozici pro tento proces.  
  
 Při vyhodnocování tohoto problému byste měli vzít v úvahu následující skutečnosti:  
  
- Celkový systém může být přehlášený za předplacený. Vezměte v úvahu, že další procesy v systému mohou přerušování vašich vláken. Když pozastavíte převzetí na segment přerušení v zobrazení vláken, ovládací prvek bude identifikovat vlákno a proces, který zrušil vlákno. Tento proces nemusí nutně být ten, který se provedl během celého procesu, který byl zrušen, ale poskytuje nápovědu k tomu, jak vzdálení způsobilo protitlak proti vašemu procesu.  
  
- Vyhodnoťte způsob, jakým proces určí příslušný počet vláken pro spuštění během této fáze práce. Pokud váš proces přímo vypočítá počet aktivních paralelních vláken, zvažte úpravu tohoto algoritmu, aby lépe zohlednil počet dostupných logických jader v systému. Použijete-li Concurrency Runtime, Task Parallel Library nebo PLINQ, tato knihovna provede práci výpočtu počtu vláken.  
  
## <a name="inefficient-io"></a>Neefektivní vstupně-výstupní operace  
 ![Neefektivní I&#47;O](../profiling/media/inefficient-io.png "Inefficient_IO")  
  
 Vyvýšení nebo zneužití vstupně-výstupních operací je běžné příčinou neefektivity v aplikacích. Vezměte v úvahu předchozí obrázek. Profil viditelné časové osy ukazuje, že v/v se spotřebuje 42 procent viditelného času vlákna. Časová osa zobrazuje velké objemy vstupně-výstupních operací, což znamená, že profilovaná aplikace je často blokovaná pomocí vstupně-výstupních operací. Chcete-li zobrazit podrobnosti o druzích vstupně-výstupních operací a o tom, kde je program zablokován, přihlaste se k problematickým oblastem, Prohlédněte si profil viditelné časové osy a kliknutím na konkrétní vstupně-výstupní blok zobrazte aktuální zásobníky volání.  
  
## <a name="lock-convoys"></a>Zamknout convoys  
 ![Zamknout convoys](../profiling/media/lock-convoys.png "Lock_Convoys")  
  
 K uzamčení convoys dojde v případě, že aplikace získá zámky v rámci prvního přihlášeného, prvního dodávaného pořadí a když je míra doručení na zámek vyšší než sazba pořízení. Kombinace těchto dvou podmínek způsobí, že požadavky na zámek zahájí zálohování. Jedním ze způsobů, jak tento problém vyřešit, je použití "nenekalých" zámků, nebo zámků, které poskytují přístup k prvnímu vláknu, aby je bylo možné v odemčených stavech. Předchozí obrázek znázorňuje toto chování convoy. Chcete-li tento problém vyřešit, zkuste snížit kolizí pro synchronizační objekty a zkuste použít nekalé zámky.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení vláken](../profiling/threads-view-parallel-performance.md)
