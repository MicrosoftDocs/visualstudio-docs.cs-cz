---
title: Seznam vlastností okna objekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6b7d238f7ce64122ac18a52dab59afb063ce47e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130133"
---
# <a name="properties-window-object-list"></a>Seznam objektů vlastnosti – okno
Seznam objektů v **vlastnosti** okno je rozevíracího seznamu, který vám umožní změnit výběr na další objekty, které jsou k dispozici v rámci jednoho nebo více vybraných windows. Vyberte jiný objekt z v tomto seznamu se aktivuje volání <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> k informování prostředí vybral nový objekt. Informace zobrazené v **vlastnosti** okno se poté změní na Zobrazit vlastnosti přidružené k nově vybraný objekt.  
  
## <a name="the-object-list"></a>Seznam objektů  
 Seznam objektů se skládá ze dvou polích: název objektu (zobrazená tučným písmem) a typ objektu.  
  
 Název objektu, který zobrazí nalevo od typu objektu tučným písmem se načítají ze samotného objektu pomocí `Name` vlastnost poskytované <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> rozhraní. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jedinou metodou na <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, vrátí <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> pro třída typu coclass tohoto rozhraní. **Vlastnosti** okno používá <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> získat název třída typu coclass, který se zobrazí jako název objektu v rozevíracím seznamu.  
  
 Pokud objekt nemá `Name` vlastnost, název se nezobrazí v oblasti název seznamu objektů. Vlastnost názvu můžete přidat k objektu, pokud chcete, aby název zobrazený v seznamu objektů.  
  
 Pokud objekt COM neimplementuje <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **vlastnosti** okně se zobrazí název rozhraní namísto názvu objekt na levé straně seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)