---
title: Vypnutí omezení při naplňování datové sady | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667165"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Vypnutí omezení při naplňování datové sady
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud datová sada obsahuje omezení (například omezení cizího klíče), theycan vyvolá chyby související s pořadím operací, které jsou provedeny proti datové sadě. Například načtení podřízených záznamů před loadingrelated nadřazenými záznamy může narušovat omezení a způsobit chybu. Jakmile načtete podřízený záznam, omezení ověří související nadřazený záznam a vyvolá chybu.

 Pokud neexistuje žádný mechanismus, který by umožnil dočasné pozastavení omezení, při každém pokusu o načtení záznamu do podřízené tabulky se vyvolá chyba. Dalším způsobem, jak pozastavit všechna omezení v datové sadě, je pomocí <xref:System.Data.DataRow.BeginEdit%2A> a <xref:System.Data.DataRow.EndEdit%2A>ch vlastností.

> [!NOTE]
> Události ověřování (například <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging>) nebudou vyvolány, pokud jsou vypnuta omezení.

### <a name="to-suspend-update-constraints-programmatically"></a>Pozastavení omezení aktualizací prostřednictvím kódu programu

- Následující příklad ukazuje, jak dočasně vypnout kontrolu omezení pro datovou sadu:

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Pozastavení omezení aktualizací pomocí Návrhář datových sad

1. Otevřete datovou sadu v Návrhář datových sad. Další informace najdete v tématu [Postup: otevření datové sady v Návrhář datových sad](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. V okně **vlastnosti** nastavte vlastnost <xref:System.Data.DataSet.EnforceConstraints%2A> na hodnotu `false`.

## <a name="see-also"></a>Viz také
 [Vyplňování datových sad pomocí vztahů objekty TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md) [v datových sadách](../data-tools/relationships-in-datasets.md)
