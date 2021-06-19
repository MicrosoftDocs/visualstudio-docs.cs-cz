---
title: O jazycích specifických pro konkrétní domény
description: Přečtěte si, jak je jazyk specifický pro doménu (DSL) navržený tak, aby restatemental příkazy v konkrétním prostoru problému nebo doméně.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab56292aafda25efc0b3dfeeb14e93d4502a5567
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384977"
---
# <a name="about-domain-specific-languages"></a>O jazycích specifických pro konkrétní domény

Na rozdíl od univerzálního jazyka, jako je C# nebo UML, je jazyk specifický pro doménu (DSL) navržený tak, aby se příkazy v konkrétním prostoru pro potíže nebo doméně nevyjádřily.

Dobře známý DSL zahrnuje regulární výrazy a SQL. Každá DSL je mnohem lepší než pro obecný jazyk pro popis operací s textovými řetězci nebo databází, ale mnohem horší pro popis nápadů, které jsou mimo svůj vlastní rozsah. Jednotlivé obory mají také vlastní DSL. Například v odvětví telekomunikací se jazyky popisu volání často používají k určení posloupnosti stavů v rámci telefonního hovoru a v leteckém průmyslu se standardní DSL používá k popisu letových knih.

Vaše podnikání a váš projekt také řeší speciální sady konceptů, které by mohly být popsány pomocí DSL. Můžete například definovat DSL pro jednu z těchto aplikací:

- Plánování navigačních cest na webu.

- Diagramy zapojení pro elektronické součásti.

- Sítě pásových pásů a vybavení pro zpracování zavazadel pro letiště.

Při návrhu DSL definujete *doménovou třídu* pro každý z důležitých konceptů v doméně, jako je například webová stránka, lampa nebo oddělení pro kontrolu letiště. Můžete definovat *vztahy mezi doménami* , jako je hypertextový odkaz, telegraf nebo pásový, aby bylo možné propojit koncepty dohromady.

Uživatelé vaší DSL vytvoří *modely.* Modely jsou *instancemi* DSL. Například popisují konkrétní web nebo zapojení konkrétního zařízení nebo systém pro zpracování zavazadel na konkrétní letiště.

Uživatelé mohou zobrazit model jako diagram nebo jako formulář Windows. Modely lze také zobrazit jako XML, což znamená způsob jejich uložení. Při definování DSL můžete definovat, jak se budou instance jednotlivých doménových tříd a vztahů zobrazovat na obrazovce uživatele. Typická DSL se zobrazuje jako kolekce ikon nebo obdélníků propojených šipkami.

Následující obrázek ukazuje malý model v diagramatické DSL:

![Model stromu Tudor Family](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Co můžete dělat s DSL

Typickou aplikací DSL je generování kódu programu nebo jiných artefaktů. Při definování DSL můžete definovat *textové šablony* , které ČTOU model DSL a vygenerují textové soubory.

Můžete například napsat šablony, které berou plán letiště, a vygenerovat část softwaru pro zpracování zavazadel a také některé dokumenty uživatele, které popisují tento plán.

Pokud jste definovali DSL, můžete ji distribuovat dalším uživatelům, kteří ji můžou nainstalovat na svých počítačích. Uživatelé vaší DSL můžou vytvářet a upravovat modely v aplikaci Visual Studio.

Můžete také definovat příkazy nabídky a další nástroje, které uživatelům pomůžou upravit DSL, ověřovací omezení, aby se zajistilo, že se DSL používá správně, a šablony položek, které uživatelům pomůžou vytvářet nové instance. Jeden nebo více DSL můžete zabalit pomocí nástrojů a dalších rozšíření aplikace Visual Studio jako integrovaného balíčku.

Obvykle se vytvoří jazyk specifický pro doménu, když vývojový tým musí psát podobný kód pro několik produktů. Například společnost, která se specializuje na systémy zpracování zavazadel, může definovat linku DSL pro záznam o zavazadlu, ze které mohou vygenerovat kód pro každou instalaci. Výhodou DSL je, že je může rozumět jejich zákazníkům, že kód vygenerovaný z něj je spolehlivý a že systém lze rychle aktualizovat, pokud se změní požadavky zákazníků.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] umožňuje vytvořit jazyk specifický pro doménu, který má vlastního grafického návrháře a vlastní zápis diagramu, a pak použít jazyk k vygenerování vhodného zdrojového kódu pro každý projekt.

## <a name="domain-specific-development"></a>Vývoj Domain-Specific

Vývoj specifický pro doménu je proces identifikace částí vašich aplikací, které je možné modelovat pomocí jazyka specifického pro doménu, a následným vytvořením jazyka a jeho nasazením do vývojářů aplikací. Vývojáři používají jazyk specifický pro doménu k vytvoření modelů, které jsou specifické pro jejich aplikace, použijte modely pro generování zdrojového kódu a pak použijte zdrojový kód pro vývoj aplikací.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekty vývoje grafického Domain-Specific

Jazyk specifický pro doménu musí zahrnovat následující funkce:

- Notace

- Doménový model

- Generování artefaktů

- Serializace

- Integrace se sadou Visual Studio

### <a name="notation"></a>Notace

Jazyk specifický pro doménu musí mít přiměřeně malou sadu prvků, které lze snadno definovat a rozšířit tak, aby představovaly konstrukce specifické pro doménu. Zápis se skládá z tvarů, které reprezentují prvky a spojnice, které znázorňují vztahy mezi prvky, na grafické ploše diagramu. V nástroji je [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] možné tvary rozšířit a zdokonalit tak, aby představovaly prvky vašeho jazyka specifického pro doménu.

### <a name="domain-model"></a>Doménový model

Jazyk specifický pro doménu musí kombinovat sadu prvků a vztahy mezi nimi do souvislé gramatické gramatiky. Musí také definovat, zda jsou kombinace prvků a relací platné. Například programovací jazyky obvykle zabraňují cyklické dědičnosti, kdy jedna třída je odvozena od druhé třídy a druhá třída je odvozena od první třídy. Omezení lze také použít k vyjádření obchodní logiky, například jedna osoba nemůže být závislá na sobě. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Nástroj používá omezení k vyjádření druhů omezení, která vyžaduje většina jazyků specifických pro doménu.

### <a name="artifact-generation"></a>Generování artefaktů

Jedním z hlavních účelů jazyka specifického pro doménu je vygenerování artefaktu, například zdrojového kódu, souboru XML nebo jiných použitelných dat. Změna v modelu obvykle znamená změnu v artefaktu. Můžete použít [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] ke generování artefaktů a k jejich opětovnému vygenerování při změně modelu.

### <a name="serialization"></a>Serializace

Jazyk specifický pro doménu musí být trvalý v některém formuláři, který lze upravovat, ukládat, uzavírat a znovu načíst. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] používá formát XML, který umožňuje definovat a přizpůsobit způsob, jakým je váš jazyk specifický pro doménu serializován nebo trval.

### <a name="integration-with-visual-studio"></a>Integrace se sadou Visual Studio

Protože [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] je hostovaný v aplikaci Visual Studio, rozšiřuje mnoho oken a ovládacích prvků sady Visual Studio. Umožňuje také přizpůsobit chování příkazů nabídky, položek panelu nástrojů a dalších prvků uživatelského rozhraní.

Pro jazyk specifický pro doménu můžete také vytvořit adaptér model sběrnice. Tento adaptér umožňuje odkazovat na model a prvky v rámci modelu a umožňuje psát kód, který má přístup k instanci DSL a její aktualizaci. Pomocí výkonného mechanismu sběrnice modelu můžete napsat rozšíření sady Visual Studio, která fungují s více modely. Můžete také psát samostatné aplikace, které pracují s modely. Další informace naleznete v tématu [integrování modelů pomocí sady Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Výhody vývoje Domain-Specific

Jazyk specifický pro doménu může poskytovat následující výhody:

- Obsahuje konstrukce, které přesně odpovídají prostoru problému.

     Na rozdíl od obecných jazyků se jazyk specifický pro doménu skládá z prvků a vztahů, které přímo reprezentují logiku prostoru problému. Například aplikace zásad pojištění musí zahrnovat prvky pro zásady a deklarace identity. Jazyk specifický pro doménu usnadňuje návrh aplikace a vyhledávání a opravy chyb logiky.

- Umožňuje, aby nevývojáři a lidé, kteří znají doménu, pochopili celkový návrh.

     Pomocí grafického jazyka specifického pro doménu můžete vytvořit vizuální reprezentaci domény, aby nevývojáři mohli snadno pochopit návrh aplikace.

- Usnadňuje vytváření prototypu finální aplikace.

     Vývojáři mohou pomocí kódu, který svůj model generuje, vytvořit aplikaci prototypu, kterou mohou zobrazit klientům.

## <a name="the-process-of-domain-specific-development"></a>Proces vývoje Domain-Specific

Většina vývojářských týmů, které používají jazyky specifické pro doménu, vám umožní vytvořit a použít jejich modely pomocí následujících kroků:

- Tým rozlišuje části domény proměnných od částí, které se nikdy nezmění.

- Vývojáři napíší kód pro pevné části a nechají Rozšiřovací body pro části proměnných.

- Vývojář softwaru nebo architekt vytvoří jazyk specifický pro doménu, který zahrnuje vzory návrhu pevných částí domény a rozšiřovací body pro části proměnné.

- Vedoucí vývojář softwaru nebo architekt nasadí jazyk specifický pro doménu vývojářům různých aplikací, které tým vytvoří.

- Každý vývojář vytvoří model, který se vztahuje na konkrétní aplikaci.
