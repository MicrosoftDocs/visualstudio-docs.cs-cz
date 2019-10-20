---
title: Sada pravidel Nativní minimální pravidla
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc7888a49f5bc7896f5f3cd568b1062e9b9a0379
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649174"
---
# <a name="native-minimum-rules-rule-set"></a>Sada pravidel Nativní minimální pravidla

Nativní minimální pravidla společnosti Microsoft se zaměřují na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a chyb aplikací.

Zahrňte tuto sadu pravidel v jakékoli vlastní sadě pravidel, kterou vytvoříte pro nativní projekty.

|Pravidlo|Popis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Použití neinicializované paměti|
|[C6011](../code-quality/c6011.md)|Přesměrování ukazatele null|
|[C6029](../code-quality/c6029.md)|Použití nezkontrolované hodnoty|
|[C6053](../code-quality/c6053.md)|Nula ukončení volání|
|[C6059](../code-quality/c6059.md)|Chybné zřetězení|
|[C6063](../code-quality/c6063.md)|Chybí argument řetězce pro formátování funkce|
|[C6064](../code-quality/c6064.md)|Chybějící argument typu Integer pro formátování funkce|
|[C6066](../code-quality/c6066.md)|Chybí argument ukazatele pro formátování funkce|
|[C6067](../code-quality/c6067.md)|Chybí argument ukazatele řetězce pro formátování funkce|
|[C6101](../code-quality/c6101.md)|Vracení neinicializované paměti|
|[C6200](../code-quality/c6200.md)|Index překračuje maximum vyrovnávací paměti.|
|[C6201](../code-quality/c6201.md)|Index překračuje maximum vyrovnávací paměti zásobníku.|
|[C6270](../code-quality/c6270.md)|Chybí argument typu float pro formátování funkce|
|[C6271](../code-quality/c6271.md)|Nadbytečný argument pro formátování funkce|
|[C6272](../code-quality/c6272.md)|Argument jiného než typu float pro formátování funkce|
|[C6273](../code-quality/c6273.md)|Argument jiného než typu Integer pro formátování funkce|
|[C6274](../code-quality/c6274.md)|Argument bez znaku pro formátování funkce|
|[C6276](../code-quality/c6276.md)|Neplatné přetypování řetězce|
|[C6277](../code-quality/c6277.md)|Neplatné volání funkce CreateProcess|
|[C6284](../code-quality/c6284.md)|Neplatný argument objektu pro formátování funkce|
|[C6290](../code-quality/c6290.md)|Logický operátor NOT a Priorita|
|[C6291](../code-quality/c6291.md)|Logický operátor NOT ani Priorita|
|[C6302](../code-quality/c6302.md)|Neplatný argument řetězce znaků pro formátování funkce|
|[C6303](../code-quality/c6303.md)|Neplatný argument řetězce s velkým znakem pro formátování funkce|
|[C6305](../code-quality/c6305.md)|Neshoda s použitím velikosti a počtu|
|[C6306](../code-quality/c6306.md)|Nesprávné volání funkce argumentu proměnné|
|[C6328](../code-quality/c6328.md)|Potenciální Neshoda typu argumentu|
|[C6385](../code-quality/c6385.md)|Přetečení čtení|
|[C6386](../code-quality/c6386.md)|Přetečení zápisu|
|[C6387](../code-quality/c6387.md)|Neplatná hodnota parametru|
|[C6500](../code-quality/c6500.md)|Neplatná vlastnost atributu|
|[C6501](../code-quality/c6501.md)|Konfliktní hodnoty vlastností atributu|
|[C6503](../code-quality/c6503.md)|Odkazy nemohou mít hodnotu null.|
|[C6504](../code-quality/c6504.md)|Null na bez ukazatele|
|[C6505](../code-quality/c6505.md)|Vlastnost mustcheck na void|
|[C6506](../code-quality/c6506.md)|Velikost vyrovnávací paměti na neukazateli nebo poli|
|[C6508](../code-quality/c6508.md)|Přístup pro zápis na konstantě|
|[C6509](../code-quality/c6509.md)|Vrácení se používá v předběžné podmínce.|
|[C6510](../code-quality/c6510.md)|Hodnota null byla ukončena na neukazateli.|
|[C6511](../code-quality/c6511.md)|Vlastnost mustcheck musí být Ano nebo ne.|
|[C6513](../code-quality/c6513.md)|Velikost prvku bez velikosti vyrovnávací paměti|
|[C6514](../code-quality/c6514.md)|Velikost vyrovnávací paměti překračuje velikost pole.|
|[C6515](../code-quality/c6515.md)|Velikost vyrovnávací paměti na bez ukazatele|
|[C6516](../code-quality/c6516.md)|Atribut nemá žádné vlastnosti.|
|[C6517](../code-quality/c6517.md)|Platná velikost pro vyrovnávací paměť, která není čitelná|
|[C6518](../code-quality/c6518.md)|Zapisovatelná velikost pro vyrovnávací paměť, která není zapisovatelná|
|[C6522](../code-quality/c6522.md)|Neplatný typ řetězce velikosti|
|[C6525](../code-quality/c6525.md)|Neplatná velikost řetězce nedosažitelného umístění|
|[C6527](../code-quality/c6527.md)|Neplatná Anotace: vlastnost NeedsRelease se nedá použít u hodnot typu void.|
|[C6530](../code-quality/c6530.md)|Nerozpoznaný styl řetězce formátu|
|[C6540](../code-quality/c6540.md)|Použití poznámek k atributům u této funkce zruší platnost všech existujících poznámek __declspec.|
|[C6551](../code-quality/c6551.md)|Neplatná specifikace velikosti: výraz nejde analyzovat.|
|[C6552](../code-quality/c6552.md)|Neplatný DEREF = nebo Notref =: výraz nelze analyzovat|
|[C6701](../code-quality/c6701.md)|Hodnota není platná hodnota Ano/Ne/možná.|
|[C6702](../code-quality/c6702.md)|Hodnota není řetězcová hodnota.|
|[C6703](../code-quality/c6703.md)|Hodnota není číslo.|
|[C6704](../code-quality/c6704.md)|Neočekávaná chyba výrazu poznámky|
|[C6705](../code-quality/c6705.md)|Očekávaný počet argumentů pro anotaci neodpovídá skutečnému počtu argumentů pro poznámku.|
|[C6706](../code-quality/c6706.md)|Neočekávaná chyba poznámky u poznámky|
|[C26450](../code-quality/c26450.md)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](../code-quality/c26451.md)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](../code-quality/c26452.md)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](../code-quality/c26453.md)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](../code-quality/c26454.md)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](../code-quality/c26495.md)|MEMBER_UNINIT|
|[C28021](../code-quality/c28021.md)|Parametr, který se dá opatřit poznámkami, musí být ukazatelem.|
|[C28182](../code-quality/c28182.md)|Přesměrování ukazatele s hodnotou NULL. Ukazatel obsahuje stejnou hodnotu NULL jako jiný ukazatel.|
|[C28202](../code-quality/c28202.md)|Neplatný odkaz na nestatický člen|
|[C28203](../code-quality/c28203.md)|Nejednoznačný odkaz na člena třídy.|
|[C28205](../code-quality/c28205.md)|\_Success \_ nebo \_On \_failure \_ použito v neplatném kontextu|
|[C28206](../code-quality/c28206.md)|Levý operand ukazuje na strukturu, použijte '-> '|
|[C28207](../code-quality/c28207.md)|Levý operand je struktura, použijte '. '|
|[C28210](../code-quality/c28210.md)|Poznámky pro kontext __on_failure nesmí být v explicitním předběžném kontextu.|
|[C28211](../code-quality/c28211.md)|Pro SAL_context se očekává název statického kontextu.|
|[C28212](../code-quality/c28212.md)|U poznámky se očekává výraz ukazatele.|
|[C28213](../code-quality/c28213.md)|@No__t_0Use \_decl \_annotations \_ anotace musí být použita k odkazování na předchozí deklaraci beze změny.|
|[C28214](../code-quality/c28214.md)|Názvy parametrů atributu musí být P1... P9|
|[C28215](../code-quality/c28215.md)|Typefix nelze použít na parametr, který již má typefix|
|[C28216](../code-quality/c28216.md)|Anotace Poznámka checkreturn se vztahuje pouze na následné podmínky pro konkrétní parametr funkce.|
|[C28217](../code-quality/c28217.md)|Pro funkci se počet parametrů poznámky neshoduje s počtem nalezeným v souboru.|
|[C28218](../code-quality/c28218.md)|Parametr poznámky pro parametr funkce se neshoduje s parametrem nalezeným v souboru.|
|[C28219](../code-quality/c28219.md)|Pro anotaci parametru v poznámce je očekáván člen výčtu.|
|[C28220](../code-quality/c28220.md)|Pro anotaci parametru v poznámce je očekáván celočíselný výraz.|
|[C28221](../code-quality/c28221.md)|Pro parametr v poznámce je očekáván řetězcový výraz.|
|[C28222](../code-quality/c28222.md)|pro anotaci se očekává __yes, \__no nebo \__maybe.|
|[C28223](../code-quality/c28223.md)|Nebyl nalezen očekávaný token/identifikátor pro anotaci, parametr|
|[C28224](../code-quality/c28224.md)|Poznámka vyžaduje parametry.|
|[C28225](../code-quality/c28225.md)|Nebyl nalezen správný počet požadovaných parametrů v poznámce|
|[C28226](../code-quality/c28226.md)|Anotace nemůže být také PrimOp (v aktuální deklaraci)|
|[C28227](../code-quality/c28227.md)|Anotace nemůže být také PrimOp (viz předchozí deklarace)|
|[C28228](../code-quality/c28228.md)|Parametr Anotace: v poznámkách nelze použít typ.|
|[C28229](../code-quality/c28229.md)|Poznámka nepodporuje parametry|
|[C28230](../code-quality/c28230.md)|Typ parametru nemá žádného člena.|
|[C28231](../code-quality/c28231.md)|Anotace je platná pouze pro pole.|
|[C28232](../code-quality/c28232.md)|předplatná, post nebo DEREF nejsou aplikovány na žádnou poznámku.|
|[C28233](../code-quality/c28233.md)|použití pre, post nebo DEREF pro blok|
|[C28234](../code-quality/c28234.md)|výraz __at se nedá použít u aktuální funkce.|
|[C28235](../code-quality/c28235.md)|Funkce nemůže být samostatná jako anotace.|
|[C28236](../code-quality/c28236.md)|Anotaci nelze použít ve výrazu.|
|[C28237](../code-quality/c28237.md)|Poznámka k parametru už není podporovaná.|
|[C28238](../code-quality/c28238.md)|Poznámka u parametru má více než jednu hodnotu, stringValue a longValue. Použít paramn = XXX|
|[C28239](../code-quality/c28239.md)|Poznámka u parametru má hodnotu, stringValue nebo longValue; a paramn = xxx. Použít pouze paramn = XXX|
|[C28240](../code-quality/c28240.md)|Poznámka u parametru má param2, ale ne param1.|
|[C28241](../code-quality/c28241.md)|Poznámka pro funkci v parametru nebyla rozpoznána.|
|[C28243](../code-quality/c28243.md)|Poznámka pro funkci v parametru vyžaduje více odkazů, než je skutečný typ s poznámkami. umožňuje|
|[C28245](../code-quality/c28245.md)|Poznámka pro funkci přihlásí this na funkci bez členu.|
|[C28246](../code-quality/c28246.md)|Anotace parametru pro funkci se neshoduje s typem parametru.|
|[C28250](../code-quality/c28250.md)|Nekonzistentní Poznámka pro funkci: předchozí instance obsahuje chybu.|
|[C28251](../code-quality/c28251.md)|Nekonzistentní Poznámka pro funkci: Tato instance obsahuje chybu.|
|[C28252](../code-quality/c28252.md)|Nekonzistentní Poznámka pro funkci: parametr má v této instanci jiné anotace.|
|[C28253](../code-quality/c28253.md)|Nekonzistentní Poznámka pro funkci: parametr má v této instanci jiné anotace.|
|[C28254](../code-quality/c28254.md)|dynamic_cast < > () se v poznámkách nepodporuje.|
|[C28262](../code-quality/c28262.md)|Chyba syntaxe v poznámce byla nalezena ve funkci pro poznámku|
|[C28263](../code-quality/c28263.md)|Našla se chyba syntaxe v podmíněné poznámce pro vnitřní anotaci.|
|[C28267](../code-quality/c28267.md)|Ve funkci byla nalezena Poznámka s chybou syntaxe v poznámkách.|
|[C28272](../code-quality/c28272.md)|Poznámka pro funkci, parametr při zkoumání je nekonzistentní s deklarací funkce|
|[C28273](../code-quality/c28273.md)|V případě funkcí jsou změny nekonzistentní s deklarací funkce|
|[C28275](../code-quality/c28275.md)|Parametr pro \_Macro \_value \_ má hodnotu null.|
|[C28279](../code-quality/c28279.md)|Pro symbol byl nalezen prvek Begin bez odpovídajícího příkazu end.|
|[C28280](../code-quality/c28280.md)|Pro symbol byl nalezen znak end bez odpovídajícího prvku Begin.|
|[C28282](../code-quality/c28282.md)|Řetězce formátu musí být v předběžných podmínkách.|
|[C28285](../code-quality/c28285.md)|Pro funkci, Chyba syntaxe v parametru|
|[C28286](../code-quality/c28286.md)|Pro funkci se chyba syntaxe blíží konci.|
|[C28287](../code-quality/c28287.md)|Pro funkci, Chyba syntaxe v \_At anotace \_ () (nerozpoznaný název parametru)|
|[C28288](../code-quality/c28288.md)|Pro funkci, Chyba syntaxe v \_At anotace \_ () (neplatný název parametru)|
|[C28289](../code-quality/c28289.md)|Funkce: ReadableTo nebo Writableto nebyl neobsahovala omezení-spec jako parametr.|
|[C28290](../code-quality/c28290.md)|Anotace for Function obsahuje více externích typů, než je skutečný počet parametrů.|
|[C28291](../code-quality/c28291.md)|Hodnota post null/NotNull na DEREF Level 0 nemá význam pro funkci.|
|[C28300](../code-quality/c28300.md)|Operandy výrazu nekompatibilních typů pro operátor|
|[C28301](../code-quality/c28301.md)|Žádné poznámky pro první deklaraci funkce|
|[C28302](../code-quality/c28302.md)|V poznámce byl nalezen operátor nadbytečné \_Deref \_.|
|[C28303](../code-quality/c28303.md)|V poznámce byl nalezen nejednoznačný \_Deref operátor \_.|
|[C28304](../code-quality/c28304.md)|Byl nalezen nesprávně umístěný \_Notref operátor \_ použit na token.|
|[C28305](../code-quality/c28305.md)|Zjistila se chyba při analýze tokenu.|
|[C28350](../code-quality/c28350.md)|Poznámka popisuje situaci, která není podmíněně platná.|
|[C28351](../code-quality/c28351.md)|Poznámka popisuje, kde v podmínce nelze použít dynamickou hodnotu (proměnnou).|
