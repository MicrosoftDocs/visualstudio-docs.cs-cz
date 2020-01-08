---
title: Datové sady dotazů
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4080866de58e17c5e11ed01d61740c2f83aed9a7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586338"
---
# <a name="query-datasets"></a>Datové sady dotazů
Chcete-li vyhledat konkrétní záznamy v datové sadě, použijte metodu `FindBy` v objektu DataTable, napište vlastní příkaz foreach pro smyčku nad kolekcí řádků tabulky nebo použijte [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Datová sada – rozlišovat velká a malá písmena
Ve výchozím nastavení v názvu datové sady, tabulky a sloupce nejsou rozlišována velká a malá písmena – to znamená, že tabulka v datové sadě s názvem "Customers" je také označována jako "Customers". To odpovídá konvencím pojmenování v mnoha databázích, včetně SQL Server. V SQL Server výchozí chování je, že názvy datových elementů nelze odlišit pouze v případě, že jsou rozlišována malá a velká písmena.

> [!NOTE]
> Na rozdíl od datových sad dokumenty XML rozlišují velká a malá písmena, takže názvy datových elementů definovaných ve schématech rozlišují velká a malá písmena. Například protokol schématu umožňuje schématu definovat tabulku s názvem "Customers" (zákazníci) a jinou tabulku nazvanou Customers. To může mít za následek kolizi názvů, pokud schéma obsahující prvky, které se liší pouze pomocí případu, je použito pro vygenerování třídy DataSet.

Rozlišování velkých a malých písmen, ale může být faktorem v tom, jak jsou data interpretována v rámci datové sady. Například pokud filtrujete data v tabulce DataSet, kritéria hledání mohou vracet různé výsledky v závislosti na tom, zda porovnávání rozlišuje malá a velká písmena. Nastavením vlastnosti <xref:System.Data.DataSet.CaseSensitive%2A> datové sady můžete řídit rozlišování velkých a malých písmen pro filtrování, vyhledávání a řazení. Všechny tabulky v datové sadě ve výchozím nastavení dědí hodnotu této vlastnosti. (Tuto vlastnost můžete pro každou jednotlivou tabulku přepsat nastavením vlastnosti <xref:System.Data.DataTable.CaseSensitive%2A> tabulky).

## <a name="locate-a-specific-row-in-a-data-table"></a>Vyhledání konkrétního řádku v tabulce dat

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Vyhledání řádku v typované datové sadě s hodnotou primárního klíče

- Chcete-li najít řádek, zavolejte silně typovou `FindBy` metodu, která používá primární klíč tabulky.

     V následujícím příkladu je sloupec `CustomerID` primárním klíčem tabulky `Customers`. To znamená, že vygenerovaná `FindBy` metoda je `FindByCustomerID`. Příklad ukazuje, jak přiřadit konkrétní <xref:System.Data.DataRow> k proměnné pomocí generované `FindBy` metody.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Vyhledání řádku v netypové datové sadě s hodnotou primárního klíče

- Zavolejte metodu <xref:System.Data.DataRowCollection.Find%2A> kolekce <xref:System.Data.DataRowCollection> a předejte primární klíč jako parametr.

     Následující příklad ukazuje, jak deklarovat nový řádek s názvem `foundRow` a přiřadit mu návratovou hodnotu metody <xref:System.Data.DataRowCollection.Find%2A>. Pokud se najde primární klíč, obsah sloupce index 1 se zobrazí v okně se zprávou.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Najde řádky podle hodnot sloupců.

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Vyhledání řádků na základě hodnot v jakémkoli sloupci

- Tabulky dat jsou vytvořeny pomocí metody <xref:System.Data.DataTable.Select%2A>, která vrací pole <xref:System.Data.DataRow>na základě výrazu předaného metodě <xref:System.Data.DataTable.Select%2A>. Další informace o vytváření platných výrazů naleznete v části syntax výrazů stránky na stránce o vlastnosti <xref:System.Data.DataColumn.Expression%2A>.

     Následující příklad ukazuje, jak použít metodu <xref:System.Data.DataTable.Select%2A> <xref:System.Data.DataTable> k vyhledání konkrétních řádků.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Přístup k souvisejícím záznamům
Když tabulky v datové sadě souvisejí, objekt <xref:System.Data.DataRelation> může zpřístupnit související záznamy v jiné tabulce. Například je možné zpřístupnit datovou sadu obsahující `Customers` a tabulky `Orders`.

Objekt <xref:System.Data.DataRelation> lze použít k vyhledání souvisejících záznamů voláním metody <xref:System.Data.DataRow.GetChildRows%2A> <xref:System.Data.DataRow> v nadřazené tabulce. Tato metoda vrací pole souvisejících podřízených záznamů. Nebo můžete volat metodu <xref:System.Data.DataRow.GetParentRow%2A> <xref:System.Data.DataRow> v podřízené tabulce. Tato metoda vrací jeden <xref:System.Data.DataRow> z nadřazené tabulky.

Tato stránka poskytuje příklady pomocí typových datových sad. Informace o procházení vztahů v netypových datových sadách naleznete v tématu [navigace mezi DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Pokud pracujete v aplikaci model Windows Forms a pomocí funkcí pro datovou vazbu zobrazíte data, formulář generovaný návrhářem může poskytovat dostatek funkcí pro vaši aplikaci. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Konkrétně najdete [v tématu relace v datových sadách](relationships-in-datasets.md).

Následující příklady kódu ukazují, jak procházet vztahy nahoru a dolů v zadaných datových sadách. Příklady kódu používají typové <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) a generované metody FindBy*PrimaryKey* (`FindByCustomerID`) k vyhledání požadovaného řádku a vrácení souvisejících záznamů. Příklady jsou kompilovány a spouštěny správně pouze v případě, že máte:

- Instance sady dat s názvem `NorthwindDataSet` s tabulkou `Customers`.

- Tabulka `Orders`.

- Vztah s názvem `FK_Orders_Customers`související s těmito dvěma tabulkami.

Kromě toho musí být obě tabulky vyplněny daty pro všechny záznamy, které mají být vráceny.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Vrácení podřízených záznamů vybraného nadřazeného záznamu

- Zavolejte metodu <xref:System.Data.DataRow.GetChildRows%2A> konkrétního řádku dat `Customers` a vraťte pole řádků z tabulky `Orders`:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Vrácení nadřazeného záznamu vybraného podřízeného záznamu

- Zavolejte metodu <xref:System.Data.DataRow.GetParentRow%2A> konkrétního řádku dat `Orders` a vraťte jeden řádek z tabulky `Customers`:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Viz také:

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
