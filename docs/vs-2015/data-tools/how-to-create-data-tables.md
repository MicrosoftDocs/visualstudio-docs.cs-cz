---
title: 'Postupy: vytváření datových tabulek | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8b26bf0cfbd387f33f9f038d5927db795a8f2769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288909"
---
# <a name="how-to-create-data-tables"></a>Postupy: Vytváření datových tabulek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data mohou být uloženy v paměti v <xref:System.Data.DataTable> objekty. (Datové sady jsou tvořené <xref:System.Data.DataTable> objekty.) Obvykle vytvoříte nové tabulky data pomocí objektů TableAdapter [Průvodce nastavením TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) nebo přetažením databázových objektů z **Průzkumníka serveru** na **návrháře datových sad** .  
  
 Tabulky dat jsou vytvořeny jako byproduct při vytváření nových prvků TableAdapters ve [Průvodce konfigurací zdroje dat](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) stejně, se můžete také vytvořit nezávisle na sobě, ale. Vytvořit samostatnou tabulku dat přetažením <xref:System.Data.DataTable> objektu z **datovou sadu** kartě **nástrojů** na **Návrhář Dataset**.  
  
> [!NOTE]
>  Vytvoření tabulek dat prostřednictvím kódu programu, najdete v tématu [vytvoření datové tabulky](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>Vytvoření datové tabulky pomocí TableAdapter  
 Datových tabulek pomocí instancí TableAdapter zahrnují metody, které vyplnit tabulku daty a zapsat změny zpět do databáze. Objekty TableAdapter vytvoříte spuštěním **Průvodce nastavením TableAdapter** nebo přetažením databázových objektů z **Průzkumníka serveru** na **Návrhář Dataset**.  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>Chcete-li vytvořit novou tabulku dat pomocí TableAdapter  
  
1.  Otevřete svou datovou sadu v **Návrhář Dataset**. Informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Přetáhněte **TableAdapter** z **datovou sadu** kartě **nástrojů** na **Návrhář Dataset**.  
  
     **Průvodce nastavením TableAdapter** otevře.  
  
3.  Dokončete průvodce. Další informace najdete v tématu [Průvodce nastavením TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>Chcete-li vytvořit nové tabulky data pomocí prvku TableAdapter z Průzkumníka serveru  
  
1.  Otevřete svou datovou sadu v **návrháře zdroje dat**.  
  
2.  Přetáhněte objekt databáze (například tabulky) z **Průzkumníka serveru** na **Návrhář Dataset**.  
  
## <a name="creating-a-standalone-datatable"></a>Vytvoření samostatné datové tabulky  
 Samostatné tabulky musí mít `Fill` implementovat logiku k vyplnění daty. Informace o vyplnění tabulek dat samostatné, naleznete v tématu [naplnění datové sady z adaptéru dat](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>Chcete-li vytvořit novou tabulku samostatné  
  
1.  Otevřete svou datovou sadu v **Návrhář Dataset**.  
  
2.  Přetáhněte <xref:System.Data.DataTable> z **datovou sadu** kartě **nástrojů** na **Návrhář Dataset**.  
  
3.  Přidáte sloupce pro definování dat tabulky. Další informace najdete v tématu [postupy: Přidání sloupců do DataTable určitého](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataTable>   
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Návod: Zobrazování dat ve formuláři Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Vytváření a úpravy typovaných datových sad](../data-tools/creating-and-editing-typed-datasets.md)   
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [Okno zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)