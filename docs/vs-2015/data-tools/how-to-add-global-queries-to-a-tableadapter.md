---
title: 'Postupy: přidávání globálních dotazů do TableAdapter | Dokumentace Microsoftu'
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: fd185c9a6803a5e66b1fdaac0f040815328ddb82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193892"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>Postupy: přidávání globálních dotazů do TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Globální dotazy* jsou dotazy SQL, které vrací jedinou hodnotu (skalární) nebo žádnou hodnotu. Globální funkce obvykle provádění databázových operací, jako je například vložení, aktualizace, odstranění a agregovat informace, jako je například vrací počet zákazníků v tabulce nebo celkové poplatky pro všechny položky v určitém pořadí.  
  
 Přidávání globálních dotazů spuštěním **Průvodce nastavením dotazu TableAdapter** v rámci **Návrhář Dataset**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>Chcete-li přidat globální dotaz na datovou sadu  
  
1.  Otevřete datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Přetáhněte **dotazu** z **datovou sadu** karty **nástrojů** na prázdnou oblast **Návrhář Dataset**.  
  
     [Úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md) otevře.  
  
3.  Zvolte připojení pro dotaz, který chcete použít. Můžete ho ze seznamu vyberte nebo vytvořte nové připojení. Pokud vytvoříte nové připojení, budete mít možnost ho uložit do konfiguračního souboru aplikace. Další informace najdete v tématu [postupy: uložení a úpravy připojovacích řetězců](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
4.  Zvolte, jestli chcete používat příkazy SQL nebo úložné procedury.  
  
5.  Vyberte uloženou proceduru pro použití nebo na **zvolit typ dotazu** stránku průvodce, zvolte typ dotazu a pak klikněte na **Další**.  
  
6.  Zadejte dotaz, který provede požadovanou úlohu, například `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Přetažení dotaz přímo na **Návrhář Dataset** vytvoří metodu, která vrátí pouze skalární hodnoty (single). Během dotazu nebo uložené procedury, které jste vybrali může vrátit více než jednu hodnotu, vrátí metoda vytvořené průvodcem pouze jednu hodnotu. Dotaz může například vrátit první sloupec prvního řádku vracená data.  
  
7.  Dokončete průvodce. dotaz se přidá do **Návrhář Dataset**. Informace o spouštění dotazu naleznete v tématu [postupy: spuštění dotazů TableAdapter](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Vytváření a úpravy typovaných datových sad](../data-tools/creating-and-editing-typed-datasets.md)   
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [Postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Postupy: navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Návod: Zobrazování dat ve formuláři Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)