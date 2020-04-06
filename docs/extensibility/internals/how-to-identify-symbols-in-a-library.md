---
title: 'Postup: Identifikace symbolů v knihovně | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708007"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Postup: Identifikace symbolů v knihovně
Nástroje pro procházení symbolů zobrazují hierarchické zobrazení symbolů. Symboly představují obory názvů, objekty, třídy, členy třídy a další prvky jazyka.

 Každý symbol v hierarchii lze identifikovat podle navigačních informací [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] předaných knihovnou symbolů správci objektů prostřednictvím následujících rozhraní:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Umístění symbolu v hierarchii odlišuje symbol. Umožňuje nástroje pro procházení symbolů pro navigaci na konkrétní symbol. Jedinečné, plně kvalifikované cesta ke symbolu určuje umístění. Každý prvek v cestě je uzel. Cesta začíná uzlovým uzětem nejvyšší úrovně a končí určitým symbolem. Například pokud M1 metoda je členem třídy C1 a C1 je v oboru názvů N1, úplná cesta M1 metoda je N1. C1. M1. Tato cesta obsahuje tři uzly: N1, C1 a M1.

 Navigační informace umožňují [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] správci objektů vyhledat, vybrat a zachovat vybrané symboly v hierarchii. Umožňuje navigaci z jednoho nástroje pro prohlížení do druhého. Při použití **prohlížeče objektů** k [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] procházení symbolů v projektu můžete klepnout pravým tlačítkem myši na metodu a spustit nástroj **Call Browser** a zobrazit metodu v grafu volání.

 Umístění symbolu popisují dva formuláře. Kanonický formulář je založen na plně kvalifikované cestě symbolu. Představuje jedinečnou pozici symbolu v hierarchii. Je nezávislý na nástroji pro prohlížení symbolů. Chcete-li získat informace o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kanonickém formuláři, správce objektů volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodu. Prezentační formulář popisuje umístění symbolu v rámci konkrétního nástroje pro procházení symbolů. Pozice symbolu je relativní vzhledem k umístění jiných symbolů v hierarchii. Daný symbol může mít několik cest prezentace, ale pouze jednu kanonické cesty. Pokud je například třída C1 zděděna z třídy C2 a obě třídy jsou v oboru názvů N1, **prohlížeč objektů** zobrazí následující hierarchický strom:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Kanonická cesta třídy C2 je v tomto příkladu N1 + C2. Prezentační cesta C2 obsahuje uzly C1 a "Základy a rozhraní": N1 + C1 + "Základy a rozhraní" + C2.

 Chcete-li získat informace o formuláři prezentace, správce objektů volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metodu.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Chcete-li získat informace o kanonických a prezentačních formulářích

1. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodu.

     Správce objektů volá tuto metodu k získání seznamu uzlů obsažených v kanonické cestě symbolu.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metodu.

     Správce objektů volá tuto metodu k získání seznamu uzlů obsažených v cestě prezentace symbolu.

## <a name="see-also"></a>Viz také
- [Podpora nástrojů pro procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Postup: Registrace knihovny u správce objektů](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Postup: Vystavit seznamy symbolů poskytovaných knihovnou správci objektů](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
