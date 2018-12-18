---
title: Správa načítání projektů v řešení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 041c5ab52a7a0e8be89ef1abe6db4d1aed51ecfc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781761"
---
# <a name="managing-project-loading-in-a-solution"></a>Správa načítání projektů v řešení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Řešení sady Visual Studio může obsahovat velký počet projektů. Výchozí chování sady Visual Studio je načíst všechny projekty v řešení v době, kdy je otevřené řešení a nikoli do povolí uživateli přístup žádným z projektů, dokud všechny z nich dokončení načítání. Při procesu načítání projektu bude trvat více než dvě minuty, se zobrazí indikátor průběhu zobrazující počet projekty a celkovém počtu projektů. Uživatel může při práci v řešení s více projekty uvolnění projektů, ale tento postup má i určité nevýhody: jako součást příkazu znovu sestavit řešení nejsou sestaveny uvolněné projekty a popisy technologie IntelliSense typů a členů uzavřený projekty se nezobrazí.  
  
 Vývojářům můžete snížit dobu načítání řešení a spravovat chování načítání tím, že vytvoříte načtení řešení správce projektu. Správce zatížení řešení lze nastavit jiný projekt načítání priority pro konkrétní projekty nebo typy projektů, ujistěte se, že projekty načetly před spuštěním sestavení na pozadí, zpoždění načítání na pozadí, dokud nebudou dokončeny ostatní úlohy na pozadí a provádění Další úlohy správy zatížení projektu.  
  
## <a name="project-loading-priorities"></a>Načítání priority projektu  
 Visual Studio definuje čtyři priority načítání jiného projektu:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (výchozí): při otevření řešení, projekty jsou načítána asynchronně. Pokud tato priorita je nastavena na projekt uvolněn po řešení je již otevřen, projekt se načtou na další bod nečinnosti.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: při otevření řešení, projekty načetly na pozadí, které uživateli umožňují přístup k projekty, jako jsou načteny bez nutnosti čekat, dokud se všechny projekty načetly.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projekty načetly při jsou přístupné. Projekt se přistupuje, když je uživatel rozbalí uzel projektu v Průzkumníku řešení, pokud soubor, který patří do projektu se otevře po otevření řešení, protože je v seznamu otevřených dokumentů (uchovávané v souboru s možností řešení uživatele), nebo pokud jiný projekt který je načítán závislý na projektu. Tento typ projektu není načten automaticky před zahájením procesu sestavení. Správci řešení zatížení zodpovídá za to, zda jsou načteny všechny potřebné projekty. Tyto projekty se mají načíst také před zahájením najít/nahradit v souborech napříč celé řešení.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projekty není mají být načteny, pokud uživatel je výslovně požaduje. To je případ, kdy projekty jsou explicitně uvolněna.  
  
## <a name="creating-a-solution-load-manager"></a>Vytvoření správce načtení řešení  
 Vývojáři mohou vytvářet načtení řešení Správce implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> a sady Visual Studio, že správce zatížení řešení je aktivní.  
  
#### <a name="activating-a-solution-load-manager"></a>Aktivace správce zatížení řešení  
 Visual Studio umožňuje pouze jeden správce zatížení řešení v daném okamžiku, proto musíte poradit sady Visual Studio, pokud chcete aktivovat vaše načtení řešení správce. Pokud později při aktivaci druhý správce zatížení řešení správce zatížení řešení bude odpojen.  
  
 Musíte získat <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> služby a nastavení <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> vlastnost:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementace IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Metoda je volána v průběhu procesu otevření řešení. Implementace této metody použijete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> služby nastavení priority zatížení pro typ projektu, kterou chcete spravovat. Například následující kód nastaví projektu typy C# pro načtení na pozadí:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Metoda je volána, když probíhá vypínání aplikace Visual Studio nebo když se jiný balíček má převzetí jako správce zatížení aktivního řešení voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> s <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> vlastnost.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie pro různé druhy řešení načíst správce  
 Správci zatížení řešení můžete implementovat různými způsoby v závislosti na typech řešení, které jsou určené pro správu.  
  
 Pokud se správce zatížení řešení pro správu obecně načítání řešení, se dá implementovat jako součást sady VSPackage. Balíček musí být nastavená na autoload tak, že přidáte <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> na VSPackage s hodnotou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Správci řešení zatížení můžete v aktivovat <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
> [!NOTE]
>  Další informace o balíčcích autoloading najdete v tématu [načítání rozšíření VSPackages](../extensibility/loading-vspackages.md).  
  
 Vzhledem k tomu, že Visual Studio rozpozná pouze poslední řešení zatížení správce aktivaci, by měl obecné řešení zatížení správci vždy zjistit, zda je před aktivací sami stávající správce zatížení. Pokud volání GetProperty() řešení služby pro <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> vrátí `null`, neexistuje žádný správce zatížení aktivního řešení. Pokud nevrací hodnotu null, zkontrolujte, zda je objekt stejný jako správce zatížení vašeho řešení.  
  
 Pokud se správce zatížení řešení pro správu pouze několik typů řešení, sady VSPackage mohou přihlásit k odběru událostí načítání řešení (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) a použijte obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> aktivovat správce zatížení řešení.  
  
 Pokud se správce zatížení řešení pro správu pouze konkrétní řešení, informace o aktivaci můžete nastavit jako trvalý jako součást souboru řešení. Chcete-li to provést, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> pro části před řešení.  
  
 Konkrétní řešení zatížení Správce by měl deaktivovat sebe sama v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> obslužná rutina události, aby nebyla v konfliktu s ostatními správci načtení řešení.  
  
 Pokud potřebujete správce zatížení řešení pouze k uchování priority zatížení globální projektu (například vlastnosti nastavené u stránky Možnosti), můžete aktivovat správce zatížení řešení v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> obslužná rutina události, zachovat nastavení klikněte v okně vlastností řešení Deaktivujte správce zatížení řešení.  
  
## <a name="handling-solution-load-events"></a>Zpracování událostí načítání řešení  
 Chcete-li přihlásit k odběru řešení zatížení události, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> při aktivaci správce zatížení vašeho řešení. Pokud se rozhodnete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, můžete reagovat na události, které se vztahují k jinému projektu načítání priority.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Toto je aktivována před otevřením řešení. Můžete ho změnit projekt načítání prioritu pro projekty v řešení.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Toto je aktivována po řešení, je zcela načten, ale před pozadí začne znovu načíst projekt. Například uživatel mohl získat přístup k projektu, jejichž priorita zatížení je LoadIfNeeded nebo správce řešení zatížení mohlo změnit prioritu zatížení projektu na BackgroundLoad, který by měl začínat na pozadí zatížení tohoto projektu.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Toto se aktivuje po načtení řešení je zpočátku plně, jestli správce zatížení řešení. Také aktivuje po načtení na pozadí nebo vyžádání načíst pokaždé, když se stane řešení plně načteno. Ve stejnou dobu <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se znovu aktivuje.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Toto je aktivována před načtením projektu (nebo projektů). Ujistěte se, že ostatní procesy na pozadí se dokončila předtím, než se načtou projekty, nastavte `pfShouldDelayLoadToNextIdle` k **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Toto je aktivována, když je batch projektů bude načten. Pokud `fIsBackgroundIdleBatch` má hodnotu true, projekty, které se mají být načteny na pozadí; Pokud `fIsBackgroundIdleBatch` má hodnotu false, projekty, které mají být načteny synchronně jako výsledek požadavku na uživatele, například pokud je uživatel rozbalí čekajícího projektu v Průzkumníku řešení. Můžete implementovat toto tlačítko náročné práce, v opačném případě by bylo potřeba udělat v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Toto je aktivována po načtení služby batch projektů.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Zjišťování a správu řešení a načítání projektů  
 Aby bylo možné zjistit stav načtení projekty a řešení, volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> s použitím následujících hodnot:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` vrátí `true` Pokud řešení a všechny jeho projekty jsou načteny, jinak `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` vrátí `true` Pokud dávku projekty jsou aktuálně načítání na pozadí, v opačném případě `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` vrátí `true` Pokud dávku projekty jsou aktuálně načítání synchronně jako výsledek příkazu uživatele nebo jiné explicitní zatížení, v opačném případě `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` vrátí `true` Pokud řešení aktuálně dochází k uzavření, jinak `false`.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` vrátí `true` Pokud řešení je právě otevřen, v opačném případě `false`.  
  
  Můžete také zajistit, že jsou načteny projekty a řešení (bez ohledu na to, co jsou priority zatížení projektu) voláním jedné z následujících metod:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: volání této metody vynutí projekty v řešení se načíst dříve, než metoda vrátí.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: volání této metody vynutí projekty v `guidProject` načíst dříve, než metoda vrátí.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: volání této metody vynutí projekt v `guidProjectID` načíst dříve, než metoda vrátí.  
  
> [!NOTE]
>  . Ve výchozím nastavení pouze projekty, které mají vyžádání načíst a byly načteny priority načítání na pozadí, ale pokud <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> příznak je předáno metodě, se načtou všechny projekty s výjimkou těch, které jsou označeny explicitně načíst.

