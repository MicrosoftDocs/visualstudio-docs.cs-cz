---
title: 'Scénář: Změna návrhu pomocí vizualizace a modelování'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 1400f6d5881d5340ec452297d3579306111391b6
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759746"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Scénář: Změna návrhu pomocí vizualizace a modelování

Ujistěte se, že váš softwarový systém splňuje potřeby uživatelů pomocí vizualizačních a modelovacích nástrojů v sadě Visual Studio.
Pomocí nástrojů, jako jsou mapy kódu, diagramy závislostí a diagramy tříd, můžete:

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

## <a name="scenario-overview"></a>Přehled scénáře

Tento scénář popisuje epizody z životního cyklu vývoje softwaru dvou fiktivních společností: Dinner Now a Lucerne Publishing. Dinner Now poskytuje webovou službu doručování jídel v Seattlu. Zákazníci si mohou objednat jídlo a zaplatit za ně na webových stránkách Dinner Now. Objednávky jsou pak odeslány do příslušné místní restaurace k doručení. Lucerne Publishing, společnost v New Yorku, provozuje několik firem jak off, tak na webu. Například provozují web, na kterém mohou zákazníci zveřejňovat recenze restaurací.

Lucerne nedávno získal večeři nyní a chce provést následující změny:

- Integrujte jejich webové stránky přidáním funkcí pro kontrolu restaurací do aplikace Dinner Now.

- Nahraďte platební systém Dinner Now systémem Lucerne.

- Rozbalte službu Večeři v celém regionu.

Večeře nyní používá SCRUM a eXtreme programování. Mají velmi vysoké pokrytí testu a velmi málo nepodporovaného kódu. Minimalizují rizika vytvořením malých, ale funkčních verzí systému a následným přírůstkovým přidáváním funkcí. Vyvíjejí svůj kód přes krátké a časté iterace. To jim umožňuje přijmout změny s jistotou, refaktorovat kód často a vyhnout se "velký design dopředu".

Lucerne udržuje mnohem větší a komplexní sbírku systémů, z nichž některé jsou více než 40 let staré. Jsou velmi opatrní při provádění změn z důvodu složitosti a rozsahu staršího kódu. Řídí se přísnějším procesem vývoje, dávají přednost návrhu podrobných řešení a dokumentují návrh a změny, ke kterým dochází během vývoje.

Oba týmy používají diagramy modelování v sadě Visual Studio, které jim pomáhají vyvíjet systémy, které splňují potřeby uživatelů. Společně s dalšími nástroji používají team foundation server, který jim pomáhá plánovat, organizovat a spravovat jejich práci.

Další informace o serveru Team Foundation Server naleznete v tématu:

- [Plánování a sledování práce](#plan-and-track-work)

- [Testování, ověřování a vrácení aktualizovaného kódu se změnami](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Role architektury a diagramů modelování ve vývoji softwaru

Následující tabulka popisuje role, které mohou tyto nástroje hrát v různých a různých fázích životního cyklu vývoje softwaru:

||**Modelování požadavků uživatelů**|**Modelování obchodních procesů**|**Systémová architektura & návrh**|**Vizualizace kódu & průzkum**|**Ověření**|
|------|-|-|-|-|-|
|Diagram jazyka specifického pro doménu (DSL)|Ano|Ano|Ano|||
|Diagram závislostí, ověření vrstvy|||Ano|Ano|Ano|
|Mapa kódu|||Ano|Ano|Ano|
|Návrhář třídy (na základě kódu)||||Ano||

Chcete-li nakreslit diagramy závislostí, musíte vytvořit projekt modelování jako součást existujícího nebo nového řešení. Tyto diagramy musí být vytvořeny v projektu modelování.
Položky na diagramy závislostí jsou umístěny v projektu modelování, ale nejsou uloženy ve společném modelu. Mapy kódu a diagramy tříd .NET vytvořené z kódu existují mimo projekt modelování.

Přečtěte si:

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Oba týmy také použít ověření závislostí k ujistěte se, že kód ve vývoji zůstává konzistentní s návrhem. Přečtěte si:

- [Zachování kódu v souladu s návrhem](#ValidatingCode)

- [Popište logickou architekturu: diagramy závislostí](#DescribeLayers)

- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Některé verze sady Visual Studio podporují ověřování závislostí a verze map kódu jen pro čtení pro vizualizaci a modelování. Informace o tom, které edice sady Visual Studio tuto funkci podporují, naleznete [v tématu Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Pochopení a sdělování informací o systému

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

Před týmy zkontrolovat jejich změny, ověří kód proti testy a návrh spuštěním sestavení, které zahrnují ověření závislostí a automatizované testy. To pomáhá zajistit, že aktualizovaný kód není v konfliktu s návrhem a přerušení dříve pracovní funkce.

### <a name="identify-changes-to-the-existing-system"></a>Identifikovat změny stávajícího systému

Večeře nyní musí odhadnout náklady na splnění nového požadavku. To částečně závisí na tom, jak moc tato změna ovlivní ostatní části systému. Chcete-li jim to pochopit, jeden z vývojářů večeři nyní vytvoří tyto mapy a diagramy z existujícího kódu:

|**Mapa nebo diagram**|**Ukazuje**|
|-|-|
|*Mapa kódu*<br /><br /> Přečtěte si:<br /><br /> - [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)<br />- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Závislosti a další vztahy v kódu.<br /><br /> Například večeři nyní může začít kontrolou mapy kódu sestavení pro přehled sestavení a jejich závislosti. Mohou přejít k podrobnostem do mapy prozkoumat obory názvů a třídy v těchto sestaveních.<br /><br /> Večeře nyní můžete také vytvořit mapy prozkoumat konkrétní oblasti a jiné druhy vztahů v kódu. Pomocí Průzkumníka řešení vyhledávají a vybírají oblasti a vztahy, které je zajímají.|
|*Diagram třídy založený na kódu*<br /><br /> Postup: [Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Existující třídy v kódu|

 Například vývojář vytvoří mapu kódu. Upraví svůj rozsah, aby se zaměřila na oblasti, které budou ovlivněny novým scénářem. Tyto oblasti jsou vybrány a zvýrazněny na mapě:

 ![Graf závislostí oboru názvů](../modeling/media/namespace_reviewsystem.png)

 **Mapa kódu oboru názvů**

 Vývojář rozbalí vybrané obory názvů, aby zotřil jejich třídy, metody a vztahy:

 ![Rozšířený graf závislostí oboru názvů](../modeling/media/dep_reviewsystem.png)

 **Rozšířená mapa kódu oboru názvů s viditelnými odkazy mezi skupinami**

 Vývojář zkontroluje kód najít ovlivněné třídy a metody. Chcete-li zobrazit účinky každé změny při jejich vytvoření, regenerovat mapy kódu po každé změně. Viz [Vizualizace kódu](../modeling/visualize-code.md).

 Chcete-li popsat změny v jiných částech systému, jako jsou součásti nebo interakce, tým může čerpat tyto prvky na tabuli. Mohou také nakreslit následující diagramy v sadě Visual Studio tak, aby podrobnosti mohly být zachyceny, spravovány a pochopeny oběma týmy:

|**Diagramy**|**Popisuje**|
|-|-|
|*Diagram třídy založený na kódu*<br /><br /> Postup: [Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Existující třídy v kódu.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Zachovat kód v souladu s návrhem
 Večeři nyní musí ujistěte se, že aktualizovaný kód zůstane konzistentní s návrhem. Vytvářejí diagramy závislostí, které popisují vrstvy funkcí v systému, určují povolené závislosti mezi nimi a přidružují artefakty řešení k těmto vrstvám.

|**Diagram**|**Popisuje**|
|-|-|
|*Diagram závislostí*<br /><br /> Přečtěte si:<br /><br /> - [Vytvoření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: Odkaz](../modeling/layer-diagrams-reference.md)<br />- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)<br />- [Ověření kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|Logická architektura kódu.<br /><br /> Diagram závislostí uspořádá a mapuje artefakty v řešení sady Visual Studio na abstraktní skupiny nazývané *vrstvy*. Tyto vrstvy identifikují role, úkoly nebo funkce, které tyto artefakty provádějí v systému.<br /><br /> Diagramy závislostí jsou užitečné pro popis zamýšleného návrhu systému a ověření vyvíjejícího se kódu proti tomuto návrhu.<br /><br /> Chcete-li vytvořit vrstvy, přetáhněte položky z Průzkumníka řešení, map kódu, zobrazení tříd a prohlížeče objektů. Chcete-li nakreslit nové vrstvy, použijte panel nástrojů nebo klepněte pravým tlačítkem myši na povrch diagramu.<br /><br /> Chcete-li zobrazit existující závislosti, klepněte pravým tlačítkem myši na povrch diagramu závislostí a potom klepněte na příkaz **Generovat závislosti**. Chcete-li určit zamýšlené závislosti, nakreslete nové závislosti.|

Například následující diagram závislostí popisuje závislosti mezi vrstvami a počet artefaktů, které jsou přidruženy ke každé vrstvě:

![Diagram závislostí integrovaného platebního systému](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram závislostí**

Chcete-li se ujistit, že konflikty s návrhem nedochází během vývoje kódu, týmy používá ověření závislostí na sestavení, které jsou spuštěny na Azure DevOps. Také vytvořit vlastní úkol MSBuild vyžadovat ověření závislostí v jejich operacích vrácení se změnami. Používají sestavy sestavení ke shromažďování chyb ověření.

Přečtěte si:

- [Použití vizuálního návrháře](/azure/devops/pipelines/get-started-designer)

- [TFTVC gated vrácení se změnami](/azure/devops/pipelines/build/triggers)

- [Vytváření a vydávání úloh](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Obecné tipy pro vytváření a používání modelů

- Většina diagramů se skládá z uzlů, které jsou propojeny čarami. Pro každý typ diagramu panel nástrojů poskytuje různé druhy uzlů a řádků.

   Chcete-li otevřít panel nástrojů, klepněte v nabídce **Zobrazení** na **položku Panel nástrojů**.

- Chcete-li vytvořit uzel, přetáhněte jej z panelu nástrojů do diagramu. Některé druhy uzlů musí být přetaženy na existující uzly. Například v diagramu komponenty musí být do existující součásti přidán nový port.

- Chcete-li vytvořit čáru nebo připojení, klepněte na příslušný nástroj v panelu nástrojů, klepněte na zdrojový uzel a potom klepněte na cílový uzel. Některé řádky lze vytvořit pouze mezi určitými druhy uzlů. Když přesunete ukazatel nad možný zdroj nebo cíl, ukazatel označuje, zda můžete vytvořit připojení.

### <a name="plan-and-track-work"></a>Plánování a sledování práce

Vizovací diagramy modelování jsou integrovány s Team Foundation Server, takže můžete plánovat, spravovat a sledovat práci snadněji. Oba týmy používají modely k identifikaci testovacích případů a vývojových úloh a k odhadu jejich práce. Lucerne vytvoří a propojí pracovní položky Team Foundation Server s prvky modelu, jako jsou případy použití nebo součásti. To jim pomáhá sledovat jejich průběh a sledovat jejich práci zpět k požadavkům uživatelů. To jim pomáhá zajistit, aby jejich změny i nadále splňovat tyto požadavky.

Jak jejich práce postupuje, týmy aktualizovat své pracovní položky tak, aby odrážely čas, který strávili na jejich úkoly. Také monitorují a hlásí stav své práce pomocí následujících funkcí Team Foundation Server:

- Denní *zprávy o vyhoření,* které ukazují, zda dokončí plánovanou práci v očekávaném čase. Generují další podobné sestavy ze serveru Team Foundation Server ke sledování průběhu chyb.

- *Iterace list,* který používá aplikaci Microsoft Excel pomoci týmu sledovat a vyvažovat zatížení mezi jeho členy. Tento list je propojen se serverem Team Foundation A poskytuje fokus pro diskusi během jejich pravidelných schůzek o průběhu.

- Řídicí *panel vývoje,* který pomocí aplikace Office Project informuje tým o důležitých informacích o projektu.

Přečtěte si:

- [O agilních nástrojích a agilním řízení projektů](/azure/devops/boards/backlogs/backlogs-overview?view=vsts)

- [Grafy, řídicí panely a widgety (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts)

- [Vytváření nevyřízených položek a úkolů pomocí Projectu](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a>Test, ověření a vrácení kódu se změnami

Když týmy dokončí každý úkol, zkontrolují svůj kód do správy zdrojového kódu a obdrží připomenutí ze serveru Team Foundation, pokud zapomenou. Předtím, než Team Foundation Server přijme jejich vrácení se změnami, týmy spustit testování částí a ověření závislostí k ověření kódu proti jejich testovacích případů a návrhu. Používají Team Foundation Server ke spuštění sestavení, automatizované testy částí a ověřování závislostí pravidelně. To pomáhá zajistit, že kód splňuje následující kritéria:

- Funguje to.

- Nepřeruší dříve funkční kód.

- Není v rozporu s návrhem.

Večeře nyní má velkou sbírku automatizovaných testů, které Lucerne můžete znovu použít, protože téměř všechny stále platí. Lucerne můžete také stavět na těchto testech a přidat nové, které pokrývají nové funkce. Oba také použít Visual Studio spustit ruční testy.

Chcete-li se ujistit, že kód odpovídá návrhu, týmy nakonfigurují jejich sestavení v Azure DevOps tak, aby zahrnovala ověření závislostí. Pokud dojde ke konfliktům, je generována sestava s podrobnostmi.

Přečtěte si:

- [Testování aplikace](/azure/devops/test/overview?view=vsts)

- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)

- [Použití správy verzí](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Aktualizace systému pomocí vizualizace a modelování

Lucerne a Večeře Nyní musí integrovat své platební systémy. Následující části ukazují diagramy modelování v sadě Visual Studio, které jim pomáhají provádět tento úkol:

- [Vizualizujte existující kód: Mapy kódu](#VisualizeCode)

- [Definování glosáře typů: Diagramy tříd](#DefineClasses)

- [Popište logickou architekturu: diagramy závislostí](#DescribeLayers)

Přečtěte si:

- [Vizualizace kódu](../modeling/visualize-code.md)

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Vizualizujte existující kód: Mapy kódu

Mapy kódu zobrazují aktuální organizaci a vztahy v kódu. Položky jsou reprezentovány *uzly* na mapě a vztahy jsou reprezentovány *odkazy*. Mapy kódu vám mohou pomoci provádět následující typy úkolů:

- Prozkoumejte neznámý kód.

- Zjistěte, kde a jak může navrhovaná změna ovlivnit existující kód.

- Najděte oblasti složitosti, přirozené závislosti nebo vzory nebo jiné oblasti, které mohou mít prospěch z vylepšení.

Například večeři nyní musí odhadnout náklady na aktualizaci PaymentProcessing komponenty. To částečně závisí na tom, jak moc tato změna ovlivní ostatní části systému. Chcete-li jim pomoci pochopit, jeden z vývojáři večeři nyní generuje mapy kódu z kódu a upravuje zaměření oboru na oblasti, které mohou být ovlivněny změnou.

Následující mapa zobrazuje závislosti mezi třídou PaymentProcessing a dalšími částmi systému Večeři, které se zobrazí jako vybrané:

![Graf závislostí pro platební systém Večeři nyní](../modeling/media/dep_dnpayment.png)

**Mapa kódu pro platební systém Večeři nyní**

Vývojář prozkoumá mapu rozšířením třídy PaymentProcessing a výběrem jeho členů zobrazíte oblasti, které jsou potenciálně ovlivněny:

![Metody uvnitř PaymentProcessing a závislosti](../modeling/media/depgraph_expandeddn.png)

**Metody uvnitř třídy PaymentProcessing a jejich závislosti**

Vygenerují následující mapu pro platební systém Lucerne ke kontrole jeho třídy, metody a závislosti. Tým vidí, že systém Lucerne může také vyžadovat práci na interakci s ostatními částmi večeři nyní:

![Graf závislostí pro platební systém Lucerne](../modeling/media/depgraph_lucernepay.png)

**Mapa kódu pro platební systém Lucerne**

Oba týmy spolupracují na určení změn, které jsou nutné k integraci obou systémů. Rozhodnou se refaktorovat část kódu tak, aby bylo snazší jej aktualizovat. Třída PaymentApprover se přesune do oboru názvů DinnerNow.Business a bude vyžadovat některé nové metody. Večeře nyní třídy, které zpracovávají transakce bude mít svůj vlastní obor názvů. Týmy vytvářejí a používají pracovní položky k plánování, uspořádání a sledování své práce. Propojují pracovní položky s prvky modelu, kde je to užitečné.

Po reorganizaci kódu týmy vygenerují novou mapu kódu, aby zotřitili aktualizovanou strukturu a vztahy:

![Graf závislostí s reorganizovaným kódem](../modeling/media/depgraph_integrated.png)

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
|-|-|
|Diagram závislostí|Logická architektura systému. Pomocí ověření závislostí se ujistěte, že kód zůstane konzistentní s návrhem.<br /><br /> Chcete-li identifikovat existující závislosti nebo zamýšlené závislosti, vytvořte mapování kódu a položky související se skupinou. Chcete-li vytvořit diagram závislostí, přečtěte si následující informace:<br /><br /> - [Vytvoření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)|
|Diagram třídy (na základě kódu)|Existující třídy v kódu pro konkrétní projekt.<br /><br /> Chcete-li vizualizovat a upravovat existující třídu v kódu, použijte Návrhář tříd.<br /><br /> Postup: [Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Definování glosáře typů: Diagramy tříd
 Diagramy tříd definují entity, termíny nebo koncepty, které se účastní systému a jejich vzájemné vztahy. Tyto diagramy můžete například použít během vývoje k popisu atributů a operací pro každou třídu, bez ohledu na jejich jazyk implementace nebo styl.

 Chcete-li pomoci Lucerne popsat a diskutovat o entity, které se účastní případu použití procesu platby, nakreslí následující diagram třídy:

 ![Zpracovat entity platby v diagramu třídy](../modeling/media/uml_payentities.png)

 **Zpracovat entity platby v diagramu třídy**

 Tento diagram ukazuje, že zákazník může mít mnoho objednávek a různé způsoby, jak platit za objednávky. BankAccount a CreditCard dědí z platby.

 Během vývoje lucerne používá následující diagram třídy k popisu a diskusi o podrobnostech každé třídy:

 ![Zpracovat podrobnosti entity platby v diagramu třídy](../modeling/media/uml_payment.png)

 **Zpracovat podrobnosti platby v diagramu třídy**

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

- [Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Shrnutí: Silné diagramy tříd
 Diagramy tříd vám pomohou definovat:

- Společný glosář termínů, které se mají používat při diskusi o potřebách uživatelů a entitách, které se účastní systému. Viz [Požadavky uživatelů modelu](../modeling/model-user-requirements.md).

- Typy, které jsou používány části systému, jako jsou součásti, bez ohledu na jejich implementaci. Viz [Model architektury aplikace](../modeling/model-your-app-s-architecture.md).

- Vztahy, například závislosti, mezi typy. Můžete například zobrazit, že jeden typ může být přidružen k více instancím jiného typu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-|-|
|Diagram závislostí|Definujte logickou architekturu systému, pokud se vztahuje k třídám.<br /><br /> Pomocí ověření závislostí se ujistěte, že kód zůstane konzistentní s návrhem.<br /><br /> Přečtěte si:<br /><br /> - [Vytvoření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: Odkaz](../modeling/layer-diagrams-reference.md)<br />- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)<br />- [Ověření kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li identifikovat třídy, jejich vztahy a jejich metody, vytvořte mapu kódu, která zobrazuje tyto prvky.<br /><br /> Přečtěte si:<br /><br /> - [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a>Popište logickou architekturu: diagramy závislostí
 Diagramy závislostí popisují logickou architekturu systému uspořádáním artefaktů v řešení do abstraktních skupin nebo *vrstev*. Artefakty může být mnoho věcí, jako jsou například obory názvů, projekty, třídy, metody a tak dále. Vrstvy představují a popisují role nebo úkoly, které artefakty provádějí v systému. Můžete také zahrnout ověření vrstvy v sestavení a vrácení se změnami operace a ujistěte se, že kód zůstane konzistentní s jeho návrhu.

 Chcete-li zachovat kód v souladu s návrhem, večeři nyní a Lucerne použít následující diagram závislostí k ověření jejich kódu, jak se vyvíjí:

 ![Diagram závislostí integrovaného platebního systému](../modeling/media/layer_integrated_dnlucerne.png)

 **Diagram závislostí pro večeři nyní integrované s Lucerne**

 Vrstvy v tomto diagramu odkaz na odpovídající večeři nyní a Lucerne řešení artefakty. Například obchodní vrstva odkazy na DinnerNow.Business obor názvů a jeho členy, které nyní zahrnují PaymentApprover třídy. Vrstva Access prostředků odkazuje na obor názvů DinnerNow.Data. Šipky nebo *závislosti*určují, že funkci ve vrstvě Přístup u prostředků může používat pouze obchodní vrstva. Jak týmy aktualizují svůj kód, ověřování vrstev se provádí pravidelně zachytit konflikty, jak k nim dochází, a pomoci týmům je rychle vyřešit.

 Týmy spolupracují na postupné integraci a testování obou systémů. Nejprve se ujistěte, že PaymentApprover a zbytek večeři nyní úspěšně pracovat s sebou před tím, než se zabývají PaymentProcessing.

 Následující mapa kódu zobrazuje nová volání mezi večeří nyní a PaymentApprover:

 ![Aktualizovaný graf závislostí s integrovaným systémem](../modeling/media/depgraph_intsystem.png)

 **Mapa kódu s aktualizovanými voláními metod**

 Poté, co potvrdí, že systém funguje podle očekávání, večeři nyní komentáře z PaymentProcessing kód. Sestavy ověření vrstvy jsou čisté a výsledné mapování kódu ukazuje, že neexistují žádné další závislosti PaymentProcessing:

 ![Graf závislostí bez zpracování platby](../modeling/media/depgraph_nomore.png)

 **Mapa kódu bez zpracování platby**

#### <a name="drawing-a-dependency-diagram"></a>Kreslení diagramu závislostí

Diagram závislostí má následující hlavní funkce:

- *Vrstvy* popisují logické skupiny artefaktů.

- *Propojení* je přidružení mezi vrstvou a artefaktem.

     Chcete-li vytvořit vrstvy z artefaktů, přetáhněte položky z Průzkumníka řešení, map kódu, zobrazení tříd nebo prohlížeče objektů. Chcete-li nakreslit nové vrstvy a pak je propojit s artefakty, použijte panel nástrojů nebo klepněte pravým tlačítkem myši na povrch diagramu a vytvořte vrstvy a pak položky přetáhněte do těchto vrstev.

     Číslo ve vrstvě zobrazuje počet artefaktů, které jsou propojeny s vrstvou. Tyto artefakty mohou být obory názvů, projekty, třídy, metody a tak dále. Při interpretaci počtu artefaktů ve vrstvě si pamatujte následující:

  - Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.

       Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.

  - Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.

    Pokud chcete zobrazit artefakty, které jsou propojeny s vrstvou, klikněte pravým tlačítkem myši na závislost a potom klepnutím na **Zobrazit odkazy** otevřete **Průzkumníka vrstev**.

- *Závislost* označuje, že jedna vrstva může používat funkce v jiné vrstvě, ale ne naopak. *Obousměrná závislost* označuje, že jedna vrstva může používat funkce v jiné vrstvě a naopak.

     Chcete-li zobrazit existující závislosti v diagramu závislostí, klepněte pravým tlačítkem myši na povrch diagramu a potom klepněte na příkaz **Generovat závislosti**. Chcete-li popsat zamýšlené závislosti, nakreslete nové.

Přečtěte si:

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)

- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)

- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Shrnutí: Silné diagramy závislostí

Diagramy závislostí vám pomohou:

- Popište logickou architekturu systému podle funkčnosti jeho artefaktů.

- Ujistěte se, že kód ve vývoji odpovídá zadanému návrhu.

#### <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům

|**Diagram**|**Popis**|
|-|-|
|Mapa kódu|Vizualizujte organizaci a vztahy v existujícím kódu.<br /><br /> Chcete-li vytvořit vrstvy, vygenerujte mapu kódu a pak seskupte položky na mapě jako potenciální vrstvy. Přetáhněte skupiny z mapy do diagramu závislostí.<br /><br /> Přečtěte si:<br /><br /> - [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|-|-|
|**Fóra**|- [Nástroje pro vizualizaci & visual studia Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visualization Visualization & Modelování SDK (NÁSTROJE DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Viz také

- [Vizualizace kódu](../modeling/visualize-code.md)
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
- [Použití modelů v agilním vývoji](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Ověřování systému během vývoje](../modeling/validate-your-system-during-development.md)
