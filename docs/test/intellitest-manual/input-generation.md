---
title: Dynamická symbolická realizace | Testovací nástroj pro vývojáře IntelliTest společnosti Microsoft
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e5a3248d3f081bcab08c08110d305f0aa6235817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302621"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>Generování vstupů pomocí dynamického symbolického spuštění

IntelliTest generuje vstupy pro [parametrizované testy částí](test-generation.md#parameterized-unit-testing) analýzou podmínek větve v programu. Testovací vstupy jsou vybrány na základě toho, zda mohou aktivovat nové větvení chování programu. Analýza je přírůstkový proces. Zpřesňuje predikát `q: I -> {true, false}` nad parametry `I`formálního zkušebního vstupu . `q`představuje sadu chování, které intelliTest již pozoroval. Zpočátku, `q := false`, protože zatím nebylo pozorováno nic.

Kroky smyčky jsou:

1. IntelliTest určuje vstupy `i` `q(i)=false` tak, že pomocí [řešiče omezení](#constraint-solver). Podle konstrukce vstup `i` bude mít cestu spuštění není vidět dříve. Zpočátku to `i` znamená, že může být libovolný vstup, protože dosud nebyla zjištěna žádná cesta spuštění.

1. IntelliTest provede test s vybraným vstupem `i`a sleduje provádění testu a testovaný program.

1. Během provádění program trvá určitou cestu, která je určena všemi podmíněnými větvemi programu. Sada všech podmínek, které určují provádění se nazývá *podmínka cesty* `p: I -> {true, false}` , napsaný jako predikát přes formální vstupní parametry. IntelliTest vypočítá reprezentaci tohoto predikátu.

1. Sady IntelliTest `q := (q or p)`. Jinými slovy, zaznamenává skutečnost, že viděl cestu `p`reprezentovanou .

1. Přejděte ke kroku 1.

IntelliTest [řešič omezení](#constraint-solver) může řešit hodnoty všech typů, které se mohou objevit v programech .NET:

* [Celá čísla](#integers-and-floats) a [plováky](#integers-and-floats)
* [Objekty](#objects)
* [Struktury](#structs)
* [Pole](#arrays-and-strings) a [řetězce](#arrays-and-strings)

IntelliTest filtruje vstupy, které porušují uvedené předpoklady.

Kromě okamžité vstupy (argumenty [parametrizované testy částí),](test-generation.md#parameterized-unit-testing)test může čerpat další vstupní hodnoty ze statické třídy [PexChoose.](static-helper-classes.md#pexchoose) Volby také určují chování [parametrizovaných mocks](#parameterized-mocks).

## <a name="constraint-solver"></a>Řešitel omezení

IntelliTest používá řešič omezení k určení příslušných vstupních hodnot testu a testovce testovce.

IntelliTest používá řešič omezení [Z3.](https://github.com/Z3Prover/z3/wiki)

## <a name="dynamic-code-coverage"></a>Dynamické pokrytí kódu

Jako vedlejší účinek monitorování za běhu IntelliTest shromažďuje data pokrytí dynamického kódu.
To se nazývá *dynamické,* protože IntelliTest ví pouze o kódu, který byl proveden, proto nemůže poskytnout absolutní hodnoty pro pokrytí stejným způsobem jako jiný nástroj pokrytí obvykle.

Například když IntelliTest hlásí dynamické pokrytí jako 5/10 základní bloky, to znamená, že pět bloků z deseti byly pokryty, kde celkový počet bloků ve všech metod, které byly dosud dosaženo analýzou (na rozdíl od všech metod, které existují v sestavení testované) je deset.
Později v analýze, jako krezalnější metody jsou zjištěny, jak čitatel (5 v tomto příkladu) a jmenovatel (10) může zvýšit.

## <a name="integers-and-floats"></a>Celá čísla a čísla s plovoucí desetinnou čárkou

IntelliTest [je omezení řešič](#constraint-solver) určuje vstupní hodnoty test primitivních typů, jako je **bajt**, **int**, **float**a další s cílem aktivovat různé cesty spuštění pro test a testovky programu.

## <a name="objects"></a>Objekty

IntelliTest můžete buď [vytvořit instance existujících tříd .NET](#existing-classes), nebo můžete použít IntelliTest automaticky [vytvořit mock objekty,](#parameterized-mocks) které implementují určité rozhraní a chovají se různými způsoby v závislosti na použití.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>Vytvoření instance existujících tříd

**V čem je problém?**

IntelliTest monitoruje provedené pokyny při spuštění testu a testovaného programu. Zejména monitoruje veškerý přístup k polím. Potom používá [řešič omezení](#constraint-solver) k určení nových testovacích vstupů, včetně objektů a jejich hodnot polí, takže test a testotestovací program se budou chovat jinými zajímavými způsoby.

To znamená, že IntelliTest musí vytvořit objekty určitých typů a nastavit jejich hodnoty polí. Pokud je třída [viditelná](#visibility) a má [viditelný](#visibility) výchozí konstruktor, IntelliTest můžete vytvořit instanci třídy.
Pokud jsou [viditelná](#visibility)všechna pole třídy , intelliTest můžete nastavit pole automaticky.

Pokud typ není viditelný nebo pole nejsou [viditelné](#visibility), IntelliTest potřebuje pomoc k vytvoření objektů a jejich uvedení do zajímavých stavů k dosažení maximální pokrytí kódu. IntelliTest může použít reflexe k vytvoření a inicializaci instancí libovolnými způsoby, ale to není obvykle žádoucí, protože může přenést objekt do stavu, který nemůže nikdy dojít během normálního spuštění programu. Místo toho IntelliTest spoléhá na rady od uživatele.

## <a name="visibility"></a>Viditelnost

.NET má propracovaný model viditelnosti: typy, metody, pole a další členy mohou být **soukromé**, **veřejné**, **interní**a další.

Když IntelliTest generuje testy, pokusí se provést pouze akce (například volání konstruktorů, metod a nastavení polí), které jsou legální s ohledem na pravidla viditelnosti .NET z kontextu generovaných testů.

Pravidla jsou následující:

* **Viditelnost interních členů**
  * IntelliTest předpokládá, že generované testy budou mít přístup k interním členům, které byly viditelné pro ohraničující [třídu PexClass](attribute-glossary.md#pexclass).
  .NET má **InternalsVisibleToAttribute** rozšířit viditelnost interních členů do jiných sestavení.

* **Viditelnost soukromých a rodinných příslušníků (chráněných v C#) členů [třídy PexClass](attribute-glossary.md#pexclass)**
  * IntelliTest vždy umístí generované testy přímo do [PexClass](attribute-glossary.md#pexclass) nebo do podtřídy. Proto IntelliTest předpokládá, že může používat všechny viditelné členy rodiny (**chráněné** v C#).
  * Pokud generované testy jsou umístěny přímo do [PexClass](attribute-glossary.md#pexclass) (obvykle pomocí částečné třídy), IntelliTest předpokládá, že může také použít všechny soukromé členy [PexClass](attribute-glossary.md#pexclass).

* **Viditelnost veřejných členů**
  * IntelliTest předpokládá, že může používat všechny exportované členy viditelné v kontextu [PexClass](attribute-glossary.md#pexclass).

## <a name="parameterized-mocks"></a>Parametrizované napodobeniny

Jak otestovat metodu, která má parametr typu rozhraní? Nebo nezapečetěné třídy? IntelliTest neví, které implementace budou později použity při volání této metody. A možná tam není ani skutečná implementace k dispozici v době testování.

Konvenční odpověď je použití *mock objekty* s explicitní chování.

Mock objekt implementuje rozhraní (nebo rozšiřuje nezapečetěné třídy). Nepředstavuje skutečné implementace, ale pouze zástupce, který umožňuje provádění testů pomocí mock objektu. Jeho chování je definováno ručně jako součást každého testovacího případu, kde se používá. Existuje mnoho nástrojů, které usnadňují definování mock objektů a jejich očekávané chování, ale toto chování musí být stále definovány ručně.

Namísto pevně zakódovaných hodnot v mock objektech intelliTest můžete generovat hodnoty. Stejně jako umožňuje [parametrizované testování částí](test-generation.md#parameterized-unit-testing), IntelliTest také umožňuje parametrizované mocks.

Parametrizované mocks mají dva různé režimy provádění:

* **volba**: při zkoumání kódu jsou parametrizované mocks zdrojem dalších testovacích vstupů a IntelliTest se pokusí vybrat zajímavé hodnoty
* **replay**: při provádění dříve generovaného testu se parametrizované mocky chovají jako zástupné procedury s chováním (jinými slovy předdefinované chování).

Pomocí [funkce PexChoose](static-helper-classes.md#pexchoose) můžete získat hodnoty pro parametrizované mocky.

## <a name="structs"></a>Struktury

IntelliTest je úvaha o **strukturovat** hodnoty je podobný způsob, jakým se zabývá [objekty](#objects).

## <a name="arrays-and-strings"></a>Pole a řetězce

IntelliTest monitoruje provedené pokyny při spuštění testu a testovaného programu. Zejména sleduje, kdy program závisí na délce řetězce nebo pole (a dolní hranice a délky vícerozměrné pole).
Také sleduje, jak program používá různé prvky řetězce nebo pole. Potom používá [řešič omezení](#constraint-solver) k určení, které délky a hodnoty prvků mohou způsobit, že test a testovky testovny se budou chovat zajímavým způsobem.

IntelliTest se pokusí minimalizovat velikost polí a řetězců potřebných ke spuštění zajímavéchování programu.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>Získat další vstupy

[PexChoose](static-helper-classes.md#pexchoose) statické třídy lze získat další vstupy do testu a lze použít k implementaci [parametrizované mocks](#parameterized-mocks).

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="further-reading"></a>Další čtení

* [Jak to funguje?](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)
