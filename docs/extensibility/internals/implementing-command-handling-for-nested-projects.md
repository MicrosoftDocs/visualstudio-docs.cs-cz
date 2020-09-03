---
title: Implementace zpracování příkazů pro vnořené projekty | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707597"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementace zpracování příkazů pro vnořené projekty
Rozhraní IDE může předat příkazy, které jsou předány prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a pro vnořené projekty, nebo nadřazené projekty mohou příkazy filtrovat nebo přepsat.

> [!NOTE]
> Filtrovat lze pouze příkazy běžně zpracovávané nadřazeným projektem. Příkazy, jako je **sestavení** a **nasazení** , které jsou zpracovávány rozhraním IDE, nelze filtrovat.

 Následující kroky popisují proces implementace zpracování příkazů.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Implementace zpracování příkazů

1. Když uživatel vybere vnořený projekt nebo uzel ve vnořeném projektu:

   1. Rozhraní IDE volá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu.

      ani

   2. Pokud příkaz vznikl v okně hierarchie, jako je například příkaz místní nabídky v Průzkumník řešení, rozhraní IDE volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metodu v nadřazeném projektu.

2. Nadřazený projekt může prošetřit parametry, které mají být předány `QueryStatus` , například `pguidCmdGroup` a `prgCmds` , aby bylo možné určit, zda nadřazený projekt má filtrovat příkazy. Pokud je nadřazený projekt implementován pro filtrování příkazů, měl by být nastaven:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Pak by měl nadřazený projekt vracet `S_OK` .

    Pokud nadřazený projekt nefiltruje příkaz, měl by se vrátit pouze `S_OK` . V tomto případě rozhraní IDE automaticky směruje příkaz do podřízeného projektu.

    Nadřazený projekt není nutné směrovat příkaz do podřízeného projektu. Rozhraní IDE tuto úlohu provede..

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Vnoření projektů](../../extensibility/internals/nesting-projects.md)
