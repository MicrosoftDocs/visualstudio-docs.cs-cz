---
title: Uložení datové sady ve formátu XML | Dokumentace Microsoftu
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
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a91bc594f2f028f7dfc7a11263b7aac23150b7f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287570"
---
# <a name="save-a-dataset-as-xml"></a>Uložení datové sady ve formátu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Data XML v datové sadě je možný voláním dostupné metody XML v datové sadě. K ukládání dat ve formátu XML, lze volat buď <xref:System.Data.DataSet.GetXml%2A> metoda nebo <xref:System.Data.DataSet.WriteXml%2A> metodu <xref:System.Data.DataSet>.  
  
 Volání <xref:System.Data.DataSet.GetXml%2A> metoda vrátí řetězec, který obsahuje data ze všech tabulek dat v datové sadě, který je formátován jako XML.  
  
 Volání <xref:System.Data.DataSet.WriteXml%2A> metoda odesílá data ve formátu XML do souboru, který zadáte.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Chcete-li uložit data v datové sadě ve formátu XML do proměnné  
  
-   <xref:System.Data.DataSet.GetXml%2A> Metoda vrátí hodnotu <xref:System.String>. To znamená, že deklarujete proměnnou typu <xref:System.String> a přiřaďte ho výsledky <xref:System.Data.DataSet.GetXml%2A> metody.  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Chcete-li uložit data v datové sadě ve formátu XML do souboru  
  
-   <xref:System.Data.DataSet.WriteXml%2A> Metoda má několik přetížení. Následující kód ukazuje, jak uložit data do souboru. Deklarujte proměnnou a přiřaďte ho platnou cestu k uložení souboru.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Viz také  
 [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)

