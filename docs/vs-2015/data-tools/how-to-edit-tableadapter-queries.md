---
title: 'Postupy: upravování dotazů TableAdapter | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DbSource
- vbdata.Microsoft.VSDesigner.DataSource.DbSource
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- queries [Visual Basic], editing
- TableAdapters, editing queries
- data [Visual Studio], TableAdapters
- editing queries
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 687336b979ef7e6d46ea6deb4a5682f3aec065be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287895"
---
# <a name="how-to-edit-tableadapter-queries"></a>Postupy: Upravování dotazů TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upravování dotazů TableAdapter s [úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md) v **Návrhář Dataset**. Dotaz TableAdapter by měl změnit, když už vyhovuje potřebám vaší aplikace. (Alternativně můžete vytvořit další dotazy na TableAdapter. Další informace o přidávání nových dotazů najdete v tématu [postupy: vytváření dotazů TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).)  
  
> [!NOTE]
>  Pokud [Průvodce nastavením TableAdapter](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) otevře místo **Průvodce nastavením dotazu TableAdapter**, je možná zvolen objektu TableAdapter hlavní `Fill` dotaz a není jednou z Další dotazy objektu TableAdapter. Pro informace o úpravách objektu TableAdapter hlavní `Fill` dotazu naleznete v tématu [jak: Edit TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
 ![TableAdapter s více dotazy](../data-tools/media/tableadapter.gif "TableAdapter")  
  
### <a name="to-edit-a-tableadapter-query"></a>Chcete-li upravit dotaz TableAdapter  
  
1.  Otevřete datovou sadu v **Návrhář Dataset**. Další informace najdete v tématu [postupy: otevření datové sady v návrháři datových sad](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Vyberte dotaz TableAdapter, který chcete upravit.  
  
3.  Dotaz TableAdapter pravým tlačítkem a vyberte **konfigurovat**.  
  
     **Průvodce nastavením dotazu TableAdapter** se otevře, můžete upravit dotaz nebo uloženou proceduru pro daný dotaz.  
  
4.  Dokončení **Průvodce nastavením dotazu TableAdapter** se změnami, které chcete. Další informace najdete v tématu [úpravy objektů TableAdapter](../data-tools/editing-tableadapters.md).  
  
## <a name="see-also"></a>Viz také  
 [Objekty TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)   
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)