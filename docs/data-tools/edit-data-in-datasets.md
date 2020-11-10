---
title: Úpravy dat v datových sadách
description: Naučte se upravovat data v datových sadách. Informace o tom, jak upravit řádky datové sady, vložit nové řádky do datové sady, zjistit, zda jsou řádky změněny, a vyhledat řádky s chybami
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: e547d3a6a07a7881c34462138ffbe708b8d74080
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435088"
---
# <a name="edit-data-in-datasets"></a>Úpravy dat v datových sadách
Data v datových tabulkách můžete upravovat podobně, jako když upravujete data v tabulce v libovolné databázi. Tento proces může zahrnovat vkládání, aktualizaci a mazání záznamů v tabulce. Ve formuláři vázaného na data můžete určit, která pole jsou uživatelsky upravitelná. V těchto případech infrastruktura vázání dat zpracovává všechna sledování změn tak, aby se změny mohly poslat zpátky do databáze později. Pokud budete programově upravovat data a máte v úmyslu odeslat tyto změny zpět do databáze nástroje, musíte použít objekty a metody, které pro vás provedou sledování změn.

Kromě změny skutečných dat můžete také zadat dotaz <xref:System.Data.DataTable> na, který vrátí konkrétní řádky dat. Můžete například zadat dotaz na jednotlivé řádky, konkrétní verze řádků (původní a navržený), řádky, které se změnily, nebo řádky s chybami.

## <a name="to-edit-rows-in-a-dataset"></a>Úprava řádků v datové sadě
Chcete-li upravit existující řádek v nástroji <xref:System.Data.DataTable> , je třeba vyhledat <xref:System.Data.DataRow> , který chcete upravit, a poté přiřadit aktualizované hodnoty k požadovaným sloupcům.

Pokud neznáte index řádku, který chcete upravit, použijte `FindBy` k hledání pomocí metody primární klíč:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Pokud znáte index řádku, můžete získat a upravit řádky následujícím způsobem:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Vložení nových řádků do datové sady
Aplikace, které používají ovládací prvky vázané na data, obvykle přidávají nové záznamy pomocí tlačítka **Přidat nový** v [ovládacím prvku BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Chcete-li ručně přidat nové záznamy do datové sady, vytvořte nový řádek dat voláním metody v objektu DataTable. Pak přidejte řádek do <xref:System.Data.DataRow> kolekce ( <xref:System.Data.DataTable.Rows%2A> ) <xref:System.Data.DataTable> :

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Aby se zachovaly informace, které datová sada potřebuje k odeslání aktualizací do zdroje dat, použijte <xref:System.Data.DataRow.Delete%2A> metodu k odebrání řádků v tabulce dat. Například pokud vaše aplikace používá TableAdapter (nebo <xref:System.Data.Common.DataAdapter> ), `Update` Metoda TableAdapter odstraní řádky v databázi, které mají <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> .

Pokud vaše aplikace nepotřebuje odesílat aktualizace zpět do zdroje dat, je možné je odebrat přímým přístupem k kolekci datových řádků ( <xref:System.Data.DataRowCollection.Remove%2A> ).

#### <a name="to-delete-records-from-a-data-table"></a>Odstranění záznamů z tabulky dat

- Zavolejte <xref:System.Data.DataRow.Delete%2A> metodu <xref:System.Data.DataRow> .

     Tato metoda fyzicky neodebere záznam. Místo toho označí záznam pro odstranění.

    > [!NOTE]
    > Pokud získáte vlastnost Count pro <xref:System.Data.DataRowCollection> , výsledný počet obsahuje záznamy, které byly označeny k odstranění. Chcete-li získat přesný počet záznamů, které nejsou označeny k odstranění, můžete cyklicky procházet kolekci, která je v <xref:System.Data.DataRow.RowState%2A> jednotlivých záznamech. (Záznamy označené k odstranění mají <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted> .) Alternativně můžete vytvořit zobrazení dat datové sady, která filtruje na základě stavu řádku a získá vlastnost Count.

Následující příklad ukazuje, jak zavolat <xref:System.Data.DataRow.Delete%2A> metodu k označení prvního řádku v `Customers` tabulce jako odstraněný:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Zjistit, jestli existují změněné řádky
V případě změn záznamů v datové sadě jsou informace o těchto změnách uloženy, dokud je nepotvrdíte. Změny potvrdíte při volání `AcceptChanges` metody datové sady nebo tabulky dat nebo při volání `Update` metody TableAdapter nebo datového adaptéru.

Změny jsou v každém řádku dat sledovány dvěma způsoby:

- Každý řádek dat obsahuje informace související s jeho <xref:System.Data.DataRow.RowState%2A> (například,, <xref:System.Data.DataRowState.Added> <xref:System.Data.DataRowState.Modified> <xref:System.Data.DataRowState.Deleted> nebo <xref:System.Data.DataRowState.Unchanged> ).

- Každý změněný řádek dat obsahuje několik verzí tohoto řádku ( <xref:System.Data.DataRowVersion> ), původní verzi (před změnami) a aktuální verzi (po změnách). Během období, kdy se čeká na změnu (čas, kdy můžete reagovat na <xref:System.Data.DataTable.RowChanging> událost), je k dispozici také třetí verze – navržená verze.

<xref:System.Data.DataSet.HasChanges%2A>Metoda objektu DataSet vrátí, `true` Pokud byly v datové sadě provedeny změny. Po zjištění, že existují změněné řádky, můžete zavolat `GetChanges` metodu <xref:System.Data.DataSet> nebo, <xref:System.Data.DataTable> která vrátí sadu změněných řádků.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Určení, zda byly provedeny změny v jakýchkoli řádcích

- Zavolejte <xref:System.Data.DataSet.HasChanges%2A> metodu datové sady pro kontrolu změněných řádků.

Následující příklad ukazuje, jak ověřit návratovou hodnotu z <xref:System.Data.DataSet.HasChanges%2A> metody k detekci, zda existují změněné řádky v datové sadě s názvem `NorthwindDataset1` :

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Určení typu změn
Můžete také zjistit, jaké typy změn byly provedeny v datové sadě předáním hodnoty z <xref:System.Data.DataRowState> výčtu do <xref:System.Data.DataSet.HasChanges%2A> metody.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Určení typu změn provedených na řádku

- Předat <xref:System.Data.DataRowState> hodnotu <xref:System.Data.DataSet.HasChanges%2A> metodě.

Následující příklad ukazuje, jak ověřit datovou sadu s názvem `NorthwindDataset1` k určení, zda do ní byly přidány nějaké nové řádky:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Vyhledání řádků s chybami
Když pracujete s jednotlivými sloupci a řádky dat, může dojít k chybám. Můžete kontrolovat `HasErrors` vlastnost a zjistit, zda chyby existují v <xref:System.Data.DataSet> , <xref:System.Data.DataTable> nebo <xref:System.Data.DataRow> .

1. Zkontrolujte `HasErrors` vlastnost a podívejte se, zda datová sada obsahuje chyby.

2. Pokud `HasErrors` je vlastnost `true` , Iterujte pomocí kolekcí tabulek a potom přes řádky a vyhledejte řádek s chybou.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Viz také

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
