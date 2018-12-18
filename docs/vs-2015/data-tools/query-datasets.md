---
title: Dotazování datové sady | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6e1ff0cd6f77d2155ff4982ca02657a741c02d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890566"
---
# <a name="query-datasets"></a>Datové sady dotazů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
K vyhledání konkrétních záznamů v datové sadě, použijte metodu FindBy v objektu DataTable, napsat smyčku foreach přes kolekce řádků v tabulce nebo použijte [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17). LINQ to DataSet.  
  
## <a name="dataset-case-sensitivity"></a>Rozlišování velikosti písmen pro datovou sadu  
 V datové sadě, názvy tabulek a sloupců ve výchozím nastavení rozlišují – to znamená, tabulku v datovou sadu s názvem "Zákazníci" lze také odkazovat jako "zákazníci." To odpovídá zásady vytváření názvů v mnoha databází, včetně SQL Server.In SQL Server, výchozím chováním je, že názvy datových prvků nelze odlišit pouze ve velikosti písmen.  
  
> [!NOTE]
>  Na rozdíl od datové sady dokumenty XML jsou malá a velká písmena, tak, aby byly názvy datových prvků, které jsou definovány ve schématech malá a velká písmena. Například protokol schéma umožňuje schéma pro definování tabulky nazvané "Zákazníci" a jiné tabulky nazvané "zákazníků." To může způsobit kolize názvů při schéma, které obsahuje prvky, které se liší pouze velikostí písma se používá ke generování třídy datové sady.  
  
 Rozlišování velikosti písmen, ale může být faktor při tom, jak je interpretován data v datové sadě. Například pokud můžete filtrovat data v tabulce datové sady, kritéria hledání může vrátit různé výsledky v závislosti na tom, jestli je výsledkem porovnávání malá a velká písmena. Rozlišování velikosti písmen filtrování, hledání a řazení podle nastavení datové sady můžete řídit <xref:System.Data.DataSet.CaseSensitive%2A> vlastnost. Podle výchozího nastavení dědí všechny tabulky v datové sadě hodnota této vlastnosti. (Tato vlastnost pro každé jednotlivé tabulky můžete přepsat tak, že nastavíte v tabulce <xref:System.Data.DataTable.CaseSensitive%2A> vlastnosti.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Vyhledejte konkrétní řádek v tabulce dat  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Najít řádek v typové datové sady s hodnotou primárního klíče  
  
-   Chcete-li vyhledejte řádek, zavolejte silného typu `FindBy` metodu, která používá primární klíč v tabulce.  
  
     V následujícím příkladu `CustomerID` primární klíč je sloupec `Customers` tabulky. To znamená, že generované `FindBy` je metoda `FindByCustomerID`. Tento příklad ukazuje, jak přiřadit konkrétní <xref:System.Data.DataRow> proměnné s použitím vytvořeného `FindBy` metody.  
  
     [!code-csharp[VbRaddataEditing#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#18)]
     [!code-vb[VbRaddataEditing#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#18)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Najít řádek v netypovou datovou sadu s hodnotu primárního klíče  
  
-   Volání <xref:System.Data.DataRowCollection.Find%2A> metodu <xref:System.Data.DataRowCollection> kolekce, které se předá jako parametr primární klíč.  
  
     Následující příklad ukazuje, jak deklarovat nový řádek, který volá `foundRow` a přiřaďte ho na návratový typ <xref:System.Data.DataRowCollection.Find%2A> metody. Pokud je nalezen primární klíč, obsah index sloupce 1 jsou zobrazeny v okně se zprávou.  
  
     [!code-csharp[VbRaddataEditing#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#19)]
     [!code-vb[VbRaddataEditing#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#19)]  
  
## <a name="findrows-by-column-values"></a>FindRows podle hodnoty sloupců  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>K vyhledání řádků na základě hodnot v libovolný sloupec  
  
-   Tabulky dat jsou vytvořeny pomocí<xref:System.Data.DataTable.Select%2A> metodu, která vrací pole <xref:System.Data.DataRow>předán s založené na výrazu <xref:System.Data.DataTable.Select%2A> metody. Další informace o vytváření platné výrazy, naleznete v části "Syntaxe výrazu" na stránce <xref:System.Data.DataColumn.Expression%2A> vlastnost.  
  
     Následující příklad ukazuje způsob použití <xref:System.Data.DataTable.Select%2A> metodu <xref:System.Data.DataTable> najít konkrétní řádky.  
  
     [!code-csharp[VbRaddataEditing#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#20)]
     [!code-vb[VbRaddataEditing#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#20)]  
  
## <a name="accessrelated-records"></a>Accessrelated záznamů  
 Když jsou souvisejících tabulkách v datové sadě, <xref:System.Data.DataRelation> objektu můžete zpřístupnit souvisejících záznamů v druhé tabulce. Například datovou sadu obsahující `Customers` a `Orders` tabulky může být k dispozici.  
  
 Můžete použít <xref:System.Data.DataRelation> objekt vyhledejte související záznamy voláním <xref:System.Data.DataRow.GetChildRows%2A> metodu <xref:System.Data.DataRow> v nadřazené tabulce. Tato metoda vrátí pole související podřízené záznamy. Nebo můžete volat <xref:System.Data.DataRow.GetParentRow%2A> metodu <xref:System.Data.DataRow> v podřízené tabulce. Tato metoda vrací jedinou <xref:System.Data.DataRow> z nadřazené tabulky.  
  
 Tato stránka obsahuje příklady použití typové datové sady. Informace o navigace v relacích v netypové datové sady, naleznete v tématu [procházení datových relací](http://msdn.microsoft.com/library/e5e673f4-9b44-45ae-aaea-c504d1cc5d3e).  
  
> [!NOTE]
>  Pokud pracujete v aplikaci Windows Forms a používání funkcí datové vazby k zobrazení dat, generovaný návrhářem formuláře může poskytnout dostatek funkcí pro vaši aplikaci. Další informace najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Konkrétně, naleznete v tématu[postupy: zobrazení souvisejících dat ve formulářové aplikaci Windows](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md) a [návod: zobrazování souvisejících dat ve formuláři Windows Forms](../data-tools/walkthrough-displaying-related-data-on-a-windows-form.md).  
  
 Následující příklady kódu ukazují, jak procházet nahoru a dolů vztahy v typových datových sadách. Příklady použití kód zadali <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) a vygenerovaný `FindBy` *PrimaryKey* (`FindByCustomerID`) metody pro vyhledání požadovaný řádek a vrácení souvisejících záznamů. V příkladech kompilace a spuštění správně pouze v případě, že máte:  
  
- Instance datovou sadu s názvem `NorthwindDataSet` s `Customers` tabulky.  
  
- `Orders` Tabulky.  
  
- Relace s názvem `FK_Orders_Customers`týkající se dvěma tabulkami, které jsou k dispozici obor kódu  
  
  Kromě toho obou tabulek muset být naplněný daty pro záznamy, které se mají vrátit.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Vrátit podřízené záznamy vybraný nadřazený záznam  
  
-   Volání <xref:System.Data.DataRow.GetChildRows%2A> metoda konkrétní `Customers` data řádku a vrátí řádky z pole `Orders` tabulky:  
  
     [!code-csharp[VbRaddataDatasets#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDatasets#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#6)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Chcete-li vrátit nadřazený záznam vybraný podřízený záznam  
  
-   Volání <xref:System.Data.DataRow.GetParentRow%2A> metoda konkrétní `Orders` řádek dat a vrátí jeden řádek z `Customers` tabulky:  
  
     [!code-csharp[VbRaddataDatasets#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDatasets#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#7)]

