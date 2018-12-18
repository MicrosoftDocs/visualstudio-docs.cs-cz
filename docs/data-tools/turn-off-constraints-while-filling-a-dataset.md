---
title: Vypnutí omezení při naplňování datové sady
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d128216f84228c9cd4946f9a38c6c1b7845f92f1
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117235"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Vypnutí omezení při naplňování datové sady

Obsahuje-li datovou sadu omezení (například omezení cizího klíče), může být spojeno chyby související pracovního operace, které jsou provedeny s datovou sadu. Například načítání podřízené záznamy před načtením související nadřazené záznamy můžete porušení omezení a způsobit chybu. Při načítání na podřízený záznam, omezení kontroluje související nadřazený záznam a vyvolá chybu.

Kdyby existovalo žádný mechanismus pro povolit omezení pro dočasné pozastavení, by pokaždé, když jste se pokusili načíst záznamu do tabulky podřízené vyvolána chyba. Je také možné pozastavit všechna omezení v datové sadě s <xref:System.Data.DataRow.BeginEdit%2A>, a <xref:System.Data.DataRow.EndEdit%2A> vlastnosti.

> [!NOTE]
> Události ověření (například <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.RowChanging>) nebude se vyvolá, když jsou vypnuté omezení.

## <a name="to-suspend-update-constraints-programmatically"></a>Pozastavení omezení aktualizace prostřednictvím kódu programu

-   Následující příklad ukazuje, jak chcete dočasně vypnout kontrolu v datové sadě omezení:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Pozastavení omezení aktualizace pomocí návrháře Dataset

1.  Otevřete datovou sadu v **návrháře Dataset**. Další informace najdete v tématu [návod: vytvoření datové sady v Návrháři Dataset](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  V **vlastnosti** nastavte <xref:System.Data.DataSet.EnforceConstraints%2A> vlastnost `false`.

## <a name="see-also"></a>Viz také:

- [Vyplnění datové sady s použitím objektů TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Vztahy v datových sadách](../data-tools/relationships-in-datasets.md)