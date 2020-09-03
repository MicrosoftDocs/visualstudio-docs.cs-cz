---
title: Seznam objektů okna vlastností | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706152"
---
# <a name="properties-window-object-list"></a>Seznam objektů okna Vlastnosti
Seznam objektů v okně **vlastnosti** je rozevírací seznam, který umožňuje změnit výběr na jiné objekty, které jsou k dispozici v rámci jedné nebo více vybraných oken. Výběr jiného objektu v rámci tohoto seznamu aktivuje volání pro <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> informování prostředí, že byl vybrán nový objekt. Informace zobrazené v okně **vlastnosti** se pak změní tak, aby se zobrazily vlastnosti přidružené k nově vybranému objektu.

## <a name="the-object-list"></a>Seznam objektů
 Seznam objektů se skládá ze dvou polí: název objektu (zobrazený tučně) a typ objektu.

 Název objektu zobrazený vlevo od typu objektu je tučně načten z objektu, který je `Name` uveden pomocí vlastnosti poskytované <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> rozhraním. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jediná metoda v <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , se vrátí <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> pro třídu coclass daného rozhraní. Okno **vlastnosti** používá <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> k získání názvu coclass, který se zobrazí jako název objektu v rozevíracím seznamu.

 Pokud objekt neobsahuje `Name` vlastnost, není zobrazen název v oblasti název seznamu objektů. Chcete-li název zobrazit v seznamu objektů, lze do objektu přidat vlastnost Name.

 Pokud objekt modelu COM neimplementuje <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , zobrazí se v okně **vlastnosti** název rozhraní místo názvu objektu na levé straně seznamu.

## <a name="see-also"></a>Viz také
- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
