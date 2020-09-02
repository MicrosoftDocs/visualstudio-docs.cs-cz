---
title: 'Postupy: implementace vnořených projektů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 427ef425c64323246ffe1141d081fd7d921506a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816195"
---
# <a name="how-to-implement-nested-projects"></a>Postupy: Implementace vnořených projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při vytváření vnořeného typu projektu je nutné implementovat několik dalších kroků. Nadřazený projekt přebírá některé ze stejných odpovědností, které má řešení pro své vnořené (podřízené) projekty. Nadřazený projekt je kontejner projektů podobných řešení. Konkrétně existuje několik událostí, které musí řešení a nadřazené projekty vyvolat pro sestavení hierarchie vnořených projektů. Tyto události jsou popsány v následujícím postupu pro vytváření vnořených projektů.  
  
### <a name="to-create-nested-projects"></a>Vytvoření vnořených projektů  
  
1. Integrované vývojové prostředí (IDE) načte soubor projektu nadřazené aplikace a spouštěcí informace voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> rozhraní. Nadřazený projekt je vytvořen a přidán do řešení.  
  
   > [!NOTE]
   > V tomto okamžiku je příliš brzy v procesu pro nadřazený projekt vytvořit vnořený projekt, protože nadřazený projekt musí být vytvořen před tím, než mohou být vytvořeny podřízené projekty. Po tomto pořadí může nadřízený projekt použít nastavení pro podřízené projekty a podřízené projekty mohou v případě potřeby získat informace z nadřazených projektů. Tato sekvence je, pokud je vyžaduje pro klienty, jako je například Správa zdrojového kódu (SCC) a Průzkumník řešení.  
  
    Nadřazený projekt musí počkat na <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> volání metody rozhraním IDE předtím, než může vytvořit svůj vnořený (podřízený) projekt nebo projekty.  
  
2. Rozhraní IDE zavolá `QueryInterface` v nadřazeném projektu pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Je-li toto volání úspěšné, rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodu nadřazeného objektu pro otevření všech vnořených projektů nadřazeného projektu.  
  
3. Nadřazený projekt volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> metodu pro upozornění posluchačů, že budou vytvořeny vnořené projekty. SCC například naslouchá těmto událostem, aby věděl, zda jsou v daném pořadí k dis kroky v procesu vytváření řešení a projektu. Pokud postup vyprší mimo pořadí, řešení nemusí být registrováno správně se správou zdrojového kódu.  
  
4. Nadřazený projekt volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> metodu nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metodu na každém z jejích podřízených projektů.  
  
    Předáte <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> `AddVirtualProject` metodě, která označuje, že virtuální (vnořený) projekt by měl být přidán do okna projektu, vyloučeno ze sestavení, přidáno do správy zdrojového kódu a tak dále. `VSADDVPFLAGS` umožňuje řídit viditelnost vnořeného projektu a označovat, k čemu jsou přidruženy funkce.  
  
    Pokud znovu načtete dříve existující podřízený projekt, který má identifikátor GUID projektu uložený v nadřazeném souboru projektu nadřazeného projektu, volání nadřazených projektů `AddVirtualProjectEx` . Jediný rozdíl mezi `AddVirtualProject` a `AddVirtualProjectEX` je, že `AddVirtualProjectEX` má parametr, který umožňuje nadřazenému projektu určit instanci `guidProjectID` pro podřízený projekt, aby bylo možné povolit <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> správně fungovat.  
  
    Pokud není k dispozici žádný identifikátor GUID, například když přidáte nový vnořený projekt, řešení vytvoří jeden pro projekt v době, kdy je přidán k nadřazenému. Je odpovědností nadřazeného projektu zachovat tento identifikátor GUID projektu v jeho souboru projektu. Odstraníte-li vnořený projekt, lze také odstranit identifikátor GUID tohoto projektu.  
  
5. Rozhraní IDE volá `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` metodu pro každý podřízený projekt nadřazeného projektu.  
  
    Nadřazený projekt musí být implementován, `IVsParentProject` Pokud chcete vnořit projekty. Nadřazený projekt ale nikdy nevolá `QueryInterface` , `IVsParentProject` i když má pod ním nadřazené projekty. Řešení zpracovává volání `IVsParentProject` a, pokud je implementováno, volání `OpenChildren` pro vytvoření vnořených projektů. `AddVirtualProjectEX` je vždy volána z `OpenChildren` . Nikdy by neměl být volán nadřazeným projektem, aby bylo možné zachovat události vytváření hierarchie v daném pořadí.  
  
6. Rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodu v podřízeném projektu.  
  
7. Nadřazený projekt volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> metodu pro oznámení posluchačům, že byly vytvořeny podřízené projekty pro nadřazený objekt.  
  
8. Rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metodu v nadřazeném projektu po otevření všech podřízených projektů.  
  
    Pokud ještě neexistuje, nadřazený projekt vytvoří identifikátor GUID pro každý vnořený projekt voláním `CoCreateGuid` .  
  
   > [!NOTE]
   > `CoCreateGuid` je volána rozhraní API modelu COM, když má být vytvořen identifikátor GUID. Další informace najdete v tématu `CoCreateGuid` a identifikátory GUID v knihovně MSDN.  
  
    Nadřazený projekt uloží tento identifikátor GUID do souboru projektu, který má být načten při příštím otevření v integrovaném vývojovém prostředí (IDE). Další informace týkající se volání metody `AddVirtualProjectEX` k načtení pro podřízený projekt naleznete v kroku 4 `guidProjectID` .  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Metoda je poté volána pro nadřazený identifikátor ItemId, který je podle konvence delegována do vnořeného projektu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Načte vlastnosti uzlu, který vnoření projekt, který chcete delegovat při volání na nadřazený objekt.  
  
     Vzhledem k tomu, že nadřazené a podřízené projekty jsou vytvořeny programově, můžete v tomto okamžiku nastavit vlastnosti pro vnořené projekty.  
  
    > [!NOTE]
    > Pouze z vnořeného projektu obdržíte pouze kontextové informace, ale můžete se také zeptat, zda má nadřazený projekt libovolný kontext pro tuto položku kontrolou <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> . Tímto způsobem můžete přidat další atributy dynamického pomocníka a možnosti nabídky specifické pro jednotlivé vnořené projekty.  
  
10. Hierarchie je vytvořena pro zobrazení v Průzkumník řešení s voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metody.  
  
     Hierarchii můžete do prostředí předat až po `GetNestedHierarchy` sestavení hierarchie pro zobrazení v Průzkumník řešení. Tímto způsobem řešení ví, že projekt existuje a lze jej spravovat pro sestavení správcem sestavení nebo může dovolit, aby byly soubory v projektu umístěny pod správu zdrojového kódu.  
  
11. Po vytvoření všech vnořených projektů pro Project1 se řízení předává zpět do řešení a proces se opakuje pro "Project2".  
  
     Stejný postup pro vytváření vnořených projektů nastane pro podřízený projekt, který má podřízenou položku. V tomto případě, pokud BuildProject1, která je podřízenou položkou Project1, měla podřízené projekty, budou vytvořeny po BuildProject1 a před "Project2". Proces je rekurzivní a hierarchie je sestavena shora dolů.  
  
     Když je vnořený projekt uzavřen, protože uživatel zavřel řešení nebo samotný projekt, je volána druhá metoda on `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> . Nadřazený projekt zalomí volání metody s metodami <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> k oznámení posluchačům pro události řešení, které jsou uzavřeny ve vnořených projektech.  
  
    Následující témata se týkají několika dalších konceptů, které je třeba vzít v úvahu při implementaci vnořených projektů:  
  
    [Důležité informace pro uvolnění a opětovné načtení vnořených projektů](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
    [Podpora průvodce pro vnořené projekty](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
    [Implementace zpracování příkazů pro vnořené projekty](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
    [Filtrování dialogového okna Přidat položku pro vnořené projekty](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Viz také  
 [Přidávání položek do dialogových oken Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Kontrolní seznam: vytváření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
