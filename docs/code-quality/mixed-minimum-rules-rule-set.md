---
title: Sada pravidel Smíšená minimální pravidla
ms.date: 11/04/2016
description: Přečtěte si o sadě pravidel smíšeného minima Rules v sadě Visual Studio. Viz popisy pravidel pro projekty jazyka C++, které podporují modul CLR (Common Language Runtime).
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bb87da3cc668ba946c6ee607fa3be5a2c79cc32
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435323"
---
# <a name="mixed-minimum-rules-rule-set"></a>Sada pravidel Smíšená minimální pravidla

Minimální pravidla Microsoft Mixed se zaměřují na nejdůležitější problémy v projektech C++, které podporují modul CLR (Common Language Runtime), včetně možných bezpečnostních děr a chyb aplikací.

Zahrňte tuto sadu pravidel v jakékoli vlastní sadě pravidel, kterou vytvoříte pro projekty C++, které podporují modul CLR (Common Language Runtime).

|Pravidlo|Popis|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Použití neinicializované paměti|
|[C6011](/cpp/code-quality/c6011)|Přesměrování ukazatele null|
|[C6029](/cpp/code-quality/c6029)|Použití nezkontrolované hodnoty|
|[C6053](/cpp/code-quality/c6053)|Nula ukončení volání|
|[C6059](/cpp/code-quality/c6059)|Chybné zřetězení|
|[C6063](/cpp/code-quality/c6063)|Chybí argument řetězce pro formátování funkce|
|[C6064](/cpp/code-quality/c6064)|Chybějící argument typu Integer pro formátování funkce|
|[C6066](/cpp/code-quality/c6066)|Chybí argument ukazatele pro formátování funkce|
|[C6067](/cpp/code-quality/c6067)|Chybí argument ukazatele řetězce pro formátování funkce|
|[C6101](/cpp/code-quality/c6101)|Vracení neinicializované paměti|
|[C6200](/cpp/code-quality/c6200)|Index překračuje maximum vyrovnávací paměti.|
|[C6201](/cpp/code-quality/c6201)|Index překračuje maximum vyrovnávací paměti zásobníku.|
|[C6270](/cpp/code-quality/c6270)|Chybí argument typu float pro formátování funkce|
|[C6271](/cpp/code-quality/c6271)|Nadbytečný argument pro formátování funkce|
|[C6272](/cpp/code-quality/c6272)|Argument jiného než typu float pro formátování funkce|
|[C6273](/cpp/code-quality/c6273)|Argument jiného než typu Integer pro formátování funkce|
|[C6274](/cpp/code-quality/c6274)|Argument bez znaku pro formátování funkce|
|[C6276](/cpp/code-quality/c6276)|Neplatné přetypování řetězce|
|[C6277](/cpp/code-quality/c6277)|Neplatné volání funkce CreateProcess|
|[C6284](/cpp/code-quality/c6284)|Neplatný argument objektu pro formátování funkce|
|[C6290](/cpp/code-quality/c6290)|Logical-Not priority Bitwise-And|
|[C6291](/cpp/code-quality/c6291)|Logical-Not priority Bitwise-Or|
|[C6302](/cpp/code-quality/c6302)|Neplatný argument řetězce znaků pro formátování funkce|
|[C6303](/cpp/code-quality/c6303)|Neplatný argument řetězce s velkým znakem pro formátování funkce|
|[C6305](/cpp/code-quality/c6305)|Neshoda s použitím velikosti a počtu|
|[C6306](/cpp/code-quality/c6306)|Nesprávné volání funkce argumentu proměnné|
|[C6328](/cpp/code-quality/c6328)|Potenciální Neshoda typu argumentu|
|[C6385](/cpp/code-quality/c6385)|Přetečení čtení|
|[C6386](/cpp/code-quality/c6386)|Přetečení zápisu|
|[C6387](/cpp/code-quality/c6387)|Neplatná hodnota parametru|
|[C6500](/cpp/code-quality/c6500)|Neplatná vlastnost atributu|
|[C6501](/cpp/code-quality/c6501)|Konfliktní hodnoty vlastností atributu|
|[C6503](/cpp/code-quality/c6503)|Odkazy nemohou mít hodnotu null.|
|[C6504](/cpp/code-quality/c6504)|Null na bez ukazatele|
|[C6505](/cpp/code-quality/c6505)|Vlastnost mustcheck na void|
|[C6506](/cpp/code-quality/c6506)|Velikost vyrovnávací paměti na neukazateli nebo poli|
|[C6508](/cpp/code-quality/c6508)|Přístup pro zápis na konstantě|
|[C6509](/cpp/code-quality/c6509)|Vrácení se používá v předběžné podmínce.|
|[C6510](/cpp/code-quality/c6510)|Hodnota null byla ukončena na neukazateli.|
|[C6511](/cpp/code-quality/c6511)|Vlastnost mustcheck musí být Ano nebo ne.|
|[C6513](/cpp/code-quality/c6513)|Velikost prvku bez velikosti vyrovnávací paměti|
|[C6514](/cpp/code-quality/c6514)|Velikost vyrovnávací paměti překračuje velikost pole.|
|[C6515](/cpp/code-quality/c6515)|Velikost vyrovnávací paměti na bez ukazatele|
|[C6516](/cpp/code-quality/c6516)|Atribut nemá žádné vlastnosti.|
|[C6517](/cpp/code-quality/c6517)|Platná velikost pro vyrovnávací paměť, která není čitelná|
|[C6518](/cpp/code-quality/c6518)|Zapisovatelná velikost pro vyrovnávací paměť, která není zapisovatelná|
|[C6522](/cpp/code-quality/c6522)|Neplatný typ řetězce velikosti|
|[C6525](/cpp/code-quality/c6525)|Neplatná velikost řetězce nedosažitelného umístění|
|[C6527](/cpp/code-quality/c6527)|Neplatná Anotace: vlastnost NeedsRelease se nedá použít u hodnot typu void.|
|[C6530](/cpp/code-quality/c6530)|Nerozpoznaný styl řetězce formátu|
|[C6540](/cpp/code-quality/c6540)|Použití poznámek k atributům u této funkce zruší platnost všech existujících poznámek __declspec.|
|[C6551](/cpp/code-quality/c6551)|Neplatná specifikace velikosti: výraz nejde analyzovat.|
|[C6552](/cpp/code-quality/c6552)|Neplatný DEREF = nebo Notref =: výraz nelze analyzovat|
|[C6701](/cpp/code-quality/c6701)|Hodnota není platná hodnota Ano/Ne/možná.|
|[C6702](/cpp/code-quality/c6702)|Hodnota není řetězcová hodnota.|
|[C6703](/cpp/code-quality/c6703)|Hodnota není číslo.|
|[C6704](/cpp/code-quality/c6704)|Neočekávaná chyba výrazu poznámky|
|[C6705](/cpp/code-quality/c6705)|Očekávaný počet argumentů pro anotaci neodpovídá skutečnému počtu argumentů pro poznámku.|
|[C6706](/cpp/code-quality/c6706)|Neočekávaná chyba poznámky u poznámky|
|[C28021](/cpp/code-quality/c28021)|Parametr, který se dá opatřit poznámkami, musí být ukazatelem.|
|[C28182](/cpp/code-quality/c28182)|Přesměrování ukazatele s hodnotou NULL. Ukazatel obsahuje stejnou hodnotu NULL jako jiný ukazatel.|
|[C28202](/cpp/code-quality/c28202)|Neplatný odkaz na nestatický člen|
|[C28203](/cpp/code-quality/c28203)|Nejednoznačný odkaz na člena třídy.|
|[C28205](/cpp/code-quality/c28205)|\_Úspěch \_ nebo \_ při \_ selhání při \_ použití v neplatném kontextu|
|[C28206](/cpp/code-quality/c28206)|Levý operand ukazuje na strukturu, použijte '-> '|
|[C28207](/cpp/code-quality/c28207)|Levý operand je struktura, použijte '. '|
|[C28210](/cpp/code-quality/c28210)|Poznámky pro kontext __on_failure nesmí být v explicitním předběžném kontextu.|
|[C28211](/cpp/code-quality/c28211)|Pro SAL_context se očekává název statického kontextu.|
|[C28212](/cpp/code-quality/c28212)|U poznámky se očekává výraz ukazatele.|
|[C28213](/cpp/code-quality/c28213)|\_Poznámka k prohlášení o použití se \_ \_ \_ musí použít k odkazování na předchozí deklaraci bez úprav.|
|[C28214](/cpp/code-quality/c28214)|Názvy parametrů atributu musí být P1... P9|
|[C28215](/cpp/code-quality/c28215)|Typefix nelze použít na parametr, který již má typefix|
|[C28216](/cpp/code-quality/c28216)|Anotace Poznámka checkreturn se vztahuje pouze na následné podmínky pro konkrétní parametr funkce.|
|[C28217](/cpp/code-quality/c28217)|Pro funkci se počet parametrů poznámky neshoduje s počtem nalezeným v souboru.|
|[C28218](/cpp/code-quality/c28218)|Parametr poznámky pro parametr funkce se neshoduje s parametrem nalezeným v souboru.|
|[C28219](/cpp/code-quality/c28219)|Pro anotaci parametru v poznámce je očekáván člen výčtu.|
|[C28220](/cpp/code-quality/c28220)|Pro anotaci parametru v poznámce je očekáván celočíselný výraz.|
|[C28221](/cpp/code-quality/c28221)|Pro parametr v poznámce je očekáván řetězcový výraz.|
|[C28222](/cpp/code-quality/c28222)|\_pro anotaci se očekává __yes, _no nebo \_ _maybe.|
|[C28223](/cpp/code-quality/c28223)|Nebyl nalezen očekávaný token/identifikátor pro anotaci, parametr|
|[C28224](/cpp/code-quality/c28224)|Poznámka vyžaduje parametry.|
|[C28225](/cpp/code-quality/c28225)|Nebyl nalezen správný počet požadovaných parametrů v poznámce|
|[C28226](/cpp/code-quality/c28226)|Anotace nemůže být také PrimOp (v aktuální deklaraci)|
|[C28227](/cpp/code-quality/c28227)|Anotace nemůže být také PrimOp (viz předchozí deklarace)|
|[C28228](/cpp/code-quality/c28228)|Parametr Anotace: v poznámkách nelze použít typ.|
|[C28229](/cpp/code-quality/c28229)|Poznámka nepodporuje parametry|
|[C28230](/cpp/code-quality/c28230)|Typ parametru nemá žádného člena.|
|[C28231](/cpp/code-quality/c28231)|Anotace je platná pouze pro pole.|
|[C28232](/cpp/code-quality/c28232)|předplatná, post nebo DEREF nejsou aplikovány na žádnou poznámku.|
|[C28233](/cpp/code-quality/c28233)|použití pre, post nebo DEREF pro blok|
|[C28234](/cpp/code-quality/c28234)|výraz __at se nedá použít u aktuální funkce.|
|[C28235](/cpp/code-quality/c28235)|Funkce nemůže být samostatná jako anotace.|
|[C28236](/cpp/code-quality/c28236)|Anotaci nelze použít ve výrazu.|
|[C28237](/cpp/code-quality/c28237)|Poznámka k parametru už není podporovaná.|
|[C28238](/cpp/code-quality/c28238)|Poznámka u parametru má více než jednu hodnotu, stringValue a longValue. Použít paramn = XXX|
|[C28239](/cpp/code-quality/c28239)|Poznámka u parametru má hodnotu, stringValue nebo longValue; a paramn = xxx. Použít pouze paramn = XXX|
|[C28240](/cpp/code-quality/c28240)|Poznámka u parametru má param2, ale ne param1.|
|[C28241](/cpp/code-quality/c28241)|Poznámka pro funkci v parametru nebyla rozpoznána.|
|[C28243](/cpp/code-quality/c28243)|Poznámka pro funkci v parametru vyžaduje více odkazů, než je skutečný typ s poznámkami. umožňuje|
|[C28245](/cpp/code-quality/c28245)|Poznámka pro funkci přihlásí this na funkci bez členu.|
|[C28246](/cpp/code-quality/c28246)|Anotace parametru pro funkci se neshoduje s typem parametru.|
|[C28250](/cpp/code-quality/c28250)|Nekonzistentní Poznámka pro funkci: předchozí instance obsahuje chybu.|
|[C28251](/cpp/code-quality/c28251)|Nekonzistentní Poznámka pro funkci: Tato instance obsahuje chybu.|
|[C28252](/cpp/code-quality/c28252)|Nekonzistentní Poznámka pro funkci: parametr má v této instanci jiné anotace.|
|[C28253](/cpp/code-quality/c28253)|Nekonzistentní Poznámka pro funkci: parametr má v této instanci jiné anotace.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<> () se v poznámkách nepodporuje.|
|[C28262](/cpp/code-quality/c28262)|Chyba syntaxe v poznámce byla nalezena ve funkci pro poznámku|
|[C28263](/cpp/code-quality/c28263)|Našla se chyba syntaxe v podmíněné poznámce pro vnitřní anotaci.|
|[C28267](/cpp/code-quality/c28267)|Ve funkci byla nalezena Poznámka s chybou syntaxe v poznámkách.|
|[C28272](/cpp/code-quality/c28272)|Poznámka pro funkci, parametr při zkoumání je nekonzistentní s deklarací funkce|
|[C28273](/cpp/code-quality/c28273)|V případě funkcí jsou změny nekonzistentní s deklarací funkce|
|[C28275](/cpp/code-quality/c28275)|Parametr k \_ hodnotě makra \_ \_ je null.|
|[C28279](/cpp/code-quality/c28279)|Pro symbol byl nalezen prvek Begin bez odpovídajícího příkazu end.|
|[C28280](/cpp/code-quality/c28280)|Pro symbol byl nalezen znak end bez odpovídajícího prvku Begin.|
|[C28282](/cpp/code-quality/c28282)|Řetězce formátu musí být v předběžných podmínkách.|
|[C28285](/cpp/code-quality/c28285)|Pro funkci, Chyba syntaxe v parametru|
|[C28286](/cpp/code-quality/c28286)|Pro funkci se chyba syntaxe blíží konci.|
|[C28287](/cpp/code-quality/c28287)|Pro funkci došlo k chybě syntaxe \_ v \_ () anotaci () (nerozpoznaný název parametru).|
|[C28288](/cpp/code-quality/c28288)|Pro funkci, Chyba syntaxe v \_ \_ poznámce () anotace (neplatný název parametru)|
|[C28289](/cpp/code-quality/c28289)|Funkce: ReadableTo nebo Writableto nebyl neobsahovala omezení-spec jako parametr.|
|[C28290](/cpp/code-quality/c28290)|Anotace for Function obsahuje více externích typů, než je skutečný počet parametrů.|
|[C28291](/cpp/code-quality/c28291)|Hodnota post null/NotNull na DEREF Level 0 nemá význam pro funkci.|
|[C28300](/cpp/code-quality/c28300)|Operandy výrazu nekompatibilních typů pro operátor|
|[C28301](/cpp/code-quality/c28301)|Žádné poznámky pro první deklaraci funkce|
|[C28302](/cpp/code-quality/c28302)|\_ \_ V poznámce byl nalezen další operátor DEREF.|
|[C28303](/cpp/code-quality/c28303)|\_ \_ V poznámce byl nalezen dvojznačný DEREF operátor.|
|[C28304](/cpp/code-quality/c28304)|Byl nalezen nesprávně umístěný \_ Notref \_ operátor, který se použil pro token.|
|[C28305](/cpp/code-quality/c28305)|Zjistila se chyba při analýze tokenu.|
|[C28350](/cpp/code-quality/c28350)|Poznámka popisuje situaci, která není podmíněně platná.|
|[C28351](/cpp/code-quality/c28351)|Poznámka popisuje, kde v podmínce nelze použít dynamickou hodnotu (proměnnou).|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Odeberte prázdné finalizační metody|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Uvolnitelná pole by měla být uvolněna|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Přetižte operátor rovnosti při přetížení ValueType.Equals|