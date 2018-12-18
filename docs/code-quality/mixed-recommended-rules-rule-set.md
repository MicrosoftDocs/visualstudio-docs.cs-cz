---
title: Sada pravidel Smíšená doporučená pravidla
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e155457b250eaa03f56d0009ee434bd1ecb39b63
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945868"
---
# <a name="mixed-recommended-rules-rule-set"></a>Sada pravidel Smíšená doporučená pravidla

Microsoft smíšená doporučená pravidla se soustředí na nejběžnějších a kritické problémy v projektech C++, které podporují modul Common Language Runtime, včetně možných bezpečnostních děr, selhání aplikace a jiných důležitých chyb logiky a návrhu. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše projekty C++, které podporují modul Common Language Runtime.

|Pravidlo|Popis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Použití neinicializované paměti|
|[C6011](../code-quality/c6011.md)|Přesměrování ukazatele Null|
|[C6029](../code-quality/c6029.md)|Použití nezkontrolované hodnoty|
|[C6031](../code-quality/c6031.md)|Vrácená hodnota ignorována|
|[C6053](../code-quality/c6053.md)|Ukončeno nulou z volání|
|[C6054](../code-quality/c6054.md)|Ukončení nulou nebylo nalezeno|
|[C6059](../code-quality/c6059.md)|Špatné zřetězení|
|[C6063](../code-quality/c6063.md)|Chybí Argument řetězce pro formátování funkce|
|[C6064](../code-quality/c6064.md)|Pro naformátování funkce chybí Argument typu celé číslo|
|[C6066](../code-quality/c6066.md)|Pro naformátování funkce chybí Argument typu ukazatel|
|[C6067](../code-quality/c6067.md)|Chybí Argument typu ukazatel řetězce pro formátování funkce|
|[C6101](../code-quality/c6101.md)|Vrácení neinicializované paměti|
|[C6200](../code-quality/c6200.md)|Index přesáhl vyrovnávací paměti|
|[C6201](../code-quality/c6201.md)|Index přesáhl vyrovnávací paměti zásobníku|
|[C6214](../code-quality/c6214.md)|Neplatné přetypování typu HRESULT na typ BOOL|
|[C6215](../code-quality/c6215.md)|Neplatné přetypování typu BOOL na hodnotu HRESULT|
|[C6216](../code-quality/c6216.md)|Neplatné přetypování vložené kompilátorem mezi BOOL a HRESULT|
|[C6217](../code-quality/c6217.md)|Test neplatný HRESULT s NOT|
|[C6220](../code-quality/c6220.md)|Porovnání neplatný HRESULT s -1|
|[C6226](../code-quality/c6226.md)|Přiřazení neplatné HRESULT na -1|
|[C6230](../code-quality/c6230.md)|Použití neplatné HRESULT jako typu Boolean|
|[C6235](../code-quality/c6235.md)|Non-Zero Constant s logické- nebo|
|[C6236](../code-quality/c6236.md)|Logické- nebo s nenulovou konstantou|
|[C6237](../code-quality/c6237.md)|Nula s logickým- And ztrácí vedlejší efekt|
|[C6242](../code-quality/c6242.md)|Vynuceno místní uvolnění|
|[C6248](../code-quality/c6248.md)|Vytváření DACL hodnoty Null|
|[C6250](../code-quality/c6250.md)|Neuvolněné popisovače adresy|
|[C6255](../code-quality/c6255.md)|Nechráněné použití funkce alloca|
|[C6258](../code-quality/c6258.md)|Pomocí ukončení vlákna|
|[C6259](../code-quality/c6259.md)|Dead kódu ve bez bitového operátoru- nebo jsou omezena přepínače|
|[C6260](../code-quality/c6260.md)|Použití aritmetického bajtů|
|[C6262](../code-quality/c6262.md)|Nadměrné použití zásobníku|
|[C6263](../code-quality/c6263.md)|Použití funkce Alloca ve smyčce|
|[C6268](../code-quality/c6268.md)|V přetypování chybí závorky|
|[C6269](../code-quality/c6269.md)|Přesměrování ukazatele bylo ignorováno|
|[C6270](../code-quality/c6270.md)|Chybí Argument typu Float pro formátování funkce|
|[C6271](../code-quality/c6271.md)|Nadbytečný Argument pro formátování funkce|
|[C6272](../code-quality/c6272.md)|Argument než typu Float pro formátování funkce|
|[C6273](../code-quality/c6273.md)|Pro naformátování funkce Argument jiných než celých čísel|
|[C6274](../code-quality/c6274.md)|Argument bez znaků pro formátování funkce|
|[C6276](../code-quality/c6276.md)|Neplatné přetypování řetězce|
|[C6277](../code-quality/c6277.md)|Neplatné volání funkce CreateProcess|
|[C6278](../code-quality/c6278.md)|Neshoda mezi nové pole smazat-Skalárně|
|[C6279](../code-quality/c6279.md)|Skalární nové pole-Skalárně|
|[C6280](../code-quality/c6280.md)|Neshoda paměti Dealokací paměti|
|[C6281](../code-quality/c6281.md)|Priorita bitového vztahu|
|[C6282](../code-quality/c6282.md)|Přiřazení nahrazuje Test|
|[C6283](../code-quality/c6283.md)|Primitivní nové pole smazat-Skalárně|
|[C6284](../code-quality/c6284.md)|Neplatný Argument objektu pro formátování funkce|
|[C6285](../code-quality/c6285.md)|Logické- nebo konstant|
|[C6286](../code-quality/c6286.md)|Non-Zero logické- nebo ztráty vedlejší účinky|
|[C6287](../code-quality/c6287.md)|Nadbytečný Test|
|[C6288](../code-quality/c6288.md)|Vzájemné zahrnutí přes logický- a má hodnotu False|
|[C6289](../code-quality/c6289.md)|Vzájemné vyloučení přes logický- nebo má hodnotu True|
|[C6290](../code-quality/c6290.md)|Bitový logický operátor Not- a určování priorit|
|[C6291](../code-quality/c6291.md)|Bitový logický operátor Not- nebo Priorita|
|[C6292](../code-quality/c6292.md)|Smyčka přičítá nahoru z maxima|
|[C6293](../code-quality/c6293.md)|Smyčka odčítá dolů z minima|
|[C6294](../code-quality/c6294.md)|Tělo smyčky se nikdy se neprovedlo.|
|[C6295](../code-quality/c6295.md)|Nekonečná smyčka|
|[C6296](../code-quality/c6296.md)|Smyčky se provede pouze jednou|
|[C6297](../code-quality/c6297.md)|Výsledek posunu přetypován na větší velikost|
|[C6299](../code-quality/c6299.md)|Bitového pole a logická porovnání|
|[C6302](../code-quality/c6302.md)|Neplatný Argument řetězec znaků pro formátování funkce|
|[C6303](../code-quality/c6303.md)|Neplatný širokého znaku řetězcový Argument pro formátování funkce|
|[C6305](../code-quality/c6305.md)|Neshoda velikosti a počtu používání|
|[C6306](../code-quality/c6306.md)|Volání funkce nesprávné argumentů s proměnnou délkou|
|[C6308](../code-quality/c6308.md)|Nevrácená paměť|
|[C6310](../code-quality/c6310.md)|Konstanta ve filtru výjimky neplatné|
|[C6312](../code-quality/c6312.md)|Výjimka bude smyčka dál vykonávat|
|[C6314](../code-quality/c6314.md)|Bitový operátor- nebo Priorita|
|[C6317](../code-quality/c6317.md)|Not Not doplněk|
|[C6318](../code-quality/c6318.md)|Výjimka pokračuje v hledání|
|[C6319](../code-quality/c6319.md)|Ignorován čárkou|
|[C6324](../code-quality/c6324.md)|Kopie řetězce namísto porovnání řetězců|
|[C6328](../code-quality/c6328.md)|Možná Neshoda typu argumentu|
|[C6331](../code-quality/c6331.md)|VirtualFree neplatné příznaky|
|[C6332](../code-quality/c6332.md)|VirtualFree neplatný parametr|
|[C6333](../code-quality/c6333.md)|VirtualFree neplatná velikost|
|[C6335](../code-quality/c6335.md)|Nevrácení popisovače procesu|
|[C6381](../code-quality/c6381.md)|Chybí informace o vypnutí|
|[C6383](../code-quality/c6383.md)|Počet prvků Byte-počet přetečení vyrovnávací paměti|
|[C6384](../code-quality/c6384.md)|Dělení velikosti ukazatele|
|[C6385](../code-quality/c6385.md)|Přetečení čtení|
|[C6386](../code-quality/c6386.md)|Přetečení zápisu|
|[C6387](../code-quality/c6387.md)|Neplatná hodnota parametru|
|[C6388](../code-quality/c6388.md)|Neplatná hodnota parametru|
|[C6500](../code-quality/c6500.md)|Neplatná vlastnost atributu|
|[C6501](../code-quality/c6501.md)|Konfliktní hodnotami vlastností atributu|
|[C6503](../code-quality/c6503.md)|Odkazy nesmí mít hodnotu Null|
|[C6504](../code-quality/c6504.md)|Null na typech bez ukazatele|
|[C6505](../code-quality/c6505.md)|Vlastnost MustCheck na typ Void|
|[C6506](../code-quality/c6506.md)|Velikost vyrovnávací paměti na typech bez ukazatele nebo pole|
|[C6508](../code-quality/c6508.md)|K zápisu na konstantě|
|[C6509](../code-quality/c6509.md)|Návratová hodnota použita na předpokladu|
|[C6510](../code-quality/c6510.md)|NULL byl ukončen na typech bez ukazatele|
|[C6511](../code-quality/c6511.md)|MustCheck musí nabývat hodnot Ano nebo ne|
|[C6513](../code-quality/c6513.md)|Velikost prvku bez velikosti vyrovnávací paměti|
|[C6514](../code-quality/c6514.md)|Velikost vyrovnávací paměti překračuje velikost pole|
|[C6515](../code-quality/c6515.md)|Velikost vyrovnávací paměti na typech bez ukazatele|
|[C6516](../code-quality/c6516.md)|Atribut nemá žádné vlastnosti|
|[C6517](../code-quality/c6517.md)|Platná velikost pro vyrovnávací paměť bez možnosti čtení|
|[C6518](../code-quality/c6518.md)|Zapisovatelná velikost pro vyrovnávací paměť, Nezapisovatelný|
|[C6522](../code-quality/c6522.md)|Typ řetězec neplatné velikosti|
|[C6525](../code-quality/c6525.md)|Neplatná velikost řetězce-nedosažitelná oblast|
|[C6527](../code-quality/c6527.md)|Neplatná Poznámka: vlastnost 'NeedsRelease' nesmí být použita pro hodnoty typu void|
|[C6530](../code-quality/c6530.md)|Nerozpoznaný styl řetězce formátu|
|[C6540](../code-quality/c6540.md)|Použití poznámek atributu na této funkci způsobí neplatnost všech existujících poznámek __declspec|
|[C6551](../code-quality/c6551.md)|Neplatná specifikace velikosti: výraz není analyzovatelný|
|[C6552](../code-quality/c6552.md)|Neplatná specifikace Deref = nebo Notref =: výraz není analyzovatelný|
|[C6701](../code-quality/c6701.md)|Hodnota není platná hodnota Ano/Ne/možná|
|[C6702](../code-quality/c6702.md)|Hodnota není hodnota řetězce|
|[C6703](../code-quality/c6703.md)|Hodnota není číslo|
|[C6704](../code-quality/c6704.md)|Neočekávaná chyba výrazu|
|[C6705](../code-quality/c6705.md)|Očekávaný počet argumentů pro anotaci se neshoduje s aktuální počet argumentů pro anotaci|
|[C6706](../code-quality/c6706.md)|Neočekávaná chyba poznámky|
|[C6995](../code-quality/c6995.md)|Nepovedlo se uložit soubor protokolu XML|
|[C26100](../code-quality/c26100.md)|Konflikt časování|
|[C26101](../code-quality/c26101.md)|Selhání použití propojené operace správně|
|[C26110](../code-quality/c26110.md)|Selhání volajícího udržet zámek|
|[C26111](../code-quality/c26111.md)|Selhání volajícího uvolnit zámek|
|[C26112](../code-quality/c26112.md)|Volající nemůže držet žádný zámek|
|[C26115](../code-quality/c26115.md)|Selhání uvolnění zámku|
|[C26116](../code-quality/c26116.md)|Selhání získání nebo udržení zámku|
|[C26117](../code-quality/c26117.md)|Uvolnění nepotřebného zámku|
|[C26140](../code-quality/c26140.md)|Chyba anotace SAL souběžnosti|
|[C28020](../code-quality/c28020.md)|Výraz není PRAVDA na toto volání|
|[C28021](../code-quality/c28021.md)|Anotovaný parametr musí být ukazatel|
|[C28022](../code-quality/c28022.md)|Třídy funkce, které u této funkce neodpovídají třídám funkce v definici typu typedef použité pro jejich definování.|
|[C28023](../code-quality/c28023.md)|Přidělovaná nebo předávaná funkce by měly mít \_funkce\_třídy\_ anotace pro nejméně jednu|
|[C28024](../code-quality/c28024.md)|Přidělován ukazatel funkce, je opatřen poznámkou funkce třídy, která není obsažena v seznamu funkcí třídy.|
|[C28039](../code-quality/c28039.md)|Typ skutečného parametru by měl přesně odpovídat typu|
|[C28112](../code-quality/c28112.md)|Proměnná, ke kterému se přistupuje přes funkci Interlocked, musí být vždy přístupná prostřednictvím funkce Interlocked.|
|[C28113](../code-quality/c28113.md)|Přístup k místní proměnné prostřednictvím funkce Interlocked|
|[C28125](../code-quality/c28125.md)|Funkce musí být volána z v rámci bloku try / except bloku|
|[C28137](../code-quality/c28137.md)|Argument proměnné by měl být (literál) Konstanta|
|[C28138](../code-quality/c28138.md)|Konstantní argument by měl být raději proměnná|
|[C28159](../code-quality/c28159.md)|Zvažte použití jiné funkce.|
|[C28160](../code-quality/c28160.md)|Poznámka k chybě|
|[C28163](../code-quality/c28163.md)|Funkce nikdy lze volat z bloku try / except bloku|
|[C28164](../code-quality/c28164.md)|Argument je předáván funkci, která očekává ukazatel na objekt (ne ukazatel na ukazatel)|
|[C28182](../code-quality/c28182.md)|Přesměrování ukazatele NULL. Ukazatel obsahuje tutéž hodnotu NULL jako jiný ukazatel.|
|[C28183](../code-quality/c28183.md)|Argument může být jedna hodnota a je kopie hodnoty nalezené v ukazateli|
|[C28193](../code-quality/c28193.md)|Proměnná drží hodnotu, která musí být zkontrolovaná|
|[C28196](../code-quality/c28196.md)|Požadavek není splněn. (Výraz není vyhodnocen na hodnotu true.)|
|[C28202](../code-quality/c28202.md)|Neplatný odkaz na Nestatický člen|
|[C28203](../code-quality/c28203.md)|Nejednoznačný odkaz na člena třídy.|
|[C28205](../code-quality/c28205.md)|\_Úspěch\_ nebo \_na\_selhání\_ použít v neplatném kontextu|
|[C28206](../code-quality/c28206.md)|Levý operand ukazuje na strukturu, použijte "->"|
|[C28207](../code-quality/c28207.md)|Levý operand je struktura, použijte "."|
|[C28209](../code-quality/c28209.md)|Deklarace symbolu má konfliktní deklaraci|
|[C28210](../code-quality/c28210.md)|Poznámky pro kontext __on_failure nesmí být v explicitním předkontextu|
|[C28211](../code-quality/c28211.md)|Pro SAL_context se očekává název statického kontextu|
|[C28212](../code-quality/c28212.md)|Očekávaný výraz ukazatele pro poznámku|
|[C28213](../code-quality/c28213.md)|\_Použití\_decl\_poznámky\_ tak, aby odkazovaly předchozí deklarace bez jakýchkoli úprav, třeba použít poznámku.|
|[C28214](../code-quality/c28214.md)|Názvy atributových parametrů musí být p1... p9|
|[C28215](../code-quality/c28215.md)|Typefix nelze použít pro parametr, který již poznámku typefix obsahuje|
|[C28216](../code-quality/c28216.md)|Poznámka checkreturn se vztahuje pouze k následným podmínkám specifických parametrů funkcí.|
|[C28217](../code-quality/c28217.md)|Pro funkci Počet parametrů anotace neodpovídá nalezeným na souboru|
|[C28218](../code-quality/c28218.md)|Pro parametr funkce parametr poznámky se neshoduje s nalezeným na souboru|
|[C28219](../code-quality/c28219.md)|Očekávaný člen výčtu pro okomentování parametru v poznámce|
|[C28220](../code-quality/c28220.md)|Očekáván celočíselný výraz pro okomentování parametru v poznámce|
|[C28221](../code-quality/c28221.md)|Řetězcový výraz očekávaný pro parametr v poznámce|
|[C28222](../code-quality/c28222.md)|__yes \__Ne nebo \__maybe očekáván pro anotaci|
|[C28223](../code-quality/c28223.md)|Nebyl nalezen očekávaný Token/identifikátor poznámky, parametr|
|[C28224](../code-quality/c28224.md)|Poznámka vyžaduje parametry|
|[C28225](../code-quality/c28225.md)|Nalezen správný počet požadovaných parametrů v poznámce|
|[C28226](../code-quality/c28226.md)|Poznámka nemůže být také PrimOp (v aktuální deklaraci)|
|[C28227](../code-quality/c28227.md)|Poznámka nemůže být také PrimOp (viz předchozí deklarace)|
|[C28228](../code-quality/c28228.md)|Parametr poznámky: v poznámkách nelze použít typ|
|[C28229](../code-quality/c28229.md)|Poznámka nepodporuje parametry|
|[C28230](../code-quality/c28230.md)|Typ parametru nemá žádný člen.|
|[C28231](../code-quality/c28231.md)|Poznámky je platný jenom pro pole|
|[C28232](../code-quality/c28232.md)|_pre_, _post_ ani _deref_ se nepoužily pro žádnou poznámku|
|[C28233](../code-quality/c28233.md)|_pre_, _post_ ani _deref_ se použily pro blok|
|[C28234](../code-quality/c28234.md)|__at výraz se nedá použít u aktuální funkce|
|[C28235](../code-quality/c28235.md)|Funkce nemůže zůstat sama jako poznámka|
|[C28236](../code-quality/c28236.md)|Poznámka nemůže použít ve výrazu|
|[C28237](../code-quality/c28237.md)|Anotace na parametru se už nepodporuje.|
|[C28238](../code-quality/c28238.md)|Anotace na parametru má více než jednu hodnotu, stringValue a longValue. Použijte paramn = xxx|
|[C28239](../code-quality/c28239.md)|Anotace na parametru má hodnotu, stringValue nebo longValue; a paramn = xxx. Použijte pouze paramn = xxx|
|[C28240](../code-quality/c28240.md)|Anotace na parametru má param2, ale ne param1|
|[C28241](../code-quality/c28241.md)|Poznámka pro funkci na parametru nebyl rozpoznán.|
|[C28243](../code-quality/c28243.md)|Poznámka pro funkci na parametru vyžaduje více přístupů přes ukazatel, než skutečný anotovaný typ umožňuje|
|[C28244](../code-quality/c28244.md)|Poznámka pro funkci má Neanalyzovatelný parametr či externí Poznámka|
|[C28245](../code-quality/c28245.md)|Poznámka pro funkci Komentuje 'this' na jiné – členská funkce|
|[C28246](../code-quality/c28246.md)|Anotace parametru funkce neodpovídá typu parametru|
|[C28250](../code-quality/c28250.md)|Nekonzistentní Poznámka pro funkci: předchozí instanci došlo k chybě.|
|[C28251](../code-quality/c28251.md)|Nekonzistentní Poznámka pro funkci: Tato instance obsahuje chybu.|
|[C28252](../code-quality/c28252.md)|Nekonzistentní Poznámka pro funkci: parametr má v této instanci jiné anotace.|
|[C28253](../code-quality/c28253.md)|Nekonzistentní Poznámka pro funkci: parametr má v této instanci jiné anotace.|
|[C28254](../code-quality/c28254.md)|(dynamic_cast <>) není v anotacích podporována|
|[C28262](../code-quality/c28262.md)|Chyba syntaxe v poznámce byl nalezen ve funkci pro anotaci|
|[C28263](../code-quality/c28263.md)|Byla nalezena chyba syntaxe v podmíněné poznámce pro vnitřní anotaci|
|[C28267](../code-quality/c28267.md)|Poznámky v funkce byla nalezena chyba syntaxe v poznámkách.|
|[C28272](../code-quality/c28272.md)|Poznámka pro funkci, je parametr při zkoumání nekonzistentní s deklarací funkce|
|[C28273](../code-quality/c28273.md)|Pro funkci nejsou konzistentní s deklarací funkce|
|[C28275](../code-quality/c28275.md)|Parametr \_– makro\_hodnotu\_ má hodnotu null.|
|[C28279](../code-quality/c28279.md)|Pro symbol "begin" bylo nalezeno bez odpovídajícího "end"|
|[C28280](../code-quality/c28280.md)|Pro symbol bylo nalezeno "end" bez odpovídajícího "begin"|
|[C28282](../code-quality/c28282.md)|Řetězce formátu musí být v předběžných podmínkách|
|[C28285](../code-quality/c28285.md)|Pro funkci. syntaktická chyba v parametru|
|[C28286](../code-quality/c28286.md)|Pro funkci. syntaktická chyba poblíž konce|
|[C28287](../code-quality/c28287.md)|Pro funkci. Chyba syntaxe v \_na\_poznámky () (nerozeznaný název parametru)|
|[C28288](../code-quality/c28288.md)|Pro funkci. Chyba syntaxe v \_na\_poznámky () (neplatný název parametru)|
|[C28289](../code-quality/c28289.md)|Pro funkci: ReadableTo nebo writableto nebyl neměl limit specifikace jako parametr|
|[C28290](../code-quality/c28290.md)|Poznámka pro funkci obsahuje více typů External než je skutečný počet parametrů|
|[C28291](../code-quality/c28291.md)|Po null/notnull deref úroveň 0 je pro funkci bezvýznamné.|
|[C28300](../code-quality/c28300.md)|Operandy výrazu nekompatibilních typů pro operátor|
|[C28301](../code-quality/c28301.md)|Žádné poznámky pro první deklaraci funkce.|
|[C28302](../code-quality/c28302.md)|Speciální \_Deref\_ v poznámce byl nalezen operátor.|
|[C28303](../code-quality/c28303.md)|Nejednoznačný \_Deref\_ v poznámce byl nalezen operátor.|
|[C28304](../code-quality/c28304.md)|Nesprávně umístěný \_Notref\_ byl nalezen operátor použitý na token.|
|[C28305](../code-quality/c28305.md)|Zjistila se chyba při analýze tokenu.|
|[C28306](../code-quality/c28306.md)|Anotace na parametru je zastaralá|
|[C28307](../code-quality/c28307.md)|Anotace na parametru je zastaralá|
|[C28350](../code-quality/c28350.md)|Poznámka popisuje situaci, která není podmíněně použitelná.|
|[C28351](../code-quality/c28351.md)|Poznámka popisuje, kde dynamickou hodnotu (proměnnou) nelze použít v podmínce.|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, které vlastní uvolnitelné pole by měly být uvolnitelné|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Deklarujte správně obslužné rutiny událostí|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Označte sestavení pomocí atributu AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Metody rozhraní by měla být volatelné podřízenými typy|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Typy, které vlastní nativní prostředky by měly být uvolnitelné|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Přesuňte volání nespravovaných kódů do třídy NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Neskrývejte metody třídy base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementuje správně IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Nevyvolávejte výjimky v neočekávaných umístěních|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Vyhněte se duplicitním akcelerátorům|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Vstupní body volání nespravovaného by měly existovat|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Volání nespravovaných kódů by neměly být viditelné|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Typy automatického rozložení by neměly být viditelné modelu COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Volejte GetLastError ihned po volání nespravovaného kódu|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Základní typy viditelného typu modelu COM by měly být viditelné modelu COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Metody registrace modelu COM by si měly odpovídat|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Deklarujte správně volání nespravovaných kódů|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Odstraňte prázdné finalizační metody|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Pole hodnot by měla být přenosná|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Deklarace volání nespravovaného kódu by měla být přenosná|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Nepoužívejte zámky na objekty se slabou identitou|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Zkontrolujte dotazy SQL pro chyby zabezpečení|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Určete zařazování pro argumenty řetězce volání nespravovaného|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Revize deklarativních zabezpečení na hodnotách|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Ukazatelé by neměli být viditelné|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Zabezpečené typy by neměly vystavovat pole|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Zabezpečení metody by mělo být nadmnožinou typu|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Metody APTCA by měly volat pouze metody APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Typy APTCA by měl rozšířit pouze základní typy APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Nezveřejňujte nepřímo metody s požadavky propojení|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Požadavky na přepsání odkazu musejí být identické s bází|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Zabalte ohroženou klauzuli finally do vnějšího bloku try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Požadavky propojení typů vyžadují dědičnost požadavků|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Typy kritické pro zabezpečení nemusejí podporovat účast na ekvivalenci typů|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Výchozí konstruktory nesmějí být kritické jako výchozí konstruktory základního typu|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegáti musí mít vazbu k metodám s konzistentní transparentností|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Metody musejí při přepisování základních metod zachovávat konzistentní transparentnost|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Transparentní metody musejí obsahovat pouze ověřitelné IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Transparentní metody nesmějí volat metody s atributem suppressunmanagedcodesecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Transparentní kód nesmí odkazovat na položky kritické pro zabezpečení|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Transparentní metody nesmějí vyhovovat LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Typy musí být alespoň tak kritický jako jeho základní typy a rozhraní|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Transparentní metody nemusejí podporovat použití zabezpečení nepodmíněné výrazy|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Transparentní metody nesmějí provádět volání do nativního kódu|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Znovu vyvolejte pro zachování podrobností zásobníku|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Neuvolňujte objekty několikrát|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inicializujte vloženou hodnotu statických polí|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Neoznačujte obsluhované součásti pomocí WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Uvolnitelné pole by mělo být uvolněno|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Nevolejte přepisovatelné metody v konstruktorech|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Uvolnitelné typy by měly deklarovat finalizační metodu|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Finalizační metody by měly volat finalizační metodu třídy base|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementovat Serializační konstruktory|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Přetižte operátor equals při přepsání ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Vstupní body označit Windows Forms pomocí STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Označte všechna neserializovatelná pole|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Volání metody třídy base na typech ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Označte typy ISerializable pomocí SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementujte správně metody serializace|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementujte správně ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Poskytněte správné argumenty metodě formátování|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Testujte správně NaN|