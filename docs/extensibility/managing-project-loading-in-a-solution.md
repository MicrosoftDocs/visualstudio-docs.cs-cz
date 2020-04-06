---
title: Správa načítání projektu v řešení | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702723"
---
# <a name="manage-project-loading-in-a-solution"></a>Správa načítání projektu v řešení
Řešení sady Visual Studio mohou obsahovat velké množství projektů. Výchozí visual studio chování je načíst všechny projekty v řešení v době otevření řešení a nepovolit uživateli přístup k některé z projektů, dokud všechny z nich dokončilnačítání. Pokud proces načítání projektu bude trvat déle než dvě minuty, zobrazí se indikátor průběhu zobrazující počet načtených projektů a celkový počet projektů. Uživatel může uvolnit projekty při práci v řešení s více projekty, ale tento postup má některé nevýhody: uvolněné projekty nejsou vytvořeny jako součást příkazu znovu sestavit řešení a intelliSense popisy typů a členů uzavřených projektů nejsou zobrazeny.

 Vývojáři mohou zkrátit dobu načítání řešení a spravovat chování načítání projektu vytvořením správce zatížení řešení. Správce zatížení řešení můžete zajistit, že projekty jsou načteny před zahájením sestavení na pozadí, zpoždění načítání na pozadí, dokud ostatní úlohy na pozadí jsou dokončeny a provádět další úlohy řízení zatížení projektu.

## <a name="create-a-solution-load-manager"></a>Vytvoření správce zatížení řešení
 Vývojáři mohou vytvořit správce zatížení <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> řešení implementací a poradenstvím visual studio, že správce zatížení řešení je aktivní.

### <a name="activate-a-solution-load-manager"></a>Aktivace správce zatížení řešení
 Visual Studio umožňuje pouze jeden správce zatížení řešení v daném okamžiku, takže je nutné poradit Visual Studio, pokud chcete aktivovat správce zatížení řešení. Pokud je později aktivován druhý správce zatížení řešení, bude správce zatížení řešení odpojen.

 Musíte získat <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> službu a nastavit [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) vlastnost:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> je volána buď při vypnutí sady Visual Studio nebo při převzetí jiného <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> balíčku jako aktivnísprávce zatížení řešení voláním [s __VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) majetek.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie pro různé druhy správce zatížení řešení
 Můžete implementovat správce zatížení řešení různými způsoby, v závislosti na typech řešení, které jsou určeny ke správě.

 Pokud správce zatížení řešení je určen ke správě načítání řešení obecně, může být implementována jako součást VSPackage. Balíček by měl být nastaven <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> na automatické načtení přidáním <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>na VSPackage s hodnotou . Správce zatížení řešení pak může <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> být aktivován v metodě.

> [!NOTE]
> Další informace o automatickém načítání balíčků naleznete v [tématu Načítání balíčků VSPackages](../extensibility/loading-vspackages.md).

 Vzhledem k tomu, že Visual Studio rozpozná pouze poslední správce zatížení řešení, který má být aktivován, měli by správci zatížení obecného řešení vždy zjistit, zda existuje existující správce zatížení před samotnou aktivací. Pokud `GetProperty()` voláte službu řešení pro [__VSPROPID4. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`vrátí , neexistuje žádný aktivní správce zatížení řešení. Pokud nevrátí null, zkontrolujte, zda je objekt stejný jako správce zatížení řešení.

 Pokud správce zatížení řešení je určen ke správě pouze několik typů řešení, VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>můžete přihlásit k <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> odběru událostí zatížení řešení (voláním ) a použít obslužnou rutinu události pro aktivaci správce zatížení řešení.

 Pokud správce zatížení řešení je určen ke správě pouze konkrétní řešení, informace o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> aktivaci lze zachovat jako součást souboru řešení voláním části předběžné řešení.

 Konkrétní správci zatížení řešení by <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> se měli deaktivovat v obslužné rutině události, aby nedošlo ke konfliktu s jinými správci zatížení řešení.

 Pokud potřebujete správce zatížení řešení pouze k zachování vlastností globálního zatížení projektu (například vlastnosti nastavené <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> na stránce Možnosti), můžete aktivovat správce zatížení řešení v obslužné rutině události, zachovat nastavení ve vlastnostech řešení a poté deaktivovat správce zatížení řešení.

## <a name="handle-solution-load-events"></a>Zpracování událostí zatížení řešení
 Chcete-li se přihlásit <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> k odběru událostí načítání řešení, volejte při aktivaci správce zatížení řešení. Pokud implementujete <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, můžete reagovat na události, které se vztahují k různým vlastnostem načítání projektu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Tato událost je aktivována před otevřením řešení.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Tato událost je aktivována po úplném načtení řešení, ale před načtením projektu na pozadí začne znovu.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Tato událost je aktivována po řešení je zpočátku plně načten, zda je nebo není správce zatížení řešení. Je také aktivována po zatížení pozadí nebo zatížení poptávky vždy, když se řešení plně načte. Současně <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> je znovu aktivován.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Tato událost je aktivována před načtením projektu (nebo projektů). Chcete-li zajistit, že ostatní procesy na `pfShouldDelayLoadToNextIdle` pozadí jsou dokončeny před načtením projektů, nastavte na **hodnotu true**.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Tato událost je aktivována, když se má načíst dávka projektů. Pokud `fIsBackgroundIdleBatch` je true, projekty mají být načteny na pozadí; Pokud `fIsBackgroundIdleBatch` je false, projekty mají být načteny synchronně v důsledku požadavku uživatele, například pokud uživatel rozbalí čekající projekt v Průzkumníku řešení. Tuto událost můžete zpracovat tak, abyste provedli <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>nákladnou práci, kterou byste jinak museli provést v .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Tato událost je aktivována po načtení dávky projektů.

## <a name="detect-and-manage-solution-and-project-loading"></a>Zjišťování a správa řešení a načítání projektů
 Chcete-li zjistit stav zatížení projektů a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> řešení, volejte s následujícími hodnotami:

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` : `true` vrátí, pokud je načteno `false`řešení a všechny jeho projekty, jinak .

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` : `true` vrátí, pokud je dávka projektů právě načtena na pozadí, jinak `false`.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` : `true` vrátí, pokud je dávka projektů aktuálně načtena synchronně v důsledku uživatelského `false`příkazu nebo jiného explicitního zatížení, jinak .

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` : `true` vrátí, pokud je řešení `false`právě uzavřeno, jinak .

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` : `true` vrátí, pokud je řešení `false`právě otevíráno, jinak .

Můžete také zajistit, že projekty a řešení jsou načteny voláním jedné z následujících metod:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: volání této metody vynutí, aby se projekty v řešení načítalo před vrácením metody.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: volání této metody `guidProject` vynutí, aby se projekty načítalo před vrácením metody.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: volání této metody `guidProjectID` vynutí, aby se projekt načetl před vrácením metody.
