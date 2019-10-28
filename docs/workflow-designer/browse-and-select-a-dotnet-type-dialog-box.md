---
title: Návrhář postupu provádění – procházení a výběr dialogového okna typu .NET
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2efea8f23e42b9f4839c8a1ae0d74248738b9cf4
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985355"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Dialogové okno Procházet a vybrat typ .NET

V okně **vlastnosti** , dialogová okna nebo návrháře, jako je například Návrhář proměnných, je po výběru možnosti **Vyhledat typy** ze seznamu datových typů zaškrtnuto políčko **Procházet a vybrat typ rozhraní .NET** (dále jen ve zkráceném tvaru jako typ). prohlížeč "). V tomto dialogovém okně můžete zvolit typ ze stromového zobrazení sestavení a projektů.

Toto dialogové okno se používá v řadě uživatelských scénářů, včetně následujících:

- Při nastavování typu proměnné nebo argumentu.

- Při výběru typu pro obecnou aktivitu.

- Při přidávání catch na aktivitu <xref:System.Activities.Statements.TryCatch>.

> [!NOTE]
> Prohlížeč typů se může zobrazit Visual Basic vícenásobné typy polí, ale ne typy multidimenzionálního pole. Podrobnosti najdete v tématu [vícenásobná pole](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) a [multidimenzionální pole](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) .

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Výběr hodnoty nebo typu odkazu z prohlížeče typu

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Výběr hodnoty nebo typu odkazu z prohlížeče typu

1. Do pole **název typu** zadejte název typu, který chcete použít.

2. Proveďte jednu z těchto akcí:

    - Jakmile se název typu, který chcete použít, zobrazí ve stromové struktuře v poli **název typu** , dvakrát klikněte na typ a vyberte ho.

    - Zadejte do pole **název typu** dostatek znaků k jedinečné identifikaci typu, který chcete použít, a potom stiskněte klávesu ENTER, aby se typ vybral.

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Výběr obecného typu z prohlížeče typu

1. Do pole **název typu** zadejte název typu, který chcete použít.

2. Jakmile je název typu, který chcete použít, zobrazen ve stromové struktuře v poli **název typu** , klikněte na možnost typ pro výběr, aby se zobrazily rozevírací seznamy.

     Vyberte typ, který chcete použít k zavření obecného v rozevíracích seznamech, a pak klikněte na **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Typy zobrazené v prohlížeči typů

Typy zobrazené v prohlížeči typů se mohou lišit v závislosti na tom, jak byl prohlížeč typu spuštěn. Pokud byl prohlížeč typu spuštěn z projektu pracovního postupu v rámci **VS2010**, zobrazí se ve výchozím nastavení všechny typy v odkazovaných sestaveních a odkazovaných projektech. Pokud se prohlížeč typů spustil mimo systém projektu **VS2010** (například v rámci hostitele aplikace pracovního postupu nebo v samostatném souboru pracovního postupu), pak se ve výchozím nastavení zobrazí typy ze všech sestavení načtených v doméně AppDomain.

Typy v prohlížeči typů lze filtrovat podle vývojářů návrháře aktivit. U jakékoli dané aktivity se může zobrazit pouze podmnožina typů. Například v aktivitě <xref:System.Activities.Statements.TryCatch> jsou v prohlížeči typu zobrazeny pouze typy odvozené od <xref:System.Exception>.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtrování výsledků hledání v prohlížeči typů

Seznam typů v poli **název typu** je kratší, než zadáte více znaků k vyhledání shody. Pouze typy, jejichž název FullyQualified začíná řetězcem, který jste zadali, nebo typy, jejichž krátký název začíná řetězcem, který jste zadali, se zobrazí v seznamu filtrovaný.

Příklad:

1. **Operace** zápisu odpovídá <xref:System.OperationCanceledException>, ale není <xref:System.InvalidOperationException>. Aby se shodovala s <xref:System.InvalidOperationException>, začněte psát System. I nebo invalid.

2. Zadání **obecných** shod <xref:System.GenericUriParser>, ale ne typů v oboru názvů <xref:System.Collections.Generic>. Chcete-li vyhledat typy v oboru názvů <xref:System.Collections.Generic>, zadejte plně kvalifikovaný název oboru názvů.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Výběr kontraktu služby pomocí dialogového okna typ prohlížeče

Při výběru typu kontraktu služby se v prohlížeči typů zobrazují pouze typy, které mají atribut <xref:System.ServiceModel.ServiceContractAttribute>.

## <a name="see-also"></a>Viz také:

- [Používání návrhářů aktivit](../workflow-designer/using-the-activity-designers.md)