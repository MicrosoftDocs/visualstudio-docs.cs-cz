---
title: Návrhář postupu provádění - Procházet a vybrat typ dialogovému oknu rozhraní .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 686969c233f50dd1df743590206966183be48da9
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513195"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Dialogové okno Procházet a vybrat typ .NET

V **vlastnosti** oken, dialogových oknech nebo návrháře, jako je například Návrhář proměnných, když vyberete **vyhledat typy** ze seznamu datových typů, je **Procházet a vybrat typ .NET** dialogové okno (uvedené ve zkrácené formě jako "typ prohlížeče"). V tomto dialogovém okně lze vybrat typ ze zobrazení stromové struktury projektů a sestavení.

Toto dialogové okno se použijí různými uživatelské scénáře, včetně následujících:

-   Při nastavování typu proměnné nebo argumentu.

-   Při výběru typu pro obecný aktivitu.

-   Při přidávání v bloku catch <xref:System.Activities.Statements.TryCatch> aktivity.

> [!NOTE]
> Typ prohlížeče můžete zobrazit typy jazyka Visual Basic Vícenásobná pole, ale není vícerozměrné pole typů. Zobrazit [Vícenásobná pole](http://go.microsoft.com/fwlink/?LinkId=195226) a [vícerozměrná pole](http://go.microsoft.com/fwlink/?LinkId=195227) podrobnosti.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Výběrem hodnoty nebo typ odkazu z typu prohlížeče

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Vyberte typ hodnoty nebo odkazu z typu prohlížeče

1.  V **název typu** zadejte název typu, který chcete použít.

2.  Proveďte jednu z těchto akcí:

    -   Jakmile se zobrazí název typu, který chcete použít ve stromu **název typu** pole, poklepejte na typ, vyberte ho.

    -   Zadejte dost znaků **název typu** pole k jednoznačné identifikaci typ, který chcete použít, a stiskněte klávesu enter vyberte typ

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Chcete-li vybrat obecného typu z typu prohlížeče

1.  V **název typu** pole, zadejte název typu, který chcete použít.

2.  Jakmile se zobrazí název typu, který chcete použít ve stromu **název typu** pole, klikněte na typ, který má vyberte ji a způsobit, že rozevírací seznamy se zobrazí.

     Vyberte typ, který chcete použít zavřete obecné z rozevíracího seznamu polí a potom klikněte na tlačítko **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Typy zobrazení v prohlížeči typu

Typy zobrazení v prohlížeči typu se může lišit v závislosti na tom, jak byl spuštěn prohlížeč typů. Pokud byl spuštěn prohlížeč typů z projektu pracovního postupu uvnitř **vs2010**, ve výchozím nastavení všechny typy v odkazovaných sestaveních a odkazované projekty se zobrazují. Pokud prohlížeč typů byl spuštěn ze mimo **vs2010** projektu systému (například jako v pracovním postupu provádění se změněným hostováním aplikací nebo samostatný soubor pracovního postupu), pak ve výchozím nastavení jsou uvedeny typy ze sestavení načtená v doméně aplikace .

Typy v prohlížeči typ by šlo filtrovat podle vývojáře návrháře aktivit. Pro danou aktivitu může se zobrazit pouze podmnožinu těchto typů. Například v <xref:System.Activities.Statements.TryCatch> aktivity, pouze typy odvozené z <xref:System.Exception> jsou zobrazená v prohlížeči typu.

## <a name="filtering-search-results-in-the-type-browser"></a>Filtrování výsledků hledání v prohlížeči typu

Seznam typů v **název typu** pole získá kratší při psaní více znaků pro vyhledání shody. Ve filtrovaném seznamu se zobrazí pouze typy, jejichž fullyqualified název začíná řetězcem, který jste zadali nebo jejichž krátký název začíná řetězcem, který jste zadali.

Příklad:

1.  Zadáním **operace** odpovídá <xref:System.OperationCanceledException> , ale ne <xref:System.InvalidOperationException>. Tak, aby odpovídaly <xref:System.InvalidOperationException>, začněte psát System.I nebo je neplatný.

2.  Zadáním **obecný** odpovídá <xref:System.GenericUriParser> , ale ne typy, které do <xref:System.Collections.Generic> oboru názvů. K vyhledání typů v <xref:System.Collections.Generic> obor názvů, zadejte plně kvalifikovaný název oboru názvů.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Výběr pomocí dialogového okna prohlížeče typ kontraktu služby

Když vyberete typ kontraktu služby, typu prohlížeče zobrazuje pouze typy, které mají <xref:System.ServiceModel.ServiceContractAttribute> atribut.

## <a name="see-also"></a>Viz také:

- [Používání návrhářů aktivit](../workflow-designer/using-the-activity-designers.md)