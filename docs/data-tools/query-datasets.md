---
title: Datové sady dotazů
description: Porozumění datovým sadám dotazů. Přečtěte si o citlivosti velikosti datových sad. Najde konkrétní řádek v tabulce dat, vyhledá řádky podle hodnot sloupce a přístup k souvisejícím záznamům.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8ccf228b147301eb9fccf41da98f8cc5204971a9
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436065"
---
# <a name="query-datasets"></a>Datové sady dotazů
Chcete-li vyhledat konkrétní záznamy v datové sadě, použijte `FindBy` metodu v objektu DataTable, zapište vlastní příkaz foreach k zacyklení nad kolekcí řádků tabulky nebo použijte [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Datová sada – rozlišovat velká a malá písmena
Ve výchozím nastavení v názvu datové sady, tabulky a sloupce nejsou rozlišována velká a malá písmena – to znamená, že tabulka v datové sadě s názvem "Customers" je také označována jako "Customers". To odpovídá konvencím pojmenování v mnoha databázích, včetně SQL Server. V SQL Server výchozí chování je, že názvy datových elementů nelze odlišit pouze v případě, že jsou rozlišována malá a velká písmena.

> [!NOTE]
> Na rozdíl od datových sad dokumenty XML rozlišují velká a malá písmena, takže názvy datových elementů definovaných ve schématech rozlišují velká a malá písmena. Například protokol schématu umožňuje schématu definovat tabulku s názvem "Customers" (zákazníci) a jinou tabulku nazvanou Customers. To může mít za následek kolizi názvů, pokud schéma obsahující prvky, které se liší pouze pomocí případu, je použito pro vygenerování třídy DataSet.

Rozlišování velkých a malých písmen, ale může být faktorem v tom, jak jsou data interpretována v rámci datové sady. Například pokud filtrujete data v tabulce DataSet, kritéria hledání mohou vracet různé výsledky v závislosti na tom, zda porovnávání rozlišuje malá a velká písmena. Nastavením vlastnosti datové sady můžete řídit, jak rozlišovat velká a malá písmena při filtrování, vyhledávání a řazení <xref:System.Data.DataSet.CaseSensitive%2A> . Všechny tabulky v datové sadě ve výchozím nastavení dědí hodnotu této vlastnosti. (Tuto vlastnost můžete pro každou jednotlivou tabulku přepsat nastavením <xref:System.Data.DataTable.CaseSensitive%2A> Vlastnosti tabulky.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Vyhledání konkrétního řádku v tabulce dat

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Vyhledání řádku v typované datové sadě s hodnotou primárního klíče

- Chcete-li najít řádek, zavolejte metodu silného typu `FindBy` , která používá primární klíč tabulky.

     V následujícím příkladu `CustomerID` je sloupec primárním klíčem `Customers` tabulky. To znamená, že vygenerovaná `FindBy` Metoda je `FindByCustomerID` . Příklad ukazuje, jak přiřadit určitou <xref:System.Data.DataRow> proměnnou pomocí vygenerované `FindBy` metody.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Vyhledání řádku v netypové datové sadě s hodnotou primárního klíče

- Zavolejte <xref:System.Data.DataRowCollection.Find%2A> metodu <xref:System.Data.DataRowCollection> kolekce a předejte primární klíč jako parametr.

     Následující příklad ukazuje, jak deklarovat nový řádek s názvem `foundRow` a přiřadit mu vrácenou hodnotu <xref:System.Data.DataRowCollection.Find%2A> metody. Pokud se najde primární klíč, obsah sloupce index 1 se zobrazí v okně se zprávou.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Najde řádky podle hodnot sloupců.

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Vyhledání řádků na základě hodnot v jakémkoli sloupci

- Tabulky dat jsou vytvořeny pomocí <xref:System.Data.DataTable.Select%2A> metody, která vrací pole <xref:System.Data.DataRow> s v závislosti na výrazu předaného <xref:System.Data.DataTable.Select%2A> metodě. Další informace o vytváření platných výrazů naleznete v části syntax výrazů stránky na stránce o této <xref:System.Data.DataColumn.Expression%2A> Vlastnosti.

     Následující příklad ukazuje, jak použít <xref:System.Data.DataTable.Select%2A> metodu <xref:System.Data.DataTable> k vyhledání konkrétních řádků.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Přístup k souvisejícím záznamům
Když tabulky v datové sadě souvisejí, <xref:System.Data.DataRelation> objekt může zpřístupnit související záznamy v jiné tabulce. Například datovou sadu obsahující `Customers` a `Orders` tabulky je možné zpřístupnit.

Pomocí <xref:System.Data.DataRelation> objektu můžete vyhledat související záznamy voláním <xref:System.Data.DataRow.GetChildRows%2A> metody <xref:System.Data.DataRow> v nadřazené tabulce. Tato metoda vrací pole souvisejících podřízených záznamů. Nebo můžete zavolat <xref:System.Data.DataRow.GetParentRow%2A> metodu <xref:System.Data.DataRow> v podřízené tabulce. Tato metoda vrací jeden <xref:System.Data.DataRow> z nadřazené tabulky.

Tato stránka poskytuje příklady pomocí typových datových sad. Informace o procházení vztahů v netypových datových sadách naleznete v tématu [navigace mezi DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
> Pokud pracujete v aplikaci model Windows Forms a pomocí funkcí pro datovou vazbu zobrazíte data, formulář generovaný návrhářem může poskytovat dostatek funkcí pro vaši aplikaci. Další informace najdete v tématu [vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Konkrétně najdete [v tématu relace v datových sadách](relationships-in-datasets.md).

Následující příklady kódu ukazují, jak procházet vztahy nahoru a dolů v zadaných datových sadách. Příklady kódu používají typové <xref:System.Data.DataRow> s ( `NorthwindDataSet.OrdersRow` ) a generované metody FindBy *PrimaryKey* ( `FindByCustomerID` ) k vyhledání požadovaného řádku a vrácení souvisejících záznamů. Příklady jsou kompilovány a spouštěny správně pouze v případě, že máte:

- Instance sady dat s názvem `NorthwindDataSet` s `Customers` tabulkou

- `Orders`Tabulka.

- Vztah s názvem `FK_Orders_Customers` souvisejícím s těmito dvěma tabulkami.

Kromě toho musí být obě tabulky vyplněny daty pro všechny záznamy, které mají být vráceny.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Vrácení podřízených záznamů vybraného nadřazeného záznamu

- Zavolejte <xref:System.Data.DataRow.GetChildRows%2A> metodu konkrétního `Customers` řádku dat a vraťte pole řádků z `Orders` tabulky:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Vrácení nadřazeného záznamu vybraného podřízeného záznamu

- Zavolejte <xref:System.Data.DataRow.GetParentRow%2A> metodu konkrétního `Orders` řádku dat a vraťte jeden řádek z `Customers` tabulky:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Viz také

- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
