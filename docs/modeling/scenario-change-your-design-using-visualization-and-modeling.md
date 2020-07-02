---
title: 'Scénář: Změna návrhu pomocí vizualizace a modelování'
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c0e971a2a38013ae75287467404e3321e3c4d37
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544193"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scénář: Změna návrhu pomocí vizualizace a modelování

Ujistěte se, že váš softwarový systém splňuje požadavky uživatelů pomocí nástrojů pro vizualizaci a modelování v aplikaci Visual Studio.
Pomocí nástrojů, jako jsou mapy kódu, diagramy závislostí a diagramy tříd:

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

## <a name="scenario-overview"></a>Přehled scénáře

Tento scénář popisuje díly z životního cyklu vývoje softwaru dvou fiktivních společností: večeře nyní a Lucerne Publishing. Večeře teď poskytuje webovou službu pro doručování na základě jídla v Seattlu. Zákazníci můžou objednat jídla a platit za ně na webu večeře Now. Objednávky se pak odesílají do příslušné místní restaurace pro doručení. Lucerne Publishing, společnost v New Yorku, provozuje na webu několik firem současně. Například spouštějí web, kde můžou zákazníci publikovat recenze na restaurace.

Společnost Lucerne nedávno získala večeři a chce provést následující změny:

- Integrujte své weby přidáním funkcí recenze pro restaurace do hostina Now.

- V systému společnosti Lucerne teď nahraďte platební systém.

- Rozbalte službu večeře Now v rámci oblasti.

Večeře teď používá SCRUM a extrémní programování. Mají velmi vysoké pokrytí testů a velmi nepodporovaný kód. Tím se minimalizují rizika vytvořením malých, ale funkčních verzí systému a následným přidáním funkcí. Vyvíjejí svůj kód v krátkých a častých iteracích. To jim umožní mít jistotu na změnu, často Refaktorovat kód a vyhnout se "velkému návrhu předem".

Společnost Lucerne udržuje mnohem větší a složitou kolekci systémů, z nichž některé jsou starší než 40 let. Jsou velmi opatrní při provádění změn z důvodu složitosti a rozsahu starší verze kódu. Dodržují přísnější proces vývoje, který předvedl návrh podrobných řešení a dokumentuje návrh a změny, ke kterým došlo během vývoje.

Oba týmy používají diagramy modelování v aplikaci Visual Studio, které jim pomůžou vyvíjet systémy, které vyhovují potřebám uživatelů. Používají Team Foundation Server společně s dalšími nástroji, které jim pomohou naplánovat, uspořádat a spravovat jejich práci.

Další informace o Team Foundation Server najdete v tématech:

- [Plánování a sledování práce](#plan-and-track-work)

- [Testování, ověřování a vrácení aktualizovaného kódu](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Role architektury a modelování diagramů při vývoji softwaru

Následující tabulka popisuje role, které tyto nástroje mohou hrát během několika různých fází životního cyklu vývoje softwaru:

||**Modelování uživatelských požadavků**|**Modelování obchodních procesů**|**Architektura systému & návrh**|**Zkoumání & vizualizace kódu**|**Ověření**|
|------|-|-|-|-|-|
|Diagram DSL (Domain-Specific Language)|Ano|Ano|Ano|||
|Diagram závislosti, ověřování vrstvy|||Ano|Ano|Ano|
|Mapa kódu|||Ano|Ano|Ano|
|Návrhář tříd (založený na kódu)||||Ano||

Chcete-li kreslit diagramy závislostí, je nutné vytvořit projekt modelování jako součást stávajícího řešení nebo nového. Tyto diagramy musí být vytvořeny v projektu modelování.
Položky v diagramech závislostí se nacházejí v projektu modelování, ale nejsou uloženy ve společném modelu. Mapy kódu a diagramy tříd .NET vytvořené z kódu existují mimo projekt modelování.

Přečtěte si:

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Oba týmy také používají ověření závislostí, aby se zajistilo, že kód ve vývoji zůstane v souladu s návrhem. Přečtěte si:

- [Udržování kódu v souladu s návrhem](#ValidatingCode)

- [Popište logickou architekturu: diagramy závislosti](#DescribeLayers)

- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Některé verze sady Visual Studio podporují ověřování závislostí a verze map kódu jen pro čtení pro vizualizaci a modelování. Pokud chcete zjistit, které edice sady Visual Studio podporují tuto funkci, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Pochopení a sdělování informací o systému

Neexistuje žádné předepsané pořadí pro použití diagramů modelování sady Visual Studio, takže je můžete použít tak, jak vyhovují vašim potřebám nebo přístupu. Týmy obvykle opakovaně přepínají své modely v rámci projektu. Každý diagram nabízí konkrétní sílu, které vám pomůžou pochopit, popsat a komunikovat různé aspekty systému ve vývoji.

Večeře nyní a Lucerne komunikují mezi sebou a s účastníky projektu pomocí diagramů jako jejich společného jazyka. Například večeře teď používá diagramy k provádění těchto úkolů:

- Vizualizujte existující kód.

- Komunikujte s vojtěškou o nových nebo aktualizovaných uživatelských scénářích.

- Identifikujte změny, které jsou potřeba k podpoře nových nebo aktualizovaných uživatelských scénářů.

Společnost Lucerne používá diagramy k provádění těchto úkolů:

- Přečtěte si o tomto obchodním procesu večeři.

- Pochopení návrhu systému.

- Komunikujte s večeři teď o nových nebo aktualizovaných požadavcích uživatelů.

- Aktualizuje dokument do systému.

Diagramy jsou integrované s Team Foundation Server, takže týmy můžou snadněji plánovat, spravovat a sledovat práci. Například používají modely k identifikaci testových případů a vývojářských úloh a k odhadu jejich práce. Společnost Lucerne propojuje Team Foundation Server pracovní položky s prvky modelu tak, aby mohly sledovat průběh a ujistit se, že systém splňuje požadavky uživatelů. Například propojí případy použití s pracovními položkami testovacího případu, takže uvidí, že případy použití jsou splněné, když všechny testy proběhnou.

Než týmy zaregistrují změny, ověří kód proti testům a návrhu spuštěním sestavení, která zahrnují ověřování závislosti a automatizované testy. To pomáhá zajistit, že aktualizovaný kód není v konfliktu s návrhem a přerušit dříve funkční funkčnost.

### <a name="identify-changes-to-the-existing-system"></a>Identifikujte změny stávajícího systému

Večeře teď musí odhadnout náklady na splnění nového požadavku. Tato změna závisí částečně na tom, kolik změn bude mít vliv na ostatní části systému. Abychom jim mohli porozumět, jeden z vývojářů s večeři teď vytvoří tyto mapy a diagramy z existujícího kódu:

|**Mapa nebo diagram**|**Objeví**|
|-|-|
|*Mapa kódu*<br /><br /> Přečtěte si:<br /><br /> - [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)<br />- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Závislosti a další vztahy v kódu.<br /><br /> Například večeře teď může začít kontrolou map kódu sestavení pro přehled sestavení a jejich závislostí. Mohou přejít k podrobnostem o mapách a prozkoumat obory názvů a třídy v těchto sestaveních.<br /><br /> Večeře teď může také vytvořit mapy k prozkoumání konkrétních oblastí a dalších druhů vztahů v kódu. Používají Průzkumník řešení k vyhledání a výběru oblastí a vztahů, které vás zajímají.|
|*Diagram tříd založený na kódu*<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Existující třídy v kódu|

 Například vývojář Vytvoří mapu kódu. Upraví svůj obor tak, aby se zaměřil na oblasti, které budou tímto novým scénářem ovlivněny. Tyto oblasti jsou vybrané a zvýrazněné na mapě:

 ![Graf závislosti oboru názvů](../modeling/media/namespace_reviewsystem.png)

 **Mapa kódu oboru názvů**

 Vývojář rozšíří vybrané obory názvů tak, aby viděli jejich třídy, metody a vztahy:

 ![Graf závislosti rozšířeného oboru názvů](../modeling/media/dep_reviewsystem.png)

 **Rozšířené mapování kódu oboru názvů s viditelnými odkazy mezi skupinami**

 Vývojář prověřuje kód, aby našli příslušné třídy a metody. Chcete-li zobrazit účinky každé změny při jejich provádění, znovu vygenerujte mapy kódu po každé změně. Viz [vizualizuje kód](../modeling/visualize-code.md).

 Aby bylo možné popsat změny v jiných částech systému, jako jsou komponenty nebo interakce, může tým vykreslit tyto prvky do tabulí. Mohou také nakreslit následující diagramy v aplikaci Visual Studio tak, aby bylo možné údaje zachytit, spravovat a pochopit v obou týmech:

|**Diagram**|**Udává**|
|-|-|
|*Diagram tříd založený na kódu*<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Existující třídy v kódu.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Udržování kódu v souladu s návrhem
 Večeře teď musí zajistit, aby aktualizovaný kód zůstával v souladu s návrhem. Vytvářejí diagramy závislostí, které popisují vrstvy funkčnosti v systému, určují povolené závislosti mezi nimi a přiřadí artefakty řešení těmto vrstvám.

|**Diagram**|**Udává**|
|-|-|
|*Diagram závislosti*<br /><br /> Přečtěte si:<br /><br /> - [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />- [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)<br />- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|Logická architektura kódu.<br /><br /> Diagram závislosti uspořádá a mapuje artefakty v řešení sady Visual Studio do abstraktních skupin nazývaných *vrstvy*. Tyto vrstvy identifikují role, úlohy nebo funkce, které tyto artefakty provádějí v systému.<br /><br /> Diagramy závislostí jsou užitečné pro popis zamýšleného návrhu systému a ověřování vývojového kódu s tímto návrhem.<br /><br /> Chcete-li vytvořit vrstvy, přetáhněte položky z Průzkumník řešení, mapy kódu, Zobrazení tříd a Prohlížeč objektů. Chcete-li nakreslit nové vrstvy, použijte panel nástrojů nebo klikněte pravým tlačítkem myši na plochu diagramu.<br /><br /> Chcete-li zobrazit existující závislosti, klikněte pravým tlačítkem na plochu diagramu závislosti a potom klikněte na možnost **Generovat závislosti**. Chcete-li zadat zamýšlené závislosti, nakreslete nové závislosti.|

Například následující diagram závislosti popisuje závislosti mezi vrstvami a počet artefaktů, které jsou spojeny s každou vrstvou:

![Diagram závislosti integrovaného platebního systému](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram závislosti**

Aby se zajistilo, že během vývoje kódu nedojde ke konfliktům s návrhem, týmy využívají ověřování závislostí na sestaveních, která běží na Azure DevOps. Také vytvoří vlastní úlohu MSBuild, která vyžaduje ověření závislosti v operacích vrácení se změnami. Používají sestavy sestavení ke shromáždění chyb ověřování.

Přečtěte si:

- [Použití vizuálního návrháře](/azure/devops/pipelines/get-started-designer)

- [TFVC ověřované vrácení se změnami](/azure/devops/pipelines/build/triggers)

- [Úkoly sestavení a vydání](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Obecné tipy pro vytváření a používání modelů

- Většina diagramů se skládá z uzlů, které jsou propojeny pomocí řádků. Pro každý typ diagramu poskytuje sada nástrojů různé druhy uzlů a řádků.

   Chcete-li otevřít sadu nástrojů, klikněte v nabídce **zobrazení** na příkaz **Sada nástrojů**.

- Chcete-li vytvořit uzel, přetáhněte jej ze sady nástrojů do diagramu. Některé druhy uzlů musí být přetaženy na existující uzly. Například v diagramu komponent musí být do existující součásti přidán nový port.

- Chcete-li vytvořit čáru nebo připojení, klikněte na příslušný nástroj na panelu nástrojů, klikněte na zdrojový uzel a potom klikněte na cílový uzel. Některé řádky lze vytvořit pouze mezi určitými typy uzlů. Když přesunete ukazatel na možný zdroj nebo cíl, ukazatel myši označuje, zda lze vytvořit připojení.

### <a name="plan-and-track-work"></a>Plánování a sledování práce

Diagramy modelování sady Visual Studio jsou integrované s Team Foundation Server, takže můžete plánovat, spravovat a sledovat práci snadněji. Oba týmy používají modely k identifikaci testových případů a vývojářských úloh a k odhadování jejich práce. Společnost Lucerne vytvoří a propojí Team Foundation Server pracovní položky s prvky modelu, jako jsou například případy použití nebo komponenty. To pomáhá sledovat jejich průběh a sledovat jejich práci zpátky do požadavků uživatelů. To jim pomůže zajistit, aby jejich změny i nadále splňovaly tyto požadavky.

Jak fungují, týmy aktualizují své pracovní položky tak, aby odrážely čas strávený na svých úkolech. Také monitorují a nastavují jejich práci pomocí následujících funkcí Team Foundation Server:

- Každodenní *vypalování sestav* , které ukazují, zda budou dokončeny plánované práce v očekávaném čase. Generují další podobné sestavy z Team Foundation Server ke sledování průběhu chyb.

- *List iterace* , který používá aplikaci Microsoft Excel k usnadnění monitorování týmu a vyrovnání zatížení mezi jeho členy. Tento list je propojen s Team Foundation Server a poskytuje fokus na diskuzi během pravidelných setkání o průběhu.

- *Řídicí panel pro vývoj* , který používá Office Project, aby tým informoval o důležitých informacích o projektu.

Přečtěte si:

- [O agilních nástrojích a agilních řízeních projektů](/azure/devops/boards/backlogs/backlogs-overview?view=vsts)

- [Grafy, řídicí panely a widgety (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts)

- [Vytvoření nevyřízených položek a úkolů pomocí projektu](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a>Testování, ověřování a vrácení kódu se změnami

Jak týmy dokončí každý úkol, kontrolují svůj kód do správy zdrojového kódu a zobrazují připomenutí od Team Foundation Server, pokud je zapomenete. Než Team Foundation Server akceptuje jejich vrácení se změnami, týmy spustí testy jednotek a ověření závislostí pro ověření kódu proti testovacím případům a návrhu. Používají Team Foundation Server k pravidelnému spouštění buildů, automatizované testy jednotek a ověřování závislostí. To pomáhá zajistit, že kód splňuje následující kritéria:

- Funguje.

- Neruší předchozí pracovní kód.

- Nekoliduje s návrhem.

Večeře teď má velkou kolekci automatizovaných testů, které může společnost Lucerne použít, protože skoro všechno stále platí. Společnost Lucerne může také vytvořit tyto testy a přidat nové, aby se pokryly nové funkce. Zároveň aplikace Visual Studio používá ke spouštění manuálních testů.

Aby se zajistilo, že kód odpovídá návrhu, týmy konfigurují sestavení ve službě Azure DevOps tak, aby zahrnovaly ověřování závislostí. Pokud dojde k jakýmkoli konfliktům, vygeneruje se sestava s podrobnostmi.

Přečtěte si:

- [Testování aplikace](/azure/devops/test/overview?view=vsts)

- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)

- [Použít správu verzí](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualizace systému pomocí vizualizace a modelování

Společnost Lucerne a večeře teď musí integrovat své platební systémy. Následující části znázorňují diagramy modelování v aplikaci Visual Studio, které jim pomůžou provést tuto úlohu:

- [Vizualizovat existující kód: mapy kódu](#VisualizeCode)

- [Definování glosáře typů: diagramy tříd](#DefineClasses)

- [Popište logickou architekturu: diagramy závislosti](#DescribeLayers)

Přečtěte si:

- [Vizualizace kódu](../modeling/visualize-code.md)

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Vizualizovat existující kód: mapy kódu

Mapy kódu ukazují aktuální organizaci a vztahy v kódu. Položky jsou reprezentovány *uzly* na mapě a vztahy jsou reprezentovány pomocí *odkazů*. Mapy kódu vám mohou pomáhat při provádění následujících typů úloh:

- Prozkoumejte Neznámý kód.

- Pochopení, kde a jak může navrhovaná změna ovlivnit existující kód.

- Najděte oblasti složitosti, přirozených závislostí nebo vzorů nebo jiných oblastí, které mohou využívat vylepšení.

Například večeře teď musí odhadnout náklady na aktualizaci komponenty PaymentProcessing. Tato změna závisí částečně na tom, kolik změn bude mít vliv na ostatní části systému. Abychom jim mohli porozumět, jeden z vývojářů v současnosti nyní generuje mapy kódu z kódu a upraví fokus oboru na oblasti, které by mohly být ovlivněny změnou.

Následující mapa znázorňuje závislosti mezi třídou PaymentProcessing a dalšími částmi v systému večeře Now, která se zobrazí jako vybraná:

![Graf závislosti pro platební systém pro večeři nyní](../modeling/media/dep_dnpayment.png)

**Mapa kódu pro platební systém pro večeři Now**

Vývojář prozkoumá mapu rozbalením třídy PaymentProcessing a výběrem jejích členů zobrazíte oblasti, které jsou potenciálně ovlivněny:

![Metody uvnitř PaymentProcessing a závislosti](../modeling/media/depgraph_expandeddn.png)

**Metody uvnitř třídy PaymentProcessing a jejich závislosti**

Generují následující mapu pro platební systém Lucerne ke kontrole jeho tříd, metod a závislostí. Tým uvidí, že systém Lucerne může také vyžadovat práci k interakci s ostatními součástmi večeře nyní:

![Graf závislosti pro platební systém Lucerne](../modeling/media/depgraph_lucernepay.png)

**Mapa kódu pro platební systém Lucerne**

Oba týmy pracují společně, aby určily změny, které jsou potřeba k integraci těchto dvou systémů. Rozhodnou se k refaktorování kódu, aby bylo snazší ho aktualizovat. Třída PaymentApprover se přesune do oboru názvů DinnerNow. Business a bude vyžadovat některé nové metody. Třídy večeře Now, které zpracovávají transakce, budou mít svůj vlastní obor názvů. Týmy vytvářejí a používají pracovní položky k plánování, uspořádání a sledování práce. Propojí pracovní položky s prvky modelu, kde je to užitečné.

Po reorganizaci kódu generují týmy novou mapu kódu pro zobrazení aktualizované struktury a vztahů:

![Graf závislosti se stejným uspořádáním kódu](../modeling/media/depgraph_integrated.png)

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

|**Diagram**|**Udává**|
|-|-|
|Diagram závislosti|Logická architektura systému. Použijte ověřování závislostí a ujistěte se, že kód zůstává v souladu s návrhem.<br /><br /> Abyste mohli identifikovat existující závislosti nebo zamýšlené závislosti, vytvořte mapu kódu a položky související s seskupením. Chcete-li vytvořit diagram závislostí, přečtěte si téma:<br /><br /> - [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)|
|Diagram tříd (založený na kódu)|Existující třídy v kódu pro určitý projekt.<br /><br /> Chcete-li vizualizovat a upravit existující třídu v kódu, použijte Návrhář tříd.<br /><br /> Viz [Postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Definování glosáře typů: diagramy tříd
 Diagramy tříd definují entity, pojmy nebo koncepty, které jsou součástí systému a jejich vztahů mezi sebou. Například můžete použít tyto diagramy během vývoje k popisu atributů a operací pro každou třídu, bez ohledu na jejich jazyk implementace nebo styl.

 Aby mohl společnost Lucerne popsat a diskutovat entity, které se účastní případu použití procesu platby, nakreslí následující diagram tříd:

 ![Zpracování entit plateb v diagramu tříd](../modeling/media/uml_payentities.png)

 **Zpracování entit platby v diagramu tříd**

 Tento diagram znázorňuje, že zákazník může mít mnoho objednávek a různé způsoby platby za objednávky. BankAccount a CreditCard dědí z platby.

 Během vývoje používá společnost Lucerne následující diagram tříd k popisu a diskuzi o podrobnostech každé třídy:

 ![Podrobnosti o zpracování platebních entit v diagramu tříd](../modeling/media/uml_payment.png)

 **Podrobnosti o platbě procesu v diagramu tříd**

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

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a>Popište logickou architekturu: diagramy závislosti
 Diagramy závislostí popisují logickou architekturu systému uspořádáním artefaktů ve vašem řešení do abstraktních skupin nebo *vrstev*. Artefakty mohou být mnoho věcí, například obory názvů, projekty, třídy, metody a tak dále. Vrstvy reprezentují a popisují role nebo úkoly, které artefakty provádějí v systému. Můžete také zahrnout ověřování vrstvy do sestavení a operace vrácení se změnami, abyste se ujistili, že kód zůstává v souladu s jeho návrhem.

 Chcete-li zachovat kód v souladu s návrhem, večeře Now a Lucerne použijte následující diagram závislostí k ověření kódu při jeho vývoje:

 ![Diagram závislosti integrovaného platebního systému](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram závislostí pro večeři je teď integrovaný s vojtěškou.**

 Vrstvy na tomto diagramu odkazují na odpovídající artefakty řešení večeře Now a Lucerne. Například obchodní vrstva odkazuje na obor názvů DinnerNow. Business a její členy, které nyní obsahují třídu PaymentApprover. Vrstva přístupu k prostředkům odkazuje na obor názvů DinnerNow. data. Šipky nebo *závislosti*určují, že funkce ve vrstvě přístupu k prostředkům může používat jenom obchodní vrstva. Jak týmy aktualizují svůj kód, provádí se pravidelné ověřování vrstev za účelem zachycení konfliktů při jejich výskytu a k usnadnění jejich řešení.

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

## <a name="see-also"></a>Viz také:

- [Vizualizace kódu](../modeling/visualize-code.md)
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
- [Používání modelů v agilním vývoji](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)
