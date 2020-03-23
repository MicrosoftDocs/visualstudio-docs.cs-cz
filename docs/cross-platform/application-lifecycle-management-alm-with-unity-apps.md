---
title: Správa životního cyklu aplikací (ALM) s aplikacemi Unity | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272273"
---
# <a name="devops-with-unity-apps"></a>DevOps s aplikacemi Unity

Vývoj aplikací pro moderní platformy zahrnuje mnohem více aktivit než jen psaní kódu. Tyto aktivity, označované jako DevOps (vývoj + operace), pokrývají celý životní cyklus aplikace a zahrnují plánování a sledování práce, navrhování a implementaci kódu, správu úložiště zdrojového kódu, spouštění sestavení, správu průběžných integrací a nasazení, testování (včetně testů částí a testů uživatelského rozhraní), spuštění různých forem diagnostiky ve vývojovém i produkčním prostředí a monitorování výkonu aplikací a chování uživatelů v reálném čase prostřednictvím telemetrie a analýzy.

Visual Studio spolu se službami Azure DevOps Services a Team Foundation Server poskytuje celou řadu funkcí DevOps. Mnohé z nich jsou použitelné pro projekty napříč platformami, včetně&mdash;her a pohlcující grafické aplikace vytvořené s Unity, zejména při použití Jazyka C# jako skriptovacího jazyka. Protože však Unity má své vlastní vývojové prostředí a modul runtime, řada funkcí DevOps se nepoužije stejně jako u jiných druhů projektů vytvořených v sadě Visual Studio.

Následující tabulky určují, jak se funkce DevOps v sadě Visual Studio aplikují nebo neplatí při práci s Unity. Podrobnosti o samotných funkcích naleznete v propojené dokumentaci.

## <a name="agile-tools"></a>Agilní nástroje

Odkaz: [O agilních nástrojích a agilním řízení projektů](/azure/devops/boards/backlogs/backlogs-overview?view=vsts) (pomocí Azure Boards nebo TFS, včetně Průzkumníka celého týmu)

Obecný komentář: všechny funkce plánování a sledování jsou nezávislé na typu projektu a kódovacích jazycích.

|Funkce|Podporováno pomocí unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Správa nevyřízených položek a sprintů|Ano||
|Sledování práce|Ano||
|Spolupráce v týmové místnosti|Ano||
|Kanbandesky|Ano||
|Hlášení a vizualizace průběhu|Ano||

## <a name="modeling"></a>Modelování

Referenční odkaz: ** [Analýza a architektura modelu](../modeling/analyze-and-model-your-architecture.md)**

Obecný komentář: Přestože tyto funkce návrhu jsou nezávislé na jazyku kódování nebo pracovat s jazyky .NET, jako je C#, pracují na tradiční aplikační paradigma s hierarchiemi objektů a vztahy tříd. Navrhování hry v unity zahrnuje úplně jiné paradigma, a to vztahy grafických objektů, zvuků, shaderů, skriptů a tak dále. Z tohoto důvodu nástroje diagramu modelování sady Visual Studio nejsou zvláště důležité pro celý projekt Unity. Mohou být případně použity ke správě vztahů v rámci skriptů jazyka C#, ale to je pouze jedna část celku.

|Funkce|Podporováno pomocí unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Sekvenční diagramy|Ne||
|Grafy závislostí|Ne||
|Hierarchie volání|Ne||
|Návrhář třídy|Ne||
|Průzkumník architektury|Ne||
|UML diagramy (případ použití, aktivita, třída, komponenta, sekvence a DSL)|Ne||
|Diagramy vrstev|Ne||
|Ověření vrstvy|Ne||

## <a name="code"></a>kód

|Funkce|Podporováno pomocí unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|[Použití správy verzí Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) nebo Azure Repos|Ano|Unity projekty jsou jednoduše kolekce souborů, které lze umístit do systémů správy verzí jako jakýkoli jiný projekt, ale existuje několik zvláštních aspekty popsané po této tabulce.|
|[Začínáme s Gitem v Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Ano|Viz poznámky za stolem.|
|[Zlepšení kvality kódu](../test/improve-code-quality.md)|Ano||
|[Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)|Ano||
|[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)|Ano||

Zvláštní aspekty pro správu verzí s Unity:

1. Unity sleduje metadata o herních datových zdrojích v jedné neprůhledné knihovně, která je ve výchozím nastavení skrytá. Chcete-li zachovat soubory a metadata v synchronizaci, je nutné, aby metadata viditelné a uložit je do více spravovatelné bloky dat. Podrobnosti naleznete [v části Použití externích systémů správy verzí s unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity dokumentace).

2. Ne všechny soubory a složky v projektu Unity jsou vhodné pro složky zdrojového kódu, jak je také popsáno v odkazu výše. Složky Assets a ProjectSettings by měly být přidány, ale složky Knihovna a Temp by neměly. Další seznam generovaných souborů, které by nepřešely do správy zdrojového kódu, najdete v diskusi [Jak používat Git pro ovládací prvek zdroj Unity3D?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na StackOverflow. Mnoho vývojářů také blogged na toto téma nezávisle.

3. Binární datové zdroje v projektu Unity – například textury nebo zvukové soubory – mohou zabírají velké množství úložiště. Různé systémy správy zdrojového kódu, jako je Git, ukládají jedinečnou kopii souboru pro každou provedenou změnu, i když změna ovlivní pouze malou část souboru. To může způsobit, že úložiště Git bude nafouklé. K řešení tohoto problému se vývojáři Unity často rozhodnou přidat do svého úložiště pouze konečné prostředky a používat jiný způsob udržování pracovní historie svých prostředků, jako je Například OneDrive, DropBox nebo git-annex. Tento přístup funguje, protože tyto prostředky obvykle není nutné verzí spolu se změnami zdrojového kódu. Vývojáři také obvykle nastavit editoru projektu Serializace režimu vynutit text ukládat soubory scény v textu, nikoli binární formát, který umožňuje sloučení ve správě zdrojového kódu. Podrobnosti naleznete v [tématu Nastavení editoru](https://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentace Unity).

## <a name="build"></a>Sestavení

Referenční odkaz: ** [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)**

|Funkce|Podporováno pomocí unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Místní server Team Foundation (TFS)|Možné|Unity projekty jsou vytvořeny prostřednictvím prostředí Unity a nikoli prostřednictvím systému sestavení sady Visual Studio (sestavení v rámci Visual Studio Tools for Unity bude kompilovat skripty, ale nevytváří spustitelný soubor). Je možné [sestavit unity projekty z příkazového řádku](https://docs.unity3d.com/Manual/CommandLineArguments.html) (Unity dokumentace), takže je možné nakonfigurovat proces MSBuild na serveru TFS ke spuštění příslušné unity příkazy, za předpokladu, že Unity sám je nainstalován v tomto počítači.<br /><br /> Unity také nabízí [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), který monitoruje úložiště Git nebo SVN a spouští periodická sestavení. V současné době nefunguje s TFVC nebo Azure DevOps Services.|
|Místní server sestavení propojený se službami Azure DevOps Services|Možné|Za stejných podmínek jako výše je dále možné přímé sestavení aktivované prostřednictvím služby Azure DevOps Services používat místní počítač TFS. Pokyny najdete [v tématu Sestavení a uvolnění agentů.](/azure/devops/pipelines/agents/agents?view=vsts)|
|Hostovaná služba řadiče služby Azure DevOps Services|Ne|Unity sestavení nejsou v současné době podporovány.|
|Vytváření definic pomocí předa postskriptů|Ano|Vlastní definice sestavení, která používá příkazový řádek Unity ke spuštění sestavení lze také nakonfigurovat pro skripty před a po sestavení.|
|Průběžná integrace včetně gated check-inů|Ano|Gated vrácení se změnami pro TFVC pouze jako Git pracuje na modelu žádosti o přijetí návladní, spíše než vrácení se změnami.|

## <a name="test"></a>Test

|Funkce|Podporováno pomocí unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Plánování testů, vytváření testovacích případů a uspořádání testovacích sad|Ano||
|Ruční testování|Ano||
|Správce testů (testy záznamu a přehrávání)|Pouze zařízení s Windows a emulátory Androidu||
|Pokrytí kódu|neuvedeno|Není použitelné jako testování částí se stane v unity a ne Visual Studio, viz níže.|
|[Testování částí kódu](../test/unit-test-your-code.md)|V rámci unity, ale ne Visual Studio|Unity poskytuje vlastní rozhraní testování částí jako součást [nástroje Unity test](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity Asset Store). Výsledky testování částí jsou hlášeny v unity a nebudou se zobrazí v rámci sady Visual Studio.|
|[Testování kódu pomocí automatizace uživatelského rozhraní](../test/use-ui-automation-to-test-your-code.md)|Ne|Programové testy ui spoléhají na čitelné ovládací prvky v rozhraní ui aplikace; Unity aplikace mají grafickou povahu, a proto obsah není čitelný pomocí programové nástroje pro testování uživatelského prostředí.|

## <a name="improve-code-quality"></a>Zlepšení kvality kódu

Odkaz odkaz: ** [Zlepšení kvality kódu](../test/improve-code-quality.md)**

|Funkce|Podporováno pomocí unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|[Analýza kvality spravovaného kódu](../code-quality/code-analysis-for-managed-code-overview.md)|Ano|Můžete analyzovat kód skriptu C# v rámci sady Visual Studio.|
|[Vyhledání duplicitního kódu pomocí detekce klonování kódu](https://msdn.microsoft.com/library/hh205279.aspx)|Ano|Můžete analyzovat kód skriptu C# v rámci sady Visual Studio.|
|[Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/code-metrics-values.md)|Ano|Můžete analyzovat kód skriptu C# v rámci sady Visual Studio.|
|[Nástroje pro měření výkonu](../profiling/performance-explorer.md)|Ne|Použijte [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html) (Unity webové stránky).|
|[Analýza problémů s pamětí rozhraní .NET Framework](https://msdn.microsoft.com/library/dn342825.aspx)|Ne|Visual Studio nástroje nemají háčky do mono rozhraní (jak je používá Unity) pro profilování. Použijte [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity dokumentace).|

## <a name="release-management"></a>Správa vydaných verzí

Odkaz na odkaz: [Sestavení a vydání v Azure Pipelines a TFS](/azure/devops/pipelines/overview?view=vsts)

|Funkce|Podporováno pomocí unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Správa procesů vydání|Ano||
|Nasazení na servery pro boční načítání pomocí skriptů|Ano||
|Nahrání do obchodu s aplikacemi|Částečné|K dispozici jsou rozšíření, která mohou tento proces automatizovat pro některé obchody s aplikacemi. Viz [Rozšíření pro služby Azure DevOps](https://marketplace.visualstudio.com/VSTS); například [rozšíření pro Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitor s Aplikací HockeyApp

Referenční odkaz: ** [Monitor s HockeyApp](https://www.hockeyapp.net/features/)**

|Funkce|Podporováno pomocí unity|Další komentáře|
|-------------|--------------------------|-------------------------|
|Crash analytics, telemetrie a distribuce beta verze|Ano|HockeyApp je primárně užitečný pro zpracování distribuce beta verzí a získávání zpráv o selhání.<br /><br /> Pro telemetrii ze skriptů jazyka C# je možné použít libovolný analytický rámec za předpokladu, že je spuštěn na verzi rozhraní .NET, kterou používá Unity. To však umožňuje analýzy pouze v rámci hernískripty a ne hlouběji uvnitř unity motoru. V současné době neexistuje žádný plugin pro Application Insights, ale pluginy jsou k dispozici pro další analytická řešení, jako je [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) a [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Služby jako Unity Analytics, které chápou povahu projektu Unity, budou samozřejmě poskytovat mnohem smysluplnější analýzu než obecné rámce.|
