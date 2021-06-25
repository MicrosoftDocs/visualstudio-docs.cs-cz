---
title: Implementace zpracování příkazů pro vnořené projekty | Microsoft Docs
description: Naučte se implementovat zpracování příkazů pro vnořené projekty v integrovaném vývojovém Visual Studio (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4324e207d7b424295137f9523ed0bed538b3d806
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899983"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Implementace zpracování příkazů pro vnořené projekty
Integrované vývojové prostředí (IDE) může předávat příkazy, které jsou předány prostřednictvím rozhraní a vnořeným projektům, nebo nadřazené projekty mohou příkazy filtrovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> nebo přepisovat.

> [!NOTE]
> Filtrovat je možné pouze příkazy obvykle zpracované nadřazeným projektem. Příkazy, jako **je sestavení** a **nasazení,** které zpracovává integrované vývojové prostředí (IDE), není možné filtrovat.

 Následující kroky popisují proces implementace zpracování příkazů.

## <a name="procedures"></a>Procedury

#### <a name="to-implement-command-handling"></a>Implementace zpracování příkazů

1. Když uživatel vybere vnořený projekt nebo uzel ve vnořeném projektu:

   1. Integrované vývojové prostředí (IDE) volá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu .

      — or —

   2. Pokud příkaz vznikl v okně hierarchie, například příkaz místní nabídky v Průzkumník řešení, volá integrované vývojové prostředí metodu v <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> nadřazeném projektu.

2. Nadřazený projekt může prozkoumat parametry, které se mají předat do , jako je a , a určit, jestli má nadřazený `QueryStatus` `pguidCmdGroup` projekt filtrovat `prgCmds` příkazy. Pokud je nadřazený projekt implementován pro filtrování příkazů, měl by nastavit:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Potom by nadřazený projekt měl vrátit `S_OK` .

    Pokud nadřazený projekt příkaz nefiltruje, měl by vrátit hodnotu `S_OK` . V takovém případě integrované vývojové prostředí (IDE) automaticky směruje příkaz do podřízeného projektu.

    Nadřazený projekt nemusí směrovat příkaz na podřízený projekt. Integrované vývojové prostředí (IDE) provádí tuto úlohu..

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Příkazy, nabídky a panely nástrojů](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Vnoření projektů](../../extensibility/internals/nesting-projects.md)
