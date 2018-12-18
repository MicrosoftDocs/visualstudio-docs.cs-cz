---
title: Sada pravidel nativní minimální pravidla | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ca97fa7d4e3b78077e50a2039647afd5c380ebd3
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389423"
---
# <a name="native-minimum-rules-rule-set"></a>Sada pravidel Nativní minimální pravidla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nativní minimální pravidla společnosti Microsoft se soustředí na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a selhání aplikace. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše nativní projekty.  


|                                      Pravidlo                                      |                                                  Popis                                                  |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
|                       [C6001](../code-quality/c6001.md)                        |                                          Použití neinicializované paměti                                           |
|                       [C6011](../code-quality/c6011.md)                        |                                          Přesměrování ukazatele Null                                           |
|                       [C6029](../code-quality/c6029.md)                        |                                            Použití nezkontrolované hodnoty                                             |
|                       [C6053](../code-quality/c6053.md)                        |                                          Ukončeno nulou z volání                                           |
|                       [C6059](../code-quality/c6059.md)                        |                                               Špatné zřetězení                                               |
|                       [C6063](../code-quality/c6063.md)                        |                                  Chybí Argument řetězce pro formátování funkce                                   |
|                       [C6064](../code-quality/c6064.md)                        |                                  Pro naformátování funkce chybí Argument typu celé číslo                                  |
|                       [C6066](../code-quality/c6066.md)                        |                                  Pro naformátování funkce chybí Argument typu ukazatel                                  |
|                       [C6067](../code-quality/c6067.md)                        |                              Chybí Argument typu ukazatel řetězce pro formátování funkce                               |
|                       [C6101](../code-quality/c6101.md)                        |                                        Vrácení neinicializované paměti                                         |
|                       [C6200](../code-quality/c6200.md)                        |                                         Index přesáhl vyrovnávací paměti                                          |
|                       [C6201](../code-quality/c6201.md)                        |                                      Index přesáhl vyrovnávací paměti zásobníku                                       |
|                       [C6270](../code-quality/c6270.md)                        |                                   Chybí Argument typu Float pro formátování funkce                                   |
|                       [C6271](../code-quality/c6271.md)                        |                                       Nadbytečný Argument pro formátování funkce                                       |
|                       [C6272](../code-quality/c6272.md)                        |                                     Argument než typu Float pro formátování funkce                                     |
|                       [C6273](../code-quality/c6273.md)                        |                                    Pro naformátování funkce Argument jiných než celých čísel                                     |
|                       [C6274](../code-quality/c6274.md)                        |                                   Argument bez znaků pro formátování funkce                                   |
|                       [C6276](../code-quality/c6276.md)                        |                                              Neplatné přetypování řetězce                                              |
|                       [C6277](../code-quality/c6277.md)                        |                                          Neplatné volání funkce CreateProcess                                           |
|                       [C6284](../code-quality/c6284.md)                        |                                  Neplatný Argument objektu pro formátování funkce                                   |
|                       [C6290](../code-quality/c6290.md)                        |                                      Bitový logický operátor Not- a určování priorit                                       |
|                       [C6291](../code-quality/c6291.md)                        |                                       Bitový logický operátor Not- nebo Priorita                                       |
|                       [C6302](../code-quality/c6302.md)                        |                             Neplatný Argument řetězec znaků pro formátování funkce                              |
|                       [C6303](../code-quality/c6303.md)                        |                           Neplatný širokého znaku řetězcový Argument pro formátování funkce                           |
|                       [C6305](../code-quality/c6305.md)                        |                                         Neshoda velikosti a počtu používání                                         |
|                       [C6306](../code-quality/c6306.md)                        |                                   Volání funkce nesprávné argumentů s proměnnou délkou                                   |
|                       [C6328](../code-quality/c6328.md)                        |                                       Možná Neshoda typu argumentu                                        |
|                       [C6385](../code-quality/c6385.md)                        |                                                 Přetečení čtení                                                  |
|                       [C6386](../code-quality/c6386.md)                        |                                                 Přetečení zápisu                                                 |
|                       [C6387](../code-quality/c6387.md)                        |                                            Neplatná hodnota parametru                                            |
|                       [C6500](../code-quality/c6500.md)                        |                                          Neplatná vlastnost atributu                                           |
|                       [C6501](../code-quality/c6501.md)                        |                                     Konfliktní hodnotami vlastností atributu                                     |
|                       [C6503](../code-quality/c6503.md)                        |                                           Odkazy nesmí mít hodnotu Null                                           |
|                       [C6504](../code-quality/c6504.md)                        |                                              Null na typech bez ukazatele                                              |
|                       [C6505](../code-quality/c6505.md)                        |                                               Vlastnost MustCheck na typ Void                                               |
|                       [C6506](../code-quality/c6506.md)                        |                                      Velikost vyrovnávací paměti na typech bez ukazatele nebo pole                                      |
| [C6507](http://msdn.microsoft.com/en-us/18f88cd1-d035-4403-a6a4-12dd0affcf21)  |                                       Null Neshoda v přístupu přes ukazatel nula                                       |
|                       [C6508](../code-quality/c6508.md)                        |                                           K zápisu na konstantě                                            |
|                       [C6509](../code-quality/c6509.md)                        |                                          Návratová hodnota použita na předpokladu                                          |
|                       [C6510](../code-quality/c6510.md)                        |                                        NULL byl ukončen na typech bez ukazatele                                         |
|                       [C6511](../code-quality/c6511.md)                        |                                          MustCheck musí nabývat hodnot Ano nebo ne                                          |
|                       [C6513](../code-quality/c6513.md)                        |                                       Velikost prvku bez velikosti vyrovnávací paměti                                        |
|                       [C6514](../code-quality/c6514.md)                        |                                        Velikost vyrovnávací paměti překračuje velikost pole                                         |
|                       [C6515](../code-quality/c6515.md)                        |                                          Velikost vyrovnávací paměti na typech bez ukazatele                                           |
|                       [C6516](../code-quality/c6516.md)                        |                                          Atribut nemá žádné vlastnosti                                           |
|                       [C6517](../code-quality/c6517.md)                        |                                       Platná velikost pro vyrovnávací paměť bez možnosti čtení                                       |
|                       [C6518](../code-quality/c6518.md)                        |                                     Zapisovatelná velikost pro vyrovnávací paměť, Nezapisovatelný                                      |
| [C6519](http://msdn.microsoft.com/en-us/2b6326b0-0539-4d26-8fb1-720114933232)  |                  Neplatná Poznámka: hodnota vlastnosti 'NeedsRelease' musí být Ano nebo ne                   |
| [C6521](http://msdn.microsoft.com/en-us/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)  |                                        Neplatná velikost řetězce přistoupit přes ukazatel                                        |
|                       [C6522](../code-quality/c6522.md)                        |                                           Typ řetězec neplatné velikosti                                            |
| [C6523](http://msdn.microsoft.com/en-us/11397a31-b224-46b0-afb7-d49ca576a3bb)  |                                         Neplatná velikost parametru řetězce                                         |
|                       [C6525](../code-quality/c6525.md)                        |                                   Neplatná velikost řetězce-nedosažitelná oblast                                    |
| [C6526](http://msdn.microsoft.com/en-us/59c590c7-0098-4166-a1ac-87f324596002)  |                                        Typ vyrovnávací paměti pro řetězec neplatné velikosti                                        |
|                       [C6527](../code-quality/c6527.md)                        |              Neplatná Poznámka: vlastnost 'NeedsRelease' nesmí být použita pro hodnoty typu void               |
|                       [C6530](../code-quality/c6530.md)                        |                                       Nerozpoznaný styl řetězce formátu                                        |
|                       [C6540](../code-quality/c6540.md)                        | Použití poznámek atributu na této funkci způsobí neplatnost všech existujících poznámek __declspec  |
|                       [C6551](../code-quality/c6551.md)                        |                              Neplatná specifikace velikosti: výraz není analyzovatelný                              |
|                       [C6552](../code-quality/c6552.md)                        |                              Neplatná specifikace Deref = nebo Notref =: výraz není analyzovatelný                               |
|                       [C6701](../code-quality/c6701.md)                        |                                  Hodnota není platná hodnota Ano/Ne/možná                                  |
|                       [C6702](../code-quality/c6702.md)                        |                                        Hodnota není hodnota řetězce                                        |
|                       [C6703](../code-quality/c6703.md)                        |                                           Hodnota není číslo                                           |
|                       [C6704](../code-quality/c6704.md)                        |                                    Neočekávaná chyba výrazu                                     |
|                       [C6705](../code-quality/c6705.md)                        |     Očekávaný počet argumentů pro anotaci se neshoduje s aktuální počet argumentů pro anotaci      |
|                       [C6706](../code-quality/c6706.md)                        |                                  Neočekávaná chyba poznámky                                   |
|                      [C28021](../code-quality/c28021.md)                       |                                Anotovaný parametr musí být ukazatel                                |
|                      [C28182](../code-quality/c28182.md)                       |         Přesměrování ukazatele NULL. Ukazatel obsahuje tutéž hodnotu NULL jako jiný ukazatel.          |
|                      [C28202](../code-quality/c28202.md)                       |                                    Neplatný odkaz na Nestatický člen                                     |
|                      [C28203](../code-quality/c28203.md)                       |                                     Nejednoznačný odkaz na člena třídy.                                      |
|                      [C28205](../code-quality/c28205.md)                       |                           \_Úspěch\_ nebo \_On_failure\_ použít v neplatném kontextu                            |
|                      [C28206](../code-quality/c28206.md)                       |                                   Levý operand ukazuje na strukturu, použijte "->"                                   |
|                      [C28207](../code-quality/c28207.md)                       |                                       Levý operand je struktura, použijte "."                                       |
|                      [C28210](../code-quality/c28210.md)                       |                 Poznámky pro kontext __on_failure nesmí být v explicitním předkontextu                  |
|                      [C28211](../code-quality/c28211.md)                       |                                 Pro SAL_context se očekává název statického kontextu                                  |
|                      [C28212](../code-quality/c28212.md)                       |                                  Očekávaný výraz ukazatele pro poznámku                                   |
|                      [C28213](../code-quality/c28213.md)                       | \_Use_decl_annotations\_ tak, aby odkazovaly předchozí deklarace bez jakýchkoli úprav, třeba použít poznámku. |
|                      [C28214](../code-quality/c28214.md)                       |                                   Názvy atributových parametrů musí být p1... p9                                   |
|                      [C28215](../code-quality/c28215.md)                       |                    Typefix nelze použít pro parametr, který již poznámku typefix obsahuje                    |
|                      [C28216](../code-quality/c28216.md)                       |        Poznámka checkreturn se vztahuje pouze k následným podmínkám specifických parametrů funkcí.         |
|                      [C28217](../code-quality/c28217.md)                       |            Pro funkci Počet parametrů anotace neodpovídá nalezeným na souboru             |
|                      [C28218](../code-quality/c28218.md)                       |             Pro parametr funkce parametr poznámky se neshoduje s nalezeným na souboru              |
|                      [C28219](../code-quality/c28219.md)                       |                 Očekávaný člen výčtu pro okomentování parametru v poznámce                 |
|                      [C28220](../code-quality/c28220.md)                       |                  Očekáván celočíselný výraz pro okomentování parametru v poznámce                   |
|                      [C28221](../code-quality/c28221.md)                       |                        Řetězcový výraz očekávaný pro parametr v poznámce                         |
|                      [C28222](../code-quality/c28222.md)                       |                               __yes \__Ne nebo \__maybe očekáván pro anotaci                               |
|                      [C28223](../code-quality/c28223.md)                       |                       Nebyl nalezen očekávaný Token/identifikátor poznámky, parametr                        |
|                      [C28224](../code-quality/c28224.md)                       |                                        Poznámka vyžaduje parametry                                         |
|                      [C28225](../code-quality/c28225.md)                       |                     Nalezen správný počet požadovaných parametrů v poznámce                      |
|                      [C28226](../code-quality/c28226.md)                       |                          Poznámka nemůže být také PrimOp (v aktuální deklaraci)                          |
|                      [C28227](../code-quality/c28227.md)                       |                          Poznámka nemůže být také PrimOp (viz předchozí deklarace)                           |
|                      [C28228](../code-quality/c28228.md)                       |                             Parametr poznámky: v poznámkách nelze použít typ                              |
|                      [C28229](../code-quality/c28229.md)                       |                                    Poznámka nepodporuje parametry                                     |
|                      [C28230](../code-quality/c28230.md)                       |                                     Typ parametru nemá žádný člen.                                      |
|                      [C28231](../code-quality/c28231.md)                       |                                       Poznámky je platný jenom pro pole                                       |
|                      [C28232](../code-quality/c28232.md)                       |                               _pre_, _post_ ani _deref_ se nepoužily pro žádnou poznámku                               |
|                      [C28233](../code-quality/c28233.md)                       |                                    _pre_, _post_ ani _deref_ se použily pro blok                                     |
|                      [C28234](../code-quality/c28234.md)                       |                              __at výraz se nedá použít u aktuální funkce                               |
|                      [C28235](../code-quality/c28235.md)                       |                               Funkce nemůže zůstat sama jako poznámka                                |
|                      [C28236](../code-quality/c28236.md)                       |                                Poznámka nemůže použít ve výrazu                                 |
|                      [C28237](../code-quality/c28237.md)                       |                              Anotace na parametru se už nepodporuje.                               |
|                      [C28238](../code-quality/c28238.md)                       |      Anotace na parametru má více než jednu hodnotu, stringValue a longValue. Použijte paramn = xxx       |
|                      [C28239](../code-quality/c28239.md)                       |  Anotace na parametru má hodnotu, stringValue nebo longValue; a paramn = xxx. Použijte pouze paramn = xxx   |
|                      [C28240](../code-quality/c28240.md)                       |                             Anotace na parametru má param2, ale ne param1                              |
|                      [C28241](../code-quality/c28241.md)                       |                          Poznámka pro funkci na parametru nebyl rozpoznán.                           |
|                      [C28243](../code-quality/c28243.md)                       |   Poznámka pro funkci na parametru vyžaduje více přístupů přes ukazatel, než skutečný anotovaný typ umožňuje   |
|                      [C28245](../code-quality/c28245.md)                       |                     Poznámka pro funkci Komentuje 'this' na jiné – členská funkce                     |
|                      [C28246](../code-quality/c28246.md)                       |                Anotace parametru funkce neodpovídá typu parametru                 |
|                      [C28250](../code-quality/c28250.md)                       |                    Nekonzistentní Poznámka pro funkci: předchozí instanci došlo k chybě.                     |
|                      [C28251](../code-quality/c28251.md)                       |                       Nekonzistentní Poznámka pro funkci: Tato instance obsahuje chybu.                       |
|                      [C28252](../code-quality/c28252.md)                       |           Nekonzistentní Poznámka pro funkci: parametr má v této instanci jiné anotace.           |
|                      [C28253](../code-quality/c28253.md)                       |           Nekonzistentní Poznámka pro funkci: parametr má v této instanci jiné anotace.           |
|                      [C28254](../code-quality/c28254.md)                       |                               (dynamic_cast <>) není v anotacích podporována                                |
|                      [C28262](../code-quality/c28262.md)                       |                    Chyba syntaxe v poznámce byl nalezen ve funkci pro anotaci                     |
|                      [C28263](../code-quality/c28263.md)                       |                 Byla nalezena chyba syntaxe v podmíněné poznámce pro vnitřní anotaci                 |
| [C28264](http://msdn.microsoft.com/en-us/bf6ea983-a06e-4752-a042-747a7dbf338c) |                                    Výsledné hodnoty seznamů musí být konstanty.                                     |
|                      [C28267](../code-quality/c28267.md)                       |                    Poznámky v funkce byla nalezena chyba syntaxe v poznámkách.                    |
|                      [C28272](../code-quality/c28272.md)                       |      Poznámka pro funkci, je parametr při zkoumání nekonzistentní s deklarací funkce      |
|                      [C28273](../code-quality/c28273.md)                       |                    Pro funkci nejsou konzistentní s deklarací funkce                     |
|                      [C28275](../code-quality/c28275.md)                       |                                   Parametr \_Macro_value\_ má hodnotu null.                                    |
|                      [C28279](../code-quality/c28279.md)                       |                           Pro symbol "begin" bylo nalezeno bez odpovídajícího "end"                            |
|                      [C28280](../code-quality/c28280.md)                       |                           Pro symbol bylo nalezeno "end" bez odpovídajícího "begin"                           |
|                      [C28282](../code-quality/c28282.md)                       |                                    Řetězce formátu musí být v předběžných podmínkách                                    |
|                      [C28285](../code-quality/c28285.md)                       |                                    Pro funkci. syntaktická chyba v parametru                                    |
|                      [C28286](../code-quality/c28286.md)                       |                                    Pro funkci. syntaktická chyba poblíž konce                                    |
|                      [C28287](../code-quality/c28287.md)                       |                Pro funkci. Chyba syntaxe v \_na\_poznámky () (nerozeznaný název parametru)                |
|                      [C28288](../code-quality/c28288.md)                       |                  Pro funkci. Chyba syntaxe v \_na\_poznámky () (neplatný název parametru)                   |
|                      [C28289](../code-quality/c28289.md)                       |                Pro funkci: ReadableTo nebo writableto nebyl neměl limit specifikace jako parametr                |
|                      [C28290](../code-quality/c28290.md)                       |           Poznámka pro funkci obsahuje více typů External než je skutečný počet parametrů            |
|                      [C28291](../code-quality/c28291.md)                       |                        Po null/notnull deref úroveň 0 je pro funkci bezvýznamné.                        |
|                      [C28300](../code-quality/c28300.md)                       |                            Operandy výrazu nekompatibilních typů pro operátor                             |
|                      [C28301](../code-quality/c28301.md)                       |                               Žádné poznámky pro první deklaraci funkce.                               |
|                      [C28302](../code-quality/c28302.md)                       |                             Speciální \_Deref\_ v poznámce byl nalezen operátor.                              |
|                      [C28303](../code-quality/c28303.md)                       |                           Nejednoznačný \_Deref\_ v poznámce byl nalezen operátor.                            |
|                      [C28304](../code-quality/c28304.md)                       |                     Nesprávně umístěný \_Notref\_ byl nalezen operátor použitý na token.                      |
|                      [C28305](../code-quality/c28305.md)                       |                                Zjistila se chyba při analýze tokenu.                                 |
|                      [C28350](../code-quality/c28350.md)                       |                  Poznámka popisuje situaci, která není podmíněně použitelná.                   |
|                      [C28351](../code-quality/c28351.md)                       |         Poznámka popisuje, kde dynamickou hodnotu (proměnnou) nelze použít v podmínce.          |

