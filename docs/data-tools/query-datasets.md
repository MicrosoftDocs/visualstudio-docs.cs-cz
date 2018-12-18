---
title: Datové sady dotazů
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2276828a67cec2562063d220ef3173d98fdf487b
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174290"
---
# <a name="query-datasets"></a>Datové sady dotazů
K vyhledání konkrétních záznamů v datové sadě, použijte `FindBy` metodu na objekt DataTable, psát vlastní příkazu foreach k vytvoření smyčky přes kolekce řádků v tabulce, nebo použijte [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

## <a name="dataset-case-sensitivity"></a>Rozlišování velikosti písmen pro datovou sadu
V datové sadě, názvy tabulek a sloupců ve výchozím nastavení rozlišují – to znamená, tabulku v datovou sadu s názvem "Zákazníci" lze také odkazovat jako "zákazníci." To stejné zásady vytváření názvů v mnoha databází, včetně SQL serveru. V systému SQL Server výchozím chováním je, že názvy datových prvků nelze odlišit pouze ve velikosti písmen.

> [!NOTE]
>  Na rozdíl od datové sady dokumenty XML jsou malá a velká písmena, tak, aby byly názvy datových prvků, které jsou definovány ve schématech malá a velká písmena. Například protokol schéma umožňuje schéma pro definování tabulky nazvané "Zákazníci" a jiné tabulky nazvané "zákazníků." To může způsobit kolize názvů při schéma, které obsahuje prvky, které se liší pouze velikostí písma se používá ke generování třídy datové sady.

Rozlišování velikosti písmen, ale může být faktor při tom, jak je interpretován data v datové sadě. Například pokud můžete filtrovat data v tabulce datové sady, kritéria hledání může vrátit různé výsledky v závislosti na tom, jestli je výsledkem porovnávání malá a velká písmena. Rozlišování velikosti písmen filtrování, hledání a řazení podle nastavení datové sady můžete řídit <xref:System.Data.DataSet.CaseSensitive%2A> vlastnost. Podle výchozího nastavení dědí všechny tabulky v datové sadě hodnota této vlastnosti. (Tato vlastnost pro každé jednotlivé tabulky můžete přepsat tak, že nastavíte v tabulce <xref:System.Data.DataTable.CaseSensitive%2A> vlastnosti.)

## <a name="locate-a-specific-row-in-a-data-table"></a>Vyhledejte konkrétní řádek v tabulce dat

#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Najít řádek v typové datové sady s hodnotou primárního klíče

-   Chcete-li vyhledejte řádek, zavolejte silného typu `FindBy` metodu, která používá primární klíč v tabulce.

     V následujícím příkladu `CustomerID` primární klíč je sloupec `Customers` tabulky. To znamená, že generované `FindBy` je metoda `FindByCustomerID`. Tento příklad ukazuje, jak přiřadit konkrétní <xref:System.Data.DataRow> proměnné s použitím vytvořeného `FindBy` metody.

     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]

#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Najít řádek v netypovou datovou sadu s hodnotu primárního klíče

-   Volání <xref:System.Data.DataRowCollection.Find%2A> metodu <xref:System.Data.DataRowCollection> kolekce, které se předá jako parametr primární klíč.

     Následující příklad ukazuje, jak deklarovat nový řádek, který volá `foundRow` a přiřaďte ho na návratový typ <xref:System.Data.DataRowCollection.Find%2A> metody. Pokud je nalezen primární klíč, obsah index sloupce 1 jsou zobrazeny v okně se zprávou.

     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]

## <a name="find-rows-by-column-values"></a>Vyhledání řádků podle hodnoty sloupců

#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>K vyhledání řádků na základě hodnot v libovolný sloupec

-   Tabulky dat jsou vytvořeny pomocí <xref:System.Data.DataTable.Select%2A> metodu, která vrací pole <xref:System.Data.DataRow>předán s založené na výrazu <xref:System.Data.DataTable.Select%2A> metody. Další informace o vytváření platné výrazy, naleznete v části "Syntaxe výrazu" na stránce <xref:System.Data.DataColumn.Expression%2A> vlastnost.

     Následující příklad ukazuje způsob použití <xref:System.Data.DataTable.Select%2A> metodu <xref:System.Data.DataTable> najít konkrétní řádky.

     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]

## <a name="access-related-records"></a>Přístup k související záznamy
Když jsou souvisejících tabulkách v datové sadě, <xref:System.Data.DataRelation> objektu můžete zpřístupnit souvisejících záznamů v druhé tabulce. Například datovou sadu obsahující `Customers` a `Orders` tabulky může být k dispozici.

Můžete použít <xref:System.Data.DataRelation> objekt vyhledejte související záznamy voláním <xref:System.Data.DataRow.GetChildRows%2A> metodu <xref:System.Data.DataRow> v nadřazené tabulce. Tato metoda vrátí pole související podřízené záznamy. Nebo můžete volat <xref:System.Data.DataRow.GetParentRow%2A> metodu <xref:System.Data.DataRow> v podřízené tabulce. Tato metoda vrací jedinou <xref:System.Data.DataRow> z nadřazené tabulky.

Tato stránka obsahuje příklady použití typové datové sady. Informace o navigace v relacích v netypové datové sady, naleznete v tématu [procházení datových relací](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).

> [!NOTE]
>  Pokud pracujete v aplikaci Windows Forms a používání funkcí datové vazby k zobrazení dat, generovaný návrhářem formuláře může poskytnout dostatek funkcí pro vaši aplikaci. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Konkrétně, naleznete v tématu [vztahy v datových sadách](relationships-in-datasets.md).

Následující příklady kódu ukazují, jak procházet nahoru a dolů vztahy v typových datových sadách. Příklady použití kód zadali <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) a vygenerovaný FindBy*PrimaryKey* (`FindByCustomerID`) metody pro vyhledání požadovaný řádek a vrácení souvisejících záznamů. V příkladech kompilace a spuštění správně pouze v případě, že máte:

-   Instance datovou sadu s názvem `NorthwindDataSet` s `Customers` tabulky.

-   `Orders` Tabulky.

-   Relace s názvem `FK_Orders_Customers`týkající se dvěma tabulkami.

Kromě toho obou tabulek muset být naplněný daty pro záznamy, které se mají vrátit.

#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Vrátit podřízené záznamy vybraný nadřazený záznam

-   Volání <xref:System.Data.DataRow.GetChildRows%2A> metoda konkrétní `Customers` data řádku a vrátí řádky z pole `Orders` tabulky:

     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]

#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Chcete-li vrátit nadřazený záznam vybraný podřízený záznam

-   Volání <xref:System.Data.DataRow.GetParentRow%2A> metoda konkrétní `Orders` řádek dat a vrátí jeden řádek z `Customers` tabulky:

     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Viz také:

- [Nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)