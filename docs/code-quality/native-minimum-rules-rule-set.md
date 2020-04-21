---
title: Sada pravidel Nativní minimální pravidla
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8abf4d4c5d2158ab4a3c9deeb11ab93e31b4cc3
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649342"
---
# <a name="native-minimum-rules-rule-set"></a>Sada pravidel Nativní minimální pravidla

Nativní minimální pravidla společnosti Microsoft se zaměřují na nejdůležitější problémy v nativním kódu, včetně potenciálních bezpečnostních děr a selhání aplikací.

Tuto sadu pravidel zahrňte do libovolné vlastní sady pravidel, kterou vytvoříte pro nativní projekty.

|Pravidlo|Popis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Použití neinicializované paměti|
|[C6011](../code-quality/c6011.md)|Odkazování na nulový ukazatel|
|[C6029](../code-quality/c6029.md)|Použití nekontrolované hodnoty|
|[C6053](../code-quality/c6053.md)|Nulové ukončení z volání|
|[C6059](../code-quality/c6059.md)|Špatné zřetězení|
|[C6063](../code-quality/c6063.md)|Funkce Chybějící argument řetězec pro formátování|
|[C6064](../code-quality/c6064.md)|Chybí funkce Integer Argument To Format|
|[C6066](../code-quality/c6066.md)|Chybějící argument ukazatele na funkci Formát|
|[C6067](../code-quality/c6067.md)|Chybějící argument ukazatele řetězce na funkci Formát|
|[C6101](../code-quality/c6101.md)|Vrácení neinicializované paměti|
|[C6200](../code-quality/c6200.md)|Index překračuje maximální vyrovnávací paměť|
|[C6201](../code-quality/c6201.md)|Maximální hodnota vyrovnávací paměti zásobníku překračuje|
|[C6270](../code-quality/c6270.md)|Funkce Chybějící argument plovoucí na formát|
|[C6271](../code-quality/c6271.md)|Funkce Extra Argument to Format|
|[C6272](../code-quality/c6272.md)|Funkce Neplovoucí argument pro formát|
|[C6273](../code-quality/c6273.md)|Funkce Neceločíselný argument pro formátování|
|[C6274](../code-quality/c6274.md)|Neznakový argument pro funkci Formátování|
|[C6276](../code-quality/c6276.md)|Neplatný přetypování řetězců|
|[C6277](../code-quality/c6277.md)|Neplatné volání createprocess|
|[C6284](../code-quality/c6284.md)|Neplatný argument objektu pro funkci Formátování|
|[C6290](../code-quality/c6290.md)|Logická-ne bitová a priorita|
|[C6291](../code-quality/c6291.md)|Logická nebitová nebo priorita|
|[C6302](../code-quality/c6302.md)|Neplatný argument znakového řetězce pro funkci Formátování|
|[C6303](../code-quality/c6303.md)|Neplatný argument řetězec celého znaku pro funkci Formátování|
|[C6305](../code-quality/c6305.md)|Neodpovídající velikost a počet použití|
|[C6306](../code-quality/c6306.md)|Nesprávné volání funkce argumentu proměnné|
|[C6328](../code-quality/c6328.md)|Neshoda potenciálního typu argumentu|
|[C6385](../code-quality/c6385.md)|Čtení překročení|
|[C6386](../code-quality/c6386.md)|Přetečovat|
|[C6387](../code-quality/c6387.md)|Neplatná hodnota parametru|
|[C6500](../code-quality/c6500.md)|Neplatná vlastnost atributu|
|[C6501](../code-quality/c6501.md)|Konfliktní hodnoty vlastností atributu|
|[C6503](../code-quality/c6503.md)|Odkazy nemohou být null|
|[C6504](../code-quality/c6504.md)|Null na non-ukazatel|
|[C6505](../code-quality/c6505.md)|Musí zkontrolovat na void|
|[C6506](../code-quality/c6506.md)|Velikost vyrovnávací paměti na non-ukazatel nebo pole|
|[C6508](../code-quality/c6508.md)|Přístup pro zápis na konstantu|
|[C6509](../code-quality/c6509.md)|Vrácení použité na předpokladu|
|[C6510](../code-quality/c6510.md)|Null ukončeno na non-ukazatel|
|[C6511](../code-quality/c6511.md)|MustCheck musí být ano nebo ne.|
|[C6513](../code-quality/c6513.md)|Velikost prvku bez velikosti vyrovnávací paměti|
|[C6514](../code-quality/c6514.md)|Velikost vyrovnávací paměti překračuje velikost pole|
|[C6515](../code-quality/c6515.md)|Velikost vyrovnávací paměti na neukazateli|
|[C6516](../code-quality/c6516.md)|Na atributu nejsou žádné vlastnosti.|
|[C6517](../code-quality/c6517.md)|Platná velikost na nečitelné vyrovnávací paměti|
|[C6518](../code-quality/c6518.md)|Zapisovatelná velikost na vyrovnávací paměť, která není zapisovatelná|
|[C6522](../code-quality/c6522.md)|Neplatný typ řetězce velikosti|
|[C6525](../code-quality/c6525.md)|Neplatné umístění řetězce velikosti|
|[C6527](../code-quality/c6527.md)|Neplatná poznámka: Vlastnost NeedsRelease nesmí být použita u hodnot typu void.|
|[C6530](../code-quality/c6530.md)|Nerozpoznaný styl formátovacího řetězce|
|[C6540](../code-quality/c6540.md)|Použití atributových anotací v této funkci zruší platnost všech existujících __declspec anotací.|
|[C6551](../code-quality/c6551.md)|Specifikace neplatné velikosti: výraz není analyzovatelný|
|[C6552](../code-quality/c6552.md)|Neplatný Deref= nebo Notref=: výraz není analyzovatelný|
|[C6701](../code-quality/c6701.md)|Hodnota není platná hodnota Ano/Ne/Možná|
|[C6702](../code-quality/c6702.md)|Hodnota není řetězcová hodnota.|
|[C6703](../code-quality/c6703.md)|Hodnota není číslo|
|[C6704](../code-quality/c6704.md)|Neočekávaná chyba výrazu poznámky|
|[C6705](../code-quality/c6705.md)|Očekávaný počet argumentů pro poznámku neodpovídá skutečnému počtu argumentů pro poznámku.|
|[C6706](../code-quality/c6706.md)|Neočekávaná chyba poznámky pro poznámku|
|[C26450](../code-quality/c26450.md)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](../code-quality/c26451.md)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](../code-quality/c26452.md)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](../code-quality/c26453.md)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](../code-quality/c26454.md)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](../code-quality/c26495.md)|MEMBER_UNINIT|
|[C28021](../code-quality/c28021.md)|Parametr, který je anotován, musí být ukazatel.|
|[C28182](../code-quality/c28182.md)|Dereferencing null ukazatel. Ukazatel obsahuje stejnou hodnotu NULL jako jiný ukazatel.|
|[C28202](../code-quality/c28202.md)|Neplatný odkaz na nestatický člen|
|[C28203](../code-quality/c28203.md)|Nejednoznačný odkaz na člen třídy.|
|[C28205](../code-quality/c28205.md)|\_Úspěch\_ \_nebo\_\_ při neúspěchu použitém v nelegálním kontextu|
|[C28206](../code-quality/c28206.md)|Levý operand ukazuje na strukturu, použijte '->'|
|[C28207](../code-quality/c28207.md)|Levý operand je struktura, použijte '.'|
|[C28210](../code-quality/c28210.md)|Poznámky pro kontext __on_failure nesmí být v explicitním kontextu pre|
|[C28211](../code-quality/c28211.md)|Pro SAL_context byl očekáván statický název kontextu.|
|[C28212](../code-quality/c28212.md)|Pro poznámku byl očekáván výraz ukazatele.|
|[C28213](../code-quality/c28213.md)|\_Anotace anotace Použití\_decl\_musí být použita\_ k odkazu bez epošálu na předchozí deklaraci.|
|[C28214](../code-quality/c28214.md)|Názvy parametrů atributu musí být p1... p9|
|[C28215](../code-quality/c28215.md)|Opravu typefix nelze použít na parametr, který již má opravu typefix.|
|[C28216](../code-quality/c28216.md)|CheckReturn anotace platí pouze pro postconditions pro parametr konkrétní funkce.|
|[C28217](../code-quality/c28217.md)|U funkce se počet parametrů anotace neshoduje s parametrem nalezeným v souboru.|
|[C28218](../code-quality/c28218.md)|Parametr funkce pro parametr funkce neodpovídá parametru nalezenému v souboru|
|[C28219](../code-quality/c28219.md)|Člen výčtu očekávaný pro anotaci parametr v anotaci|
|[C28220](../code-quality/c28220.md)|Byl očekáván výraz celého čísla pro anotaci parametr v poznámkách|
|[C28221](../code-quality/c28221.md)|Pro parametr v poznámkách byl očekáván řetězcový výraz.|
|[C28222](../code-quality/c28222.md)|__yes, \__no \_nebo _maybe očekáváno pro poznámku|
|[C28223](../code-quality/c28223.md)|Nebyl anotace, parametr nebyl anotací.|
|[C28224](../code-quality/c28224.md)|Anotace vyžaduje parametry|
|[C28225](../code-quality/c28225.md)|V anotaci nebyl našel správný počet požadovaných parametrů.|
|[C28226](../code-quality/c28226.md)|Anotace nemůže být také PrimOp (v aktuální deklaraci)|
|[C28227](../code-quality/c28227.md)|Anotace nemůže být také PrimOp (viz předchozí prohlášení)|
|[C28228](../code-quality/c28228.md)|Parametr poznámky: nelze použít typ v poznámkách|
|[C28229](../code-quality/c28229.md)|Anotace nepodporuje parametry|
|[C28230](../code-quality/c28230.md)|Typ parametru nemá žádný člen.|
|[C28231](../code-quality/c28231.md)|Anotace je platná pouze v poli|
|[C28232](../code-quality/c28232.md)|před, post nebo deref, které nejsou použity na žádné poznámky|
|[C28233](../code-quality/c28233.md)|před, post nebo deref aplikované na blok|
|[C28234](../code-quality/c28234.md)|__at výraz se nevztahuje na aktuální funkci|
|[C28235](../code-quality/c28235.md)|Funkce nemůže stát samostatně jako anotace|
|[C28236](../code-quality/c28236.md)|Poznámku nelze použít ve výrazu.|
|[C28237](../code-quality/c28237.md)|Anotace na parametru již není podporována.|
|[C28238](../code-quality/c28238.md)|Anotace na parametr má více než jednu hodnotu, stringValue a longValue. Použít paramn=xxx|
|[C28239](../code-quality/c28239.md)|Anotace na parametr má hodnotu, stringValue nebo longValue; a paramn=xxx. Používejte pouze paramn=xxx|
|[C28240](../code-quality/c28240.md)|Anotace na parametru má param2, ale ne param1|
|[C28241](../code-quality/c28241.md)|Anotace funkce na parametru není rozpoznána.|
|[C28243](../code-quality/c28243.md)|Anotace funkce na parametru vyžaduje více odkazů, než skutečný typ anotovaný umožňuje|
|[C28245](../code-quality/c28245.md)|Anotace funkce anotuje "to" na non-člen-funkce|
|[C28246](../code-quality/c28246.md)|Anotace parametru pro funkci neodpovídá typu parametru.|
|[C28250](../code-quality/c28250.md)|Nekonzistentní anotace pro funkci: předchozí instance má chybu.|
|[C28251](../code-quality/c28251.md)|Nekonzistentní anotace pro funkci: tato instance má chybu.|
|[C28252](../code-quality/c28252.md)|Nekonzistentní anotace pro funkci: parametr má další poznámky v této instanci.|
|[C28253](../code-quality/c28253.md)|Nekonzistentní anotace pro funkci: parametr má další poznámky v této instanci.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>() není podporovánv poznámkách|
|[C28262](../code-quality/c28262.md)|Ve funkci byla nalezena syntaktická chyba v anotaci pro anotaci|
|[C28263](../code-quality/c28263.md)|Byla nalezena syntaktická chyba v podmíněné anotaci pro vnitřní poznámku.|
|[C28267](../code-quality/c28267.md)|Ve funkci byla nalezena syntaktická chyba v poznámkách.|
|[C28272](../code-quality/c28272.md)|Anotace pro funkci, parametr při zkoumání není konzistentní s deklarací funkce|
|[C28273](../code-quality/c28273.md)|Pro funkci jsou stopy nekonzistentní s deklarací funkce|
|[C28275](../code-quality/c28275.md)|Parametr hodnoty \_\_ \_Makra je null.|
|[C28279](../code-quality/c28279.md)|Pro symbol byl nalezen "begin" bez odpovídajícího "konce"|
|[C28280](../code-quality/c28280.md)|Pro symbol byl nalezen "konec" bez odpovídajícího "begin"|
|[C28282](../code-quality/c28282.md)|Formátovací řetězce musí být v předběžných podmínkách.|
|[C28285](../code-quality/c28285.md)|Pro funkci, syntaktická chyba v parametru|
|[C28286](../code-quality/c28286.md)|Pro funkci, syntaktická chyba blízko konce|
|[C28287](../code-quality/c28287.md)|Pro funkci, syntaktická chyba v \_at\_() anotaci (nerozpoznaný název parametru)|
|[C28288](../code-quality/c28288.md)|Pro funkci, syntaktická chyba v \_at\_() anotaci (neplatný název parametru)|
|[C28289](../code-quality/c28289.md)|Pro funkci: ReadableTo nebo WritableTo neměl limit-spec jako parametr|
|[C28290](../code-quality/c28290.md)|anotace funkce obsahuje více externích externích funkcí než skutečný počet parametrů|
|[C28291](../code-quality/c28291.md)|post null/notnull na úrovni deref 0 je pro funkci bezvýznamný.|
|[C28300](../code-quality/c28300.md)|Výraz operandy nekompatibilní typy pro operátor|
|[C28301](../code-quality/c28301.md)|Žádné poznámky pro první deklaraci funkce.|
|[C28302](../code-quality/c28302.md)|Další \_Deref\_ operátor byl nalezen na poznámky.|
|[C28303](../code-quality/c28303.md)|V \_anotaci byl nalezen nejednoznačný operátor Deref.\_|
|[C28304](../code-quality/c28304.md)|Nesprávně umístěný \_operátor\_ Notref byl nalezen použitý pro token.|
|[C28305](../code-quality/c28305.md)|Při analýzě tokenu byla zjištěna chyba.|
|[C28350](../code-quality/c28350.md)|Anotace popisuje situaci, která není podmíněně použitelná.|
|[C28351](/cpp/code-quality/c28351)|Anotace popisuje, kde dynamickou hodnotu (proměnnou) nelze použít v podmínce.|
