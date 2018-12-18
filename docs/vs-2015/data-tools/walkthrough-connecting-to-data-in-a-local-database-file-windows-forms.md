---
title: 'Návod: Připojování k datům v lokálního databázového souboru (Windows Forms) | Dokumentace Microsoftu'
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
- databases, connecting to
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 71898c88a8d7a1d4a119a7e7a932e295ae12eb34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176160"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>Návod: Připojování k datům v lokálním databázovém souboru (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data z místního databázového souboru můžete v aplikaci snadno a rychle zobrazit vytvořením datové sady a potom přidáním ovládacích prvků vázaných na data do aplikace. V tomto návodu budete zobrazovat data z lokálního databázového souboru, který jste vytvořili podle pokynů v [vytvoření databáze SQL pomocí návrháře](../data-tools/create-a-sql-database-by-using-a-designer.md). Po vytvoření projektu Windows Forms se k této databázi připojíte a určíte, že chcete data z tabulky Zákazníci zobrazit v datové mřížce ve formuláři pro aplikaci.  
  
 Při vytvoření databáze v aplikaci Visual Studio 2013 se modul SQL Server Express LocalDB používá pro přístup k souboru databáze (.mdf) v aplikaci SQL Server 2012. V dřívějších verzích sady Visual Studio slouží modul SQL Server Express k přístupu k souboru databáze (.mdf). Zobrazit [přehled lokálních dat](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 Tento návod zahrnuje následující úlohy:  
  
-   [Vytvoření a konfigurace datové sady](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Přidání ovládacích prvků vázaných na data](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li dokončit tento návod, potřebujete přístup k databázi SampleDatabase.mdf, kterou vytvoříte dokončením [vytvoření databáze SQL pomocí návrháře](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Vytvoření a konfigurace datové sady  
  
#### <a name="to-create-and-configure-a-dataset"></a>Vytvoření a konfigurace datové sady  
  
1.  Vytvoření projektu Windows Forms a pojmenujte ho **ConnectLocalData**.  
  
     Zobrazit [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
2.  Pokud **zdroje dat** se nezobrazí okno, stiskněte klávesy Shift + Alt + D nebo na panelu nabídek zvolte **zobrazení**, **ostatní Windows**, **Zobrazitzdrojedat**.  
  
3.  V **zdroje dat** okna, vyberte **přidat nový zdroj dat** odkaz.  
  
     V **Průvodce konfigurací zdroje dat**, zvolte **Další** tlačítko, čímž přijmete výchozí nastavení.  
  
4.  Na **vyberte datové připojení** zvolte **nové připojení** tlačítko.  
  
     **Zvolit zdroj dat** zobrazí se dialogové okno.  
  
5.  V **zdroj dat** klikněte na položku **soubor databáze Microsoft SQL Server**a klikněte na tlačítko **pokračovat** tlačítko.  
  
     **Přidat připojení** zobrazí se dialogové okno.  
  
6.  V **název souboru databáze** zadejte soubor, který jste vytvořili v návodu [vytvoření databáze SQL pomocí návrháře](../data-tools/create-a-sql-database-by-using-a-designer.md), nebo zvolte **Procházet** tlačítko a pak vyhledejte Tento soubor.  
  
     Ve výchozím nastavení, soubor je v seznamu Uživatelé\\*Váš_účet*\Documents\Visual Studio *verze*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough.  
  
7.  V části **Přihlaste se k serveru**, přijměte výchozí hodnoty, zvolte **OK** tlačítko a klikněte na tlačítko **Další** tlačítko.  
  
    > [!NOTE]
    >  Při připojení k lokálnímu databázovému souboru můžete v projektu vytvořit kopii databáze nebo můžete připojit soubor databáze z jeho aktuálního umístění. Zobrazit [postupy: Správa lokálních datových souborů ve vašem projektu](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  V dialogovém okně, které se zobrazí, zvolte **Ano** zkopírovat databázový soubor do projektu.  
  
9. Na **uložit připojovací řetězec do konfiguračního souboru aplikace** zvolte **Další** tlačítko.  
  
10. Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky** uzlu, vyberte **zákazníkům** a **objednávky** zaškrtávací políčka a pak Zvolte **Dokončit** tlačítko.  
  
     **SampleDatabaseDataSet** se přidá do vašeho projektu a **zákazníkům** a **objednávky** tabulky se zobrazí v **zdroje dat** okna.  
  
##  <a name="BKMK_AddCtrls"></a> Přidání ovládacích prvků vázaných na data  
  
#### <a name="to-add-data-bound-controls"></a>Přidání ovládacích prvků vázaných na data  
  
1.  Přesuňte hlavní **zákazníkům** uzlu z **zdroje dat** okna do **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> a pruh nástrojů (<xref:System.Windows.Forms.BindingNavigator>) pro procházení záznamů se zobrazí ve formuláři. A [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent.  
  
2.  Chcete-li spustit aplikaci a zobrazit data, která jste přidali v předchozím návodu, stiskněte klávesu F5.  
  
3.  Vyberte žlutou ikonu přidání (![přidat tlačítko ve formuláři Windows](../data-tools/media/addrecord.png "AddRecord")), přidejte záznam zákazníka a následně změny uložte zvolením ikony disku (![tlačítko Uložit ve formuláři Windows](../data-tools/media/saveinwf.png "SaveInWF")).  
  
4.  Odstranit záznam, který jste právě vytvořili, že jej vyberete a potom kliknete na červenou ikonu odstranění (![tlačítko Odstranit v podobě Windows](../data-tools/media/deleterecord.png "OdstranitZáznam")).  
  
## <a name="next-steps"></a>Další kroky  
 Můžete vytvořit nebo upravit objekty v datové sadě, pokud otevřete zdroj dat v [vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md). Můžete také přidat logiku ověřování k <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> události tabulek dat v datové sadě. Zobrazit [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled lokálních dat](../data-tools/local-data-overview.md)   
 [Postupy: Správa lokálních datových souborů ve vašem projektu](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)