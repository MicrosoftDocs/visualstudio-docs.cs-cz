---
title: Správa načítání projektů v řešení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64786148"
---
# <a name="managing-project-loading-in-a-solution"></a>Správa načítání projektů v řešení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Řešení sady Visual Studio můžou obsahovat velký počet projektů. Výchozím chováním sady Visual Studio je načíst všechny projekty v řešení v době, kdy je řešení otevřeno, a nedovolit uživateli přístup k jakémukoli z projektů, dokud se všechny z nich nedokončí. Pokud bude proces načítání projektu poslední více než dvě minuty, zobrazí se indikátor průběhu znázorňující počet načtených projektů a celkový počet projektů. Uživatel může uvolnit projekty při práci v řešení s více projekty, ale tento postup má některé nevýhody: Nenačtené projekty nejsou sestaveny jako součást příkazu znovu sestavit řešení a popisy IntelliSense typů a členů uzavřených projektů nejsou zobrazeny.  
  
 Vývojáři můžou snížit dobu načítání řešení a spravovat chování při načítání projektů vytvořením správce načtení řešení. Správce načtení řešení může nastavit různé priority načítání projektů pro konkrétní projekty nebo typy projektů, zajistit, aby se projekty načetly před zahájením sestavení na pozadí, zpozdilo načítání na pozadí, dokud nebudou dokončeny jiné úlohy na pozadí, a provádět další úlohy správy zatížení projektu.  
  
## <a name="project-loading-priorities"></a>Priority načtení projektu  
 Visual Studio definuje čtyři různé priority načtení projektu:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (výchozí): když je otevřeno řešení, projekty se načítají asynchronně. Pokud je tato priorita nastavena v uvolněném projektu poté, co je řešení již otevřeno, projekt bude načten do dalšího nečinného bodu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: když je otevřeno řešení, projekty jsou načteny na pozadí, což uživateli umožňuje přístup k projektům při jejich načtení bez nutnosti čekat, dokud nejsou načteny všechny projekty.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projekty jsou načteny při jejich použití. K projektu je přihlášený, když uživatel rozbalí uzel projektu v Průzkumník řešení, když se otevře soubor patřící do projektu, protože je v seznamu otevřených dokumentů (uložený v souboru uživatelských možností řešení), nebo když jiný projekt, který se načítá, má závislost na projektu. Tento typ projektu není před spuštěním procesu sestavení automaticky načten; Správce zatížení řešení zodpovídá za to, aby bylo zajištěno, že budou načteny všechny potřebné projekty. Tyto projekty by se měly také načíst před spuštěním hledání a nahrazení v souborech v celém rámci celého řešení.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projekty nelze načíst, pokud je uživatel výslovně nepožaduje. To je případ, kdy jsou projekty explicitně uvolněny.  
  
## <a name="creating-a-solution-load-manager"></a>Vytvoření správce zatížení řešení  
 Vývojáři mohou vytvořit správce načtení řešení implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> a poradenstvím sady Visual Studio, že je správce zatížení řešení aktivní.  
  
#### <a name="activating-a-solution-load-manager"></a>Aktivace správce zatížení řešení  
 Visual Studio umožňuje v daný okamžik pouze jednoho správce načtení řešení, takže je nutné poradit se systémem Visual Studio, pokud chcete aktivovat správce zatížení řešení. Pokud se později aktivuje druhý správce načtení řešení, váš správce zatížení řešení se odpojí.  
  
 Musíte získat <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> službu a nastavit <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> vlastnost:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementace IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>Metoda je volána během procesu otevírání řešení. Chcete-li implementovat tuto metodu, použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> službu k nastavení priority zatížení pro typ projektu, který chcete spravovat. Například následující kód nastaví typy projektů C# k načtení na pozadí:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Metoda je volána buď při vypnutí sady Visual Studio, nebo v případě, že byl jiný balíček převzat jako aktivní správce načtení řešení voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> Vlastnosti.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie pro různé druhy správce načtení řešení  
 Správce načítání řešení můžete implementovat různými způsoby v závislosti na typech řešení, která jsou určena ke správě.  
  
 Je-li správce načtení řešení určen ke správě obecného načítání řešení, je možné jej implementovat jako součást VSPackage. Balíček by měl být nastaven na AUTOLOAD přidáním na <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> VSPackage s hodnotou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . V metodě se pak dá aktivovat správce načtení řešení <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
> [!NOTE]
> Další informace o automatickém načítání balíčků naleznete v tématu [načítání VSPackage](../extensibility/loading-vspackages.md).  
  
 Vzhledem k tomu, že aplikace Visual Studio rozpozná pouze posledního správce načtení řešení, který má být aktivován, by měli správci načtení obecných řešení vždycky zjistit, zda existoval správce zatížení před aktivací. Pokud volání GetProperty () ve službě řešení pro <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> vrácení vrátí `null` , neexistuje žádný aktivní správce načtení řešení. Pokud nevrátí hodnotu null, ověřte, zda je objekt stejný jako váš správce zatížení řešení.  
  
 Pokud má správce zatížení řešení spravovat pouze několik typů řešení, VSPackage se může přihlásit k odběru událostí načtení řešení (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) a použít obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> aktivaci správce načtení řešení.  
  
 Pokud má správce zatížení řešení spravovat pouze konkrétní řešení, mohou být aktivační informace uchovány jako součást souboru řešení. Chcete-li to provést, zavolejte na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> oddíl pre-Solution.  
  
 Konkrétní správci načtení řešení by se měli v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> obslužné rutině události deaktivovat, aby nedocházelo ke konfliktům s jinými správci načtení řešení.  
  
 Pokud potřebujete správce načtení řešení pouze pro zachování globálních priorit zatížení projektu (například vlastnosti nastavené na stránce Možnosti), můžete aktivovat správce načtení řešení v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> obslužné rutině události, zachovat nastavení ve vlastnostech řešení a pak deaktivovat správce načtení řešení.  
  
## <a name="handling-solution-load-events"></a>Zpracování událostí načtení řešení  
 Chcete-li se přihlásit k odběru událostí načtení řešení, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> při aktivaci správce zatížení řešení. Pokud implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , můžete reagovat na události, které se vztahují k různým prioritám načtení projektu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Tato akce je aktivována před otevřením řešení. Můžete ji použít ke změně priority načtení projektu pro projekty v řešení.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Tato akce je aktivována po úplném načtení řešení, ale před začátkem nasazování projektu na pozadí. Například uživatel se mohl dostat k projektu, jehož priorita zatížení je LoadIfNeeded, nebo správce zatížení řešení mohl změnit prioritu zatížení projektu na BackgroundLoad, což by vedlo k tomu, že se spustí zatížení tohoto projektu na pozadí.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Tato událost je aktivována po prvním úplném načtení řešení, bez ohledu na to, zda existuje správce načtení řešení. Je také aktivována po načtení nebo zatížení na pozadí, kdykoli se řešení úplně načte. V současné době <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se znovu aktivuje.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Tato akce je aktivována před načtením projektu (nebo projektů). Aby bylo zajištěno, že před načtením projektů byly dokončeny další procesy na pozadí, nastavte `pfShouldDelayLoadToNextIdle` na **hodnotu true**.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Tato událost je aktivována, když bude načtena dávka projektů. Pokud `fIsBackgroundIdleBatch` je hodnota true, projekty budou načteny na pozadí. Pokud je hodnota `fIsBackgroundIdleBatch` false, projekty mají být načteny synchronně jako výsledek požadavku uživatele, například pokud uživatel rozbalí nedokončený projekt v Průzkumník řešení. To můžete provést tak, aby fungovala náročná práce, kterou by jinak bylo potřeba udělat v nástroji <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Aktivuje se po načtení dávky projektů.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Zjišťování a Správa načítání řešení a projektů  
 Aby bylo možné zjistit stav zatížení projektů a řešení, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> následující hodnoty:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` vrátí `true` , zda je řešení a všechny jeho projekty načteno, jinak `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` vrátí `true` , zda je dávka projektů v současné době načítána na pozadí, jinak `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` vrátí `true` , zda je dávka projektů v současné době načítána synchronně v důsledku uživatelského příkazu nebo jiné explicitní zátěže, jinak `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` vrátí `true` , zda je řešení momentálně uzavřeno, jinak `false` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` vrátí `true` , zda je aktuálně otevřeno řešení, jinak `false` .  
  
  Můžete také zajistit, aby byly projekty a řešení načteny (bez ohledu na to, co priority zatížení projektu jsou) voláním jedné z následujících metod:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: volání této metody vynutí, aby se projekty v řešení načetly předtím, než se metoda vrátí.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: volání této metody vynutí, aby se projekty `guidProject` načetly předtím, než se metoda vrátí.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: volání této metody vynutí, aby byl projekt `guidProjectID` načten před vrácením metody.  
  
> [!NOTE]
> . Ve výchozím nastavení jsou načteny pouze projekty, které mají zatížení požadavků a priority zatížení na pozadí, ale pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> je příznak předán do metody, budou načteny všechny projekty kromě těch, které jsou označeny pro explicitní načtení.
