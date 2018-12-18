---
title: 'Postupy: implementace vnořených projektů | Dokumentace Microsoftu'
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
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a392b8b336c57c47055357147075f29ba173d8f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810127"
---
# <a name="how-to-implement-nested-projects"></a>Postupy: implementace vnořených projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při vytváření jsou typu vnořený projekt existuje několik dalších kroků, které musí být implementován. Nadřazený projekt trvá u některých stejné odpovědnosti, které má řešení pro jeho vnořená projektů. Nadřazený projekt je kontejner, podobně jako řešení projektů. Konkrétně existují několik událostí, které musí být vyvolány řešení a nadřazené projektů k sestavení hierarchie vnořených projektů. Tyto události jsou popsány v následující proces pro vytváření vnořených projektů.  
  
### <a name="to-create-nested-projects"></a>Pokud chcete vytvářet vnořené projekty  
  
1. Integrované vývojové prostředí (IDE) načte informace o souboru a spuštění projektu nadřazený projekt voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> rozhraní. Nadřazený projekt je vytvořen a přidán do řešení.  
  
   > [!NOTE]
   >  V tomto okamžiku je příliš stará v procesu pro nadřazený projekt na vytvoření vnořený projekt, protože nadřazený projekt musí být vytvořen před vytvořením podřízené projekty. Toto pořadí nadřazeného projektu nastavení můžete použít podřízené projekty a podřízené projekty můžete získat informace z nadřazené projektů v případě potřeby. Toto pořadí je, pokud to není nutné provádět na klienty, jako je například Správa zdrojového kódu (SCC) a Průzkumník řešení.  
  
    Nadřazený projekt musí čekat <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metoda volána integrovaným vývojovým prostředím, před jeho vnořené (podřízené) je možné vytvořit projekt nebo projekty.  
  
2. Volání rozhraní IDE `QueryInterface` na nadřazený projekt pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Pokud toto volání bude úspěšné, volání integrovaného vývojového prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metoda nadřazeného prvku všech vnořených projektů pro nadřazený projekt otevřete.  
  
3. Volání nadřazený projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> metoda oznámit naslouchacích procesů, které vnořené projekty se chystáte vytvořit. SCC, například naslouchá na tyto události chcete vědět, pokud kroky v procesu vytváření řešení a projektu se vyskytují v pořadí. Pokud se objeví mimo pořadí kroků, řešení není registrován správně pomocí správy zdrojového kódu.  
  
4. Volání nadřazený projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> metoda nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metodu na každý z jeho podřízených projektů.  
  
    Můžete předat <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> k `AddVirtualProject` indikace, že by virtuální (vnořených) projekt přidán do projektu okna vyloučena ze sestavení, přidat do správy zdrojového kódu a tak dále. `VSADDVPFLAGS` umožňuje řídit viditelnost vnořený projekt a určit, jaké funkce jsou k ní přidružena.  
  
    Pokud načtete dříve existující podřízený projekt, který má projektu GUID, které jsou uloženy v souboru projektu nadřazený projekt, volání nadřazený projekt `AddVirtualProjectEx`. Jediným rozdílem mezi `AddVirtualProject` a `AddVirtualProjectEX` je, že `AddVirtualProjectEX` má parametr umožňující nadřazený projekt k určení na jednu instanci `guidProjectID` pro podřízený projekt umožňující <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> na funkci správně.  
  
    Pokud není žádný identifikátor GUID, například při přidání nového projektu vnořené řešení vytvoří pro projekt v době, kdy se přidá do nadřazené. Je odpovědností nadřazený projekt se zachovat tento projekt identifikátor GUID v jeho souboru projektu. Při odstranění vnořený projekt, můžete odstranit také identifikátor GUID pro daný projekt.  
  
5. Volání rozhraní IDE `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` metodu na každý podřízený projekt z nadřazeného projektu.  
  
    Nadřazený projekt musí implementovat `IVsParentProject` Pokud budete chtít vnořit projekty. Ale nadřazený projekt nikdy volání `QueryInterface` pro `IVsParentProject` i v případě, že má nadřazený projekty pod ním. Řešení zpracovává volání `IVsParentProject` a pokud je implementováno, zavolá `OpenChildren` vytvoření vnořených projektů. `AddVirtualProjectEX` je volána vždy z `OpenChildren`. To by nikdy volat žádný nadřazený projekt Zachovat hierarchii událostí vytváření v pořadí.  
  
6. Volání rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodu na podřízený projekt.  
  
7. Volání nadřazený projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> metoda oznámit naslouchacích procesů vytvořené podřízené projekty nadřazené.  
  
8. Volání rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metodu na nadřazený projekt po otevření všechny podřízené projekty.  
  
    Pokud ještě neexistuje, nadřazený projekt vytvoří identifikátor GUID pro každý projekt vnořené voláním `CoCreateGuid`.  
  
   > [!NOTE]
   >  `CoCreateGuid` je rozhraní API modelu COM volána, když se má vytvořit identifikátor GUID. Další informace najdete v tématu `CoCreateGuid` a identifikátory GUID v knihovně MSDN.  
  
    Nadřazený projekt ukládá tento identifikátor GUID v jeho souboru projektu, který se má načíst další čas, který je otevřen v integrovaném vývojovém prostředí. Přejděte ke kroku 4 pro další informace týkající se volání `AddVirtualProjectEX` načíst `guidProjectID` pro podřízený projekt.  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Metoda je volána poté nadřazené ItemID podle konvence delegovat v pro vnořený projekt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Načíst vlastnosti uzlu, který se vnoří projekt, který chcete delegovat v, když je volána v nadřazené.  
  
     Protože nadřazené a podřízené projekty jsou vytvořena prostřednictvím kódu programu, můžete nastavit vlastnosti pro vnořené projekty v tomto okamžiku.  
  
    > [!NOTE]
    >  Pouze dostáváte kontextové informace z vnořený projekt, ale můžete také požádat, pokud nadřazený projekt má jakýkoli kontext pro danou položku tak, že zkontrolujete <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. Tímto způsobem můžete přidat další atributy Dynamická nápověda a možnosti nabídky konkrétní jednotlivých vnořených projektů.  
  
10. V hierarchii je sestaven pro zobrazení v Průzkumníku řešení pomocí volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metody.  
  
     Předat hierarchii prostředí prostřednictvím `GetNestedHierarchy` k vytvoření hierarchie pro zobrazení v Průzkumníku řešení. Tímto způsobem řešení ví projektu existuje a je možné spravovat pomocí Správce sestavení pro sestavení nebo můžou soubory v projektu, které budou umístěny pod správou zdrojového kódu.  
  
11. Po vytvoření všech vnořených projektů pro Project1 řízení se předá zpět do řešení a proces se opakuje pro "project2".  
  
     Tento stejný proces pro vytváření vnořených projektů bude proveden pro podřízený projekt, který má podřízený element. V takovém případě pokud BuildProject1, který je podřízeným prvkem Project1 měli podřízené projekty, měly by být vytvořeny po BuildProject1 a před "project2". Tento proces je rekurzivní a hierarchii je sestavena shora dolů.  
  
     Pokud je vnořený projekt zavřít, protože uživatel zavřít řešení nebo konkrétní samotný projekt jiná metoda v `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, je volána. Nadřazený projekt zabaluje volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> metody oznámit naslouchacích procesů událostí řešení se zavírá vnořených projektů.  
  
    Následující témata se zabývají několik konceptů, které je třeba zvážit při implementaci vnořených projektů:  
  
    [Důležité informace pro uvolnění a opětovné načtení vnořených projektů](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
    [Podpora průvodce pro vnořené projekty](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
    [Implementace zpracování příkazů pro vnořené projekty](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
    [Filtrování dialogového okna Přidat položku pro vnořené projekty](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Viz také  
 [Přidávání položek do přidání nové položky v dialogových oknech](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

