---
title: Správa akcí zpět a znovu pomocí starší verze rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194361"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Správa příkazů Zpět a Znovu pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editory musí podporovat operace vrácení zpět, které umožní uživatelům vrátit poslední změny při úpravách kódu. Většina editorů implementovaných v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] může mít podporu pro vrácení zpět automaticky poskytovanou integrovaným vývojovým prostředím (IDE).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Implementace správy příkazu Zpět](../extensibility/how-to-implement-undo-management.md)  
 Poskytuje možnost zrušení pro editory s jedním nebo více zobrazeními.  
  
 [Postupy: Vymazání zásobníku příkazu Zpět](../extensibility/how-to-clear-the-undo-stack.md)  
 Popisuje, jak vymazat zásobník pro vrácení zpět.  
  
 [Postupy: Použití správy propojeného příkazu Zpět](../extensibility/how-to-use-linked-undo-management.md)  
 Zahrnuje propojenou správu zpět do editoru.  
  
## <a name="reference"></a>Referenční informace  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Poskytuje správu zpět pro Editor, který podporuje více zobrazení.  
  
## <a name="related-sections"></a>Související oddíly
