---
title: Správa životního cyklu aplikací (ALM) s aplikacemi Xamarin | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: f2e7af8227e11d554a4f953593dad396d5543aca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745202"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Správa životního cyklu aplikací s aplikacemi Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Xamarin umožňuje vytvářet multiplatformní mobilní aplikace cílí na Android, iOS a Windows pomocí C#, .NET a Visual Studio. Xamarin umožňuje velkou část kódu sdílet mezi platformami s pouze malým procentem museli být specifické pro platformu. Další informace o Xamarinu, sama, naleznete v tématu [Visual Studio a Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Vývoj aplikací pro moderní platformy zahrnuje mnoho aktivit více než jen psaní kódu. Tyto aktivity, označuje jako span kompletní životní cyklus aplikace DevOps (vývoj + operations) a zahrnují plánování a sledování práce, navrhování a implementace kódu, správu úložiště zdrojového kódu, běžících sestavení, Správa průběžné integrace nasazení, testování (včetně jednotkové testy a testy uživatelského rozhraní), spuštění různé formy diagnostiku ve vývojovém a produkčním prostředí a sledování výkonu a uživatel chování aplikací v reálném čase prostřednictvím telemetrie a analýz.  
  
 Visual Studio spolu s Visual Studio Team Services a Team Foundation Server poskytuje širokou škálu možnosti DevOps, také označuje jako správa životního cyklu aplikací nebo ALM. Mnohé z nich jsou zcela použitelná pro multiplatformní projekty.  
  
 To platí zejména s aplikacemi Xamarin vzhledem k tomu, že tyto šablony jsou sestaveny pomocí jazyka C# a .NET, po které některé ALM jsou integrované nástroje. Další nástroje, vyžaduje úzkou integraci s buildu a běhového prostředí. Protože aplikace spustit na platformách než Windows a Xamarin používat Mono implementaci rozhraní .NET, Xamarin poskytuje pro určité vyžaduje specializované nástroje.  
  
 V tabulce dole najdete identifikuje funkcí, které Visual Studio ALM můžete očekávat fungovat dobře si projekt Xamarin a ty, které mají omezení. Naleznete v dokumentaci propojené informace o funkcích, sami.  
  
## <a name="agile-tools"></a>Agilní nástroje  
 Referenční odkaz: **[pracovní](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (pomocí Visual Studio Team Services nebo TFS, včetně Team Explorer Everywhere)  
  
 Obecné komentáře: všechny plánování a sledování funkce jsou nezávislé na typu projektu a kódování jazyky.  
  
|Funkce|Nepodporuje se Xamarinem|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Správa nevyřízených položek a sprintů|Ano||  
|Sledování práce|Ano||  
|Spolupráce pomocí týmové místnosti|Ano||  
|Kanbanové Tabule|Ano||  
|Sestavy a vizualizace průběhu|Ano||  
  
## <a name="modeling"></a>Modelování  
 Referenční odkaz:  **[analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
 Funkce pro návrh platí bez ohledu na programovací jazyk, nebo pracovat s jazyky .NET, jako je C#. Zobrazit [role architektury a modelování diagramů při vývoji softwaru](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) pro jaké aspekty se vztahují ke kódu.  
  
|Funkce|Nepodporuje se Xamarinem|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Sekvenční diagramy|Ano||  
|Grafy závislostí|Ano||  
|Hierarchie volání|Ano||  
|Návrhář tříd|Ano||  
|Průzkumník architektury|Ano||  
|Diagramy UML (použití případu, aktivit, třídy, komponenty, pořadí a DSL)|Ano||  
|Diagramy vrstev|Ano||  
|Ověření vrstvy|Ano||  
  
## <a name="code"></a>Kód  
  
|Funkce|Nepodporuje se Xamarinem|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|[Použití správy verzí Team Foundation](http://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) nebo Visual Studio Team Services|Ano||  
|[Začínáme s úložištěm Git ve službě Team Services](http://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Ano||  
|[Kód analýzy/zlepšení kvality kódu (odkazy, navrhované změny, atd.)](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Ano||  
|[Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)|Ano|S výjimkou napříč hranicemi specifické pro platformu, kde implementace není vyřešený až do spuštění.|  
|[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)|Ano||  
  
## <a name="build"></a>Sestavení  
 Referenční odkaz:  **[sestavení](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Funkce|Nepodporuje se Xamarinem|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Na místním serveru TFS|Ano|Počítače sestavení musí mít nainstalovaný Xamarin a lze propojit na OSX počítač pro vývoj pro iOS. Zobrazit [konfigurace serveru TFS pro Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (webu Xamarin)|  
|Místní server sestavení propojené s Visual Studio Team Services|Ano|Zobrazit [server sestavení](http://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) pokyny.|  
|Hostovaný kontroler služby Visual Studio Team Services|Ano|Zobrazit [sestavení vaší aplikace Xamarin](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin).|  
|Vytvoření definice s předběžné a pozálohovacích skriptů|Ano||  
|Průběžná integrace, včetně hlídané vrácení se změnami se|Ano|Ověřované vrácení se změnami se pro TFVC pouze, jak Git funguje na modelu žádosti o přijetí změn spíše než vrácení se změnami.|  
  
## <a name="testing"></a>Testování  
 Referenční odkaz:  **[testování aplikace](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkce|Nepodporuje se Xamarinem|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Plánování testů, vytváření testovacích případů a uspořádání testovacích sad|Ano||  
|Manuální testování|Ano||  
|Test Manager (záznam a přehrávání testů)|Ano|Zařízení Windows a emulátory Androidu jenom ze sady Visual Studio. Záznam pro všechna zařízení je možné s [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
|Pokrytí kódu|není k dispozici||  
|[Testování částí kódu](../test/unit-test-your-code.md)|Ano|Pro Windows a cílech Android je možné integrované nástroje MSTest. Xamarin pro spuštění testů jednotek pro Windows, Android a iOS, doporučuje NUnit. Zobrazit [konfigurace serveru TFS pro Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin webu).|  
|[Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)|Pouze Windows|Rekordér testu uživatelského rozhraní sady Visual Studio je jenom pro Windows. Pro všechny platformy, najdete v článku [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Zlepšení kvality kódu  
 Referenční odkaz:  **[zlepšení kvality kódu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkce|Nepodporuje se Xamarinem|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|[Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ano||  
|[Hledání duplicitního kódu pomocí zjišťování klonování kódu](http://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Ano||  
|[Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ano||  
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|Ne|Použití [Xamarin Profiler](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) přes Xamarin Studio místo. Všimněte si, že Xamarin Profiler je aktuálně ve verzi preview a ještě nefunguje pro Windows cíle.|  
|[Analýza problémů paměti rozhraní .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Ne|Nástroje sady Visual Studio nemusí háky do Mono framework pro profilování.|  
  
## <a name="release-management"></a>Správa vydaných verzí  
 Referenční odkaz:  **[automatizovat nasazení pomocí správy vydaných verzí](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkce|Nepodporuje se Xamarinem|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Správa procesů vydávání verzí|Ano||  
|Nasazení na servery pro zkušební načtení pomocí skriptů|Ano||  
|Nahrát do app storu|Částečné|Rozšíření jsou k dispozici, který tento proces pro některé obchody automatizovat.  Zobrazit [rozšíření pro Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), například [rozšíření pro Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitorování pomocí aplikace HockeyApp  
 Referenční odkaz:  **[monitorování pomocí aplikace HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkce|Nepodporuje se Xamarinem|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|K chybě analýzy, telemetrie a beta rozdělení|Ano||

