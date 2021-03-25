---
title: Seznam objektů okna vlastností | Microsoft Docs
description: Přečtěte si o rozhraních používaných k interakci se seznamem objektů v okno Vlastnosti v integrovaném vývojovém prostředí sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 489ea25e0b06ab69650d4b48a306483945b34598
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060975"
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
