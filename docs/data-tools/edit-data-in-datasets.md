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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1ad74243c70b4ca7aaa8460759abbc898d30bb9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757146"
---
# <a name="edit-data-in-datasets"></a>Úpravy dat v datových sadách
Můžete upravit dat v datových tabulkách jako upravovat data v tabulce v některé z databází. Tento proces může obsahovat vkládání, aktualizaci a odstraňování záznamů v tabulce. Ve formuláři vázané na data můžete zadat pole, která budou uživatele nelze upravit. V takových případech infrastruktury vazby dat zpracovává všechny sledování změn, aby změny může být odeslána zpět do databáze později. Pokud provedete úpravy prostřednictvím kódu programu k datům, a chcete odeslat tyto změny zpět do databáze, musíte použít objekty a metody, které provádějí sledování změn pro vás.

Kromě změna skutečná data, můžete taky zadat dotaz <xref:System.Data.DataTable> vrátit konkrétní řádky dat. Například může dotaz pro jednotlivé řádky, konkrétních verzí řádků (původní a navrhované), řádky, které se změnily nebo řádků s chybami.

## <a name="to-edit-rows-in-a-dataset"></a>Chcete-li upravit řádků v datové sadě
Chcete-li upravit existující řádek v <xref:System.Data.DataTable>, budete muset najít <xref:System.Data.DataRow> chcete upravit a potom přiřadit požadovaných sloupců aktualizovanými hodnotami.

Pokud si nejste jisti index řádku chcete upravit, použijte `FindBy` metody na hledání podle primární klíč:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Pokud znáte index řádku, můžete přístup a upraví následující řádky:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Chcete-li vkládání nových řádků do datové sady
Aplikace, které používají ovládací prvky vázané na data obvykle přidávat nové záznamy prostřednictvím **přidat nové** tlačítko [BindingNavigator – ovládací prvek](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Ruční přidání nových záznamů do datové sady, vytvořte nový řádek dat voláním metody na DataTable. Poté, přidejte řádek, abyste <xref:System.Data.DataRow> kolekce (<xref:System.Data.DataTable.Rows%2A>) z <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Aby bylo možné uchovávat informace, že datová sada musí k odesílání aktualizací ke zdroji dat, použijte <xref:System.Data.DataRow.Delete%2A> metoda odebrat řádky v tabulce data. Například, pokud vaše aplikace používá TableAdapter (nebo <xref:System.Data.Common.DataAdapter>), TableAdapter `Update` metoda odstraní řádků v databázi, které mají <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Deleted>.

Pokud vaše aplikace nemusí k odesílání aktualizací zpět ke zdroji dat, je možné odebrat záznamy přímým přístupem k řádku shromažďování dat (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>K odstranění záznamů z tabulky dat

-   Volání <xref:System.Data.DataRow.Delete%2A> metodu <xref:System.Data.DataRow>.

     Tato metoda není fyzicky odebrat záznam. Místo toho označí záznam pro odstranění.

    > [!NOTE]
    >  Pokud se zobrazí vlastnosti count <xref:System.Data.DataRowCollection>, výsledná počet obsahuje záznamy, které byla označena pro odstranění. Získat přesné počet záznamů, které nejsou označené k odstranění, můžete projít kolekci vidí <xref:System.Data.DataRow.RowState%2A> vlastnost každý záznam. (Mají záznamy označena pro odstranění <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Deleted>.) Alternativně můžete vytvořit zobrazení dat pro datovou sadu, která filtry na základě řádku stavu a get pro vlastnost počet odtud.

Následující příklad ukazuje způsob volání <xref:System.Data.DataRow.Delete%2A> metoda označit první řádek v `Customers` tabulky odstranil:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Určí, jestli jsou změněných řádků
Když změn záznamů v datové sadě, uloží se až po informace o těchto změnách. Použití změn při volání `AcceptChanges` metoda tabulky datové sady nebo data, nebo když zavoláte `Update` metoda adaptéru TableAdapter nebo data.

Změny sledovaných dvěma způsoby v každém řádku dat:

-   Každý řádek dat obsahuje informace související s jeho <xref:System.Data.DataRow.RowState%2A> (například <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, nebo <xref:System.Data.DataRowState.Unchanged>).

-   Každý řádek změněná data obsahuje více verzí tento řádek (<xref:System.Data.DataRowVersion>), původní verze (před změny) a verzí (po provedení změn). V době, kdy čeká na vyřízení změnu (čas, kdy může reagovat na <xref:System.Data.DataTable.RowChanging> událostí), třetí verzi – navrhované verze – je také k dispozici.

<xref:System.Data.DataSet.HasChanges%2A> Vrátí metoda datové sady `true` Pokud byly provedeny změny v datové sadě. Po určení, že existují změněných řádků, můžete zavolat `GetChanges` metodu <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> vrátit sadu změněných řádků.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Chcete-li zjistit, pokud byly provedeny změny na všechny řádky

-   Volání <xref:System.Data.DataSet.HasChanges%2A> metodu datové sady zkontrolujte změnit řádků.

Následující příklad ukazuje, jak zkontrolovat návratovou hodnotou z <xref:System.Data.DataSet.HasChanges%2A> metodu za účelem zjištění, jestli se všechny změněné řádky v datové sadě s názvem `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Určuje typ změny
Můžete také zkontrolovat, pokud chcete zobrazit, jaké typy změn byly provedeny v datové sadě předáním hodnoty z <xref:System.Data.DataRowState> výčet <xref:System.Data.DataSet.HasChanges%2A> metoda.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Chcete-li zjistit jaký typ změny byly provedeny na řádek

-   Předat <xref:System.Data.DataRowState> hodnotu <xref:System.Data.DataSet.HasChanges%2A> metoda.

Následující příklad ukazuje, jak zkontrolovat datovou sadu s názvem `NorthwindDataset1` k určení, pokud k němu byly přidány žádné nové řádky:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>K vyhledání řádků s chybami
Při práci s jednotlivých sloupců a řádků dat, může dojít k chybám. Můžete zkontrolovat `HasErrors` vlastnosti k určení, zda existují chyby v <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow>.

1.  Zkontrolujte `HasErrors` vlastnosti chcete zobrazit, pokud nejsou žádné chyby v datové sadě.

2.  Pokud `HasErrors` vlastnost je `true`, iteraci prostřednictvím kolekce tabulek a potom prostřednictvím řádky, k vyhledání řádků došlo k chybě.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Viz také:

- [Datové sady nástrojů v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)