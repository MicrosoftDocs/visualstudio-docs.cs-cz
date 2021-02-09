---
title: 'Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word'
description: Přečtěte si, že v projektech na úrovni dokumentu můžete přidat ovládací prvky záložky do dokumentu v projektu v době návrhu nebo v době běhu.
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c5330d4419c065d7209900bfd4fa404663be185d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917477"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word
  V projektech na úrovni dokumentu můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky do dokumentu v projektu v době návrhu nebo v době běhu. V projektech doplňku VSTO můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky do libovolného otevřeného dokumentu v době běhu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 V tomto tématu jsou popsány následující úlohy:

- [Přidat ovládací prvky záložky v době návrhu](#designtime)

- [Přidat ovládací prvky záložky za běhu v projektu na úrovni dokumentu](#runtimedoclevel)

- [Přidání ovládacích prvků záložky za běhu v projektu doplňku VSTO](#runtimeaddin)

  Další informace o <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvcích naleznete v tématu [Bookmark Control](../vsto/bookmark-control.md).

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a> Přidat ovládací prvky záložky v době návrhu
 Existuje několik způsobů, jak přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky do dokumentu v projektu na úrovni dokumentu v době návrhu:

- V **sadě nástrojů sady** Visual Studio.

   Ovládací prvek lze přetáhnout <xref:Microsoft.Office.Tools.Word.Bookmark> z **panelu nástrojů** do dokumentu. Můžete chtít zvolit tento způsob, pokud již používáte **sadu nástrojů** k přidání model Windows Forms ovládacích prvků do dokumentu.

- V aplikaci Word.

   Můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek do dokumentu stejným způsobem, jako byste přidali nativní záložku. Výhodou přidání tohoto způsobu je, že ovládací prvek můžete pojmenovat v době, kdy ho vytvoříte.

- Z okna **zdroje dat** .

   Ovládací prvek lze přetáhnout <xref:Microsoft.Office.Tools.Word.Bookmark> do dokumentu z okna **zdroje dat** . To je užitečné, pokud chcete ovládací prvek navazovat na data ve stejnou dobu. Můžete přidat ovládací prvek hostitele stejným způsobem, jako byste přidali ovládací prvek Windows Form z okna **zdroje dat** . Další informace najdete v tématu [datové vazby a model Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Přidání ovládacího prvku záložka do dokumentu ze sady nástrojů

1. Otevřete **sadu nástrojů** a klikněte na kartu **ovládací prvky aplikace Word** .

2. Přetáhněte <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek do dokumentu.

     Zobrazí se dialogové okno **Přidat záložku** .

3. Vyberte text nebo jiné položky, které chcete zahrnout do záložky.

4. Klikněte na **OK**.

     Pokud nechcete zachovat výchozí název záložky, můžete název změnit v okně **vlastnosti** .

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Přidání ovládacího prvku záložka do dokumentu ve Wordu

1. V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrháři, umístěte kurzor na místo, kam chcete záložku přidat, nebo vyberte text, který má záložka uzavřít.

2. Na kartě **vložení** na pásu karet ve skupině **odkazy** klikněte na tlačítko **Záložka** .

3. V dialogovém okně **Záložka** zadejte název nové záložky a klikněte na **Přidat**.

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Přidat ovládací prvky záložky za běhu v projektu na úrovni dokumentu
 <xref:Microsoft.Office.Tools.Word.Bookmark>Pomocí metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnosti `ThisDocument` třídy v projektu lze do dokumentu programově přidat ovládací prvky v době běhu. Existují dvě přetížení metod, které lze použít k přidání <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku následujícími způsoby:

- Přidá <xref:Microsoft.Office.Tools.Word.Bookmark> v zadaném rozsahu.

- Přidejte <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na nativní záložce v dokumentu (tj <xref:Microsoft.Office.Interop.Word.Bookmark> . a).

  Dynamicky vytvořené <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky nejsou v dokumentu při zavření dokumentu trvalé. Nicméně nativní <xref:Microsoft.Office.Interop.Word.Bookmark> zůstává v dokumentu. Můžete znovu vytvořit <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na nativní záložce při příštím otevření dokumentu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Přidání ovládacího prvku záložka do dokumentu prostřednictvím kódu programu

1. V `ThisDocument_Startup` obslužné rutině události v projektu vložte následující kód pro přidání <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku do prvního odstavce v dokumentu.

     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]

    > [!NOTE]
    > Pokud chcete vytvořit <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek z existujícího <xref:Microsoft.Office.Interop.Word.Bookmark> , použijte <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metodu a předejte existující <xref:Microsoft.Office.Interop.Word.Bookmark> .

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Přidání ovládacích prvků záložky za běhu v projektu doplňku VSTO
 <xref:Microsoft.Office.Tools.Word.Bookmark>Pomocí doplňku VSTO můžete programově přidat ovládací prvky do libovolného otevřeného dokumentu v době běhu. Chcete-li to provést, vygenerujte <xref:Microsoft.Office.Tools.Word.Document> hostitelskou položku, která je založena na otevřeném dokumentu, a pak použijte metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnosti této položky hostitele. Existují dvě přetížení metod, které lze použít k přidání <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku následujícími způsoby:

- Přidá <xref:Microsoft.Office.Tools.Word.Bookmark> v zadaném rozsahu.

- Přidejte <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na nativní záložce v dokumentu (tj <xref:Microsoft.Office.Interop.Word.Bookmark> . a).

  Dynamicky vytvořené <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky nejsou v dokumentu při zavření dokumentu trvalé. Nicméně nativní <xref:Microsoft.Office.Interop.Word.Bookmark> zůstává v dokumentu. Můžete znovu vytvořit <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na nativní záložce při příštím otevření dokumentu. Další informace najdete v tématu [trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Další informace o generování položek hostitele v projektech doplňku VSTO najdete v tématu [rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Přidání ovládacího prvku záložka v zadaném rozsahu

1. Použijte <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metodu a předejte do WHERE, <xref:Microsoft.Office.Interop.Word.Range> kam chcete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> .

     Následující příklad kódu přidá nový <xref:Microsoft.Office.Tools.Word.Bookmark> na začátek aktivního dokumentu. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn_Startup` obslužné rutiny události v projektu doplňku aplikace Word VSTO.

     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Přidání ovládacího prvku záložka, který je založen na nativním ovládacím prvku záložky

1. Použijte <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metodu a předejte existující <xref:Microsoft.Office.Interop.Word.Bookmark> , který chcete použít jako základ pro nový <xref:Microsoft.Office.Tools.Word.Bookmark> .

     Následující příklad kódu vytvoří nový <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na první <xref:Microsoft.Office.Interop.Word.Bookmark> v aktivním dokumentu. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn_Startup` obslužné rutiny události v projektu doplňku aplikace Word VSTO.

     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]

## <a name="see-also"></a>Viz také
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Postupy: Změna velikosti ovládacích prvků záložek](../vsto/how-to-resize-bookmark-controls.md)
