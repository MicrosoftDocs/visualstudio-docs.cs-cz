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
ms.openlocfilehash: 42974852a3051fd3473b6b23d880eeb38b966b95
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216199"
---
# <a name="save-a-dataset-as-xml"></a>Uložení datové sady ve formátu XML

Přístup k datům XML v datové sadě voláním dostupných metod XML pro datovou sadu. Chcete-li uložit data ve formátu XML, můžete zavolat buď <xref:System.Data.DataSet.GetXml%2A> metodu, nebo <xref:System.Data.DataSet.WriteXml%2A> metodu <xref:System.Data.DataSet> .

Volání <xref:System.Data.DataSet.GetXml%2A> metody vrátí řetězec, který obsahuje data ze všech tabulek dat v datové sadě, která je formátována jako XML.

Volání <xref:System.Data.DataSet.WriteXml%2A> metody odesílá data ve formátu XML do souboru, který zadáte.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Uložení dat v datové sadě jako XML do proměnné

- <xref:System.Data.DataSet.GetXml%2A>Metoda vrátí <xref:System.String> . Deklarujte proměnnou typu <xref:System.String> a přiřaďte jí výsledky <xref:System.Data.DataSet.GetXml%2A> metody.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet12":::

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Uložení dat v datové sadě jako XML do souboru

- <xref:System.Data.DataSet.WriteXml%2A>Metoda má několik přetížení. Deklarujte proměnnou a přiřaďte jí platnou cestu k uložení souboru do. Následující kód ukazuje, jak uložit data do souboru:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet13":::

## <a name="see-also"></a>Viz také

- [Ukládání dat zpět do databáze](../data-tools/save-data-back-to-the-database.md)
