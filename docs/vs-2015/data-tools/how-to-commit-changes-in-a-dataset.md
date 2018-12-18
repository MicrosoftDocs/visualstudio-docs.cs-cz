---
title: 'Postupy: potvrzení změn v datové sadě | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataSet.AcceptChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], committing changes
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 41d27c248763f42db6543db0a9b4e56e4c4eac82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276429"
---
# <a name="how-to-commit-changes-in-a-dataset"></a>Postupy: Potvrzení změn v datové sadě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při provádění změn záznamů v datové sadě aktualizací, vkládání a odstranění záznamů, datové sady udržuje aktuální a původní verzí záznamů. Kromě toho každý řádek v <xref:System.Data.DataRow.RowState%2A> uchovává informace o vlastnosti, zda záznamy jsou v jejich původním stavu nebo byly aktualizovány, vložit nebo odstranit. Tyto informace jsou užitečné, když je potřeba k vyhledání konkrétní verze řádku. Obvykle byste získali podmnožinu všechny změněné záznamy k odeslání na jiný proces. Další informace najdete v tématu [postupy: načtení změnil řádků](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9). Po zpracování všech změněných řádků je změny potvrdit voláním `AcceptChanges` metodu <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow>. `AcceptChanges` Metoda je volána automaticky při volání metod aktualizace [TableAdapter](../data-tools/tableadapter-overview.md) nebo datový adaptér. Volání `AcceptChanges` po odeslání změn do databáze.  
  
 Při volání <xref:System.Data.DataSet.AcceptChanges%2A> na <xref:System.Data.DataSet>, jakékoli <xref:System.Data.DataRow> objekty stále v režimu úprav úspěšně ukončit jejich úpravy. <xref:System.Data.DataRow.RowState%2A> Vlastnosti každého <xref:System.Data.DataRow> také změní; <xref:System.Data.DataRowState> a <xref:System.Data.DataRowState> řádky budou <xref:System.Data.DataRowState>, a <xref:System.Data.DataRowState> řádky se odeberou.  
  
 Pokud <xref:System.Data.DataSet> obsahuje <xref:System.Data.ForeignKeyConstraint> objekty, volání <xref:System.Data.DataSet.AcceptChanges%2A> metoda také způsobí, že <xref:System.Data.AcceptRejectRule> vynucení.  
  
### <a name="to-commit-changes-in-a-dataset"></a>K provedení změn v datové sadě  
  
-   Volání `AcceptChanges` metodu na buď <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow> potvrdit změny v těchto objektů.  
  
     Následující příklad ukazuje, jak volat `AcceptChanges` metody k provedení změn v `Customers` tabulky po aktualizaci zdroje dat:  
  
     [!code-csharp[VbRaddataEditing#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#11)]
     [!code-vb[VbRaddataEditing#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#11)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Ukládání dat](../data-tools/saving-data.md)   
 [Postupy: načítání změněných řádků](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9)