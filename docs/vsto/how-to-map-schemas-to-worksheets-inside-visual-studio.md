---
title: 'Postupy: mapování schémat na listy v rámci sady Visual Studio'
description: Přečtěte si, jak můžete mapovat schéma XML na excelový list systém Microsoft Office v době, kdy je sešit otevřený v aplikaci Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0e6d868655e3f697a7f659064026929568f2e400
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900848"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Postupy: mapování schémat na listy v rámci sady Visual Studio
  Pokud je sešit otevřený v aplikaci Visual Studio, můžete namapovat schéma XML na list. Použijete stejné systém Microsoft Office excelové nástroje, které použijete, když je sešit otevřený mimo sadu Visual Studio. Projekt sady Office vytvoří stejné objekty bez ohledu na to, zda je schéma namapováno na list před nebo po vytvoření řešení aplikace Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> V řešeních aplikace Excel nelze použít schémata XML s více částmi.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Mapování schématu XML na excelový list v aplikaci Visual Studio

1. Otevřete excelový sešit nebo šablonu projektu v aplikaci Visual Studio.

2. Kliknutím na list přesuňte fokus do návrháře.

3. Na pásu karet klikněte na kartu **vývojář** .

    > [!NOTE]
    > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Ve skupině **XML** klikněte na **zdroj**.

     Otevře se okno **zdroje XML** .

5. V okně **zdroje XML** klikněte na **mapování XML**.

     Otevře se dialogové okno **mapy XML** .

6. V dialogovém okně **mapy XML** klikněte na tlačítko **Přidat**.

7. Vyhledejte soubor schématu, vyberte jej a klikněte na tlačítko **otevřít**.

8. Klikněte na **OK**.

     Schéma je znázorněno v okně **zdroje XML** . V projektu je zadaný typ <xref:System.Data.DataSet> generovaný na základě schématu a vytvoří <xref:System.Windows.Forms.BindingSource> se.

9. Přetáhněte prvky z okna **zdroje XML** na místa v listu, kde chcete vytvořit odpovídající ovládací prvky.

     Pokud přetáhnete neopakující se prvek schématu, projekt sady Office vytvoří <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek, který je automaticky svázán s rozhraním <xref:System.Windows.Forms.BindingSource> .

     Pokud přetáhnete opakující se prvek schématu, projekt sady Office vytvoří <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek, který není automaticky svázán se zdrojem dat. Další informace najdete v tématu [schémata a data XML v přizpůsobeních na úrovni dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Viz také
- [Postupy: mapování schémat na dokumenty aplikace Word v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Schémata XML a data v přizpůsobeních na úrovni dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
