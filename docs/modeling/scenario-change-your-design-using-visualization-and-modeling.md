---
title: Změna návrhu pomocí vizualizace a modelování
description: Přečtěte si o nástrojích pro vizualizaci a modelování v Visual Studio a o tom, jak tyto nástroje používáte ke změně návrhu.
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05cdd769a59c4101fbc05a7e51893752e2532f42
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385822"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scénář: Změna návrhu pomocí vizualizace a modelování

Pomocí nástrojů pro vizualizaci a modelování v nástrojích pro vizualizaci v nástrojích pro vizualizaci a modelování v Visual Studio.
Pomocí nástrojů, jako jsou mapy kódu, diagramy závislostí a diagramy tříd, můžete:

Informace o tom, které verze Visual Studio podporují jednotlivé nástroje, najdete v tématu [Podpora verzí pro nástroje architektury a modelování.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

- Vyjasnění požadavků a obchodních procesů uživatelů

- Vizualizujte a prozkoumejte existující kód.

- Popsat změny existujícího systému

- Ověřte, že systém splňuje jeho požadavky.

- Udržujte kód konzistentní s návrhem.

Tento názorný postup:

- Popisuje, jak tyto nástroje těží z vašeho softwarového projektu.

- Ukazuje, jak můžete tyto nástroje použít, bez ohledu na přístup k vývoji, s příkladem scénáře.

Další informace o těchto nástrojích a scénářích, které podporují, najdete tady:

- [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)

- [Vizualizace kódu](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Přehled scénáře

Tento scénář popisuje scénáře ze životních cyklů vývoje softwaru dvou fiktivních společností: Dinner Now a Vee Publishing. Dinner Now poskytuje službu doručování jídla na webu v Seattlu. Zákazníci si mohou objednat jídla a platit za ně na webu Dinner Now. Objednávky se pak posílají do příslušné místní restaurace k doručení. Firma v New Yorku, která se nachází v New Yorku, provozuje několik firem mimo web i na webu. Například spustí web, kde zákazníci mohou z recenzí restaurace psát.

Nedávno jste si koupili "Dinner Now" a chce provést následující změny:

- Integrujte své weby přidáním možností pro recenze restaurace do nabídky Dinner Now (Nyní u oběda).

- Nahraďte platební systém Dinner Now systémem Odyse.

- Rozbalte službu Dinner Now v celé oblasti.

Dinner Now uses SCRUM and e Programming. Mají velmi vysoké pokrytí testu a velmi malý nepodporovaný kód. Minimalizují rizika tím, že vytváří malé, ale funkční verze systému a následně postupně přidávají funkce. Svůj kód vyvíjejí v krátkých a častých iteracích. To jim umožňuje přijmout změny s jistotou, často refaktorovat kód a vyhnout se velkému návrhu předem.

Udržuje mnohem větší a složitou kolekci systémů, z nichž některé jsou starší než 40 let. Jsou velmi opatrní při provádění změn kvůli složitosti a rozsahu starší verze kódu. Postupují podle přísnějšího procesu vývoje, preferují navrhování podrobných řešení a dokumentují návrh a změny, ke kterým během vývoje dochází.

Oba týmy používají diagramy modelování v Visual Studio, aby jim pomohly vyvíjet systémy, které splňují potřeby uživatelů. Společně s Team Foundation Server nástroje používají nástroje, které jim pomáhají plánovat, organizovat a spravovat jejich práci.

Další informace o těchto Team Foundation Server v tématu:

- [Plánování a sledování práce](#plan-and-track-work)

- [Testování, ověřování a kontrola aktualizovaného kódu](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a> Role diagramů architektury a modelování ve vývoji softwaru

Následující tabulka popisuje role, které mohou tyto nástroje hrát během několika různých fází životního cyklu vývoje softwaru:

|Nástroj nebo role|Modelování požadavků na uživatele|Modelování obchodních procesů|Návrh architektury & systému|Code Visualization & Exploration|Ověření|
|------|-|-|-|-|-|
|Diagram Domain-Specific jazyka (DSL)|Yes|Yes|Yes|||
|Diagram závislostí, ověřování vrstev|||Yes|Yes|Yes|
|Mapa kódu|||Yes|Yes|Yes|
|Návrhář tříd (založené na kódu)||||Yes||

Pokud chcete nakreslit diagramy závislostí, musíte vytvořit projekt modelování jako součást existujícího řešení nebo nového. Tyto diagramy musí být vytvořeny v projektu modelování.
Položky v diagramech závislostí se nacházejí v projektu modelování, ale nejsou uloženy v běžném modelu. Mapy kódu a diagramy tříd .NET vytvořené z kódu existují mimo projekt modelování.

Přečtěte si:

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Oba týmy také používají ověřování závislostí, aby se ujistili, že vývojový kód zůstává konzistentní s návrhem. Přečtěte si:

- [Zajištění konzistentního kódu s návrhem](#ValidatingCode)

- [Popis logické architektury: Diagramy závislostí](#DescribeLayers)

- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Některé verze Visual Studio podporují ověřování závislostí a mapy kódu jen pro čtení pro vizualizaci a modelování. Informace o tom, které edice Visual Studio tuto funkci podporují, najdete v tématu Podpora edicí [pro nástroje architektury a modelování.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="understand-and-communicate-information-about-the-system"></a>Pochopení a komunikace informací o systému

Neexistuje žádné předepsané pořadí použití diagramů Visual Studio, takže je můžete použít tak, aby vyhovovaly vašim potřebám nebo přístupu. Týmy obvykle navštěvují své modely iterativně a často v rámci projektu. Každý diagram nabízí konkrétní silné stránky, které vám pomůžou pochopit, popsat a sdělit různé aspekty vývojového systému.

Dinner Now a Přichytili spolu navzájem a se zúčastněnými stranami projektu pomocí diagramů jako jejich společného jazyka. Například Nyní se k provádění těchto úloh používají diagramy:

- Vizualizujte existující kód.

- Komunikujte se Službou o nových nebo aktualizovaných uživatelských příbězích.

- Identifikujte změny, které jsou nutné pro podporu nových nebo aktualizovaných uživatelských příběhů.

K provádění těchto úloh používá Diagramy:

- Přečtěte si o obchodním procesu "Dinner Now".

- Porozuměli jste návrhu systému.

- Komunikujte se službou Dinner Now o nových nebo aktualizovaných požadavcích uživatelů.

- Zdokumentovat aktualizace systému.

Diagramy jsou integrované s Team Foundation Server aby týmy mohli snadněji plánovat, spravovat a sledovat svou práci. Pomocí modelů například identifikují testovací případy a vývojové úlohy a odhadují svou práci. Tyto Team Foundation Server pracovní položky k prvkům modelu, aby mohli sledovat průběh a zajistit, aby systém splňoval požadavky uživatelů. Například propojují případy použití s pracovními položkami testovacího případu, aby viděli, že případy použití jsou splněné, když všechny testy projdou.

Než týmy kontrolují své změny, ověří kód proti testům a návrhu spuštěním sestavení, která zahrnují ověřování závislostí a automatizované testy. To pomáhá zajistit, aby aktualizovaný kód nebyl v konfliktu s návrhem a porušovat dříve funkční funkce.

### <a name="identify-changes-to-the-existing-system"></a>Identifikace změn existujícího systému

Teď se musí odhadnout náklady na splnění nového požadavku. Částečně to závisí na tom, do jaké míry tato změna ovlivní jiné části systému. Aby jim to pomohlo pochopit, jeden z vývojářů v aplikaci Dinner Now vytvoří z existujícího kódu tyto mapy a diagramy:

|**Mapa nebo diagram**|**Ukazuje**|
|-|-|
|*Mapa kódu*<br /><br /> Přečtěte si:<br /><br /> - [Mapování závislostí napříč řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)<br />- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Závislosti a další relace v kódu.<br /><br /> Například nyní můžete začít tím, že si prohlédněte mapy kódu sestavení, ve kterých najdete přehled sestavení a jejich závislostí. Mohou přejít k podrobnostem map a prozkoumat obory názvů a třídy v těchto sestaveních.<br /><br /> Nyní můžete vytvořit mapy pro prozkoumání konkrétních oblastí a dalších druhů relací v kódu. Pomocí Průzkumník řešení najdou a vyberou oblasti a relace, které je zajímají.|
|*Diagram tříd založených na kódu*<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd).](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|Existující třídy v kódu|

 Vývojář například vytvoří mapu kódu. Upraví svůj rozsah tak, aby se zaměřil na oblasti, které bude nový scénář ovlivněn. Tyto oblasti jsou vybrány a zvýrazněny na mapě:

 ![Graf závislostí oboru názvů](../modeling/media/namespace_reviewsystem.png)

 **Mapa kódu oboru názvů**

 Vývojář rozbalí vybrané obory názvů a zobrazí své třídy, metody a relace:

 ![Graf závislostí rozšířeného oboru názvů](../modeling/media/dep_reviewsystem.png)

 **Rozbalená mapa kódu oboru názvů s viditelnými odkazy napříč skupinami**

 Vývojář prozkoumá kód a najde ovlivněné třídy a metody. Pokud chcete vidět účinky každé změny při jejich provedení, po každé změně znovu vygenerujte mapy kódu. Viz [Vizualizovat kód](../modeling/visualize-code.md).

 Aby mohl tým popsat změny v jiných částech systému, jako jsou komponenty nebo interakce, může tyto prvky nakreslit na tabuli. Mohou také vykreslit následující diagramy v Visual Studio, aby mohly být podrobnosti zachyceny, spravovány a srozumitelné oběma týmy:

|**Diagramy**|**Popisuje**|
|-|-|
|*Diagram tříd založených na kódu*<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd).](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|Existující třídy v kódu.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a> Zajištění konzistentního kódu s návrhem
 Teď se musíme ujistit, že aktualizovaný kód zůstává konzistentní s návrhem. Vytvářejí diagramy závislostí, které popisují vrstvy funkčnosti v systému, určují povolené závislosti mezi nimi a přidružují k oběma vrstvám artefakty řešení.

|**Diagram**|**Popisuje**|
|-|-|
|*Diagram závislostí*<br /><br /> Přečtěte si:<br /><br /> - [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: Referenční informace](../modeling/layer-diagrams-reference.md)<br />- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)<br />- [Ověření kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|Logická architektura kódu.<br /><br /> Diagram závislostí organizuje a mapuje artefakty v Visual Studio řešení na abstraktní skupiny nazývané *vrstvy*. Tyto vrstvy identifikují role, úlohy nebo funkce, které tyto artefakty provádějí v systému.<br /><br /> Diagramy závislostí jsou užitečné pro popis zamýšleného návrhu systému a ověřování vyvíjející se kódu proti tomuto návrhu.<br /><br /> Pokud chcete vytvořit vrstvy, přetáhněte položky z Průzkumník řešení, map kódu, Zobrazení tříd a Prohlížeče objektů. Pokud chcete nakreslit nové vrstvy, použijte panel nástrojů nebo klikněte pravým tlačítkem na plochu diagramu.<br /><br /> Pokud chcete zobrazit existující závislosti, klikněte pravým tlačítkem na plochu diagramu závislostí a pak klikněte na **Vygenerovat závislosti.** Chcete-li určit zamýšlené závislosti, nakreslete nové závislosti.|

Následující diagram závislostí například popisuje závislosti mezi vrstvami a počet artefaktů, které jsou přidruženy k jednotlivým vrstvám:

![Diagram závislostí integrovaného platebního systému](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram závislostí**

Aby se při vývoji kódu nejednaly o konflikty s návrhem, používají týmy ověřování závislostí u sestavení, která se spouštěly na Azure DevOps. Vytvoří také vlastní úlohu MSBuild, která bude vyžadovat ověření závislostí ve svých operacích určená k přihlášení. Ke shromažďování chyb ověřování používají sestavy sestavení.

Přečtěte si:

- [Použití vizuálního návrháře](/azure/devops/pipelines/get-started-designer)

- [Kontrola se škrtem TFVC](/azure/devops/pipelines/build/triggers)

- [Úlohy sestavení a vydání](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Obecné tipy pro vytváření a používání modelů

- Většina diagramů se skládá z uzlů, které jsou propojeny čárami. Pro každý typ diagramu sada nástrojů poskytuje různé druhy uzlů a čar.

   Pokud chcete otevřít panel nástrojů, klikněte v **nabídce Zobrazení** na **Panel nástrojů.**

- Pokud chcete vytvořit uzel, přetáhněte ho ze sady nástrojů do diagramu. Některé druhy uzlů musí být přetaženy do existujících uzlů. Například v diagramu součástí musí být nový port přidán do existující komponenty.

- Pokud chcete vytvořit řádek nebo připojení, klikněte na příslušný nástroj na panelu nástrojů, klikněte na zdrojový uzel a pak klikněte na cílový uzel. Některé řádky lze vytvořit pouze mezi určitými druhy uzlů. Když přesunete ukazatel nad možný zdroj nebo cíl, ukazatel určuje, zda lze vytvořit připojení.

### <a name="plan-and-track-work"></a>Plánování a sledování práce

Visual Studio diagramy modelování jsou integrované s Team Foundation Server, abyste mohli snadněji plánovat, spravovat a sledovat práci. Oba týmy používají modely k identifikaci testovacích případů a vývojových úloh a k odhadu své práce. Při vytváření pracovních položek Team Foundation Server jejich propojení s prvky modelu, jako jsou případy použití nebo komponenty. To jim pomůže sledovat jejich průběh a sledovat jejich práci zpět na požadavky uživatelů. To jim pomůže zajistit, aby jejich změny i nadále splňovaly tyto požadavky.

V průběhu práce týmy aktualizují své pracovní položky tak, aby odrážely čas strávený na svých úkolech. Monitorují a hlásí stav své práce také pomocí následujících Team Foundation Server funkcí:

- Denní *sestavy burn down,* které ukazují, jestli dokončí plánovanou práci v očekávaném čase. Generují další podobné sestavy z Team Foundation Server, aby sledovali průběh chyb.

- *Iterační list,* který pomocí Microsoft Excelu pomáhá týmu monitorovat a vyvažovat zatížení mezi jeho členy. Tento list je propojený s Team Foundation Server a zaměřuje se na diskuzi během pravidelných schůzek s průběhem.

- Vývojový *řídicí panel,* který používá Office Project k informování týmu o důležitých projektových informacích.

Přečtěte si:

- [Informace o agilní nástrojích a agilní správě projektů](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

- [Grafy, řídicí panely a widgety (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts&preserve-view=true)

- [Vytvoření backlogu a úloh pomocí projectu](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a> Testování, ověření a kontrola kódu

Když týmy dokončí každý úkol, zaškrtají svůj kód do správy zdrojového kódu a dostanou připomenutí od Team Foundation Server, pokud na to zapomenou. Předtím Team Foundation Server tým přijme svá přihlášení, spustí testy jednotek a ověření závislostí, aby ověřily kód proti svým testovacím případům a návrhu. Používají Team Foundation Server ke spouštění sestavení, automatizovaných testů jednotek a pravidelného ověřování závislostí. To pomáhá zajistit, aby kód splňoval následující kritéria:

- Funguje to.

- Nenaruší dříve fungující kód.

- Není v konfliktu s návrhem.

Dinner Now has a large collection of automated tests, which Collection can reuse because almost all still apply. Můžete také na těchto testech stavět a přidat nové testy, které budou pokrývat nové funkce. Obě používají také Visual Studio ke spouštění manuálních testů.

Aby se ujistili, že kód odpovídá návrhu, týmy nakonfigurují svá sestavení v Azure DevOps tak, aby zahrnovala ověření závislostí. Pokud dojde ke konfliktům, vygeneruje se sestava s podrobnostmi.

Přečtěte si:

- [Testování aplikace](/azure/devops/test/overview?view=vsts&preserve-view=true)

- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)

- [Použití řízení verzí](/azure/devops/repos/tfvc/overview?view=azure-devops&preserve-view=true)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualizace systému pomocí vizualizace a modelování

Nyní musí integrovat své platební systémy. Následující části znázorňují diagramy modelování v Visual Studio, které jim pomůžou tuto úlohu provést:

- [Vizualizace existujícího kódu: Mapy kódu](#VisualizeCode)

- [Definování glosáře typů: Diagramy tříd](#DefineClasses)

- [Popis logické architektury: Diagramy závislostí](#DescribeLayers)

Přečtěte si:

- [Vizualizace kódu](../modeling/visualize-code.md)

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a> Vizualizace existujícího kódu: Mapy kódu

Mapy kódu zobrazují aktuální organizaci a vztahy v kódu. Položky jsou *reprezentovány uzly* na mapě a relace jsou *reprezentovány* odkazy . Mapy kódu vám můžou pomoct provádět následující druhy úloh:

- Prozkoumejte neznámý kód.

- Pochopte, kde a jak může navrhovaná změna ovlivnit stávající kód.

- Vyhledejte oblasti složitosti, přirozené závislosti, vzory nebo jiné oblasti, pro které může být zlepšení přínosné.

Například Teď se musí odhadnout náklady na aktualizaci komponenty PaymentProcessing. Částečně to závisí na tom, do jaké míry tato změna ovlivní jiné části systému. Aby jim to pomohlo pochopit, jeden z vývojářů v aplikaci Dinner Now generuje mapy kódu z kódu a upravuje rozsah zaměření na oblasti, které mohou být touto změnou ovlivněny.

Následující mapa ukazuje závislosti mezi třídou PaymentProcessing a dalšími částmi systému Dinner Now, které se zobrazí jako vybrané:

![Graf závislostí pro platební systém Dinner Now](../modeling/media/dep_dnpayment.png)

**Mapa kódu platebního systému Dinner Now**

Vývojář prozkoumá mapu rozbalením třídy PaymentProcessing a výběrem jejích členů zobrazí oblasti, které by mohly být ovlivněny:

![Metody uvnitř PaymentProcessing a závislostí](../modeling/media/depgraph_expandeddn.png)

**Metody uvnitř třídy PaymentProcessing a jejich závislosti**

Vygenerují následující mapu, na které si platební systém Může prohlédnout jeho třídy, metody a závislosti. Tým vidí, že systém Sémie může také vyžadovat práci pro interakci s ostatními částmi dinner now:

![Graf závislostí pro platební systém Uže](../modeling/media/depgraph_lucernepay.png)

**Mapa kódu pro platební systém Namée**

Oba týmy spolupracují na určování změn, které jsou potřeba k integraci těchto dvou systémů. Rozhodnou se refaktorovat část kódu, aby bylo snazší ho aktualizovat. Třída PaymentApprover se přesune do oboru názvů DinnerNow.Business a bude vyžadovat některé nové metody. Třídy Dinner Now, které zachytává transakce, budou mít vlastní obor názvů. Týmy vytvářejí a používají pracovní položky k plánování, uspořádání a sledování práce. Pracovní položky propojují s prvky modelu, kde jsou užitečné.

Po změně uspořádání kódu týmy vygenerují novou mapu kódu, která zobrazí aktualizovanou strukturu a relace:

![Graf závislostí s reorganizovaným kódem](../modeling/media/depgraph_integrated.png)

**Mapa kódu s reorganizovaným kódem**

Tato mapa ukazuje, že třída PaymentApprover je teď v oboru názvů DinnerNow.Business a má několik nových metod. Třídy transakcí Dinner Now teď mají svůj vlastní obor názvů PaymentSystem, což usnadňuje pozdější řešení tohoto kódu.

#### <a name="creating-a-code-map"></a>Vytvoření mapy kódu

- Rychlý přehled zdrojového kódu najdete v těchto krocích a vygenerování mapy kódu:

     V nabídce **Architecture (Architektura)** klikněte na **Generate Code Map for Solution (Vygenerovat mapu kódu pro řešení).**

     Pro rychlý přehled zkompilovaný kód vytvořte prázdnou mapu kódu a potom přetáhněte soubory sestavení nebo binární soubory na plochu mapy.

- Pokud chcete prozkoumat konkrétní kód nebo položky řešení, Průzkumník řešení vyberte položky a relace, které chcete vizualizovat. Pak můžete vygenerovat novou mapu nebo přidat vybrané položky do existující mapy. Viz [Mapování závislostí napříč vašimi řešeními.](../modeling/map-dependencies-across-your-solutions.md)

- Mapu můžete prozkoumat tak, že změníte uspořádání rozložení tak, aby vyhovovalo druhům úloh, které chcete provádět.

     Pokud chcete například vizualizovat vrstvení v kódu, vyberte rozložení stromu. Viz [Procházení a změna uspořádání map kódu.](../modeling/browse-and-rearrange-code-maps.md)

#### <a name="summary-strengths-of-code-maps"></a>Shrnutí: Silné stránky map kódu
 Mapy kódu vám pomůžou:

- Přečtěte si o organizaci a relacích v existujícím kódu.

- Identifikujte oblasti, které mohou být ovlivněny navrhovanou změnou.

- Najděte oblasti složitosti, vzorů, vrstev nebo jiných oblastí, které byste mohli vylepšit, aby se usnadnila údržba, změna a opakované použití kódu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popisuje**|
|-|-|
|Diagram závislostí|Logická architektura systému. Pomocí ověřování závislostí zajistěte, aby kód zůstal konzistentní s návrhem.<br /><br /> Abyste mohli snadno identifikovat existující závislosti nebo zamýšlené závislosti, vytvořte mapu kódu a seskupte související položky. Diagram závislostí vytvoříte v tématu:<br /><br /> - [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)|
|Diagram tříd (založený na kódu)|Existující třídy v kódu pro konkrétní projekt.<br /><br /> K vizualizaci a úpravě existující třídy v kódu použijte Návrhář tříd.<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd).](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a> Definování glosáře typů: Diagramy tříd
 Diagramy tříd definují entity, termíny nebo koncepty, které se účastní systému, a jejich vztahy mezi sebou. Tyto diagramy můžete například použít během vývoje k popisu atributů a operací pro každou třídu bez ohledu na jejich jazyk nebo styl implementace.

 Aby pomohli s popisem a diskuzí o entitách, které se účastní případu použití procesní platby, nakreslí následující diagram tříd:

 ![Zpracování entit platby v diagramu tříd](../modeling/media/uml_payentities.png)

 **Zpracování entit platby v diagramu tříd**

 Tento diagram znázorňuje, že zákazník může mít mnoho objednávek a různé způsoby, jak za objednávky platit. BankAccount i CreditCard dědí z platby.

 Během vývoje Používá následující diagram tříd k popisu a diskusi o podrobnostech jednotlivých tříd:

 ![Zpracování podrobností o entitě platby v diagramu tříd](../modeling/media/uml_payment.png)

 **Zpracování podrobností o platbách v diagramu tříd**

#### <a name="drawing-a-class-diagram"></a>Kreslení diagramu tříd

Diagram tříd má následující hlavní funkce:

- Typy, jako jsou třídy, rozhraní a výčty:

  - Třída *je* definice objektů, které sdílejí specifické strukturální nebo behaviorální charakteristiky.

  - Rozhraní  definuje část externě viditelného chování objektu.

  - Výčet *je* klasifikátor, který obsahuje seznam hodnot literálů.

- *Atributy* jsou hodnoty určitého typu, které popisují jednotlivé instance *klasifikátoru*. Klasifikátor je obecný název pro typy, komponenty, případy použití a dokonce aktéry.

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

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Shrnutí: silné stránky diagramů tříd
 Diagramy tříd vám pomůžou definovat:

- Společný Glosář termínů, který se má použít při projednávání potřeb uživatelů a entit, které jsou součástí systému. Viz [Model požadavky uživatelů na uživatele](../modeling/model-user-requirements.md).

- Typy, které jsou používány částmi systému, jako jsou komponenty, bez ohledu na jejich implementaci. Podívejte [se na téma modelování architektury vaší aplikace](../modeling/model-your-app-s-architecture.md).

- Relace, například závislosti, mezi typy. Můžete například zobrazit, že jeden typ může být přidružen k více instancím jiného typu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-|-|
|Diagram závislosti|Definujte logickou architekturu systému v souvislosti se třídami.<br /><br /> Použijte ověřování závislostí a ujistěte se, že kód zůstává v souladu s návrhem.<br /><br /> Přečtěte si:<br /><br /> - [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />- [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)<br />- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li identifikovat třídy, jejich vztahy a jejich metody, vytvořte mapu kódu, která tyto prvky zobrazí.<br /><br /> Přečtěte si:<br /><br /> - [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a> Popište logickou architekturu: diagramy závislosti
 Diagramy závislostí popisují logickou architekturu systému uspořádáním artefaktů ve vašem řešení do abstraktních skupin nebo *vrstev*. Artefakty mohou být mnoho věcí, například obory názvů, projekty, třídy, metody a tak dále. Vrstvy reprezentují a popisují role nebo úkoly, které artefakty provádějí v systému. Můžete také zahrnout ověřování vrstvy do sestavení a operace vrácení se změnami, abyste se ujistili, že kód zůstává v souladu s jeho návrhem.

 Chcete-li zachovat kód v souladu s návrhem, večeře Now a Lucerne použijte následující diagram závislostí k ověření kódu při jeho vývoje:

 ![Diagram závislosti integrovaného platebního systému](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram závislostí pro večeři je teď integrovaný s vojtěškou.**

 Vrstvy na tomto diagramu odkazují na odpovídající artefakty řešení večeře Now a Lucerne. Například obchodní vrstva odkazuje na obor názvů DinnerNow. Business a její členy, které nyní obsahují třídu PaymentApprover. Vrstva přístupu k prostředkům odkazuje na obor názvů DinnerNow. data. Šipky nebo *závislosti* určují, že funkce ve vrstvě přístupu k prostředkům může používat jenom obchodní vrstva. Jak týmy aktualizují svůj kód, provádí se pravidelné ověřování vrstev za účelem zachycení konfliktů při jejich výskytu a k usnadnění jejich řešení.

 Týmy spolupracují na přírůstkové integraci a testování těchto dvou systémů. Nejprve se ujistěte, že PaymentApprover a zbytek hostina teď pracují s jiným systémem úspěšně, než budou pracovat s PaymentProcessing.

 Následující mapa kódu ukazuje nová volání mezi večeři Now a PaymentApprover:

 ![Aktualizovaný graf závislosti s integrovaným systémem](../modeling/media/depgraph_intsystem.png)

 **Mapa kódu s aktualizovanými voláními metody**

 Po potvrzení, že systém funguje podle očekávání, večeře teď Zakomentovat kód PaymentProcessing. Sestavy ověření vrstvy jsou čisté a výsledná mapa kódu ukazuje, že neexistují žádné další závislosti PaymentProcessing:

 ![Graf závislosti bez PaymentProcessing](../modeling/media/depgraph_nomore.png)

 **Mapa kódu bez PaymentProcessing**

#### <a name="drawing-a-dependency-diagram"></a>Vykreslení diagramu závislostí

Diagram závislostí má následující hlavní funkce:

- *Vrstvy* popisují logické skupiny artefaktů.

- *Odkaz* je přidružení mezi vrstvou a artefaktem.

     Chcete-li vytvořit vrstvy z artefaktů, přetáhněte položky z Průzkumník řešení, mapy kódu, Zobrazení tříd nebo Prohlížeč objektů. Chcete-li nakreslit nové vrstvy a propojit je s artefakty, použijte panel nástrojů nebo klikněte pravým tlačítkem myši na plochu diagramu, vytvořte vrstvy a přetáhněte položky do těchto vrstev.

     Číslo ve vrstvě znázorňuje počet artefaktů, které jsou propojeny s vrstvou. Tyto artefakty mohou být obory názvů, projekty, třídy, metody a tak dále. Při interpretaci počtu artefaktů ve vrstvě mějte na paměti následující:

  - Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.

       Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.

  - Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.

    Chcete-li zobrazit artefakty, které jsou propojeny s vrstvou, klikněte pravým tlačítkem myši na závislost a potom kliknutím na možnost **Zobrazit odkazy** otevřete **Průzkumníka vrstev**.

- *Závislost* znamená, že jedna vrstva může použít funkci v jiné vrstvě, ale ne naopak. *Obousměrná závislost* znamená, že jedna vrstva může použít funkci v jiné vrstvě a naopak.

     Chcete-li zobrazit existující závislosti v diagramu závislostí, klikněte pravým tlačítkem myši na plochu diagramu a potom klikněte na možnost **Generovat závislosti**. Chcete-li popsat zamýšlené závislosti, nakreslete nové.

Přečtěte si:

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)

- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)

- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Shrnutí: síly diagramů závislostí

Diagramy závislostí vám pomůžou:

- Popište logickou architekturu systému v závislosti na funkcích jeho artefaktů.

- Ujistěte se, že kód ve vývoji odpovídá zadanému návrhu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-|-|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li vytvořit vrstvy, vygenerujte mapu kódu a pak položky na mapě seskupte jako potenciální vrstvy. Přetáhněte skupiny z mapy do diagramu závislostí.<br /><br /> Přečtěte si:<br /><br /> - [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|-|-|
|**Fóra**|- [Nástroje pro vizualizaci sady Visual Studio & modelování](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Viz také

- [Vizualizace kódu](../modeling/visualize-code.md)
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
- [Používání modelů v agilním vývoji](/previous-versions/ff398061(v=vs.140))
- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)