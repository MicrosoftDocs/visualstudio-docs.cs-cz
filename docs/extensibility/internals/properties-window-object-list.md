---
title: Seznam objektů okna vlastností | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e50b3fe46edb8d14cad9a03a45bc8650cb9713ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725188"
---
# <a name="properties-window-object-list"></a>Seznam objektů okna Vlastnosti
Seznam objektů v okně **vlastnosti** je rozevírací seznam, který umožňuje změnit výběr na jiné objekty, které jsou k dispozici v rámci jedné nebo více vybraných oken. Výběr jiného objektu v rámci tohoto seznamu aktivuje volání <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> pro informování prostředí, že byl vybrán nový objekt. Informace zobrazené v okně **vlastnosti** se pak změní tak, aby se zobrazily vlastnosti přidružené k nově vybranému objektu.

## <a name="the-object-list"></a>Seznam objektů
 Seznam objektů se skládá ze dvou polí: název objektu (zobrazený tučně) a typ objektu.

 Název objektu zobrazený vlevo od typu objektu je tučně načten z objektu, který je uveden pomocí vlastnosti `Name` poskytované rozhraním <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A> jediná metoda na <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> vrací <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> pro třídu coclass daného rozhraní. Okno **vlastnosti** používá <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> k získání názvu coclass, který se zobrazí jako název objektu v rozevíracím seznamu.

 Pokud objekt nemá vlastnost `Name`, název se nezobrazí v oblasti název seznamu objektů. Chcete-li název zobrazit v seznamu objektů, lze do objektu přidat vlastnost Name.

 Pokud objekt COM neimplementuje <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, zobrazí se v okně **vlastnosti** název rozhraní místo názvu objektu na levé straně seznamu.

## <a name="see-also"></a>Viz také:
- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)