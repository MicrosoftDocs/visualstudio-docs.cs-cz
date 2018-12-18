---
title: 'Scénář: Změna návrhu pomocí vizualizace a modelování'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc8066148b2c8612b3a07922e15422022b8c9c4d
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967503"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scénář: Změna návrhu pomocí vizualizace a modelování

Ujistěte se, že softwarový systém vyhovuje potřebám uživatelů pomocí vizualizace a modelování nástroje v sadě Visual Studio.
Pomocí nástrojů, jako je map kódu, diagramů závislostí a diagramů tříd do:

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

## <a name="scenario-overview"></a>Přehled scénářů

Tento scénář popisuje epizody z životního cyklu vývoje softwaru dvou fiktivních společností: večeře nyní a Lucerne Publishing. Společnost dinner Now poskytuje služby pro doručování webového pokrmů v Seattlu. Zákazníci mohou objednat jídlo a zaplatit za ně na webu Dinner Now. Objednávky jsou potom odeslány příslušné místní restauraci pro dodání. Společnost Lucerne Publishing, společnost působící v New Yorku, provozuje několik podniků, vypnout a na webu. Například spusťte web, kde můžou zákazníci posílat své recenze na restauraci.

Společnost Lucerne nedávno odkoupila web Dinner Now a chce provést následující změny:

- Integrujte svoje weby přidáním funkce recenzování restaurací na web Dinner Now.

- Nahraďte společnosti Dinner Now platební systém společnosti Lucerne systému.

- Rozbalte službu Dinner Now v oblasti.

Společnost dinner Now používá programování SCRUM a eXtreme. Mají velmi vysoké testovací pokrytí a velmi málo nepodporovaného kódu. Minimalizují riziko vytvářením malých, ale funkčních verzí systému a pak postupně přidávají funkce. Vyvíjejí svůj kód v krátkých a častých iteracích. Díky tomu mohou podpořit změnu s jistotou, často Refaktorovat kód a vyhnout se "velkému návrhu".

Společnost Lucerne udržuje výrazně větší a složitější kolekci systémů, z nichž některé jsou více než 40 let. Jsou velmi opatrní při provádění změn z důvodu složitosti a rozsahu staršího kódu. Následují přísnější vývojový proces, preferují návrh podrobných řešení a dokumentaci návrhu a změn, které nastanou během vývoje.

Oba týmy používají diagramy modelování v sadě Visual Studio k usnadnění vývoje systémů, které vyhovují potřebám uživatelů. Aby to pomohl ostatním plánovat, organizovat a spravovat svou práci používají Team Foundation Server spolu s dalšími nástroji.

Další informace o Team Foundation Server naleznete v tématu:

- [Plánování a sledování práce](#planning-and-tracking-work)

- [Testování, ověřování a vrácení kódu se změnami](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a> Role architektury a modelování diagramů při vývoji softwaru

Následující tabulka popisuje role, které tyto nástroje mohou hrát při více a v různých fázích životního cyklu vývoje softwaru:

||**Modelování požadavků uživatelů**|**Modelování obchodních procesů**|**Architektura systému a Design**|**Vizualizace kódu & průzkum**|**Ověření**|
|------|-|-|-|-|-|
|Diagram jazyka specifického pro doménu (DSL)|Ano|Ano|Ano|||
|Diagram závislostí, ověřování vrstvy|||Ano|Ano|Ano|
|Mapy kódu|||Ano|Ano|Ano|
|Návrhář tříd (založený na kódu)||||Ano||

Chcete-li nakreslit diagramy závislostí, musíte vytvořit projekt modelování jako součást existujícího řešení nebo nové. Tyto diagramy musí být vytvořeny v projektu modelování.
Položky v diagramech závislostí se nacházejí v projektu modelování, ale nejsou uloženy ve společném modelu. Mapy kódu a diagramy tříd .NET vytvořené z kódu existují mimo projekt modelování.

Další informace:

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Oba týmy používají ověřování závislostí také aby se zajistilo, že kód ve vývoji zůstává konzistentní s návrhem. Další informace:

- [Udržování kódu v souladu s návrhem](#ValidatingCode)

- [Popište logickou architekturu: diagramy závislostí](#DescribeLayers)

- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Některé verze sady Visual Studio podporují ověřování závislostí a map kódu verze jen pro čtení pro vizualizaci a modelování. Chcete-li zjistit, jaké edice sady Visual Studio podporují tuto funkci, přečtěte si téma [podpora edice nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Pochopení a sdělování informací o systému

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

Než týmy vrátí změny, ověří kód proti testům a návrhu spuštěním sestavení, která obsahují ověřování závislostí a automatizované testy. To pomáhá, ujistěte se, že aktualizovaný kód není v konfliktu s návrhem a nezruší dříve fungující funkce.

### <a name="identify-changes-to-the-existing-system"></a>Určení změn ve stávajícím systému

Společnost dinner Now musí odhadnout náklady na splnění nového požadavku. To zčásti závisí na tom, jak moc tato změna ovlivní ostatní části systému. Aby pomohl ostatním pochopit, jeden z vývojářů aplikace večeře nyní z existujícího kódu vytvoří tyto mapy a diagramy:

|**Mapování nebo diagramu**|**Ukazuje**|
|-|-|
|*Mapy kódu*<br /><br /> Další informace:<br /><br /> - [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)<br />- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)<br />- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Závislosti a jiné vztahy v kódu.<br /><br /> Například web Dinner Now může začít kontrolou map kódu sestavení přehledné informace o sestavení a jejich závislosti. Mohou se ponořit do mapy pro prozkoumání oborů názvů a třídy v těchto sestaveních.<br /><br /> Společnost dinner Now může také vytváření map prozkoumat určité oblasti a další druhy vztahů v kódu. Používají Průzkumníka řešení najít a vybrat oblasti a vztahy, které je zajímají.|
|*Diagram třídy založený na kódu*<br /><br /> Zobrazit [postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Existující třídy v kódu|

 Například vývojář vytvoří mapu kódu. Nastaví oblast pro zaměření na oblasti, které budou ovlivněny novým scénářem. Tyto oblasti jsou vybrané a zvýrazněné v mapě:

 ![Graf závislosti Namespace](../modeling/media/namespace_reviewsystem.png)

 **Mapy kódu Namespace**

 Vývojář rozbalí vybrané obory názvů zobrazíte jejich třídy, metody a vztahy:

 ![Graf závislosti expandovaného oboru názvů](../modeling/media/dep_reviewsystem.png)

 **Mapy kódu expandovaného oboru názvů s viditelné propojení mezi skupinami**

 Vývojář kontroluje kód k nalezení příslušné tříd a metod. Abyste viděli efekt každé změny při provádění je, znovu vygenerovat mapy kódu po každé změně. Zobrazit [vizualizovat kód](../modeling/visualize-code.md).

 K popisu změn jiných částí systému, jako je například součástí nebo interakcí, může tým kreslit tyto prvky na Tabule. Mohou také nakreslit následující diagramy v aplikaci Visual Studio tak, aby podrobnosti lze zachytit, spravovat a srozumitelné pro oba týmy:

|**Diagramy**|**Popisuje**|
|-|-|
|*Diagram třídy založený na kódu*<br /><br /> Zobrazit [postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Existující třídy v kódu.|

### <a name="ValidatingCode"></a> Udržujte kód v souladu s návrhem
 Společnost dinner Now musí zajistit, že aktualizovaný kód zůstane konzistentní s návrhem. Vytvářejí diagramy závislostí, které popisují vrstvy funkčnosti v systému, určují povolené závislosti mezi nimi a přidružují řešení artefakty k těmto vrstvám.

|**Diagram**|**Popisuje**|
|-|-|
|*Diagram závislostí*<br /><br /> Další informace:<br /><br /> - [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />- [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)<br />- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|Logická architektura kódu.<br /><br /> Závislost diagram organizuje a mapuje artefakty v řešení sady Visual Studio účelem abstrahování skupin nazvaných *vrstvy*. Tyto vrstvy určují role, úlohy nebo funkce, které tyto artefakty provádějí v systému.<br /><br /> Diagramy vrstev jsou užitečné pro popis zamýšleného návrhu systému a ověřování vyvíjeného kódu ve srovnání s tímto návrhem.<br /><br /> Chcete-li vytvořit vrstvy, přetáhněte položky z Průzkumníku řešení, map kódu, zobrazení tříd a prohlížeče objektů. Chcete-li nakreslit nové vrstvy, použijte panel nástrojů nebo kliknutím pravým tlačítkem na plochu diagramu.<br /><br /> Chcete-li zobrazit existující závislosti, klikněte pravým tlačítkem na plochu diagramu a potom klikněte na tlačítko **generovat závislosti**. K určení zamýšlených závislostí, nakreslete nové závislosti.|

 Například následující diagram závislostí popisuje závislosti mezi vrstvami a počet artefaktů, které jsou spojené s každou vrstvou:

 ![Diagram závislostí z integrované platební systém](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram závislostí**

Pokud chcete mít jistotu, že je v konfliktu s návrhem nedochází během vývoje kódu, týmy používají ověřování závislostí v sestavení, které běží na Azure DevOps. Jsou také vytvořit vlastní úkol MSBuild pro vyžadování ověřování závislostí v jejich operacích vrácení se změnami. Používají zprávy sestavení ke shromažďování chyb ověřování.

Další informace:

- [Pomocí vizuálního návrháře](/azure/devops/pipelines/get-started-designer)

- [TFVC hlídané vrácení se změnami](/azure/devops/pipelines/build/triggers#gated)

- [Úlohy sestavení a vydávání](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Obecné tipy pro vytváření a použití modelů

- Většina diagramů se skládá z uzlů, které jsou spojeny čarami. Pro každý typ diagramu obsahuje panel nástrojů různé druhy uzlů a řádků.

     Chcete otevřít v sadě nástrojů **zobrazení** nabídky, klikněte na tlačítko **nástrojů**.

- Chcete-li vytvořit uzel, přetáhněte ho z panelu nástrojů do diagramu. Některé typy uzlů musí být přetaženy do existujících uzlů. Například v diagramu komponent nový port musíte přidat do existující komponenty.

- Chcete-li vytvořit čáru nebo připojení, klikněte na příslušný nástroj v soupravě nástrojů, klikněte na zdrojový uzel a potom klikněte na cílový uzel. Některé řádky lze vytvořit pouze mezi určitými typy uzlů. Když přesunete ukazatel přes možný zdroj nebo cíl, ukazatel myši informuje, zda můžete vytvořit připojení.

### <a name="plan-and-track-work"></a>Plánování a sledování práce

Diagramy modelování Visual Studio jsou integrovány se serverem Team Foundation Server tak, že můžete plánovat, řídit a sledovat svou práci snadněji. Oba týmy používat modely k identifikaci testových případů a vývojářských úloh a k odhadu hotové práce. Společnost Lucerne vytvoří a propojí Team Foundation Server pracovní položky k prvkům modelu, jako jsou případy použití nebo komponenty. To pomáhá sledovat jejich průběh a trasovat jejich práci zpět podle požadavků uživatelů. Pomáhá se ujistit, že jejich změny nadále splňují tyto požadavky.

Jak jejich práce postupuje, týmy aktualizují své pracovní položky tak, aby odrážely čas strávený na úkolech. Také sledují a hlásí stav své práce pomocí následujících funkcí Team Foundation Server:

- Denní *hlášení pracovního tempa* , které uvádí, zda dokončí plánovanou práci v očekávaném čase. Vytvářejí jiné podobné sestavy z Team Foundation serveru ke sledování průběhu chyby.

- *Iterací* , který používá aplikace Microsoft Excel k pomoci sledovat a vyvážit zatížení mezi členy týmu. Tento list je propojen Team Foundation Server a poskytuje zaměření na diskuse během pravidelných schůzky o pokroku.

- A *řídicí panel vývoje* , který používá Office Project k informování o důležitých informacích projektu týmu.

Další informace:

- [Informace o Agilních nástrojů a Agilního řízení projektů](/azure/devops/boards/backlogs/overview?view=vsts)

- [Grafů, řídicích panelů a widgetů (služby Azure DevOps)](/azure/devops/report/dashboards/overview?view=vsts)

- [Vytvoření nevyřízených položek a úkolů pomocí aplikace Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="TestValidateCheckInCode"></a> Testování, ověřování a vrácení kódu se změnami

Jak týmy dokončují jednotlivé úkoly, vraťte jejich kód do správy zdrojového kódu a přijměte připomenutí z Team Foundation Server, v případě, že zapomenete. Předtím, než Team Foundation Server přijme jejich vrácení se změnami, týmy spustí jednotkové testy a ověřování závislostí k ověření kódu proti testovacím případům a návrhu. Používají Team Foundation Server pro sestavení, spouštět automatizované testy jednotky a pravidelně ověřování závislostí. To pomáhá se ujistit, že kód splňuje následující kritéria:

- To funguje.

- Nedojde k poškození dříve funkčního kódu.

- Nevznikne konflikt s návrhem.

Společnost dinner Now má velkou kolekci automatických testů, které společnost Lucerne můžete znovu použít, protože téměř všechny jsou stále platné. Společnost Lucerne může také stavět na těchto testech a přidat nové, aby pokryl nové funkce. Oba také využívají Visual Studio ke spuštění ručních testů.

Pokud chcete mít jistotu, že kód odpovídá návrhu, konfigurují týmy svá sestavení v Azure DevOps zahrnout ověřování závislostí. Pokud dojde k jakýmkoli konfliktům, generování sestavy s podrobnostmi.

Další informace:

- [Testování aplikace](/azure/devops/test/overview?view=vsts)

- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)

- [Správa verzí](http://go.microsoft.com/fwlink/?LinkID=525605)

- [Kanály Azure](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualizace systému pomocí vizualizace a modelování

Společnost Lucerne a Dinner Now musí integrovat své platební systémy. Následující oddíly zobrazují že diagramy modelování v sadě Visual Studio pomáhat při provedení této úlohy:

- [Vizualizujte existující kód: Kódových map](#VisualizeCode)

- [Definice glosáře typů: diagramy třídy](#DefineClasses)

- [Popište logickou architekturu: diagramy závislostí](#DescribeLayers)

Další informace:

- [Vizualizace kódu](../modeling/visualize-code.md)

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

### <a name="VisualizeCode"></a> Vizualizujte existující kód: Kódových map

Mapy kódu zobrazit aktuální organizaci a vztahy v kódu. Položky jsou představovány *uzly* na mapě, a vztahy jsou reprezentovány *odkazy*. Mapy kódu vám může pomoct provádět následující druhy úloh:

- Prozkoumejte neznámý kód.

- Zjistěte, jak a kde navrhované změny mohou ovlivnit existující kód.

- Vyhledejte oblasti složitosti, přirozené závislosti nebo vzory nebo další oblasti, které by mohly mít prospěch z vylepšení.

Například web Dinner Now musí odhadnout náklady na aktualizaci komponenty PaymentProcessing. To zčásti závisí na tom, jak moc tato změna ovlivní ostatní části systému. Chcete-li pomohl ostatním pochopit, jeden z vývojářů aplikace večeře nyní generuje map kódu z kódu a upravuje rozsah zaměření na oblasti, které by mohly mít dopad změnu.

Následující mapa zobrazuje závislosti mezi třídou PaymentProcessing a jiných částí systému Dinner Now, které se zobrazí vybrané:

![Graf závislosti pro platební systém společnosti Dinner Now](../modeling/media/dep_dnpayment.png)

**Mapu kódu pro platební systém společnosti Dinner Now**

Vývojář zkoumá mapy rozšiřující třídou PaymentProcessing a výběrem svých členů pro zobrazení oblastí, které jsou ovlivněny potenciálně ovlivněny:

![Metody uvnitř PaymentProcessing a závislosti](../modeling/media/depgraph_expandeddn.png)

**Metody uvnitř třídy PaymentProcessing a jejich závislosti**

Generují následující mapování pro systém platby Lucerne, chcete-li prověřit své třídy, metody a závislosti. Tým vidí, že systém Lucerne může také vyžadovat práci kvůli interakci s ostatními částmi systému Dinner Now:

![Graf závislosti pro platební systém Lucerne](../modeling/media/depgraph_lucernepay.png)

**Mapu kódu pro systém platby Lucerne**

Oba týmy společně pracují na určení změn, které jsou nutné k integraci obou systémů. Rozhodnou se Refaktorovat kód, takže bude snadněji aktualizovat. Třída PaymentApprover se přesune do oboru názvů DinnerNow.Business a bude vyžadovat některé nové metody. Třídy Dinner Now, které zpracují transakce bude mít vlastní obor názvů. Týmy vytvářejí a použití pracovních položek k plánování, uspořádání a sledování své práce. Spojují pracovní položky k prvkům modelu, kde je to užitečné.

Po reorganizaci kódů týmy generují mapu s novým kódem, chcete-li zobrazit aktualizované strukturu a vztahů:

![Graf závislosti s přeorganizovaným kódem](../modeling/media/depgraph_integrated.png)

**Mapy kódu s přeorganizovaným kódem**

Mapa ukazuje, že třída PaymentApprover je nyní v oboru názvů DinnerNow.Business a má některé nové metody. Třídy transakcí Dinner Now nyní mají své vlastní obor názvů PaymentSystem, což usnadňuje později zacházet s tímto kódem.

#### <a name="creating-a-code-map"></a>Vytvořením mapy kódu

- Získejte rychlý přehled zdrojového kódu použijte následující postup Generovat mapu kódu:

     Na **architektura** nabídky, klikněte na tlačítko **Generovat mapu kódu pro řešení**.

     A získejte rychlý přehled kompilovaného kódu vytvořte mapu kódu prázdné a pak přetáhněte soubory sestavení nebo binární soubory do mapy povrchu.

- Chcete-li prozkoumat určitý kód nebo řešení položky, vyberte položky a vztahy, které chcete zobrazit pomocí Průzkumníka řešení. Potom můžete buď vygenerovat mapu s novým nebo přidat vybrané položky do existující mapování. Zobrazit [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md).

- Můžete prozkoumat na mapě, změňte rozložení tak, aby vyhovovalo typům úkolů, které chcete provést.

     Například pro vizualizaci rozvrstvení v kódu, vyberte rozložení stromové struktury. Zobrazit [Procházet a uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Shrnutí: Silné stránky map kódu
 Mapy kódu vám pomůže:

- Další informace o organizaci a vztahy v existujícím kódu.

- Identifikujte oblasti, které mohou být postiženy navrhovanou změnou.

- Vyhledejte oblasti složitosti, vzorky, vrstvy nebo další oblasti, které lze zlepšit a usnadnit údržbu, změnit a opakovaně používat kód.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popisuje**|
|-|-|
|Diagram závislostí|Logická architektura systému. Pomocí ověřování závislostí se ujistěte, že kód zůstane konzistentní s návrhem.<br /><br /> Chcete-li usnadnit identifikaci existujících dependencys nebo zamýšlený dependencys, vytvořte si mapu kódu a seskupte související položky. Chcete-li vytvořit diagram závislostí, naleznete v tématu:<br /><br /> - [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)|
|Diagram tříd (založený na kódu)|Existující třídy v kódu pro konkrétní projekt.<br /><br /> Chcete-li vizualizovat a upravit existující třídu v kódu, použijte nástroj Návrhář tříd.<br /><br /> Zobrazit [postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="DefineClasses"></a> Definice glosáře typů: diagramy třídy
 Diagramy tříd definují entity, podmínky nebo koncepty, které jsou součástí systému a jejich vztahy mezi sebou. Tyto diagramy můžete použít například během vývoje pro popis atributů a operací pro každou třídu, bez ohledu na jejich implementaci jazyka nebo stylu.

 Aby usnadnili aplikaci Lucerne popsat a diskutovat subjekty, které se účastní případu použití zpracování platby, nakreslí následující diagram tříd:

 ![Entity platby procesu na diagram třídy](../modeling/media/uml_payentities.png)

 **Entity platby procesu na diagram třídy**

 Tento diagram znázorňuje, že zákazník může mít mnoho objednávek a různé způsoby platby za objednávky. BankAccount a CreditCard dědí z Payment.

 Během vývoje používá společnost Lucerne následující diagram tříd k popisu a diskuzi o podrobnostech každá třída:

 ![Detaily platby procesu entity na diagram třídy](../modeling/media/uml_payment.png)

 **Detaily platby procesu na diagram třídy**

#### <a name="drawing-a-class-diagram"></a>Náčrt diagramu třídy

Diagram třídy má následující hlavní funkce:

- Typy, jako jsou třídy, rozhraní a výčty:

    - A *třídy* je definice objektů, které sdílejí určité strukturální nebo behaviorální charakteristiky.

    - *Rozhraní* definuje část externě viditelného chování objektu.

    - *Výčet* je klasifikátor, který obsahuje seznam hodnot literálů.

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

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Shrnutí: Silné stránky diagramů tříd
 Diagramy tříd umožňují definovat:

- Společný glosář termínů pro použití při projednávání potřeb uživatelů a entit, které jsou součástí systému. Zobrazit [modelování uživatelských požadavků](../modeling/model-user-requirements.md).

- Typy, které jsou používány součástmi systému, například komponenty bez ohledu na jejich implementaci. Zobrazit [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).

- Vztahy, například závislosti mezi typy. Například můžete zobrazit, že jeden typ může být přiřazen k více instancím jiného typu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-|-|
|Diagram závislostí|Definujte logickou architekturu systému souvislosti se třídami.<br /><br /> Pomocí ověřování závislostí se ujistěte, že kód zůstane konzistentní s návrhem.<br /><br /> Další informace:<br /><br /> - [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />- [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)<br />- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|
|Mapy kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> K identifikaci tříd, jejich vztahy a jejich metod, vytvořte mapu kódu, který obsahuje tyto prvky.<br /><br /> Další informace:<br /><br /> - [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="DescribeLayers"></a> Popište logickou architekturu: diagramy závislostí
 Diagramy závislostí popište logickou architekturu systému organizací artefaktů ve vašem řešení do abstraktních skupin nebo *vrstvy*. Artefakty mohou být mnoho věcí, například obory názvů, projekty, třídy, metody a tak dále. Vrstvy představují a popisují role a úlohy, které tyto artefakty provádějí v systému. Můžete také zahrnout ověřování vrstvy v sestavení a operace vrácení se změnami zajistit, že kód zůstane konzistentní s návrhem.

 Chcete-li byl kód zachován konzistentní s návrhem, použijte web Dinner Now a Lucerne následující diagram závislostí k ověřování svého kódu, jak se vyvíjí:

 ![Diagram závislostí z integrované platební systém](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram závislostí pro web Dinner Now integrovaný se systémem Lucerne**

 Vrstvy v tomto diagramu odkaz na odpovídající artefaktů řešení Dinner Now a Lucerne. Například, propojení obchodní vrstvy do oboru názvů DinnerNow.Business a jeho členy, které teď obsahují obsahuje třídu PaymentApprover. Přístup k prostředkům vrstva obsahuje odkazy na obor názvů DinnerNow.Data. Šipky, nebo *závislosti*, určete, že pouze vrstva Business může použít funkci ve vrstvě přístupu k prostředkům. Jak týmy aktualizují svůj kód, vrstva ověřování je prováděna pravidelně, aby zachytila konflikty při jejich výskytu a pomohla týmům je rychle řešit.

 Týmy pracují společně, postupně integrují a testují tyto dva systémy. Nejprve se ujistí, že PaymentApprover a zbytek systému Dinner Now spolupracují úspěšně předtím, než se vypořádají s PaymentProcessing.

 Následující mapa kódu zobrazuje nová volání mezi Dinner Now a PaymentApprover:

 ![Graf závislosti aktualizované pomocí integrovaného systému](../modeling/media/depgraph_intsystem.png)

 **Mapy kódu s voláním aktualizované metody**

 Po potvrzení, že systém funguje podle očekávání, Dinner Now okomentuje kód PaymentProcessing. Zprávy ověření vrstvy jsou čisté a výsledný mapy kódu ukazuje, že neexistují žádné další závislosti PaymentProcessing:

 ![Graf závislosti bez funkce PaymentProcessing](../modeling/media/depgraph_nomore.png)

 **Mapy kódu bez funkce PaymentProcessing**

#### <a name="drawing-a-dependency-diagram"></a>Náčrt diagramu závislostí

Diagram závislostí má následující hlavní funkce:

- *Vrstvy* popisují logické skupiny artefaktů.

- A *odkaz* je přidružení mezi vrstvou a artefaktem.

     Chcete-li vytvořit vrstvu z artefaktů, přetáhněte položky z Průzkumníku řešení, map kódu, zobrazení tříd nebo prohlížeči objektů. Chcete-li nakreslit nové vrstvy a propojit je s artefakty, použijte panel nástrojů nebo klikněte pravým tlačítkem na plochu diagramu pro vytvoření vrstvy a přetáhněte položky k těmto vrstvám.

     Číslo ve vrstvě zobrazuje počet artefaktů, které jsou spojeny s vrstvou. Tyto artefakty mohou být obory názvů, projekty, třídy, metody a tak dále. Při interpretaci počtu artefaktů ve vrstvě mějte na paměti následující:

  - Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.

       Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.

  - Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.

    Chcete-li zobrazit artefakty, které jsou propojeny s vrstvou, klikněte pravým tlačítkem na závislost a potom klikněte na tlačítko **zobrazit odkazy** otevřete **Průzkumník vrstev**.

- A *závislost* znamená, že jedna vrstva může použít funkci v jiné vrstvě, ale ne naopak. A *obousměrná závislost* znamená, že jedna vrstva může použít funkci v jiné vrstvě a naopak.

     Chcete-li zobrazit existující závislosti na diagram závislostí, klikněte pravým tlačítkem na plochu diagramu a potom klikněte na tlačítko **generovat závislosti**. K popisu zamýšlených závislostí, nakreslete nové.

Další informace:

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)

- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)

- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Shrnutí: Silné stránky diagramů závislostí

Diagramy závislosti umožňují:

- Popište logickou architekturu systému podle funkcí jeho artefaktů.

- Ujistěte se, že kód ve vývoji odpovídá zadanému návrhu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-|-|
|Mapy kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li vytvořit vrstvy, Generovat mapu kódu a potom seskupte položky na mapě jako potenciální vrstvy. Přetáhněte skupiny z mapy do diagram závislostí.<br /><br /> Další informace:<br /><br /> - [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)<br />- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|-|-|
|**Fóra**|- [Visual Studio Visualization & Modeling nástroje](http://go.microsoft.com/fwlink/?LinkId=184720)<br />- [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Viz také:

- [Vizualizace kódu](../modeling/visualize-code.md)
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
- [Použití modelů v Agilním vývoji](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)
