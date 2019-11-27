---
title: Správa životního cyklu aplikací (ALM) s aplikacemi pro Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1a0ea4f611c5312331fa0e2f2f467b4189778f30
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300024"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Správa životního cyklu aplikací s aplikacemi Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin umožňuje vytvářet mobilní aplikace pro různé platformy, které cílí na Android, iOS a Windows pomocí C#, .NET a Visual studia. Xamarin umožňuje sdílet velkou část kódu mezi platformami, a to pouze malým procentem vyžadujícím konkrétní platformu. Další informace o Xamarin, který je samotný, najdete v tématu [Visual Studio a Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Vývoj aplikací pro moderní platformy zahrnuje mnoho dalších aktivit než jenom psaní kódu. Tyto aktivity, označované jako DevOps (vývoj a operace), zahrnují úplný životní cyklus aplikace a zahrnují plánování a sledování práce, návrh a implementaci kódu, správu úložiště zdrojového kódu, spouštění sestavení a správu průběžných integrací. a nasazení, testování (včetně testů jednotek a testů uživatelského rozhraní), spouštění různých forem diagnostiky ve vývojovém i produkčním prostředí a monitorování výkonu aplikací a chování uživatelů v reálném čase prostřednictvím telemetrie a analýz.  
  
 Visual Studio společně s Visual Studio Team Services a Team Foundation Server poskytují celou řadu funkcí DevOps, označovaných také jako správa životního cyklu aplikací nebo ALM. Mnohé z nich jsou plně použitelné pro projekty pro různé platformy.  
  
 To platí zejména pro aplikace Xamarin, protože jsou sestavené s C# rozhraním .NET, kde jsou vytvořeny některé nástroje Alm. Jiné nástroje, vyžadují úzkou integraci s prostředími sestavení a runtime. Vzhledem k tomu, že aplikace Xamarin běží na platformách jiných než Windows a používají implementaci .NET mono, nabízí Xamarin specializované nástroje pro určité potřeby.  
  
 Níže uvedené tabulky určují, které funkce sady Visual Studio ALM můžete očekávat dobře pracovat s projektem Xamarin a u kterých mají omezení. Podrobnosti o samotných funkcích najdete v odkazované dokumentaci.  
  
## <a name="agile-tools"></a>Agilní nástroje  
 Odkaz na odkaz: **[práce](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (pomocí Visual Studio Team Services nebo TFS, včetně Team Explorer Everywhere)  
  
 Obecný komentář: všechny funkce plánování a sledování jsou nezávislé na typu projektu a jazycích kódování.  
  
|Funkce|Podporováno v Xamarin|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Správa nevyřízených položek a sprintů|Ano||  
|Sledování práce|Ano||  
|Spolupráce v týmové místnosti|Ano||  
|Kanbanové desky|Ano||  
|Sestavování a vizualizace průběhu|Ano||  
  
## <a name="modeling"></a>Modelování  
 Referenční odkaz:  **[Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
 Funkce návrhu jsou nezávislé na jazyku kódování nebo fungují s jazyky .NET, C#jako je. Informace o aspektech souvisejících s kódem najdete [v tématu role architektury a diagramů modelování v vývoji softwaru](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) .  
  
|Funkce|Podporováno v Xamarin|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Sekvenční diagramy|Ano||  
|Grafy závislostí|Ano||  
|Hierarchie volání|Ano||  
|Návrhář tříd|Ano||  
|Průzkumník architektury|Ano||  
|Diagramy UML (případ použití, aktivita, třída, komponenta, sekvence a DSL)|Ano||  
|Diagramy vrstev|Ano||  
|Ověření vrstvy|Ano||  
  
## <a name="code"></a>Kód  
  
|Funkce|Podporováno v Xamarin|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|[Použití Správa verzí Team Foundation](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) nebo Visual Studio Team Services|Ano||  
|[Začínáme s Git ve službě Team Services](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Ano||  
|[Analýza kódu/zlepšení kvality kódu (odkazy, navrhované změny atd.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Ano||  
|[Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)|Ano|Výjimkou jsou hranice specifické pro platformu, kde implementace není vyřešena až do doby běhu.|  
|[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)|Ano||  
  
## <a name="build"></a>Sestavení  
 Odkaz na odkaz:  **[sestavení](/azure/devops/pipelines/index)**  
  
|Funkce|Podporováno v Xamarin|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Místní server TFS|Ano|Počítače pro sestavení musí mít nainstalovaný Xamarin a můžou být propojené s OSX počítačem pro sestavení pro iOS. Viz [konfigurace TFS pro Xamarin](https://docs.microsoft.com/azure/devops/repos/tfvc/overview?view=azure-devops) (Web Xamarin)|  
|Místní sestavovací Server propojený s Visual Studio Team Services|Ano|Pokyny najdete v tématu [sestavení serveru](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) .|  
|Služba hostovaného kontroleru služby Visual Studio Team Services|Ano|Viz [Vytvoření aplikace Xamarin](https://www.visualstudio.com/docs/build/apps/mobile/xamarin).|  
|Definice buildu s využitím předzálohovacích skriptů|Ano||  
|Průběžná integrace včetně ověřovaných vrácení se změnami|Ano|Ověřované vrácení se změnami pro TFVC jenom v případě, že Git funguje na modelu žádosti o přijetí změn, a ne vrácení se změnami.|  
  
## <a name="testing"></a>Testování  
 Referenční odkaz:  **[testování aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkce|Podporováno v Xamarin|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Plánování testů, vytváření testovacích případů a organizování testovacích sad|Ano||  
|Manuální testování|Ano||  
|Test Manager (testy záznamů a přehrávání)|Ano|Zařízení se systémem Windows a emulátory systému Android pouze ze sady Visual Studio. Záznam pro všechna zařízení je možné použít v programu [Xamarin test](https://www.xamarin.com/test-cloud/recorder)Record.|  
|Pokrytí kódu|neuvedeno||  
|[Testování částí kódu](../test/unit-test-your-code.md)|Ano|Pro cíle Windows a Androidu je možné použít integrované nástroje MSTest. Pro spuštění testů jednotek v systémech Windows, Android a iOS doporučuje Xamarin doporučit NUnit. Viz [konfigurace TFS pro Xamarin](https://docs.microsoft.com/azure/devops/repos/tfvc/overview?view=azure-devops) (Web Xamarin).|  
|[Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)|Pouze Windows|Zapisovač testu uživatelského rozhraní sady Visual Studio je pouze Windows. Pro všechny platformy si přečtěte téma [Xamarin test](https://www.xamarin.com/test-cloud/recorder)Record.|  
  
## <a name="improve-code-quality"></a>Zlepšení kvality kódu  
 Odkaz na odkaz:  **[vylepšení kvality kódu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkce|Podporováno v Xamarin|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|[Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ano||  
|[Hledání duplicitního kódu pomocí zjišťování klonování kódu](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Ano||  
|[Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ano||  
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|Ne|Místo toho použijte [Xamarin Profiler](https://docs.microsoft.com/xamarin/cross-platform/deploy-test/) do Xamarin Studio. Všimněte si, že Xamarin Profiler je momentálně ve verzi Preview a ještě nefunguje pro cíle Windows.|  
|[Analýza problémů s .NET Framework paměti](../misc/analyze-dotnet-framework-memory-issues.md)|Ne|Nástroje sady Visual Studio nejsou zapojeny do architektury mono pro profilování.|  
  
## <a name="release-management"></a>Správa vydaných verzí  
 Odkaz odkaz:  **[Automatizace nasazení pomocí Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkce|Podporováno v Xamarin|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Správa procesů vydaných verzí|Ano||  
|Nasazení na servery pro souběžné načítání prostřednictvím skriptů|Ano||  
|Nahrát do App Storu|Částečně|K dispozici jsou rozšíření, která mohou tento proces automatizovat pro některé obchody s aplikacemi.  Viz [rozšíření pro Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); například [rozšíření pro Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitorování pomocí HockeyApp  
 Odkaz odkaz:  **[monitorování pomocí HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkce|Podporováno v Xamarin|Další komentáře|  
|-------------|----------------------------|-------------------------|  
|Analýza selhání, telemetrie a distribuce beta verzí|Ano||
