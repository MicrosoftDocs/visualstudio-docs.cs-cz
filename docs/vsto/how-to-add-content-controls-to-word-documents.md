---
title: 'Postupy: Přidání obsahu ovládacích prvků do dokumentů aplikace Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f654efacace3e4b7cbdfff8919309a09d4a544ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936963"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Postupy: Přidání obsahu ovládacích prvků do dokumentů aplikace Word
  V projektech aplikace Word úrovni dokumentu můžete přidat ovládací prvky obsahu v dokumentu v projektu, v době návrhu nebo za běhu. V projekty doplňku VSTO pro Word můžete přidat ovládací prvky obsahu do libovolného otevřeného dokumentu za běhu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Toto téma popisuje následující úkoly:  
  
- [Přidání ovládacích prvků obsahu v době návrhu](#designtime)  
  
- [Přidání ovládacích prvků obsahu za běhu v projektu úrovni dokumentu](#runtimedoclevel)  
  
- [Přidání ovládacích prvků obsahu za běhu v projektu doplňku VSTO](#runtimeaddin)  
  
  Informace o ovládacích prvcích obsahu najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Přidat obsah ovládací prvky v době návrhu  
 Existuje několik způsobů, jak přidat ovládací prvky obsahu v dokumentu v projektu úrovni dokumentu v době návrhu:  
  
- Přidejte ovládací prvek obsahu z **ovládací prvky aplikace Word** karty **nástrojů**.  
  
- Přidání ovládacího prvku obsahu do dokumentu stejným způsobem by přidat nativní ovládací prvek obsahu v aplikaci Word.  
  
- Přetáhněte ovládací prvek obsahu do dokumentu z **zdroje dat** okna. To je užitečné, pokud chcete ovládací prvek svázat data při vytvoření ovládacího prvku. Další informace najdete v tématu [postupy: naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md) a [postupy: naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Chcete-li přidat ovládací prvek obsahu do dokumentu pomocí panelu nástrojů  
  
1.  V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] návrháře, umístěte kurzor na místo, kde chcete přidat ovládací prvek obsahu, nebo vyberte text, který má ovládací prvek obsahu pro nahrazení.  
  
2.  Otevřít **nástrojů** a klikněte na tlačítko **ovládací prvky aplikace Word** kartu.  
  
3.  Přidejte ovládací prvek jednoho z následujících způsobů:  
  
    -   Poklepejte na ovládací prvek obsahu v **nástrojů**.  
  
         or  
  
    -   Klikněte na ovládací prvek obsahu v **nástrojů** a potom stiskněte klávesu **Enter** klíč.  
  
         or  
  
    -   Přetáhněte ovládací prvek obsahu z **nástrojů** v dokumentu. Ovládací prvek obsahu se přidá na aktuální výběr v dokumentu, není v umístění ukazatele myši.  
  
> [!NOTE]  
>  Nelze přidat <xref:Microsoft.Office.Tools.Word.GroupContentControl> pomocí **nástrojů**. Lze přidat pouze <xref:Microsoft.Office.Tools.Word.GroupContentControl> v aplikaci Word nebo za běhu.  
  
> [!NOTE]  
>  Visual Studio neposkytuje obsahu ovládacího prvku zaškrtávací políčko v panelu nástrojů. Chcete-li přidat ovládací prvek zaškrtávací políčko obsahu v dokumentu, musíte vytvořit <xref:Microsoft.Office.Tools.Word.ContentControl> objektu prostřednictvím kódu programu. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Chcete-li přidat ovládací prvek obsahu dokumentu ve Wordu  
  
1.  V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] návrháře, umístěte kurzor na místo, kde chcete přidat ovládací prvek obsahu, nebo vyberte text, který má ovládací prvek obsahu pro nahrazení.  
  
2.  Na pásu karet klikněte na tlačítko **Developer** kartu.  
  
    > [!NOTE]  
    >  Pokud **Developer** karta není zobrazena, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  V **ovládací prvky** klikněte na ikonu ovládacího prvku obsahu, který chcete přidat.  
  
##  <a name="runtimedoclevel"></a> Přidání ovládacích prvků obsahu za běhu v projektu úrovni dokumentu  
 Můžete přidat ovládací prvky obsahu prostřednictvím kódu programu do dokumentu za běhu pomocí metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnost `ThisDocument` třídu ve vašem projektu. Každá z metod má tři přetížení, které můžete použít k přidání ovládacího prvku obsahu následujícími způsoby:  
  
- Přidejte ovládací prvek na aktuální výběr.  
  
- Přidání ovládacího prvku v zadaném rozsahu.  
  
- Přidejte ovládací prvek, který je založen na nativním ovládacím prvku obsahu v dokumentu.  
  
  Dynamicky vytvoří obsah, který se jako trvalý ovládací prvky v dokumentu, při zavření dokumentu. Nativní ovládací prvek obsahu, ale zůstává v dokumentu. Můžete znovu vytvořit ovládací prvek obsahu, který je založen na nativním ovládacím prvku obsahu při příštím otevření dokumentu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Chcete-li přidat ovládací prvek zaškrtávací políčko obsahu dokumentu v projektu aplikace Word 2010, musíte vytvořit <xref:Microsoft.Office.Tools.Word.ContentControl> objektu. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Chcete-li přidat ovládací prvek obsahu v aktuálním výběru  
  
1.  Použití <xref:Microsoft.Office.Tools.Word.ControlCollection> metodu, která má název `Add` \< *třídu ovládacího prvku*> (kde *třídu ovládacího prvku* je název třídy obsahu ovládacího prvku, který chcete přidat, jako je například <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), a který má jeden parametr pro název nového ovládacího prvku.  
  
     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> způsob, jak přidat nové <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na začátek dokumentu. Tento kód spustit, přidejte kód, který `ThisDocument` třídu v projektu a volejte `AddRichTextControlAtSelection` metodu z `ThisDocument_Startup` obslužné rutiny události.  
  
     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Přidání obsahu ovládacího prvku v zadaném rozsahu  
  
1.  Použití <xref:Microsoft.Office.Tools.Word.ControlCollection> metodu, která má název `Add` \< *třídu ovládacího prvku*> (kde *třídu ovládacího prvku* je název třídy ovládacího prvku obsahu, který chcete přidat, jako je například <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), a který má <xref:Microsoft.Office.Interop.Word.Range> parametru.  
  
     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> způsob, jak přidat nové <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na začátek dokumentu. Tento kód spustit, přidejte kód, který `ThisDocument` třídu v projektu a volejte `AddRichTextControlAtRange` metodu z `ThisDocument_Startup` obslužné rutiny události.  
  
     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]  
  
### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Chcete-li přidat ovládací prvek obsahu, který je založen na nativním ovládacím prvku obsahu  
  
1.  Použití <xref:Microsoft.Office.Tools.Word.ControlCollection> metodu, která má název `Add` \< *třídu ovládacího prvku*> (kde *třídu ovládacího prvku* je název třídy ovládacího prvku obsahu, který chcete přidat, jako je například <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), a který má `Microsoft.Office.Interop.Word.ContentControl` parametru.  
  
     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodu pro vytvoření nového <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pro každý ovládací prvek nativní formátovaný text, který je v dokumentu. Tento kód spustit, přidejte kód, který `ThisDocument` třídu v projektu a volejte `CreateRichTextControlsFromNativeControls` metodu z `ThisDocument_Startup` obslužné rutiny události.  
  
     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Přidání ovládacích prvků obsahu za běhu v projektu doplňku VSTO  
 Přidáním ovládacích prvků obsahu prostřednictvím kódu programu do libovolného otevřeného dokumentu za běhu pomocí doplňku VSTO. Chcete-li to provést, vygenerovat <xref:Microsoft.Office.Tools.Word.Document> hostitelem položku, která vychází z otevřeného dokumentu a pak použijte metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnosti této položky hostitele. Každá z metod má tři přetížení, které můžete použít k přidání ovládacího prvku obsahu následujícími způsoby:  
  
- Přidejte ovládací prvek na aktuální výběr.  
  
- Přidání ovládacího prvku v zadaném rozsahu.  
  
- Přidejte ovládací prvek, který je založen na nativním ovládacím prvku obsahu v dokumentu.  
  
  Dynamicky vytvoří obsah, který se jako trvalý ovládací prvky v dokumentu, při zavření dokumentu. Nativní ovládací prvek obsahu, ale zůstává v dokumentu. Můžete znovu vytvořit ovládací prvek obsahu, který je založen na nativním ovládacím prvku obsahu při příštím otevření dokumentu. Další informace najdete v tématu [uchování dynamických ovládacích prvků v dokumentech systému Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  Další informace o generování hostitelských položkách v projekty doplňku VSTO v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Chcete-li do dokumentu přidat ovládací prvek zaškrtávací políčko obsahu, musíte vytvořit <xref:Microsoft.Office.Tools.Word.ContentControl> objektu. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Chcete-li přidat ovládací prvek obsahu v aktuálním výběru  
  
1.  Použití <xref:Microsoft.Office.Tools.Word.ControlCollection> metodu, která má název `Add` \< *třídu ovládacího prvku*> (kde *třídu ovládacího prvku* je název třídy obsahu ovládacího prvku, který chcete přidat, jako je například <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), a který má jeden parametr pro název nového ovládacího prvku.  
  
     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> způsob, jak přidat nové <xref:Microsoft.Office.Tools.Word.RichTextContentControl> začátek aktivní dokument. Tento kód spustit, přidejte kód, který `ThisAddIn` třídu v projektu a volejte `AddRichTextControlAtSelection` metodu z `ThisAddIn_Startup` obslužné rutiny události.  
  
     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Přidání obsahu ovládacího prvku v zadaném rozsahu  
  
1.  Použití <xref:Microsoft.Office.Tools.Word.ControlCollection> metodu, která má název `Add` \< *třídu ovládacího prvku*> (kde *třídu ovládacího prvku* je název třídy ovládacího prvku obsahu, který chcete přidat, jako je například <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), a který má <xref:Microsoft.Office.Interop.Word.Range> parametru.  
  
     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> způsob, jak přidat nové <xref:Microsoft.Office.Tools.Word.RichTextContentControl> začátek aktivní dokument. Tento kód spustit, přidejte kód, který `ThisAddIn` třídu v projektu a volejte `AddRichTextControlAtRange` metodu z `ThisAddIn_Startup` obslužné rutiny události.  
  
     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Chcete-li přidat ovládací prvek obsahu, který je založen na nativním ovládacím prvku obsahu  
  
1.  Použití <xref:Microsoft.Office.Tools.Word.ControlCollection> metodu, která má název `Add` \< *třídu ovládacího prvku*> (kde *třídu ovládacího prvku* je název třídy ovládacího prvku obsahu, který chcete přidat, jako je například <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), a který má `Microsoft.Office.Interop.Word.ContentControl` parametru.  
  
     Následující příklad kódu používá <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodu pro vytvoření nového <xref:Microsoft.Office.Tools.Word.RichTextContentControl> pro každý ovládací prvek nativní formátovaný text, který je v dokumentu, po otevření dokumentu. Tento kód spustit, přidejte kód, který `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]  
  
     Pro jazyk C#, je nutné také připojit `Application_DocumentOpen` obslužnou rutinu události <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> událostí.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)  
  