---
title: 'Scénář: Změna návrhu pomocí vizualizace a modelování | Dokumenty společnosti Microsoft'
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
ms.openlocfilehash: 70cc3c81c426ec55d0afb36360155786ec97d937
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302313"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scénář: Změna návrhu pomocí vizualizace a modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ujistěte se, že váš softwarový systém splňuje potřeby uživatelů pomocí vizualizačních a modelovacích nástrojů v sadě Visual Studio. Pomocí nástrojů, jako jsou diagramy UML (Unified Modeling Language), mapy kódu, diagramy vrstev a diagramy tříd, můžete použít k:

 Informace o tom, které verze sady Visual Studio podporují jednotlivé nástroje, naleznete [v tématu Podpora verzí pro architekturu a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Vyjasněte požadavky uživatelů a obchodní procesy.

- Vizualizujte a prozkoumejte existující kód.

- Popište změny existujícího systému.

- Ověřte, zda systém splňuje své požadavky.

- Udržujte kód v souladu s návrhem.

  Tento návod:

- Popisuje, jak mohou tyto nástroje využívat váš softwarový projekt.

- Ukazuje, jak můžete použít tyto nástroje, bez ohledu na váš vývojový přístup, s ukázkovým scénářem.

  Další informace o těchto nástrojích a scénářích, které podporují, najdete v následujících tématech:

- [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)

- [Vizualizace kódu](../modeling/visualize-code.md)

- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)

## <a name="scenario-overview"></a><a name="ScenarioOverview"></a>Přehled scénářů
 Tento scénář popisuje epizody z životního cyklu vývoje softwaru dvou fiktivních společností: Dinner Now a Lucerne Publishing. Dinner Now poskytuje webovou službu doručování jídel v Seattlu. Zákazníci si mohou objednat jídlo a zaplatit za ně na večeři nyní webu. Objednávky jsou pak odeslány do příslušné místní restaurace k doručení. Lucerne Publishing, společnost v New Yorku, provozuje několik firem jak off, tak na webu. Například provozují web, na kterém mohou zákazníci zveřejňovat recenze restaurací.

 Lucerne nedávno získal večeři nyní a chce provést následující změny:

- Integrujte jejich weby přidáním funkcí kontroly restaurací do aplikace Dinner Now.

- Nahraďte platební systém Dinner Now systémem Lucerne.

- Rozbalte službu Večeři v celém regionu.

  Večeře nyní používá SCRUM a eXtreme programování. Mají velmi vysoké pokrytí testu a velmi málo nepodporovaného kódu. Minimalizují rizika vytvořením malých, ale funkčních verzí systému a následným přírůstkovým přidáváním funkcí. Vyvíjejí svůj kód přes krátké a časté iterace. To jim umožňuje přijmout změny s jistotou, refaktorovat kód často a vyhnout se "velký design dopředu".

  Lucerne udržuje mnohem větší a komplexní sbírku systémů, z nichž některé jsou více než 40 let staré. Jsou velmi opatrní při provádění změn z důvodu složitosti a rozsahu staršího kódu. Řídí se přísnějším procesem vývoje, dávají přednost návrhu podrobných řešení a dokumentují návrh a změny, ke kterým dochází během vývoje.

  Oba týmy používají diagramy modelování v sadě Visual Studio, které jim pomáhají vyvíjet systémy, které splňují potřeby uživatelů. Společně s dalšími nástroji používají team foundation server, který jim pomáhá plánovat, organizovat a spravovat jejich práci.

  Další informace o serveru Team Foundation Server naleznete v tématu:

- [Plánování a sledování práce](#PlanningTracking)

- [Testování, ověřování a vrácení aktualizovaného kódu se změnami](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Role architektury a diagramů modelování ve vývoji softwaru
 Následující tabulka popisuje role, které mohou tyto nástroje hrát v různých a různých fázích životního cyklu vývoje softwaru:

||**Modelování požadavků uživatelů**|**Modelování obchodních procesů**|**Systémová architektura & návrh**|**Vizualizace kódu & průzkum**|**Ověření**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Diagram případu použití (UML)|√|√|||√|
|Diagram činnosti (UML)|√|√|√||√|
|Diagram třídy (UML)|√|√|√||√|
|Diagram komponent (UML)|√|√|√||√|
|Sekvenční diagram (UML)|√|√|√||√|
|Diagram jazyka specifického pro doménu (DSL)|√|√|√|||
|Diagram vrstvy, ověření vrstvy|||√|√|√|
|Mapa kódu|||√|√|√|
|Návrhář třídy (na základě kódu)||||√||

 Chcete-li nakreslit diagramy UML a diagramy vrstev, musíte vytvořit projekt modelování jako součást existujícího nebo nového řešení. Tyto diagramy musí být vytvořeny v projektu modelování. Položky v diagramech UML jsou součástí společného modelu a diagramy UML jsou pohledy tohoto modelu. Položky v diagramech vrstev jsou umístěny v projektu modelování, ale nejsou uloženy ve společném modelu. Mapy kódu a diagramy tříd .NET vytvořené z kódu existují mimo projekt modelování.

 Přečtěte si:

- [Vytváření projektů a diagramů pomocí modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Chcete-li zobrazit alternativní zobrazení architektury, můžete znovu použít určité prvky ze stejného modelu na více nebo různých diagramech. Můžete například přetáhnout komponentu do jiného diagramu komponenty nebo do sekvenčního diagramu, aby mohla fungovat jako objekt actor. Viz [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

  Oba týmy také použít ověření vrstvy k ujistěte se, že kód ve vývoji zůstává konzistentní s návrhem.

  Přečtěte si:

- [Zachování kódu v souladu s návrhem](#ValidatingCode)

- [Popište logickou architekturu: diagramy vrstev](#DescribeLayers)

- [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Některé verze sady Visual Studio podporují ověřování vrstev a verze map kódu jen pro čtení a diagramy UML pro vizualizaci a modelování. Informace o tom, které verze sady Visual Studio tuto funkci podporují, naleznete [v tématu Podpora verzí pro architekturu a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understanding-and-communicating-information-about-the-system"></a><a name="UnderstandingCommunicating"></a>Porozumění a sdělování informací o systému
 Neexistuje žádné předepsané pořadí pro použití diagramy modelování sady Visual Studio, takže je můžete použít tak, aby odpovídaly vašim potřebám nebo přístupu. Týmy obvykle v průběhu projektu iterativně a často znovu navštěvují své modely. Každý diagram nabízí konkrétní silné stránky, které vám pomohou pochopit, popsat a komunikovat různé aspekty systému ve vývoji.

 Večeře nyní a Lucerne komunikovat mezi sebou navzájem a se zúčastněnými stranami projektu pomocí diagramů jako jejich společný jazyk. Například Večeři nyní používá diagramy k provádění těchto úkolů:

- Vizualizujte existující kód.

- Komunikujte s Lucerne o nových nebo aktualizovaných uživatelských scénářích.

- Identifikujte změny, které jsou nutné pro podporu nových nebo aktualizovaných uživatelských scénářů.

  Lucerne používá diagramy k provádění těchto úkolů:

- Přečtěte si o obchodním procesu Večeři nyní.

- Pochopte návrh systému.

- Komunikujte s večeří nyní o nových nebo aktualizovaných požadavcích uživatelů.

- Aktualizace dokumentu systému.

  Diagramy jsou integrovány se serverem Team Foundation Server, takže týmy mohou snadněji plánovat, spravovat a sledovat svou práci. Například používají modely k identifikaci testovacích případů a vývojových úloh a k odhadu jejich práce. Lucerne propojí pracovní položky team foundation server na prvky modelu tak, aby mohly sledovat průběh a ujistěte se, že systém splňuje požadavky uživatelů. Například propojují případy použití s pracovními položkami testovacího případu, aby viděli, že případy použití jsou splněny při průchodu všech testů.

  Před týmy zkontrolovat jejich změny, ověří kód proti testy a návrh spuštěním sestavení, které zahrnují ověření vrstvy a automatizované testy. To pomáhá zajistit, že aktualizovaný kód není v konfliktu s návrhem a přerušení dříve pracovní funkce.

  Přečtěte si:

- [Pochopení úlohy systému v obchodním procesu](#UnderstandingBPMandSystemDesign)

- [Popis nových nebo aktualizovaných požadavků uživatelů](#DescribingURM)

- [Vytváření testů z modelů](#CreatingTests)

- [Identifikace změn stávajícího systému](#DeterminingChanges)

- [Zachování kódu v souladu s návrhem](#ValidatingCode)

- [Obecné tipy pro vytváření a používání modelů](#GeneralTips)

- [Plánování a sledování práce](#PlanningTracking)

- [Testování, ověřování a vrácení aktualizovaného kódu se změnami](#TestValidateCheckInCode)

### <a name="understanding-the-role-of-the-system-in-the-business-process"></a><a name="UnderstandingBPMandSystemDesign"></a>Pochopení role systému v obchodním procesu
 Lucerne se chce dozvědět více o obchodní proces večeři nyní. Vytvářejí následující diagramy, aby objasnily své porozumění s večeří nyní snadněji:

|**Diagram**|**Popisuje**|
|-----------------|-------------------|
|*Diagram případu použití (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy případu použití UML: Odkaz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|- Aktivity, které podporuje systém Dinner Now<br />- Lidé a externí systémy, které vykonávají činnosti<br />- Hlavní složky systému, které podporují každou činnost<br />- Části obchodního procesu, které jsou mimo rozsah současného systému, například dodávky potravin|
|*Diagram činnosti (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy aktivit UML: Odkaz](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktivit UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Tok kroků, ke kterým dochází, když zákazník vytvoří objednávku|
|*Diagram třídy (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy tříd UML: Odkaz](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|Obchodní entity a termíny, které se používají v diskusi a vztahy mezi těmito entitami. Například Order a Menu Item jsou součástí slovníku v tomto scénáři.|

 Například Lucerne vytvoří následující diagram případu použití pochopit úkoly, které jsou prováděny na večeři nyní webu a kdo je provádí:

 ![Diagram případu použití UML](../modeling/media/uml-usecase.png "UML_UseCase")

 **Diagram případu použití UML**

 Následující diagram činnosti popisuje tok kroků, když zákazník vytvoří objednávku na webu Večeři nyní. V této verzi prvky komentářů identifikují role a čáry vytvářejí *plavecké dráhy*, které organizují kroky podle role:

 ![Diagram činnosti UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **Diagram činnosti UML**

 Následující diagram třídy popisuje entity, které se účastní procesu pořadí:

 ![Diagram tříd UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **Diagram tříd UML**

### <a name="describing-new-or-updated-user-requirements"></a><a name="DescribingURM"></a>Popis nových nebo aktualizovaných požadavků uživatelů
 Lucerne chce přidat funkce do systému Večeři nyní tak, aby zákazníci mohli číst a přispívat recenze restaurací. Aktualizují následující diagramy tak, aby mohli popsat a diskutovat o tento nový požadavek s večeří nyní:

|**Diagram**|**Popisuje**|
|-----------------|-------------------|
|*Diagram případu použití (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy případu použití UML: Odkaz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|Nový případ použití pro "Napsat recenzi restaurace"|
|*Diagram činnosti (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy aktivit UML: Odkaz](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktivit UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Kroky, ke kterým dochází, když zákazník chce napsat recenzi restaurace|
|*Diagram třídy (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy tříd UML: Odkaz](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|Data potřebná k uložení recenze|

 Například následující diagram případu použití obsahuje nový případ použití "Revize zápisu" představující nový požadavek. Je zvýrazněnoryčně na diagramu pro snadnější identifikaci:

 ![Diagram případu použití UML](../modeling/media/uml-writerev.png "UML_WriteRev")

 **Diagram případu použití UML**

 Následující diagram činnosti obsahuje nové prvky oranžově popisující tok kroků v novém případě použití:

 ![Diagram činnosti UML](../modeling/media/uml-writereview.png "UML_WriteReview")

 **Diagram činnosti UML**

 Následující diagram třídobsahuje novou třídu Review a její vztahy s jinými třídami, aby týmy mohly diskutovat o podrobnostech. Všimněte si, že zákazník a restaurace mohou mít více recenzí:

 ![Diagram tříd UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **Diagram třídy UML**

### <a name="creating-tests-from-models"></a><a name="CreatingTests"></a>Vytváření testů z modelů
 Oba týmy se shodují, že před provedením změn potřebují kompletní sadu testů pro systém a jeho součásti. Lucerne má specializovaný tým, který provádí testování na úrovni systému a komponent. Znovu použít testy vytvořené večeři nyní a strukturujte tyto testy pomocí diagramů UML:

- Každý případ použití je reprezentován jedním nebo více testy. Prvky v diagramu případu použití odkaz na pracovní položky testovacího případu v Team Foundation Server.

- Každý tok na diagramu činnosti nebo sekvenční diagram na úrovni systému je propojen přinejmenším s jedním testem. Testovací tým systematicky zajišťuje, že testují všechny možné cesty diagramu činnosti.

- Termíny použité k popisu testů jsou založeny na termínech definovaných diagramy případu použití, třídy a aktivity.

  Jak se požadavky mění a diagramy jsou aktualizovány tak, aby odrážely tyto změny, testy jsou také aktualizovány. Požadavek se považuje za splněný pouze při průchodu zkoušek. Pokud je to možné nebo praktické, testy jsou definovány a založeny na diagramech UML před zahájením implementace.

  Přečtěte si:

- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)

- [Ověření modelu UML](../modeling/validate-your-uml-model.md)

### <a name="identifying-changes-to-the-existing-system"></a><a name="DeterminingChanges"></a>Identifikace změn stávajícího systému
 Večeře nyní musí odhadnout náklady na splnění nového požadavku. To částečně závisí na tom, jak moc tato změna ovlivní ostatní části systému. Chcete-li jim to pochopit, jeden z vývojářů večeři nyní vytvoří tyto mapy a diagramy z existujícího kódu:

|**Mapa nebo diagram**|**Ukazuje**|
|------------------------|---------------|
|*Mapa kódu*<br /><br /> Přečtěte si:<br /><br /> -   [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Závislosti a další vztahy v kódu.<br /><br /> Například večeři nyní může začít kontrolou mapy kódu sestavení pro přehled sestavení a jejich závislosti. Mohou přejít k podrobnostem do mapy prozkoumat obory názvů a třídy v těchto sestaveních.<br /><br /> Večeře nyní můžete také vytvořit mapy prozkoumat konkrétní oblasti a jiné druhy vztahů v kódu. Pomocí Průzkumníka řešení vyhledávají a vybírají oblasti a vztahy, které je zajímají.|
|*Diagram třídy založený na kódu*<br /><br /> Postup: [Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Existující třídy v kódu|

 Například vývojář vytvoří mapu kódu. Upraví svůj rozsah, aby se zaměřila na oblasti, které budou ovlivněny novým scénářem. Tyto oblasti jsou vybrány a zvýrazněny na mapě:

 ![Graf závislostí oboru názvů](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Mapa kódu oboru názvů**

 Vývojář rozbalí vybrané obory názvů, aby zotřil jejich třídy, metody a vztahy:

 ![Rozšířený graf závislostí oboru názvů](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Rozšířená mapa kódu oboru názvů s viditelnými odkazy mezi skupinami**

 Vývojář zkontroluje kód najít ovlivněné třídy a metody. Chcete-li zobrazit účinky každé změny při jejich vytvoření, regenerovat mapy kódu po každé změně. Viz [Vizualizace kódu](../modeling/visualize-code.md).

 Chcete-li popsat změny v jiných částech systému, jako jsou součásti nebo interakce, tým může čerpat tyto prvky na tabuli. Mohou také nakreslit následující diagramy v sadě Visual Studio tak, aby podrobnosti mohly být zachyceny, spravovány a pochopeny oběma týmy:

|**Diagramy**|**Popisuje**|
|------------------|-------------------|
|*Diagram činnosti (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy aktivit UML: Odkaz](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktivit UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Tok kroků, ke kterým dochází, když si systém všimne, že zákazník znovu zadá objednávku z restaurace, vyzve zákazníka k napsání recenze.|
|*Diagram třídy (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy tříd UML: Odkaz](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|Logické třídy a jejich vztahy. Například je přidána nová třída popisující **recenzi** a její vztahy s jinými entitami, jako je **restaurace**, **menu**a **zákazník**.<br /><br /> Chcete-li přidružit recenze k zákazníkovi, musí systém ukládat podrobnosti o zákazníkovi. Diagram třídy UML může pomoci objasnit tyto podrobnosti.|
|*Diagram třídy založený na kódu*<br /><br /> Postup: [Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Existující třídy v kódu.|
|*Diagram komponent (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy komponent UML: Odkaz](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)|Části systému na vysoké úrovni, například web Dinner Now, a jejich rozhraní. Tato rozhraní definují, jak komponenty vzájemně spolupracují prostřednictvím metod nebo služeb, které poskytují a spotřebovávají.|
|*Sekvenční diagram (UML)*<br /><br /> Přečtěte si:<br /><br /> -   [Sekvenční diagramy UML: Odkaz](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|Posloupnost interakcí mezi instancemi.|

 Například následující diagram komponent yírá novou komponentu, která je součástí komponenty Web Večeři. Komponenta ReviewProcessing zpracovává funkce vytváření recenzí a zobrazuje se zvýrazněná oranžově:

 ![Diagram komponent UML](../modeling/media/uml-internal.png "UML_Internal")

 **Diagram komponent UML**

 Následující sekvenční diagram znázorňuje posloupnost interakcí, ke kterým dochází při večeři nyní webu zkontroluje, zda zákazník objedná v restauraci dříve. Pokud je to pravda, pak požádá zákazníka o vytvoření recenze, která je odeslána do restaurace a publikována webem:

 ![Sekvenční diagram UML](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **Sekvenční diagram UML**

### <a name="keeping-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Zachování kódu v souladu s návrhem
 Večeři nyní musí ujistěte se, že aktualizovaný kód zůstane konzistentní s návrhem. Vytvářejí diagramy vrstev, které popisují vrstvy funkcí v systému, určují povolené závislosti mezi nimi a přidružují artefakty řešení k těmto vrstvám.

|**Diagram**|**Popisuje**|
|-----------------|-------------------|
|*Diagram vrstev*<br /><br /> Přečtěte si:<br /><br /> -   [Vytvoření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: Odkaz](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [Ověření kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|Logická architektura kódu.<br /><br /> Diagram vrstev uspořádá a mapuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] artefakty v řešení abstraktních skupin *nazývaných vrstvy*. Tyto vrstvy identifikují role, úkoly nebo funkce, které tyto artefakty provádějí v systému.<br /><br /> Diagramy vrstev jsou užitečné pro popis zamýšleného návrhu systému a ověření vyvíjejícího se kódu proti tomuto návrhu.<br /><br /> Chcete-li vytvořit vrstvy, přetáhněte položky z Průzkumníka řešení, map kódu, zobrazení tříd a prohlížeče objektů. Chcete-li nakreslit nové vrstvy, použijte panel nástrojů nebo klepněte pravým tlačítkem myši na povrch diagramu.<br /><br /> Chcete-li zobrazit existující závislosti, klepněte pravým tlačítkem myši na povrch diagramu **vrstvy**a potom klepněte na příkaz Generovat závislosti . Chcete-li určit zamýšlené závislosti, nakreslete nové závislosti.|

 Například následující diagram vrstvy popisuje závislosti mezi vrstvami a počet artefaktů, které jsou přidruženy ke každé vrstvě:

 ![Diagram vrstev integrovaného platebního systému](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagram vrstev**

 Chcete-li se ujistit, že konflikty s návrhem nedochází během vývoje kódu, týmy používá ověření vrstvy na sestavení, které jsou spuštěny na Team Foundation Sestavení. Také vytvořit vlastní úlohu MSBuild vyžadovat ověření vrstvy v jejich operací chod se změnami. Používají sestavy sestavení ke shromažďování chyb ověření.

 Přečtěte si:

- [Definování procesu sestavení](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Ověření změn pomocí procesu sestavení s gated vrácením se změnami](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Přizpůsobení šablony procesu sestavení](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="general-tips-for-creating-and-using-models"></a><a name="GeneralTips"></a>Obecné tipy pro vytváření a používání modelů

- Většina diagramů se skládá z uzlů, které jsou propojeny čarami. Pro každý typ diagramu panel nástrojů poskytuje různé druhy uzlů a řádků.

   Chcete-li otevřít panel nástrojů, klepněte v nabídce **Zobrazení** na **položku Panel nástrojů**.

- Chcete-li vytvořit uzel, přetáhněte jej z panelu nástrojů do diagramu. Některé druhy uzlů musí být přetaženy na existující uzly. Například v diagramu komponenty musí být do existující součásti přidán nový port.

- Chcete-li vytvořit čáru nebo připojení, klepněte na příslušný nástroj v panelu nástrojů, klepněte na zdrojový uzel a potom klepněte na cílový uzel. Některé řádky lze vytvořit pouze mezi určitými druhy uzlů. Když přesunete ukazatel nad možný zdroj nebo cíl, ukazatel označuje, zda můžete vytvořit připojení.

- Při vytváření položek v diagramech UML je také přidáváte do společného modelu. Diagramy UML v projektu modelování jsou pohledy tohoto modelu. Položky v diagramu vrstvy jsou součástí projektu modelování, i když nejsou uloženy ve společném modelu.

   Model zobrazíte tak, že v nabídce **Architektura** přejděte na **položku Windows**a klepněte na tlačítko **Průzkumník a průzkumník modelů UML**.

- V některých případech můžete přetáhnout určité položky z **Průzkumníka modelů UML** do diagramu UML. Některé prvky v rámci stejného modelu lze použít na více nebo různých diagramů k zobrazení alternativní zobrazení architektury. Můžete například přetáhnout komponentu do jiného diagramu komponenty nebo do sekvenčního diagramu a použít ji jako objekt actor.

- Visual Studio podporuje UML 2.1.2. Tento přehled popisuje pouze hlavní funkce diagramů UML v této verzi, ale existuje mnoho knih, které podrobně popisují UML a jeho použití.

  Viz [Vytváření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).

### <a name="planning-and-tracking-work"></a><a name="PlanningTracking"></a>Plánování a sledování práce
 Vizovací diagramy modelování jsou integrovány s Team Foundation Server, takže můžete plánovat, spravovat a sledovat práci snadněji. Oba týmy používají modely k identifikaci testovacích případů a vývojových úloh a k odhadu jejich práce. Lucerne vytvoří a propojí pracovní položky Team Foundation Server s prvky modelu, jako jsou případy použití nebo součásti. To jim pomáhá sledovat jejich průběh a sledovat jejich práci zpět k požadavkům uživatelů. To jim pomáhá zajistit, aby jejich změny i nadále splňovat tyto požadavky.

 Jak jejich práce postupuje, týmy aktualizovat své pracovní položky tak, aby odrážely čas, který strávili na jejich úkoly. Také monitorují a hlásí stav své práce pomocí následujících funkcí Team Foundation Server:

- Denní *sestavy úbytku práce,* které ukazují, zda dokončí plánovanou práci v očekávaném čase. Generují další podobné sestavy ze serveru Team Foundation Server ke sledování průběhu chyb.

- *Iterace list,* který používá aplikaci Microsoft Excel pomoci týmu sledovat a vyvažovat zatížení mezi jeho členy. Tento list je propojen se serverem Team Foundation A poskytuje fokus pro diskusi během jejich pravidelných schůzek o průběhu.

- Řídicí *panel vývoje,* který pomocí aplikace Office Project informuje tým o důležitých informacích o projektu.

  Přečtěte si:

- [Sledování práce pomocí služby Visual Studio Team Services nebo Team Foundation Server](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md)

- [Grafy, řídicí panely a sestavy pro Visual Studio ALM](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Vytváření nevyřízených položek a úkolů pomocí Projectu](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="testing-validating-and-checking-in-code"></a><a name="TestValidateCheckInCode"></a>Testování, ověřování a vrácení kódu se změnami
 Když týmy dokončí každý úkol, zkontrolují svůj kód do správy verzí Team Foundation a obdrží připomenutí ze serveru Team Foundation, pokud zapomenou. Předtím, než Team Foundation Server přijme jejich vrácení se změnami, týmy spustit testování částí a ověření vrstvy k ověření kódu proti jejich testovacích případů a návrhu. Používají Team Foundation Server ke spuštění sestavení, automatizované testování částí a ověřování vrstev pravidelně. To pomáhá zajistit, že kód splňuje následující kritéria:

- Funguje to.

- Nepřeruší dříve funkční kód.

- Není v rozporu s návrhem.

  Večeře nyní má velkou sbírku automatizovaných testů, které Lucerne můžete znovu použít, protože téměř všechny stále platí. Lucerne můžete také stavět na těchto testech a přidat nové, které pokrývají nové funkce. Oba také použít Visual Studio spustit ruční testy.

  Chcete-li se ujistit, že kód odpovídá návrhu, týmy nakonfigurují jejich sestavení v Team Foundation Sestavení zahrnout ověření vrstvy. Pokud dojde ke konfliktům, je generována sestava s podrobnostmi.

  Přečtěte si:

- [Testování aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)

- [Použití správy verzí](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Sestavení aplikace](/azure/devops/pipelines/index)

## <a name="updating-the-system-using-visualization-and-modeling"></a><a name="UpdatingSystem"></a>Aktualizace systému pomocí vizualizace a modelování
 Lucerne a Večeře Nyní musí integrovat své platební systémy. Následující části ukazují diagramy modelování v sadě Visual Studio, které jim pomáhají provádět tento úkol:

- [Pochopit požadavky uživatele: Diagramy případů použití](#UnderstandUseCases)

- [Principy obchodního procesu: diagramy aktivit](#UnderstandActivities)

- [Popište systémovou strukturu: diagramy součástí](#DescribeComponents)

- [Popište interakce: Sekvenční diagramy](#DescribeSequence)

- [Vizualizujte existující kód: Mapy kódu](#VisualizeCode)

- [Definování glosáře typů: Diagramy tříd](#DefineClasses)

- [Popište logickou architekturu: diagramy vrstev](#DescribeLayers)

  Přečtěte si:

- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)

- [Vizualizace kódu](../modeling/visualize-code.md)

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)

- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

### <a name="understand-the-user-requirements-use-case-diagrams"></a><a name="UnderstandUseCases"></a>Pochopit požadavky uživatele: Diagramy případů použití
 Diagramy případu použití shrnují aktivity, které systém podporuje a kdo tyto aktivity provádí. Lucerne používá diagram případu použití se dozvíte následující o večeři nyní systému:

- Zákazníci vytvářejí objednávky.

- Restaurace přijímají objednávky.

- Brána externího platebního procesoru, kterou platební systém Večeři nyní používá k ověření plateb, je pro web mimo rozsah.

  Diagram také ukazuje, jak některé z hlavních případů použití rozdělit do menších případů použití. Lucerne chce používat svůj vlastní platební systém. Zvýrazní případ použití zpracovat platbu v jiné barvě označující, že vyžaduje změny:

  ![Zvýraznění procesní platby v diagramu případu použití](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Zvýraznění procesní platby v diagramu případu použití**

  Pokud doba vývoje byla krátká, tým může diskutovat o tom, zda chtějí nechat zákazníky platit restaurace přímo. Chcete-li zobrazit, by nahradit případ použití procesu platby s jedním, který je mimo hranice systému večeři nyní. Oni by pak propojit zákazníka přímo do restaurace, což naznačuje, že večeře nyní by pouze zpracování objednávek:

  ![Rescoping Pay Restaurant na diagramu případu použití](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Rescoping Pay Restaurant na diagramu případu použití**

  Přečtěte si:

- [Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Kreslení diagramu případu použití
 Diagram případu použití má následující hlavní funkce:

- *Objekty actor* představují role, které hrají osoby, organizace, stroje nebo softwarové systémy. Například zákazník, restaurace a večeři nyní platební systém jsou objekty actor.

- *Případy použití* představují interakce mezi účastníky a systémem ve vývoji.  Mohou představovat libovolné měřítko interakce od jediného kliknutí myší nebo zprávy k transakci rozšířené po mnoho dní.

- *Přidružení* propojit objekty actor na případy použití.

- Větší případ použití může *obsahovat* menší, například Vytvořit objednávku zahrnuje vybrat restauraci. Můžete *rozšířit* případ použití, který přidá cíle a kroky k případu rozšířené použití, k označení, že případ použití dochází pouze za určitých podmínek. Případy použití mohou také dědit od sebe navzájem.

- *Subsystém* představuje softwarový systém, který je ve vývoji, nebo jednu z jeho součástí. Jedná se o velké pole, které obsahuje případy použití. Diagram případu použití objasňuje, co je uvnitř nebo vně hranice subsystému. Chcete-li označit, že uživatel musí dosáhnout určitých cílů jinými způsoby, nakreslete tyto případy použití mimo hranice subsystému.

- *Artefakty propojují prvky* v diagramu s jinými diagramy nebo dokumenty.

  Přečtěte si:

- [Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)

- [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Shrnutí: Silné diagramy případu použití
 Diagramy případu použití vám pomohou vizualizovat:

- Činnosti, které systém podporuje nebo nepodporuje

- Lidé a externí systémy, které tyto činnosti vykonávají

- Hlavní součásti systému, které podporují každou aktivitu, kterou můžete představovat jako subsystémy vnořené uvnitř nadřazeného systému

- Jak se případ použití může rozdělit na menší nebo varianty

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popisuje**|
|-----------------|-------------------|
|Diagram činnosti|Tok kroků v případě použití a ty, kteří provádějí tyto kroky v tomto případě použití.<br /><br /> Názvy případů použití často zrcadlí kroky v diagramu činnosti. Diagramy aktivit podporují prvky, jako jsou rozhodnutí, sloučení, vstupy a výstupy, souběžné toky a tak dále.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy aktivit UML: Odkaz](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktivit UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)|
|Sekvenční diagram|Posloupnost interakcí mezi účastníky v případě použití.<br /><br /> Přečtěte si:<br /><br /> -   [Sekvenční diagramy UML: Odkaz](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagram třídy (UML)|Entity nebo typy, které se účastní případu použití.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy tříd UML: Odkaz](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="understand-the-business-process-activity-diagrams"></a><a name="UnderstandActivities"></a>Principy obchodního procesu: diagramy aktivit
 Diagramy aktivit popisují tok kroků v obchodním procesu a poskytují jednoduchý způsob komunikace pracovního postupu. Vývojový projekt může mít více diagramů aktivit. Aktivita obvykle zahrnuje všechny akce, které jsou výsledkem jedné vnější akce, jako je například objednání jídla, aktualizace nabídky nebo přidání nové restaurace do firmy. Aktivita může také popisovat podrobnosti o složité akci.

 Lucerne aktualizuje následující diagram činnosti, aby bylo vidět, že Lucerne zpracovává platbu a platí restauraci. Nahrazují platební systém Dinner Now systémem plateb Lucerne, jak je zvýrazněno:

 ![Platební systém Lucernu v diagramu činnosti](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Nahrazení platebního systému večeři v diagramu činnosti**

 Aktualizovaný diagram pomáhá Lucerne a večeři nyní vizualizovat, kde lucerne platební systém zapadá do obchodního procesu. V této verzi komentáře slouží k identifikaci rolí, které provádějí kroky. Čáry se používají k vytvoření *plaveckých děvek*, které organizují kroky podle role.

 Týmy mohou také zvážit diskusi o alternativní příběh, kde zákazník platí restaurace místo po doručení objednávky. To by vytvořilo různé požadavky na softwarový systém.

 Dříve večeře nyní nakreslil tyto diagramy na tabuli nebo v powerpointové. Nyní také používají Visual Studio k nakreslení těchto diagramů tak, aby oba týmy mohly zachytit, pochopit a spravovat podrobnosti.

 Přečtěte si:

- [Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)

- [Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Kreslení diagramu činnosti
 Diagram činnosti má následující hlavní funkce:

- *Počáteční uzel,* který označuje první akci aktivity.

   Diagram by měl mít vždy jeden z těchto uzlů.

- *Akce,* které popisují kroky, kdy uživatel nebo software provádí úkol.

- *Řídicí toky,* které zobrazují tok mezi akcemi.

- *Rozhodovací uzly,* které představují podmíněné větve v toku.

- *Uzly rozkladu,* které rozdělují jednotlivé toky na souběžné toky.

- *Konečné uzly aktivity,* které zobrazují konce aktivity.

   Přestože tyto uzly jsou volitelné, je užitečné zahrnout je do diagramu ukázat, kde končí aktivita.

  Přečtěte si:

- [Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)

- [Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Shrnutí: Silné diagramy činnosti
 Diagramy aktivit pomáhají vizualizovat a popisovat tok řízení a informací mezi akcemi firmy, systému nebo programu. Jedná se o jednoduchý a užitečný způsob, jak popsat pracovní postup při komunikaci s ostatními uživateli.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-----------------|---------------------|
|Použití diagramu případu|Shrňte aktivity, které provádí každý objekt actor.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy případu použití UML: Odkaz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagram součásti|Vizualizujte systém jako kolekci opakovaně použitelných částí, které poskytují nebo spotřebovávají chování prostřednictvím dobře definované sady rozhraní.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy komponent UML: Odkaz](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="describe-the-system-structure-component-diagrams"></a><a name="DescribeComponents"></a>Popište systémovou strukturu: diagramy součástí
 Diagramy komponent popisují systém jako kolekci oddělitelných částí, které poskytují nebo spotřebovávají chování prostřednictvím dobře definované sady rozhraní. Díly mohou být v libovolném měřítku a mohou se připojit jakýmkoli způsobem.

 Chcete-li pomoci Lucerne a večeře nyní vizualizovat a diskutovat o součásti systému a jejich rozhraní, vytvářejí následující diagramy komponent:

 ![Externí komponenty v platebním systému](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Součásti platebního systému Večeři nyní**

 Tento diagram znázorňuje různé typy součástí a jejich *závislosti*. Například web Dinner Now a platební systém Lucerne vyžadují k ověření plateb bránu externího platebního procesoru. Šipky mezi součástmi představují závislosti, které označují, které součásti vyžadují funkce jiných součástí.

 Chcete-li použít platební systém Lucerne, je nutné aktualizovat web Dinner Now, aby bylo možné používat rozhraní PaymentApproval a PayableInsertion v systému plateb Vojtova.

 Následující diagram znázorňuje konkrétní konfiguraci součástí pro web Dinner Now. Tato konfigurace označuje, že každá instance webu se skládá ze čtyř *částí*:

- CustomerProcessing

- Zpracování objednávek

- ReviewProcessing

- Zpracování plateb

  Tyto části jsou instancemi zadaných typů součástí a jsou spojeny následovně:

  ![Součásti uvnitř webu Večeři](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Součásti uvnitř webu Večeři nyní**

  Web Večeři nyní deleguje své chování na tyto části, které zpracovávají funkce webu. Šipky mezi nadřazenou komponentou a jejími členskými součástmi zobrazují *delegování,* které označují, které části zpracovávají zprávy, které nadřazený obdrží nebo odešle prostřednictvím svých rozhraní.

  V této konfiguraci zpracovává komponenta PaymentProcessing platby odběratele. Proto musí být aktualizována tak, aby byla integrována s platebním systémem společnosti Lucerne. V jiných scénářích může existovat více instancí typu komponenty ve stejné nadřazené součásti.

  Přečtěte si:

- [Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)

- [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Kreslení diagramu komponent
 Diagram komponent má následující hlavní funkce:

- *Součásti,* které představují oddělitelné části funkčnosti systému.

- *Za předpokladu, porty rozhraní,* které představují skupiny zpráv nebo volání, které součásti implementovat a jsou používány jinými součástmi nebo externími systémy.

- *Požadované porty rozhraní,* které představují skupiny zpráv nebo volání, které součásti odesílají do jiných součástí nebo externích systémů. Tento druh portu popisuje operace, které komponenta alespoň očekává od jiných součástí nebo externích systémů.

- *Součásti* jsou členy součástí a jsou obvykle instancemi jiných součástí. Díl je část vnitřního návrhu nadřazené součásti.

- *Závislosti,* které označují součásti vyžadují funkce jiných součástí.

- *Delegování,* které označují části součásti zpracovávají zprávy odeslané nebo přijaté nadřazenou komponentou.

  Přečtěte si:

- [Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)

- [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Shrnutí: Silné diagramy komponent
 Diagramy komponent vám pomohou vizualizovat:

- Systém jako kolekce oddělitelných částí bez ohledu na jejich implementační jazyk nebo styl.

- Komponenty s dobře definovanými rozhraními, což usnadňuje pochopení a aktualizaci návrhu při změně požadavků.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-----------------|---------------------|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li identifikovat kandidáty pro součásti, vytvořte mapu kódu a seskupte položky podle jejich funkce v systému.<br /><br /> Přečtěte si:<br /><br /> -   [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)|
|Sekvenční diagram|Vizualizujte posloupnost interakcí mezi součástmi nebo součástmi uvnitř součásti.<br /><br /> Chcete-li vytvořit životnost v sekvenčním diagramu z komponenty, klepněte pravým tlačítkem myši na komponentu a potom klepněte na příkaz **Vytvořit životnost**.<br /><br /> Přečtěte si:<br /><br /> -   [Sekvenční diagramy UML: Odkaz](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|
|Diagram třídy (UML)|Definujte rozhraní na zadaných nebo požadovaných portech a třídách, které implementují funkce součástí.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy tříd UML: Odkaz](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram vrstev|Popište logickou architekturu systému ve vztahu k součástem. Pomocí ověření vrstvy se ujistěte, že kód zůstane konzistentní s návrhem.<br /><br /> Přečtěte si:<br /><br /> -   [Vytvoření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: Odkaz](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [Ověření kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|
|Diagram činnosti|Vizualizujte interní zpracování, které komponenty provádějí v reakci na příchozí zprávy.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy aktivit UML: Odkaz](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktivit UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Vizualizujte existující kód: Mapy kódu
 Mapy kódu zobrazují aktuální organizaci a vztahy v kódu. Položky jsou reprezentovány *uzly* na mapě a vztahy jsou reprezentovány *odkazy*. Mapy kódu vám mohou pomoci provádět následující typy úkolů:

- Prozkoumejte neznámý kód.

- Zjistěte, kde a jak může navrhovaná změna ovlivnit existující kód.

- Najděte oblasti složitosti, přirozené vrstvy nebo vzory nebo jiné oblasti, které by mohly mít prospěch ze zlepšení.

  Například večeři nyní musí odhadnout náklady na aktualizaci PaymentProcessing komponenty. To částečně závisí na tom, jak moc tato změna ovlivní ostatní části systému. Chcete-li jim pomoci pochopit, jeden z vývojáři večeři nyní generuje mapy kódu z kódu a upravuje zaměření oboru na oblasti, které mohou být ovlivněny změnou.

  Následující mapa zobrazuje závislosti mezi třídou PaymentProcessing a dalšími částmi systému Večeři, které se zobrazí jako vybrané:

  ![Graf závislostí pro platební systém Večeři nyní](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Mapa kódu pro platební systém Večeři nyní**

  Vývojář prozkoumá mapu rozšířením třídy PaymentProcessing a výběrem jeho členů zobrazíte oblasti, které jsou potenciálně ovlivněny:

  ![Metody uvnitř PaymentProcessing a závislosti](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **Metody uvnitř třídy PaymentProcessing a jejich závislosti**

  Vygenerují následující mapu pro platební systém Lucerne ke kontrole jeho třídy, metody a závislosti. Tým vidí, že systém Lucerne může také vyžadovat práci na interakci s ostatními částmi večeři nyní:

  ![Graf závislostí pro platební systém Lucerne](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Mapa kódu pro platební systém Lucerne**

  Oba týmy spolupracují na určení změn, které jsou nutné k integraci obou systémů. Rozhodnou se refaktorovat část kódu tak, aby bylo snazší jej aktualizovat. Třída PaymentApprover se přesune do oboru názvů DinnerNow.Business a bude vyžadovat některé nové metody. Večeře nyní třídy, které zpracovávají transakce bude mít svůj vlastní obor názvů. Týmy vytvářejí a používají pracovní položky k plánování, uspořádání a sledování své práce. Propojují pracovní položky s prvky modelu, kde je to užitečné.

  Po reorganizaci kódu týmy vygenerují novou mapu kódu, aby zotřitili aktualizovanou strukturu a vztahy:

  ![Graf závislostí s reorganizovaným kódem](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **Mapa kódu s reorganizovaným kódem**

  Tato mapa ukazuje, že Třída PaymentApprover je nyní v oboru názvů DinnerNow.Business a má některé nové metody. Třídy transakcí Večeři nyní mají svůj vlastní obor názvů PaymentSystem, což usnadňuje pozdější zpracování tohoto kódu.

#### <a name="creating-a-code-map"></a>Vytvoření mapy kódu

- Rychlý přehled zdrojového kódu naleznete takto, chcete-li vygenerovat mapování kódu:

     V nabídce **Architektura** klepněte na **položku Generovat mapu kódu pro řešení**.

     Chcete-li získat rychlý přehled o kompilovaném kódu, vytvořte prázdnou mapu kódu a potom přetáhněte soubory sestavení nebo binární soubory na povrch mapy.

- Chcete-li prozkoumat konkrétní kód nebo položky řešení, vyberte položky a vztahy, které chcete vizualizovat, pomocí Průzkumníka řešení. Poté můžete buď vygenerovat novou mapu, nebo přidat vybrané položky do existující mapy. Viz [Mapovat závislosti napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md).

- Chcete-li mapu prozkoumat, změňte uspořádání rozložení tak, aby vyhovovalo typům úkolů, které chcete provádět.

     Chcete-li například vizualizovat vrstvení v kódu, vyberte rozložení stromu. Viz [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Shrnutí: Silné stránky kódových map
 Kódové mapy vám pomohou:

- Další informace o organizaci a vztazích v existujícím kódu.

- Identifikujte oblasti, které by mohly být navrhovanou změnou ovlivněny.

- Najděte oblasti složitosti, vzorky, vrstvy nebo jiné oblasti, které byste mohli zlepšit, abyste usnadnili údržbu, změnu a opakované použití kódu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popisuje**|
|-----------------|-------------------|
|Diagram vrstev|Logická architektura systému. Pomocí ověření vrstvy se ujistěte, že kód zůstane konzistentní s návrhem.<br /><br /> Chcete-li identifikovat existující vrstvy nebo zamýšlené vrstvy, vytvořte mapu kódu a seskupte související položky. Chcete-li vytvořit diagram vrstvy, přečtěte si následující informace:<br /><br /> -   [Vytvoření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)|
|Diagram součásti|Komponenty, jejich rozhraní a jejich vztahy.<br /><br /> Chcete-li identifikovat součásti, vytvořte mapu kódu a seskupte položky podle jejich funkce v systému.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy komponent UML: Odkaz](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)|
|Diagram třídy (UML)|Třídy, jejich atributy a operace a jejich vztahy.<br /><br /> Chcete-li pomoci identifikovat tyto prvky, vytvořte diagram třídy UML, který zobrazuje tyto prvky.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy tříd UML: Odkaz](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram třídy (na základě kódu)|Existující třídy v kódu pro konkrétní projekt.<br /><br /> Chcete-li vizualizovat a upravovat existující třídu v kódu, použijte Návrhář tříd.<br /><br /> Postup: [Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="describe-the-interactions-sequence-diagrams"></a><a name="DescribeSequence"></a>Popište interakce: Sekvenční diagramy
 Sekvenční diagramy popisují řadu interakcí mezi částmi systému. Díly mohou být libovolného měřítka. Mohou se například pohybovat od jednotlivých objektů v programu až po velké subsystémy nebo externí aktéry. Interakce mohou být libovolného měřítka a typu. Mohou se například pohybovat od jednotlivých zpráv až po rozšířené transakce a mohou se jedná o volání funkcí nebo zprávy webové služby.

 Chcete-li pomoci Lucerne a večeři nyní popisují a diskutovat o krocích v případě použití procesu platby, vytvoří následující sekvenční diagram z diagramu komponenty. Životnosti zrcadlí komponentu Web Večeři a její části. Zprávy, které se zobrazí mezi životnosti postupujte podle připojení na diagramy komponent:

 ![Sekvenční diagram pro případ použití zpracovat platbu](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Sekvenční diagram pro případ použití procesní platby**

 Sekvenční diagram ukazuje, že když zákazník vytvoří objednávku, večeři nyní na webu volá ProcessOrder na instanci OrderProcessing. Dále OrderProcessing volání ProcessPayment na PaymentProcessing. To pokračuje, dokud externí platební procesor brány ověří platbu. Teprve potom se řízení vrátí na web Večeři.

 Lucerne musí odhadnout náklady na aktualizaci svého platebního systému integrovat se systémem Večeři nyní. Aby to pochopili, mohou také vytvořit mapy kódu pro vizualizaci ovlivněného kódu.

 Přečtěte si:

- [Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)

- [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Kreslení sekvenčního diagramu
 Sekvenční diagram má následující hlavní funkce:

- Vertikální *životnosti* představují objekty actor nebo instance softwarových objektů.

   Chcete-li přidat symbol objektu actor, který označuje, že účastník je mimo systém ve vývoji, klepněte na životnost. V okně **Vlastnosti** nastavte **objekt actor** na **hodnotu True**. Pokud okno **Vlastnosti** není otevřené, stiskněte **klávesu F4**.

- Vodorovné *zprávy* představují volání metod, zprávy webové služby nebo jinou komunikaci. *Spuštění výskyty* jsou svislé stínované obdélníky, které se zobrazí na životnosti a představují období, během kterých přijímající objekty proces volání.

- Během *synchronní* zprávy čeká objekt odesílatele na <\<návrat ovládacího prvku>> jako při běžném volání funkce. Během *asynchronní* zprávy může odesílatel pokračovat okamžitě.

- Pomocí \<<vytvořit>> zprávy k označení konstrukce objektů jinými objekty. Měla by to být první zpráva odeslaná objektu.

  Přečtěte si:

- [Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)

- [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Shrnutí: Silné sekvenční diagramy
 Sekvenční diagramy vám pomohou vizualizovat:

- Tok řízení, který přenáší mezi objekty actor nebo objekty během provádění případu použití.

- Implementace volání metody nebo zprávy.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-----------------|---------------------|
|Diagram třídy (UML)|Definujte třídy, které představují životnosti a parametry a vrácené hodnoty, které se používají ve zprávách odeslaných mezi životnosti.<br /><br /> Chcete-li vytvořit třídu z životnosti, klepněte pravým tlačítkem myši na životnost a potom klepněte na příkaz **Vytvořit třídu** nebo **Vytvořit rozhraní**. Chcete-li vytvořit životnost z typu v diagramu třídy, klepněte pravým tlačítkem myši na typ a potom klepněte na příkaz **Vytvořit životnost**.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy tříd UML: Odkaz](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)|
|Diagram součásti|Popište součásti, které představují životnosti a rozhraní, které poskytují a spotřebovávají chování reprezentované zprávy.<br /><br /> Chcete-li vytvořit životnost z diagramu komponenty, klepněte pravým tlačítkem myši na komponentu a potom klepněte na příkaz **Vytvořit životnost**.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy komponent UML: Odkaz](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)|
|Použití diagramu případu|Shrňte interakce mezi uživateli a součástmi v sekvenčním diagramu jako případ použití, který představuje cíl uživatele.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy případu použití UML: Odkaz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Definování glosáře typů: Diagramy tříd
 Diagramy tříd definují entity, termíny nebo koncepty, které se účastní systému a jejich vzájemné vztahy. Tyto diagramy můžete například použít během vývoje k popisu atributů a operací pro každou třídu, bez ohledu na jejich jazyk implementace nebo styl.

 Chcete-li pomoci Lucerne popsat a diskutovat o entity, které se účastní případu použití procesu platby, nakreslí následující diagram třídy:

 ![Zpracovat entity platby v diagramu třídy](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Zpracovat entity platby v diagramu třídy**

 Tento diagram ukazuje, že zákazník může mít mnoho objednávek a různé způsoby, jak platit za objednávky. BankAccount a CreditCard dědí z platby.

 Během vývoje lucerne používá následující diagram třídy k popisu a diskusi o podrobnostech každé třídy:

 ![Zpracovat podrobnosti entity platby v diagramu třídy](../modeling/media/uml-payment.png "UML_Payment")

 **Zpracovat podrobnosti platby v diagramu třídy**

 Přečtěte si:

- [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)

- [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>Kreslení diagramu třídy
 Diagram třídy má následující hlavní funkce:

- Typy, jako jsou třídy, rozhraní a výčty:

  - *Třída* je definice objektů, které sdílejí specifické strukturální nebo behaviorální charakteristiky.

  - *Rozhraní* definuje část externě viditelné chování objektu.

  - *Výčet* je třídění, které obsahuje seznam literálových hodnot.

- *Atributy* jsou hodnoty určitého typu, které popisují každou instanci *třídění*. Třídění je obecný název pro typy, součásti, případy použití a dokonce i objekty actor.

- *Operace* jsou metody nebo funkce, které mohou provádět instance třídění.

- *Přidružení* označuje nějaký druh vztahu mezi dvěma klasifikátory.

  - *Agregace* je přidružení, které označuje sdílené vlastnictví mezi klasifikátory.

  - *Složení* je přidružení, které označuje vztah celé části mezi třídění.

    Chcete-li zobrazit agregace nebo kompozice, nastavte vlastnost **Agregace** na přidružení. **Sdílené** zobrazuje agregace a **složené** zobrazuje kompozice.

- *Závislost* označuje, že změna definice jednoho třídění může změnit definici jiného třídění.

- *Generalizace* označuje, že konkrétní třídění dědí část jeho definice z obecnétřídění. *Realizace* označuje, že třída implementuje operace a atributy nabízené rozhraním.

   Chcete-li vytvořit tyto relace, použijte nástroj **dědičnost.** Alternativně může být realizace reprezentována jako *lízátko*.

- *Balíčky* jsou skupiny třídění, přidružení, životnosti, součásti a další balíčky. *Vztahy importu* označují, že jeden balíček obsahuje všechny definice jiného balíčku.

  Jako výchozí bod prozkoumat a diskutovat o existující třídy, můžete použít Class Designer k vytvoření diagramy tříd z kódu.

  Přečtěte si:

- [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)

- [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Shrnutí: Silné diagramy tříd
 Diagramy tříd vám pomohou definovat:

- Společný glosář termínů, které se mají používat při diskusi o potřebách uživatelů a entitách, které se účastní systému. Viz [Požadavky uživatelů modelu](../modeling/model-user-requirements.md).

- Typy, které jsou používány části systému, jako jsou součásti, bez ohledu na jejich implementaci. Viz [Model architektury aplikace](../modeling/model-your-app-s-architecture.md).

- Vztahy, například závislosti, mezi typy. Můžete například zobrazit, že jeden typ může být přidružen k více instancím jiného typu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-----------------|---------------------|
|Použití diagramu případu|Definujte typy, které se používají k popisu cílů a kroků v případech použití.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy případu použití UML: Odkaz](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|
|Diagram činnosti|Definujte typy dat, které procházejí uzly objektu, vstupními kolíky, výstupními kolíky a uzly parametrů aktivity.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy aktivit UML: Odkaz](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy aktivit UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)|
|Diagram součásti|Popište součásti, jejich rozhraní a jejich vztahy. Třída může také popisovat úplnou součást.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy komponent UML: Odkaz](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)|
|Diagram vrstev|Definujte logickou architekturu systému, pokud se vztahuje k třídám.<br /><br /> Pomocí ověření vrstvy se ujistěte, že kód zůstane konzistentní s návrhem.<br /><br /> Přečtěte si:<br /><br /> -   [Vytvoření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: Odkaz](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [Ověření kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|
|Sekvenční diagram|Definujte typy životnosti a operace, parametry a vrácené hodnoty pro všechny zprávy, které může přijímat životnost.<br /><br /> Chcete-li vytvořit životnost z typu v diagramu třídy, klepněte pravým tlačítkem myši na typ a potom klepněte na příkaz **Vytvořit životnost**.<br /><br /> Přečtěte si:<br /><br /> -   [Sekvenční diagramy UML: Odkaz](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li identifikovat třídy, jejich vztahy a jejich metody, vytvořte mapu kódu, která zobrazuje tyto prvky.<br /><br /> Přečtěte si:<br /><br /> -   [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-layer-diagrams"></a><a name="DescribeLayers"></a>Popište logickou architekturu: diagramy vrstev
 Diagramy vrstev popisují logickou architekturu systému uspořádáním artefaktů v řešení do abstraktních skupin nebo *vrstev*. Artefakty může být mnoho věcí, jako jsou například obory názvů, projekty, třídy, metody a tak dále. Vrstvy představují a popisují role nebo úkoly, které artefakty provádějí v systému. Můžete také zahrnout ověření vrstvy v sestavení a vrácení se změnami operace a ujistěte se, že kód zůstane konzistentní s jeho návrhu.

 Chcete-li zachovat kód v souladu s návrhem, večeři nyní a Lucerne použít následující diagram vrstvy k ověření jejich kódu, jak se vyvíjí:

 ![Diagram vrstev integrovaného platebního systému](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Diagram vrstev pro večeři nyní integrovaný s Lucerne**

 Vrstvy v tomto diagramu odkaz na odpovídající večeři nyní a Lucerne řešení artefakty. Například obchodní vrstva odkazy na DinnerNow.Business obor názvů a jeho členy, které nyní zahrnují PaymentApprover třídy. Vrstva Access prostředků odkazuje na obor názvů DinnerNow.Data. Šipky nebo *závislosti*určují, že funkci ve vrstvě Přístup u prostředků může používat pouze obchodní vrstva. Jak týmy aktualizují svůj kód, ověřování vrstev se provádí pravidelně zachytit konflikty, jak k nim dochází, a pomoci týmům je rychle vyřešit.

 Týmy spolupracují na postupné integraci a testování obou systémů. Nejprve se ujistěte, že PaymentApprover a zbytek večeři nyní úspěšně pracovat s sebou před tím, než se zabývají PaymentProcessing.

 Následující mapa kódu zobrazuje nová volání mezi večeří nyní a PaymentApprover:

 ![Aktualizovaný graf závislostí s integrovaným systémem](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Mapa kódu s aktualizovanými voláními metod**

 Poté, co potvrdí, že systém funguje podle očekávání, večeři nyní komentáře z PaymentProcessing kód. Sestavy ověření vrstvy jsou čisté a výsledné mapování kódu ukazuje, že neexistují žádné další závislosti PaymentProcessing:

 ![Graf závislostí bez zpracování platby](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **Mapa kódu bez zpracování platby**

#### <a name="drawing-a-layer-diagram"></a>Kreslení diagramu hladiny
 Diagram vrstev má následující hlavní rysy:

- *Vrstvy* popisují logické skupiny artefaktů.

- *Propojení* je přidružení mezi vrstvou a artefaktem.

   Chcete-li vytvořit vrstvy z artefaktů, přetáhněte položky z Průzkumníka řešení, map kódu, zobrazení tříd nebo prohlížeče objektů. Chcete-li nakreslit nové vrstvy a pak je propojit s artefakty, použijte panel nástrojů nebo klepněte pravým tlačítkem myši na povrch diagramu a vytvořte vrstvy a pak položky přetáhněte do těchto vrstev.

   Číslo ve vrstvě zobrazuje počet artefaktů, které jsou propojeny s vrstvou. Tyto artefakty mohou být obory názvů, projekty, třídy, metody a tak dále. Při interpretaci počtu artefaktů ve vrstvě si pamatujte následující:

  - Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.

     Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.

  - Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.

    Chcete-li zobrazit artefakty, které jsou propojeny s vrstvou, klepněte na ni pravým tlačítkem myši a klepnutím na **příkaz Zobrazit odkazy** otevřete **Průzkumníka vrstev**.

- *Závislost* označuje, že jedna vrstva může používat funkce v jiné vrstvě, ale ne naopak. *Obousměrná závislost* označuje, že jedna vrstva může používat funkce v jiné vrstvě a naopak.

   Chcete-li zobrazit existující závislosti v diagramu vrstvy, klepněte pravým tlačítkem myši na povrch diagramu a potom klepněte na příkaz **Generovat závislosti**. Chcete-li popsat zamýšlené závislosti, nakreslete nové.

  Přečtěte si:

- [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)

- [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)

- [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Shrnutí: Silné diagramy vrstev
 Diagramy vrstev vám pomohou:

- Popište logickou architekturu systému podle funkčnosti jeho artefaktů.

- Ujistěte se, že kód ve vývoji odpovídá zadanému návrhu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-----------------|---------------------|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li vytvořit vrstvy, vygenerujte mapu kódu a pak seskupte položky na mapě jako potenciální vrstvy. Přetáhněte skupiny z mapy do diagramu vrstev.<br /><br /> Přečtěte si:<br /><br /> -   [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)|
|Diagram součásti|Popište součásti, jejich rozhraní a jejich vztahy.<br /><br /> Chcete-li vizualizovat hladiny, vytvořte diagram komponent, který popisuje funkce různých součástí v systému.<br /><br /> Přečtěte si:<br /><br /> -   [Diagramy komponent UML: Odkaz](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|------------------|---------------|
|**Fóra**|-   [Nástroje pro vizualizaci & visual studia Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visualization Visualization & Modelování SDK (NÁSTROJE DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Viz také
 [Vizualizujte kód](../modeling/visualize-code.md) [Vytváření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md) [Použití modelů ve vývojovém procesu](../modeling/use-models-in-your-development-process.md) [Použití modelů v agilním vývoji](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) [Ověření systému během vývoje](../modeling/validate-your-system-during-development.md) Rozšíření modelů a [diagramů UML](../modeling/extend-uml-models-and-diagrams.md)
