---
title: 'Postup: Implementace vnořených projektů | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707974"
---
# <a name="how-to-implement-nested-projects"></a>Postup: Implementace vnořených projektů

Při vytváření vnořeného typu projektu existuje několik dalších kroků, které musí být implementovány. Nadřazený projekt přebírá některé stejné odpovědnosti, které má řešení pro své vnořené (podřízené) projekty. Nadřazený projekt je kontejner projektů podobný řešení. Zejména existuje několik událostí, které musí být vyvolány řešení a nadřazené projekty k vytvoření hierarchie vnořených projektů. Tyto události jsou popsány v následujícím procesu pro vytváření vnořených projektů.

## <a name="create-nested-projects"></a>Vytvoření vnořených projektů

1. Integrované vývojové prostředí (IDE) načte soubor projektu nadřazeného projektu a informace o spuštění voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> rozhraní. Nadřazený projekt je vytvořen a přidán do řešení.

    > [!NOTE]
    > V tomto okamžiku je příliš brzy v procesu pro nadřazený projekt k vytvoření vnořeného projektu, protože nadřazený projekt musí být vytvořen před vytvořením podřízených projektů. Po této sekvenci nadřazený projekt můžete použít nastavení podřízené projekty a podřízené projekty mohou získat informace z nadřazených projektů v případě potřeby. Tato sekvence je, pokud je potřeba na klienty, jako je například řízení zdrojového kódu (SCC) a **Průzkumník řešení**.

     Nadřazený projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> musí čekat na metodu, která má být volána ide před vytvořením jeho vnořený (podřízený) projekt nebo projekty.

2. Ide volá `QueryInterface` nadřazený projekt pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Pokud toto volání proběhne úspěšně, ide volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodu nadřazené otevřít všechny vnořené projekty pro nadřazený projekt.

3. Nadřazený <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> projekt volá metodu upozornit posluchače, že vnořené projekty se chystají vytvořit. SCC, například naslouchá těmto událostem, aby zjistil, zda kroky v procesu vytváření řešení a projektu probíhají v pořadí. Pokud dojde k krokům mimo pořadí, nemusí být řešení správně zaregistrováno s ovládacím prvkem zdrojového kódu.

4. Nadřazený projekt volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> metodu nebo metodu pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> každý z jeho podřízených projektů.

     Předáte <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> metodu `AddVirtualProject` k označení, že virtuální (vnořený) projekt by měl být přidán do okna projektu, vyloučen z sestavení, přidán do správy zdrojového kódu a tak dále. `VSADDVPFLAGS`umožňuje řídit viditelnost vnořeného projektu a označit, jaké funkce jsou k němu přidruženy.

     Pokud znovu načtete dříve existující podřízený projekt, který má identifikátor GUID projektu `AddVirtualProjectEx`uložený v souboru projektu nadřazeného projektu, volání nadřazeného projektu . Jediný rozdíl `AddVirtualProject` mezi `AddVirtualProjectEX` a `AddVirtualProjectEX` je, že má parametr povolit `guidProjectID` nadřazený <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> určit za instanci pro podřízený projekt povolit a správně fungovat.

     Pokud není k dispozici žádný identifikátor GUID, například při přidání nového vnořeného projektu, řešení vytvoří jeden pro projekt v době, kdy je přidán do nadřazeného projektu. Je odpovědností nadřazeného projektu zachovat tento identifikátor GUID projektu v souboru projektu. Pokud odstraníte vnořený projekt, guid pro tento projekt lze také odstranit.

5. IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> metodu pro každý podřízený projekt nadřazeného projektu.

     Nadřazený `IVsParentProject` projekt musí implementovat, pokud chcete vnořit projekty. Ale nadřazený `IVsParentProject` projekt nikdy volá, `QueryInterface` i když má nadřazené projekty pod ním. Řešení zpracovává volání `IVsParentProject` a pokud je implementováno, volání `OpenChildren` k vytvoření vnořené projekty. `AddVirtualProjectEX`je vždy `OpenChildren`volána z . Nadřazený projekt by nikdy neměl být volán, aby události vytváření hierarchie byly v pořádku.

6. IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodu v podřízeném projektu.

7. Nadřazený <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> projekt volá metodu upozornit posluchače, že byly vytvořeny podřízené projekty pro nadřazené.

8. IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metodu v nadřazeném projektu po otevření všech podřízených projektů.

     Pokud ještě neexistuje, nadřazený projekt vytvoří identifikátor GUID `CoCreateGuid`pro každý vnořený projekt voláním .

    > [!NOTE]
    > `CoCreateGuid`je rozhraní API com volané při vytvoření identifikátoru GUID. Další informace naleznete `CoCreateGuid` v tématu a identifikátory GUID v knihovně MSDN.

     Nadřazený projekt ukládá tento identifikátor GUID do souboru projektu, který má být načten při příštím otevření v rozhraní IDE. Další informace týkající se volání `AddVirtualProjectEX` pro podřízený `guidProjectID` projekt naleznete v kroku 4.

9. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> je pak volána pro nadřazené ItemID, které podle konvence delegovat v vnořeném projektu. Načte <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> vlastnosti uzlu, který vnoří projekt, který chcete delegovat v při volání na nadřazené.

     Vzhledem k tomu, že nadřazené a podřízené projekty jsou vytvořena instance programově, můžete v tomto okamžiku nastavit vlastnosti vnořených projektů.

    > [!NOTE]
    > Nejen, že obdržíte informace o kontextu z vnořeného projektu, ale můžete se také zeptat, zda má nadřazený projekt nějaký kontext pro tuto položku kontrolou [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). Tímto způsobem můžete přidat další dynamické atributy nápovědy a možnosti nabídky specifické pro jednotlivé vnořené projekty.

10. Hierarchie je vytvořena pro zobrazení v **Průzkumníku řešení** s voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metody.

     Předáte hierarchii do `GetNestedHierarchy` prostředí až k vytvoření hierarchie pro zobrazení v Průzkumníku řešení. Tímto způsobem řešení ví, že projekt existuje a může být spravován pro vytváření správcem sestavení nebo může povolit, aby soubory v projektu byly umístěny pod správou zdrojového kódu.

11. Po vytvoření všech vnořených projektů pro Project1 je ovládací prvek předán zpět do řešení a proces se opakuje pro Project2.

     Stejný proces pro vytváření vnořených projektů dochází pro podřízený projekt, který má podřízený. V tomto případě pokud BuildProject1, který je podřízený Project1, měl podřízené projekty, by byly vytvořeny po BuildProject1 a před Project2. Proces je rekurzivní a hierarchie je sestavena shora dolů.

     Pokud je vnořený projekt uzavřen, protože uživatel uzavřel řešení nebo `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>konkrétní samotný projekt, volá se jiná metoda v aplikaci . Nadřazený projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> zalomí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> metody s a metody upozornit posluchače na události řešení, které jsou uzavřeny vnořené projekty.

Následující témata se zabývají několika dalšími koncepty, které je třeba zvážit při implementaci vnořených projektů:

- [Důležité informace pro uvolnění a opětovné načtení vnořených projektů](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Podpora průvodce pro vnořené projekty](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementovat zpracování příkazů pro vnořené projekty](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrování dialogového okna Přidat položku pro vnořené projekty](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Viz také

- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Kontextové parametry](../../extensibility/internals/context-parameters.md)
- [Soubor Průvodce (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
