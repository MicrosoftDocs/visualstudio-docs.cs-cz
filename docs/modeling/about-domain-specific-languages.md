---
title: O jazycích specifických pro konkrétní domény
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 501b85579460038d6d20ca38b17ab22be7825f5c
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176990"
---
# <a name="about-domain-specific-languages"></a>O jazycích specifických pro konkrétní domény

Na rozdíl od pro obecné účely jazyka, jako je C# nebo UML jazyka specifického pro doménu (DSL) slouží k vyjádření příkazy v místo konkrétního problému, nebo doméně.

Známé DSL zahrnují regulárních výrazů a SQL. Každý DSL je mnohem lepší než obecný jazyk pro popis operace v textových řetězců nebo databázi, ale mnohem horší popisující nápadech, které jsou mimo svůj vlastní obor. Jednotlivé obory také mít své vlastní DSL. Například v odvětví telekomunikace popis volání jazyky se běžně používají k určení posloupnost stavy v telefonní hovor a ve vzduchu cestovní odvětví standardního DSL slouží k popisu letu rezervace.

Vaše podnikání a váš projekt také řešit speciální sadu koncepty, které by mohly být popsané společně s DSL. Můžete například definovat DSL pro jednu z těchto aplikací:

-   Plán cesty navigace na webu.

-   Vzájemné propojení diagramy pro elektronických komponent.

-   Sítě dopravní pásy a zpracování zařízení pro letišti sobě.

Při návrhu DSL, můžete definovat *doménové třídy* pro všechny důležité koncepty v doméně, třeba webové stránky, lamp nebo letiště stolu vrácení se změnami. Můžete definovat *vztahy domén* jako hypertextový odkaz, při přenosu nebo dopravní pás koncepty propojit dohromady.

Vytvoření uživatelů tohoto kódu DSL *modely.* Modely jsou *instance* nástroje DSL. Například popisují určitý web nebo její konkrétní zařízení nebo sobě systém v určitém letišti zpracování.

Vaši uživatelé mohou zobrazit model, jako diagram nebo formulář Windows. Modely lze také zobrazit ve formátu XML, jak jsou uložené. Při definování DSL definujete, jak se zobrazují instance každé doménové třídy a relace na obrazovce uživatele. Typické DSL se zobrazí kolekce ikon nebo obdélníky propojené pomocí šipky.

Následující obrázek znázorňuje malé modelu v graficky DSL:

![Tudor řady stromu modelu](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Co můžete dělat s DSL

Typická aplikace DSL je generování programového kódu nebo jiné artefakty. Při definování vašeho DSL, můžete definovat *textových šablon* , který čtení modelu DSL a generování textových souborů.

Můžete například napsat šablony, které používat plán letišti a generovat část softwaru pro zpracování, a také některé dokumenty uživatele, které popisují plánu sobě.

Po nadefinování DSL, můžete ho distribuovat ostatním uživatelům, kteří ji můžete nainstalovat na svých počítačích. Uživatelé tohoto kódu DSL můžete vytvářet a upravovat modelů v sadě Visual Studio.

Můžete také definovat příkazy a další nástroje, které pomáhají uživatelům upravit DSL omezení ověření k zajištění, že se správně používá DSL a šablon položek, které pomáhají uživatelům vytvoření nových instancí. Jeden nebo více DSL, své nástroje a další rozšíření sady Visual Studio lze zabalit jako integrované balíček.

Obvykle jazyka specifického pro doménu se vytvoří při vývojový tým musí zapisovat podobný kód pro několik produktů. Společnost, která se specializuje na sobě systémy zpracování může například definovat DSL sledování sobě ze kterého se generovat kód pro každou instalaci. Nástroje DSL je, že lze chápat tak svým zákazníkům, že kód generovaný z něj je spolehlivý a, že systém je možné rychle aktualizovat, pokud se změní požadavky zákazníků.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Umožňuje vytvoření jazyka specifického pro doménu, která má grafického návrháře a zápis diagramu a potom použít ke generování příslušného zdrojového kódu pro každý projekt jazyk.

## <a name="domain-specific-development"></a>Vývoj specifického pro doménu

Vývoj specifického pro doménu je proces identifikace části vašich aplikací, které mohou být modelovaná pomocí jazyka specifického pro doménu, vytváření jazyka a jeho nasazení pro vývojáře aplikací. Vývojáři jazyka specifického pro doménu můžete vytvořit modely, které jsou specifické pro své aplikace, používat modely k vygenerování zdrojového kódu a pak pomocí zdrojového kódu pro vývoj aplikací.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekty vývoje grafické specifického pro doménu

Grafické jazyka specifického pro doménu, musí obsahovat následující funkce:

- Zápis

- Doménový model

- Generování artefaktu

- Serializace

- Integrace se sadou Visual Studio

### <a name="notation"></a>Zápis

Jazyka specifického pro doménu, musí mít poměrně malého počtu prvků, které lze snadno definované a rozšířená tak, aby představují konstrukce jazyka specifického pro doménu. Zápis se skládá z tvary, které zastupují elementy, a konektorů, které představují vztahy mezi elementy, na ploše Grafický diagram. V [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], tvary můžou být dále rozšiřována a vylepšili o představují prvky jazyka specifického pro doménu.

### <a name="domain-model"></a>Doménový Model

Jazyka specifického pro doménu obsahující kombinaci sadu elementů a vztahů mezi nimi do koherentního gramatiky. Musíte také definovat, zda kombinace různých typů elementů a vztahů jsou platné. Například programovacích jazyků obvykle zakázat Cyklické dědění, ve které jedna třída je odvozena z třídy sekundu a druhá třída je odvozena od třídy první. Omezení je také možné vyjádřit obchodní logiky, například jedna osoba nemůže být závislá aplikace sám. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] pomocí omezení express typy omezení, které vyžadují nejvíc jazyky specifickými pro doménu.

### <a name="artifact-generation"></a>Generování artefaktu

Jedním z hlavních účelů jazyka specifického pro doménu je generování artefakt, například zdrojový kód, soubor XML nebo jiných využitelná data. Změny v modelu obvykle znamená změnu v artefaktu. Můžete použít [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] ke generování artefakty a znovu vygenerovat, je při změně modelu.

### <a name="serialization"></a>Serializace

Jazyka specifického pro doménu, musíte nastavit jako trvalý, v nějaké podobě, který je možné upravit, uložit, zavření a znovu načíst. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] používá formát XML, který umožňuje definování a přizpůsobení jak jazyka specifického pro doménu je serializován nebo trvalé.

### <a name="integration-with-visual-studio"></a>Integrace se sadou Visual Studio

Protože [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] hostována v sadě Visual Studio rozšiřuje mnoho okna sady Visual Studio a ovládací prvky. Můžete ho taky přizpůsobit chování příkazy nabídek, položky panelu nástrojů a další prvky uživatelského rozhraní.

Můžete také vytvořit adaptér sběrnice modelu pro jazyka specifického pro doménu. Tento adaptér umožňuje odkaz modelem a prvky v rámci modelu a umožňuje, aby při psaní kódu, které můžete používat a aktualizovat instance DSL. S použitím o efektivní mechanismus sběrnice modelu, můžete napsat s rozšířeními Visual Studia, které pracují s více modely. Můžete taky psát samostatné aplikace, které pracují s modely. Další informace najdete v tématu [integrace modelů pomocí Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Výhody vývoj specifického pro doménu

Jazyka specifického pro doménu může poskytnout následující výhody:

- Obsahuje konstruktory, které přesně odpovídají místo problém.

     Na rozdíl od pro obecné účely jazyků jazyka specifického pro doménu se skládá z prvky a vztahy, které představují přímo logiku místo problém. Například pojistku aplikace musí zahrnovat elementy pro zásady a deklarace identity. Jazyka specifického pro doménu usnadňuje návrh aplikace a najít a opravit chyby logiky.

- Umožňuje nevývojáře a uživatelů, kteří neznáte domény pochopit celkový návrh.

     S použitím grafického jazyka specifického pro doménu, můžete vytvořit vizuální reprezentaci domény tak, aby nevývojáře, můžete snadno seznámit se s návrhem aplikace.

- Usnadňuje vytvoření prototypu poslední aplikace.

     Vývojáři mohou použít kód, který generuje jejich model k vytvoření prototypu aplikace, která můžete zobrazit na klienty.

## <a name="the-process-of-domain-specific-development"></a>Proces vývoje specifického pro doménu

Většina vývojových týmů, které používají jazyky specifickými pro doménu použijte následující postup vytvoření a používání svoje modely:

-   Tým odlišuje části proměnné domény, z části, které nikdy nezmění.

-   Vývojáři psát kód pro pevnou části a nechat Rozšiřovací body proměnné částí.

-   Vedoucí softwarový vývojář nebo architekt vytvoří jazyka specifického pro doménu, zahrnující vzory návrhu pevné částí domény a Rozšiřovací body proměnné částí.

-   Vedoucí softwarový vývojář nebo architekt nasadí vývojářům různé aplikace, které vytvoří tým jazyka specifického pro doménu.

-   Každý vývojář vytvoří model, který platí pro konkrétní aplikaci.