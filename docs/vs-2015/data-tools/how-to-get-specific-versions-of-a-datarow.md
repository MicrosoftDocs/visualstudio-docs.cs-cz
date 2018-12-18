---
title: 'Postupy: získání konkrétních verzí DataRow | Dokumentace Microsoftu'
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
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 5bd8ae12c77c671e375043a0381a4b580d1a03d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255482"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>Postupy: Získání konkrétních verzí DataRow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při změně na řádky dat, datová sada zachová původní (<xref:System.Data.DataRowVersion>) i novou (<xref:System.Data.DataRowVersion>) verzi řádku. Například před voláním `AcceptChanges` metoda, vaše aplikace můžou přistupovat k různé verze záznamu (jak je definováno ve <xref:System.Data.DataRowVersion> výčet) a odpovídajícím způsobem zpracovávat změny.  
  
> [!NOTE]
>  Různé verze řádku existují pouze poté, co byl upraven a před zaznamenala `AcceptChanges` metodu s názvem. Po `AcceptChanges` byla volána metoda, aktuální a původní verze jsou stejné.  
  
 Předání <xref:System.Data.DataRowVersion> hodnotu spolu indexem sloupce (nebo název sloupce jako řetězce) vrátí hodnotu z verze konkrétního řádku tohoto sloupce. Změněný sloupec je rozpoznán během <xref:System.Data.DataTable.ColumnChanging> a <xref:System.Data.DataTable.ColumnChanged> události, aby byl vhodný čas projít různé verze řádků pro účely ověření. Pokud jste dočasně pozastavili omezení, tyto události nebudou vyvolány a budete muset programově určit sloupce, které se změnily. Uděláte to tak iterace <xref:System.Data.DataTable.Columns%2A> kolekce a porovnáním různých <xref:System.Data.DataRowVersion> hodnoty.  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>Přístup k původní verzi objektu DataRow  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Získání původní verze záznamu  
  
-   Přístup k hodnotě sloupce předávajícího <xref:System.Data.DataRowVersion> řádku, který chcete vrátit.  
  
     Následující příklad ukazuje, jak můžete <xref:System.Data.DataRowVersion> hodnotu k získání původní hodnoty `CompanyName` pole <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>Přístup k aktuální verzi objektu DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Chcete-li získat aktuální verze záznamu  
  
-   Přístup k hodnotě sloupce a přidejte parametr do indexu označujícího, kterou verzi řádku chcete vrátit.  
  
     Následující příklad ukazuje, jak můžete <xref:System.Data.DataRowVersion> hodnotu k získání aktuální hodnoty `CompanyName` pole <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>Viz také  
 [Úpravy dat v aplikaci](../data-tools/editing-data-in-your-application.md)   
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Ukládání dat](../data-tools/saving-data.md)   
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Přehled datových aplikacích v sadě Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Připojování k datům v sadě Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Načítají se Data do vaší aplikace](../data-tools/fetching-data-into-your-application.md)   
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)