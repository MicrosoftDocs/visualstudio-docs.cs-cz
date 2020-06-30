---
title: 'Postupy: Ochrana částí dokumentů pomocí ovládacích prvků obsahu'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b03521023ea0b4d92bd3125f256d2230de9bba03
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541346"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Postupy: Ochrana částí dokumentů pomocí ovládacích prvků obsahu
  Při ochraně části dokumentu zabráníte uživatelům měnit nebo odstraňovat obsah v této části dokumentu. Existuje několik způsobů, jak můžete chránit části dokumentu aplikace systém Microsoft Office Word pomocí ovládacích prvků obsahu:

- Můžete chránit ovládací prvek obsahu.

- Můžete chránit část dokumentu, který není v ovládacím prvku obsahu.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a>Ochrana ovládacího prvku obsahu
 Můžete zabránit uživatelům v úpravách nebo odstraňování ovládacího prvku obsahu nastavením vlastností ovládacího prvku v projektu na úrovni dokumentu v době návrhu nebo v době běhu.

 Pomocí projektu doplňku VSTO můžete také chránit ovládací prvky obsahu, které do dokumentu přidáte v době běhu. Další informace najdete v tématu [Postup: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>Ochrana ovládacího prvku obsahu v době návrhu

1. V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrháři, vyberte ovládací prvek obsahu, který chcete chránit.

2. V okně **vlastnosti** nastavte jednu nebo obě následující vlastnosti:

    - Chcete-li uživatelům zabránit v úpravách ovládacího prvku, nastavte **LockContents** na **hodnotu true**.

    - Chcete-li uživatelům zabránit v odstranění ovládacího prvku, nastavte **LockContentControl** na **hodnotu true**.

3. Klikněte na **OK**.

### <a name="to-protect-a-content-control-at-run-time"></a>Ochrana ovládacího prvku obsahu v době běhu

1. Nastavte `LockContents` vlastnost ovládacího prvku obsahu na **hodnotu true** , chcete-li uživatelům zabránit v úpravách ovládacího prvku, a nastavte `LockContentControl` vlastnost na **hodnotu true** , aby uživatelé nemohli tento ovládací prvek odstranit.

     Následující příklad kódu ukazuje použití <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> vlastností a dvou různých <xref:Microsoft.Office.Tools.Word.RichTextContentControl> objektů v projektu na úrovni dokumentu. Chcete-li spustit tento kód, přidejte kód do `ThisDocument` třídy v projektu a zavolejte `AddProtectedContentControls` metodu z `ThisDocument_Startup` obslužné rutiny události.

     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]

     Následující příklad kódu ukazuje použití <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> vlastností a dvou různých <xref:Microsoft.Office.Tools.Word.RichTextContentControl> objektů v projektu doplňku VSTO. Chcete-li spustit tento kód, přidejte kód do `ThisAddIn` třídy v projektu a zavolejte `AddProtectedContentControls` metodu z `ThisAddIn_Startup` obslužné rutiny události.

     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Ochrana části dokumentu, který není v ovládacím prvku obsahu
 Uživatelům můžete zabránit v změně oblasti dokumentu tak, že umístíte oblast do <xref:Microsoft.Office.Tools.Word.GroupContentControl> . To je užitečné v následujících scénářích:

- Chcete chránit oblast, která neobsahuje ovládací prvky obsahu.

- Chcete chránit oblast, která již obsahuje ovládací prvky obsahu, ale text nebo jiné položky, které chcete chránit, nejsou v ovládacích prvcích obsahu.

> [!NOTE]
> Pokud vytvoříte objekt <xref:Microsoft.Office.Tools.Word.GroupContentControl> , který obsahuje ovládací prvky vloženého obsahu, ovládací prvky vloženého obsahu nejsou automaticky chráněny. Chcete-li uživatelům zabránit v úpravách vloženého ovládacího prvku obsahu, použijte vlastnost **LockContents** ovládacího prvku.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Ochrana oblasti dokumentu v době návrhu

1. V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrháři, vyberte oblast, kterou chcete chránit.

2. Na pásu karet klikněte na kartu **vývojář** .

    > [!NOTE]
    > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. Ve skupině **ovládací prvky** klikněte na rozevírací tlačítko **Skupina** a pak klikněte na **Skupina**.

     Objekt <xref:Microsoft.Office.Tools.Word.GroupContentControl> , který obsahuje chráněnou oblast, je automaticky vygenerován ve `ThisDocument` třídě v projektu. Ohraničení, které představuje ovládací prvek skupiny, je viditelné v době návrhu, ale v době běhu není viditelné ohraničení.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Ochrana oblasti dokumentu v době běhu

1. Programově vyberte oblast, kterou chcete chránit, a pak zavolejte <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> metodu pro vytvoření <xref:Microsoft.Office.Tools.Word.GroupContentControl> .

     Následující příklad kódu pro projekt na úrovni dokumentu přidá text k prvnímu odstavci v dokumentu, vybere první odstavec a potom vytvoří instanci <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Chcete-li spustit tento kód, přidejte kód do `ThisDocument` třídy v projektu a zavolejte `ProtectFirstParagraph` metodu z `ThisDocument_Startup` obslužné rutiny události.

     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]

     Následující příklad kódu pro projekt doplňku VSTO přidá text do prvního odstavce v aktivním dokumentu, vybere první odstavec a potom vytvoří instanci <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Chcete-li spustit tento kód, přidejte kód do `ThisAddIn` třídy v projektu a zavolejte `ProtectFirstParagraph` metodu z `ThisAddIn_Startup` obslužné rutiny události.

     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]

## <a name="see-also"></a>Viz také
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Ovládací prvky obsahu](../vsto/content-controls.md)
- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
