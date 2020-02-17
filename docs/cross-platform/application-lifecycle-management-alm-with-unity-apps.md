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
ms.openlocfilehash: 5a1c449a77e3000205ee81f5414949743b6035c4
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272273"
---
# <a name="devops-with-unity-apps"></a>DevOps s aplikacemi Unity

Vývoj aplikací pro moderní platformy zahrnuje mnoho dalších aktivit než jenom psaní kódu. Tyto aktivity, označované jako DevOps (vývoj a operace), zahrnují celý životní cyklus aplikace a zahrnují plánování a sledování práce, návrh a implementaci kódu, správu úložiště zdrojového kódu, spouštění sestavení a správu průběžných integrací. a nasazení, testování (včetně testů jednotek a testů uživatelského rozhraní), spouštění různých forem diagnostiky ve vývojovém i produkčním prostředí a monitorování výkonu aplikací a chování uživatelů v reálném čase prostřednictvím telemetrie a analýz.

Visual Studio společně s Azure DevOps Services a Team Foundation Server poskytuje celou řadu funkcí DevOps. Mnohé z nich se vztahují na projekty pro různé platformy, včetně her a moderních grafických aplikací vytvořených pomocí Unity&mdash;obzvláště při použití C# jako skriptovací jazyk. Vzhledem k tomu, že Unity má své vlastní vývojové prostředí a modul modulu runtime, není množství DevOpsch funkcí použito, protože by to bylo pro jiné druhy projektů sestavené v aplikaci Visual Studio.

Následující tabulky popisují, jak se DevOps funkce v aplikaci Visual Studio používají nebo nepoužívají při práci s Unity. Podrobnosti o samotných funkcích najdete v odkazované dokumentaci.

## <a name="agile-tools"></a>Agilní nástroje

Referenční odkaz: [informace o agilních nástrojích a agilním řízení projektů](/azure/devops/boards/backlogs/backlogs-overview?view=vsts) (pomocí Azure boards nebo TFS, včetně Team Explorer Everywhere)

Obecný komentář: všechny funkce plánování a sledování jsou nezávislé na typu projektu a jazycích kódování.

|Funkce|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Správa nevyřízených položek a sprintů|Ano||
|Sledování práce|Ano||
|Spolupráce v týmové místnosti|Ano||
|Kanbanové desky|Ano||
|Sestavování a vizualizace průběhu|Ano||

## <a name="modeling"></a>Modelování

Referenční odkaz:  **[Analýza a architektura modelu](../modeling/analyze-and-model-your-architecture.md)**

Obecný komentář: i když tyto funkce návrhu jsou nezávislé na jazyku kódování nebo pracují s jazyky .NET, C#jako jsou, pracují s tradičními paradigma aplikace s hierarchiemi objektů a vztahy tříd. Návrh hry v rámci Unity zahrnuje zcela jiné paradigma, konkrétně vztahy grafických objektů, zvuků, shaderů, skriptů a tak dále. Z tohoto důvodu nástroje diagramu modelování sady Visual Studio nejsou obzvláště důležité pro celý projekt Unity. Je možné je použít ke správě relací v rámci C# skriptů, ale je to jenom jedna část celého.

|Funkce|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Sekvenční diagramy|Ne||
|Grafy závislostí|Ne||
|Hierarchie volání|Ne||
|Návrhář tříd|Ne||
|Průzkumník architektury|Ne||
|Diagramy UML (případ použití, aktivita, třída, komponenta, sekvence a DSL)|Ne||
|Diagramy vrstev|Ne||
|Ověření vrstvy|Ne||

## <a name="code"></a>Kód

|Funkce|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|[Použít Správa verzí Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) nebo Azure Repos|Ano|Projekty Unity jsou jednoduše kolekcí souborů, které lze umístit do systémů správy verzí, jako je jakýkoli jiný projekt, ale existuje několik zvláštních doporučení popsaných po této tabulce.|
|[Začínáme s Git v Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Ano|Viz poznámky za tabulkou.|
|[Zlepšení kvality kódu](../test/improve-code-quality.md)|Ano||
|[Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)|Ano||
|[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)|Ano||

Zvláštní požadavky na správu verzí s Unity:

1. Unity sleduje metadata o herních prostředcích v jediné neprůhledné knihovně, která je ve výchozím nastavení skrytá. Aby se soubory a metadata udržovaly synchronizované, je nutné, aby se metadata zobrazovala a ukládala v blocích s více spravovatelnými. Podrobnosti najdete v tématu [použití externích systémů správy verzí s Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentace k Unity).

2. Ne všechny soubory a složky v projektu Unity jsou vhodné pro správu zdrojového kódu, jak je popsáno dále v odkazu. Měly by se přidat složky assets a ProjectSettings, ale knihovna a dočasné složky by se neměly. Další seznam generovaných souborů, které nepatří do správy zdrojového kódu, naleznete v tématu diskuze [o použití Gitu pro správu zdrojového kódu Unity3D?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) v StackOverflow. Mnoho vývojářů se také blogged na tento subjekt nezávisle.

3. Binární prostředky v projektu Unity, jako jsou textury nebo zvukové soubory, můžou zabrat velký objem úložiště. Různé systémy správy zdrojového kódu, jako je git, ukládají jedinečnou kopii souboru pro každou změnu, která se provedla, a to i v případě, že změna ovlivní jenom malou část souboru. To může způsobit, že se úložiště Git stane bloated. V takovém případě se vývojáři Unity často rozhodnou přidat do svého úložiště pouze konečné prostředky a použít jiný způsob uchování pracovní historie jejich prostředků, jako je OneDrive, DropBox nebo Git-příloha. Tento přístup funguje, protože tyto prostředky obvykle nemusí být ve verzi společně se změnami zdrojového kódu. Vývojáři také obvykle nastavují režim serializace Asset Editor projektu, aby vynutila ukládání souborů scény v textu, nikoli v binárním formátu, který umožňuje sloučení ve správě zdrojového kódu. Podrobnosti najdete v tématu [nastavení editoru](https://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentace Unity).

## <a name="build"></a>Sestavení

Odkaz na odkaz:  **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts)**

|Funkce|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Místní Team Foundation Server (TFS)|Provést|Projekty Unity se vytvářejí prostřednictvím prostředí Unity, a ne prostřednictvím systému sestavení sady Visual Studio (sestavení v rámci Visual Studio Tools for Unity zkompiluje skripty, ale nevytvoří spustitelný soubor). Projekty Unity je možné [vytvořit z příkazového řádku](https://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentace Unity), takže je možné nakonfigurovat proces MSBuild na serveru TFS, aby prováděl příslušné příkazy Unity za předpokladu, že je v tomto počítači nainstalovaná jednota Unity.<br /><br /> Unity taky nabízí [cloudové sestavení Unity](https://build.cloud.unity3d.com/landing/), které monitoruje úložiště Git nebo SVN a spouští pravidelná sestavení. V současné době nefunguje s TFVC nebo Azure DevOps Services.|
|Místní sestavovací Server propojený s Azure DevOps Services|Provést|Vzhledem k tomu, že jsou uvedené stejné podmínky jako výše, je dále možné směrovat sestavení aktivované prostřednictvím Azure DevOps Services pro použití místního počítače TFS. Pokyny najdete v tématu [agenti sestavení a vydání](/azure/devops/pipelines/agents/agents?view=vsts) .|
|Služba hostovaného kontroleru služby Azure DevOps Services|Ne|Sestavení Unity se v současnosti nepodporují.|
|Definice buildu s využitím předzálohovacích skriptů|Ano|Vlastní definice sestavení, která používá příkazový řádek Unity pro spuštění sestavení, se dá nakonfigurovat taky pro skripty spouštěné předem a po sestavení.|
|Průběžná integrace včetně ověřovaných vrácení se změnami|Ano|Ověřované vrácení se změnami pro TFVC jenom v případě, že Git funguje na modelu žádosti o přijetí změn, a ne vrácení se změnami.|

## <a name="test"></a>Test

|Funkce|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Plánování testů, vytváření testovacích případů a organizování testovacích sad|Ano||
|Manuální testování|Ano||
|Test Manager (testy záznamů a přehrávání)|Jenom zařízení s Windows a emulátory pro Android||
|Pokrytí kódu|neuvedeno|Nedá se použít jako testování částí v Unity a ne v sadě Visual Studio, viz níže.|
|[Testování částí kódu](../test/unit-test-your-code.md)|V Unity, ale ne v sadě Visual Studio|Unity poskytuje vlastní testovací architekturu jednotek jako součást [testovacích nástrojů Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (úložiště assetů Unity). Výsledky testování částí jsou hlášeny v rámci Unity a nebudou se v sadě Visual Studio rozplochy.|
|[Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)|Ne|Programové testy uživatelského rozhraní spoléhají na čitelné ovládací prvky v uživatelském rozhraní aplikace. Aplikace Unity jsou grafické, takže obsah není čitelný pomocí nástrojů programového testu uživatelského rozhraní.|

## <a name="improve-code-quality"></a>Zlepšení kvality kódu

Odkaz na odkaz:  **[vylepšení kvality kódu](../test/improve-code-quality.md)**

|Funkce|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|[Analýza kvality spravovaného kódu](../code-quality/code-analysis-for-managed-code-overview.md)|Ano|Může analyzovat kód C# skriptu v sadě Visual Studio.|
|[Hledání duplicitního kódu pomocí zjišťování klonování kódu](https://msdn.microsoft.com/library/hh205279.aspx)|Ano|Může analyzovat kód C# skriptu v sadě Visual Studio.|
|[Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/code-metrics-values.md)|Ano|Může analyzovat kód C# skriptu v sadě Visual Studio.|
|[Nástroje pro sledování výkonu](../profiling/performance-explorer.md)|Ne|Používejte [Profiler Unity](https://docs.unity3d.com/Manual/Profiler.html) (Web Unity).|
|[Analýza problémů s .NET Framework paměti](https://msdn.microsoft.com/library/dn342825.aspx)|Ne|Nástroje sady Visual Studio se nepřipojily k rozhraní Mono (jak je používáno v Unity) k profilaci. Použijte [Profiler Unity](http://docs.unity3d.com/Manual/Profiler.html) (dokumentace Unity).|

## <a name="release-management"></a>Správa vydaných verzí

Odkaz na odkaz: [sestavení a vydání v Azure Pipelines a TFS](/azure/devops/pipelines/overview?view=vsts)

|Funkce|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Správa procesů vydaných verzí|Ano||
|Nasazení na servery pro souběžné načítání prostřednictvím skriptů|Ano||
|Nahrát do App Storu|Částečně|K dispozici jsou rozšíření, která mohou tento proces automatizovat pro některé obchody s aplikacemi. Viz [rozšíření pro Azure DevOps Services](https://marketplace.visualstudio.com/VSTS); například [rozšíření pro Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorování pomocí HockeyApp

Odkaz odkaz:  **[monitorování pomocí HockeyApp](https://www.hockeyapp.net/features/)**

|Funkce|Podporováno s Unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Analýza selhání, telemetrie a distribuce beta verzí|Ano|HockeyApp je primárně užitečná pro zpracování distribuce beta verzí a získání hlášení o chybách.<br /><br /> Pro telemetrii ze C# skriptů je možné použít jakékoli analytické rozhraní, které je k dispozici ve verzi rozhraní .NET, kterou používá Unity. To ale umožňuje analýzám jenom v rámci herních skriptů a ne i v jádru Unity. V současné době není k dispozici žádný modul plug-in pro Application Insights, ale moduly plug-in jsou k dispozici pro jiná analytická [řešení, jako](https://github.com/googleanalytics/google-analytics-plugin-for-unity)je třeba [Analýza Unity](https://www.assetstore.unity3d.com/en/#!/content/28120) Služby, jako je analýza Unity, které rozumí povaze projektu Unity, samozřejmě poskytují mnohem smysluplnější analýzu než obecná rozhraní.|
