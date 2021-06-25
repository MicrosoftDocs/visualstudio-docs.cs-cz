---
title: Seznam objektů okna Vlastnosti | Microsoft Docs
description: Seznamte se s rozhraními používanými k interakci se seznamem objektů v okno Vlastnosti v Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 908acf3f8ecad390266c3d085778dc13077a6fa8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903434"
---
# <a name="properties-window-object-list"></a>Seznam objektů okna Vlastnosti
Seznam objektů v okně **Vlastnosti** je rozevírací seznam, který umožňuje změnit výběr na jiné objekty dostupné v jednom nebo více vybraných oknech. Výběrem jiného objektu v tomto seznamu se aktivuje volání , které informuje prostředí, že byl vybrán <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> nový objekt. Informace zobrazené v okně **Vlastnosti** se pak změní tak, aby se zobrazují vlastnosti přidružené k nově vybranému objektu.

## <a name="the-object-list"></a>Seznam objektů
 Seznam objektů se skládá ze dvou polí: názvu objektu (zobrazeného tučně) a typu objektu.

 Název objektu zobrazený tučně nalevo od typu objektu se načte z samotného objektu pomocí vlastnosti `Name` poskytované <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> rozhraním. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jediná metoda pro vrátí pro třídu <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> typu coclass tohoto rozhraní. Okno **Vlastnosti** používá k získání názvu třídy typu coclass, který se zobrazí jako název objektu <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> v rozevíracím seznamu.

 Pokud objekt nemá vlastnost , název se nezobrazí v `Name` oblasti Název seznamu objektů. Pokud chcete název zobrazit v seznamu objektů, můžete k objektu přidat vlastnost Name.

 Pokud objekt COM neimplementuje , zobrazí okno Vlastnosti místo názvu objektu na levé straně <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> seznamu název rozhraní. 

## <a name="see-also"></a>Viz také
- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
