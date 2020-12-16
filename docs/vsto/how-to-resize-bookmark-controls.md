---
title: 'Postupy: Změna velikosti ovládacích prvků záložek'
description: Naučte se, jak můžete pomocí sady Visual Studio nastavit velikost ovládacího prvku záložky, když ho přidáte do dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0d577f825337862de4ef967bb4f92f61ebbb0b45
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528191"
---
# <a name="how-to-resize-bookmark-controls"></a>Postupy: Změna velikosti ovládacích prvků záložek
  Velikost <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku se nastavuje při jeho přidání do systém Microsoft Office wordového dokumentu. Později můžete změnit její velikost.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Existují tři způsoby, jak změnit velikost záložky:

- Přidejte nebo odeberte text v <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacím prvku.

   Kdykoli přidáte text do záložky, velikost záložky se automaticky zvětšuje tak, aby obsahovala nový text. Při odstranění textu se automaticky zmenší velikost záložky.

- Změňte <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> vlastnosti <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku a.

   To je užitečné v případě, že měníte velikost jenom pomocí několika znaků.

- Vytvořte znovu <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek.

   To je užitečné v případě, že dojde k podstatné změně velikosti nebo umístění záložky.

  V projektech na úrovni dokumentu můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky do dokumentu v projektu v době návrhu nebo v době běhu. V projektech doplňku VSTO můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky do libovolného otevřeného dokumentu v době běhu. Další informace najdete v tématu [Postup: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="change-the-start-and-end-properties"></a>Změna počátečních a koncových vlastností

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Změna velikosti záložky v projektu na úrovni dokumentu v době návrhu

1. V okně **vlastnosti** vyberte záložku.

2. Zvyšte nebo snižte hodnotu <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> Vlastnosti.

3. Zvyšte nebo snižte hodnotu <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> Vlastnosti.

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Změna velikosti záložky v projektu na úrovni dokumentu v době běhu

1. Upravte <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> vlastnosti a, <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> které jste vytvořili v době běhu nebo v době návrhu.

     Následující příklad kódu přidá pět znaků na začátek záložky s názvem `SampleBookmark` . Tento kód předpokládá, že před záložkou je k dispozici alespoň pět znaků textu.

     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]

     Následující příklad kódu přidá pět znaků na konec stejné záložky. Tento kód předpokládá, že po záložce je k dispozici alespoň pět znaků textu.

     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]

### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-run-time"></a>Změna velikosti záložky v projektu doplňku VSTO za běhu

1. Upravte <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> vlastnosti a, <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> které jste vytvořili v době běhu.

     Následující příklad kódu vytvoří objekt <xref:Microsoft.Office.Tools.Word.Bookmark> , který obsahuje text v prvním odstavci aktivního dokumentu a pak odebere pět znaků od začátku a konce <xref:Microsoft.Office.Tools.Word.Bookmark> .

     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]

## <a name="recreate-the-bookmark"></a>Opětovné vytvoření záložky
 Můžete změnit velikost záložky v projektu na úrovni dokumentu přidáním nové záložky, která má stejný název jako existující záložka, ale má jinou velikost.

### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Opětovné vytvoření záložky v projektu na úrovni dokumentu v době návrhu

1. Vyberte text, který chcete zahrnout do nového <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku.

2. V nabídce **Vložit** klikněte na položku **Záložka**.

3. V dialogovém okně **Záložka** vyberte název záložky, u které chcete změnit velikost, a klikněte na tlačítko **Přidat**.

## <a name="see-also"></a>Viz také
- [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
