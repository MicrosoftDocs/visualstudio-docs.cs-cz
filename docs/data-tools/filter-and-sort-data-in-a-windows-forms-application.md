---
title: Filtrování a řazení dat ve formulářové aplikaci Windows
description: Filtrování a řazení dat v model Windows Forms aplikaci. Nastavte vlastnost Filter na řetězcový výraz, který vrací požadované záznamy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 045da0ade1ce60e2a8d21c24238c8e2b061e8612
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215822"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrování a řazení dat ve formulářové aplikaci Windows

Data filtrujete nastavením <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnosti na řetězcový výraz, který vrací požadované záznamy.

Data seřadíte nastavením <xref:System.Windows.Forms.BindingSource.Sort%2A> vlastnosti na název sloupce, ve kterém chcete řadit; připojit `DESC` se k řazení v sestupném pořadí nebo připojit `ASC` k seřazení ve vzestupném pořadí.

> [!NOTE]
> Pokud vaše aplikace nepoužívá <xref:System.Windows.Forms.BindingSource> komponenty, můžete filtrovat a řadit data pomocí <xref:System.Data.DataView> objektů. Další informace naleznete v tématu [DataViews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Filtrování dat pomocí komponenty BindingSource

- Nastavte <xref:System.Windows.Forms.BindingSource.Filter%2A> vlastnost na výraz, který chcete vrátit. Například následující kód vrátí zákazníky s `CompanyName` , který začíná "B":

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet6":::

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Řazení dat pomocí komponenty BindingSource

- Nastavte <xref:System.Windows.Forms.BindingSource.Sort%2A> vlastnost na sloupec, podle kterého chcete řadit. Například následující kód seřadí zákazníky se `CompanyName` sloupcem v sestupném pořadí:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
