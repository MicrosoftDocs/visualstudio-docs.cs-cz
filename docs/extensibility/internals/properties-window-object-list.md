---
title: Seznam objektů okna vlastností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706152"
---
# <a name="properties-window-object-list"></a>Seznam objektů okna Vlastnosti
Seznam objektů v okně **Vlastnosti** je rozevírací seznam, který umožňuje změnit výběr na jiné objekty dostupné v jednom nebo více vybraných oknech. Výběr jiného objektu z tohoto seznamu <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> spustí volání informovat prostředí, že byl vybrán nový objekt. Informace zobrazené v okně **Vlastnosti** se pak změní tak, aby zobrazovaly vlastnosti přidružené k nově vybranému objektu.

## <a name="the-object-list"></a>Seznam objektů
 Seznam objektů se skládá ze dvou polí: názvu objektu (zobrazeného tučně) a typu objektu.

 Název objektu zobrazený nalevo od typu objektu tučně je `Name` načten ze <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> samotného objektu pomocí vlastnosti poskytované rozhraním. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jedinou <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>metodou <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> na , vrátí pro toto rozhraní coclass. Okno **Vlastnosti** používá <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> k získání názvu coclass, který se zobrazí jako název objektu v rozevíracím seznamu.

 Pokud objekt nemá `Name` vlastnost, název se nezobrazí v oblasti Název seznamu objektů. Pokud chcete, aby se název zobrazoval v seznamu objektů, můžete k objektu přidat vlastnost Name.

 Pokud se objekt COM <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>neimplementuje , zobrazí se v okně **Vlastnosti** název rozhraní namísto názvu objektu na levé straně seznamu.

## <a name="see-also"></a>Viz také
- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
