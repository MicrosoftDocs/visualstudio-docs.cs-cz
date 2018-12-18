---
title: Zadávání poznámek o chování při zamykání
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 21c67bb8b99c2772e107ded9063a99940a7fac74
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901525"
---
# <a name="annotating-locking-behavior"></a>Zadávání poznámek o chování při zamykání
Abyste se vyhnuli souběžnosti chyby v programu s více vlákny, vždy postupujte podle příslušné uzamčení oboru a použití poznámek SAL.

 Chyby souběžnosti jsou často pevný reprodukujte, diagnostikovat a ladit, protože jsou není deterministický. Reasoning o prokládání přístup z více vláken v nejlepší je obtížné a bude nepraktické při návrhu text kódu, který má víc než několik vláken. Proto je vhodné postupovat podle uzamčení disciplíně v vaše programy s více vlákny. Například obeying zámku pořadí při získávání několika zámky pomáhá vyhýbat se blokování a získávání správné guarding zámku před přístupem k sdílený prostředek zabráníte časování.

 Bohužel zdánlivě jednoduché uzamčení pravidla mohou být překvapivě pevný použít postup popsaný v praxi. Základní omezení v dnešních programovací jazyky a kompilátory je, že nepodporují přímo specifikace a analýzu požadavky na souběžnost. Programátory muset spoléhat na komentáře neformální kódu k jejich záměry express o způsobu použití zámky.

 Poznámky SAL souběžnosti jsou navrženy pro vám pomohou stanovit uzamčení vedlejší účinky, uzamčení odpovědnost, data opatrovníka, uzamčení pořadí hierarchie a další očekávané chování při zamykání. Tím, že implicitní pravidla explicitní, zadejte poznámek SAL souběžnosti stálý dokumentů, jak váš kód používá uzamčení pravidla. Poznámky souběžnosti také zvýšit schopnost nástrojů pro analýzu kódu najít časování, zablokování, operace neodpovídající synchronizace a dalších chyb jemně souběžnosti.

## <a name="general-guidelines"></a>Obecné pokyny
 Pomocí poznámky, můžete stav smlouvy, které jsou implicitní podle definice funkcí mezi implementací (volané) a klienti (volající) a express výstupních podmínek a dalších vlastností program, který lze zlepšit analysis.

 SAL podporuje mnoho různých druhů uzamčení primitiv – například kritické oddíly, mutex – třídy, typu číselník zámků a jiných objektů prostředků. Mnoho poznámek souběžnosti trvat výraz zámku jako parametr. Podle konvence zámek je označený jako výraz cesty podkladového objektu zámku.

 Některá pravidla vlastnictví vlákno třeba vzít v úvahu:

-   Otočení zámky nebudou uncounted zámky, které mají vlastnictví zrušte přístup z více vláken.

-   Mutex – třídy a kritické oddíly počítají zámky, které mají vlastnictví zrušte přístup z více vláken.

-   Semaforů a událostí, se počítají zámky, které nemají vlastnictví zrušte přístup z více vláken.

## <a name="locking-annotations"></a>Uzamčení poznámky
 Následující tabulka uvádí uzamčení poznámky.

|Poznámka|Popis|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Označí funkci a označuje, že v blogu stav funkce zvětší jedním výhradní zámek počet zámek objektu s názvem `expr`.|
|`_Acquires_lock_(expr)`|Označí funkci a označuje, že v blogu stav funkce zvětší jedním zámku počet zámek objektu s názvem `expr`.|
|`_Acquires_nonreentrant_lock_(expr)`|Zámek s názvem `expr` je získali.  Zobrazí se chybová zpráva, pokud je již blokován zámek.|
|`_Acquires_shared_lock_(expr)`|Označí funkci a označuje, že v blogu stav funkce zvětší jedním Sdílený zámek počet zámek objektu s názvem `expr`.|
|`_Create_lock_level_(name)`|Příkaz, který deklaruje symbol `name` jako úroveň zámku tak, aby se může použít v poznámky `_Has_Lock_level_` a `_Lock_level_order_`.|
|`_Has_lock_kind_(kind)`|Označí libovolného objektu upřesněte informací o typu objektu prostředků. Někdy se používá společný typ pro různé druhy prostředků a typ přetížené není dostatečná k rozlišení sémantického požadavky mezi různé zdroje. Tady je seznam předdefinovaných `kind` parametry:<br /><br /> `_Lock_kind_mutex_`<br /> ID typu zámku pro mutex – třídy<br /><br /> `_Lock_kind_event_`<br /> ID typu zámku pro události.<br /><br /> `_Lock_kind_semaphore_`<br /> ID typu zámku pro semaforů<br /><br /> `_Lock_kind_spin_lock_`<br /> ID typu zámku pro zámky typu číselník<br /><br /> `_Lock_kind_critical_section_`<br /> ID typu zámku pro kritické oddíly.|
|`_Has_lock_level_(name)`|Označí objekt zámku a nastaví úroveň zámku `name`.|
|`_Lock_level_order_(name1, name2)`|Příkaz, který poskytuje zámek řazení mezi `name1` a `name2`.|
|`_Post_same_lock_(expr1, expr2)`|Označí funkci a určuje, že v blogu stavu dvě zámky `expr1` a `expr2`, jsou zpracovány jako v případě, že jsou na stejný objekt zámku.|
|`_Releases_exclusive_lock_(expr)`|Označí funkci a označuje, že v blogu stavu snižuje funkce jedním výhradní zámek počet zámek objektu s názvem `expr`.|
|`_Releases_lock_(expr)`|Označí funkci a označuje, že v blogu stavu snižuje funkce jedním počet zámků zámek objektu s názvem `expr`.|
|`_Releases_nonreentrant_lock_(expr)`|Zámek s názvem `expr` vydání. Zobrazí se chybová zpráva, pokud zámek není aktuálně uchovávat.|
|`_Releases_shared_lock_(expr)`|Označí funkci a označuje, že v blogu stavu snižuje funkce jedním Sdílený zámek počet zámek objektu s názvem `expr`.|
|`_Requires_lock_held_(expr)`|Označí funkci a označuje, že v předběžné stavu počet zámek objektu s názvem `expr` alespoň jeden.|
|`_Requires_lock_not_held_(expr)`|Označí funkci a označuje, že v předběžné stavu počet zámek objektu s názvem `expr` je nulová.|
|`_Requires_no_locks_held_`|Označí funkci a udává, že zámku počty všechny zámky, které jsou známé nástroj pro kontrolu nula.|
|`_Requires_shared_lock_held_(expr)`|Označí funkci a označuje, že v předběžné stavu počet Sdílený zámek objektu s názvem `expr` alespoň jeden.|
|`_Requires_exclusive_lock_held_(expr)`|Označí funkci a označuje, že v předběžné stavu počet výhradní zámek objektu s názvem `expr` alespoň jeden.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Vnitřní funkce SAL pro objekty Nevystaveným zamykání
 Některé objekty zámku nejsou vystavené implementace přidružené uzamčení funkce.  Následující tabulka uvádí SAL vnitřní proměnné, které poznámky na funkce, které fungují u těchto objektů nevystaveným zámku.

|Poznámka|Popis|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|Popisuje uzamčení Storno.|
|`_Global_critical_region_`|Popisuje důležité oblasti.|
|`_Global_interlock_`|Popisuje propojené operace.|
|`_Global_priority_region_`|Popisuje oblasti s prioritou.|

## <a name="shared-data-access-annotations"></a>Poznámky přístup sdílených dat
 Následující tabulka uvádí poznámky pro přístup k sdíleným datům.

|Poznámka|Popis|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Označí proměnné a znamená, že vždy, když je přistupovat proměnnou, počet zámků zámek objektu s názvem `expr` alespoň jeden.|
|`_Interlocked_`|Označí proměnné a je ekvivalentní `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|Parametr s poznámkami funkce je operand target jednoho z různých funkcí Interlocked.  Tyto operandy musí mít specifické další vlastnosti.|
|`_Write_guarded_by_(expr)`|Označí proměnné a vždy, když proměnné je změněna, počet zámků zámek objektu s názvem `expr` alespoň jeden.|

## <a name="see-also"></a>Viz také
 [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [porozumění SAL](../code-quality/understanding-sal.md) [zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md) [zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md) [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md) [určující, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md) [vnitřní funkce](../code-quality/intrinsic-functions.md) [osvědčené postupy a Příklady](../code-quality/best-practices-and-examples-sal.md) [Code Analysis Blog týmu](http://go.microsoft.com/fwlink/p/?LinkId=251197)