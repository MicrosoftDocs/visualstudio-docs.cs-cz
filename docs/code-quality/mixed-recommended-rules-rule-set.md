---
title: Sada pravidel Smíšená doporučená pravidla
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ce28a8c1dd5c9ec510e4bf30b6e710b2b4dbc2a
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649320"
---
# <a name="mixed-recommended-rules-rule-set"></a>Sada pravidel Smíšená doporučená pravidla

Smíšená doporučená pravidla společnosti Microsoft se zaměřují na nejběžnější a kritické problémy v projektech jazyka C++, které podporují prostředí Common Language Runtime, včetně potenciálních bezpečnostních děr, selhání aplikací a dalších důležitých chyb logiky a návrhu. Tato sada pravidel zahrnuje všechna pravidla v sadě pravidel [smíšených minimálních pravidel.](mixed-minimum-rules-rule-set.md)

Tuto sadu pravidel zahrňte do libovolné vlastní sady pravidel, kterou vytvoříte pro projekty jazyka C++, které podporují běžný jazykový běh.

|Pravidlo|Popis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Použití neinicializované paměti|
|[C6011](../code-quality/c6011.md)|Odkazování na nulový ukazatel|
|[C6029](../code-quality/c6029.md)|Použití nekontrolované hodnoty|
|[C6031](../code-quality/c6031.md)|Vrácená hodnota byla ignorována.|
|[C6053](../code-quality/c6053.md)|Nulové ukončení z volání|
|[C6054](../code-quality/c6054.md)|Chybí nulové ukončení.|
|[C6059](../code-quality/c6059.md)|Špatné zřetězení|
|[C6063](../code-quality/c6063.md)|Funkce Chybějící argument řetězec pro formátování|
|[C6064](../code-quality/c6064.md)|Chybí funkce Integer Argument To Format|
|[C6066](../code-quality/c6066.md)|Chybějící argument ukazatele na funkci Formát|
|[C6067](../code-quality/c6067.md)|Chybějící argument ukazatele řetězce na funkci Formát|
|[C6101](../code-quality/c6101.md)|Vrácení neinicializované paměti|
|[C6200](../code-quality/c6200.md)|Index překračuje maximální vyrovnávací paměť|
|[C6201](../code-quality/c6201.md)|Maximální hodnota vyrovnávací paměti zásobníku překračuje|
|[C6214](../code-quality/c6214.md)|Neplatný přetypovat HRESULT na BOOL|
|[C6215](../code-quality/c6215.md)|Neplatný přetypovat BOOL na HRESULT|
|[C6216](../code-quality/c6216.md)|Neplatný kompilátor vložený přetypování BOOL na HRESULT|
|[C6217](../code-quality/c6217.md)|Neplatný test HRESULT s neplatným|
|[C6220](../code-quality/c6220.md)|Neplatný hRESULT v porovnání s -1|
|[C6226](../code-quality/c6226.md)|Neplatné přiřazení HRESULT na -1|
|[C6230](../code-quality/c6230.md)|Neplatné použití hresult jako logické|
|[C6235](../code-quality/c6235.md)|Nenulová konstanta s logickým nebo|
|[C6236](../code-quality/c6236.md)|Logická nebo s nenulovou konstantou|
|[C6237](../code-quality/c6237.md)|Nula s logickým-a ztrácí vedlejší účinky|
|[C6242](../code-quality/c6242.md)|Místní unwind vynucený|
|[C6248](../code-quality/c6248.md)|Vytvoření seznamu DACL null|
|[C6250](../code-quality/c6250.md)|Nevydané popisovače adres|
|[C6255](../code-quality/c6255.md)|Nechráněné použití aloublky|
|[C6258](../code-quality/c6258.md)|Použití ukončit podproces|
|[C6259](../code-quality/c6259.md)|Mrtvý kód v bitovém nebo omezeném přepínači|
|[C6260](../code-quality/c6260.md)|Použití arithmetiky bajtů|
|[C6262](../code-quality/c6262.md)|Nadměrné využití zásobníku|
|[C6263](../code-quality/c6263.md)|Použití aplikace Alloca in loop|
|[C6268](../code-quality/c6268.md)|Chybějící závorky v přetypce|
|[C6269](../code-quality/c6269.md)|Odkaz na ukazatel byl ignorován.|
|[C6270](../code-quality/c6270.md)|Funkce Chybějící argument plovoucí na formát|
|[C6271](../code-quality/c6271.md)|Funkce Extra Argument to Format|
|[C6272](../code-quality/c6272.md)|Funkce Neplovoucí argument pro formát|
|[C6273](../code-quality/c6273.md)|Funkce Neceločíselný argument pro formátování|
|[C6274](../code-quality/c6274.md)|Neznakový argument pro funkci Formátování|
|[C6276](../code-quality/c6276.md)|Neplatný přetypování řetězců|
|[C6277](../code-quality/c6277.md)|Neplatné volání createprocess|
|[C6278](../code-quality/c6278.md)|Neshoda mezi novým skalárním odstraněním pole|
|[C6279](../code-quality/c6279.md)|Skalární nové pole-odstranění neshody|
|[C6280](../code-quality/c6280.md)|Neshoda přidělení paměti a přidělení paměti|
|[C6281](../code-quality/c6281.md)|Priorita bitových vztahů|
|[C6282](../code-quality/c6282.md)|Test nahrazení přiřazení|
|[C6283](../code-quality/c6283.md)|Neshoda primitivního pole - nové hořlavé odstranění|
|[C6284](../code-quality/c6284.md)|Neplatný argument objektu pro funkci Formátování|
|[C6285](../code-quality/c6285.md)|Logické nebo konstanty|
|[C6286](../code-quality/c6286.md)|Nenulové logické nebo ztrátové vedlejší účinky|
|[C6287](../code-quality/c6287.md)|Redundantní test|
|[C6288](../code-quality/c6288.md)|Vzájemné začlenění přes logické-a je nepravdivé|
|[C6289](../code-quality/c6289.md)|Vzájemné vyloučení přes logické nebo je pravdivé|
|[C6290](../code-quality/c6290.md)|Logická-ne bitová a priorita|
|[C6291](../code-quality/c6291.md)|Logická nebitová nebo priorita|
|[C6292](../code-quality/c6292.md)|Smyčková se počítá od maxima|
|[C6293](../code-quality/c6293.md)|Odpočítávání smyčky od minima|
|[C6294](../code-quality/c6294.md)|Tělo smyčky nebylo nikdy provedeno|
|[C6295](../code-quality/c6295.md)|Nekonečná smyčka|
|[C6296](../code-quality/c6296.md)|Smyčka byla spuštěna pouze jednou|
|[C6297](../code-quality/c6297.md)|Výsledek posunu přetypovacího lití na větší velikost|
|[C6299](../code-quality/c6299.md)|Bitfield to boolean porovnání|
|[C6302](../code-quality/c6302.md)|Neplatný argument znakového řetězce pro funkci Formátování|
|[C6303](../code-quality/c6303.md)|Neplatný argument řetězec celého znaku pro funkci Formátování|
|[C6305](../code-quality/c6305.md)|Neodpovídající velikost a počet použití|
|[C6306](../code-quality/c6306.md)|Nesprávné volání funkce argumentu proměnné|
|[C6308](../code-quality/c6308.md)|Realloc úniku|
|[C6310](../code-quality/c6310.md)|Konstanta filtru neplatných výjimek|
|[C6312](../code-quality/c6312.md)|Smyčka pokračování v provádění výjimky|
|[C6314](../code-quality/c6314.md)|Bitová priorita nebo priorita|
|[C6317](../code-quality/c6317.md)|Nedoplňuje|
|[C6318](../code-quality/c6318.md)|Výjimka pokračovat v hledání|
|[C6319](../code-quality/c6319.md)|Ignorováno čárkou|
|[C6324](../code-quality/c6324.md)|Kopie řetězce místo porovnání řetězců|
|[C6328](../code-quality/c6328.md)|Neshoda potenciálního typu argumentu|
|[C6331](../code-quality/c6331.md)|Neplatné příznaky VirtualFree|
|[C6332](../code-quality/c6332.md)|Neplatný parametr VirtualFree|
|[C6333](../code-quality/c6333.md)|Neplatná velikost VirtualFree|
|[C6335](../code-quality/c6335.md)|Netěsnící popisovač procesu|
|[C6381](../code-quality/c6381.md)|Chybí informace o vypnutí|
|[C6383](../code-quality/c6383.md)|Přetečení vyrovnávací paměti počet bajtů počtu prvků|
|[C6384](../code-quality/c6384.md)|Rozdělení velikosti ukazatele|
|[C6385](../code-quality/c6385.md)|Čtení překročení|
|[C6386](../code-quality/c6386.md)|Přetečovat|
|[C6387](../code-quality/c6387.md)|Neplatná hodnota parametru|
|[C6388](../code-quality/c6388.md)|Neplatná hodnota parametru|
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
|[C6995](../code-quality/c6995.md)|Uložení souboru protokolu XML se nezdařilo.|
|[C26100](../code-quality/c26100.md)|Konflikt časování|
|[C26101](../code-quality/c26101.md)|Nepoužití vzájemně propojených operací správně|
|[C26110](../code-quality/c26110.md)|Volající nedrží zámek|
|[C26111](../code-quality/c26111.md)|Volající se nepodařilo uvolnit zámek|
|[C26112](../code-quality/c26112.md)|Volající nemůže podržet žádný zámek.|
|[C26115](../code-quality/c26115.md)|Neuvolnění zámku|
|[C26116](../code-quality/c26116.md)|Nezískání nebo zablokování|
|[C26117](../code-quality/c26117.md)|Uvolnění nedrženého zámku|
|[C26140](../code-quality/c26140.md)|Chyba poznámky SAL souběžnosti|
|[C28020](../code-quality/c28020.md)|Výraz není pravdivý při tomto volání|
|[C28021](../code-quality/c28021.md)|Parametr, který je anotován, musí být ukazatel.|
|[C28022](../code-quality/c28022.md)|Třída funkce v této funkci neodpovídá třídám funkcí na typedef, který ji definuje.|
|[C28023](../code-quality/c28023.md)|Funkce, která je přiřazena \_\_nebo\_ předána, by měla mít poznámku třídy Function alespoň pro jednu třídu (třídy)|
|[C28024](../code-quality/c28024.md)|Ukazatel funkce, který je přiřazen, je anotován s třídou funkce, která není obsažena v seznamu třídy funkcí.|
|[C28039](../code-quality/c28039.md)|Typ skutečného parametru by měl přesně odpovídat typu|
|[C28112](../code-quality/c28112.md)|Proměnná, ke které se přistupuje prostřednictvím interlocked funkce, musí být vždy přístupná prostřednictvím funkce Interlocked.|
|[C28113](../code-quality/c28113.md)|Přístup k místní proměnné prostřednictvím funkce Interlocked|
|[C28125](../code-quality/c28125.md)|Funkce musí být volána z bloku try/except|
|[C28137](../code-quality/c28137.md)|Argument proměnné by měl být místo toho (literál) konstanta|
|[C28138](../code-quality/c28138.md)|Konstantní argument by měl být místo toho variabilní.|
|[C28159](../code-quality/c28159.md)|Zvažte použití jiné funkce místo.|
|[C28160](../code-quality/c28160.md)|Anotace došlo k chybě.|
|[C28163](../code-quality/c28163.md)|Funkce by nikdy neměla být volána z bloku try/except|
|[C28164](../code-quality/c28164.md)|Argument je předáván funkci, která očekává ukazatel na objekt (nikoli ukazatel na ukazatel)|
|[C28182](../code-quality/c28182.md)|Dereferencing null ukazatel. Ukazatel obsahuje stejnou hodnotu NULL jako jiný ukazatel.|
|[C28183](../code-quality/c28183.md)|Argument může být jedna hodnota a je kopií hodnoty nalezené v ukazateli|
|[C28193](../code-quality/c28193.md)|Proměnná obsahuje hodnotu, která musí být zkontrolována|
|[C28196](../code-quality/c28196.md)|Požadavek není splněn. (Výraz není vyhodnocen jako true.)|
|[C28202](../code-quality/c28202.md)|Neplatný odkaz na nestatický člen|
|[C28203](../code-quality/c28203.md)|Nejednoznačný odkaz na člen třídy.|
|[C28205](../code-quality/c28205.md)|\_Úspěch\_ \_nebo\_\_ při neúspěchu použitém v nelegálním kontextu|
|[C28206](../code-quality/c28206.md)|Levý operand ukazuje na strukturu, použijte '->'|
|[C28207](../code-quality/c28207.md)|Levý operand je struktura, použijte '.'|
|[C28209](../code-quality/c28209.md)|Deklarace symbolu má konfliktní deklaraci.|
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
|[C28244](../code-quality/c28244.md)|Anotace pro funkci má neanalyzovatelný parametr/externí anotaci|
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
|[C28306](../code-quality/c28306.md)|Anotace na parametrje zastaralá|
|[C28307](../code-quality/c28307.md)|Anotace na parametrje zastaralá|
|[C28350](../code-quality/c28350.md)|Anotace popisuje situaci, která není podmíněně použitelná.|
|[C28351](/cpp/code-quality/c28351)|Anotace popisuje, kde dynamickou hodnotu (proměnnou) nelze použít v podmínce.|
|[CA1001](../code-quality/ca1001.md)|Typy, které vlastní uvolnitelné pole, by měly být uvolnitelné|
|[CA1009](../code-quality/ca1009.md)|Deklarujte správně obslužné rutiny událostí|
|[CA1016](../code-quality/ca1016.md)|Označte sestavení pomocí AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|Metody rozhraní by měly být volatelné podřízenými typy|
|[CA1049](../code-quality/ca1049.md)|Typy, které vlastní nativní prostředky, by měly být uvolnitelné|
|[CA1060](../code-quality/ca1060.md)|Přesuňte volání nespravovaných kódů do třídy NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Neskrývejte metody základní třídy|
|[CA1063](../code-quality/ca1063.md)|Implementuje správně IDisposable|
|[CA1065](../code-quality/ca1065.md)|Nevyvolávejte výjimky v neočekávaných umístěních|
|[CA1301](../code-quality/ca1301.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1400](../code-quality/ca1400.md)|Vstupní body volání nespravovaného kódu by měly existovat|
|[CA1401](../code-quality/ca1401.md)|Volání nespravovaných kódů by neměla být viditelná|
|[CA1403](../code-quality/ca1403.md)|Typy automatického rozložení by neměly být viditelné modelu COM|
|[CA1404](../code-quality/ca1404.md)|Volejte GetLastError ihned po volání nespravovaného kódu|
|[CA1405](../code-quality/ca1405.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody registrace modelu COM by si měly odpovídat|
|[CA1415](../code-quality/ca1415.md)|Deklarujte správně volání nespravovaných kódů|
|[CA1821](../code-quality/ca1821.md)|Odeberte prázdné finalizační metody|
|[CA1900](../code-quality/ca1900.md)|Pole typů hodnot by měla být přenosná|
|[CA1901](../code-quality/ca1901.md)|Deklarace volání nespravovaného kódu by měla být přenosná|
|[CA2002](../code-quality/ca2002.md)|Nepoužívejte zámky u objektů se slabou identitou|
|[CA2100](../code-quality/ca2100.md)|Zkontrolujte chyby zabezpečení u dotazů SQL|
|[CA2101](../code-quality/ca2101.md)|Určete zařazování pro argumenty řetězce volání nespravovaného kódu|
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
|[CA2141](../code-quality/ca2141.md)|Transparentní metody nesmí splňovat LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Typy musí být alespoň tak kritické, jako jejich základní typy a rozhraní|
|[CA2147](../code-quality/ca2147.md)|Transparentní metody nemusí používat kontrolní příkazy zabezpečení|
|[CA2149](../code-quality/ca2149.md)|Transparentní metody nesmí provádět volání nativního kódu|
|[CA2200](../code-quality/ca2200.md)|Znovu vyvolejte pro zachování podrobností zásobníku|
|[CA2202](../code-quality/ca2202.md)|Neuvolňujte objekty několikrát|
|[CA2207](../code-quality/ca2207.md)|Inicializujte statická pole s typem hodnoty vloženě|
|[CA2212](../code-quality/ca2212.md)|Neoznačujte obsluhované komponenty pomocí WebMethod|
|[CA2213](../code-quality/ca2213.md)|Uvolnitelná pole by měla být uvolněna|
|[CA2214](../code-quality/ca2214.md)|Nevolejte přepisovatelné metody v konstruktorech|
|[CA2216](../code-quality/ca2216.md)|Uvolnitelné typy by měly deklarovat finalizační metodu|
|[CA2220](../code-quality/ca2220.md)|Finalizační metody by měly volat finalizační metodu základní třídy|
|[CA2229](../code-quality/ca2229.md)|Implementujte serializační konstruktory|
|[CA2231](../code-quality/ca2231.md)|Přetižte operátor rovnosti při přetížení ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Označte vstupní body modelu Windows Forms pomocí STAThread|
|[CA2235](../code-quality/ca2235.md)|Označte všechna neserializovatelná pole|
|[CA2236](../code-quality/ca2236.md)|Volejte metody základní třídy u typů ISerializable|
|[CA2237](../code-quality/ca2237.md)|Označte typy ISerializable pomocí SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementujte správně metody serializace|
|[CA2240](../code-quality/ca2240.md)|Implementujte správně ISerializable|
|[CA2241](../code-quality/ca2241.md)|Zadejte správné argumenty pro metody formátování|
|[CA2242](../code-quality/ca2242.md)|Testujte správně NaN|
