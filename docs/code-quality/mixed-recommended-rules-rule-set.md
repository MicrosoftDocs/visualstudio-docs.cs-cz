---
title: Sada pravidel Smíšená doporučená pravidla
ms.date: 11/04/2016
description: Seznamte se se smíšenou sadou pravidel doporučených pravidel v sadě Visual Studio. Viz popisy pravidel pro projekty jazyka C++, které podporují modul CLR (Common Language Runtime).
ms.custom: SEO-VS-2020
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7897799e631aad1005d4300e811f8209adb8281d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859772"
---
# <a name="mixed-recommended-rules-rule-set"></a>Sada pravidel Smíšená doporučená pravidla

Doporučená pravidla společnosti Microsoft se zaměřují na nejběžnější a kritické problémy v projektech C++, které podporují modul CLR (Common Language Runtime), včetně možných děr zabezpečení, chyb aplikací a dalších důležitých chyb logiky a návrhu. Tato sada pravidel zahrnuje všechna pravidla v sadě pravidel [smíšeného minima Rules](mixed-minimum-rules-rule-set.md) .

Zahrňte tuto sadu pravidel v jakékoli vlastní sadě pravidel, kterou vytvoříte pro projekty C++, které podporují modul CLR (Common Language Runtime).

|Pravidlo|Description|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Použití neinicializované paměti|
|[C6011](/cpp/code-quality/c6011)|Přesměrování ukazatele null|
|[C6029](/cpp/code-quality/c6029)|Použití nezkontrolované hodnoty|
|[C6031](/cpp/code-quality/c6031)|Návratová hodnota ignorována|
|[C6053](/cpp/code-quality/c6053)|Nula ukončení volání|
|[C6054](/cpp/code-quality/c6054)|Chybí nulové zakončení.|
|[C6059](/cpp/code-quality/c6059)|Chybné zřetězení|
|[C6063](/cpp/code-quality/c6063)|Chybí argument řetězce pro formátování funkce|
|[C6064](/cpp/code-quality/c6064)|Chybějící argument typu Integer pro formátování funkce|
|[C6066](/cpp/code-quality/c6066)|Chybí argument ukazatele pro formátování funkce|
|[C6067](/cpp/code-quality/c6067)|Chybí argument ukazatele řetězce pro formátování funkce|
|[C6101](/cpp/code-quality/c6101)|Vracení neinicializované paměti|
|[C6200](/cpp/code-quality/c6200)|Index překračuje maximum vyrovnávací paměti.|
|[C6201](/cpp/code-quality/c6201)|Index překračuje maximum vyrovnávací paměti zásobníku.|
|[C6214](/cpp/code-quality/c6214)|Neplatné přetypování HRESULT na BOOL|
|[C6215](/cpp/code-quality/c6215)|Neplatné přetypování typu BOOL na HRESULT|
|[C6216](/cpp/code-quality/c6216)|Neplatná hodnota typu BOOL přetypování Compiler-Inserted na HRESULT|
|[C6217](/cpp/code-quality/c6217)|Neplatný test HRESULT s NOT|
|[C6220](/cpp/code-quality/c6220)|Neplatné porovnání HRESULT s-1|
|[C6226](/cpp/code-quality/c6226)|Neplatné přiřazení HRESULT na-1|
|[C6230](/cpp/code-quality/c6230)|Neplatné použití HRESULT jako Boolean|
|[C6235](/cpp/code-quality/c6235)|Nenulová konstanta s Logical-Or|
|[C6236](/cpp/code-quality/c6236)|Logical-Or s nenulovou konstantou|
|[C6237](/cpp/code-quality/c6237)|Nula s Logical-And ztratí vedlejší účinky|
|[C6242](/cpp/code-quality/c6242)|Vynucené místní unwind|
|[C6248](/cpp/code-quality/c6248)|Vytváření seznamu DACL s hodnotou null|
|[C6250](/cpp/code-quality/c6250)|Nevydané popisovače adres|
|[C6255](/cpp/code-quality/c6255)|Nechráněné použití alokace|
|[C6258](/cpp/code-quality/c6258)|Použití vlákna ukončit|
|[C6259](/cpp/code-quality/c6259)|Mrtvý kód v Bitwise-Or omezený přepínač|
|[C6260](/cpp/code-quality/c6260)|Použití aritmetických bajtů|
|[C6262](/cpp/code-quality/c6262)|Nadměrné využití zásobníku|
|[C6263](/cpp/code-quality/c6263)|Použití alokačního příkazu ve smyčce|
|[C6268](/cpp/code-quality/c6268)|V přetypování chybí kulaté závorky.|
|[C6269](/cpp/code-quality/c6269)|Byl ignorován odkaz na ukazatel.|
|[C6270](/cpp/code-quality/c6270)|Chybí argument typu float pro formátování funkce|
|[C6271](/cpp/code-quality/c6271)|Nadbytečný argument pro formátování funkce|
|[C6272](/cpp/code-quality/c6272)|Argument jiného než typu float pro formátování funkce|
|[C6273](/cpp/code-quality/c6273)|Argument jiného než typu Integer pro formátování funkce|
|[C6274](/cpp/code-quality/c6274)|Argument bez znaku pro formátování funkce|
|[C6276](/cpp/code-quality/c6276)|Neplatné přetypování řetězce|
|[C6277](/cpp/code-quality/c6277)|Neplatné volání funkce CreateProcess|
|[C6278](/cpp/code-quality/c6278)|Neshoda Array-New Scalar-Delete|
|[C6279](/cpp/code-quality/c6279)|Neshoda Scalar-New Array-Delete|
|[C6280](/cpp/code-quality/c6280)|Neshoda Allocation-Deallocation paměti|
|[C6281](/cpp/code-quality/c6281)|Priorita bitového vztahu|
|[C6282](/cpp/code-quality/c6282)|Přiřazení nahrazuje test|
|[C6283](/cpp/code-quality/c6283)|Neshoda primitivních Array-New Scalar-Delete|
|[C6284](/cpp/code-quality/c6284)|Neplatný argument objektu pro formátování funkce|
|[C6285](/cpp/code-quality/c6285)|Logical-Or konstant|
|[C6286](/cpp/code-quality/c6286)|Nenulové Logical-Or ztráty vedlejších účinků|
|[C6287](/cpp/code-quality/c6287)|Redundantní test|
|[C6288](/cpp/code-quality/c6288)|Vzájemné zahrnutí přes Logical-And je nepravdivé.|
|[C6289](/cpp/code-quality/c6289)|Vzájemné vyloučení přes Logical-Or je pravdivé.|
|[C6290](/cpp/code-quality/c6290)|Logical-Not priority Bitwise-And|
|[C6291](/cpp/code-quality/c6291)|Logical-Not priority Bitwise-Or|
|[C6292](/cpp/code-quality/c6292)|Smyčka počítá směrem nahoru od maxima|
|[C6293](/cpp/code-quality/c6293)|Smyčka odpočítává dolů z minima|
|[C6294](/cpp/code-quality/c6294)|Tělo smyčky není nikdy provedeno|
|[C6295](/cpp/code-quality/c6295)|Nekonečná smyčka|
|[C6296](/cpp/code-quality/c6296)|Smyčka se spustila jenom jednou.|
|[C6297](/cpp/code-quality/c6297)|Výsledek přetypování Shift na větší velikost|
|[C6299](/cpp/code-quality/c6299)|Bitového pole na logické porovnání|
|[C6302](/cpp/code-quality/c6302)|Neplatný argument řetězce znaků pro formátování funkce|
|[C6303](/cpp/code-quality/c6303)|Neplatný argument řetězce s velkým znakem pro formátování funkce|
|[C6305](/cpp/code-quality/c6305)|Neshoda s použitím velikosti a počtu|
|[C6306](/cpp/code-quality/c6306)|Nesprávné volání funkce argumentu proměnné|
|[C6308](/cpp/code-quality/c6308)|Vrácení realokace|
|[C6310](/cpp/code-quality/c6310)|Neplatná konstanta filtru výjimky|
|[C6312](/cpp/code-quality/c6312)|Výjimka při provádění smyčky pro pokračování|
|[C6314](/cpp/code-quality/c6314)|Bitwise-Or priorita|
|[C6317](/cpp/code-quality/c6317)|Nedoplnit|
|[C6318](/cpp/code-quality/c6318)|Výjimka – hledání v pokračování|
|[C6319](/cpp/code-quality/c6319)|Ignoruje čárkou|
|[C6324](/cpp/code-quality/c6324)|Kopírovat řetězec místo řetězce porovnání|
|[C6328](/cpp/code-quality/c6328)|Potenciální Neshoda typu argumentu|
|[C6331](/cpp/code-quality/c6331)|VirtualFree neplatné příznaky|
|[C6332](/cpp/code-quality/c6332)|Neplatný parametr VirtualFree|
|[C6333](/cpp/code-quality/c6333)|VirtualFree neplatná velikost|
|[C6335](/cpp/code-quality/c6335)|Nevrácení popisovače procesu|
|[C6381](/cpp/code-quality/c6381)|Chybí informace o vypnutí.|
|[C6383](/cpp/code-quality/c6383)|Přetečení vyrovnávací paměti Element-Count Byte-Count|
|[C6384](/cpp/code-quality/c6384)|Dělení velikosti ukazatele|
|[C6385](/cpp/code-quality/c6385)|Přetečení čtení|
|[C6386](/cpp/code-quality/c6386)|Přetečení zápisu|
|[C6387](/cpp/code-quality/c6387)|Neplatná hodnota parametru|
|[C6388](/cpp/code-quality/c6388)|Neplatná hodnota parametru|
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
|[C6995](/cpp/code-quality/c6995)|Nepovedlo se uložit soubor protokolu XML.|
|[C26100](/cpp/code-quality/c26100)|Konflikt časování|
|[C26101](/cpp/code-quality/c26101)|Selhání použití propojené operace správně|
|[C26110](/cpp/code-quality/c26110)|Selhání volajícího blokovat zámek|
|[C26111](/cpp/code-quality/c26111)|Selhání volajícího uvolnit zámek|
|[C26112](/cpp/code-quality/c26112)|Volající nemůže držet žádný zámek.|
|[C26115](/cpp/code-quality/c26115)|Selhání uvolnění zámku|
|[C26116](/cpp/code-quality/c26116)|Selhání získání nebo udržení zámku|
|[C26117](/cpp/code-quality/c26117)|Uvolňuje se neuchovávaný zámek.|
|[C26140](/cpp/code-quality/c26140)|Chyba anotace SAL pro Concurrency|
|[C28020](/cpp/code-quality/c28020)|Výraz není na tomto volání pravdivý.|
|[C28021](/cpp/code-quality/c28021)|Parametr, který se dá opatřit poznámkami, musí být ukazatelem.|
|[C28022](/cpp/code-quality/c28022)|Třídy funkcí této funkce se neshodují s třídami Functions na definici TypeDef použitou k jejímu definování.|
|[C28023](/cpp/code-quality/c28023)|Přiřazená nebo předaná funkce by měla mít \_ \_ \_ anotaci třídy funkce pro alespoň jednu ze tříd (ES).|
|[C28024](/cpp/code-quality/c28024)|Ukazatel funkce, ke kterému se přiřazuje, je opatřen poznámkou se třídou Function, která není obsažena v seznamu tříd funkcí.|
|[C28039](/cpp/code-quality/c28039)|Typ skutečného parametru by měl přesně odpovídat typu|
|[C28112](/cpp/code-quality/c28112)|K proměnné, ke které se dá přistupovat přes propojenou funkci, se musí vždycky přistupovat prostřednictvím propojené funkce.|
|[C28113](/cpp/code-quality/c28113)|Přístup k místní proměnné prostřednictvím propojené funkce|
|[C28125](/cpp/code-quality/c28125)|Funkce musí být volána v rámci bloku try/except.|
|[C28137](/cpp/code-quality/c28137)|Argument proměnné by měl být (literál) konstanta.|
|[C28138](/cpp/code-quality/c28138)|Konstantní argument by měl být místo proměnné.|
|[C28159](/cpp/code-quality/c28159)|Zvažte místo toho použití jiné funkce.|
|[C28160](/cpp/code-quality/c28160)|Poznámka k chybě|
|[C28163](/cpp/code-quality/c28163)|Funkce by nikdy neměla být volána v rámci bloku try/except|
|[C28164](/cpp/code-quality/c28164)|Argument se předává funkci, která očekává ukazatel na objekt (ne ukazatel na ukazatel).|
|[C28182](/cpp/code-quality/c28182)|Přesměrování ukazatele s hodnotou NULL. Ukazatel obsahuje stejnou hodnotu NULL jako jiný ukazatel.|
|[C28183](/cpp/code-quality/c28183)|Argumentem může být jedna hodnota a je kopie hodnoty nalezené v ukazateli.|
|[C28193](/cpp/code-quality/c28193)|Proměnná obsahuje hodnotu, kterou je třeba prozkoumat.|
|[C28196](/cpp/code-quality/c28196)|Požadavek není splněn. (Výraz se nevyhodnotí jako true.)|
|[C28202](/cpp/code-quality/c28202)|Neplatný odkaz na nestatický člen|
|[C28203](/cpp/code-quality/c28203)|Nejednoznačný odkaz na člena třídy.|
|[C28205](/cpp/code-quality/c28205)|\_Úspěch \_ nebo \_ při \_ selhání při \_ použití v neplatném kontextu|
|[C28206](/cpp/code-quality/c28206)|Levý operand ukazuje na strukturu, použijte '-> '|
|[C28207](/cpp/code-quality/c28207)|Levý operand je struktura, použijte '. '|
|[C28209](/cpp/code-quality/c28209)|Deklarace pro symbol má konfliktní deklaraci.|
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
|[C28244](/cpp/code-quality/c28244)|Anotace for Function má neanalyzovatelné parametry/externí anotaci.|
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
|[C28306](/cpp/code-quality/c28306)|Poznámka k parametru je zastarávající|
|[C28307](/cpp/code-quality/c28307)|Poznámka k parametru je zastarávající|
|[C28350](/cpp/code-quality/c28350)|Poznámka popisuje situaci, která není podmíněně platná.|
|[C28351](/cpp/code-quality/c28351)|Poznámka popisuje, kde v podmínce nelze použít dynamickou hodnotu (proměnnou).|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1009](../code-quality/ca1009.md)|Deklarujte správně obslužné rutiny událostí|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Označte sestavení pomocí AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Metody rozhraní by měly být volatelné podřízenými typy|
|[CA1049](../code-quality/ca1049.md)|Typy, které vlastní nativní prostředky, by měly být uvolnitelné|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Přesuňte volání nespravovaných kódů do třídy NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Neskrývejte metody základní třídy|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implementuje správně IDisposable|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Nevyvolávejte výjimky v neočekávaných umístěních|
|[CA1301](../code-quality/ca1301.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1400](../code-quality/ca1400.md)|Vstupní body volání nespravovaného kódu by měly existovat|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Volání nespravovaných kódů by neměla být viditelná|
|[CA1403](../code-quality/ca1403.md)|Typy automatického rozložení by neměly být viditelné modelu COM|
|[CA1404](../code-quality/ca1404.md)|Volejte GetLastError ihned po volání nespravovaného kódu|
|[CA1405](../code-quality/ca1405.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody registrace modelu COM by si měly odpovídat|
|[CA1415](../code-quality/ca1415.md)|Deklarujte správně volání nespravovaných kódů|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Odeberte prázdné finalizační metody|
|[CA1900](../code-quality/ca1900.md)|Pole typů hodnot by měla být přenosná|
|[CA1901](../code-quality/ca1901.md)|Deklarace volání nespravovaného kódu by měla být přenosná|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Nepoužívejte zámky u objektů se slabou identitou|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Zkontrolujte chyby zabezpečení u dotazů SQL|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Určete zařazování pro argumenty řetězce volání nespravovaného kódu|
|[CA2108](../code-quality/ca2108.md)|Zkontrolujte deklarativní zabezpečení u typů hodnot|
|[CA2111](../code-quality/ca2111.md)|Ukazatele by neměly být viditelné|
|[CA2112](../code-quality/ca2112.md)|Zabezpečené typy by neměly vystavovat pole|
|[CA2114](../code-quality/ca2114.md)|Zabezpečení metod by mělo být nadmnožinou typu|
|[CA2116](../code-quality/ca2116.md)|Metody APTCA by měly volat pouze metody APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy APTCA by měl rozšiřovat pouze základní typy APTCA|
|[CA2122](../code-quality/ca2122.md)|Nezveřejňujte nepřímo metody s požadavky propojení|
|[CA2123](../code-quality/ca2123.md)|Požadavky na propojení přepisů by měly být identické s bází|
|[CA2124](../code-quality/ca2124.md)|Zabalte ohroženou klauzuli finally do vnějšího bloku try|
|[CA2126](../code-quality/ca2126.md)|Požadavky na propojení typů vyžadují požadavky na dědičnost|
|[CA2131](../code-quality/ca2131.md)|Typy kritické pro zabezpečení se nesmí účastnit ekvivalence typů|
|[CA2132](../code-quality/ca2132.md)|Výchozí konstruktory musí být alespoň tak kritické, jako výchozí konstruktory základního typu|
|[CA2133](../code-quality/ca2133.md)|Delegáti musí mít vazbu s metodami s konzistentní transparentností|
|[CA2134](../code-quality/ca2134.md)|Metody musí při přepisování základních metod zachovávat konzistentní transparentnost|
|[CA2137](../code-quality/ca2137.md)|Transparentní metody musí obsahovat pouze ověřitelné IL|
|[CA2138](../code-quality/ca2138.md)|Transparentní metody nesmí volat metody s atributem SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení|
|[CA2141](../code-quality/ca2141.md)|Transparentní metody nesmí splňovat LinkDemand.|
|[CA2146](../code-quality/ca2146.md)|Typy musí být alespoň tak kritické, jako jejich základní typy a rozhraní|
|[CA2147](../code-quality/ca2147.md)|Transparentní metody nemusí používat kontrolní příkazy zabezpečení|
|[CA2149](../code-quality/ca2149.md)|Transparentní metody nesmí provádět volání nativního kódu|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Znovu vyvolejte pro zachování podrobností zásobníku|
|[CA2202](../code-quality/ca2202.md)|Neuvolňujte objekty několikrát|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Inicializujte statická pole s typem hodnoty vloženě|
|[CA2212](../code-quality/ca2212.md)|Neoznačujte obsluhované komponenty pomocí WebMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Uvolnitelná pole by měla být uvolněna|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|Nevolejte přepisovatelné metody v konstruktorech|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Uvolnitelné typy by měly deklarovat finalizační metodu|
|[CA2220](../code-quality/ca2220.md)|Finalizační metody by měly volat finalizační metodu základní třídy|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implementujte serializační konstruktory|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Přetižte operátor rovnosti při přetížení ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Označte vstupní body modelu Windows Forms pomocí STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Označte všechna neserializovatelná pole|
|[CA2236](../code-quality/ca2236.md)|Volejte metody základní třídy u typů ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Označte typy ISerializable pomocí SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementujte správně metody serializace|
|[CA2240](../code-quality/ca2240.md)|Implementujte správně ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Zadejte správné argumenty pro metody formátování|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Testujte správně NaN|