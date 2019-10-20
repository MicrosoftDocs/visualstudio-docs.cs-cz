---
title: Úprava dat v datových sadách | Microsoft Docs
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
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672407"
---
# <a name="edit-data-in-datasets"></a>Úpravy dat v datových sadách
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data v datových tabulkách můžete upravovat podobně, jako když upravujete data v tabulce v libovolné databázi. Tento proces může zahrnovat vkládání, aktualizaci a mazání záznamů v tabulce. Ve formuláři vázaného na data můžete určit, která pole jsou uživatelsky upravitelná. V těchto případech infrastruktura vázání dat zpracovává všechna sledování změn tak, aby se změny mohly poslat zpátky do databáze později. Pokud budete programově upravovat data a máte v úmyslu odeslat tyto změny zpět do databáze nástroje, musíte použít objekty a metody, které pro vás provedou sledování změn.

 Kromě změny skutečných dat můžete také zadat dotaz na <xref:System.Data.DataTable>, který vrátí konkrétní řádky dat. Můžete například zadat dotaz na jednotlivé řádky, konkrétní verze řádků (původní a navržený), řádky, které se změnily, nebo řádky s chybami.

## <a name="to-edit-rows-in-a-dataset"></a>Úprava řádků v datové sadě
 Chcete-li upravit existující řádek v <xref:System.Data.DataTable>, je nutné vyhledat <xref:System.Data.DataRow>, který chcete upravit, a poté přiřadit aktualizované hodnoty požadovaným sloupcům.

 Pokud neznáte index řádku, který chcete upravit, vyhledejte pomocí metody `FindBy` primární klíč:

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 Pokud znáte index řádku, můžete získat a upravit řádky následujícím způsobem:

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Vložení nových řádků do datové sady
 Aplikace, které používají ovládací prvky vázané na data, obvykle přidávají nové záznamy pomocí tlačítka **Přidat nový** v [ovládacím prvku BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

 Chcete-li ručně přidat nové záznamy do datové sady, vytvořte nový řádek dat voláním metody v objektu DataTable. Pak přidejte řádek do kolekce <xref:System.Data.DataRow> (<xref:System.Data.DataTable.Rows%2A>) <xref:System.Data.DataTable>:

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 Aby se zachovaly informace, které datová sada potřebuje k odeslání aktualizací do zdroje dat, použijte metodu <xref:System.Data.DataRow.Delete%2A> k odebrání řádků v tabulce dat. Například pokud vaše aplikace používá TableAdapter (nebo <xref:System.Data.Common.DataAdapter>), `Update` metoda TableAdapter odstraní řádky v databázi, které mají <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState>.

 Pokud vaše aplikace nepotřebuje odesílat aktualizace zpět do zdroje dat, je možné je odebrat přímým přístupem k kolekci datových řádků (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Odstranění záznamů z tabulky dat

- Zavolejte metodu <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow>.

     Tato metoda fyzicky neodebere záznam. Místo toho označí záznam pro odstranění.

    > [!NOTE]
    > Pokud získáte vlastnost Count <xref:System.Data.DataRowCollection>, výsledný počet obsahuje záznamy, které byly označeny k odstranění. Chcete-li získat přesný počet záznamů, které nejsou označeny k odstranění, můžete cyklicky procházet kolekci, která je v <xref:System.Data.DataRow.RowState%2A> vlastností každého záznamu. (Záznamy označené k odstranění mají <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState>.) Alternativně můžete vytvořit zobrazení dat datové sady, která filtruje na základě stavu řádku a získá vlastnost Count.

     Následující příklad ukazuje, jak zavolat metodu <xref:System.Data.DataRow.Delete%2A> k označení prvního řádku v `Customers` tabulce jako odstraněné:

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>Zjistit, jestli existují změněné řádky
 V případě změn záznamů v datové sadě jsou informace o těchto změnách uloženy, dokud je nepotvrdíte. Změny potvrdíte při volání metody `AcceptChanges` datové sady nebo tabulky dat nebo při volání metody `Update` TableAdapter nebo datového adaptéru.

 Změny jsou v každém řádku dat sledovány dvěma způsoby:

- Každý řádek dat obsahuje informace týkající se <xref:System.Data.DataRow.RowState%2A> (například <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> nebo <xref:System.Data.DataRowState>).

- Každý změněný řádek dat obsahuje několik verzí tohoto řádku (<xref:System.Data.DataRowVersion>), původní verzi (před změnami) a aktuální verzi (po změnách). Během období, kdy probíhá změna (čas, kdy můžete reagovat na událost <xref:System.Data.DataTable.RowChanging>), je k dispozici také třetí verze – navržená verze.

  Metoda <xref:System.Data.DataSet.HasChanges%2A> objektu DataSet vrátí `true`, pokud byly v datové sadě provedeny změny. Po zjištění, že existují změněné řádky, můžete zavolat metodu `GetChanges` <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> pro vrácení sady změněných řádků. Další informace naleznete v tématu [How to: načíst změněné řádky](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Určení, zda byly provedeny změny v jakýchkoli řádcích

- Chcete-li kontrolovat změněné řádky, zavolejte metodu <xref:System.Data.DataSet.HasChanges%2A> datové sady.

     Následující příklad ukazuje, jak zjistit návratovou hodnotu z metody <xref:System.Data.DataSet.HasChanges%2A> k detekci, zda v datové sadě existují změněné řádky s názvem `NorthwindDataset1`:

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>Určení typu změn
 Můžete také zjistit, jaký typ změn byl proveden v datové sadě, předáním hodnoty z <xref:System.Data.DataRowState> výčtu do metody <xref:System.Data.DataSet.HasChanges%2A>.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Určení typu změn provedených na řádku

- Předání <xref:System.Data.DataRowState> hodnoty metodě <xref:System.Data.DataSet.HasChanges%2A>.

     Následující příklad ukazuje, jak ověřit datovou sadu s názvem `NorthwindDataset1` k určení, zda do ní byly přidány nějaké nové řádky:

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>Vyhledání řádků s chybami
 Když pracujete s jednotlivými sloupci a řádky dat, může dojít k chybám. Chcete-li zjistit, zda chyby existují v <xref:System.Data.DataSet>, <xref:System.Data.DataTable> nebo <xref:System.Data.DataRow>, můžete zaškrtnout vlastnost `HasErrors`.

1. Zkontrolujte vlastnost `HasErrors` a zjistěte, zda datová sada obsahuje chyby.

2. Pokud je vlastnost `HasErrors` `true`, Iterujte pomocí kolekcí tabulek a potom přes řádky a vyhledejte řádek s chybou.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
