---
title: Úpravy dat v datových sadách
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b51b5b4be12f76e2237ff93659617e1c1843722a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586650"
---
# <a name="edit-data-in-datasets"></a>Úpravy dat v datových sadách
Data v datových tabulkách můžete upravovat podobně, jako když upravujete data v tabulce v libovolné databázi. Tento proces může zahrnovat vkládání, aktualizaci a mazání záznamů v tabulce. Ve formuláři vázaného na data můžete určit, která pole jsou uživatelsky upravitelná. V těchto případech infrastruktura vázání dat zpracovává všechna sledování změn tak, aby se změny mohly poslat zpátky do databáze později. Pokud budete programově upravovat data a máte v úmyslu odeslat tyto změny zpět do databáze nástroje, musíte použít objekty a metody, které pro vás provedou sledování změn.

Kromě změny skutečných dat můžete také zadat dotaz na <xref:System.Data.DataTable>, který vrátí konkrétní řádky dat. Můžete například zadat dotaz na jednotlivé řádky, konkrétní verze řádků (původní a navržený), řádky, které se změnily, nebo řádky s chybami.

## <a name="to-edit-rows-in-a-dataset"></a>Úprava řádků v datové sadě
Chcete-li upravit existující řádek v <xref:System.Data.DataTable>, je nutné vyhledat <xref:System.Data.DataRow>, který chcete upravit, a poté přiřadit aktualizované hodnoty požadovaným sloupcům.

Pokud neznáte index řádku, který chcete upravit, vyhledejte pomocí metody `FindBy` primární klíč:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Pokud znáte index řádku, můžete získat a upravit řádky následujícím způsobem:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Vložení nových řádků do datové sady
Aplikace, které používají ovládací prvky vázané na data, obvykle přidávají nové záznamy pomocí tlačítka **Přidat nový** v [ovládacím prvku BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Chcete-li ručně přidat nové záznamy do datové sady, vytvořte nový řádek dat voláním metody v objektu DataTable. Pak přidejte řádek do kolekce <xref:System.Data.DataRow> (<xref:System.Data.DataTable.Rows%2A>) <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Aby se zachovaly informace, které datová sada potřebuje k odeslání aktualizací do zdroje dat, použijte metodu <xref:System.Data.DataRow.Delete%2A> k odebrání řádků v tabulce dat. Například pokud vaše aplikace používá TableAdapter (nebo <xref:System.Data.Common.DataAdapter>), `Update` metoda TableAdapter odstraní řádky v databázi, které mají <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted>.

Pokud vaše aplikace nepotřebuje odesílat aktualizace zpět do zdroje dat, je možné je odebrat přímým přístupem k kolekci datových řádků (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Odstranění záznamů z tabulky dat

- Zavolejte metodu <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow>.

     Tato metoda fyzicky neodebere záznam. Místo toho označí záznam pro odstranění.

    > [!NOTE]
    > Pokud získáte vlastnost Count <xref:System.Data.DataRowCollection>, výsledný počet obsahuje záznamy, které byly označeny k odstranění. Chcete-li získat přesný počet záznamů, které nejsou označeny k odstranění, můžete cyklicky procházet kolekci, která je v <xref:System.Data.DataRow.RowState%2A> vlastností každého záznamu. (Záznamy označené k odstranění mají <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted>.) Alternativně můžete vytvořit zobrazení dat datové sady, která filtruje na základě stavu řádku a získá vlastnost Count.

Následující příklad ukazuje, jak zavolat metodu <xref:System.Data.DataRow.Delete%2A> k označení prvního řádku v `Customers` tabulce jako odstraněné:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Zjistit, jestli existují změněné řádky
V případě změn záznamů v datové sadě jsou informace o těchto změnách uloženy, dokud je nepotvrdíte. Změny potvrdíte při volání metody `AcceptChanges` datové sady nebo tabulky dat nebo při volání metody `Update` TableAdapter nebo datového adaptéru.

Změny jsou v každém řádku dat sledovány dvěma způsoby:

- Každý řádek dat obsahuje informace související s jeho <xref:System.Data.DataRow.RowState%2A> (například <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>nebo <xref:System.Data.DataRowState.Unchanged>).

- Každý změněný řádek dat obsahuje více verzí tohoto řádku (<xref:System.Data.DataRowVersion>), původní verzi (před změnami) a aktuální verzi (po změnách). Během období, kdy probíhá změna (čas, kdy můžete reagovat na událost <xref:System.Data.DataTable.RowChanging>), je k dispozici také třetí verze – navržená verze.

Metoda <xref:System.Data.DataSet.HasChanges%2A> objektu DataSet vrátí `true`, pokud byly v datové sadě provedeny změny. Po zjištění, že existují změněné řádky, můžete zavolat metodu `GetChanges` <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> pro vrácení sady změněných řádků.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Určení, zda byly provedeny změny v jakýchkoli řádcích

- Chcete-li kontrolovat změněné řádky, zavolejte metodu <xref:System.Data.DataSet.HasChanges%2A> datové sady.

Následující příklad ukazuje, jak zjistit návratovou hodnotu z metody <xref:System.Data.DataSet.HasChanges%2A> k detekci, zda v datové sadě existují změněné řádky s názvem `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Určení typu změn
Můžete také zjistit, jaký typ změn byl proveden v datové sadě, předáním hodnoty z <xref:System.Data.DataRowState> výčtu do metody <xref:System.Data.DataSet.HasChanges%2A>.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Určení typu změn provedených na řádku

- Předání <xref:System.Data.DataRowState> hodnoty metodě <xref:System.Data.DataSet.HasChanges%2A>.

Následující příklad ukazuje, jak ověřit datovou sadu s názvem `NorthwindDataset1` k určení, zda do ní byly přidány nějaké nové řádky:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Vyhledání řádků s chybami
Když pracujete s jednotlivými sloupci a řádky dat, může dojít k chybám. Chcete-li zjistit, zda chyby existují v <xref:System.Data.DataSet>, <xref:System.Data.DataTable>nebo <xref:System.Data.DataRow>, můžete zaškrtnout vlastnost `HasErrors`.

1. Zkontrolujte vlastnost `HasErrors` a zjistěte, zda datová sada obsahuje chyby.

2. Pokud je vlastnost `HasErrors` `true`, Iterujte pomocí kolekcí tabulek a potom přes řádky a vyhledejte řádek s chybou.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Viz také:

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
