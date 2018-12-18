---
title: Filtrování a řazení dat ve formulářové aplikaci Windows
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1868d670458e204f6e503b132aaceab17f3da742
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750920"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrování a řazení dat ve formulářové aplikaci Windows

Filtrování dat tím, že nastavíte <xref:System.Windows.Forms.BindingSource.Filter%2A> řetězcového výrazu, které vrací záznamy požadovanou vlastnost.

Řazení dat tím, že nastavíte <xref:System.Windows.Forms.BindingSource.Sort%2A> vlastnost názvu sloupce, na kterém jste mohli takto řadit; připojit `DESC` seřadit v sestupném pořadí, nebo připojit `ASC` seřadit v vzestupném pořadí.

> [!NOTE]
> Pokud vaše aplikace nepoužívá <xref:System.Windows.Forms.BindingSource> součásti, můžete filtrovat a řadit data s využitím <xref:System.Data.DataView> objekty. Další informace najdete v tématu [zobrazení dat](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>K filtrování dat pomocí komponenty BindingSource

-   Nastavte <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnost na výraz, který chcete vrátit. Například následující kód vrátí zákazníkům `CompanyName` , který začíná písmenem "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Řazení dat s použitím komponenty BindingSource

-   Nastavte <xref:System.Windows.Forms.BindingSource.Sort%2A> vlastnost do sloupce, které chcete řadit. Například následující kód se seřadí zákazníci `CompanyName` sloupec v sestupném pořadí:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)