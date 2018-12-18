---
title: 'Návod: Vytvoření datové sady pomocí návrháře datových sad | Dokumentace Microsoftu'
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d77d63cc82b7af6281183b3eae67d09b0454fffb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868258"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Návod: Vytvoření datové sady pomocí Návrháře DataSet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu vytvoříte datovou sadu pomocí **Návrhář Dataset**. Bude vás provedou procesem vytvoření nového projektu a přidání nové **datovou sadu** položku do ní. Naučíte se vytvářet tabulky na základě tabulek z databáze bez použití průvodce.  
  
 Úlohy v tomto návodu zahrnují:  
  
- Vytvoření nového **aplikace Windows** projektu.  
  
- Přidání prázdné **datovou sadu** položky do projektu.  
  
- Vytvoření a konfigurace zdroje dat v aplikaci sestavením datové sady s **Návrhář Dataset**.  
  
- Vytvoření připojení k databázi Northwind v **Průzkumníka serveru**.  
  
- Vytváření tabulek pomocí instancí TableAdapter v datové sadě založené na tabulkách v databázi.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 Pokud chcete dokončit tento návod, potřebujete:  
  
-   Přístup k ukázkové databázi Northwind (verze SQL Server nebo Access). Další informace najdete v tématu [postupy: Instalace ukázkových databází](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Vytvoření nového projektu aplikace systému Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Chcete-li vytvořit nový projekt aplikace Windows  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Zvolte programovací jazyk v **typy projektů** podokně.  
  
3.  Klikněte na tlačítko **aplikace Windows** v **šablony** podokně.  
  
4.  Pojmenujte projekt `DatasetDesignerWalkthrough`a potom klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přidá projekt do **Průzkumníka řešení** a nový formulář pro zobrazení v návrháři.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Přidání nové datové sady do aplikace  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Postup přidání nové položky datové sady do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
     **Přidat novou položku** zobrazí se dialogové okno.  
  
2.  V **šablony** pomocí boxingu **přidat novou položku** dialogové okno, klikněte na tlačítko **datovou sadu**.  
  
3.  Zadejte název datové sady `NorthwindDataset`a potom klikněte na tlačítko **přidat**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Přidá soubor s názvem **NorthwindDataset.xsd** do projektu a otevřete ho v **Návrhář Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Vytvoření datového připojení v Průzkumníku serveru  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Postup vytvoření připojení k databázi Northwind  
  
1.  Na **zobrazení** nabídky, klikněte na tlačítko **Průzkumníka serveru**.  
  
2.  V **Průzkumníka serveru**, klikněte na tlačítko **připojit k databázi** tlačítko.  
  
3.  Vytvořte připojení ke vzorové databázi Northwind.  
  
    > [!NOTE]
    >  V tomto návodu bude možné se připojit k databázi Northwind pomocí SQL serveru nebo pomocí verze aplikace Access.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Vytváření tabulek v datové sadě  
 V této části je vysvětlen postup přidávání tabulek do datové sady.  
  
#### <a name="to-create-the-customers-table"></a>Vytvoření tabulky Zákazníci  
  
1.  Rozbalte datová připojení, kterou jste vytvořili v **Průzkumníka serveru**a potom rozbalte **tabulky** uzlu.  
  
2.  Přetáhněte **zákazníkům** tabulce **Průzkumníka serveru** na **Návrhář Dataset**.  
  
     A **zákazníkům** tabulka dat a **CustomersTableAdapter** jsou přidány do datové sady.  
  
#### <a name="to-create-the-orders-table"></a>Vytvoření tabulky objednávek  
  
-   Přetáhněte **objednávky** tabulce **Průzkumníka serveru** na **Návrhář Dataset**.  
  
     **Objednávky** tabulka dat **OrdersTableAdapter**a datová relace mezi **zákazníkům** a **objednávky** tabulky jsou přidány do Datová sada.  
  
#### <a name="to-create-the-orderdetails-table"></a>Postup vytvoření tabulky OrderDetails  
  
-   Přetáhněte **OrderDetails** tabulce **Průzkumníka serveru** na **Návrhář Dataset**.  
  
     **OrderDetails** tabulka dat **pořadí DetailsTableAdapter**a datová relace mezi **objednávky** a **OrderDetails** tabulky jsou přidány do datové sady.  
  
## <a name="next-steps"></a>Další kroky  
  
### <a name="to-add-functionality-to-your-application"></a>Přidání funkčnosti do aplikace  
  
-   Uložte datovou sadu.  
  
-   Vyberte položky v **zdroje dat** okno a přetáhněte je na formuláři. Další informace najdete v tématu [ovládací prvky vazby Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Do instancí TableAdapter přidejte další dotazy. Další informace najdete v tématu [postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Přidejte logiku ověřování k událostem <xref:System.Data.DataTable.ColumnChanging> nebo <xref:System.Data.DataTable.RowChanging> tabulek dat v datové sadě. Další informace najdete v tématu [ověření dat v datových sadách](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Viz také  
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)