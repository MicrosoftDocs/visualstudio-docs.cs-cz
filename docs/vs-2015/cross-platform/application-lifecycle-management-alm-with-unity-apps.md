---
title: Správa životního cyklu aplikací (ALM) s aplikacemi Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 90efd4e72ea172822e0bcc424bdbbc4bc7589098
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80233282"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Application Lifecycle Management (ALM) s aplikacemi Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vývoj aplikací pro moderní platformy zahrnuje mnoho dalších aktivit než jenom psaní kódu. Tyto aktivity, označované jako DevOps (vývoj a operace), zahrnují úplný životní cyklus aplikace a zahrnují plánování a sledování práce, návrh a implementace kódu, Správa úložiště zdrojového kódu, spouštění sestavení, Správa průběžných integrací a nasazení, testování (včetně testů jednotek a testů uživatelského rozhraní), spouštění různých forem diagnostiky ve vývojovém i produkčním prostředí a monitorování výkonu aplikací a chování uživatelů v reálném čase prostřednictvím telemetrie a analýz.  
  
 Visual Studio společně s Visual Studio Team Services a Team Foundation Server poskytují celou řadu funkcí DevOps, označovaných také jako správa životního cyklu aplikací nebo ALM. Mnohé z nich platí pro projekty pro různé platformy, včetně her a moderních grafických aplikací vytvořených pomocí Unity – zejména při použití C# jako skriptovacího jazyka. Vzhledem k tomu, že Unity má své vlastní vývojové prostředí a modul modulu runtime, není množství ALMch funkcí použito, protože by to bylo pro jiné druhy projektů sestavené v aplikaci Visual Studio.  
  
 Níže uvedené tabulky určují, jak se ALM funkce sady Visual Studio použijí nebo nepoužívají při práci s Unity. Podrobnosti o samotných funkcích najdete v odkazované dokumentaci.  
  
## <a name="agile-tools"></a>Agilní nástroje  
 Odkaz na odkaz: **[práce](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (pomocí Visual Studio Team Services nebo TFS, včetně Team Explorer Everywhere)  
  
 Obecný komentář: všechny funkce plánování a sledování jsou nezávislé na typu projektu a jazycích kódování.  
  
|Příznak|Podporováno s Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Správa nevyřízených položek a sprintů|Ano||  
|Sledování práce|Ano||  
|Spolupráce v týmové místnosti|Ano||  
|Kanbanové desky|Ano||  
|Sestavování a vizualizace průběhu|Ano||  
  
## <a name="modeling"></a>Modelování  
 Referenční odkaz: ** [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
 Obecný komentář: i když tyto funkce návrhu jsou nezávislé na jazyku kódování nebo pracují s jazyky .NET, jako je C#, pracují na tradičním paradigmatu aplikace s hierarchiemi objektů a vztahy tříd. Návrh hry v rámci Unity zahrnuje zcela jiné paradigma, konkrétně vztahy grafických objektů, zvuků, shaderů, skriptů a tak dále. Z tohoto důvodu nástroje diagramu modelování sady Visual Studio nejsou obzvláště důležité pro celý projekt Unity. Mohly by být použity ke správě vztahů v rámci skriptů jazyka C#, ale je to pouze jedna část celého.  
  
|Příznak|Podporováno s Unity|Další komentáře|  
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
  
|Příznak|Podporováno s Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|[Použití Správa verzí Team Foundation](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) nebo Visual Studio Team Services|Ano|Projekty Unity jsou jednoduše kolekcí souborů, které lze umístit do systémů správy verzí, jako je jakýkoli jiný projekt, ale existuje několik zvláštních doporučení popsaných po této tabulce.|  
|[Začínáme s Git ve službě Team Services](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Ano|Viz poznámky za tabulkou.|  
|[Analýza kódu/zlepšení kvality kódu (odkazy, navrhované změny atd.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Ano||  
|[Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)|Ano||  
|[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)|Ano||  
  
 Zvláštní požadavky na správu verzí s Unity:  
  
1. Unity sleduje metadata o herních prostředcích v jediné neprůhledné knihovně, která je ve výchozím nastavení skrytá. Aby se soubory a metadata udržovaly synchronizované, je nutné, aby se metadata zobrazovala a ukládala v blocích s více spravovatelnými. Podrobnosti najdete v tématu [použití externích systémů správy verzí s Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentace k Unity).  
  
2. Ne všechny soubory a složky v projektu Unity jsou vhodné pro správu zdrojového kódu, jak je popsáno dále v odkazu. Měly by se přidat složky assets a ProjectSettings, ale knihovna a dočasné složky by se neměly. Další seznam generovaných souborů, které nepatří do správy zdrojového kódu, naleznete v tématu diskuze [o použití Gitu pro správu zdrojového kódu Unity3D?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) v StackOverflow. Mnoho vývojářů se také blogged na tento subjekt nezávisle.  
  
3. Binární prostředky v projektu Unity, jako jsou textury nebo zvukové soubory, můžou zabrat velký objem úložiště. Různé systémy správy zdrojového kódu, jako je git, ukládají jedinečnou kopii souboru pro každou změnu, která se provedla, a to i v případě, že změna ovlivní jenom malou část souboru. To může způsobit, že se úložiště Git stane bloated. V takovém případě se vývojáři Unity často rozhodnou přidat do svého úložiště pouze konečné prostředky a použít jiný způsob uchování pracovní historie jejich prostředků, jako je OneDrive, DropBox nebo Git-příloha. Tento přístup funguje, protože tyto prostředky obvykle nemusí být ve verzi společně se změnami zdrojového kódu. Vývojáři také obvykle nastavují režim serializace Asset Editor projektu, aby vynutila ukládání souborů scény v textu, nikoli v binárním formátu, který umožňuje sloučení ve správě zdrojového kódu. Podrobnosti najdete v tématu [nastavení editoru](https://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentace Unity).  
  
## <a name="build"></a>Sestavení  
 Odkaz na odkaz: ** [sestavení](/azure/devops/pipelines/index)**  
  
|Příznak|Podporováno s Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Místní server TFS|Provést|Projekty Unity se vytvářejí prostřednictvím prostředí Unity, a ne prostřednictvím systému sestavení sady Visual Studio (sestavení v rámci Visual Studio Tools for Unity zkompiluje skripty, ale nevytvoří spustitelný soubor). Projekty Unity je možné [vytvořit z příkazového řádku](https://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentace Unity), takže je možné nakonfigurovat proces MSBuild na serveru TFS, aby prováděl příslušné příkazy Unity za předpokladu, že je v tomto počítači nainstalovaná jednota Unity.<br /><br /> Unity taky nabízí [cloudové sestavení Unity](https://build.cloud.unity3d.com/landing/), které monitoruje úložiště Git nebo SVN a spouští pravidelná sestavení. V současné době nepracuje s Správa verzí Team Foundation ani Visual Studio Team Services.|  
|Místní sestavovací Server propojený s Visual Studio Team Services|Provést|Vzhledem k tomu, že jsou uvedené stejné podmínky jako výše, je dále možné směrovat sestavení aktivované prostřednictvím Visual Studio Team Services pro použití místního počítače TFS.  Pokyny najdete v tématu [sestavení serveru](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) .|  
|Služba hostovaného kontroleru služby Visual Studio Team Services|Ne|Sestavení Unity se v současnosti nepodporují.|  
|Definice buildu s využitím předzálohovacích skriptů|Ano|Vlastní definice sestavení, která používá příkazový řádek Unity pro spuštění sestavení, se dá nakonfigurovat taky pro skripty spouštěné předem a po sestavení.|  
|Průběžná integrace včetně ověřovaných vrácení se změnami|Ano|Ověřované vrácení se změnami pro TFVC jenom v případě, že Git funguje na modelu žádosti o přijetí změn, a ne vrácení se změnami.|  
  
## <a name="testing"></a>Testování  
 Referenční odkaz: ** [testování aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Příznak|Podporováno s Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Plánování testů, vytváření testovacích případů a organizování testovacích sad|Ano||  
|Manuální testování|Ano||  
|Test Manager (testy záznamů a přehrávání)|Jenom zařízení s Windows a emulátory pro Android||  
|Pokrytí kódu|Není k dispozici|Nedá se použít jako testování částí v Unity a ne v sadě Visual Studio, viz níže.|  
|[Testy jednotek kódu](../test/unit-test-your-code.md)|V Unity, ale ne v sadě Visual Studio|Unity poskytuje vlastní testovací architekturu jednotek jako součást [testovacích nástrojů Unity](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (úložiště assetů Unity). Výsledky testování částí jsou hlášeny v rámci Unity a nebudou se v sadě Visual Studio rozplochy.|  
|[Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)|Ne|Programové testy uživatelského rozhraní spoléhají na čitelné ovládací prvky v uživatelském rozhraní aplikace. Aplikace Unity jsou grafické, takže obsah není čitelný pomocí nástrojů programového testu uživatelského rozhraní.|  
  
## <a name="improve-code-quality"></a>Zlepšení kvality kódu  
 Odkaz na odkaz: ** [vylepšení kvality kódu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Příznak|Podporováno s Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|[Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ano|Může analyzovat kód skriptu jazyka C# v sadě Visual Studio.|  
|[Hledání duplicitního kódu pomocí zjišťování klonování kódu](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Ano|Může analyzovat kód skriptu jazyka C# v sadě Visual Studio.|  
|[Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ano|Může analyzovat kód skriptu jazyka C# v sadě Visual Studio.|  
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|Ne|Používejte [Profiler Unity](https://docs.unity3d.com/Manual/Profiler.html) (Web Unity).|  
|[Analýza problémů s pamětí rozhraní .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Ne|Nástroje sady Visual Studio se nepřipojily k rozhraní Mono (jak je používáno v Unity) k profilaci. Použijte [Profiler Unity](https://docs.unity3d.com/Manual/Profiler.html) (dokumentace Unity).|  
  
## <a name="release-management"></a>Správa vydaných verzí  
 Odkaz odkaz: ** [Automatizace nasazení pomocí Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Příznak|Podporováno s Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Správa procesů vydaných verzí|Ano||  
|Nasazení na servery pro souběžné načítání prostřednictvím skriptů|Ano||  
|Nahrát do App Storu|Částečné|K dispozici jsou rozšíření, která mohou tento proces automatizovat pro některé obchody s aplikacemi.  Viz [rozšíření pro Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); například [rozšíření pro Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitorování pomocí HockeyApp  
 Odkaz odkaz: ** [monitorování pomocí HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Příznak|Podporováno s Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Analýza selhání, telemetrie a distribuce beta verzí|Ano|HockeyApp je primárně užitečná pro zpracování distribuce beta verzí a získání hlášení o chybách.<br /><br /> Pro telemetrii z skriptů jazyka C# je možné použít libovolné analytické rozhraní, které je k dispozici ve verzi rozhraní .NET, kterou používá Unity. To ale umožňuje analýzám jenom v rámci herních skriptů a ne i v jádru Unity. V současné době není k dispozici žádný modul plug-in pro Application Insights, ale moduly plug-in jsou k dispozici pro jiná analytická [řešení, jako](https://github.com/googleanalytics/google-analytics-plugin-for-unity)je třeba [Analýza Unity](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) Služby, jako je analýza Unity, které rozumí povaze projektu Unity, samozřejmě poskytují mnohem smysluplnější analýzu než obecná rozhraní.|
