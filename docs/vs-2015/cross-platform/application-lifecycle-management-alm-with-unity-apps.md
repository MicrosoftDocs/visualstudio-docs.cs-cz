---
title: Správa životního cyklu aplikací (ALM) s aplikacemi Unity | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233282"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Application Lifecycle Management (ALM) s aplikacemi Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vývoj aplikací pro moderní platformy zahrnuje mnohem více aktivit než jen psaní kódu. Tyto aktivity, označované jako DevOps (vývoj + operace) pokrývají celý životní cyklus aplikace a zahrnují plánování a sledování práce, navrhování a implementaci kódu, správu úložiště zdrojového kódu, spouštění sestavení, správu průběžných integrací a nasazení, testování (včetně testů částí a testů uživatelského rozhraní), spuštění různých forem diagnostiky ve vývojovém i produkčním prostředí a monitorování výkonu aplikací a chování uživatelů v reálném čase prostřednictvím telemetrie a analýzy.  
  
 Visual Studio spolu s Visual Studio Team Services a Team Foundation Server poskytují celou řadu funkcí DevOps, označované také jako správa životního cyklu aplikací nebo ALM. Mnohé z nich jsou použitelné pro projekty napříč platformami, včetně her a pohlcující grafické aplikace vytvořené pomocí Unity – zejména při použití Jazyka C# jako skriptovacího jazyka. Protože však Unity má své vlastní vývojové prostředí a modul runtime, řada funkcí ALM neplatí jako pro jiné druhy projektů vytvořených v sadě Visual Studio.  
  
 Níže uvedené tabulky určuje, jak se při práci s Unity použijí nebo neplatí funkce VISUAL Studio ALM. Podrobnosti o samotných funkcích naleznete v propojené dokumentaci.  
  
## <a name="agile-tools"></a>Agilní nástroje  
 Odkaz na odkaz: **[Práce](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (pomocí služby Visual Studio Team Services nebo TFS, včetně Průzkumníka týmů všude)  
  
 Obecný komentář: všechny funkce plánování a sledování jsou nezávislé na typu projektu a kódovacích jazycích.  
  
|Funkce|Podporováno pomocí unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Správa nevyřízených položek a sprintů|Ano||  
|Sledování práce|Ano||  
|Spolupráce v týmové místnosti|Ano||  
|Kanbandesky|Ano||  
|Hlášení a vizualizace průběhu|Ano||  
  
## <a name="modeling"></a>Modelování  
 Odkaz odkaz: ** [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
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
|[Použití správy verzí team foundation](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) nebo týmových služeb sady Visual Studio|Ano|Unity projekty jsou jednoduše kolekce souborů, které lze umístit do systémů správy verzí jako jakýkoli jiný projekt, ale existuje několik zvláštních aspekty popsané po této tabulce.|  
|[Začínáme s Gitem v týmových službách](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Ano|Viz poznámky za stolem.|  
|[Analýza kódu/Zlepšení kvality kódu (odkazy, navrhované změny atd.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Ano||  
|[Nalezení změn kódu a další historie](../ide/find-code-changes-and-other-history-with-codelens.md)|Ano||  
|[Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)|Ano||  
  
 Zvláštní aspekty pro správu verzí s Unity:  
  
1. Unity sleduje metadata o herních datových zdrojích v jedné neprůhledné knihovně, která je ve výchozím nastavení skrytá. Chcete-li zachovat soubory a metadata v synchronizaci, je nutné, aby metadata viditelné a uložit je do více spravovatelné bloky dat. Podrobnosti naleznete [v části Použití externích systémů správy verzí s unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity dokumentace).  
  
2. Ne všechny soubory a složky v projektu Unity jsou vhodné pro složky zdrojového kódu, jak je také popsáno v odkazu výše. Složky Assets a ProjectSettings by měly být přidány, ale složky Knihovna a Temp by neměly. Další seznam generovaných souborů, které by nepřešely do správy zdrojového kódu, najdete v diskusi [Jak používat Git pro ovládací prvek zdroj Unity3D?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na StackOverflow. Mnoho vývojářů také blogged na toto téma nezávisle.  
  
3. Binární datové zdroje v projektu Unity – například textury nebo zvukové soubory – mohou zabírají velké množství úložiště. Různé systémy správy zdrojového kódu, jako je Git, ukládají jedinečnou kopii souboru pro každou provedenou změnu, i když změna ovlivní pouze malou část souboru. To může způsobit, že úložiště Git bude nafouklé. K řešení tohoto problému se vývojáři Unity často rozhodnou přidat do svého úložiště pouze konečné prostředky a používat jiný způsob udržování pracovní historie svých prostředků, jako je Například OneDrive, DropBox nebo git-annex. Tento přístup funguje, protože tyto prostředky obvykle není nutné verzí spolu se změnami zdrojového kódu. Vývojáři také obvykle nastavit editoru projektu Serializace režimu vynutit text ukládat soubory scény v textu, nikoli binární formát, který umožňuje sloučení ve správě zdrojového kódu. Podrobnosti naleznete v [tématu Nastavení editoru](https://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentace Unity).  
  
## <a name="build"></a>Sestavení  
 Odkaz na odkaz: ** [Sestavení](/azure/devops/pipelines/index)**  
  
|Funkce|Podporováno pomocí unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Místní server TFS|Možné|Unity projekty jsou vytvořeny prostřednictvím prostředí Unity a nikoli prostřednictvím systému sestavení sady Visual Studio (sestavení v rámci Visual Studio Tools for Unity bude kompilovat skripty, ale nevytváří spustitelný soubor). Je možné [sestavit unity projekty z příkazového řádku](https://docs.unity3d.com/Manual/CommandLineArguments.html) (Unity dokumentace), takže je možné nakonfigurovat proces MSBuild na serveru TFS ke spuštění příslušné unity příkazy, za předpokladu, že Unity sám je nainstalován v tomto počítači.<br /><br /> Unity také nabízí [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), který monitoruje úložiště Git nebo SVN a spouští periodická sestavení. V současné době nefunguje s Team Foundation version control nebo Visual Studio Team Services.|  
|Místní server sestavení propojený se službou Visual Studio Team Services|Možné|Za stejných podmínek jako výše, je dále možné přímé sestavení spuštěna prostřednictvím Visual Studio Team Services používat místní počítač TFS.  Pokyny najdete [v tématu Sestavení serveru.](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c)|  
|Hostovaná služba řadiče služby Visual Studio Team Services|Ne|Unity sestavení nejsou v současné době podporovány.|  
|Vytváření definic pomocí předa postskriptů|Ano|Vlastní definice sestavení, která používá příkazový řádek Unity ke spuštění sestavení lze také nakonfigurovat pro skripty před a po sestavení.|  
|Průběžná integrace včetně gated check-inů|Ano|Gated vrácení se změnami pro TFVC pouze jako Git pracuje na modelu žádosti o přijetí návladní, spíše než vrácení se změnami.|  
  
## <a name="testing"></a>Testování  
 Referenční odkaz: ** [Testování aplikace](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkce|Podporováno pomocí unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Plánování testů, vytváření testovacích případů a uspořádání testovacích sad|Ano||  
|Ruční testování|Ano||  
|Správce testů (testy záznamu a přehrávání)|Pouze zařízení s Windows a emulátory Androidu||  
|Pokrytí kódu|neuvedeno|Není použitelné jako testování částí se stane v unity a ne Visual Studio, viz níže.|  
|[Testy jednotek kódu](../test/unit-test-your-code.md)|V rámci unity, ale ne Visual Studio|Unity poskytuje vlastní rozhraní testování částí jako součást [Unity Test Tools](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (Unity Asset Store). Výsledky testování částí jsou hlášeny v unity a nebudou se zobrazí v rámci sady Visual Studio.|  
|[Použití automatizace uživatelského rozhraní k testování kódu](../test/use-ui-automation-to-test-your-code.md)|Ne|Programové testy ui spoléhají na čitelné ovládací prvky v rozhraní ui aplikace; Unity aplikace mají grafickou povahu, a proto obsah není čitelný pomocí programové nástroje pro testování uživatelského prostředí.|  
  
## <a name="improve-code-quality"></a>Zlepšení kvality kódu  
 Referenční odkaz: ** [Zlepšení kvality kódu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkce|Podporováno pomocí unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|[Analýza kvality spravovaného kódu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ano|Můžete analyzovat kód skriptu C# v rámci sady Visual Studio.|  
|[Hledání duplicitního kódu pomocí detekce klonování kódu](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Ano|Můžete analyzovat kód skriptu C# v rámci sady Visual Studio.|  
|[Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ano|Můžete analyzovat kód skriptu C# v rámci sady Visual Studio.|  
|[Prohlížeč výkonu](../profiling/performance-explorer.md)|Ne|Použijte [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html) (Unity webové stránky).|  
|[Analýza problémů s pamětí rozhraní .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Ne|Visual Studio nástroje nemají háčky do mono rozhraní (jak je používá Unity) pro profilování. Použijte [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html) (Unity dokumentace).|  
  
## <a name="release-management"></a>Správa vydaných verzí  
 Odkaz na odkaz: ** [Automatizace nasazení pomocí správy verzí](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkce|Podporováno pomocí unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Správa procesů vydání|Ano||  
|Nasazení na servery pro boční načítání pomocí skriptů|Ano||  
|Nahrání do obchodu s aplikacemi|Částečné|K dispozici jsou rozšíření, která mohou tento proces automatizovat pro některé obchody s aplikacemi.  Viz [rozšíření pro služby Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); například [rozšíření pro Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitor s Aplikací HockeyApp  
 Referenční odkaz: ** [Monitor s HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkce|Podporováno pomocí unity|Další komentáře|  
|-------------|--------------------------|-------------------------|  
|Crash analytics, telemetrie a distribuce beta verze|Ano|HockeyApp je primárně užitečný pro zpracování distribuce beta verzí a získávání zpráv o selhání.<br /><br /> Pro telemetrii ze skriptů jazyka C# je možné použít libovolný analytický rámec za předpokladu, že je spuštěn na verzi rozhraní .NET, kterou používá Unity. To však umožňuje analýzy pouze v rámci hernískripty a ne hlouběji uvnitř unity motoru. V současné době neexistuje žádný plugin pro Application Insights, ale pluginy jsou k dispozici pro další analytická řešení, jako je [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) a [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Služby jako Unity Analytics, které chápou povahu projektu Unity, budou samozřejmě poskytovat mnohem smysluplnější analýzu než obecné rámce.|
