---
title: Úprava dat v datových sadách | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a983b671b5c6b43009ad3cc32c2cb287977f05c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949289"
---
# <a name="edit-data-in-datasets"></a>Úpravy dat v datových sadách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Můžete upravovat data v datových tabulkách stejně, jako úprava dat v tabulce v jakékoli databázi. Proces může obsahovat, vkládání, aktualizaci a odstranění záznamů v tabulce. Ve formě vázané na data můžete určit, která pole se uživatel upravovat. V těchto případech se datové vazby infrastruktury zpracovává všechny řešení change tracking, aby změny lze odeslat zpět do databáze později. Pokud provedete úpravy prostřednictvím kódu programu k datům a chcete odeslat změny zpět do databáze, musíte použít objekty a metody, které udělal za vás sledování změn.  
  
 Kromě změny skutečná data, můžete také zadávat dotazy <xref:System.Data.DataTable> vrátit konkrétní řádky dat. Například se může dotazovat na jednotlivé řádky, určité verze řádků (původní a navrhované), řádky, které se změnily nebo řádky, které obsahují chyby.  
  
## <a name="to-edit-rows-in-a-dataset"></a>Chcete-li upravit řádky v datové sadě  
 Chcete-li upravit existující řádek v <xref:System.Data.DataTable>, budete muset najít <xref:System.Data.DataRow> chcete upravit a potom přiřadit aktualizovanými hodnotami požadovaných sloupců.  
  
 Pokud si nejste jisti index řádku, který chcete upravit, použijte `FindBy` metody na hledání podle primárního klíče:  
  
 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]  
  
 Pokud znáte index řádku, můžete přístup a upraví následující řádky:  
  
 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>Chcete-li vložit nových řádků do datové sady  
 Aplikace, které používají ovládací prvky vázané na data obvykle přidávat nové záznamy prostřednictvím **přidat nový** tlačítko [BindingNavigator – ovládací prvek](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).  
  
 Ruční přidání nových záznamů do datové sady, vytvořte nový řádek dat voláním metody na objektu DataTable. Pak přidejte řádku, který má <xref:System.Data.DataRow> kolekce (<xref:System.Data.DataTable.Rows%2A>) z <xref:System.Data.DataTable>:  
  
 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]  
  
 Chcete-li zachovat informace, že datová sada potřebuje k odeslání aktualizací do zdroje dat, použijte <xref:System.Data.DataRow.Delete%2A> metody, které se mají odebrat řádky v tabulce dat. Například, pokud vaše aplikace používá TableAdapter (nebo <xref:System.Data.Common.DataAdapter>), objektu TableAdapter `Update` metoda odstraní řádků v databázi, které mají <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState>.  
  
 Pokud aplikace nepotřebuje k odeslání aktualizací zpět do zdroje dat, je možné odebrat záznamy podle přímé Přistupování ke shromažďování dat řádku (<xref:System.Data.DataRowCollection.Remove%2A>).  
  
#### <a name="to-delete-records-from-a-data-table"></a>K odstranění záznamů z tabulky dat  
  
-   Volání <xref:System.Data.DataRow.Delete%2A> metodu <xref:System.Data.DataRow>.  
  
     Tato metoda neodebere fyzicky záznamu. Místo toho označí záznamy pro odstranění.  
  
    > [!NOTE]
    >  Pokud se zobrazí vlastnosti count <xref:System.Data.DataRowCollection>, výsledný počet zahrnuje záznamy, které jsou označené k odstranění. Získáte přesný počet záznamů, které nejsou označené k odstranění můžete projít kolekce podíváme <xref:System.Data.DataRow.RowState%2A> vlastností každého záznamu. (Označená k odstranění záznamů <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState>.) Alternativně můžete vytvořit zobrazení dat pro datovou sadu, filtry založené na stavu řádků a získat počet vlastností z něj.  
  
     Následující příklad ukazuje, jak volat <xref:System.Data.DataRow.Delete%2A> metoda k označení první řádek v `Customers` tabulky se odstranil:  
  
     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]  
  
## <a name="determine-if-there-are-changed-rows"></a>Určí, jestli je změněných řádků  
 Při změně záznamů v datové sadě, informace o tyto změny jsou uloženy, dokud je nepotvrdíte. Použití změn při volání `AcceptChanges` metoda tabulku datové sady nebo data, nebo při volání `Update` metody TableAdapter nebo datového adaptéru.  
  
 Změny sledované dvěma způsoby v každém řádku dat:  
  
- Každý řádek dat obsahuje informace související s jejími <xref:System.Data.DataRow.RowState%2A> (například <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, nebo <xref:System.Data.DataRowState>).  
  
- Každý řádek změněných dat obsahuje více verzí tohoto řádku (<xref:System.Data.DataRowVersion>), původní verze (před změnami) a aktuální verze (po změnách). Během doby, kdy změna čeká (čas, kdy můžete reagovat na <xref:System.Data.DataTable.RowChanging> událostí), třetí verze – navrhovaná verze – je k dispozici také. Další informace najdete v tématu [postupy: získání konkrétních verzí DataRow](../data-tools/how-to-get-specific-versions-of-a-datarow.md).  
  
  <xref:System.Data.DataSet.HasChanges%2A> Vrátí metoda objekt dataset `true` Pokud byly provedeny změny v datové sadě. Jakmile určíte, že existují změněné řádky, můžete volat `GetChanges` metodu <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> vrátit sadu změněných řádků. Další informace najdete v tématu [postupy: načtení změnil řádků](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Chcete-li zjistit, jestli byly provedené změny nějakých řádků  
  
-   Volání <xref:System.Data.DataSet.HasChanges%2A> metoda datovou sadu vyhledat změněných řádků.  
  
     Následující příklad ukazuje, jak zkontrolovat návratovou hodnotu z <xref:System.Data.DataSet.HasChanges%2A> metoda ke zjištění, zda existují nějaké změněné řádky v datové sadě s názvem `NorthwindDataset1`:  
  
     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]  
  
## <a name="determine-the-type-of-changes"></a>Určit typ změny  
 Můžete také zkontrolovat, pokud chcete zobrazit, jaký typ změny byly provedeny v datové sadě předáním hodnoty z <xref:System.Data.DataRowState> výčet <xref:System.Data.DataSet.HasChanges%2A> metody.  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>K určení jaké změny byly provedeny na řádek  
  
-   Předat <xref:System.Data.DataRowState> hodnota, která se <xref:System.Data.DataSet.HasChanges%2A> metody.  
  
     Následující příklad ukazuje, jak zkontrolovat datovou sadu s názvem `NorthwindDataset1` k určení, pokud k němu byly přidány nějaké nové řádky:  
  
     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]  
  
## <a name="to-locate-rows-that-have-errors"></a>K vyhledání řádků s chybami  
 Při práci s jednotlivé sloupce a řádky dat, mohou se vyskytnout chyby. Můžete zkontrolovat `HasErrors` a určí, pokud existují v chyby <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow>.  
  
1.  Zkontrolujte, `HasErrors` vlastnosti chcete zobrazit, pokud nejsou žádné chyby v datové sadě.  
  
2.  Pokud `HasErrors` vlastnost `true`, iteraci v rámci kolekce tabulek a pak přes řádky k vyhledání řádků s chybou.  
  
     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]

