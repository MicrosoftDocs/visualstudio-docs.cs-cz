---
title: 'Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c84ae02bd2cafde7b6232c73bc75f0976e81bd0
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254370"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word
  V projektech aplikace Word na úrovni dokumentu můžete do dokumentu v projektu přidat ovládací prvky obsahu v době návrhu nebo v době běhu. V projektech doplňku aplikace Word VSTO můžete přidat ovládací prvky obsahu do libovolného otevřeného dokumentu v době běhu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 V tomto tématu jsou popsány následující úlohy:

- [Přidat ovládací prvky obsahu v době návrhu](#designtime)

- [Přidání ovládacích prvků obsahu v době běhu v projektu na úrovni dokumentu](#runtimedoclevel)

- [Přidání ovládacích prvků obsahu v době běhu v projektu doplňku VSTO](#runtimeaddin)

  Informace o ovládacích prvcích obsahu naleznete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

## <a name="designtime"></a>Přidat ovládací prvky obsahu v době návrhu
 Existuje několik způsobů, jak přidat ovládací prvky obsahu do dokumentu v projektu na úrovni dokumentu v době návrhu:

- Přidejte ovládací prvek obsahu z karty **ovládací prvky aplikace Word** v **sadě nástrojů**.

- Přidejte ovládací prvek obsahu do dokumentu stejným způsobem, jako byste přidali nativní ovládací prvek obsahu ve Wordu.

- Přetáhněte ovládací prvek obsahu do dokumentu z okna **zdroje dat** . To je užitečné, pokud chcete ovládací prvek navazovat na data při vytvoření ovládacího prvku. Další informace najdete v tématu [jak: Naplnit dokumenty daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md) a [postupy: Naplnit dokumenty daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Přidání ovládacího prvku obsahu do dokumentu pomocí panelu nástrojů

1. V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] návrháři, umístěte kurzor na místo, kam chcete přidat ovládací prvek obsahu, nebo vyberte text, který má nahradit ovládací prvek obsahu.

2. Otevřete **sadu nástrojů** a klikněte na kartu **ovládací prvky aplikace Word** .

3. Přidejte ovládací prvek jedním z následujících způsobů:

    - Dvakrát klikněte na ovládací prvek obsahu v **sadě nástrojů**.

         or

    - Klikněte na ovládací prvek obsahu v **sadě nástrojů** a potom stiskněte klávesu **ENTER** .

         or

    - Přetáhněte ovládací prvek obsahu ze **sady nástrojů** do dokumentu. Řízení obsahu je přidáno v aktuálním výběru v dokumentu, nikoli v umístění ukazatele myši.

> [!NOTE]
> Nelze přidat <xref:Microsoft.Office.Tools.Word.GroupContentControl> pomocí **sady nástrojů**. Přidat lze pouze <xref:Microsoft.Office.Tools.Word.GroupContentControl> do aplikace Word nebo v době běhu.

> [!NOTE]
> Sada Visual Studio neposkytuje ovládací prvek obsahu zaškrtávacího políčka v sadě nástrojů. Chcete-li přidat ovládací prvek obsahu zaškrtávacího políčka do dokumentu, je nutné <xref:Microsoft.Office.Tools.Word.ContentControl> objekt vytvořit programově. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Přidání ovládacího prvku obsahu do dokumentu ve Wordu

1. V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] návrháři, umístěte kurzor na místo, kam chcete přidat ovládací prvek obsahu, nebo vyberte text, který má nahradit ovládací prvek obsahu.

2. Na pásu karet klikněte na kartu **vývojář** .

    > [!NOTE]
    > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [jak: Na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)zobrazit kartu Vývojář.

3. Ve skupině **ovládací prvky** klikněte na ikonu ovládacího prvku obsahu, který chcete přidat.

## <a name="runtimedoclevel"></a>Přidání ovládacích prvků obsahu v době běhu v projektu na úrovni dokumentu
 Pomocí metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnosti `ThisDocument` třídy v projektu můžete do dokumentu v době běhu přidat ovládací prvky obsahu programově. Každá metoda má tři přetížení, která lze použít k přidání ovládacího prvku obsahu následujícími způsoby:

- Přidat ovládací prvek na aktuální výběr.

- Přidat ovládací prvek v zadaném rozsahu.

- Přidejte ovládací prvek, který je založen na nativním ovládacím prvku obsahu v dokumentu.

  Při zavření dokumentu se v dokumentu neukládají dynamicky vytvořené ovládací prvky obsahu. V dokumentu ale zůstane i nativní ovládací prvek obsahu. Můžete znovu vytvořit ovládací prvek obsahu, který je založen na nativním ovládacím prvku obsahu při příštím otevření dokumentu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

> [!NOTE]
> Chcete-li přidat ovládací prvek obsahu zaškrtávacího políčka do dokumentu v projektu aplikace Word 2010, je nutné vytvořit <xref:Microsoft.Office.Tools.Word.ContentControl> objekt. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Přidání ovládacího prvku obsahu v aktuálním výběru

1. `Add` \< <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>Použijte metodu, která má název třídy ovládacího prvku > (kde třída ovládacího prvku je název třídy ovládacího prvku obsahu, který chcete přidat, například) a který má jeden parametr pro <xref:Microsoft.Office.Tools.Word.ControlCollection> název nového ovládacího prvku

     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodu pro přidání nového <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na začátek dokumentu. Chcete-li spustit tento kód, přidejte kód do `ThisDocument` třídy v projektu a `AddRichTextControlAtSelection` zavolejte metodu z `ThisDocument_Startup` obslužné rutiny události.

     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>Přidání ovládacího prvku obsahu v zadaném rozsahu

1. `Add` \< <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Interop.Word.Range>Použijte metodu, která má název třídy ovládacího prvku > (kde třída ovládacího prvku je název třídy ovládacího prvku obsahu, kterou chcete přidat, například) a který má <xref:Microsoft.Office.Tools.Word.ControlCollection> ukazatele.

     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodu pro přidání nového <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na začátek dokumentu. Chcete-li spustit tento kód, přidejte kód do `ThisDocument` třídy v projektu a `AddRichTextControlAtRange` zavolejte metodu z `ThisDocument_Startup` obslužné rutiny události.

     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Přidání ovládacího prvku obsahu, který je založen na nativním ovládacím prvku obsahu

1. `Add` \< <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> `Microsoft.Office.Interop.Word.ContentControl`Použijte metodu, která má název třídy ovládacího prvku > (kde třída ovládacího prvku je název třídy ovládacího prvku obsahu, kterou chcete přidat, například) a který má <xref:Microsoft.Office.Tools.Word.ControlCollection> ukazatele.

     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodu k vytvoření nového <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pro každý nativní ovládací prvek formátovaného textu, který je v dokumentu. Chcete-li spustit tento kód, přidejte kód do `ThisDocument` třídy v projektu a `CreateRichTextControlsFromNativeControls` zavolejte metodu z `ThisDocument_Startup` obslužné rutiny události.

     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]

## <a name="runtimeaddin"></a>Přidání ovládacích prvků obsahu v době běhu v projektu doplňku VSTO
 Pomocí doplňku VSTO můžete přidat ovládací prvky obsahu programově do libovolného otevřeného dokumentu v době běhu. Chcete-li to provést, <xref:Microsoft.Office.Tools.Word.Document> vygenerujte hostitelskou položku, která je založena na otevřeném dokumentu, a pak <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> použijte metody vlastnosti této položky hostitele. Každá metoda má tři přetížení, která lze použít k přidání ovládacího prvku obsahu následujícími způsoby:

- Přidat ovládací prvek na aktuální výběr.

- Přidat ovládací prvek v zadaném rozsahu.

- Přidejte ovládací prvek, který je založen na nativním ovládacím prvku obsahu v dokumentu.

  Při zavření dokumentu se v dokumentu neukládají dynamicky vytvořené ovládací prvky obsahu. V dokumentu ale zůstane i nativní ovládací prvek obsahu. Můžete znovu vytvořit ovládací prvek obsahu, který je založen na nativním ovládacím prvku obsahu při příštím otevření dokumentu. Další informace najdete v tématu [trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Další informace o generování položek hostitele v projektech doplňku VSTO najdete v tématu [rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

> [!NOTE]
> Chcete-li přidat ovládací prvek obsahu zaškrtávacího políčka do dokumentu, je nutné vytvořit <xref:Microsoft.Office.Tools.Word.ContentControl> objekt. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Přidání ovládacího prvku obsahu v aktuálním výběru

1. `Add` \< <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>Použijte metodu, která má název třídy ovládacího prvku > (kde třída ovládacího prvku je název třídy ovládacího prvku obsahu, který chcete přidat, například) a který má jeden parametr pro <xref:Microsoft.Office.Tools.Word.ControlCollection> název nového ovládacího prvku

     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodu pro přidání nového <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na začátek aktivního dokumentu. Chcete-li spustit tento kód, přidejte kód do `ThisAddIn` třídy v projektu a `AddRichTextControlAtSelection` zavolejte metodu z `ThisAddIn_Startup` obslužné rutiny události.

     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>Přidání ovládacího prvku obsahu v zadaném rozsahu

1. `Add` \< <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Interop.Word.Range>Použijte metodu, která má název třídy ovládacího prvku > (kde třída ovládacího prvku je název třídy ovládacího prvku obsahu, kterou chcete přidat, například) a který má <xref:Microsoft.Office.Tools.Word.ControlCollection> ukazatele.

     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodu pro přidání nového <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na začátek aktivního dokumentu. Chcete-li spustit tento kód, přidejte kód do `ThisAddIn` třídy v projektu a `AddRichTextControlAtRange` zavolejte metodu z `ThisAddIn_Startup` obslužné rutiny události.

     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Přidání ovládacího prvku obsahu, který je založen na nativním ovládacím prvku obsahu

1. `Add` \< <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> `Microsoft.Office.Interop.Word.ContentControl`Použijte metodu, která má název třídy ovládacího prvku > (kde třída ovládacího prvku je název třídy ovládacího prvku obsahu, kterou chcete přidat, například) a který má <xref:Microsoft.Office.Tools.Word.ControlCollection> ukazatele.

     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodu k vytvoření nového <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pro každý nativní ovládací prvek formátovaného textu, který je v dokumentu po otevření dokumentu. Chcete-li spustit tento kód, přidejte kód do `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]

     Pro C#je nutné také k `Application_DocumentOpen` <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> události připojit obslužnou rutinu události.

     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]

## <a name="see-also"></a>Viz také:
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
