---
title: Správa životního cyklu aplikací (ALM) s aplikacemi Unity | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 0a39bee5517f0a4311613af336a5b8bc6e6fa00e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760710"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Application Lifecycle Management (ALM) s aplikacemi Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vývoj aplikací pro moderní platformy zahrnuje mnoho aktivit více než jen psaní kódu. Tyto aktivity také říká DevOps (vývoj + operations) span kompletní životní cyklus aplikace a zahrnují plánování a sledování práce, navrhování a implementace kódu, správu úložiště zdrojového kódu, běžících sestavení, Správa průběžné integrace nasazení, testování (včetně jednotkové testy a testy uživatelského rozhraní), spuštění různé formy diagnostiku ve vývojovém a produkčním prostředí a sledování výkonu a uživatel chování aplikací v reálném čase prostřednictvím telemetrie a analýz.  
  
 Visual Studio spolu s Visual Studio Team Services a Team Foundation Server poskytuje širokou škálu možnosti DevOps, také označuje jako správa životního cyklu aplikací nebo ALM. Mnohé z nich se vztahují na projekty napříč platformami, včetně hry a atraktivní grafických aplikací vytvořených v Unity, zvláště při použití jazyka C# jako skriptovací jazyk. Ale protože Unity má svou vlastní vývojové prostředí a modulu runtime, mnoho funkcí ALM nemůžete použít jako u jiných typů projektů vytvořených v sadě Visual Studio.  
  
 V tabulce dole najdete identifikuje jak Visual Studio ALM funkce použít nebo nemůžete použít při práci s Unity. Naleznete v dokumentaci propojené informace o funkcích, sami.  
  
## <a name="agile-tools"></a>Agilní nástroje  
 Referenční odkaz: **[pracovní](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (pomocí Visual Studio Team Services nebo TFS, včetně Team Explorer Everywhere)  
  
 Obecné komentáře: všechny plánování a sledování funkce jsou nezávislé na typu projektu a kódování jazyky.  
  
|Funkce|Podporované v Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Správa nevyřízených položek a sprintů|Ano||  
|Sledování práce|Ano||  
|Spolupráce pomocí týmové místnosti|Ano||  
|Kanbanové Tabule|Ano||  
|Sestavy a vizualizace průběhu|Ano||  
  
## <a name="modeling"></a>Modelování  
 Referenční odkaz:  **[analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
 Obecné komentáře: I když tyto funkce návrhu jsou buď bez ohledu na programovací jazyk, nebo pracovat s jazyky .NET, jako je C#, pracují na paradigma tradiční aplikace s hierarchie objektů a relace tříd. Návrh her v Unity zahrnuje různé paradigma úplně se vynechá, konkrétně vztahy grafických objektů, zvuky, shadery, skripty a tak dále. Z tohoto důvodu, Visual Studio, diagram modelování nástroje nejsou zvlášť důležité u celé Unity projektu. Může být pravděpodobně používá ke správě relací v rámci skripty jazyka C#, ale to je jenom jedna část celé.  
  
|Funkce|Podporované v Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Sekvenční diagramy|Ne||  
|Grafy závislostí|Ne||  
|Hierarchie volání|Ne||  
|Návrhář tříd|Ne||  
|Průzkumník architektury|Ne||  
|Diagramy UML (použití případu, aktivit, třídy, komponenty, pořadí a DSL)|Ne||  
|Diagramy vrstev|Ne||  
|Ověření vrstvy|Ne||  
  
## <a name="code"></a>Kód  
  
|Funkce|Podporované v Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|[Použití správy verzí Team Foundation](http://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) nebo Visual Studio Team Services|Ano|Projekty Unity jsou jednoduše kolekce souborů, které jde umístit do systémů správy verzí, stejně jako libovolný jiný projekt, ale existuje několik důležitých popsané za touto tabulkou.|  
|[Začínáme s úložištěm Git ve službě Team Services](http://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Ano|Pod tabulkou naleznete v poznámkách.|  
|[Kód analýzy/zlepšení kvality kódu (odkazy, navrhované změny, atd.)](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Ano||  
|[Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)|Ano||  
|[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)|Ano||  
  
 Zvláštní upozornění pro správu verzí pomocí Unity:  
  
1.  Unity sleduje metadata o herních prostředků v jedné, neprůhledný knihovnu, která je ve výchozím nastavení skrytá. Pro synchronizaci souborů a metadat, je nezbytné, chcete-li zobrazit metadata a jeho uložení do více spravovatelných blocích. Podrobnosti najdete v [pomocí externích systémů pro správu verzí pomocí Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentace k Unity).  
  
2.  Ne všechny soubory a složky v Unity projektu jsou vhodné pro správu zdrojového kódu, jako je také popsáno v výše uvedený odkaz. Prostředky a ProjectSettings složky by měly být přidány, ale knihovny a dočasné složky by neměla. Další seznam generovaných souborů, které by přejít do správy zdrojového kódu, viz diskuze [jak používat Git pro správu zdrojového kódu enginy Unity3D?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na StackOverflow. Mnoho vývojářů mají také blozích máte k tomuto tématu nezávisle na sobě.  
  
3.  Binární prostředky v Unity projektu – například textury nebo zvukové soubory, může trvat až velké množství úložiště. Různé systémy správy zdrojového kódu jako je Git uložit kopii soubor pro každé změny, který je vytvořen, jedinečný i v případě, že tato změna má vliv pouze malou část souboru. To může způsobit opakovaném úložiště Git. Z toho vývojářům Unity často se je rozhodnete pouze konečný prostředky přidejte do své úložiště a použít jiný způsob uchování historie pracovní svých prostředků, jako je například OneDrive, DropBox nebo git přílohy. Tento přístup funguje, protože tyto prostředky většinou nemusí být označené verzí společně se změnami zdrojového kódu. Vývojáři také běžně nastaven režim serializace Asset editoru projektu na platnost Text k ukládání souborů scény v textu, nikoli binární formát, který umožňuje sloučení ve správě zdrojového kódu. Podrobnosti najdete v tématu [nastavení editoru](http://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentace k Unity).  
  
## <a name="build"></a>Sestavení  
 Referenční odkaz:  **[sestavení](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Funkce|Podporované v Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Na místním serveru TFS|Je to možné|Projekty Unity jsou integrované prostřednictvím prostředí Unity a ne prostřednictvím sady Visual Studio sestavovacího systému (sestavení v rámci Visual Studio Tools pro Unity se zkompilovat skripty, ale výsledkem není spustitelný soubor). Je možné [sestavování projektů Unity z příkazového řádku](http://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentace k Unity), takže je možné nakonfigurovat procesu MSBuild na serveru TFS k provedení příslušné Unity příkazy, za předpokladu, že Unity samotného je nainstalovaný na Tento počítač.<br /><br /> Unity nabízí také [sestavení Unity cloudu](https://build.cloud.unity3d.com/landing/), který sleduje úložiště Git nebo SVN a spouští pravidelná sestavení. V současné době to nebude fungovat s verzí Team Foundation nebo Visual Studio Team Services.|  
|Místní server sestavení propojené s Visual Studio Team Services|Je to možné|Zadaný stejných podmínek jako výše je dál možné přímé sestavení vyvolané prostřednictvím Visual Studio Team Services v místním počítači TFS.  Zobrazit [server sestavení](http://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) pokyny.|  
|Hostovaný kontroler služby Visual Studio Team Services|Ne|Unity sestavení nejsou v současné době nepodporují.|  
|Vytvoření definice s předběžné a pozálohovacích skriptů|Ano|Definice vlastního sestavení, která používá Unity příkazový řádek pro spuštění sestavení můžete také nakonfigurovat pro skripty před a po sestavení.|  
|Průběžná integrace, včetně hlídané vrácení se změnami se|Ano|Ověřované vrácení se změnami se pro TFVC pouze, jak Git funguje na modelu žádosti o přijetí změn spíše než vrácení se změnami.|  
  
## <a name="testing"></a>Testování  
 Referenční odkaz:  **[testování aplikace](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkce|Podporované v Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Plánování testů, vytváření testovacích případů a uspořádání testovacích sad|Ano||  
|Manuální testování|Ano||  
|Test Manager (záznam a přehrávání testů)|Jenom Android emulátory a zařízení Windows||  
|Pokrytí kódu|není k dispozici|Není k dispozici jako jednotky testování se stane v Unity a nikoli Visual Studio, najdete níže.|  
|[Testování částí kódu](../test/unit-test-your-code.md)|V rámci Unity, ale ne Visual Studio|Unity nabízí svůj vlastní rozhraní pro testování částí v rámci [testovací nástroje Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (Store Unity Asset). Výsledky testování částí jsou hlášeny v Unity a nesmí být prezentované v sadě Visual Studio.|  
|[Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)|Ne|Programové testy uživatelského rozhraní závisí na čitelné ovládací prvky v Uživatelském rozhraní aplikace; Jsou ze své podstaty grafické aplikace Unity a proto není čitelný pomocí nástroje test uživatelského rozhraní pro obsah.|  
  
## <a name="improve-code-quality"></a>Zlepšení kvality kódu  
 Referenční odkaz:  **[zlepšení kvality kódu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkce|Podporované v Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|[Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ano|Můžete analyzovat kód skriptu jazyka C# v sadě Visual Studio.|  
|[Hledání duplicitního kódu pomocí zjišťování klonování kódu](http://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Ano|Můžete analyzovat kód skriptu jazyka C# v sadě Visual Studio.|  
|[Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ano|Můžete analyzovat kód skriptu jazyka C# v sadě Visual Studio.|  
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|Ne|Použití [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity webu).|  
|[Analýza problémů paměti rozhraní .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Ne|Nástroje sady Visual Studio nemusí háky do Mono framework (jako Unity) pro profilování. Použití [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (dokumentace k Unity).|  
  
## <a name="release-management"></a>Správa vydaných verzí  
 Referenční odkaz:  **[automatizovat nasazení pomocí správy vydaných verzí](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkce|Podporované v Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Správa procesů vydávání verzí|Ano||  
|Nasazení na servery pro zkušební načtení pomocí skriptů|Ano||  
|Nahrát do app storu|Částečné|Rozšíření jsou k dispozici, který tento proces pro některé obchody automatizovat.  Zobrazit [rozšíření pro Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), například [rozšíření pro Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitorování pomocí aplikace HockeyApp  
 Referenční odkaz:  **[monitorování pomocí aplikace HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkce|Podporované v Unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|K chybě analýzy, telemetrie a beta rozdělení|Ano|HockeyApp je užitečné hlavně pro zpracování distribuce beta verzí a získání hlášení o selhání.<br /><br /> Telemetrie z skripty jazyka C# je možné použít jakýkoli analytics rozhraní za předpokladu, že běží na verzi rozhraní .NET, která používá Unity. Nicméně díky tomu pro analýzu jenom v rámci her skriptů a ne hlouběji uvnitř herní engine Unity. V současné době neexistuje žádný modul plugin pro službu Application Insights, ale moduly plug-in, jako jsou k dispozici pro ostatní řešení pro analýzu [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) a [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Služeb, jako je Unity analýzy, které pochopení povahy Unity projektu bude samozřejmě poskytují mnohem větší smysl analýzy než obecného rozhraní.|



