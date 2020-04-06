---
title: Implementace zpracování příkazů pro vnořené projekty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707597"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementace zpracování příkazů pro vnořené projekty
IDE můžete předat příkazy, které <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> jsou <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> předány prostřednictvím a rozhraní vnořené projekty nebo nadřazené projekty můžete filtrovat nebo přepsat příkazy.

> [!NOTE]
> Filtrovány lze pouze příkazy obvykle zpracované nadřazeným projektem. Příkazy, jako je **například sestavení** a **nasazení,** které jsou zpracovány ide nelze filtrovat.

 Následující kroky popisují proces implementace zpracování příkazů.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Implementace zpracování příkazů

1. Když uživatel vybere vnořený projekt nebo uzel v vnořený projekt:

   1. IDE volá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu.

      — nebo —

   2. Pokud příkaz pochází z okna hierarchie, jako je například příkaz místní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> nabídky v Průzkumníku řešení, ide volá metodu na nadřazeném projektu.

2. Nadřazený projekt může zkoumat `QueryStatus`parametry, které mají být předány , například `pguidCmdGroup` a `prgCmds`, k určení, zda nadřazený projekt má filtrovat příkazy. Pokud je nadřazený projekt implementován k filtrování příkazů, měl by nastavit:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Potom by měl `S_OK`být nadřazený projekt vrácen .

    Pokud nadřazený projekt nefiltruje `S_OK`příkaz, měl by pouze vrátit . V tomto případě ide automaticky směruje příkaz do podřízeného projektu.

    Nadřazený projekt nemusí směrovat příkaz do podřízeného projektu. IDE provádí tento úkol..

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Vnoření projektů](../../extensibility/internals/nesting-projects.md)
