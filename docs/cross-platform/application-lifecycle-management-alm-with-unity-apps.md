---
title: Správa životního cyklu aplikací (ALM) s aplikacemi Unity | Microsoft Docs
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 7b4c4dfdb8e603d7dda2ebd55c4382e57414de25
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928027"
---
# <a name="devops-with-unity-apps"></a>DevOps s aplikacemi Unity

Vývoj aplikací pro moderní platformy zahrnuje mnoho dalších aktivit než jenom psaní kódu. Tyto aktivity, označované jako DevOps (vývoj a operace), využijte celý životní cyklus aplikace a zahrňte plánování a sledování práce, návrh a implementaci kódu, správu úložiště zdrojového kódu, spouštění sestavení, správu průběžných integrací a nasazení, testování (včetně jednotkových testů a testů uživatelského rozhraní), spouštění různých forem diagnostiky ve vývojovém i produkčním prostředí a monitorování výkonu aplikací a chování uživatelů v reálném čase prostřednictvím telemetrie a analýz.

Visual Studio společně s Azure DevOps Services a Team Foundation Server poskytuje celou řadu funkcí DevOps. Mnohé z nich se vztahují na projekty pro různé platformy, včetně her a moderních grafických aplikací vytvořených pomocí Unity, &mdash; zejména při použití jazyka C# jako skriptovacího jazyka. Vzhledem k tomu, že Unity má své vlastní vývojové prostředí a modul modulu runtime, není množství DevOpsch funkcí použito, protože by to bylo pro jiné druhy projektů sestavené v aplikaci Visual Studio.

Následující tabulky popisují, jak se DevOps funkce v aplikaci Visual Studio používají nebo nepoužívají při práci s Unity. Podrobnosti o samotných funkcích najdete v odkazované dokumentaci.

## <a name="agile-tools"></a>Agilní nástroje

Referenční odkaz: [informace o agilních nástrojích a agilním řízení projektů](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true) (pomocí Azure boards nebo TFS, včetně Team Explorer Everywhere)

Obecný komentář: všechny funkce plánování a sledování jsou nezávislé na typu projektu a jazycích kódování.

|Příznak|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Správa nevyřízených položek a sprintů|Yes||
|Sledování práce|Yes||
|Spolupráce v týmové místnosti|Yes||
|Kanbanové desky|Yes||
|Sestavování a vizualizace průběhu|Yes||

## <a name="modeling"></a>Modelování

Referenční odkaz: ** [Analýza a architektura modelu](../modeling/analyze-and-model-your-architecture.md)**

Obecný komentář: i když tyto funkce návrhu jsou nezávislé na jazyku kódování nebo pracují s jazyky .NET, jako je C#, pracují na tradičním paradigmatu aplikace s hierarchiemi objektů a vztahy tříd. Návrh hry v rámci Unity zahrnuje zcela jiné paradigma, konkrétně vztahy grafických objektů, zvuků, shaderů, skriptů a tak dále. Z tohoto důvodu nástroje diagramu modelování sady Visual Studio nejsou obzvláště důležité pro celý projekt Unity. Mohly by být použity ke správě vztahů v rámci skriptů jazyka C#, ale je to pouze jedna část celého.

|Příznak|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Sekvenční diagramy|No||
|Grafy závislostí|No||
|Hierarchie volání|No||
|Návrhář tříd|No||
|Průzkumník architektury|No||
|Diagramy UML (případ použití, aktivita, třída, komponenta, sekvence a DSL)|No||
|Diagramy vrstev|No||
|Ověření vrstvy|No||

## <a name="code"></a>Kód

|Příznak|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|[Použít Správa verzí Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true) nebo Azure Repos|Yes|Projekty Unity jsou jednoduše kolekcí souborů, které lze umístit do systémů správy verzí, jako je jakýkoli jiný projekt, ale existuje několik zvláštních doporučení popsaných po této tabulce.|
|[Začínáme s Git v Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio&preserve-view=true)|Yes|Viz poznámky za tabulkou.|
|[Zlepšení kvality kódu](../test/improve-code-quality.md)|Yes||
|[Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)|Yes||
|[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)|Yes||

Zvláštní požadavky na správu verzí s Unity:

1. Unity sleduje metadata o herních prostředcích v jediné neprůhledné knihovně, která je ve výchozím nastavení skrytá. Aby se soubory a metadata udržovaly synchronizované, je nutné, aby se metadata zobrazovala a ukládala v blocích s více spravovatelnými. Podrobnosti najdete v tématu [použití externích systémů správy verzí s Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentace k Unity).

2. Ne všechny soubory a složky v projektu Unity jsou vhodné pro správu zdrojového kódu, jak je popsáno dále v odkazu. Měly by se přidat složky assets a ProjectSettings, ale knihovna a dočasné složky by se neměly. Další seznam generovaných souborů, které nepatří do správy zdrojového kódu, naleznete v tématu diskuze [o použití Gitu pro správu zdrojového kódu Unity3D?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) v StackOverflow. Mnoho vývojářů se také blogged na tento subjekt nezávisle.

3. Binární prostředky v projektu Unity, jako jsou textury nebo zvukové soubory, můžou zabrat velký objem úložiště. Různé systémy správy zdrojového kódu, jako je git, ukládají jedinečnou kopii souboru pro každou změnu, která se provedla, a to i v případě, že změna ovlivní jenom malou část souboru. To může způsobit, že se úložiště Git stane bloated. V takovém případě se vývojáři Unity často rozhodnou přidat do svého úložiště pouze konečné prostředky a použít jiný způsob uchování pracovní historie jejich prostředků, jako je OneDrive, DropBox nebo Git-příloha. Tento přístup funguje, protože tyto prostředky obvykle nemusí být ve verzi společně se změnami zdrojového kódu. Vývojáři také obvykle nastavují režim serializace Asset Editor projektu, aby vynutila ukládání souborů scény v textu, nikoli v binárním formátu, který umožňuje sloučení ve správě zdrojového kódu. Podrobnosti najdete v tématu [nastavení editoru](https://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentace Unity).

## <a name="build"></a>Sestavení

Odkaz na odkaz: ** [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)**

|Příznak|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Místní Team Foundation Server (TFS)|Provést|Projekty Unity se vytvářejí prostřednictvím prostředí Unity, a ne prostřednictvím systému sestavení sady Visual Studio (sestavení v rámci Visual Studio Tools for Unity zkompiluje skripty, ale nevytvoří spustitelný soubor). Projekty Unity je možné [vytvořit z příkazového řádku](https://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentace Unity), takže je možné nakonfigurovat proces MSBuild na serveru TFS, aby prováděl příslušné příkazy Unity za předpokladu, že je v tomto počítači nainstalovaná jednota Unity.<br /><br /> Unity taky nabízí [cloudové sestavení Unity](https://build.cloud.unity3d.com/landing/), které monitoruje úložiště Git nebo SVN a spouští pravidelná sestavení. V současné době nefunguje s TFVC nebo Azure DevOps Services.|
|Místní sestavovací Server propojený s Azure DevOps Services|Provést|Vzhledem k tomu, že jsou uvedené stejné podmínky jako výše, je dále možné směrovat sestavení aktivované prostřednictvím Azure DevOps Services pro použití místního počítače TFS. Pokyny najdete v tématu [agenti sestavení a vydání](/azure/devops/pipelines/agents/agents?view=vsts&preserve-view=true) .|
|Služba hostovaného kontroleru služby Azure DevOps Services|No|Sestavení Unity se v současnosti nepodporují.|
|Definice buildu s využitím předzálohovacích skriptů|Yes|Vlastní definice sestavení, která používá příkazový řádek Unity pro spuštění sestavení, se dá nakonfigurovat taky pro skripty spouštěné předem a po sestavení.|
|Průběžná integrace včetně ověřovaných vrácení se změnami|Yes|Ověřované vrácení se změnami pro TFVC jenom v případě, že Git funguje na modelu žádosti o přijetí změn, a ne vrácení se změnami.|

## <a name="test"></a>Test

|Příznak|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Plánování testů, vytváření testovacích případů a organizování testovacích sad|Yes||
|Manuální testování|Yes||
|Test Manager (testy záznamů a přehrávání)|Jenom zařízení s Windows a emulátory pro Android||
|Pokrytí kódu|neuvedeno|Nedá se použít jako testování částí v Unity a ne v sadě Visual Studio, viz níže.|
|[Testování částí kódu](../test/unit-test-your-code.md)|V Unity, ale ne v sadě Visual Studio|Unity poskytuje vlastní testovací architekturu jednotek jako součást [testovacích nástrojů Unity](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (úložiště assetů Unity). Výsledky testování částí jsou hlášeny v rámci Unity a nebudou se v sadě Visual Studio rozplochy.|
|[Použití automatizace uživatelského rozhraní k otestování kódu](../test/use-ui-automation-to-test-your-code.md)|No|Programové testy uživatelského rozhraní spoléhají na čitelné ovládací prvky v uživatelském rozhraní aplikace. Aplikace Unity jsou grafické, takže obsah není čitelný pomocí nástrojů programového testu uživatelského rozhraní.|

## <a name="improve-code-quality"></a>Zlepšení kvality kódu

Odkaz na odkaz: ** [vylepšení kvality kódu](../test/improve-code-quality.md)**

|Příznak|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|[Analýza kvality spravovaného kódu](../code-quality/code-analysis-for-managed-code-overview.md)|Yes|Může analyzovat kód skriptu jazyka C# v sadě Visual Studio.|
|[Hledání duplicitního kódu pomocí zjišťování klonování kódu](/previous-versions/hh205279(v=vs.140))|Yes|Může analyzovat kód skriptu jazyka C# v sadě Visual Studio.|
|[Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/code-metrics-values.md)|Yes|Může analyzovat kód skriptu jazyka C# v sadě Visual Studio.|
|[Nástroje pro měření výkonu](../profiling/performance-explorer.md)|No|Používejte [Profiler Unity](https://docs.unity3d.com/Manual/Profiler.html) (Web Unity).|
|[Analýza problémů s pamětí rozhraní .NET Framework](../vs-2015/misc/analyze-dotnet-framework-memory-issues.md)|No|Nástroje sady Visual Studio se nepřipojily k rozhraní Mono (jak je používáno v Unity) k profilaci. Použijte [Profiler Unity](http://docs.unity3d.com/Manual/Profiler.html) (dokumentace Unity).|

## <a name="release-management"></a>Správa vydaných verzí

Odkaz na odkaz: [sestavení a vydání v Azure Pipelines a TFS](/azure/devops/pipelines/overview?view=vsts&preserve-view=true)

|Příznak|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Správa procesů vydaných verzí|Yes||
|Nasazení na servery pro souběžné načítání prostřednictvím skriptů|Yes||
|Nahrát do App Storu|Částečné|K dispozici jsou rozšíření, která mohou tento proces automatizovat pro některé obchody s aplikacemi. Viz [rozšíření pro Azure DevOps Services](https://marketplace.visualstudio.com/VSTS); například [rozšíření pro Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorování pomocí HockeyApp

Odkaz odkaz: ** [monitorování pomocí HockeyApp](https://www.hockeyapp.net/features/)**

|Příznak|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Analýza selhání, telemetrie a distribuce beta verzí|Yes|HockeyApp je primárně užitečná pro zpracování distribuce beta verzí a získání hlášení o chybách.<br /><br /> Pro telemetrii z skriptů jazyka C# je možné použít libovolné analytické rozhraní, které je k dispozici ve verzi rozhraní .NET, kterou používá Unity. To ale umožňuje analýzám jenom v rámci herních skriptů a ne i v jádru Unity. V současné době není k dispozici žádný modul plug-in pro Application Insights, ale moduly plug-in jsou k dispozici pro jiná analytická [řešení, jako](https://github.com/googleanalytics/google-analytics-plugin-for-unity)je třeba [Analýza Unity](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) Služby, jako je analýza Unity, které rozumí povaze projektu Unity, samozřejmě poskytují mnohem smysluplnější analýzu než obecná rozhraní.|