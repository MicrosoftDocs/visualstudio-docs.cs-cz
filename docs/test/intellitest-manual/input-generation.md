---
title: Dynamické symbolické spuštění | Nástroj pro testování Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 33bd31c59de85f70d653d2de912b8c9bc5bb0e30
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295888"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Vstupní generování pomocí dynamické symbolické spuštění

IntelliTest generuje vstupy pro [parametrizované testy částí](test-generation.md#parameterized-unit-testing) díky analýze podmíněného vytváření větve v programu. Testovací vstupy jsou zvolili podle toho, jestli můžete aktivovat nové chování větvení programu. Analýza je přírůstkové proces. Zpřesnění predikát **Otázka: mohu -> {true, false}** přes formální vstupní parametry testu **můžu**. **q** představuje sadu chování, které již IntelliTest sledoval. Na začátku **q: = false**, protože nic ještě pozorováno.

Kroky smyčky jsou:

1. IntelliTest určuje vstupy **můžu** tak, aby **q (i) = false** pomocí [Řešitel omezení](#constraint-solver). 
   Pomocí vytváření, vstup **můžu** bude trvat cestu k provádění není online. Zpočátku to znamená, že **můžu** může být jakýkoli vstup, protože žádná cesta provedení ještě nebyla zjištěná.

1. IntelliTest spustí test s vybraným vstup **můžu**a sleduje spuštění testu a testovaném programu.

1. Během provádění program přebere konkrétní cestu, která je určená podmínkových větví program. Sada všechny podmínky, které určují, provádění se nazývá *podmínka cesty*napsaných jako predikát **p: můžu -> {true, false}** přes formální vstupní parametry. IntelliTest vypočítá reprezentace Tento predikát.

1. IntelliTest sady **q: = (q nebo p)**. Jinými slovy, zaznamenává skutečnost, že zaznamenal cesty představované **p**.

1. Přejděte ke kroku 1.

IntelliTest společnosti [Řešitel omezení](#constraint-solver) můžete vyřešit hodnoty všech typů, které se mohou objevit v aplikacích .NET:

* [Celá čísla](#integers-and-floats) a [čísel s plovoucí čárkou](#integers-and-floats)
* [Objekty](#objects)
* [Struktury](#structs)
* [Pole](#arrays-and-strings) a [řetězce](#arrays-and-strings)

IntelliTest filtruje vstupy, které porušují uvedené předpoklady.

Kromě okamžité vstupy (argumenty [parametrizované testy částí](test-generation.md#parameterized-unit-testing)), testu můžete nakreslit další vstupní hodnoty z [PexChoose](static-helper-classes.md#pexchoose) statické třídě. Volby taky určit chování [parametrizované mocks](#parameterized-mocks).

<a name="constraint-solver"></a>
## <a name="constraint-solver"></a>Řešitel omezení

IntelliTest Řešitel omezení používá k určení vstupní hodnoty testu a testovaném programu.

IntelliTest používá [Z3](https://github.com/Z3Prover/z3/wiki) Řešitel omezení.

<a name="dynamic-code-coverage"></a>
## <a name="dynamic-code-coverage"></a>Dynamický kód pokrytí

IntelliTest jako vedlejší efekt modulu runtime, monitorování, shromažďuje data o pokrytí kódu dynamické. Tento postup se nazývá *dynamické* protože IntelliTest ví pouze o kód, který byl proveden, proto ji nelze udělit absolutní hodnoty pro pokrytí stejným způsobem jako jiný nástroj pokrytí obvykle. 

Například když IntelliTest hlásí dynamické pokrytí jako základní bloky 5/10, to znamená, že pět bloků mimo deset byly pokryty, kde celkový počet bloků v všechny metody, které jste zatím přejít pomocí analýzy (na rozdíl od všech metod, které existují v sestavení v rámci testu) je deset.
Dále v analýzu, jako jsou dostupné další metody zjištění obou čítači (5 v tomto příkladu) a může zvýšit jmenovatel (10).

<a name="integers-and-floats"></a>
## <a name="integers-and-floats"></a>Celá čísla a float

IntelliTest společnosti [Řešitel omezení](#constraint-solver) určuje testovací vstupní hodnoty primitivních elementů typů, jako **bajtů**, **int**, **float**a dalšími lidmi v pořadí pro aktivaci různých pracovních cesty pro tento test a testovaném programu.

<a name="objects"></a>
## <a name="objects"></a>Objekty

IntelliTest můžete buď [vytvořit instance existujících tříd .NET](#existing-classes), nebo můžete pomocí funkce IntelliTest k automaticky [vytvořit mock objektů](#parameterized-mocks) , který konkrétní rozhraní a chovají různě v závislosti na využití.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Vytvoření instance existujících tříd

**V čem je problém?**

IntelliTest monitoruje prováděnou pokyny při spuštění testu a testovaném programu. Konkrétně se monitoruje veškerý přístup k polím. Poté použije [Řešitel omezení](#constraint-solver) k určení nové vstupů test, včetně objektů a jejich hodnoty pole tak, aby test a testovaném programu se bude chovat jinak zajímavé.

To znamená, že IntelliTest musí k vytvoření určité typy objektů a nastavení jejich hodnot pole. Pokud je třída [viditelné](#visibility) a má [viditelné](#visibility) výchozí konstruktor, inteligentní testování můžete vytvořit instanci třídy.
Pokud jsou všechna pole třídy [viditelné](#visibility), Intellitestu automaticky nastavit pole.

Pokud typ není viditelný, nebo pole nejsou [viditelné](#visibility), Intellitestu potřebuje nápovědu k vytvoření objektů a přiřaďte je do zajímavého stavů, abyste dosáhli pokrytí kódu maximální. IntelliTest použít k vytváření a inicializace instancí libovolně reflexe, ale to většinou není  
žádoucí, protože to může být přenese objekt do stavu, ve kterém může nikdy dojít během provádění programu normální. IntelliTest se místo toho spoléhá na pomocné parametry od uživatele.

<a name="visibility"></a>
## <a name="visibility"></a>Viditelnost

Rozhraní .NET Framework je model propracované viditelnost: typy, metody, pole a ostatní členové mohou být **privátní**, **veřejné**, **interní**a provádění dalších akcí.

Když IntelliTest vygeneruje testy, pokusí se provádět jenom akce (například voláním konstruktorů, metod a nastavení polí), které jsou přípustné s ohledem na pravidla viditelnosti .NET z v rámci kontextu vygenerované testy.

Pravidla jsou následující:

* **Viditelnost vnitřní členy**
  * IntelliTest se předpokládá, že vygenerované testy budou mít přístup k interní členy, které byly viditelné pro nadřazený [PexClass](attribute-glossary.md#pexclass).
  .NET má **InternalsVisibleToAttribute** rozšířit viditelnost členů interní pro jiná sestavení.<p />

* **Viditelnost privátních a členové řady (chráněné v jazyce C#) [PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest vždy umístí vygenerované testy přímo v [PexClass](attribute-glossary.md#pexclass) nebo do podtřídy. Proto se IntelliTest předpokládá, že ho může použít všechny viditelné členy rodiny (**chráněné** v jazyce C#).
  * Pokud vygenerované testy se umístí do přímo [PexClass](attribute-glossary.md#pexclass) (obvykle s využitím částečné třídy), se IntelliTest předpokládá, že ji také používat všechny soukromým členům [PexClass](attribute-glossary.md#pexclass).<p />

* **Viditelnost veřejné členy**
  * IntelliTest se předpokládá, že ho může využívat všechny exportované členy viditelné v rámci [PexClass](attribute-glossary.md#pexclass).

<a name="parameterized-mocks"></a>
## <a name="parameterized-mocks"></a>Parametrizované mocks

Jak se testovací metoda, která má parametr typu rozhraní? Nebo nezapečetěné třídy? IntelliTest neví, implementace, které se později použije, když tato metoda je volána. A možná není k dispozici i skutečné implementaci k dispozici v době testu.

Konvenční odpovědí je použití *napodobení objekty* s explicitní chování. 

Mock objektu implementuje rozhraní (nebo rozšiřuje nezapečetěná třída). To však nepředstavuje skutečné implementaci, ale jenom zástupce, který umožňuje spuštění testů pomocí mock objektu. Její chování je ručně definovali jako součást každý testovací případ, ve kterém se používá. Existuje mnoho nástrojů, které usnadňují definování mock objektů a jejich očekávané chování, ale toto chování musí stále definovat manuálně.

Namísto pevně definovaných hodnot v mock objektů můžete vygenerovat IntelliTest hodnoty. Stejně jako umožňuje [parametrizované testování částí](test-generation.md#parameterized-unit-testing), IntelliTest umožňuje také parametrizované mocks.

Parametrizované mocks mít dva režimy různých spuštění:

* **Výběr**: při zkoumání kódu, jsou parametrizované mocks zdroj další testovací vstupy a IntelliTest se pokusí zvolte zajímavé hodnoty
* **Přehrát**: při provádění testu dříve vytvořenou parametrizované mocks chovají se jako zástupné procedury s chování (jinými slovy, předdefinované chování).

Použití [PexChoose](static-helper-classes.md#pexchoose) a získat hodnoty pro parametry mocks.

<a name="structs"></a>
## <a name="structs"></a>Struktury

IntelliTest v důvody o **struktura** hodnoty je podobným způsobem, jakým se zabývá [objekty](#objects).

<a name="arrays-and-strings"></a>
## <a name="arrays-and-strings"></a>Pole a řetězce

IntelliTest monitoruje prováděnou pokyny při spuštění testu a testovaném programu. Zejména dodržuje, když program závisí na délce řetězce nebo pole (a dolní meze a délek vícerozměrné pole). Také sleduje, jak program používá různé prvky řetězce nebo pole. Poté použije [Řešitel omezení](#constraint-solver) k určení, které délky a hodnoty prvků může způsobit testu a chovat v mnoha zajímavými způsoby v testovaném programu.

IntelliTest se pokusí pro minimalizaci velikosti pole a řetězců, které jsou potřebné k aktivaci zajímavé chování programu.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Získat další vstupy

[PexChoose](static-helper-classes.md#pexchoose) statické třídy lze získat další vstupy pro testovací a slouží k implementaci [parametrizované mocks](#parameterized-mocks).

<a name="further-reading"></a>
## <a name="further-reading"></a>Další čtení

* [Jak to funguje?](https://blogs.msdn.microsoft.com/devops/2014/12/11/smart-unit-tests-a-mental-model/)

## <a name="got-feedback"></a>Máte nějakou zpětnou vazbu?

Publikovat své nápady a funkce na požadavky [komunity vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).