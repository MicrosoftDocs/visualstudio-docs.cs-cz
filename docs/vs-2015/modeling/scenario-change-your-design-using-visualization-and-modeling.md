---
title: 'Scénář: Změna návrhu pomocí vizualizace a modelování | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cafc4e2a87a31603e1f8cef4174d8538be768428
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296017"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scénář: Změna návrhu pomocí vizualizace a modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ujistěte se, že váš softwarový systém splňuje požadavky uživatelů pomocí nástrojů pro vizualizaci a modelování v aplikaci Visual Studio. Používejte nástroje, jako jsou diagramy jazyk UML (Unified Modeling Language) (UML), mapy kódu, diagramy vrstev a diagramy tříd:

 Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé nástroje, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Upřesněte požadavky uživatelů a obchodní procesy.

- Vizualizujte a prozkoumejte existující kód.

- Popisuje změny v existujícím systému.

- Ověřte, že systém splňuje požadavky.

- Udržujte kód v souladu s návrhem.

  Tento návod:

- Popisuje, jak můžou tyto nástroje těžit z vašeho softwarového projektu.

- Ukazuje, jak můžete tyto nástroje používat bez ohledu na to, jaký je váš přístup k vývoji, a to s ukázkovým scénářem.

  Další informace o těchto nástrojích a scénářích, které podporují, najdete v těchto tématech:

- [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)

- [Vizualizace kódu](../modeling/visualize-code.md)

- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)

## <a name="ScenarioOverview"></a>Přehled scénáře
 Tento scénář popisuje díly z životního cyklu vývoje softwaru dvou fiktivních společností: večeře nyní a Lucerne Publishing. Večeře teď poskytuje webovou službu pro doručování na základě jídla v Seattlu. Zákazníci můžou objednat jídla a platit za ně na webu večeře Now. Objednávky se pak odesílají do příslušné místní restaurace pro doručení. Lucerne Publishing, společnost v New Yorku, provozuje na webu několik firem současně. Například spouštějí web, kde můžou zákazníci publikovat recenze na restaurace.

 Společnost Lucerne nedávno získala večeři a chce provést následující změny:

- Integrujte své weby přidáním funkcí recenze pro restaurace do hostina Now.

- V systému společnosti Lucerne teď nahraďte platební systém.

- Rozbalte službu večeře Now v rámci oblasti.

  Večeře teď používá SCRUM a extrémní programování. Mají velmi vysoké pokrytí testů a velmi nepodporovaný kód. Tím se minimalizují rizika vytvořením malých, ale funkčních verzí systému a následným přidáním funkcí. Vyvíjejí svůj kód v krátkých a častých iteracích. To jim umožní mít jistotu na změnu, často Refaktorovat kód a vyhnout se "velkému návrhu předem".

  Společnost Lucerne udržuje mnohem větší a složitou kolekci systémů, z nichž některé jsou starší než 40 let. Jsou velmi opatrní při provádění změn z důvodu složitosti a rozsahu starší verze kódu. Dodržují přísnější proces vývoje, který předvedl návrh podrobných řešení a dokumentuje návrh a změny, ke kterým došlo během vývoje.

  Oba týmy používají diagramy modelování v aplikaci Visual Studio, které jim pomůžou vyvíjet systémy, které vyhovují potřebám uživatelů. Používají Team Foundation Server společně s dalšími nástroji, které jim pomohou naplánovat, uspořádat a spravovat jejich práci.

  Další informace o Team Foundation Server najdete v tématech:

- [Plánování a sledování práce](#PlanningTracking)

- [Testování, ověřování a vrácení aktualizovaného kódu](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a>Role architektury a modelování diagramů při vývoji softwaru
 Následující tabulka popisuje role, které tyto nástroje mohou hrát během několika různých fází životního cyklu vývoje softwaru:

||**Modelování uživatelských požadavků**|**Modelování obchodních procesů**|**Architektura systému & návrh**|**Zkoumání & vizualizace kódu**|**Zaznamenávala**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Diagram případu použití (UML)|√|√|||√|
|Diagram činnosti (UML)|√|√|√||√|
|Diagram tříd (UML)|√|√|√||√|
|Diagram komponent (UML)|√|√|√||√|
|Sekvenční diagram (UML)|√|√|√||√|
|Diagram DSL (Domain-Specific Language)|√|√|√|||
|Diagram vrstev, ověřování vrstev|||√|√|√|
|Mapa kódu|||√|√|√|
|Návrhář tříd (založený na kódu)||||√||

 Chcete-li nakreslit diagramy UML a diagramy vrstev, je nutné vytvořit projekt modelování jako součást stávajícího řešení nebo nového. Tyto diagramy musí být vytvořeny v projektu modelování. Položky v diagramech UML jsou součástí společného modelu a diagramy UML jsou zobrazeními tohoto modelu. Položky v diagramech vrstev se nacházejí v projektu modelování, ale nejsou uloženy ve společném modelu. Mapy kódu a diagramy tříd .NET vytvořené z kódu existují mimo projekt modelování.

 Další informace:

- [Vytváření projektů a diagramů pomocí modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Chcete-li zobrazit alternativní zobrazení architektury, můžete znovu použít určité prvky ze stejného modelu na více nebo různých diagramech. Například můžete přetáhnout komponentu do jiného diagramu komponent nebo do sekvenčního diagramu tak, aby mohl fungovat jako objekt actor. Viz [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

  Oba týmy také používají ověřování vrstvy, aby se zajistilo, že kód ve vývoji zůstane v souladu s návrhem.

  Další informace:

- [Udržování kódu v souladu s návrhem](#ValidatingCode)

- [Popište logickou architekturu: diagramy vrstev](#DescribeLayers)

- [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Některé verze služby Visual Studio podporují ověřování vrstvy a verze map kódu a diagramů UML jen pro čtení pro vizualizaci a modelování. Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="UnderstandingCommunicating"></a>Porozumění a sdělování informací o systému
 Neexistuje žádné předepsané pořadí pro použití diagramů modelování sady Visual Studio, takže je můžete použít tak, jak vyhovují vašim potřebám nebo přístupu. Týmy obvykle opakovaně přepínají své modely v rámci projektu. Každý diagram nabízí konkrétní sílu, které vám pomůžou pochopit, popsat a komunikovat různé aspekty systému ve vývoji.

 Večeře hned a vojtěšku navzájem komunikují a s účastníky projektu pomocí diagramů jako jejich společného jazyka. Například večeře teď používá diagramy k provádění těchto úkolů:

- Vizualizujte existující kód.

- Komunikujte s vojtěškou o nových nebo aktualizovaných uživatelských scénářích.

- Identifikujte změny, které jsou potřeba k podpoře nových nebo aktualizovaných uživatelských scénářů.

  Společnost Lucerne používá diagramy k provádění těchto úkolů:

- Přečtěte si o tomto obchodním procesu večeři.

- Pochopení návrhu systému.

- Komunikujte s večeři teď o nových nebo aktualizovaných požadavcích uživatelů.

- Aktualizuje dokument do systému.

  Diagramy jsou integrované s Team Foundation Server, takže týmy můžou snadněji plánovat, spravovat a sledovat práci. Například používají modely k identifikaci testových případů a vývojářských úloh a k odhadu jejich práce. Společnost Lucerne propojuje Team Foundation Server pracovní položky s prvky modelu tak, aby mohly sledovat průběh a ujistit se, že systém splňuje požadavky uživatelů. Například propojí případy použití s pracovními položkami testovacího případu, takže uvidí, že případy použití jsou splněné, když všechny testy proběhnou.

  Než týmy zaregistrují změny, ověří kód proti testům a návrhu spuštěním sestavení, která zahrnují ověřování vrstev a automatizované testy. To pomáhá zajistit, že aktualizovaný kód není v konfliktu s návrhem a přerušit dříve funkční funkčnost.

  Další informace:

- [Principy role systému v obchodním procesu](#UnderstandingBPMandSystemDesign)

- [Popisuje nové nebo aktualizované požadavky uživatelů](#DescribingURM)

- [Vytváření testů z modelů](#CreatingTests)

- [Určení změn stávajícího systému](#DeterminingChanges)

- [Udržování kódu v souladu s návrhem](#ValidatingCode)

- [Obecné tipy pro vytváření a používání modelů](#GeneralTips)

- [Plánování a sledování práce](#PlanningTracking)

- [Testování, ověřování a vrácení aktualizovaného kódu](#TestValidateCheckInCode)

### <a name="UnderstandingBPMandSystemDesign"></a>Principy role systému v obchodním procesu
 Společnost Lucerne si chce získat další informace o vašem obchodním procesu večeře. Vytvářejí následující diagramy, které vám pomohou pochopit jejich porozumění s večeři a teď snadněji:

|**Znázorňuje**|**Udává**|
|-----------------|-------------------|
|*Diagram případu použití (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) dokumentace<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|– Aktivity, které teď podporuje systém večeře<br />– Lidé a externí systémy, které provádějí aktivity<br />– Hlavní součásti systému, které podporují jednotlivé aktivity<br />– Části obchodního procesu, které jsou mimo rozsah aktuálního systému, například doručování potravin|
|*Diagram činnosti (UML)*<br /><br /> Další informace:<br /><br /> -   [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md) dokumentace<br />-   [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Tok kroků, ke kterým dochází, když zákazník vytvoří objednávku|
|*Diagram tříd (UML)*<br /><br /> Další informace:<br /><br /> -   [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) dokumentace<br />-   [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|Obchodní entity a výrazy, které se používají v diskusích a vztahy mezi těmito entitami. Například objednávka a položka nabídky jsou součástí slovníku v tomto scénáři.|

 Například společnost Lucerne vytvoří následující diagram případu použití, který vám pomůže pochopit úkoly, které jsou prováděny na webu večeře Now a kdo je provede:

 ![Diagram případu použití UML](../modeling/media/uml-usecase.png "UML_UseCase")

 **Diagram případu použití UML**

 Následující diagram činnosti popisuje postup, kdy zákazník vytvoří objednávku na webu večeře Now. V této verzi prvky komentářů identifikují role a řádky vytvářejí *plavecké dráhy*, které organizují kroky podle rolí:

 ![Diagram činnosti UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **Diagram činnosti UML**

 Následující diagram tříd popisuje entity, které se účastní procesu pořadí:

 ![Diagram tříd UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **Diagram tříd UML**

### <a name="DescribingURM"></a>Popisuje nové nebo aktualizované požadavky uživatelů
 Společnost Lucerne chce do systému večeře přidat funkce, aby zákazníci mohli číst a přispívat k recenzím restaurace. Aktualizují následující diagramy tak, aby mohly tento nový požadavek popsat a diskutovat z něj nyní:

|**Znázorňuje**|**Udává**|
|-----------------|-------------------|
|*Diagram případu použití (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) dokumentace<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|Nový případ použití pro "zápis přezkoumání restaurace"|
|*Diagram činnosti (UML)*<br /><br /> Další informace:<br /><br /> -   [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md) dokumentace<br />-   [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Postup, který nastane, když chce zákazník napsat revizi restaurace|
|*Diagram tříd (UML)*<br /><br /> Další informace:<br /><br /> -   [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) dokumentace<br />-   [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|Data, která jsou nutná k uložení Revize|

 Například následující diagram případu použití zahrnuje nový případ použití "zápisu revize", který reprezentuje nový požadavek. Je zvýrazněna oranžová v diagramu pro snazší identifikaci:

 ![Diagram případu použití UML](../modeling/media/uml-writerev.png "UML_WriteRev")

 **Diagram případu použití UML**

 Následující diagram činnosti obsahuje nové prvky oranžová pro popis toku kroků v novém případu použití:

 ![Diagram činnosti UML](../modeling/media/uml-writereview.png "UML_WriteReview")

 **Diagram činnosti UML**

 Následující diagram tříd obsahuje novou třídu revize a její vztahy k jiným třídám, aby týmy mohly diskutovat o svých podrobnostech. Všimněte si, že zákazník a restaurace můžou mít několik revizí:

 ![Diagram tříd UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **Diagram tříd UML**

### <a name="CreatingTests"></a>Vytváření testů z modelů
 Oba týmy souhlasí s tím, že potřebují kompletní sadu testů pro systém a jeho součásti před provedením změn. Společnost Lucerne má specializovaný tým, který provádí testování na úrovni systému a součástí. Znovu znovu vytvoří testy vytvořené přes večeři a strukturují tyto testy pomocí diagramů UML:

- Každý případ použití je reprezentován jedním nebo několika testy. Prvky na odkaz diagramu případu použití pro pracovní položky testovacího případu v Team Foundation Server.

- Každý tok v diagramu činnosti nebo sekvenční diagram na úrovni systému je propojen s jedním testem alespoň jednou. Testovací tým systematicky zajistí, že otestuje každou možnou cestu prostřednictvím diagramu činnosti.

- Podmínky používané k popisu testů jsou založeny na výrazech, které jsou definovány v diagramech případů použití, třídy a činnosti.

  Jak se mění požadavky a diagramy se aktualizují, aby odrážely tyto změny, testy se aktualizují také. Požadavek se považuje za splněný pouze v případě, že testy proběhnou. Pokud je to možné nebo praktické, testy jsou definovány a založeny na diagramech UML před spuštěním implementace.

  Další informace:

- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)

- [Ověření modelu UML](../modeling/validate-your-uml-model.md)

### <a name="DeterminingChanges"></a>Určení změn stávajícího systému
 Večeře teď musí odhadnout náklady na splnění nového požadavku. Tato změna závisí částečně na tom, kolik změn bude mít vliv na ostatní části systému. Abychom jim mohli porozumět, jeden z vývojářů s večeři teď vytvoří tyto mapy a diagramy z existujícího kódu:

|**Mapa nebo diagram**|**Objeví**|
|------------------------|---------------|
|*Mapa kódu*<br /><br /> Další informace:<br /><br /> -   [závislosti map napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />-   [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Závislosti a další vztahy v kódu.<br /><br /> Například večeře teď může začít kontrolou map kódu sestavení pro přehled sestavení a jejich závislostí. Mohou přejít k podrobnostem o mapách a prozkoumat obory názvů a třídy v těchto sestaveních.<br /><br /> Večeře teď může také vytvořit mapy k prozkoumání konkrétních oblastí a dalších druhů vztahů v kódu. Používají Průzkumník řešení k vyhledání a výběru oblastí a vztahů, které vás zajímají.|
|*Diagram tříd založený na kódu*<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Existující třídy v kódu|

 Například vývojář Vytvoří mapu kódu. Upraví svůj obor tak, aby se zaměřil na oblasti, které budou tímto novým scénářem ovlivněny. Tyto oblasti jsou vybrané a zvýrazněné na mapě:

 ![Graf závislosti oboru názvů](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Mapa kódu oboru názvů**

 Vývojář rozšíří vybrané obory názvů tak, aby viděli jejich třídy, metody a vztahy:

 ![Graf závislosti rozšířeného oboru názvů](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Rozšířené mapování kódu oboru názvů s viditelnými odkazy mezi skupinami**

 Vývojář prověřuje kód, aby našli příslušné třídy a metody. Chcete-li zobrazit účinky každé změny při jejich provádění, znovu vygenerujte mapy kódu po každé změně. Viz [vizualizuje kód](../modeling/visualize-code.md).

 Aby bylo možné popsat změny v jiných částech systému, jako jsou komponenty nebo interakce, může tým vykreslit tyto prvky do tabulí. Mohou také nakreslit následující diagramy v aplikaci Visual Studio tak, aby bylo možné údaje zachytit, spravovat a pochopit v obou týmech:

|**Diagram**|**Udává**|
|------------------|-------------------|
|*Diagram činnosti (UML)*<br /><br /> Další informace:<br /><br /> -   [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md) dokumentace<br />-   [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Tok kroků, ke kterým dochází, když systém zjistí, že zákazník zadá objednávku z restaurace znovu a vyzve zákazníka k zápisu recenze.|
|*Diagram tříd (UML)*<br /><br /> Další informace:<br /><br /> -   [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) dokumentace<br />-   [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|Logické třídy a jejich vztahy. Například je přidána nová třída, která popisuje **kontrolu** a její vztahy s jinými entitami, jako je **restaurace**, **Nabídka**a **Zákazník**.<br /><br /> Aby bylo možné přidružit recenze k zákazníkovi, systém musí uchovávat údaje o zákaznících. Diagram tříd UML může přispět k objasnění těchto podrobností.|
|*Diagram tříd založený na kódu*<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Existující třídy v kódu.|
|*Diagram komponent (UML)*<br /><br /> Další informace:<br /><br /> -   [diagramů komponent UML: referenční](../modeling/uml-component-diagrams-reference.md) dokumentace<br />-   [diagramů komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|Části systému na nejvyšší úrovni, jako je například web večeře Now a jejich rozhraní. Tato rozhraní definují, jak komponenty spolu vzájemně komunikují prostřednictvím metod nebo služeb, které poskytují a využívají.|
|*Sekvenční diagram (UML)*<br /><br /> Další informace:<br /><br /> -   [sekvenčních diagramů UML: referenční](../modeling/uml-sequence-diagrams-reference.md) dokumentace<br />-   [sekvenčních diagramů UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|Sekvence interakcí mezi instancemi.|

 Například následující diagram komponent zobrazuje novou komponentu, která je součástí komponenty webu večeře Now. Komponenta ReviewProcessing zpracovává funkce pro vytváření recenzí a zobrazují se zvýrazněné oranžová:

 ![Diagram komponent UML](../modeling/media/uml-internal.png "UML_Internal")

 **Diagram komponent UML**

 Následující sekvenční diagram znázorňuje posloupnost interakcí, ke kterým dochází, když web večeře Now kontroluje, jestli zákazník objednal od restaurace. Pokud je to pravda, požádá zákazníka, aby vytvořil recenzi, která se pošle do restaurace a publikovala na webu:

 ![Sekvenční diagram UML](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **Sekvenční diagram UML**

### <a name="ValidatingCode"></a>Udržování kódu v souladu s návrhem
 Večeře teď musí zajistit, aby aktualizovaný kód zůstával v souladu s návrhem. Vytvářejí diagramy vrstev, které popisují vrstvy funkčnosti v systému, určují povolené závislosti mezi nimi a přiřadí artefakty řešení těmto vrstvám.

|**Znázorňuje**|**Udává**|
|-----------------|-------------------|
|*Diagram vrstev*<br /><br /> Další informace:<br /><br /> -   [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy vrstev: referenční](../modeling/layer-diagrams-reference.md) dokumentace<br />-   [diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|Logická architektura kódu.<br /><br /> Diagram vrstev uspořádává a mapuje artefakty v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení do abstraktních skupin nazývaných *vrstvy*. Tyto vrstvy identifikují role, úlohy nebo funkce, které tyto artefakty provádějí v systému.<br /><br /> Diagramy vrstev jsou užitečné pro popis zamýšleného návrhu systému a ověřování vývojového kódu s tímto návrhem.<br /><br /> Chcete-li vytvořit vrstvy, přetáhněte položky z Průzkumník řešení, mapy kódu, Zobrazení tříd a Prohlížeč objektů. Chcete-li nakreslit nové vrstvy, použijte panel nástrojů nebo klikněte pravým tlačítkem myši na plochu diagramu.<br /><br /> Chcete-li zobrazit existující závislosti, klikněte pravým tlačítkem myši na plochu diagramu vrstvy a pak klikněte na možnost **Generovat závislosti**. Chcete-li zadat zamýšlené závislosti, nakreslete nové závislosti.|

 Například následující diagram vrstvy popisuje závislosti mezi vrstvami a počet artefaktů, které jsou spojeny s každou vrstvou:

 ![Diagram vrstev integrovaného platebního systému](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagram vrstev**

 Aby se zajistilo, že v konfliktu s návrhem nedochází při vývoji kódu, týmy používají ověřování vrstev na sestaveních, která jsou spuštěna v sestavení Team Foundation Build. Také vytvoří vlastní úlohu MSBuild pro vyžadování ověření vrstvy při jejich operacích vrácení se změnami. Používají sestavy sestavení ke shromáždění chyb ověřování.

 Další informace:

- [Definování procesu sestavení](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Použití ověřovaného procesu sestavení se změnami k ověření změn](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Přizpůsobení šablony procesu sestavení](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="GeneralTips"></a>Obecné tipy pro vytváření a používání modelů

- Většina diagramů se skládá z uzlů, které jsou propojeny pomocí řádků. Pro každý typ diagramu poskytuje sada nástrojů různé druhy uzlů a řádků.

   Chcete-li otevřít sadu nástrojů, klikněte v nabídce **zobrazení** na příkaz **Sada nástrojů**.

- Chcete-li vytvořit uzel, přetáhněte jej ze sady nástrojů do diagramu. Některé druhy uzlů musí být přetaženy na existující uzly. Například v diagramu komponent musí být do existující součásti přidán nový port.

- Chcete-li vytvořit čáru nebo připojení, klikněte na příslušný nástroj na panelu nástrojů, klikněte na zdrojový uzel a potom klikněte na cílový uzel. Některé řádky lze vytvořit pouze mezi určitými typy uzlů. Když přesunete ukazatel na možný zdroj nebo cíl, ukazatel myši označuje, zda lze vytvořit připojení.

- Když vytváříte položky v diagramech UML, můžete je také přidat do společného modelu. Diagramy UML v projektu modelování jsou zobrazeními tohoto modelu. Položky v diagramu vrstev jsou součástí projektu modelování, i když nejsou uloženy ve společném modelu.

   Chcete-li zobrazit model, v nabídce **Architektura** přejděte na možnost **Windows**a potom klikněte na položku **Průzkumník modelů UML**.

- V některých případech můžete přetáhnout určité položky z **Průzkumníka modelů UML** do diagramu UML. Některé prvky v rámci stejného modelu lze použít pro zobrazení alternativních zobrazení architektury v několika nebo různých diagramech. Například můžete přetáhnout komponentu do jiného diagramu komponent nebo do sekvenčního diagramu pro použití jako objekt actor.

- Visual Studio podporuje UML 2.1.2. Tento přehled popisuje pouze hlavní funkce diagramů UML v této verzi, ale existuje mnoho knih, které projednávají s UML a jeho používání detailně.

  Viz [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).

### <a name="PlanningTracking"></a>Plánování a sledování práce
 Diagramy modelování sady Visual Studio jsou integrované s Team Foundation Server, takže můžete plánovat, spravovat a sledovat práci snadněji. Oba týmy používají modely k identifikaci testových případů a vývojářských úloh a k odhadování jejich práce. Společnost Lucerne vytvoří a propojí Team Foundation Server pracovní položky s prvky modelu, jako jsou například případy použití nebo komponenty. To pomáhá sledovat jejich průběh a sledovat jejich práci zpátky do požadavků uživatelů. To jim pomůže zajistit, aby jejich změny i nadále splňovaly tyto požadavky.

 Jak fungují, týmy aktualizují své pracovní položky tak, aby odrážely čas strávený na svých úkolech. Také monitorují a nastavují jejich práci pomocí následujících funkcí Team Foundation Server:

- Denní *sestavy Burndown* , které ukazují, zda budou dokončeny plánované práce v očekávaném čase. Generují další podobné sestavy z Team Foundation Server ke sledování průběhu chyb.

- *List iterace* , který používá aplikaci Microsoft Excel k usnadnění monitorování týmu a vyrovnání zatížení mezi jeho členy. Tento list je propojen s Team Foundation Server a poskytuje fokus na diskuzi během pravidelných setkání o průběhu.

- *Řídicí panel pro vývoj* , který používá Office Project, aby tým informoval o důležitých informacích o projektu.

  Další informace:

- [Sledování práce pomocí Visual Studio Team Services nebo Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md)

- [Grafy, řídicí panely a sestavy pro Visual Studio ALM](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Vytvoření nevyřízených položek a úkolů pomocí projektu](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="TestValidateCheckInCode"></a>Testování, ověřování a vrácení kódu se změnami
 Jak týmy dokončí každý úkol, kontrolují svůj kód do správy verzí Team Foundation a zobrazují připomenutí od Team Foundation Server, pokud jsou zapomenout. Předtím, než Team Foundation Server akceptuje jejich vrácení se změnami, týmy spustí testy jednotek a ověření vrstvy pro ověření kódu proti testovacím případům a návrhu. Používají Team Foundation Server ke spouštění sestavení, automatizované testování částí a pravidelného ověřování vrstev. To pomáhá zajistit, že kód splňuje následující kritéria:

- Funguje.

- Neruší předchozí pracovní kód.

- Nekoliduje s návrhem.

  Večeře teď má velkou kolekci automatizovaných testů, které může společnost Lucerne použít, protože skoro všechno stále platí. Společnost Lucerne může také vytvořit tyto testy a přidat nové, aby se pokryly nové funkce. Zároveň aplikace Visual Studio používá ke spouštění manuálních testů.

  Aby se zajistilo, že kód odpovídá návrhu, týmy konfigurují sestavení v Team Foundation buildu tak, aby zahrnovalo ověřování vrstvy. Pokud dojde k jakýmkoli konfliktům, vygeneruje se sestava s podrobnostmi.

  Další informace:

- [Testování aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)

- [Použít správu verzí](https://go.microsoft.com/fwlink/?LinkID=525605)

- [Sestavení aplikace](/azure/devops/pipelines/index)

## <a name="UpdatingSystem"></a>Aktualizace systému pomocí vizualizace a modelování
 Společnost Lucerne a večeře teď musí integrovat své platební systémy. Následující části znázorňují diagramy modelování v aplikaci Visual Studio, které jim pomůžou provést tuto úlohu:

- [Pochopení požadavků uživatelů: Diagramy případů použití](#UnderstandUseCases)

- [Pochopení obchodního procesu: diagramy činnosti](#UnderstandActivities)

- [Popis systémové struktury: diagramy komponent](#DescribeComponents)

- [Popsat interakce: sekvenční diagramy](#DescribeSequence)

- [Vizualizovat existující kód: mapy kódu](#VisualizeCode)

- [Definování glosáře typů: diagramy tříd](#DefineClasses)

- [Popište logickou architekturu: diagramy vrstev](#DescribeLayers)

  Další informace:

- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)

- [Vizualizace kódu](../modeling/visualize-code.md)

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)

- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

### <a name="UnderstandUseCases"></a>Pochopení požadavků uživatelů: Diagramy případů použití
 Diagramy případů použití shrnují aktivity, které systém podporuje a který provádí tyto činnosti. Společnost Lucerne používá diagram případu použití k tomu, aby se dozvěděla následující informace o systému večeře Now:

- Zákazníci vytvářejí objednávky.

- Restaurace obdrží objednávky.

- Externí brána pro platební procesor, kterou používá systém platby večeře Now k ověřování plateb, je mimo rozsah webu.

  Diagram také ukazuje, jak některé z hlavních případů použití jsou rozděleny do menších případů použití. Společnost Lucerne chce použít svůj vlastní platební systém. Zvýrazňují případ použití procesu platby odlišnou barvou, aby označoval, že vyžaduje změny:

  ![Zvýrazňování platby procesu v diagramu případu použití](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Zvýrazňování platby procesu v diagramu případu použití**

  Pokud čas vývoje byl krátký, tým se může pojednávat, jestli chce umožnit zákazníkům platit v restauracích přímo. Pokud to chcete zobrazit, nahradili byste případ použití platby procesu jedním z nich mimo hranici systému večeře Now. Budou pak zákazníka propojit přímo s restaurací, což značí, že večeře nyní bude zpracovávat pouze objednávky:

  ![Přeoborování mzdové Restaurace v diagramu případu použití](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Přeoborování mzdové Restaurace v diagramu případu použití**

  Další informace:

- [Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Vykreslení diagramu případu použití
 Diagram případu použití má následující hlavní funkce:

- *Objekty actor* reprezentují role přehrávané osobami, organizacemi, počítači nebo softwarovými systémy. Například zákazník, restaurace a systém pro platby na večeři nyní jsou aktéry.

- *Případy použití* reprezentují interakce mezi objekty actor a systémem ve vývoji.  Můžou představovat libovolné škálování interakce z jediného kliknutí myší nebo zprávy na transakci rozšířenou o několik dní.

- *Asociace* spojí objekty actor s případy použití.

- Větší případ použití může *zahrnovat* menší hodnoty, například vytvoření objednávky zahrnuje výběr restaurace. Můžete *rozšířit* případ použití, který přidá cíle a kroky k rozšířenému případu použití, aby označoval, že k případu použití dochází pouze za určitých podmínek. Případy použití mohou také dědit od sebe.

- *Podsystém* představuje softwarový systém, který je pod vývojem nebo některou z jeho součástí. Je to velké pole, které obsahuje případy použití. Diagram případu použití vysvětluje, co je uvnitř nebo vně hranice subsystému. Chcete-li určit, že uživatel musí provést určité cíle jinými způsoby, nakreslete tyto případy použití mimo hranici subsystému.

- *Artefakty* odkazují prvky v diagramu k ostatním diagramům nebo dokumentům.

  Další informace:

- [Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Shrnutí: silné stránky diagramů případů použití
 Diagramy případů použití vám pomůžou vizualizovat:

- Aktivity, které systém podporuje nebo nepodporuje

- Osoby a externí systémy, které provádějí tyto činnosti

- Hlavní součásti systému, které podporují jednotlivé aktivity, které můžete vyjádřit jako subsystémy vnořené v nadřazeném systému

- Jak se případ použití může rozdělit na menší hodnoty nebo variace

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Znázorňuje**|**Udává**|
|-----------------|-------------------|
|Diagram činnosti|Tok kroků v případu použití a těch, kteří provádějí tyto kroky v případu použití.<br /><br /> Názvy případů použití často zrcadlí kroky v diagramu činnosti. Diagramy činnosti podporují prvky, jako jsou rozhodnutí, sloučení, vstupy a výstupy, souběžné toky a tak dále.<br /><br /> Další informace:<br /><br /> -   [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md) dokumentace<br />-   [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|
|Sekvenční diagram|Sekvence interakcí mezi účastníky v případu použití.<br /><br /> Další informace:<br /><br /> -   [sekvenčních diagramů UML: referenční](../modeling/uml-sequence-diagrams-reference.md) dokumentace<br />-   [sekvenčních diagramů UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagram tříd (UML)|Entity nebo typy, které se účastní případu použití.<br /><br /> Další informace:<br /><br /> -   [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) dokumentace<br />-   [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="UnderstandActivities"></a>Pochopení obchodního procesu: diagramy činnosti
 Diagramy činnosti popisují tok kroků v podnikovém procesu a poskytují jednoduchý způsob, jak komunikovat pracovní postup. Vývojový projekt může mít více diagramů aktivit. Aktivita obvykle zahrnuje všechny akce, které jsou výsledkem jedné externí akce, jako je například objednání moučky, aktualizace nabídky nebo přidání nové restaurace do firmy. Aktivita může také popsat podrobnosti složitosti akce.

 Společnost Lucerne aktualizuje následující diagram činnosti, aby ukázala, že společnost Lucerne zpracuje platbu a zaplatí restauraci. Nahrazují platební systém v rámci programu Lucerne Now, jak je zvýrazněné:

 ![Systém platby Lucerne v diagramu činnosti](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Nahrazení platebního systému pro večeři nyní v diagramu činnosti**

 Aktualizovaný diagram pomáhá aplikacím Lucerne a večeře nyní vizualizovat, kde systém platby Lucerne zapadá do obchodního procesu. V této verzi se k identifikaci rolí, které provádějí kroky, používají komentáře. Řádky slouží k vytváření *plaveckých drah*, které organizují kroky podle rolí.

 Týmy mohou také zvážit diskuzi o alternativním článku, kde zákazník zaplatí restauraci místo od doručení objednávky. Tím se vytvoří různé požadavky na softwarový systém.

 V minulosti teď máte tyto diagramy na tabuli nebo v PowerPointu. Nyní také používají Visual Studio k vykreslování těchto diagramů, aby oba týmy mohly zachytit, pochopit a spravovat podrobnosti.

 Další informace:

- [Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)

- [Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Vykreslení diagramu činnosti
 Diagram činnosti má následující hlavní funkce:

- *Počáteční uzel* , který označuje první akci aktivity.

   Diagram by měl mít vždy jeden z těchto uzlů.

- *Akce* , které popisují postup, kdy uživatel nebo software provádí úlohu.

- *Řízení toků* , které zobrazují tok mezi akcemi.

- *Uzly rozhodnutí* , které reprezentují podmíněné větve v toku.

- *Uzly rozvětvení* , které rozdělí jednotlivé toky do souběžných toků.

- *Konečné uzly aktivity* , které zobrazují ukončení aktivity.

   I když jsou tyto uzly volitelné, je vhodné je zahrnout do diagramu, aby se zobrazilo, kde končí aktivita.

  Další informace:

- [Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)

- [Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Shrnutí: silné stránky diagramů činnosti
 Diagramy aktivit vám pomůžou vizualizovat a popsat tok řízení a informací mezi akcemi obchodního, systému nebo programu. Toto je jednoduchý a užitečný způsob, jak popsat pracovní postup při komunikaci s dalšími lidmi.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Znázorňuje**|**Popis**|
|-----------------|---------------------|
|Použití diagramu případu|Shrňte aktivity, které každý objekt actor provádí.<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) dokumentace<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagram součásti|Vizualizujte systém jako kolekci opakovaně použitelných částí, které poskytují nebo využívají chování prostřednictvím dobře definované sady rozhraní.<br /><br /> Další informace:<br /><br /> -   [diagramů komponent UML: referenční](../modeling/uml-component-diagrams-reference.md) dokumentace<br />-   [diagramů komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="DescribeComponents"></a>Popis systémové struktury: diagramy komponent
 Diagramy komponent popisují systém jako kolekci oddělitelných částí, které poskytují nebo využívají chování prostřednictvím dobře definované sady rozhraní. Části můžou být v jakémkoli měřítku a můžou se připojit jakýmkoli způsobem.

 Aby vám pomohla společnost Lucerne a večeře nyní vizualizovat a diskutovat o komponentách systému a jejich rozhraních, vytvářejí následující diagramy komponent:

 ![Externí komponenty v platebním systému](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Součásti platebního systému pro večeři**

 Tento diagram znázorňuje různé typy komponent a jejich *závislosti*. Například web večeře Now i platební systém Lucerne vyžadují, aby k ověřování plateb měl externí brána platebního procesoru. Šipky mezi součástmi reprezentují závislosti, které určují, které součásti vyžadují funkčnost jiných komponent.

 Chcete-li použít platební systém Lucerne, je nutné web večeře Now aktualizovat tak, aby používal rozhraní PaymentApproval a PayableInsertion v platebním systému Lucerne.

 Následující diagram znázorňuje konkrétní konfiguraci komponent pro web večeře Now. Tato konfigurace znamená, že všechny instance webu se skládají ze čtyř *částí*:

- CustomerProcessing

- OrderProcessing

- ReviewProcessing

- PaymentProcessing

  Tyto části jsou instancemi zadaných typů komponent a jsou propojeny následujícím způsobem:

  ![Komponenty v rámci webu večeře Now Now](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Komponenty uvnitř webu večeře Now**

  Web večeře Now deleguje své chování na tyto části, které zpracovávají funkce webu. Šipky mezi nadřazenou komponentou a jejími součástmi členů zobrazují *delegování* , která určují, které části zpracovávají zprávy, které nadřazený objekt přijímá nebo odesílá prostřednictvím svých rozhraní.

  V této konfiguraci komponenta PaymentProcessing zpracovává platby zákazníků. Proto je nutné ji aktualizovat, aby se mohla integrovat se platebním systémem společnosti Lucerne. V jiných scénářích může existovat více instancí typu komponenty ve stejné nadřazené komponentě.

  Další informace:

- [Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)

- [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Kreslení diagramu komponent
 Diagram komponent má následující hlavní funkce:

- *Komponenty* , které reprezentují oddělitelné součásti systémových funkcí.

- *Poskytnuté porty rozhraní* , které představují skupiny zpráv nebo volání implementující komponenty a používané jinými komponentami nebo externími systémy.

- *Požadované porty rozhraní* , které reprezentují skupiny zpráv nebo volání, které součásti odesílají do jiných součástí nebo externích systémů. Tento druh portu popisuje operace, které součást přinejmenším očekává od jiných komponent nebo externích systémů.

- *Součásti jsou členy* součástí a obvykle jsou instancemi jiných komponent. Část je částí interního návrhu nadřazené komponenty.

- *Závislosti* , které naznačují komponenty, vyžadují funkčnost dalších komponent.

- *Delegování* , která označují části komponenty, zpracovávají zprávy odesílané nebo přijímané nadřazenou komponentou.

  Další informace:

- [Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)

- [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Shrnutí: silné stránky diagramů komponent
 Diagramy komponent vám pomůžou vizualizovat:

- Systém jako kolekce oddělitelných částí bez ohledu na jejich implementační jazyk nebo styl.

- Komponenty s dobře definovanými rozhraními, které usnadňují pochopení a aktualizaci návrhu při změně požadavků.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Znázorňuje**|**Popis**|
|-----------------|---------------------|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li identifikovat kandidáty na komponenty, vytvořte mapu kódu a seskupte položky podle jejich funkce v systému.<br /><br /> Další informace:<br /><br /> -   [závislosti map napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)|
|Sekvenční diagram|Vizualizujte posloupnost interakcí mezi komponentami nebo částmi uvnitř komponenty.<br /><br /> Chcete-li vytvořit životnost v sekvenčním diagramu ze součásti, klikněte pravým tlačítkem myši na součást a potom klikněte na možnost **vytvořit životnost**.<br /><br /> Další informace:<br /><br /> -   [sekvenčních diagramů UML: referenční](../modeling/uml-sequence-diagrams-reference.md) dokumentace<br />-   [sekvenčních diagramů UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagram tříd (UML)|Definujte rozhraní na poskytnutých nebo požadovaných portech a třídách, které implementují funkce komponent.<br /><br /> Další informace:<br /><br /> -   [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) dokumentace<br />-   [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram vrstvy|Popište logickou architekturu systému v souvislosti se součástmi. Použijte ověřování vrstvy, abyste se ujistili, že kód zůstává v souladu s návrhem.<br /><br /> Další informace:<br /><br /> -   [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy vrstev: referenční](../modeling/layer-diagrams-reference.md) dokumentace<br />-   [diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|
|Diagram činnosti|Vizualizujte vnitřní zpracování, které komponenty provádějí v reakci na příchozí zprávy.<br /><br /> Další informace:<br /><br /> -   [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md) dokumentace<br />-   [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="VisualizeCode"></a>Vizualizovat existující kód: mapy kódu
 Mapy kódu ukazují aktuální organizaci a vztahy v kódu. Položky jsou reprezentovány *uzly* na mapě a vztahy jsou reprezentovány pomocí *odkazů*. Mapy kódu vám mohou pomáhat při provádění následujících typů úloh:

- Prozkoumejte Neznámý kód.

- Pochopení, kde a jak může navrhovaná změna ovlivnit existující kód.

- Najděte oblasti složitosti, přirozených vrstev a vzorů nebo jiných oblastí, které mohou být výhodné pro zlepšení.

  Například večeře teď musí odhadnout náklady na aktualizaci komponenty PaymentProcessing. Tato změna závisí částečně na tom, kolik změn bude mít vliv na ostatní části systému. Abychom jim mohli porozumět, jeden z vývojářů v současnosti nyní generuje mapy kódu z kódu a upraví fokus oboru na oblasti, které by mohly být ovlivněny změnou.

  Následující mapa znázorňuje závislosti mezi třídou PaymentProcessing a dalšími částmi v systému večeře Now, která se zobrazí jako vybraná:

  ![Graf závislosti pro platební systém pro večeři nyní](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Mapa kódu pro platební systém pro večeři Now**

  Vývojář prozkoumá mapu rozbalením třídy PaymentProcessing a výběrem jejích členů zobrazíte oblasti, které jsou potenciálně ovlivněny:

  ![Metody uvnitř PaymentProcessing a závislosti](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **Metody uvnitř třídy PaymentProcessing a jejich závislosti**

  Generují následující mapu pro platební systém Lucerne ke kontrole jeho tříd, metod a závislostí. Tým uvidí, že systém Lucerne může také vyžadovat práci k interakci s ostatními součástmi večeře nyní:

  ![Graf závislosti pro platební systém Lucerne](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Mapa kódu pro platební systém Lucerne**

  Oba týmy pracují společně, aby určily změny, které jsou potřeba k integraci těchto dvou systémů. Rozhodnou se k refaktorování kódu, aby bylo snazší ho aktualizovat. Třída PaymentApprover se přesune do oboru názvů DinnerNow. Business a bude vyžadovat některé nové metody. Třídy večeře Now, které zpracovávají transakce, budou mít svůj vlastní obor názvů. Týmy vytvářejí a používají pracovní položky k plánování, uspořádání a sledování práce. Propojí pracovní položky s prvky modelu, kde je to užitečné.

  Po reorganizaci kódu generují týmy novou mapu kódu pro zobrazení aktualizované struktury a vztahů:

  ![Graf závislosti se stejným uspořádáním kódu](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **Mapa kódu se stejným uspořádáním kódu**

  Tato mapa znázorňuje, že třída PaymentApprover je nyní v oboru názvů DinnerNow. Business a obsahuje některé nové metody. Třídy transakce večeře Now nyní mají svůj vlastní obor názvů PaymentSystem, což usnadňuje práci s tímto kódem později.

#### <a name="creating-a-code-map"></a>Vytvoření mapy kódu

- Chcete-li získat rychlý přehled o zdrojovém kódu, postupujte podle těchto kroků a vygenerujte mapu kódu:

     V nabídce **Architektura** klikněte na možnost **Generovat mapu kódu pro řešení**.

     Pro rychlý přehled zkompilovaného kódu vytvořte prázdnou mapu kódu a pak přetáhněte soubory sestavení nebo binární soubory na plochu rozvržení.

- Chcete-li prozkoumat konkrétní kód nebo položky řešení, použijte Průzkumník řešení k výběru položek a relací, které chcete vizualizovat. Pak můžete buď vygenerovat novou mapu, nebo přidat vybrané položky do existující mapy. Podívejte [se na téma mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md).

- Abychom vám pomohli prozkoumat mapu, uspořádejte rozložení tak, aby vyhovovalo typům úloh, které chcete provést.

     Například pro vizualizaci vrstvení v kódu vyberte rozložení stromové struktury. Viz [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Shrnutí: síly map kódu
 Mapy kódu vám pomůžou:

- Přečtěte si o organizaci a vztazích v existujícím kódu.

- Identifikujte oblasti, které mohou být ovlivněny navrhovanou změnou.

- Najděte oblasti složitosti, vzory, vrstvy nebo jiné oblasti, které byste mohli vylepšit, aby bylo snazší udržovat, měnit a opakovaně používat kód.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Znázorňuje**|**Udává**|
|-----------------|-------------------|
|Diagram vrstvy|Logická architektura systému. Použijte ověřování vrstvy, abyste se ujistili, že kód zůstává v souladu s návrhem.<br /><br /> Pro snadnější identifikaci existujících vrstev nebo zamýšlených vrstev vytvořte mapu kódu a položky související se skupinami. Chcete-li vytvořit diagram vrstvy, přečtěte si:<br /><br /> -   [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)|
|Diagram součásti|Komponenty, jejich rozhraní a jejich vztahy.<br /><br /> Abyste mohli identifikovat komponenty, vytvořte mapu kódu a seskupte položky podle jejich funkce v systému.<br /><br /> Další informace:<br /><br /> -   [diagramů komponent UML: referenční](../modeling/uml-component-diagrams-reference.md) dokumentace<br />-   [diagramů komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|
|Diagram tříd (UML)|Třídy, jejich atributy a operace a jejich vztahy.<br /><br /> Pro usnadnění identifikace těchto prvků vytvořte diagram tříd UML, který tyto prvky zobrazuje.<br /><br /> Další informace:<br /><br /> -   [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) dokumentace<br />-   [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram tříd (založený na kódu)|Existující třídy v kódu pro určitý projekt.<br /><br /> Chcete-li vizualizovat a upravit existující třídu v kódu, použijte Návrhář tříd.<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="DescribeSequence"></a>Popsat interakce: sekvenční diagramy
 Sekvenční diagramy popisují řadu interakcí mezi částmi systému. Části mohou být libovolné škály. Například může být v rozsahu od jednotlivých objektů v programu až po velké subsystémy nebo externí objekty Actors. Interakce můžou být libovolného rozsahu a typu. Například mohou být v rozsahu od jednotlivých zpráv až po rozšířené transakce a mohou být volání funkcí nebo zprávy webové služby.

 Abychom vám pomohli společnosti Lucerne a večeře nyní popsat a diskutovat o krocích v případu použití platby procesu, vytvoří následující sekvenční diagram z diagramu komponent. Životnosti zrcadlí jako součást webu večeře Now a jeho části. Zprávy, které se zobrazují mezi životnosti, následují po připojeních v diagramech komponent:

 ![Sekvenční diagram pro případ použití platby procesu](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Sekvenční diagram případu použití platby procesu**

 Sekvenční diagram ukazuje, že když zákazník vytvoří objednávku, web večeře Now volá ProcessOrder na instanci OrderProcessing. V dalším kroku OrderProcessing volá ProcessPayment na PaymentProcessing. To pokračuje, dokud brána externích platebních procesorů platbu neověří. Pak se ovládací prvek vrátí zpět na web večeře Now.

 Společnost Lucerne musí odhadnout náklady na aktualizaci platebního systému pro integraci se systémem večeře Now. Abychom jim pomohli tyto informace pochopit, mohou také vytvořit mapy kódu pro vizualizaci ovlivněného kódu.

 Další informace:

- [Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)

- [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Vykreslení sekvenčního diagramu
 Sekvenční diagram má následující hlavní funkce:

- Svislé *životnosti* znázorňují objekty actor nebo instance softwarových objektů.

   Chcete-li přidat symbol objektu actor, který indikuje, že účastník je mimo systém ve vývoji, klikněte na životnost. V okně **vlastnosti** nastavte **objekt actor** na **hodnotu true**. Pokud okno **vlastnosti** není otevřené, stiskněte **F4**.

- Horizontální *zprávy* reprezentují volání metod, zprávy webové služby nebo jinou komunikaci. *Výskyty spuštění* jsou svislé šedé obdélníky, které se zobrazí na životnostech a představují období, během kterých přijímající objekty zpracovávají volání.

- Během *synchronní* zprávy čeká objekt odesílateli řízení <\<vrácení > > jako při běžném volání funkce. Během *asynchronní* zprávy může odesílatel pokračovat okamžitě.

- Pomocí <\<vytvořit > > zprávy pro indikaci konstrukce objektů jinými objekty. Mělo by se jednat o první zprávu odeslanou objektu.

  Další informace:

- [Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)

- [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Shrnutí: síly sekvenčních diagramů
 Sekvenční diagramy vám pomůžou vizualizovat:

- Tok řízení, který přenáší mezi objekty actor a objekty během provádění případu použití.

- Implementace volání metody nebo zprávy.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Znázorňuje**|**Popis**|
|-----------------|---------------------|
|Diagram tříd (UML)|Definujte třídy, které představují životnost, a parametry a návratové hodnoty, které jsou používány ve zprávách odesílaných mezi životnostmi.<br /><br /> Chcete-li vytvořit třídu z životnosti, klikněte pravým tlačítkem na životnost a pak klikněte na **vytvořit třídu** nebo **vytvořit rozhraní**. Chcete-li vytvořit životnost z typu v diagramu tříd, klikněte pravým tlačítkem na typ a pak klikněte na **vytvořit životnost**.<br /><br /> Další informace:<br /><br /> -   [diagramů tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) dokumentace<br />-   [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram součásti|Popište komponenty, které životnost představují, a rozhraní, která poskytují a využívají chování reprezentované zprávami.<br /><br /> Chcete-li vytvořit životnost z diagramu komponent, klikněte pravým tlačítkem myši na součást a potom klikněte na možnost **vytvořit životnost**.<br /><br /> Další informace:<br /><br /> -   [diagramů komponent UML: referenční](../modeling/uml-component-diagrams-reference.md) dokumentace<br />-   [diagramů komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|
|Použití diagramu případu|Shrňte interakce mezi uživateli a komponentami v sekvenčním diagramu jako případ použití, který představuje cíl uživatele.<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) dokumentace<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="DefineClasses"></a>Definování glosáře typů: diagramy tříd
 Diagramy tříd definují entity, pojmy nebo koncepty, které jsou součástí systému a jejich vztahů mezi sebou. Například můžete použít tyto diagramy během vývoje k popisu atributů a operací pro každou třídu, bez ohledu na jejich jazyk implementace nebo styl.

 Aby mohl společnost Lucerne popsat a diskutovat entity, které se účastní případu použití procesu platby, nakreslí následující diagram tříd:

 ![Zpracování entit plateb v diagramu tříd](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Zpracování entit platby v diagramu tříd**

 Tento diagram znázorňuje, že zákazník může mít mnoho objednávek a různé způsoby platby za objednávky. BankAccount a CreditCard dědí z platby.

 Během vývoje používá společnost Lucerne následující diagram tříd k popisu a diskuzi o podrobnostech každé třídy:

 ![Podrobnosti o zpracování platebních entit v diagramu tříd](../modeling/media/uml-payment.png "UML_Payment")

 **Podrobnosti o platbě procesu v diagramu tříd**

 Další informace:

- [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)

- [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>Kreslení diagramu tříd
 Diagram tříd má následující hlavní funkce:

- Typy jako třídy, rozhraní a výčty:

  - *Třída* je definice objektů, které sdílejí konkrétní strukturální nebo behaviorální charakteristiky.

  - *Rozhraní* definuje část externě viditelného chování objektu.

  - *Výčet* je klasifikátor, který obsahuje seznam hodnot literálů.

- *Atributy* jsou hodnoty určitého typu, které popisují každou instanci *třídění*. Klasifikátor je obecný název pro typy, komponenty, případy použití a dokonce i aktéry.

- *Operace* jsou metody nebo funkce, které mohou instance klasifikátoru provádět.

- *Asociace* označuje určitý druh vztahů mezi dvěma klasifikátory.

  - *Agregace* je přidružení, které označuje sdílené vlastnictví mezi klasifikátory.

  - *Složení* je přidružení, které označuje vztah celku mezi tříděními.

    Chcete-li zobrazit agregace nebo kompozice, nastavte vlastnost **agregace** u přidružení. **Shared** zobrazuje agregace a **složená** sestavení.

- *Závislost* označuje, že změna definice jednoho klasifikátoru může změnit definici jiného třídění.

- *Generalizace* značí, že konkrétní třídění dědí část své definice z obecného třídění. *Realizace* označuje, že třída implementuje operace a atributy nabízené rozhraním.

   Chcete-li vytvořit tyto relace, použijte nástroj **Dědičnost** . Alternativně může být realizace vyjádřena jako *Lupa*.

- *Balíčky* jsou skupiny klasifikátorů, přidružení, životnosti, komponent a dalších balíčků. *Import* vztahů označuje, že jeden balíček zahrnuje všechny definice jiného balíčku.

  Jako výchozí bod pro zkoumání a diskuzi o existujících třídách můžete použít Návrhář tříd k vytváření diagramů tříd z kódu.

  Další informace:

- [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)

- [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Shrnutí: silné stránky diagramů tříd
 Diagramy tříd vám pomůžou definovat:

- Společný Glosář termínů, který se má použít při projednávání potřeb uživatelů a entit, které jsou součástí systému. Viz [Model požadavky uživatelů na uživatele](../modeling/model-user-requirements.md).

- Typy, které jsou používány částmi systému, jako jsou komponenty, bez ohledu na jejich implementaci. Podívejte [se na téma modelování architektury vaší aplikace](../modeling/model-your-app-s-architecture.md).

- Relace, například závislosti, mezi typy. Můžete například zobrazit, že jeden typ může být přidružen k více instancím jiného typu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Znázorňuje**|**Popis**|
|-----------------|---------------------|
|Použití diagramu případu|Definujte typy, které se používají k popisu cílů a kroků v případech použití.<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) dokumentace<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagram činnosti|Definujte typy dat, která procházejí uzly objektů, vstupními kolíky, výstupními kolíky a uzly parametrů aktivity.<br /><br /> Další informace:<br /><br /> -   [diagramy činnosti UML: referenční](../modeling/uml-activity-diagrams-reference.md) dokumentace<br />-   [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagram součásti|Popisují komponenty, jejich rozhraní a jejich vztahy. Třída může také popsat kompletní komponentu.<br /><br /> Další informace:<br /><br /> -   [diagramů komponent UML: referenční](../modeling/uml-component-diagrams-reference.md) dokumentace<br />-   [diagramů komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|
|Diagram vrstvy|Definujte logickou architekturu systému v souvislosti se třídami.<br /><br /> Použijte ověřování vrstvy, abyste se ujistili, že kód zůstává v souladu s návrhem.<br /><br /> Další informace:<br /><br /> -   [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy vrstev: referenční](../modeling/layer-diagrams-reference.md) dokumentace<br />-   [diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|
|Sekvenční diagram|Definujte typy životností a operace, parametry a návratové hodnoty pro všechny zprávy, které může životnost získat.<br /><br /> Chcete-li vytvořit životnost z typu v diagramu tříd, klikněte pravým tlačítkem na typ a pak klikněte na **vytvořit životnost**.<br /><br /> Další informace:<br /><br /> -   [sekvenčních diagramů UML: referenční](../modeling/uml-sequence-diagrams-reference.md) dokumentace<br />-   [sekvenčních diagramů UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li identifikovat třídy, jejich vztahy a jejich metody, vytvořte mapu kódu, která tyto prvky zobrazí.<br /><br /> Další informace:<br /><br /> -   [závislosti map napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="DescribeLayers"></a>Popište logickou architekturu: diagramy vrstev
 Diagramy vrstev popisují logickou architekturu systému uspořádáním artefaktů ve vašem řešení do abstraktních skupin nebo *vrstev*. Artefakty mohou být mnoho věcí, například obory názvů, projekty, třídy, metody a tak dále. Vrstvy reprezentují a popisují role nebo úkoly, které artefakty provádějí v systému. Můžete také zahrnout ověřování vrstvy do sestavení a operace vrácení se změnami, abyste se ujistili, že kód zůstává v souladu s jeho návrhem.

 Chcete-li zachovat kód v souladu s návrhem, večeře Now a Lucerne použijte následující diagram vrstev k ověření kódu při jeho vývoje:

 ![Diagram vrstev integrovaného platebního systému](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagram vrstev pro večeři je teď integrovaný s vojtěškou.**

 Vrstvy na tomto diagramu odkazují na odpovídající artefakty řešení večeře Now a Lucerne. Například obchodní vrstva odkazuje na obor názvů DinnerNow. Business a její členy, které nyní obsahují třídu PaymentApprover. Vrstva přístupu k prostředkům odkazuje na obor názvů DinnerNow. data. Šipky nebo *závislosti*určují, že funkce ve vrstvě přístupu k prostředkům může používat jenom obchodní vrstva. Jak týmy aktualizují svůj kód, provádí se pravidelné ověřování vrstev za účelem zachycení konfliktů při jejich výskytu a k usnadnění jejich řešení.

 Týmy spolupracují na přírůstkové integraci a testování těchto dvou systémů. Nejprve se ujistěte, že PaymentApprover a zbytek hostina teď pracují s jiným systémem úspěšně, než budou pracovat s PaymentProcessing.

 Následující mapa kódu ukazuje nová volání mezi večeři Now a PaymentApprover:

 ![Aktualizovaný graf závislosti s integrovaným systémem](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Mapa kódu s aktualizovanými voláními metody**

 Po potvrzení, že systém funguje podle očekávání, večeře teď Zakomentovat kód PaymentProcessing. Sestavy ověření vrstvy jsou čisté a výsledná mapa kódu ukazuje, že neexistují žádné další závislosti PaymentProcessing:

 ![Graf závislosti bez PaymentProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **Mapa kódu bez PaymentProcessing**

#### <a name="drawing-a-layer-diagram"></a>Vykreslení diagramu vrstev
 Diagram vrstev má následující hlavní funkce:

- *Vrstvy* popisují logické skupiny artefaktů.

- *Odkaz* je přidružení mezi vrstvou a artefaktem.

   Chcete-li vytvořit vrstvy z artefaktů, přetáhněte položky z Průzkumník řešení, mapy kódu, Zobrazení tříd nebo Prohlížeč objektů. Chcete-li nakreslit nové vrstvy a propojit je s artefakty, použijte panel nástrojů nebo klikněte pravým tlačítkem myši na plochu diagramu, vytvořte vrstvy a přetáhněte položky do těchto vrstev.

   Číslo ve vrstvě znázorňuje počet artefaktů, které jsou propojeny s vrstvou. Tyto artefakty mohou být obory názvů, projekty, třídy, metody a tak dále. Při interpretaci počtu artefaktů ve vrstvě mějte na paměti následující:

  - Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.

     Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.

  - Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.

    Chcete-li zobrazit artefakty, které jsou propojeny s vrstvou, klikněte pravým tlačítkem myši na vrstvu a potom kliknutím na možnost **Zobrazit odkazy** otevřete **Průzkumníka vrstev**.

- *Závislost* znamená, že jedna vrstva může použít funkci v jiné vrstvě, ale ne naopak. *Obousměrná závislost* znamená, že jedna vrstva může použít funkci v jiné vrstvě a naopak.

   Chcete-li zobrazit existující závislosti v diagramu vrstev, klikněte pravým tlačítkem myši na plochu diagramu a potom klikněte na možnost **Generovat závislosti**. Chcete-li popsat zamýšlené závislosti, nakreslete nové.

  Další informace:

- [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)

- [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)

- [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Shrnutí: silné stránky diagramů vrstev
 Diagramy vrstev vám pomůžou:

- Popište logickou architekturu systému v závislosti na funkcích jeho artefaktů.

- Ujistěte se, že kód ve vývoji odpovídá zadanému návrhu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Znázorňuje**|**Popis**|
|-----------------|---------------------|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li vytvořit vrstvy, vygenerujte mapu kódu a pak položky na mapě seskupte jako potenciální vrstvy. Přetáhněte skupiny z mapy do diagramu vrstev.<br /><br /> Další informace:<br /><br /> -   [závislosti map napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />-   [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)|
|Diagram součásti|Popisují komponenty, jejich rozhraní a jejich vztahy.<br /><br /> Chcete-li vizualizovat vrstvy, vytvořte diagram komponent, který popisuje funkčnost různých komponent systému.<br /><br /> Další informace:<br /><br /> -   [diagramů komponent UML: referenční](../modeling/uml-component-diagrams-reference.md) dokumentace<br />-   [diagramů komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Externí prostředky

|**Kategorií**|**Odkazy**|
|------------------|---------------|
|**Fóra**|-   [nástrojů pro modelování sady Visual Studio pro vizualizaci &](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](https://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Viz také
 [Vizualizujte kód](../modeling/visualize-code.md) [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md) [použití modelů v procesu vývoje](../modeling/use-models-in-your-development-process.md) [použití modelů v agilním vývoji](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) . [při vývoji](../modeling/validate-your-system-during-development.md) [rozšíříte modely a diagramy UML](../modeling/extend-uml-models-and-diagrams.md) do systému.
