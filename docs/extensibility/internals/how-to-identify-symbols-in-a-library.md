---
title: 'Postupy: identifikace symbolů v knihovně | Microsoft Docs'
description: Přečtěte si, jak identifikovat symboly v knihovně implementací metod, které přecházejí navigační informace z knihovny symbolů do Správce objektů sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b4e4c551c516b78ababb2400f7cfbd699ab06627
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932589"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Postupy: identifikace symbolů v knihovně
Nástroje pro procházení symbolů zobrazují hierarchická zobrazení symbolů. Symboly reprezentují obory názvů, objekty, třídy, členy třídy a další prvky jazyka.

 Každý symbol v hierarchii lze identifikovat pomocí navigační informace předané knihovnou symbolů do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Správce objektu prostřednictvím následujících rozhraní:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 Umístění symbolu v hierarchii rozlišuje symbol. Umožňuje nástrojům pro procházení symbolů přejít na konkrétní symbol. Jedinečná úplná cesta k symbolu určuje umístění. Každý prvek v cestě je uzel. Cesta začíná uzlem nejvyšší úrovně a končí pomocí konkrétního symbolu. Pokud je například Metoda M1 členem třídy C1 a C1 je v oboru názvů N1, úplná cesta k metodě M1 je N1. C1. Kategorie. Tato cesta obsahuje tři uzly: N1, C1 a M1.

 Navigační informace umožňuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] správci objektů najít, vybrat a zachovat vybrané symboly v hierarchii. Umožňuje navigaci z jednoho nástroje pro procházení na jiný. Při použití **Prohlížeč objektů** k procházení symbolů v [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektu můžete kliknout pravým tlačítkem myši na metodu a spustit nástroj **prohlížeč volání** pro zobrazení metody v grafu volání.

 Umístění symbolu popisují dva formuláře. Kanonický tvar je založen na plně kvalifikované cestě k symbolu. Představuje jedinečnou pozici symbolu v hierarchii. Nezávisle na nástroji pro procházení symbolů. Chcete-li získat informace o kanonickém formuláři, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Správce objektů volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodu. Formulář prezentace popisuje umístění symbolu v rámci určitého nástroje pro procházení symbolů. Pozice symbolu je relativní vzhledem k pozici jiných symbolů v hierarchii. Daný symbol může mít několik prezentačních cest, ale jenom jednu kanonickou cestu. Například pokud je třída C1 zděděna z třídy C2 a obě třídy jsou v oboru názvů N1, **Prohlížeč objektů** zobrazí následující hierarchický strom:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 Kanonická cesta třídy C2 v tomto příkladu je N1 + C2. Prezentační cesta C2 zahrnuje C1 a "základy a rozhraní" uzly: N1 + C1 + "základy a rozhraní" + C2.

 Chcete-li získat informace o prezentačním formuláři, volá správce objektů <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> metodu.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Získání informací o kanonických a prezentačních formulářích

1. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> metodu.

     Správce objektů volá tuto metodu, aby získala seznam uzlů obsažených v kanonické cestě k symbolu.

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

     Správce objektů volá tuto metodu, aby získala seznam uzlů obsažených v prezentační cestě k symbolu.

## <a name="see-also"></a>Viz také
- [Podpora nástrojů pro procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Postupy: registrace knihovny pomocí Správce objektů](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Postupy: vystavení seznamů symbolů poskytovaných knihovnou správci objektů](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
