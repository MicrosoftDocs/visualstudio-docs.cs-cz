---
title: 'Postupy: vytváření dotazů TableAdapter | Dokumentace Microsoftu'
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
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c4b800bcb70e41e1d80bf9a0a37d72f08f78c7a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195543"
---
# <a name="how-to-create-tableadapter-queries"></a>Postupy: Vytváření dotazů TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotazy objektu TableAdapter jsou příkazy SQL nebo úložné procedury, které vaše aplikace může provést proti databázi.  
  
 Přidejte tolik dotazů do TableAdapter vaše aplikace vyžaduje. Dotazy objektu TableAdapter se zobrazí jako metody na objektu typu TableAdapter. Když vytvoříte dotaz s názvem `FillByCity` , která přebírá parametr představující hodnotu Město, dotaz se přidá do objektu TableAdapter. Přidá se jako typová metoda, která přebírá správný typ parametru jako argument – v tomto případě řetězec představující hodnotu město. Dotaz TableAdapter stejně jako libovolnou metodu volání na libovolný objekt. Například následující kód se provádí `FillByCity` dotazu a výplní `Customers` tabulky s všichni zákazníci s hodnotou Město `Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 Dotazů TableAdapter můžete přejít k vyplnění tabulky dat (`Fill` a `FillBy` dotazy) nebo vrátí nové tabulky data naplněný daty vrácené dotazem (`GetData` a `GetDataBy` dotazy).  
  
 Lze přidat dotazy na existující TableAdapter spuštěním [úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md). (Klikněte pravým tlačítkem na libovolný TableAdapter a zvolte **přidat dotaz**.)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>Vytvořit dotaz v návrháři datových sad  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>Přidání dotazu TableAdapter v návrháři datových sad  
  
1.  Otevřete datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Klikněte pravým tlačítkem na požadovaný TableAdapter a vyberte **přidat dotaz**.  
  
     -nebo-  
  
3.  Přetáhněte **dotazu** z **datovou sadu** karty **nástrojů** do tabulky v návrháři.  
  
     **Průvodce nastavením dotazu TableAdapter** otevře.  
  
4.  Dokončete průvodce. dotaz je přidána do objektu TableAdapter.  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Vytvořit dotaz přímo na formulář v nástrojích pro aplikace Windows  
 Pokud máte instanci objektu typu TableAdapter na formuláři můžete přidat do dotazu pomocí [dialogové okno Tvůrce kritérií vyhledávání](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d), přidává <xref:System.Windows.Forms.ToolStrip> ovládacího prvku na formulář, který přijímá všechny vstupní parametry vyžadované dotazu, stejně jako tlačítko pro spuštění dotazu.  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>Přidání dotazu TableAdapter pomocí dialogového okna kritéria vyhledávání  
  
1.  Vyberte na hlavním panelu Komponenty TableAdapter.  
  
2.  Klikněte na inteligentní značku objektu TableAdapter a zvolte **přidat dotaz**.  
  
3.  Vyplňte dialogové okno a dotaz se přidá do objektu TableAdapter. Další informace najdete v tématu [dialogové okno Tvůrce kritérií vyhledávání](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d).  
  
## <a name="see-also"></a>Viz také  
 [TableAdapter – přehled](../data-tools/tableadapter-overview.md)   
 [Postupy: upravování dotazů TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Vytváření a úpravy typovaných datových sad](../data-tools/creating-and-editing-typed-datasets.md)   
 [Přidat nové zdroje dat](../data-tools/add-new-data-sources.md)   
 [Postupy: připojení k datům v databázi](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Postupy: navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Návod: Zobrazování dat ve formuláři Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Návod: Vytváření TableAdapter s více dotazy](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)