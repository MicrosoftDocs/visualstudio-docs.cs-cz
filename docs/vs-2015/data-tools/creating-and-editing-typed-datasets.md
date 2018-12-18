---
title: Vytváření a úpravy typové datové sady | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8c18717cd2a5c7e05b79dbe575d919ef0c8670dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225835"
---
# <a name="creating-and-editing-typed-datasets"></a>Vytváření a úpravy typovaných datových sad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Návrhář Dataset** je sada vizuálních nástrojů, které můžete použít k vytvoření a úprava typové datové sady a jednotlivých položek, které obsahují.  
  
 **Návrhář Dataset** poskytuje vizuální reprezentace objektů obsažených v typových datových sadách. Vytvoření a úprava [objekty TableAdapter](../data-tools/tableadapter-overview.md), [dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s, a <xref:System.Data.DataRelation>s **Návrhář Dataset**.  
  
 Chcete-li otevřít **Návrhář Dataset**, dvakrát klikněte na datovou sadu v **Průzkumníku řešení**, nebo klikněte pravým tlačítkem na datové sady v **zdroje dat** okna a klikněte na **upravit Datové sady pomocí návrháře**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3). Přidání nového <xref:System.Data.DataSet> položka s **přidat novou položku** se otevře dialogové okno **Návrhář Dataset** s prázdnou datovou sadu připravené pro úpravy.  
  
> [!NOTE]
>  **Návrhář Dataset** lze použít k rozšíření funkcí datové sady. Klikněte dvakrát na návrhové ploše nebo klikněte pravým tlačítkem myši a zvolte **zobrazit kód** k vytvoření souboru částečné třídy, ve kterém můžete přidat kód do datové sady, které nebude možné změnit ani odstranit návrhářem. Informace o rozšíření funkcí objektů TableAdapter, naleznete v tématu [rozšíření funkcí TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 V následující tabulce jsou uvedeny běžné úkoly můžete provést pomocí **Návrhář Dataset**.  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Vytvoření objektu typu TableAdapter|[Vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md)|  
|Úpravy objektu typu TableAdapter|[Postupy: upravování TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|Vytvořit dotaz TableAdapter|[Postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Úprava dotazu TableAdapter|[Postupy: upravování dotazů TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Vytvoření <xref:System.Data.DataTable>|[Postupy: vytváření datových tabulek](../data-tools/how-to-create-data-tables.md)|  
|Upravit <xref:System.Data.DataTable>|[Navrhování DataTables](../data-tools/designing-datatables.md)|  
|Vytvoření <xref:System.Data.DataColumn>|[Postupy: přidávání sloupců do DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|Vytvoření vztahu mezi dvěma <xref:System.Data.DataTable>s|[Postupy: vytváření DataRelations pomocí návrháře datových sad](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|Rozšíření funkcí datové sady|[Postupy: rozšíření funkcí datové sady](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|Přidání ověřování do datové tabulky <xref:System.Data.DataTable.ColumnChanging> událostí|[Postupy: ověřování dat během úprav sloupců](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|Přidání ověřování do datové tabulky <xref:System.Data.DataTable.RowChanging> událostí|[Postupy: ověřování dat během úprav řádků](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>Vytváření objektů na návrhové ploše  
 Přidání a úpravy jednotlivé objekty, které tvoří datovou sadu můžete vytvořit datové sady. Následující tabulka obsahuje vysvětlení různých objektů v **datovou sadu** kartě **nástrojů** , který lze přetáhnout na návrhovou plochu:  
  
|Objekt|Popis|  
|------------|-----------------|  
|TableAdapter|Obsahuje kolekci příkazů dat a datové připojení, které se používají ke komunikaci s podkladové databázi a vyplnění tabulky dat. Další informace najdete v tématu [TableAdapter – přehled](../data-tools/tableadapter-overview.md) a [vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md).|  
|Dotazy|Dotazy objektu TableAdapter jsou silného typu metody, které jsou spouštěny příkazy SQL a uložených procedur. Spuštění dotazu TableAdapter naplní tabulku dat s daty nebo provádí jiné databázové úlohy. Další informace najdete v tématu [postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md). Přetáhněte dotaz na tabulku přidá dotaz do tabulky, že přetáhnete dotaz na prázdnou oblast **Návrhář Dataset** vytvoří globální dotaz. Další informace najdete v tématu [postupy: přidání globálních dotazů do TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Představuje kolekci v paměť řádků vrácených z databáze.|  
|Relace (<xref:System.Data.DataRelation>)|Představuje relaci nadřazený podřízený mezi dvěma <xref:System.Data.DataTable>s. Další informace najdete v tématu [Úvod do objektů DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192) a [návod: vytvoření vztahu mezi datovými tabulkami](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82).|  
  
> [!NOTE]
>  **Návrhář Dataset** připojí k podkladové databázi jenom v případě datová sada se vytvoří; návrháře automaticky nerozpozná následné změny v databázi. Pokud chcete aktualizovat existující XSD, znovu spusťte **Průvodce konfigurací**. Pokud jste změnili vztahy tabulky, odeberte a znovu přidejte příslušné tabulky, které chcete XSD.  
  
## <a name="linq-to-dataset"></a>Technologie LINQ to Dataset  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] umožňuje [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) nad daty v <xref:System.Data.DataSet> objektu. Další informace najdete v tématu [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření datové sady pomocí návrháře datových sad](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Návod: Vytváření TableAdapter s více dotazy](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Návod: Vytváření DataTable v návrháři datových sad](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Návod: Vytvoření relace mezi tabulkami dat](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [Návod: Zobrazování dat ve formuláři Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Okno zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)