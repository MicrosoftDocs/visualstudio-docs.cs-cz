---
title: Implementace zpracování příkazů pro vnořené projekty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 628fde153441104e4bb504253d96235270b4b8fb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727085"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementace zpracování příkazů pro vnořené projekty
Rozhraní IDE může předat příkazy, které jsou předány pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní vnořeným projektům, nebo mohou nadřazené projekty filtrovat nebo přepsat příkazy.

> [!NOTE]
> Filtrovat lze pouze příkazy běžně zpracovávané nadřazeným projektem. Příkazy, jako je **sestavení** a **nasazení** , které jsou zpracovávány rozhraním IDE, nelze filtrovat.

 Následující kroky popisují proces implementace zpracování příkazů.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Implementace zpracování příkazů

1. Když uživatel vybere vnořený projekt nebo uzel ve vnořeném projektu:

   1. Rozhraní IDE volá metodu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>.

      ani

   2. Pokud příkaz vznikl v okně hierarchie, jako je například příkaz místní nabídky v Průzkumník řešení, rozhraní IDE volá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> na nadřazeném projektu.

2. Nadřazený projekt může prošetřit parametry, které mají být předány `QueryStatus`, například `pguidCmdGroup` a `prgCmds`, k určení, zda by měl nadřazený projekt filtrovat příkazy. Pokud je nadřazený projekt implementován pro filtrování příkazů, měl by být nastaven:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Pak by měl nadřazený projekt vracet `S_OK`.

    Pokud nadřazený projekt nefiltruje příkaz, měl by vracet pouze `S_OK`. V tomto případě rozhraní IDE automaticky směruje příkaz do podřízeného projektu.

    Nadřazený projekt není nutné směrovat příkaz do podřízeného projektu. Rozhraní IDE tuto úlohu provede..

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Vnoření projektů](../../extensibility/internals/nesting-projects.md)