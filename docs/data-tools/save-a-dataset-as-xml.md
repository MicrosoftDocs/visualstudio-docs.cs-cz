---
title: Uložení datové sady ve formátu XML
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5b3aa23cb0fde98b4da4225b8e255b7cd6e7aef5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641345"
---
# <a name="save-a-dataset-as-xml"></a>Uložení datové sady ve formátu XML

Přístup k datům XML v datové sadě voláním dostupných metod XML pro datovou sadu. Chcete-li uložit data ve formátu XML, můžete zavolat buď metodu <xref:System.Data.DataSet.GetXml%2A>, nebo metodu <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet>.

Volání metody <xref:System.Data.DataSet.GetXml%2A> vrátí řetězec, který obsahuje data ze všech tabulek dat v datové sadě, která je formátována jako XML.

Volání metody <xref:System.Data.DataSet.WriteXml%2A> odesílá data ve formátu XML do souboru, který zadáte.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Uložení dat v datové sadě jako XML do proměnné

- Metoda <xref:System.Data.DataSet.GetXml%2A> vrátí <xref:System.String>. Deklarujte proměnnou typu <xref:System.String> a přiřaďte jí výsledky metody <xref:System.Data.DataSet.GetXml%2A>.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Uložení dat v datové sadě jako XML do souboru

- Metoda <xref:System.Data.DataSet.WriteXml%2A> má několik přetížení. Deklarujte proměnnou a přiřaďte jí platnou cestu k uložení souboru do. Následující kód ukazuje, jak uložit data do souboru:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Viz také:

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)