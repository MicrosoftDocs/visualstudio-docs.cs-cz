---
title: Správa načítání projektů v řešení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702723"
---
# <a name="manage-project-loading-in-a-solution"></a>Správa načítání projektů v řešení
Řešení sady Visual Studio můžou obsahovat velký počet projektů. Výchozím chováním sady Visual Studio je načíst všechny projekty v řešení v době, kdy je řešení otevřeno, a nedovolit uživateli přístup k jakémukoli z projektů, dokud se všechny z nich nedokončí. Pokud bude proces načítání projektu poslední více než dvě minuty, zobrazí se indikátor průběhu znázorňující počet načtených projektů a celkový počet projektů. Uživatel může uvolnit projekty při práci v řešení s více projekty, ale tento postup má některé nevýhody: Nenačtené projekty nejsou sestaveny jako součást příkazu znovu sestavit řešení a popisy IntelliSense typů a členů uzavřených projektů nejsou zobrazeny.

 Vývojáři můžou snížit dobu načítání řešení a spravovat chování při načítání projektů vytvořením správce načtení řešení. Správce načtení řešení může zajistit, aby byly před spuštěním sestavení na pozadí načteny projekty, aby bylo zpožděno načítání na pozadí, dokud nebudou dokončeny jiné úlohy na pozadí, a provádět další úlohy správy zatížení projektu.

## <a name="create-a-solution-load-manager"></a>Vytvoření správce zatížení řešení
 Vývojáři mohou vytvořit správce načtení řešení implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> a poradenstvím sady Visual Studio, že je správce zatížení řešení aktivní.

### <a name="activate-a-solution-load-manager"></a>Aktivace správce zatížení řešení
 Visual Studio umožňuje v daný okamžik pouze jednoho správce načtení řešení, takže je nutné poradit se systémem Visual Studio, pokud chcete aktivovat správce zatížení řešení. Pokud se později aktivuje druhý správce načtení řešení, váš správce zatížení řešení se odpojí.

 Musíte získat <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> službu a nastavit [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) vlastnost:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>Metoda je volána buď při vypnutí sady Visual Studio, nebo v případě, že byl jiný balíček převzat jako aktivní správce načtení řešení voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> [__VSPROPID4. Vlastnost VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) .

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie pro různé druhy správce načtení řešení
 Správce načítání řešení můžete implementovat různými způsoby v závislosti na typech řešení, která jsou určena ke správě.

 Je-li správce načtení řešení určen ke správě obecného načítání řešení, je možné jej implementovat jako součást VSPackage. Balíček by měl být nastaven na AUTOLOAD přidáním na <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> VSPackage s hodnotou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . V metodě se pak dá aktivovat správce načtení řešení <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

> [!NOTE]
> Další informace o automatickém načítání balíčků naleznete v tématu [načítání VSPackage](../extensibility/loading-vspackages.md).

 Vzhledem k tomu, že aplikace Visual Studio rozpozná pouze posledního správce načtení řešení, který má být aktivován, by měli správci načtení obecných řešení vždycky zjistit, zda existoval správce zatížení před aktivací. Při volání `GetProperty()` služby řešení pro [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) vrací `null` neaktivního správce načtení řešení. Pokud nevrátí hodnotu null, ověřte, zda je objekt stejný jako váš správce zatížení řešení.

 Pokud má správce zatížení řešení spravovat pouze několik typů řešení, VSPackage se může přihlásit k odběru událostí načtení řešení (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> ) a použít obslužnou rutinu události pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> aktivaci správce načtení řešení.

 Pokud má správce zatížení řešení spravovat pouze konkrétní řešení, mohou být aktivační informace uchovány jako součást souboru řešení voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> pro oddíl pre-Solution.

 Konkrétní správci načtení řešení by se měli v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> obslužné rutině události deaktivovat, aby nedocházelo ke konfliktům s jinými správci načtení řešení.

 Pokud potřebujete správce načtení řešení pouze pro zachování globálních vlastností načtení projektu (například vlastnosti nastavené na stránce Možnosti), můžete aktivovat správce načtení řešení v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> obslužné rutině události, zachovat nastavení ve vlastnostech řešení a pak deaktivovat správce načtení řešení.

## <a name="handle-solution-load-events"></a>Zpracování událostí načtení řešení
 Chcete-li se přihlásit k odběru událostí načtení řešení, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> při aktivaci správce zatížení řešení. Pokud implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> , můžete reagovat na události, které se vztahují k různým vlastnostem načítání projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Tato událost je aktivována před otevřením řešení.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Tato událost je aktivována po úplném načtení řešení, ale před začátkem nasazování projektu na pozadí.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Tato událost je aktivována po prvním úplném načtení řešení, bez ohledu na to, zda existuje správce načtení řešení. Je také aktivována po načtení nebo zatížení na pozadí, kdykoli se řešení úplně načte. V současné době <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> se znovu aktivuje.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Tato událost je aktivována před načtením projektu (nebo projektů). Aby bylo zajištěno, že před načtením projektů byly dokončeny další procesy na pozadí, nastavte `pfShouldDelayLoadToNextIdle` na **hodnotu true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Tato událost se aktivuje, když se bude načítat dávka projektů. Pokud `fIsBackgroundIdleBatch` je hodnota true, projekty budou načteny na pozadí. Pokud je hodnota `fIsBackgroundIdleBatch` false, projekty mají být načteny synchronně jako výsledek požadavku uživatele, například pokud uživatel rozbalí nedokončený projekt v Průzkumník řešení. Tuto událost můžete zpracovat tak, aby provedla náročnou práci, kterou by jinak bylo nutné provést v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Tato událost je aktivována po načtení dávky projektů.

## <a name="detect-and-manage-solution-and-project-loading"></a>Detekovat a spravovat řešení a načítání projektů
 Aby bylo možné zjistit stav zatížení projektů a řešení, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> následující hodnoty:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` vrátí `true` , zda je řešení a všechny jeho projekty načteno, jinak `false` .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` vrátí `true` , zda je dávka projektů v současné době načítána na pozadí, jinak `false` .

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` vrátí `true` , zda je dávka projektů v současné době načítána synchronně v důsledku uživatelského příkazu nebo jiného explicitního zatížení, jinak `false` .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` vrátí `true` , zda je řešení momentálně uzavřeno, jinak `false` .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` vrátí `true` , zda je aktuálně otevřeno řešení, jinak `false` .

Můžete také zajistit, aby byly projekty a řešení načteny voláním jedné z následujících metod:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: volání této metody vynutí, aby se projekty v řešení načetly předtím, než se metoda vrátí.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: volání této metody vynutí, aby se projekty `guidProject` načetly předtím, než se metoda vrátí.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: volání této metody vynutí, aby byl projekt `guidProjectID` načten před vrácením metody.
