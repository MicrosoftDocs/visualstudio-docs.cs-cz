---
title: Uložení datové sady ve formátu XML
description: Uložte datovou sadu jako XML. Přístup k datům XML v datové sadě voláním dostupných metod XML pro datovou sadu, například GetXml – nebo WriteXml.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9030740a25312ea1463b950e34061884e9487ba4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858524"
---
# <a name="save-a-dataset-as-xml"></a>Uložení datové sady ve formátu XML

Přístup k datům XML v datové sadě voláním dostupných metod XML pro datovou sadu. Chcete-li uložit data ve formátu XML, můžete zavolat buď <xref:System.Data.DataSet.GetXml%2A> metodu, nebo <xref:System.Data.DataSet.WriteXml%2A> metodu <xref:System.Data.DataSet> .

Volání <xref:System.Data.DataSet.GetXml%2A> metody vrátí řetězec, který obsahuje data ze všech tabulek dat v datové sadě, která je formátována jako XML.

Volání <xref:System.Data.DataSet.WriteXml%2A> metody odesílá data ve formátu XML do souboru, který zadáte.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Uložení dat v datové sadě jako XML do proměnné

- <xref:System.Data.DataSet.GetXml%2A>Metoda vrátí <xref:System.String> . Deklarujte proměnnou typu <xref:System.String> a přiřaďte jí výsledky <xref:System.Data.DataSet.GetXml%2A> metody.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Uložení dat v datové sadě jako XML do souboru

- <xref:System.Data.DataSet.WriteXml%2A>Metoda má několik přetížení. Deklarujte proměnnou a přiřaďte jí platnou cestu k uložení souboru do. Následující kód ukazuje, jak uložit data do souboru:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Viz také

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
