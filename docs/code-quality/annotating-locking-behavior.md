---
title: Zadávání poznámek o chování při zamykání
ms.date: 11/04/2016
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
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 26c788319331d0da4024844b50b4c495ed2c3a37
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806764"
---
# <a name="annotating-locking-behavior"></a>Zadávání poznámek o chování při zamykání
Aby nedocházelo k chybám souběžnosti v programu s více vlákny, vždy postupujte podle příslušného pravidla uzamykání a použijte poznámky SAL.

Chyby souběžnosti jsou obvykle odlaďujeelné k reprodukování, diagnostice a ladění, protože nejsou deterministické. Rozhodnutí o proplutí vlákna je obtížné, a Pokud navrhujete tělo kódu, který má více než několik vláken, je nepraktické. Proto je dobrým zvykem sledovat v aplikacích s více vlákny blokovací obor. Například nastavování pořadí zámků a získání více zámků pomáhá zabránit zablokování a získání správného zámku ochrany před přístupem ke sdílenému prostředku pomáhá zabránit konfliktům časování.

Zdánlivě jednoduchá pravidla zamykání ale můžou být v praxi překvapivěá. Základní omezení dnešních programovacích jazyků a kompilátorů je, že nepodporují přímo specifikace a analýzu požadavků na souběžnost. Programátoři musí spoléhat na neformální komentáře kódu, aby vyjádřili své záměry o používání zámků.

Anotace SAL pro souběžnost jsou navržené tak, aby vám pomohly určit uzamčené vedlejší účinky, odpovědnost za uzamykání, strážci dat, hierarchii pořadí zámků a další očekávané chování při zamykání. V případě explicitních implicitních pravidel jsou anotace souběžnosti SAL zajištěny konzistentní způsob, jak váš kód používá pravidla uzamykání. Anotace souběžnosti také zlepšují schopnost nástrojů pro analýzu kódu najít konflikty časování, zablokování, neshodné operace synchronizace a další drobné chyby souběžnosti.

## <a name="general-guidelines"></a>Obecné pokyny
Pomocí poznámek můžete uvést smlouvy, které jsou vyvolány definicemi funkcí mezi implementacemi (volané) a klienty (volajícími) a expresními variantami a dalšími vlastnostmi programu, které mohou dále vylepšit analýzu.

SAL podporuje mnoho různých druhů uzamykání primitiv – například důležité oddíly, mutexy, zámky a další objekty prostředků. Mnoho anotací souběžnosti přijímá výraz zámku jako parametr. Podle konvence je zámek označen výrazem cesty podkladového objektu zámku.

Některá pravidla vlastnictví vláken, která si zapamatujte:

- Zámky jsou nespočítatelné zámky, které mají jasné vlastnictví vlákna.

- Odblokování a kritické oddíly jsou započítány zámky, které mají jasné vlastnictví vlákna.

- Semafory a události jsou započítány zámky, které nemají jasné vlastnictví vlákna.

## <a name="locking-annotations"></a>Uzamčené poznámky
V následující tabulce jsou uvedeny anotace zamykání.

|Poznámka|Popis|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Přidá do funkce poznámku a určí, že ve stavu post se funkce zvýší o jeden a exkluzivní počet zámků objektu zámku, který je pojmenován `expr`.|
|`_Acquires_lock_(expr)`|Přidá do funkce poznámku a určí, že ve stavu post funkce se zvýší o jeden počet zámků objektu zámku, který je pojmenován `expr`.|
|`_Acquires_nonreentrant_lock_(expr)`|Získá se zámek s názvem `expr`.  Pokud je zámek již uložen, je hlášena chyba.|
|`_Acquires_shared_lock_(expr)`|Přidá do funkce poznámku a určí, že ve stavu post se funkce zvýší o jeden sdílený počet zámků objektu zámku, který je pojmenován `expr`.|
|`_Create_lock_level_(name)`|Příkaz, který deklaruje symbol `name` jako úroveň zámku, aby mohl být použit v poznámkách `_Has_Lock_level_` a `_Lock_level_order_`.|
|`_Has_lock_kind_(kind)`|Připíše libovolný objekt k upřesnění informací o typu objektu prostředku. Někdy se používá společný typ pro různé druhy prostředků a přetížený typ není dostačující pro odlišení sémantických požadavků mezi různými prostředky. Tady je seznam předdefinovaných parametrů `kind`:<br /><br /> `_Lock_kind_mutex_`<br /> ID typu zámku pro mutexy<br /><br /> `_Lock_kind_event_`<br /> ID typu zámku pro události<br /><br /> `_Lock_kind_semaphore_`<br /> ID typu zámku pro semafory.<br /><br /> `_Lock_kind_spin_lock_`<br /> ID typu zámku pro zámky<br /><br /> `_Lock_kind_critical_section_`<br /> ID typu zámku pro kritické oddíly|
|`_Has_lock_level_(name)`|Přikáže uzamčenému objektu a nastaví úroveň zámku `name`.|
|`_Lock_level_order_(name1, name2)`|Příkaz, který poskytuje řazení zámku mezi `name1` a `name2`.|
|`_Post_same_lock_(expr1, expr2)`|Označí funkci jako poznámku a určí, že ve stavu post budou dvě zámky `expr1` a `expr2` považovány za, jako by se jednalo o stejný objekt zámku.|
|`_Releases_exclusive_lock_(expr)`|Doplní funkci a určí, že ve stavu post je funkce snížena o jeden a exkluzivní počet zámků objektu zámku, který je pojmenován `expr`.|
|`_Releases_lock_(expr)`|Doplní funkci a určí, že ve stavu post je funkce snížena o jeden počet zámků objektu zámku, který je pojmenován `expr`.|
|`_Releases_nonreentrant_lock_(expr)`|Zámek s názvem `expr` je uvolněn. Pokud zámek momentálně není držen, je hlášena chyba.|
|`_Releases_shared_lock_(expr)`|Označí funkci jako poznámku a určí, že ve stavu post je funkce snížena o jeden sdílený počet zámků objektu zámku, který je pojmenován `expr`.|
|`_Requires_lock_held_(expr)`|Doplní funkci a určí, že v předběžném stavu je počet zámků objektu s názvem `expr` aspoň jeden.|
|`_Requires_lock_not_held_(expr)`|Označí funkci jako poznámku a určí, že v předběžném stavu je počet zámků objektu, který je pojmenován `expr`, nula.|
|`_Requires_no_locks_held_`|Označí funkci jako poznámku a indikuje, že počet zámků všech zámků, které jsou pro tuto kontrolu známy, je nula.|
|`_Requires_shared_lock_held_(expr)`|Označí funkci jako poznámku a určí, že v předběžném stavu je sdílený počet zámků objektu s názvem `expr` aspoň jeden.|
|`_Requires_exclusive_lock_held_(expr)`|Doplní funkci a určí, že v předběžném stavu má výhradní zámek objektu s názvem `expr` aspoň jeden.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Vnitřní prvky SAL pro neexponované uzamčené objekty
Některé objekty zámku nejsou zpřístupněny implementací přidružených funkcí zamykání.  V následující tabulce jsou uvedeny vnitřní proměnné SAL, které umožňují poznámky k funkcím, které pracují s těmito nevystavenými objekty zámku.

|Poznámka|Popis|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|Popisuje uzamčení číselníku zrušit.|
|`_Global_critical_region_`|Popisuje kritickou oblast.|
|`_Global_interlock_`|Popisuje propojené operace.|
|`_Global_priority_region_`|Popisuje oblast priority.|

## <a name="shared-data-access-annotations"></a>Sdílené poznámky k přístupu ke sdíleným datům
V následující tabulce jsou uvedeny poznámky pro přístup ke sdíleným datům.

|Poznámka|Popis|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Označí proměnnou jako poznámku a určí, že pokaždé, když je k proměnné přistupovat, je počet zámků objektu zámku, který je pojmenován `expr`, aspoň jeden.|
|`_Interlocked_`|Označí proměnnou jako poznámku a je ekvivalentní `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|Parametr funkce s poznámkou je cílovým operandem jedné z různých vzájemně propojených funkcí.  Tyto operandy musí mít konkrétní další vlastnosti.|
|`_Write_guarded_by_(expr)`|Označí proměnnou jako poznámku a určí, že pokaždé, když je upravena proměnná, je počet zámků objektu zámku, který je pojmenován `expr`, aspoň jeden.|

## <a name="smart-lock-and-raii-annotations"></a>Poznámky Smart Lock a RAII
Inteligentní Zámky obvykle zabalí Nativní zámky a spravují jejich životnost. V následující tabulce jsou uvedeny poznámky, které lze použít s inteligentními zámky a vzory kódování RAII s podporou sémantiky `move`.

|Poznámka|Popis|
|----------------|-----------------|
|`_Analysis_assume_smart_lock_acquired_`|Dává analyzátoru pokyn, aby předpokládal, že byl získán inteligentní zámek. Tato poznámka očekává jako svůj parametr typ zámku odkazu.|
|`_Analysis_assume_smart_lock_released_`|Dává analyzátoru pokyn, aby předpokládal, že byl vydán inteligentní zámek. Tato poznámka očekává jako svůj parametr typ zámku odkazu.|
|`_Moves_lock_(target, source)`|Popisuje operaci `move constructor`, která přenáší stav zámku z objektu `source` do `target`. `target` se považuje za nově vytvořený objekt, takže všechny stavy, které dříve existovaly, jsou ztraceny a nahrazeny stavem `source`. `source` se také resetuje na čistý stav bez počtu zámků nebo cíle aliasu, ale aliasy ukazující na něj zůstanou beze změny.|
|`_Replaces_lock_(target, source)`|Popisuje sémantiku `move assignment operator`, kde je cílový zámek vydán před přenosem stavu ze zdroje. To lze považovat za kombinaci `_Moves_lock_(target, source)` předchází `_Releases_lock_(target)`.|
|`_Swaps_locks_(left, right)`|Popisuje standardní `swap` chování, které předpokládá, že objekty `left` a `right` vyměňují svůj stav. Výměna stavu zahrnuje počet zámků a cíl aliasů, pokud je k dispozici. Aliasy, které ukazují na `left` a objekty `right` zůstávají beze změny.|
|`_Detaches_lock_(detached, lock)`|Popisuje scénář, ve kterém typ zámku obálky umožňuje zrušení bylo s jeho obsaženým prostředkem. To se podobá tomu, jak `std::unique_ptr` pracuje s vnitřním ukazatelem: umožňuje programátorům extrahovat ukazatel a opustit jeho kontejner inteligentního ukazatele v čistém stavu. Podobná logika je podporována nástrojem `std::unique_lock` a lze ji implementovat ve vlastních obálkách zámku. Odpojený zámek si zachová svůj stav (počet zámků a cíl aliasů), zatímco obálka je resetována tak, aby obsahovala nulový počet zámků a žádný cíl pro vytváření aliasů a současně si zachovává vlastní aliasy. Neexistují žádné operace na počtu zámků (uvolnění a získání). Tato poznámka se chová stejně jako `_Moves_lock_` s tím rozdílem, že odpojený argument by měl být `return` spíše než `this`.|

## <a name="see-also"></a>Viz také:

- [Použití poznámek SAL k snížení míry výskytu závad kódu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Porozumění SAL](../code-quality/understanding-sal.md)
- [Zadávání poznámek k parametrům funkcí a návratovým hodnotám](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zadávání poznámek k chování funkcí](../code-quality/annotating-function-behavior.md)
- [Zadávání poznámek ke strukturám a třídám](../code-quality/annotating-structs-and-classes.md)
- [Určení, kdy a kde se má poznámka použít](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Vnitřní funkce](../code-quality/intrinsic-functions.md)
- [Doporučené postupy a příklady](../code-quality/best-practices-and-examples-sal.md)
- [Blog týmu analýzy kódu](https://blogs.msdn.microsoft.com/codeanalysis/)
