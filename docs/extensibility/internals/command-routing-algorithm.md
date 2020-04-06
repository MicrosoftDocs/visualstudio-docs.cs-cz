---
title: Algoritmus směrování příkazů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709539"
---
# <a name="command-routing-algorithm"></a>Algoritmus směrování příkazů
V sadě Visual Studio příkazy jsou zpracovány řadou různých součástí. Příkazy jsou směrovány z nejvnitřnějšího kontextu, který je založen na aktuálním výběru, do nejvzdálenějšího (označovaného také jako globální) kontextu. Další informace naleznete v [tématu Dostupnost příkazu](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Pořadí rozlišení příkazu
 Příkazy jsou předávány prostřednictvím následujících úrovní kontextu příkazu:

1. Doplňky: Prostředí nejprve nabízí příkaz pro všechny doplňky, které jsou k dispozici.

2. Příkazy priority: Tyto příkazy <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>jsou registrovány pomocí . Jsou volány pro každý příkaz v sadě Visual Studio a jsou volány v pořadí, ve kterém byly zaregistrovány.

3. Příkazy kontextové nabídky: Příkaz umístěný v místní nabídce je nejprve nabídnut cíli příkazu, který je k dispozici v místní nabídce, a poté k typickému směrování.

4. Panel nástrojů nastavit cíle příkazů: Tyto cíle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>příkazu jsou registrovány při volání . Parametr `pCmdTarget` může `null`být . Pokud tomu `null`tak není , pak se tento cíl příkazu používá k aktualizaci všech příkazů umístěných na panelu nástrojů, který nastavujete. Pokud prostředí nastavuje panel nástrojů, předává rámeček `pCmdTarget` okna tak, aby všechny aktualizace příkazů na panelu nástrojů procházely rámečkem okna, i když není zaostřený.

5. Okno nástroje: Okna nástrojů, která <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> obvykle implementují <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, by měla také implementovat rozhraní tak, aby visual studio může získat cíl příkazu, když je aktivní okno nástroje. Pokud je však okno nástroje, které má fokus, okno <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> **Projektu,** je příkaz směrován do rozhraní, které je společným nadřazeným objektem vybraných položek. Pokud tento výběr zahrnuje více projektů, příkaz je <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> směrován do hierarchie. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> obsahuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> a, které jsou obdobné odpovídající <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> příkazy na rozhraní.

6. Okno dokumentu: Pokud má `RouteToDocs` příkaz ve svém souboru *.vsct* nastavený příznak, aplikace Visual Studio hledá cíl <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> příkazu v objektu zobrazení dokumentu, což je instance rozhraní nebo instance objektu dokumentu (obvykle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> rozhraní nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> rozhraní). Pokud objekt zobrazení dokumentu nepodporuje příkaz, Visual Studio směruje příkaz do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, které je vráceno. (Toto je volitelné rozhraní pro objekty dat dokumentu.)

7. Aktuální hierarchie: Aktuální hierarchie může být projekt, který vlastní okno aktivního dokumentu nebo hierarchii vybranou v **Průzkumníku řešení**. Visual Studio hledá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, které je implementováno v aktuální nebo aktivní hierarchii. Hierarchie by měla podporovat příkazy, které jsou platné vždy, když je hierarchie aktivní, i když okno dokumentu položky projektu má fokus. Příkazy, které platí pouze v případě, **že průzkumník řešení** má fokus musí být podporovány pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> rozhraní a jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metody.

     **Příkazy Vyjmout**, **Kopírovat**, **Vložit,** **Odstranit,** **Přejmenovat**, **Zadat**a **DoubleClick** vyžadují zvláštní zpracování. Informace o tom, jak **zpracovat** příkazy Odstranit <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> a **odebrat** v hierarchiích, naleznete v rozhraní.

8. Globální: Pokud příkaz nebyl zpracován výše uvedené kontexty, Visual Studio pokusí směrovat do VSPackage, který vlastní <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> příkaz, který implementuje rozhraní. Pokud VSPackage nebyla načtena již, není načten při <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Visual Studio volá metodu. VSPackage je načten pouze <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> v případě, že je volána metoda.

## <a name="see-also"></a>Viz také
- [Návrh příkazu](../../extensibility/internals/command-design.md)
