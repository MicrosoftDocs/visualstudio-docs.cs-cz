---
title: 'Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 33afb16b9862f418f4d661bb5432ea4bb3866f16
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878606"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word
  Projekty na úrovni dokumentu, můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků do dokumentu v projektu v době návrhu nebo za běhu. Projekty doplňků VSTO, můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků do libovolného otevřeného dokumentu za běhu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Toto téma popisuje následující úkoly:  
  
- [Přidání ovládacích prvků záložek v době návrhu](#designtime)  
  
- [Přidání ovládacích prvků záložek za běhu v projektu úrovni dokumentu](#runtimedoclevel)  
  
- [Přidání ovládacích prvků záložek za běhu v projektu doplňku VSTO](#runtimeaddin)  
  
  Další informace o <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků, naleznete v tématu [Bookmark – ovládací prvek](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a> Přidání ovládacích prvků záložek v době návrhu  
 Existuje několik způsobů, jak přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků do dokumentu v projektu úrovni dokumentu v době návrhu:  
  
- Ze sady Visual Studio **nástrojů**.  
  
   Můžete přetáhnout <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku **nástrojů** do dokumentu. Můžete chtít tímto způsobem vyberte, pokud už používáte **nástrojů** přidání ovládacích prvků Windows Forms do dokumentu.  
  
- V rámci aplikace Word.  
  
   Můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku do dokumentu stejným způsobem by přidat nativní záložku. Výhodou přidáním tímto způsobem je, že použijete název ovládacího prvku v době vytvoření.  
  
- Z **zdroje dat** okna.  
  
   Můžete přetáhnout <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku do dokumentu z **zdroje dat** okna. To je užitečné, pokud chcete vytvořit vazbu ovládacího prvku k datům ve stejnou dobu. Můžete přidat hostitelský ovládací prvek stejně, jako byste přidali ovládací prvek formuláře Windows ze **zdroje dat** okna. Další informace najdete v tématu [a datové vazby Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Chcete-li přidat ovládací prvek Bookmark do dokumentu z panelu nástrojů  
  
1.  Otevřít **nástrojů** a klikněte na tlačítko **ovládací prvky aplikace Word** kartu.  
  
2.  Přetáhněte <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek v dokumentu.  
  
     **Přidat záložku** zobrazí se dialogové okno.  
  
3.  Výběr textu nebo jiné položky, které chcete zahrnout do záložky.  
  
4.  Klikněte na tlačítko **OK**.  
  
     Pokud nechcete Ponecháme výchozí název záložky, můžete změnit název v **vlastnosti** okna.  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Chcete-li přidat ovládací prvek Bookmark dokumentu ve Wordu  
  
1.  V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] návrháře, umístěte kurzor na místo, kde chcete přidat záložek, nebo vyberte text, který má na záložku k uzavření.  
  
2.  Na **vložit** kartu na pásu karet v **odkazy** klikněte na položku **záložku** tlačítko.  
  
3.  V **záložku** dialogové okno, zadejte název nové záložky a klikněte na tlačítko **přidat**.  
  
##  <a name="runtimedoclevel"></a> Přidání ovládacích prvků záložek za běhu v projektu úrovni dokumentu  
 Můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> řídí prostřednictvím kódu programu do dokumentu za běhu pomocí metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnost `ThisDocument` třídu ve vašem projektu. Existují dvě přetížení metody, které slouží k přidání <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek následujícími způsoby:  
  
- Přidat <xref:Microsoft.Office.Tools.Word.Bookmark> v zadaném rozsahu.  
  
- Přidat <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na nativním záložky v dokumentu (to znamená, <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  Dynamicky vytvoří <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky nejsou trvalé v dokumentu, při zavření dokumentu. Však nativní <xref:Microsoft.Office.Interop.Word.Bookmark> zůstane v dokumentu. Můžete znovu vytvořit <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na nativní záložku při příštím otevření dokumentu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Chcete-li přidat ovládací prvek Bookmark do dokumentů prostřednictvím kódu programu  
  
1.  V `ThisDocument_Startup` obslužná rutina události ve vašem projektu, vložte následující kód pro přidání <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku do prvního odstavce v dokumentu.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Pokud chcete vytvořit <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku z existující <xref:Microsoft.Office.Interop.Word.Bookmark>, použijte <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> a předáte v existujícím <xref:Microsoft.Office.Interop.Word.Bookmark>.  
  
##  <a name="runtimeaddin"></a> Přidání ovládacích prvků záložek za běhu v projektu doplňku VSTO  
 Můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků prostřednictvím kódu programu do libovolného otevřeného dokumentu za běhu pomocí doplňku VSTO. Chcete-li to provést, vygenerovat <xref:Microsoft.Office.Tools.Word.Document> hostitelem položku, která vychází z otevřeného dokumentu a pak použijte metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> vlastnosti této položky hostitele. Existují dvě přetížení metody, které slouží k přidání <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek následujícími způsoby:  
  
- Přidat <xref:Microsoft.Office.Tools.Word.Bookmark> v zadaném rozsahu.  
  
- Přidat <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na nativním záložky v dokumentu (to znamená, <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  Dynamicky vytvoří <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvky nejsou trvalé v dokumentu, při zavření dokumentu. Však nativní <xref:Microsoft.Office.Interop.Word.Bookmark> zůstane v dokumentu. Můžete znovu vytvořit <xref:Microsoft.Office.Tools.Word.Bookmark> , který je založen na nativní záložku při příštím otevření dokumentu. Další informace najdete v tématu [uchování dynamických ovládacích prvků v dokumentech systému Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  Další informace o generování hostitelských položkách v projekty doplňku VSTO v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Chcete-li přidat ovládací prvek Bookmark v zadaném rozsahu  
  
1.  Použití <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metoda a předejte jí <xref:Microsoft.Office.Interop.Word.Range> , které chcete přidat <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Následující příklad kódu přidá nový <xref:Microsoft.Office.Tools.Word.Bookmark> začátek aktivní dokument. Pokud chcete použít tento příklad, spusťte kód z `ThisAddIn_Startup` obslužné rutiny události v projektu doplňku VSTO pro Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Chcete-li přidat ovládací prvek Bookmark, který je založen na nativním ovládacím prvku záložku  
  
1.  Použít <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metoda a předejte jí existující <xref:Microsoft.Office.Interop.Word.Bookmark> , kterou chcete použít jako základ pro nové <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Následující příklad kódu vytvoří novou <xref:Microsoft.Office.Tools.Word.Bookmark> , který je podle prvního <xref:Microsoft.Office.Interop.Word.Bookmark> v aktivním dokumentu. Pokud chcete použít tento příklad, spusťte kód z `ThisAddIn_Startup` obslužné rutiny události v projektu doplňku VSTO pro Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)   
 [Postupy: Změna velikosti ovládacích prvků záložek](../vsto/how-to-resize-bookmark-controls.md)  
  
  