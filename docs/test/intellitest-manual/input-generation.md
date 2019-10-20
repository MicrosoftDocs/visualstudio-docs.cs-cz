---
title: Dynamické symbolické spuštění | Nástroj Microsoft IntelliTest Developer test Tool
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 26befe6612c874c2565e44459cc90fe980296137
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653190"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Generování vstupu s použitím dynamického symbolického spuštění

IntelliTest generuje vstupy pro [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing) analýzou podmínek větve v programu. Testovací vstupy se volí na základě toho, jestli můžou aktivovat nové chování větvení programu. Analýza je přírůstkový proces. Přejemnoá `q: I -> {true, false}` predikáty přes zkušební parametry formálního testu `I`. `q` představuje sadu chování, které IntelliTest již pozorován. Zpočátku `q := false`, protože ještě není nic pozorováno.

Kroky smyčky jsou:

1. IntelliTest určuje vstupy `i` tak, aby `q(i)=false` pomocí [řešitele omezení](#constraint-solver). V rámci konstrukce vstupní `i` převezme cestu spuštění, která se nezobrazuje předtím. Zpočátku to znamená, že `i` může být jakýkoli vstup, protože ještě nebyla zjištěna žádná cesta spuštění.

1. IntelliTest spustí test s vybraným vstupním `i` a monitoruje provádění testu a testovaného programu.

1. Během provádění program převezme určitou cestu, která je určena všemi podmíněnými větvemi programu. Sada všech podmínek, které určují provedení, se nazývá podmínka pro *cestu*, která se zapsala jako predikát `p: I -> {true, false}` přes formální vstupní parametry. IntelliTest vypočítává reprezentace tohoto predikátu.

1. IntelliTest sady `q := (q or p)`. Jinými slovy se zaznamená fakt, že se zobrazila cesta reprezentovaná `p`.

1. Přejít ke kroku 1.

[Řešitel omezení](#constraint-solver) IntelliTest může řešit hodnoty všech typů, které se mohou objevit v programech .NET:

* [Celá čísla](#integers-and-floats) a [Floaty](#integers-and-floats)
* [Objekty](#objects)
* [Struktury](#structs)
* [Pole](#arrays-and-strings) a [řetězce](#arrays-and-strings)

IntelliTest filtruje vstupy, které porušují uvedené předpoklady.

Kromě okamžitých vstupů (argumenty pro [parametrizované testy jednotek](test-generation.md#parameterized-unit-testing)) může test nakreslit další vstupní hodnoty ze statické třídy [PexChoose](static-helper-classes.md#pexchoose) . Volby také určují chování [parametrizovaných modelů](#parameterized-mocks).

## <a name="constraint-solver"></a>Řešitel omezení

IntelliTest používá Řešitel omezení k určení relevantních vstupních hodnot testu a testovaného programu.

IntelliTest používá Řešitel omezení [Z3](https://github.com/Z3Prover/z3/wiki) .

## <a name="dynamic-code-coverage"></a>Dynamické pokrytí kódu

V důsledku vedlejšího účinku monitorování za běhu shromažďuje IntelliTest data o rozsahu dynamických kódů.
Tato možnost se nazývá *Dynamická* , protože IntelliTest ví pouze o kódu, který byl proveden, proto nemůže poskytnout absolutní hodnoty pro pokrytí stejným způsobem jako jiný nástroj pokrytí obvykle.

Například když IntelliTest nahlásí dynamické pokrytí jako 5/10 základních bloků, znamená to, že se pokrylo pět bloků z deseti, kde celkový počet bloků ve všech metodách, které byly doposud dosaženy analýzou (na rozdíl od všech metod, které existují v a sestavení v rámci testu) je deset.
V důsledku toho, že se při analýze objeví více dosažitelných metod, může se zvýšit čitatel (5 v tomto příkladu) a jmenovatel (10).

## <a name="integers-and-floats"></a>Celá čísla a Floaty

[Řešitel omezení](#constraint-solver) IntelliTest určuje vstupní hodnoty testů primitivních typů, jako je **Byte**, **int**, **float**a další, aby se aktivovaly různé cesty spuštění pro test a testovaný program.

## <a name="objects"></a>Objekty

IntelliTest může buď [vytvořit instance existující třídy .NET](#existing-classes), nebo můžete použít IntelliTest k automatickému [vytváření objektů](#parameterized-mocks) , které implementují konkrétní rozhraní a chovají se různými způsoby v závislosti na využití.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Vytvoření instance existujících tříd

**Jaký je problém?**

IntelliTest sleduje spuštěné instrukce, když spustí test a testovaný program. Konkrétně sleduje veškerý přístup k polím. Pak pomocí [řešitele omezení](#constraint-solver) určí nové vstupy testu, včetně objektů a jejich hodnot polí, což znamená, že se test a testovaný program chová jiným zajímavým způsobem.

To znamená, že IntelliTest musí vytvořit objekty určitých typů a nastavit jejich hodnoty polí. Pokud je třída [viditelná](#visibility) a má [viditelný](#visibility) výchozí konstruktor, IntelliTest může vytvořit instanci třídy.
Pokud jsou všechna pole třídy [viditelná](#visibility), může IntelliTest nastavit pole automaticky.

Pokud typ není viditelný nebo pokud nejsou pole [viditelná](#visibility), IntelliTest potřebuje pomáhat při vytváření objektů a jejich přenesení do zajímavých stavů, aby bylo dosaženo maximálního pokrytí kódu. IntelliTest může pomocí reflexe vytvořit a inicializovat instance v libovolných způsobech, ale to není obvykle žádoucí, protože může objekt převést do stavu, který nemůže nikdy nastat během normálního provádění programu. Místo toho IntelliTest spoléhá na Rady od uživatele.

## <a name="visibility"></a>Viditelnost

.NET má model podrobné viditelnosti: typy, metody, pole a další členy můžou být **soukromé**, **veřejné**, **interní**a další.

Když IntelliTest generuje testy, pokusí se provést pouze akce (například volající konstruktory, metody a nastavení polí), které jsou platné s ohledem na pravidla viditelnosti .NET v rámci kontextu vygenerovaných testů.

Pravidla jsou následující:

* **Viditelnost vnitřních členů**
  * IntelliTest předpokládá, že vygenerované testy budou mít přístup k interním členům viditelným pro nadřazené [PexClass](attribute-glossary.md#pexclass).
  Rozhraní .NET má **InternalsVisibleToAttribute** , aby rozšířila viditelnost vnitřních členů na jiná sestavení.

* **Viditelnost soukromých a rodinných (chráněných C#v) členů [PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest vždy umístí vygenerované testy přímo do [PexClass](attribute-glossary.md#pexclass) nebo do podtřídy. Proto IntelliTest předpokládá, že může používat všechny viditelné členy rodiny (**chráněno** v C#).
  * Pokud jsou vygenerované testy umístěny přímo do [PexClass](attribute-glossary.md#pexclass) (obvykle pomocí částečných tříd), IntelliTest předpokládá, že může také použít všechny soukromé členy [PexClass](attribute-glossary.md#pexclass).

* **Viditelnost veřejných členů**
  * IntelliTest předpokládá, že může používat všechny exportované členy viditelné v kontextu [PexClass](attribute-glossary.md#pexclass).

## <a name="parameterized-mocks"></a>Parametrizované modely

Jak testovat metodu, která má parametr typu rozhraní? Nebo nezapečetěné třídy? IntelliTest neví, které implementace budou později použity při volání této metody. A možná není ani skutečná implementace dostupná v době testování.

Konvenční odpověď je použít *objekty* s explicitním chováním.

Objekt typu Object implementuje rozhraní (nebo rozšiřuje třídu, která není zapečetěná). Nepředstavuje skutečnou implementaci, ale pouze zástupce, který umožňuje spuštění testů pomocí objektu Object. Jeho chování je definováno ručně v rámci každého testovacího případu, kde je použito. Existuje mnoho nástrojů, které usnadňují definování objektů a jejich očekávané chování, ale toto chování je ještě nutné definovat ručně.

Namísto pevně zakódovaných hodnot v objektech kresby může IntelliTest vygenerovat hodnoty. Stejně jako umožňuje [parametrizované testování částí](test-generation.md#parameterized-unit-testing), IntelliTest také povoluje parametrizované modely.

Parametrizované modely mají dva různé režimy spuštění:

* **Volba**: při prozkoumávání kódu jsou parametrizované modely zdrojem dalších testovacích vstupů a IntelliTest se pokusí zvolit zajímavé hodnoty.
* **přehrání**: při provádění dřív generovaného testu se parametrizované modely chovají jako zástupné procedury s chováním (jinými slovy, předdefinované chování).

Použijte [PexChoose](static-helper-classes.md#pexchoose) k získání hodnot pro parametrizované modely.

## <a name="structs"></a>Struktury

IntelliTest z hlediska hodnot **struktury** je podobný způsobu, jakým pracuje s [objekty](#objects).

## <a name="arrays-and-strings"></a>Pole a řetězce

IntelliTest sleduje spuštěné instrukce při spuštění testu a testovaného programu. Konkrétně sleduje, kdy program závisí na délce řetězce nebo pole (a dolní meze a délky multidimenzionálního pole).
Také sleduje, jak program používá různé prvky řetězce nebo pole. Pak pomocí [řešitele omezení](#constraint-solver) určí, které délky a hodnoty prvků mohou způsobit, že se test a testovaný program chová zajímavým způsobem.

IntelliTest se pokusí minimalizovat velikost polí a řetězců potřebných ke spuštění zajímavého chování programu.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Získat další vstupy

Statickou třídu [PexChoose](static-helper-classes.md#pexchoose) lze použít k získání dalších vstupů k testu a lze ji použít k implementaci [parametrizovaných modelů](#parameterized-mocks).

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Publikujte své nápady a žádosti o funkce na [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="further-reading"></a>Další čtení

* [Jak to funguje?](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)