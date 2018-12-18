---
title: Zadávání poznámek o chování při zamykání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f09b38ceb4a6824ec38f0d9206cf37e0f056ce28
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790757"
---
# <a name="annotating-locking-behavior"></a>Zadávání poznámek o chování při zamykání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Předejdete tak chybám souběžnosti ve vašem vícevláknovém programu, vždy postupujte podle příslušné zamykání disciplína a použití anotací SAL.  
  
 Chyby souběžnosti je známo, že těžké reprodukovat, diagnostikovat a ladit, protože jsou nedeterministické. Uvažování o prokládání vlákna je obtížné nejlépe a nebude nepraktické, když navrhujete tělo kód, který má více než několik vláken. Proto je vhodné provést uzamčení disciplína ve vícevláknových aplikacích. Například obeying pořadí uzamčení při získávání několika zámky pomáhá zabránit zablokování a získávání správný zámku guarding před přístup ke sdíleným prostředkům pomáhá zabránit konfliktům časování.  
  
 Bohužel zdánlivě jednoduché zamykání pravidla může být překvapivě obtížné sledovat v praxi. Základní omezení v dnešních programovacích jazyků a kompilátory je, že nepodporují přímo specifikaci a analýzy požadavky na souběžnost. Programátoři se nemusíte spoléhat na komentáře neformální kódu k jejich záměry express o způsobu použití zámků.  
  
 Poznámky SAL souběžnosti jsou navržené tak, že vám pomůže při zadávání zamykání vedlejší účinky, blokování odpovědnosti, opatrovníka data, pořadí hierarchie zámek a jiné očekávané chování při zamykání. Tím, že implicitní pravidla explicitní, zadejte poznámky SAL souběžnosti stálý zdokumentujte, jak váš kód používá zamykání pravidla. Poznámky souběžnosti také posílit schopnost nástrojů pro analýzu kódu najít ke konfliktům časování, zablokování, neodpovídající synchronizační operace a jiné souběžnosti drobné chyby.  
  
## <a name="general-guidelines"></a>Obecné pokyny  
 Pomocí poznámek může prohlásit smluv, které jsou odvozené od definice funkcí mezi klienty (volající) a implementace (volané) a express výstupních podmínek a další vlastnosti aplikace, kterou můžete dále zlepšit analýzy.  
  
 Poznámky SAL podporuje mnoho různých typů uzamčení primitivy – například kritické oddíly, vzájemně vyloučené přístupy, otočný zámky a jiných objektů prostředků. Mnoho poznámek souběžnosti provést výraz zámku jako parametr. Podle konvence je zámek udávají výraz cesty základního objektu zámku.  
  
 Některé vlákno pravidel vlastnictví brát v úvahu:  
  
-   Číselník zámky nebudou uncounted zámky, které mají jasné vlákno vlastnictví.  
  
-   Vzájemně vyloučené přístupy a kritické oddíly se počítají zámků, které se mají vymazat vlákno vlastnictví.  
  
-   Semaforů a události se počítají zámků, které nemají vlastnictví vymazat vlákna.  
  
## <a name="locking-annotations"></a>Uzamčení poznámky  
 V následující tabulce jsou uvedeny zamykání poznámky.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Označí funkci a označuje, že v příspěvku stavu funkce zvýší o jedna výhradní zámek počet zámek objektu, který je pojmenován podle `expr`.|  
|`_Acquires_lock_(expr)`|Označí funkci a označuje, že v příspěvku stavu funkce zvýší o jednu počet zámků zámek objektu, který je pojmenován podle `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Zámek, který je pojmenován podle `expr` je požadován.  Zámek se již nachází, oznámí se chyba.|  
|`_Acquires_shared_lock_(expr)`|Označí funkci a označuje, že v příspěvku stavu funkce zvýší o jedna Sdílený zámek počet zámek objektu, který je pojmenován podle `expr`.|  
|`_Create_lock_level_(name)`|Příkaz, který deklaruje symbol `name` bude úroveň zámku, takže mohou být využity v poznámkách `_Has_Lock_level_` a `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Označí libovolný objekt, pro upřesnění informací o typu objektu prostředku. Někdy se používá společný typ pro různé druhy prostředků a přetížené typ není dostatečná k rozlišení sémantické požadavky mezi různými prostředky. Tady je seznam předem definovaných `kind` parametry:<br /><br /> `_Lock_kind_mutex_`<br /> Druh ID zámku pro vzájemně vyloučené přístupy.<br /><br /> `_Lock_kind_event_`<br /> Druh ID zámku pro události.<br /><br /> `_Lock_kind_semaphore_`<br /> Druh ID zámku pro semafory.<br /><br /> `_Lock_kind_spin_lock_`<br /> Druh ID zámku pro uzamčení typu číselník<br /><br /> `_Lock_kind_critical_section_`<br /> Druh ID zámku pro kritické oddíly.|  
|`_Has_lock_level_(name)`|Označí objekt zámku a dá jí úroveň zámku `name`.|  
|`_Lock_level_order_(name1, name2)`|Příkaz, který poskytuje zámek za výsledek řazení mezi `name1` a `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Označí funkci a označuje, že v příspěvku stavu dvě zámky `expr1` a `expr2`, zacházeno, jako by šlo stejné zámek objektu.|  
|`_Releases_exclusive_lock_(expr)`|Označí funkci a označuje, že v příspěvku stavu funkce sníží o jedna exkluzivní zámek počet zámek objektu, který je pojmenován podle `expr`.|  
|`_Releases_lock_(expr)`|Označí funkci a označuje, že v příspěvku stavu funkce sníží o jedna počet zámků zámek objektu, který je pojmenován podle `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|Zámek, který je pojmenován podle `expr` vydání. Pokud zámek není aktuálně používán, oznámí se chyba.|  
|`_Releases_shared_lock_(expr)`|Označí funkci a označuje, že v příspěvku stavu funkce sníží o jedna Sdílený zámek počet zámek objektu, který je pojmenován podle `expr`.|  
|`_Requires_lock_held_(expr)`|Označí funkci a označuje, že v předem stavu počet zámků objektu, který je pojmenován podle `expr` je alespoň jednou.|  
|`_Requires_lock_not_held_(expr)`|Označí funkci a označuje, že v předem stavu počet zámků objektu, který je pojmenován podle `expr` je nula.|  
|`_Requires_no_locks_held_`|Označí funkci a určuje, že zamykací počet všech zámků, které jsou známé nástroj pro kontrolu je nula.|  
|`_Requires_shared_lock_held_(expr)`|Označí funkci a označuje, že v předem stavu počet Sdílený zámek objektu, který je pojmenován podle `expr` je alespoň jednou.|  
|`_Requires_exclusive_lock_held_(expr)`|Označí funkci a označuje, že v předem stavu počet výhradní zámek objektu, který je pojmenován podle `expr` je alespoň jednou.|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Vnitřní objekty SAL Nevystaveným uzamčení objektů  
 Některé uzamknout objekty nejsou zveřejněné v implementaci přidružené funkce zamykání.  V následující tabulce jsou uvedeny SAL vnitřní proměnné, které umožňují poznámky o funkcích, které pracují na tyto objekty nevystaveným zámku.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|Popisuje uzamčení Storno.|  
|`_Global_critical_region_`|Popisuje důležité oblasti.|  
|`_Global_interlock_`|Popisuje propojené operace.|  
|`_Global_priority_region_`|Popisuje priority oblasti.|  
  
## <a name="shared-data-access-annotations"></a>Sdílená Data Access poznámky  
 V následující tabulce jsou uvedeny poznámky k přístupu k sdíleným datům.  
  
|Poznámka|Popis|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|Označí proměnné a označuje, že vždy, když proměnnou přistupuje, počet zámků zámek objektu, který je pojmenován podle `expr` je alespoň jednou.|  
|`_Interlocked_`|Označí proměnné a je ekvivalentní `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|Parametr s poznámkami funkce je operand target jednoho z různých funkcí Interlocked.  Těmito operandy musí mít specifické další vlastnosti.|  
|`_Write_guarded_by_(expr)`|Označí proměnné a označuje, že vždy, když je proměnná je upraveno, počet zámků zámek objektu, který je pojmenován podle `expr` je alespoň jednou.|  
  
## <a name="see-also"></a>Viz také  
 [Použití poznámek SAL k omezení defektů kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Porozumění SAL](../code-quality/understanding-sal.md)   
 [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)   
 [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)   
 [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Vnitřní funkce](../code-quality/intrinsic-functions.md)   
 [Osvědčené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)   
 [Blog týmu analýzy kódu](http://go.microsoft.com/fwlink/p/?LinkId=251197)



