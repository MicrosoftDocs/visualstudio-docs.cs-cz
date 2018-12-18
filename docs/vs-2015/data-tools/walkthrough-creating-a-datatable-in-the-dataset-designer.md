---
title: 'Návod: Vytváření DataTable v návrháři datových sad | Dokumentace Microsoftu'
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1f0f31528239794b9c7a3b4a4bf98542ed4bbcf2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299959"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Návod: Vytváření DataTable v Návrháři DataSet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod popisuje, jak vytvořit <xref:System.Data.DataTable> (bez objektu TableAdapter) pomocí **Návrhář Dataset**. Informace o vytváření tabulek dat, které obsahují objekty TableAdapter najdete v tématu [vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření nového projektu aplikace Windows  
  
-   Přidání nové datové sady do aplikace  
  
-   Přidat novou tabulku dat do datové sady  
  
-   Přidávání sloupců do tabulky dat  
  
-   Nastavení primární klíč pro tabulku  
  
## <a name="creating-a-new-windows-application"></a>Vytvoření nové aplikace systému Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Chcete-li vytvořit nový projekt aplikace Windows  
  
1.  Z **souboru** nabídky, vytvořte nový projekt.  
  
2.  Zvolte programovací jazyk v **typy projektů** podokně.  
  
3.  Klikněte na tlačítko **aplikace Windows** v **šablony** podokně.  
  
4.  Pojmenujte projekt `DataTableWalkthrough`a potom klikněte na tlačítko **OK**.  
  
     Visual Studio přidá projekt do **Průzkumníka řešení** a zobrazí **Form1** v návrháři.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Přidání nové datové sady do aplikace  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Postup přidání nové položky datové sady do projektu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
     Přidání nové položky se zobrazí dialogové okno.  
  
2.  V **šablony** vyberte **datovou sadu**.  
  
3.  Klikněte na tlačítko **přidat**.  
  
     Visual Studio přidá soubor s názvem **DataSet1.xsd** do projektu a otevřete ho v **Návrhář Dataset**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Přidání nové datové tabulky do datové sady  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Chcete-li přidat novou tabulku dat do datové sady  
  
1.  Přetáhněte **DataTable** z **datovou sadu** kartě **nástrojů** na **Návrhář Dataset**.  
  
     Tabulku s názvem **DataTable1** se přidá do datové sady.  
  
    > [!NOTE]
    >  Vytvoření tabulky dat, která zahrnuje TableAdapter, najdete v článku [návod: vytváření TableAdapter s více dotazy](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Klikněte na záhlaví **DataTable1** a přejmenujte jej `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Přidávání sloupců do tabulky dat  
  
#### <a name="to-add-columns-to-the-data-table"></a>Přidání sloupců do tabulky dat  
  
1.  Klikněte pravým tlačítkem myši **Hudba** tabulky. Přejděte na **přidat**a potom klikněte na tlačítko **sloupec**.  
  
2.  Název sloupce `SongID`.  
  
3.  V **vlastnosti** okno, nastaveno <xref:System.Data.DataColumn.DataType%2A> vlastnost <xref:System.Int16?displayProperty=fullName>.  
  
4.  Tento postup opakujte a přidejte následující sloupce:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Nastavení primární klíč pro tabulku  
 Všechny tabulky dat by měl mít primární klíč. Primární klíč jednoznačně identifikuje konkrétní záznam v tabulce dat.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Chcete-li nastavit primární klíč tabulky dat  
  
-   Klikněte pravým tlačítkem myši **SongID** sloupec a pak klikněte na tlačítko **nastavit primární klíč**.  
  
     Ikona klíče se zobrazí vedle **SongID** sloupce.  
  
## <a name="saving-your-project"></a>Uložení projektu  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>Chcete-li uložit projekt DataTableWalkthrough  
  
-   Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste vytvořili v tabulce, můžete chtít provést jednu z následujících akcí:  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Vytvoření formuláře pro vstupní data|[Návod: Zobrazování dat ve formuláři Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Přidání dat do tabulky|[Přidání dat do DataTable určitého](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b).|  
|Zobrazení dat v tabulce|[Zobrazení dat v datové tabulce](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc).|  
|Úprava dat|[Úpravy datových tabulek](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|Odstranit řádek z tabulky|[Odstranění datového řádku](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>Viz také  
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)   
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)