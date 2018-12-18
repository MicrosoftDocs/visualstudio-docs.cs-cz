---
title: 'Scénář: Změna návrhu pomocí vizualizace a modelování | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4dface8e157e44aa09b271446dba68b2779d0a6b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745761"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scénář: Změna návrhu pomocí vizualizace a modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ujistěte se, že softwarový systém vyhovuje potřebám uživatelů pomocí vizualizace a modelování nástroje v sadě Visual Studio. Pomocí nástrojů, jako jsou diagramy jazyka UML (Unified Modeling), map kódu, diagramů vrstev a diagramů tříd do:  
  
 Které verze sady Visual Studio podporují jednotlivých nástrojích najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
- Vysvětlení požadavky uživatelů a obchodních procesů.  
  
- Vizualizujte a Zkoumejte existující kód.  
  
- Popište změny stávajícího systému.  
  
- Ověřte, že systém splňuje požadavky.  
  
- Udržujte kód v souladu s návrhem.  
  
  Tento názorný postup:  
  
- Popisuje, jak tyto nástroje vám může hodit softwarového projektu.  
  
- Ukazuje, jak můžete použít tyto nástroje, bez ohledu na to váš vývoj přístup pomocí ukázkového scénáře.  
  
  Další informace o těchto nástrojích a scénářích, které podporují, najdete v tématu:  
  
- [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)  
  
- [Vizualizace kódu](../modeling/visualize-code.md)  
  
- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)  
  
##  <a name="ScenarioOverview"></a> Přehled scénářů  
 Tento scénář popisuje epizody z životního cyklu vývoje softwaru dvou fiktivních společností: večeře nyní a Lucerne Publishing. Společnost dinner Now poskytuje služby pro doručování webového pokrmů v Seattlu. Zákazníci mohou objednat jídlo a zaplatit za ně na webu Dinner Now Web. Objednávky jsou potom odeslány příslušné místní restauraci pro dodání. Společnost Lucerne Publishing, společnost působící v New Yorku, provozuje několik podniků, vypnout a na webu. Například spuštění webové stránky kde můžou zákazníci posílat své recenze na restauraci.  
  
 Společnost Lucerne nedávno odkoupila web Dinner Now a chce provést následující změny:  
  
- Integrace webových stránek přidáním funkce recenzování restaurací na web Dinner Now.  
  
- Nahraďte společnosti Dinner Now platební systém společnosti Lucerne systému.  
  
- Rozbalte službu Dinner Now v oblasti.  
  
  Společnost dinner Now používá programování SCRUM a eXtreme. Mají velmi vysoké testovací pokrytí a velmi málo nepodporovaného kódu. Minimalizují riziko vytvářením malých, ale funkčních verzí systému a pak postupně přidávají funkce. Vyvíjejí svůj kód v krátkých a častých iteracích. Díky tomu mohou podpořit změnu s jistotou, často Refaktorovat kód a vyhnout se "velkému návrhu".  
  
  Společnost Lucerne udržuje výrazně větší a složitější kolekci systémů, z nichž některé jsou více než 40 let. Jsou velmi opatrní při provádění změn z důvodu složitosti a rozsahu staršího kódu. Následují přísnější vývojový proces, preferují návrh podrobných řešení a dokumentaci návrhu a změn, které nastanou během vývoje.  
  
  Oba týmy používají diagramy modelování v sadě Visual Studio k usnadnění vývoje systémů, které vyhovují potřebám uživatelů. Aby to pomohl ostatním plánovat, organizovat a spravovat svou práci používají Team Foundation Server spolu s dalšími nástroji.  
  
  Další informace o Team Foundation Server naleznete v tématu:  
  
- [Plánování a sledování práce](#PlanningTracking)  
  
- [Testování, ověřování a vrácení kódu se změnami](#TestValidateCheckInCode)  
  
##  <a name="ModelingDiagramsTools"></a> Role architektury a modelování diagramů při vývoji softwaru  
 Následující tabulka popisuje role, které tyto nástroje mohou hrát při více a v různých fázích životního cyklu vývoje softwaru:  
  
||**Modelování požadavků uživatelů**|**Modelování obchodních procesů**|**Architektura systému a Design**|**Vizualizace kódu & průzkum**|**Ověření**|  
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|  
|Použijte diagram případu (UML)|√|√|||√|  
|Diagram činnosti (UML)|√|√|√||√|  
|Diagram tříd (UML)|√|√|√||√|  
|Diagram součásti (UML)|√|√|√||√|  
|Sekvenční diagram (UML)|√|√|√||√|  
|Diagram jazyka specifického pro doménu (DSL)|√|√|√|||  
|Diagram vrstvy, ověřování vrstvy|||√|√|√|  
|Mapy kódu|||√|√|√|  
|Návrhář tříd (založený na kódu)||||√||  
  
 Chcete-li nakreslit diagramy UML a diagramy vrstvy, musíte vytvořit projekt modelování jako součást existujícího řešení nebo nové. Tyto diagramy musí být vytvořeny v projektu modelování. Položky v diagramech UML jsou součástí společného modelu a diagramů UML jsou zobrazením tohoto modelu. Položky v diagramech vrstev se nacházejí v projektu modelování, ale nejsou uloženy ve společném modelu. Mapy kódu a diagramy tříd .NET vytvořené z kódu existují mimo projekt modelování.  
  
 Další informace:  
  
- [Vytváření projektů a diagramů pomocí modelování UML](../modeling/create-uml-modeling-projects-and-diagrams.md)  
  
- [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)  
  
- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)  
  
  Chcete-li zobrazit alternativním zobrazení architektury, můžete použít některé prvky ze stejného modelu na několika nebo různých diagramech. Například můžete přetáhnout komponentu do jiného diagramu komponent nebo do sekvenčního diagramu tak, aby může fungovat jako prvek "actor". Zobrazit [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
  Oba týmy používají také vrstvu ověřování abyste měli jistotu, že kód ve vývoji zůstává konzistentní s návrhem.  
  
  Další informace:  
  
- [Udržování kódu v souladu s návrhem](#ValidatingCode)  
  
- [Popište logickou architekturu: diagramy vrstev](#DescribeLayers)  
  
- [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)  
  
  > [!NOTE]
  >  Některé verze sady Visual Studio podporují ověřování vrstev a verze jen pro čtení z mapy kódu a diagramy UML pro vizualizaci a modelování. Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="UnderstandingCommunicating"></a> Pochopení a sdělování informací o systému  
 Neexistuje žádné předepsané pořadí pro použití sady Visual Studio modelování diagramů, takže je můžete využít podle jejich potřeb s vašim potřebám a přístupu. Obvykle týmy opravují své modely opakovaně a často v průběhu projektu. Každý diagram nabízí určité výhody, které umožňují porozumět, popsat a sdělit různé aspekty vyvíjeného systému.  
  
 Společnost dinner Now a Lucerne komunikují vzájemně a se zúčastněnými stranami pro projekt s použitím diagramů jako jejich společný jazyk. Například web Dinner Now používá diagramy k provádění těchto úkolů:  
  
- Vizualizujte existující kód.  
  
- Komunikujte se společností Lucerne o nových nebo aktualizovaných uživatelských scénářů.  
  
- Identifikujte změny, které jsou vyžadovány pro podporu nových nebo aktualizovaných uživatelských scénářů.  
  
  Společnost Lucerne používá diagramy k provádění těchto úkolů:  
  
- Další informace o obchodním procesu webu Dinner Now.  
  
- Pochopte návrh systému.  
  
- Komunikace se společností Dinner Now o nových nebo aktualizovaných uživatelských požadavcích.  
  
- Aktualizace dokumentu v systému.  
  
  Diagramy jsou integrovány se serverem Team Foundation Server, takže týmy plánovat, řídit a sledovat svou práci snadněji. Například mohou používat modely k identifikaci testových případů a vývojářských úloh a k odhadu hotové práce. Společnost Lucerne propojí Team Foundation Server pracovní položky k prvkům modelu, takže můžete sledovat průběh a ujistěte se, že systém splňuje požadavky uživatelů. Například mohou propojit případy použití k pracovním položkám testovacího případu, aby bylo patrné, že jsou případy použití splněny, pokud všechny testy jsou úspěšné.  
  
  Než týmy vrátí změny, ověří kód proti testům a návrhu spuštěním sestavení, která obsahují vrstvu ověřování a automatizované testy. To pomáhá, ujistěte se, že aktualizovaný kód není v konfliktu s návrhem a nezruší dříve fungující funkce.  
  
  Další informace:  
  
- [Principy role systému v obchodním procesu](#UnderstandingBPMandSystemDesign)  
  
- [Popisuje nové nebo aktualizované uživatelské požadavky](#DescribingURM)  
  
- [Vytváření testů z modelů](#CreatingTests)  
  
- [Určení změn ve stávajícím systému](#DeterminingChanges)  
  
- [Udržování kódu v souladu s návrhem](#ValidatingCode)  
  
- [Obecné tipy pro vytváření a použití modelů](#GeneralTips)  
  
- [Plánování a sledování práce](#PlanningTracking)  
  
- [Testování, ověřování a vrácení kódu se změnami](#TestValidateCheckInCode)  
  
###  <a name="UnderstandingBPMandSystemDesign"></a> Principy Role systému v obchodním procesu  
 Společnost Lucerne se chce dozvědět více o obchodním procesu webu Dinner Now. Vytvářejí následující diagramy ke snadnější vyjasnění svého pochopení systému Dinner Now:  
  
|**Diagram**|**Popisuje**|  
|-----------------|-------------------|  
|*Použijte diagram případu (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|– Aktivity, které podporuje systém Dinner Now<br />-Osoby a externí systémy, které provádějí činnosti<br />-Hlavní součásti systému, které podporují jednotlivé aktivity<br />-Části obchodních procesů, které jsou mimo rozsah aktuálního systému, například dodávky potravin|  
|*Diagram činnosti (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy činnosti UML: referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Tok kroků, ke kterým dochází, když zákazník vytvoří objednávku|  
|*Diagram tříd (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|Obchodní entity a termíny, které se používají v diskusi a vztazích mezi těmito entitami. Například objednávka a položka nabídky jsou součástí slovníku v tomto scénáři.|  
  
 Společnost Lucerne například vytvoří následující diagram případu použití k porozumění úloh prováděných na webu Dinner Now Web a kdo je provede:  
  
 ![Diagram případu použití UML](../modeling/media/uml-usecase.png "UML_UseCase")  
  
 **Diagram případu použití UML**  
  
 Následující diagram činnosti popisuje průběh kroků když zákazník vytvoří objednávku na webu Dinner Now Web. V tomto vydání prvky komentářů identifikují role a řádky vytvářejí *plaveckých drah*, které organizují kroky podle rolí:  
  
 ![Diagram činností UML](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")  
  
 **Diagram činností UML**  
  
 Následující diagram tříd popisuje entity, které se účastní procesu objednávání:  
  
 ![Diagram tříd UML](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")  
  
 **Diagram tříd UML**  
  
###  <a name="DescribingURM"></a> Popisuje nové nebo aktualizované uživatelské požadavky  
 Společnost Lucerne chce přidat funkce do systému Dinner Now tak, aby mohli zákazníci číst a přidávat recenze restaurací. Aktualizují následující diagramy, takže mohou popsat a diskutovat o tomto novém požadavku s aplikací večeře nyní:  
  
|**Diagram**|**Popisuje**|  
|-----------------|-------------------|  
|*Použijte diagram případu (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|Nový případ použití pro "Napsat recenzi restaurace"|  
|*Diagram činnosti (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy činnosti UML: referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Kroky, které nastanou, pokud zákazník chce napsat recenzi restaurace|  
|*Diagram tříd (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|Data, která je požadována k uložení recenze|  
  
 Například následující diagram případu použití zahrnuje nový případ použití "Napsat recenzi" k reprezentaci nový požadavek. Je zvýrazněn oranžově v diagramu pro snazší identifikaci:  
  
 ![Diagram případu použití UML](../modeling/media/uml-writerev.png "UML_WriteRev")  
  
 **Diagram případu použití UML**  
  
 Následující diagram činnosti zahrnuje nové prvky zobrazené oranžově pro popis toku kroků postupu v novém případu použití:  
  
 ![Diagram činností UML](../modeling/media/uml-writereview.png "UML_WriteReview")  
  
 **Diagram činností UML**  
  
 Následující diagram tříd obsahuje novou třídu revize a její vztahy k jiným třídám, takže týmy mohou diskutovat o podrobnostech. Všimněte si, že zákazník a restaurace mohou mít více recenzí:  
  
 ![Diagram tříd UML](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")  
  
 **Diagram tříd UML**  
  
###  <a name="CreatingTests"></a> Vytváření testů z modelů  
 Oba týmy se dohodly, že potřebují úplnou sadu testů pro systému a jeho komponenty předtím, než provedou jakékoli změny. Společnost Lucerne má specializovaný tým, který provádí systému a testování na úrovni součásti. Jsou-li znovu použít testy vytvořené aplikací večeře nyní a strukturují tyto testy pomocí UML diagramů:  
  
- Každý případ použití je reprezentován jedním nebo více testy. Prvky na odkazu diagramu případu použití k testovacímu případu pracovní položky v Team Foundation Server.  
  
- Každý tok v diagramu činnosti nebo systémové úrovni sekvenčního diagramu je propojen s přinejmenším jeden test. Testovací tým systematicky zajišťuje testování všech možných cest pomocí diagramu činnosti.  
  
- Termíny používané k popisu testů jsou založeny na termínech definovaných diagramy případu, tříd a aktivit použití.  
  
  Při změně požadavků a diagramy se aktualizují tak, aby odrážela tyto změny, jsou aktualizovány také testy. Požadavek je považován za splněný pouze v případě, že testy jsou úspěšné. Pokud je to možné nebo praktické, testy jsou definovány a založeny na diagramech UML před zahájením implementace.  
  
  Další informace:  
  
- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)  
  
- [Ověření modelu UML](../modeling/validate-your-uml-model.md)  
  
###  <a name="DeterminingChanges"></a> Určení změn ve stávajícím systému  
 Společnost dinner Now musí odhadnout náklady na splnění nového požadavku. To zčásti závisí na tom, jak moc tato změna ovlivní ostatní části systému. Aby pomohl ostatním pochopit, jeden z vývojářů aplikace večeře nyní z existujícího kódu vytvoří tyto mapy a diagramy:  
  
|**Mapování nebo diagramu**|**Ukazuje**|  
|------------------------|---------------|  
|*Mapy kódu*<br /><br /> Další informace:<br /><br /> -   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)<br />-   [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Závislosti a jiné vztahy v kódu.<br /><br /> Například web Dinner Now může začít kontrolou map kódu sestavení přehledné informace o sestavení a jejich závislosti. Mohou se ponořit do mapy pro prozkoumání oborů názvů a třídy v těchto sestaveních.<br /><br /> Společnost dinner Now může také vytváření map prozkoumat určité oblasti a další druhy vztahů v kódu. Používají Průzkumníka řešení najít a vybrat oblasti a vztahy, které je zajímají.|  
|*Diagram třídy založený na kódu*<br /><br /> Zobrazit [postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Existující třídy v kódu|  
  
 Například vývojář vytvoří mapu kódu. Nastaví oblast pro zaměření na oblasti, které budou ovlivněny novým scénářem. Tyto oblasti jsou vybrané a zvýrazněné v mapě:  
  
 ![Graf závislosti Namespace](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")  
  
 **Mapy kódu Namespace**  
  
 Vývojář rozbalí vybrané obory názvů zobrazíte jejich třídy, metody a vztahy:  
  
 ![Graf závislosti expandovaného oboru názvů](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")  
  
 **Mapy kódu expandovaného oboru názvů s viditelné propojení mezi skupinami**  
  
 Vývojář kontroluje kód k nalezení příslušné tříd a metod. Abyste viděli efekt každé změny při provádění je, znovu vygenerovat mapy kódu po každé změně. Zobrazit [vizualizovat kód](../modeling/visualize-code.md).  
  
 K popisu změn jiných částí systému, jako je například součástí nebo interakcí, může tým kreslit tyto prvky na Tabule. Mohou také nakreslit následující diagramy v aplikaci Visual Studio tak, aby podrobnosti lze zachytit, spravovat a srozumitelné pro oba týmy:  
  
|**Diagramy**|**Popisuje**|  
|------------------|-------------------|  
|*Diagram činnosti (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy činnosti UML: referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|Tok kroků, ke kterým dochází, když systém zjistí, že zákazník zadá objednávku vytvoří v restauraci znovu, výzvou zákazníka, aby napsal recenzi.|  
|*Diagram tříd (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|Logické třídy a jejich vztahy. Například je přidána nová třída popisující **revize** a jeho vztahy s ostatními entitami, jako například **restaurace**, **nabídky**, a **zákazníka**.<br /><br /> Pokud chcete přidružit recenze k zákazníkovi, systém musí ukládat informace o zákazníkovi. Diagram tříd UML může pomoci objasnit tyto podrobnosti.|  
|*Diagram třídy založený na kódu*<br /><br /> Zobrazit [postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Existující třídy v kódu.|  
|*Diagram součásti (UML)*<br /><br /> Další informace:<br /><br /> -   [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|Základní částí systému, například webu Dinner Now a jejich rozhraní. Tato rozhraní definují, jak komponenty interagují navzájem pomocí metod nebo služeb, které poskytují a spotřebovávají.|  
|*Sekvenční diagram (UML)*<br /><br /> Další informace:<br /><br /> -   [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|Sekvence interakcí mezi instancemi.|  
  
 Například následující diagram komponent ukazuje novou komponentu, která je součástí součásti webu Dinner Now. Komponenta ReviewProcessing zpracovává funkce vytváření recenzí a je zvýrazněna oranžově:  
  
 ![Diagram komponenty UML](../modeling/media/uml-internal.png "UML_Internal")  
  
 **Diagram komponenty UML**  
  
 Následující sekvence diagramu znázorňují posloupnost interakcí, které vzniknou, když webu Dinner Now zkontroluje, jestli má zákazník seřazené od restaurace před. Pokud je to pravda, požádá zákazníka o vytvoření recenze, která je odeslána restauraci a zveřejněna na webu:  
  
 ![Sekvenční Diagram UML](../modeling/media/uml-revsystem.png "UML_RevSystem")  
  
 **Sekvenční diagram UML**  
  
###  <a name="ValidatingCode"></a> Udržování kódu v souladu s návrhem  
 Společnost dinner Now musí zajistit, že aktualizovaný kód zůstane konzistentní s návrhem. Vytvářejí diagramy vrstvy, které popisují vrstvy funkčnosti v systému, určují povolené závislosti mezi nimi a přidružují řešení artefakty k těmto vrstvám.  
  
|**Diagram**|**Popisuje**|  
|-----------------|-------------------|  
|*Diagram vrstvy*<br /><br /> Další informace:<br /><br /> -   [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|Logická architektura kódu.<br /><br /> Vrstva diagram organizuje a mapuje artefakty v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení účelem abstrahování skupin nazvaných *vrstvy*. Tyto vrstvy určují role, úlohy nebo funkce, které tyto artefakty provádějí v systému.<br /><br /> Diagramy vrstev jsou užitečné pro popis zamýšleného návrhu systému a ověřování vyvíjeného kódu ve srovnání s tímto návrhem.<br /><br /> Chcete-li vytvořit vrstvy, přetáhněte položky z Průzkumníku řešení, map kódu, zobrazení tříd a prohlížeče objektů. Chcete-li nakreslit nové vrstvy, použijte panel nástrojů nebo kliknutím pravým tlačítkem na plochu diagramu.<br /><br /> Chcete-li zobrazit existující závislosti, klikněte pravým tlačítkem na plochu diagramu a potom klikněte na tlačítko **generovat závislosti**. K určení zamýšlených závislostí, nakreslete nové závislosti.|  
  
 Například následující diagram vrstvy popisuje závislosti mezi vrstvami a počet artefaktů, které jsou spojené s každou vrstvou:  
  
 ![Diagram vrstev z integrované platební systém](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagram vrstvy**  
  
 Pokud chcete mít jistotu, že je v konfliktu s návrhem nedochází během vývoje kódu, týmy používají ověřování vrstev na sestaveních, které běží na Team Foundation Build. Jsou také vytvořit vlastní úkol MSBuild pro vyžadování ověření vrstvy v jejich operacích vrácení se změnami. Používají zprávy sestavení ke shromažďování chyb ověřování.  
  
 Další informace:  
  
-   [Definování procesu sestavení](http://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)  
  
-   [Použít proces sestavení hlídaného vrácení se změnami pro ověření změn](http://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)  
  
-   [Přizpůsobení šablony procesu sestavení](http://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)  
  
###  <a name="GeneralTips"></a> Obecné tipy pro vytváření a použití modelů  
  
- Většina diagramů se skládá z uzlů, které jsou spojeny čarami. Pro každý typ diagramu obsahuje panel nástrojů různé druhy uzlů a řádků.  
  
   Chcete otevřít v sadě nástrojů **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.  
  
- Chcete-li vytvořit uzel, přetáhněte ho z panelu nástrojů do diagramu. Některé typy uzlů musí být přetaženy do existujících uzlů. Například v diagramu komponent nový port musíte přidat do existující komponenty.  
  
- Chcete-li vytvořit čáru nebo připojení, klikněte na příslušný nástroj v soupravě nástrojů, klikněte na zdrojový uzel a potom klikněte na cílový uzel. Některé řádky lze vytvořit pouze mezi určitými typy uzlů. Když přesunete ukazatel přes možný zdroj nebo cíl, ukazatel myši informuje, zda můžete vytvořit připojení.  
  
- Při vytváření položky v diagramech UML také přidáte je do společného modelu. V projektu modelování diagramy UML jsou zobrazením tohoto modelu. Položky v diagramu vrstvy jsou součástí projektu modelování, i když nejsou uloženy ve společném modelu.  
  
   V modelu, **architektury** nabídky, přejděte na **Windows**a potom klikněte na tlačítko **Průzkumníku modelů UML**.  
  
- V některých případech můžete přetáhnout některé položky z **Průzkumníku modelů UML** do diagramu UML. Některé prvky v rámci stejného modelu lze použít na více nebo různé diagramy zobrazit alternativní zobrazení architektury. Například můžete přetáhnout komponentu do jiného diagramu komponent nebo do sekvenčního diagramu, který se použije jako prvek "actor".  
  
- Visual Studio podporuje UML 2.1.2. Tento přehled popisuje hlavní funkce diagramů UML v této verzi, ale existuje mnoho knih, které o UML a jeho použití podrobně.  
  
  Zobrazit [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md).  
  
###  <a name="PlanningTracking"></a> Plánování a sledování práce  
 Diagramy modelování Visual Studio jsou integrovány se serverem Team Foundation Server tak, že můžete plánovat, řídit a sledovat svou práci snadněji. Oba týmy používat modely k identifikaci testových případů a vývojářských úloh a k odhadu hotové práce. Společnost Lucerne vytvoří a propojí Team Foundation Server pracovní položky k prvkům modelu, jako jsou případy použití nebo komponenty. To pomáhá sledovat jejich průběh a trasovat jejich práci zpět podle požadavků uživatelů. Pomáhá se ujistit, že jejich změny nadále splňují tyto požadavky.  
  
 Jak jejich práce postupuje, týmy aktualizují své pracovní položky tak, aby odrážely čas strávený na úkolech. Také sledují a hlásí stav své práce pomocí následujících funkcí Team Foundation Server:  
  
- Denní *hlášení pracovního tempa* , které uvádí, zda dokončí plánovanou práci v očekávaném čase. Vytvářejí jiné podobné sestavy z Team Foundation serveru ke sledování průběhu chyby.  
  
- *Iterací* , který používá aplikace Microsoft Excel k pomoci sledovat a vyvážit zatížení mezi členy týmu. Tento list je propojen Team Foundation Server a poskytuje zaměření na diskuse během pravidelných schůzky o pokroku.  
  
- A *řídicí panel vývoje* , který používá Office Project k informování o důležitých informacích projektu týmu.  
  
  Další informace:  
  
- [Sledování práce pomocí Visual Studio Team Services nebo Team Foundation Server](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)  
  
- [Propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md)  
  
- [Grafy, řídicí panely a sestavy pro Visual Studio ALM](http://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)  
  
- [Vytvoření nevyřízených položek a úkolů pomocí aplikace Project](http://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)  
  
###  <a name="TestValidateCheckInCode"></a> Testování, ověřování a vrácení kódu se změnami  
 Jak týmy dokončují jednotlivé úkoly, vraťte jejich kód do správy verzí Team Foundation a přijměte připomenutí z Team Foundation Server, v případě, že zapomenete. Předtím, než Team Foundation Server přijme jejich vrácení se změnami, týmy spustí jednotkové testy a ověření vrstvy za účelem ověření kódu proti testovacím případům a návrhu. Používají Team Foundation Server pro sestavení, spouštět automatizované testy jednotky a pravidelné validaci vrstev. To pomáhá se ujistit, že kód splňuje následující kritéria:  
  
- To funguje.  
  
- Nedojde k poškození dříve funkčního kódu.  
  
- Nevznikne konflikt s návrhem.  
  
  Společnost dinner Now má velkou kolekci automatických testů, které společnost Lucerne můžete znovu použít, protože téměř všechny jsou stále platné. Společnost Lucerne může také stavět na těchto testech a přidat nové, aby pokryl nové funkce. Oba také využívají Visual Studio ke spuštění ručních testů.  
  
  Pokud chcete mít jistotu, že kód odpovídá návrhu, konfigurují týmy svá sestavení v Team Foundation Build zahrnout ověřování vrstvy. Pokud dojde k jakýmkoli konfliktům, generování sestavy s podrobnostmi.  
  
  Další informace:  
  
- [Testování aplikace](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)  
  
- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)  
  
- [Správa verzí](http://go.microsoft.com/fwlink/?LinkID=525605)  
  
- [Sestavení aplikace](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)  
  
##  <a name="UpdatingSystem"></a> Aktualizace systému pomocí vizualizace a modelování  
 Společnost Lucerne a Dinner Now musí integrovat své platební systémy. Následující oddíly zobrazují že diagramy modelování v sadě Visual Studio pomáhat při provedení této úlohy:  
  
- [Pochopte požadavky uživatelů: diagramy případů použití](#UnderstandUseCases)  
  
- [Pochopte obchodní proces: diagramy činnosti](#UnderstandActivities)  
  
- [Popište strukturu systému: diagramy komponent](#DescribeComponents)  
  
- [Popište interakce: sekvenční diagramy](#DescribeSequence)  
  
- [Vizualizujte existující kód: Kódových map](#VisualizeCode)  
  
- [Definice glosáře typů: diagramy třídy](#DefineClasses)  
  
- [Popište logickou architekturu: diagramy vrstev](#DescribeLayers)  
  
  Další informace:  
  
- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)  
  
- [Vizualizace kódu](../modeling/visualize-code.md)  
  
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)  
  
- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)  
  
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)  
  
###  <a name="UnderstandUseCases"></a> Pochopte požadavky uživatelů: diagramy případů použití  
 Použijte diagramy případu pro shrnutí činností, že systém podporuje, a kdo provádí tyto činnosti. Společnost Lucerne používá diagram případu použití ke zjištění následujících o systému Dinner Now:  
  
- Zákazníci vytváří objednávky.  
  
- Restaurace přijímají objednávky.  
  
- Externí brána procesu platby, který používá platební systém Dinner Now ke schválení plateb, je mimo rozsah pro webový server.  
  
  Diagram také ukazuje, jak některé z hlavních případů použití jsou rozděleny do menších případů použití. Společnost Lucerne chce používat vlastní platební systém. Zvýrazňují případ použití zpracování platby odlišnou barvou pro označení, že vyžaduje změny:  
  
  ![Zvýraznění platby proces v diagramu případu použití](../modeling/media/uml-processpay.png "UML_ProcessPay")  
  
  **Zvýraznění platby proces v diagramu případu použití**  
  
  Pokud byl vývoj krátký, tým může projednat, zda chtějí zákazníkům restaurace umožnit zaplatit přímo. Aby to předvedli, že by nahraďte případu použití zpracování platby ten, který je mimo hranice systému večeře nyní. Spojí zákazníka přímo s restaurací, která udává, že večeře nyní bude pouze zpracovávat objednávky:  
  
  ![Změna oboru mzdy restaurace na diagramu případu použití](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")  
  
  **Změna oboru mzdy restaurace na diagramu případu použití**  
  
  Další informace:  
  
- [Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)  
  
- [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="drawing-a-use-case-diagram"></a>Náčrt diagramu případu použití  
 Diagram případu použití má následující hlavní funkce:  
  
- *Objekty actor* představují role, které hrají osoby, organizace, počítače nebo softwarové systémy. Actors jsou například zákazník, restaurace a platební systém Dinner Now.  
  
- *Případy použití* představují interakce mezi objekty actor a systémem ve vývoji.  Mohou představovat jakékoli měřítko interakce jediným klepnutím myši nebo zprávy k transakci prodloužené na kolik dní.  
  
- *Přidružení* aktéry s případy použití.  
  
- Případ většího využití může *zahrnují* menší případy, například vytvoření objednávky zahrnuje výběr restaurace. Je možné *rozšířit* případ použití, který přidá cíle a kroky k rozšířenému případu použití, označuje, že k případu použití dochází pouze za určitých podmínek. Případy použití mohou také dědit od sebe navzájem.  
  
- A *subsystému* představuje softwarový systém, který je ve vývoji, nebo některá její součást. Jde o velké pole, které obsahuje případy použití. Diagram případu použití vysvětluje, co je uvnitř nebo vně hranice podsystému. K označení, že uživatel musí dosáhnout určitých cílů jinými způsoby, nakreslete použít ty případy mimo hranice podsystému.  
  
- *Artefakty* propojení prvků v diagramu s jinými diagramy nebo dokumenty.  
  
  Další informace:  
  
- [Diagramy případů použití UML: Referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)  
  
- [Diagramy případů použití UML: Pokyny](../modeling/uml-use-case-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-use-case-diagrams"></a>Shrnutí: Silné stránky diagramů případů použití  
 Použijte diagramy případu pro lepší vizualizaci:  
  
-   Aktivity, které systém podporuje nebo nepodporuje  
  
-   Osoby a externí systémy, které provádějí tyto činnosti  
  
-   Hlavní součásti systému, které podporují jednotlivé aktivity, které mohou představovat jako podsystémy vnořené uvnitř nadřazeného systému  
  
-   Jak může být případ použití rozdělit do menších případů nebo jejich variant  
  
#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
  
|**Diagram**|**Popisuje**|  
|-----------------|-------------------|  
|Diagram činnosti|Tok kroků případu použití a těch, kteří vykonávají tyto kroky v případu použití.<br /><br /> Názvy použití případů často zrcadlí kroky v diagramu činnosti. Diagramy činnosti podporují prvky, jako jsou rozhodnutí, sloučení, vstupy a výstupy, souběžné toků a tak dále.<br /><br /> Další informace:<br /><br /> -   [Diagramy činnosti UML: referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|  
|Sekvenční diagram|Sekvence interakcí mezi účastníky v případu použití.<br /><br /> Další informace:<br /><br /> -   [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagram tříd (UML)|Subjekty nebo typy, které se účastní případu použití.<br /><br /> Další informace:<br /><br /> -   [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|  
  
###  <a name="UnderstandActivities"></a> Pochopte obchodní proces: diagramy činnosti  
 Diagramy činnosti popisují tok kroků v procesu podnikání a poskytují jednoduchý způsob, jak komunikovat pracovní postup. Projekt vývoje může mít více diagramů činnosti. Činnost obvykle zahrnuje všechny akce, které vyplývají z jedné externí akce, jako je například pokrmu, aktualizace menu nebo přidání nové restaurace do podnikání. Aktivita může také popisovat podrobnosti složité akce.  
  
 Společnost Lucerne aktualizuje následující diagram činnosti aby, že společnost Lucerne zpracuje platbu a zaplatí restauraci. Nahraďte, systém platby Lucerne, jak je zdůrazněno platební systém Dinner Now:  
  
 ![Systém platby Lucerne v diagramu činnosti](../modeling/media/uml-lucerne.png "UML_Lucerne")  
  
 **Nahrazení platební systém Dinner Now v diagramu činnosti**  
  
 Aktualizovaný diagram pomůže aplikacím Lucerne a večeře nyní vizualizovat, kde systém platby Lucerne zapadá do obchodního procesu. V tomto vydání komentáře slouží k identifikaci rolí, ve kterých kroků. Řádky slouží k vytvoření *plaveckých drah*, které organizují kroky podle rolí.  
  
 Týmy mohou také zvážit diskuzi o alternativním článku, kde zákazník zaplatí restauraci místo toho po dodání objednávky. To by vedlo k různým požadavkům na software systému.  
  
 Dříve Dinner Now byly tyto diagramy kresleny na tabuli nebo v aplikaci PowerPoint. Nyní také využívají Visual Studio tak, aby oba týmy zachytit, pochopit a spravovat podrobnosti kreslí tyto diagramy.  
  
 Další informace:  
  
-   [Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)  
  
-   [Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="drawing-an-activity-diagram"></a>Náčrt diagramu aktivit  
 Diagram aktivity má následující hlavní funkce:  
  
- *Počáteční uzel* , který označuje první akci aktivity.  
  
   Diagram by měl vždy obsahovat jeden z těchto uzlů.  
  
- *Akce* , které popisují kroky, ve kterém uživatel nebo program provede úlohu.  
  
- *Řízení toků* , které znázorňuje tok mezi akcemi.  
  
- *Uzly pro rozhodnutí* představující podmíněné větvení v toku.  
  
- *Uzly rozvětvení* , které dělí jeden tok do souběžných toků.  
  
- *Konečné uzly aktivity* , které ukazují ukončení aktivity.  
  
   I když jsou tyto uzly volitelné, je vhodné je zahrnout v diagramu a zobrazit, kde končí činnost.  
  
  Další informace:  
  
- [Diagramy činnosti UML: Referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)  
  
- [Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-activity-diagrams"></a>Shrnutí: Silné stránky diagramů činností  
 Diagramy aktivit pomáhají vizualizovat a popisovat tok řízení a informací mezi akcemi firmy, systému nebo programu. Toto je jednoduchý a užitečný způsob popisu pracovního postupu při komunikaci s jinými uživateli.  
  
#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
  
|**Diagram**|**Popis**|  
|-----------------|---------------------|  
|Použití diagramu případu|Souhrn činností, které provádí každý objekt actor.<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagram součásti|Vizualizujte systém jako kolekci znovu použitelných částí, které poskytují nebo využívají chování prostřednictvím kvalitně definované sady rozhraní.<br /><br /> Další informace:<br /><br /> -   [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|  
  
###  <a name="DescribeComponents"></a> Popište strukturu systému: diagramy komponent  
 Diagramy součástí popisují systém jako kolekci oddělitelných částí, které poskytují nebo využívají chování prostřednictvím kvalitně definované sady rozhraní. Části mohou být v libovolném měřítku a lze připojit libovolným způsobem.  
  
 Aby pomohli aplikacím Lucerne a večeře nyní vizualizovat a projednat systémové součásti a jejich rozhraní, vytvářejí následující diagramy komponent:  
  
 ![Externí součásti systému platby](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")  
  
 **Součástí platební systém společnosti Dinner Now**  
  
 Tento diagram znázorňuje různé typy komponent a jejich *závislosti*. Například webu Dinner Now i platební systém Lucerne vyžadují ke schválení plateb brána externího zpracovatele platby. Šipky mezi komponentami představují závislosti, které označují součásti, které vyžadují funkci jiných komponent.  
  
 Pokud chcete použít systém platby Lucerne, musí být aktualizovány webu Dinner Now k použití rozhraní PaymentApproval a PayableInsertion v platebním systému Lucerne.  
  
 Následující diagram ukazuje určitou konfiguraci součástí pro webu Dinner Now. Tato konfigurace určuje, že všechny instance na webu se skládá ze čtyř *částí*:  
  
- CustomerProcessing  
  
- OrderProcessing  
  
- ReviewProcessing  
  
- PaymentProcessing  
  
  Tyto části jsou instancemi určitých typů součástí a jsou propojeny takto:  
  
  ![Součásti webu Dinner Now](../modeling/media/uml-dinnernow.png "UML_DinnerNow")  
  
  **Součásti ve společnosti Dinner Now webu**  
  
  Webu Dinner Now deleguje své chování na ty části, které zpracovávají funkce webového serveru. Šipky mezi nadřízenou součástí a jejími součástmi členů zobrazují *delegace* označující části, které zpracovávají zprávy, které nadřízený přijímá nebo odesílá prostřednictvím svých rozhraní.  
  
  V této konfiguraci komponenta PaymentProcessing zpracovává platby zákazníků. Proto musí být aktualizováno pro integraci s platebním systému společnosti Lucerne. V jiných scénářích může existovat více instancí typu komponenty ve stejné nadřazené komponentě.  
  
  Další informace:  
  
- [Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)  
  
- [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="drawing-a-component-diagram"></a>Náčrt diagramu součástí  
 Diagram komponenty má následující hlavní funkce:  
  
- *Součásti* představující oddělitelné části funkcí systému.  
  
- *Uvedené porty rozhraní* , které představující skupiny zpráv nebo volání, které implementují součásti a jsou použity jinými součástmi nebo externí systémy.  
  
- *Požadované porty rozhraní* , které představující skupiny zpráv nebo volání, které odesílají do jiných komponent nebo externích systémů. Tento druh portu popisuje operace, které komponenta alespoň očekává od jiných komponent nebo externích systémů.  
  
- *Části* jsou členy komponent a jsou obvykle instance jiných komponent. Součást je část interního návrhu nadřazené komponenty.  
  
- *Závislosti* označující součásti, které vyžadují funkce jiných komponent.  
  
- *Delegace* označující části komponent slouží ke zpracování zpráv odeslaný nebo přijatý nadřazené komponenty.  
  
  Další informace:  
  
- [Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)  
  
- [Diagramy komponent UML: Pokyny](../modeling/uml-component-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-component-diagrams"></a>Shrnutí: Silné stránky diagramů komponent  
 Diagramy součástí umožňují vizualizaci:  
  
-   Systém jako kolekci oddělitelných částí bez ohledu na jejich implementaci jazyka nebo stylu.  
  
-   Součásti s kvalitně definovanými rozhraními, které usnadní orientaci a aktualizaci při změně požadavků.  
  
#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
  
|**Diagram**|**Popis**|  
|-----------------|---------------------|  
|Mapy kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li identifikovat kandidáty na součásti, vytvořte kód mapy a seskupte položky podle jejich funkce v systému.<br /><br /> Další informace:<br /><br /> -   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)|  
|Sekvenční diagram|Vizualizujte řadu interakcí mezi komponentami nebo částmi uvnitř komponenty.<br /><br /> Pokud chcete vytvořit životnosti v sekvenčním diagramu z komponentu, klikněte pravým tlačítkem na komponentu a potom klikněte na **vytvořit životnost**.<br /><br /> Další informace:<br /><br /> -   [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Diagram tříd (UML)|Definujte rozhraní poskytnutých nebo požadovaných portů a tříd, které implementují funkce součástí.<br /><br /> Další informace:<br /><br /> -   [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagram vrstvy|Popište logickou architekturu systému, protože se týká komponent. Abyste měli jistotu, že kód zůstane konzistentní s návrhem použijte ověření vrstev.<br /><br /> Další informace:<br /><br /> -   [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|  
|Diagram činnosti|Vizualizujte vnitřní zpracování, které provedou komponenty jako odpověď na příchozí zprávy.<br /><br /> Další informace:<br /><br /> -   [Diagramy činnosti UML: referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|  
  
###  <a name="VisualizeCode"></a> Vizualizujte existující kód: Kódových map  
 Mapy kódu zobrazit aktuální organizaci a vztahy v kódu. Položky jsou představovány *uzly* na mapě, a vztahy jsou reprezentovány *odkazy*. Mapy kódu vám může pomoct provádět následující druhy úloh:  
  
- Prozkoumejte neznámý kód.  
  
- Zjistěte, jak a kde navrhované změny mohou ovlivnit existující kód.  
  
- Vyhledejte oblasti složitosti, přirozené vrstvy nebo vzorky a další oblasti, které by mohly mít prospěch z vylepšení.  
  
  Například web Dinner Now musí odhadnout náklady na aktualizaci komponenty PaymentProcessing. To zčásti závisí na tom, jak moc tato změna ovlivní ostatní části systému. Chcete-li pomohl ostatním pochopit, jeden z vývojářů aplikace večeře nyní generuje map kódu z kódu a upravuje rozsah zaměření na oblasti, které by mohly mít dopad změnu.  
  
  Následující mapa zobrazuje závislosti mezi třídou PaymentProcessing a jiných částí systému Dinner Now, které se zobrazí vybrané:  
  
  ![Graf závislosti pro platební systém společnosti Dinner Now](../modeling/media/dep-dnpayment.png "Dep_DNPayment")  
  
  **Mapu kódu pro platební systém společnosti Dinner Now**  
  
  Vývojář zkoumá mapy rozšiřující třídou PaymentProcessing a výběrem svých členů pro zobrazení oblastí, které jsou ovlivněny potenciálně ovlivněny:  
  
  ![Metody uvnitř PaymentProcessing a závislosti](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")  
  
  **Metody uvnitř třídy PaymentProcessing a jejich závislosti**  
  
  Generují následující mapování pro systém platby Lucerne, chcete-li prověřit své třídy, metody a závislosti. Tým vidí, že systém Lucerne může také vyžadovat práci kvůli interakci s ostatními částmi systému Dinner Now:  
  
  ![Graf závislosti pro platební systém Lucerne](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")  
  
  **Mapu kódu pro systém platby Lucerne**  
  
  Oba týmy společně pracují na určení změn, které jsou nutné k integraci obou systémů. Rozhodnou se Refaktorovat kód, takže bude snadněji aktualizovat. Třída PaymentApprover se přesune do oboru názvů DinnerNow.Business a bude vyžadovat některé nové metody. Třídy Dinner Now, které zpracují transakce bude mít vlastní obor názvů. Týmy vytvářejí a použití pracovních položek k plánování, uspořádání a sledování své práce. Spojují pracovní položky k prvkům modelu, kde je to užitečné.  
  
  Po reorganizaci kódů týmy generují mapu s novým kódem, chcete-li zobrazit aktualizované strukturu a vztahů:  
  
  ![Graf závislosti s přeorganizovaným kódem](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")  
  
  **Mapy kódu s přeorganizovaným kódem**  
  
  Mapa ukazuje, že třída PaymentApprover je nyní v oboru názvů DinnerNow.Business a má některé nové metody. Třídy transakcí Dinner Now nyní mají své vlastní obor názvů PaymentSystem, což usnadňuje později zacházet s tímto kódem.  
  
#### <a name="creating-a-code-map"></a>Vytvořením mapy kódu  
  
-   Získejte rychlý přehled zdrojového kódu použijte následující postup Generovat mapu kódu:  
  
     Na **architektura** nabídky, klikněte na tlačítko **Generovat mapu kódu pro řešení**.  
  
     A získejte rychlý přehled kompilovaného kódu vytvořte mapu kódu prázdné a pak přetáhněte soubory sestavení nebo binární soubory do mapy povrchu.  
  
-   Chcete-li prozkoumat určitý kód nebo řešení položky, vyberte položky a vztahy, které chcete zobrazit pomocí Průzkumníka řešení. Potom můžete buď vygenerovat mapu s novým nebo přidat vybrané položky do existující mapování. Zobrazit [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Můžete prozkoumat na mapě, změňte rozložení tak, aby vyhovovalo typům úkolů, které chcete provést.  
  
     Například pro vizualizaci rozvrstvení v kódu, vyberte rozložení stromové struktury. Zobrazit [Procházet a uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).  
  
#### <a name="summary-strengths-of-code-maps"></a>Shrnutí: Silné stránky map kódu  
 Mapy kódu vám pomůže:  
  
-   Další informace o organizaci a vztahy v existujícím kódu.  
  
-   Identifikujte oblasti, které mohou být postiženy navrhovanou změnou.  
  
-   Vyhledejte oblasti složitosti, vzorky, vrstvy nebo další oblasti, které lze zlepšit a usnadnit údržbu, změnit a opakovaně používat kód.  
  
#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
  
|**Diagram**|**Popisuje**|  
|-----------------|-------------------|  
|Diagram vrstvy|Logická architektura systému. Abyste měli jistotu, že kód zůstane konzistentní s návrhem použijte ověření vrstev.<br /><br /> Chcete-li usnadnit identifikaci existujících vrstev nebo zamýšlených vrstev, vytvořte si mapu kódu a seskupte související položky. Chcete-li vytvořit diagram vrstev, naleznete v tématu:<br /><br /> -   [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)|  
|Diagram součásti|Součásti, jejich rozhraní a jejich vztahy.<br /><br /> Chcete-li usnadnit identifikaci součástí, vytvořte kód mapy a seskupte položky podle jejich funkce v systému.<br /><br /> Další informace:<br /><br /> -   [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagram tříd (UML)|Třídy, jejich atributy a operace a jejich vztahy.<br /><br /> Chcete-li usnadnit identifikaci těchto prvků, vytvoření diagramu tříd UML, který obsahuje tyto prvky.<br /><br /> Další informace:<br /><br /> -   [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagram tříd (založený na kódu)|Existující třídy v kódu pro konkrétní projekt.<br /><br /> Chcete-li vizualizovat a upravit existující třídu v kódu, použijte nástroj Návrhář tříd.<br /><br /> Zobrazit [postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|  
  
###  <a name="DescribeSequence"></a> Popište interakce: sekvenční diagramy  
 Sekvenční diagramy popisují řadu interakcí mezi částmi systému. Části mohou být libovolného rozsahu. Například se můžete v rozsahu od jednotlivých objektů v programu velké podsystémy nebo externí aktéry. Interakce může být libovolného rozsahu a typu. Například může být v rozsahu od jednotlivých zpráv po rozšířené operace a může být volání funkce nebo zprávami webové služby.  
  
 Aby pomohli aplikacím Lucerne a Večeř nyní popsat a projednat kroky v případu použití zpracování platby, vytvářejí následující sekvenční diagram z diagramu komponent. Životnosti zrcadlení součásti webu Dinner Now a jejích částí. Zprávy, které se objeví mezi životnosti následujícího připojení v diagramech komponent:  
  
 ![Případ použití sekvenční diagram pro zpracování platby](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")  
  
 **Sekvenční diagram pro zpracování platby případu použití**  
  
 Sekvenční diagram ukazuje, že pokud zákazník vytvoří objednávku, webu Dinner Now zavolá ProcessOrder v instanci OrderProcessing. V dalším kroku OrderProcessing volá funkci processpayment komponenty PaymentProcessing. Tento postup se opakuje dokud brána externího zpracovatele platby platbu neověří. Teprve potom se ovládací prvek vrátí na webu Dinner Now.  
  
 Společnost Lucerne musí odhadnout náklady na aktualizaci platebního systému, můžete integrovat s systému Dinner Now. Aby pomohl ostatním pochopit, může také vytvářejí map kódu k vizualizaci ovlivněného kódu.  
  
 Další informace:  
  
-   [Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)  
  
-   [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)  
  
-   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)  
  
#### <a name="drawing-a-sequence-diagram"></a>Náčrt diagramu sekvence  
 Diagram sekvence má následující hlavní funkce:  
  
- Svislé *životnosti* představují aktéry nebo instance objektů softwaru.  
  
   Chcete-li přidat objekt actor symbol, který označuje účastníka, který je mimo systém ve vývoji, klikněte na tlačítko životnost. V **vlastnosti** okno, nastavte **objektu Actor** k **True**. Pokud **vlastnosti** není otevřené okno, stiskněte klávesu **F4**.  
  
- Vodorovné *zprávy* představují volání metod, zprávy webové služby nebo některou jinou komunikaci. *Výskyty spuštění* jsou svislé šedé obdélníky, které se zobrazí v rámci životnosti a představují období, během kterých příjmové objekty zpracovávají volání.  
  
- Během *synchronní* zpráva, čeká objekt-odesílatel ovládací prvek <\<vrátit >> jako normální volání funkce. Během *asynchronní* zprávy odesílatel může pokračovat okamžitě.  
  
- Použití <\<vytvořit >> zprávy pro označení konstrukce objektů jinými objekty. Měla by být první zpráva odeslaná do objektu.  
  
  Další informace:  
  
- [Sekvenční diagramy UML: Referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)  
  
- [Sekvenční diagramy UML: Pokyny](../modeling/uml-sequence-diagrams-guidelines.md)  
  
#### <a name="summary-strengths-of-sequence-diagrams"></a>Shrnutí: Silné stránky sekvenčních diagramů  
 Sekvenční diagramy umožňují vizualizaci:  
  
-   Tok řízení, který přenáší mezi objekty actor nebo objekty během zpracování případu použití.  
  
-   Implementace metody volání nebo zprávy.  
  
#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
  
|**Diagram**|**Popis**|  
|-----------------|---------------------|  
|Diagram tříd (UML)|Definice třídy, které představují životnost a parametry a návratové hodnoty, které se používají ve zprávách odesílaných životností.<br /><br /> Pro vytvoření třídy ze životnosti, klepněte pravým tlačítkem myši životnost a potom klikněte na tlačítko **vytvořit třídu** nebo **vytvořit rozhraní**. Vytvořte životnost z typu v diagramu tříd, klikněte pravým tlačítkem na typ a potom klikněte na tlačítko **vytvořit životnost**.<br /><br /> Další informace:<br /><br /> -   [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)<br />-   [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)|  
|Diagram součásti|Popište komponenty, které představují životnost a rozhraní, které poskytuje a využívá chování reprezentované zprávami.<br /><br /> Vytvořit životnosti z diagramu komponent, klikněte pravým tlačítkem na komponentu a potom klikněte na tlačítko **vytvořit životnost**.<br /><br /> Další informace:<br /><br /> -   [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|  
|Použití diagramu případu|Interakce mezi uživateli a komponenty v sekvenčním diagramu Shrňte jako případ použití, který představuje cíl uživatele.<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|  
  
###  <a name="DefineClasses"></a> Definice glosáře typů: diagramy třídy  
 Diagramy tříd definují entity, podmínky nebo koncepty, které jsou součástí systému a jejich vztahy mezi sebou. Tyto diagramy můžete použít například během vývoje pro popis atributů a operací pro každou třídu, bez ohledu na jejich implementaci jazyka nebo stylu.  
  
 Aby usnadnili aplikaci Lucerne popsat a diskutovat subjekty, které se účastní případu použití zpracování platby, nakreslí následující diagram tříd:  
  
 ![Entity platby procesu na diagram tříd](../modeling/media/uml-payentities.png "UML_PayEntities")  
  
 **Entity platby procesu na diagram třídy**  
  
 Tento diagram znázorňuje, že zákazník může mít mnoho objednávek a různé způsoby platby za objednávky. BankAccount a CreditCard dědí z Payment.  
  
 Během vývoje používá společnost Lucerne následující diagram tříd k popisu a diskuzi o podrobnostech každá třída:  
  
 ![Detaily platby procesu entity na diagram třídy](../modeling/media/uml-payment.png "UML_Payment")  
  
 **Detaily platby procesu na diagram třídy**  
  
 Další informace:  
  
-   [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)  
  
-   [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)  
  
#### <a name="drawing-a-class-diagram"></a>Náčrt diagramu třídy  
 Diagram třídy má následující hlavní funkce:  
  
- Typy, jako jsou třídy, rozhraní a výčty:  
  
  -   A *třídy* je definice objektů, které sdílejí určité strukturální nebo behaviorální charakteristiky.  
  
  -   *Rozhraní* definuje část externě viditelného chování objektu.  
  
  -   *Výčet* je klasifikátor, který obsahuje seznam hodnot literálů.  
  
- *Atributy* jsou hodnoty určitého typu, které popisují každý výskyt *třídění*. Klasifikátor je obecný název pro typy, komponenty, případy použití a dokonce aktéry.  
  
- *Operace* jsou metody nebo funkce, které instance klasifikátoru mohou provádět.  
  
- *Přidružení* označuje určitý druh vztahu mezi dvěma Klasifikátory.  
  
  - *Agregace* je přidružení, které označuje sdílené vlastnictví mezi Klasifikátory.  
  
  - A *složení* je přidružení, které označuje vztah část celek mezi Klasifikátory.  
  
    Chcete-li zobrazit souhrnných hodnot nebo složení, nastavte **agregace** vlastnost pro přidružení. **Sdílené** zobrazuje agregace a **složené** zobrazuje sestavení.  
  
- A *závislost* znamená, že změna definice jednoho třídění může změnit definice jiného třídění.  
  
- A *generalizace* označuje, že zvláštní třídění dědí část definice z obecného třídění. A *realizace* označuje, že třída implementuje operace a atributy, které nabízí rozhraní.  
  
   Chcete-li vytvořit tyto vztahy, použijte **dědičnosti** nástroj. Alternativně může být realizace reprezentována jako *lollipop*.  
  
- *Balíčky* jsou skupiny klasifikátorů, přidružení, životností, komponent a dalších balíčků. *Import* vztahy označují, že jeden balíček obsahuje všechny definice jiného balíčku.  
  
  Jako výchozí bod pro zkoumání a probírání existujících tříd můžete použít Návrháře tříd pro vytvoření diagramů tříd z kódu.  
  
  Další informace:  
  
- [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)  
  
- [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)  
  
- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)  
  
#### <a name="summary-strengths-of-class-diagrams"></a>Shrnutí: Silné stránky diagramů tříd  
 Diagramy tříd umožňují definovat:  
  
-   Společný glosář termínů pro použití při projednávání potřeb uživatelů a entit, které jsou součástí systému. Zobrazit [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
-   Typy, které jsou používány součástmi systému, například komponenty bez ohledu na jejich implementaci. Zobrazit [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).  
  
-   Vztahy, například závislosti mezi typy. Například můžete zobrazit, že jeden typ může být přiřazen k více instancím jiného typu.  
  
#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
  
|**Diagram**|**Popis**|  
|-----------------|---------------------|  
|Použití diagramu případu|Definování typů, které se používají k popisu cílů a kroky v případy použití.<br /><br /> Další informace:<br /><br /> -   [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)<br />-   [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)|  
|Diagram činnosti|Definujte typy dat, která prochází uzly objektu, vstupní spojky, výstupní spojky a uzly parametru činností.<br /><br /> Další informace:<br /><br /> -   [Diagramy činnosti UML: referenční dokumentace](../modeling/uml-activity-diagrams-reference.md)<br />-   [Diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)|  
|Diagram součásti|Popište komponenty, jejich rozhraní a jejich vztahy. Třída může také popisovat kompletní komponentu.<br /><br /> Další informace:<br /><br /> -   [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|  
|Diagram vrstvy|Definujte logickou architekturu systému souvislosti se třídami.<br /><br /> Abyste měli jistotu, že kód zůstane konzistentní s návrhem použijte ověření vrstev.<br /><br /> Další informace:<br /><br /> -   [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|  
|Sekvenční diagram|Definujte typy životnosti a operace, parametry a návratové hodnoty pro všechny zprávy, které můžou přijímat životnost.<br /><br /> Vytvořte životnost z typu v diagramu tříd, klikněte pravým tlačítkem na typ a potom klikněte na tlačítko **vytvořit životnost**.<br /><br /> Další informace:<br /><br /> -   [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)<br />-   [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)|  
|Mapy kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> K identifikaci tříd, jejich vztahy a jejich metod, vytvořte mapu kódu, který obsahuje tyto prvky.<br /><br /> Další informace:<br /><br /> -   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)|  
  
###  <a name="DescribeLayers"></a> Popište logickou architekturu: diagramy vrstev  
 Diagramy vrstev popisují logickou architekturu systému organizací artefaktů ve vašem řešení do abstraktních skupin nebo *vrstvy*. Artefakty mohou být mnoho věcí, například obory názvů, projekty, třídy, metody a tak dále. Vrstvy představují a popisují role a úlohy, které tyto artefakty provádějí v systému. Můžete také zahrnout ověřování vrstvy v sestavení a operace vrácení se změnami zajistit, že kód zůstane konzistentní s návrhem.  
  
 Chcete-li byl kód zachován konzistentní s návrhem, použijte web Dinner Now a Lucerne následující diagram vrstvy k ověřování svého kódu, jak se vyvíjí:  
  
 ![Diagram vrstev z integrované platební systém](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")  
  
 **Diagram vrstvy pro web Dinner Now integrovaný se systémem Lucerne**  
  
 Vrstvy v tomto diagramu odkaz na odpovídající artefaktů řešení Dinner Now a Lucerne. Například, propojení obchodní vrstvy do oboru názvů DinnerNow.Business a jeho členy, které teď obsahují obsahuje třídu PaymentApprover. Přístup k prostředkům vrstva obsahuje odkazy na obor názvů DinnerNow.Data. Šipky, nebo *závislosti*, určete, že pouze vrstva Business může použít funkci ve vrstvě přístupu k prostředkům. Jak týmy aktualizují svůj kód, vrstva ověřování je prováděna pravidelně, aby zachytila konflikty při jejich výskytu a pomohla týmům je rychle řešit.  
  
 Týmy pracují společně, postupně integrují a testují tyto dva systémy. Nejprve se ujistí, že PaymentApprover a zbytek systému Dinner Now spolupracují úspěšně předtím, než se vypořádají s PaymentProcessing.  
  
 Následující mapa kódu zobrazuje nová volání mezi Dinner Now a PaymentApprover:  
  
 ![Graf závislosti aktualizované pomocí integrovaného systému](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")  
  
 **Mapy kódu s voláním aktualizované metody**  
  
 Po potvrzení, že systém funguje podle očekávání, Dinner Now okomentuje kód PaymentProcessing. Zprávy ověření vrstvy jsou čisté a výsledný mapy kódu ukazuje, že neexistují žádné další závislosti PaymentProcessing:  
  
 ![Graf závislosti bez funkce PaymentProcessing](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")  
  
 **Mapy kódu bez funkce PaymentProcessing**  
  
#### <a name="drawing-a-layer-diagram"></a>Náčrt diagramu vrstvy  
 Diagram vrstvy má následující hlavní funkce:  
  
- *Vrstvy* popisují logické skupiny artefaktů.  
  
- A *odkaz* je přidružení mezi vrstvou a artefaktem.  
  
   Chcete-li vytvořit vrstvu z artefaktů, přetáhněte položky z Průzkumníku řešení, map kódu, zobrazení tříd nebo prohlížeči objektů. Chcete-li nakreslit nové vrstvy a propojit je s artefakty, použijte panel nástrojů nebo klikněte pravým tlačítkem na plochu diagramu pro vytvoření vrstvy a přetáhněte položky k těmto vrstvám.  
  
   Číslo ve vrstvě zobrazuje počet artefaktů, které jsou spojeny s vrstvou. Tyto artefakty mohou být obory názvů, projekty, třídy, metody a tak dále. Při interpretaci počtu artefaktů ve vrstvě mějte na paměti následující:  
  
  - Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.  
  
     Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.  
  
  - Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.  
  
    Chcete-li zobrazit artefakty, které jsou propojeny s vrstvou, pravým tlačítkem myši na vrstvu a pak klikněte na tlačítko **zobrazit odkazy** otevřete **Průzkumník vrstev**.  
  
- A *závislost* znamená, že jedna vrstva může použít funkci v jiné vrstvě, ale ne naopak. A *obousměrná závislost* znamená, že jedna vrstva může použít funkci v jiné vrstvě a naopak.  
  
   Chcete-li zobrazit existující závislosti v diagramu vrstev, klikněte pravým tlačítkem na plochu diagramu a potom klikněte na tlačítko **generovat závislosti**. K popisu zamýšlených závislostí, nakreslete nové.  
  
  Další informace:  
  
- [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)  
  
- [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)  
  
- [Diagramy vrstev: Pokyny](../modeling/layer-diagrams-guidelines.md)  
  
- [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)  
  
#### <a name="summary-strengths-of-layer-diagrams"></a>Shrnutí: Silné stránky diagramů vrstev  
 Diagramy vrstev vám pomohou:  
  
-   Popište logickou architekturu systému podle funkcí jeho artefaktů.  
  
-   Ujistěte se, že kód ve vývoji odpovídá zadanému návrhu.  
  
#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
  
|**Diagram**|**Popis**|  
|-----------------|---------------------|  
|Mapy kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li vytvořit vrstvy, Generovat mapu kódu a potom seskupte položky na mapě jako potenciální vrstvy. Přetáhněte skupiny z mapy do diagramu vrstev.<br /><br /> Další informace:<br /><br /> -   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)|  
|Diagram součásti|Popište komponenty, jejich rozhraní a jejich vztahy.<br /><br /> Vizualizace vrstev, vytvoření diagramu komponent, který popisuje funkce různých složek v systému.<br /><br /> Další informace:<br /><br /> -   [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)<br />-   [Diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md)|  
  
## <a name="external-resources"></a>Externí zdroje  
  
|**Kategorie**|**Odkazy**|  
|------------------|---------------|  
|**Fóra**|-   [Visual Studio Visualization & Modeling nástroje](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
  
## <a name="see-also"></a>Viz také  
 [Vizualizace kódu](../modeling/visualize-code.md)   
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)   
 [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)   
 [Použití modelů v Agilním vývoji](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)   
 [Ověřování systému během vývoje.](../modeling/validate-your-system-during-development.md)   
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)



