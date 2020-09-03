---
title: Vypnutí omezení při naplňování datové sady
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7bdb225a5b310f6f602619b2afcee610c3e9258b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281263"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Vypnutí omezení při naplňování datové sady

Pokud datová sada obsahuje omezení (například omezení cizího klíče), může vyvolávat chyby související s pořadím operací, které jsou provedeny na datové sadě. Například načtení podřízených záznamů před načtením souvisejících nadřazených záznamů může porušovat omezení a způsobit chybu. Jakmile načtete podřízený záznam, omezení ověří související nadřazený záznam a vyvolá chybu.

Pokud neexistuje žádný mechanismus, který by umožnil dočasné pozastavení omezení, při každém pokusu o načtení záznamu do podřízené tabulky se vyvolá chyba. Dalším způsobem, jak pozastavit všechna omezení v datové sadě, je pomocí <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> vlastností a.

> [!NOTE]
> Události ověřování (například <xref:System.Data.DataTable.ColumnChanging> a) nebudou <xref:System.Data.DataTable.RowChanging> vyvolány, pokud jsou vypnuta omezení.

## <a name="to-suspend-update-constraints-programmatically"></a>Pozastavení omezení aktualizací prostřednictvím kódu programu

- Následující příklad ukazuje, jak dočasně vypnout kontrolu omezení pro datovou sadu:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Pozastavení omezení aktualizací pomocí Návrhář datových sad

1. Otevřete datovou sadu v **Návrhář datových sad**. Další informace najdete v tématu [Návod: vytvoření datové sady v Návrhář datových sad](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. V okně **vlastnosti** nastavte <xref:System.Data.DataSet.EnforceConstraints%2A> vlastnost na hodnotu `false` .

## <a name="see-also"></a>Viz také

- [Vyplnění datových sad pomocí objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Relace v datových sadách](../data-tools/relationships-in-datasets.md)
