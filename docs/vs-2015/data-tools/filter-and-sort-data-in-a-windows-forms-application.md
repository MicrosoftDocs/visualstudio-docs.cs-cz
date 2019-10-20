---
title: Filtrování a řazení dat v model Windows Forms aplikaci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24c623efc141ff84c2585f967596271d1efbc502
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671646"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtrování a řazení dat ve formulářové aplikaci Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data filtrujete nastavením vlastnosti <xref:System.Windows.Forms.BindingSource.Filter%2A> na řetězcový výraz, který vrací požadované záznamy.

 Data seřadíte nastavením vlastnosti <xref:System.Windows.Forms.BindingSource.Sort%2A> na název sloupce, podle kterého chcete řadit; Přidejte `DESC` pro řazení v sestupném pořadí nebo přidejte `ASC` k řazení ve vzestupném pořadí.

> [!NOTE]
> Pokud vaše aplikace nepoužívá <xref:System.Windows.Forms.BindingSource> komponenty, můžete filtrovat a řadit data pomocí objektů <xref:System.Data.DataView>. Další informace naleznete v tématu [DataViews](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Filtrování dat pomocí komponenty BindingSource

- Vlastnost <xref:System.Windows.Forms.BindingSource.Filter%2A> nastavte na výraz, který chcete vrátit. Například následující kód vrátí zákazníky se `CompanyName`, který začíná "B":

     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Řazení dat pomocí komponenty BindingSource

- Vlastnost <xref:System.Windows.Forms.BindingSource.Sort%2A> nastavte na sloupec, podle kterého chcete řadit. Například následující kód seřadí zákazníky do sloupce `CompanyName` v sestupném pořadí:

     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
