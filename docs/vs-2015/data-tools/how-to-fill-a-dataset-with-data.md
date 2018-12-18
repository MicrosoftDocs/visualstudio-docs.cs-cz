---
title: 'Postupy: vyplnění datové sady s daty | Dokumentace Microsoftu'
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
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f36aa2dac656f6fd27b656d0ddfb58a758eb6487
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295994"
---
# <a name="how-to-fill-a-dataset-with-data"></a>Postupy: vyplnění datové sady s daty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fráze "naplňování datové sady s daty" odkazuje na načtení dat do jednotlivých <xref:System.Data.DataTable> objekty, které tvoří datové sady. Vyplnění tabulek dat provádění dotazů TableAdapter nebo spuštěním adaptéru dat (například <xref:System.Data.SqlClient.SqlDataAdapter>) příkazy.  
  
 Určuje, zda byste měli použít adaptérů objekty TableAdapter nebo dat závisí na způsobu vytvoření datové sady. Je-li použít nástroje návrhu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], například [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f), vaše datová sada obsahuje objekty TableAdapter. Další informace o TableAdapters, naleznete v tématu [TableAdapter – přehled](../data-tools/tableadapter-overview.md). Pokud jste vytvořili datovou sadu prostřednictvím kódu programu, obvykle musíte k vytvoření adaptérů dat k načtení dat do datových tabulek.  
  
> [!NOTE]
>  Při přetažení položky z [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) do formuláře, kód k vyplnění tabulky dat s daty je automaticky přidán do `Form_Load` obslužné rutiny události. Otevřete formulář v editoru kódu zobrazíte syntaxe tak, aby vyplnil konkrétní tabulky. Pokud nechcete k vyplnění tabulky při načtení formuláře, můžete tento kód přesunout do jiné metody nebo jej odeberte úplně.  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>Naplnění datové sady pomocí prvku TableAdapter  
 Dotaz můžete volat na TableAdapter načtení dat do tabulek dat v datové sadě. Předání <xref:System.Data.DataTable> chcete vyplnit dotazu TableAdapter. Pokud parametry dotazu, předejte metodě i ty. Pokud datová sada obsahuje více tabulek, by měly mít samostatné objekty TableAdapter pro každou tabulku a musí proto vyplnit samostatně každá tabulka.  
  
> [!NOTE]
>  Ve výchozím nastavení při každém spuštění dotazu TableAdapter, data v tabulce odstraněna před výsledky dotazu do tabulky. Můžete zachovat existující data v tabulce a připojit tak, že nastavíte objektu TableAdapter výsledky `ClearBeforeFill` vlastnost `false`.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>Naplnění datové sady dat pomocí TableAdapter  
  
1.  Otevřete formulář nebo součástí **Editor kódu**.  
  
2.  Přidejte kód kdekoli ve vaší aplikaci, které je potřeba načíst data tabulky s daty. Pokud váš dotaz se nedají zadat parametry, předejte <xref:System.Data.DataTable> chcete vyplnit. Kód by měl vypadat nějak takto:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  Pokud váš dotaz parametry, předejte <xref:System.Data.DataTable> chcete vyplnit a parametry očekávání v dotazu. V závislosti na skutečné parametry v dotazu by vypadalo podobně jako následující příklady kódu:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>Naplnění datové sady pomocí adaptéru dat  
 Volání datový adaptér `Fill` metody. To způsobí, že adaptér, který má spustit příkaz SQL nebo uloženou proceduru odkazovat v jeho `SelectCommand` vlastnost a vloží výsledky do tabulky v datové sadě. Pokud datová sada obsahuje více tabulek, by měly mít samostatné datové adaptéry pro každou tabulku a musí proto vyplnit samostatně každá tabulka.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>K vyplnění datové sady s daty pomocí adaptéru dat  
  
-   Volání <xref:System.Data.Common.DataAdapter.Fill%2A> metodu <xref:System.Data.Common.DataAdapter>, předejte <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> načtení dat do. Příklad:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     Název by měl obvykle poskytnete <xref:System.Data.DataTable> načtení dat do. Pokud předáte z name <xref:System.Data.DataSet> namísto tabulky konkrétní data, <xref:System.Data.DataTable> s názvem `Table1` bude přidána do datové sady a načíst výsledky z databáze (na rozdíl od načtení dat v existujícím <xref:System.Data.DataTable> v datové sadě). Další informace najdete v tématu [naplnění datové sady z adaptéru dat](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
## <a name="see-also"></a>Viz také  
 [Vyplnění datové sady s použitím objektů TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)