---
title: 'Postupy: ochrana částí dokumentů pomocí ovládacích prvků obsahu'
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
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: beee4dd4a67b03f278a296d4b5f129100212fd25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850357"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Postupy: ochrana částí dokumentů pomocí ovládacích prvků obsahu
  Když chráníte část dokumentu, zabránit uživatelům v měnit nebo odstraňovat obsah v této části dokumentu. Existuje několik způsobů, jak může ochrana částí dokumentu aplikace Microsoft Office Word s použitím ovládacích prvků obsahu:  
  
- Budete moci chránit obsah ovládacího prvku.  
  
- Můžete chránit část dokumentu, který není v obsahu prvku.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Ochrana obsahu ovládacího prvku  
 Můžete zabránit uživatelům v úpravách nebo odstraňování ovládací prvek obsahu nastavením vlastností ovládacího prvku v projektu úrovni dokumentu v době návrhu nebo za běhu.  
  
 Můžete taky chránit ovládacích prvků obsahu, které přidáte do dokumentu za běhu pomocí projektu doplňku VSTO. Další informace najdete v tématu [postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
### <a name="to-protect-a-content-control-at-design-time"></a>K ochraně obsahu ovládacího prvku v době návrhu  
  
1.  V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrhář, vyberte ovládací prvek obsahu, který chcete chránit.  
  
2.  V **vlastnosti** okno, nastavte jednu nebo obě z následujících vlastností:  
  
    -   Chcete-li zabránit uživatelům v úpravách ovládacího prvku, nastavte **LockContents** k **True**.  
  
    -   Chcete-li uživatelům zabránit v odstranění ovládacího prvku, nastavte **LockContentControl** k **True**.  
  
3.  Klikněte na tlačítko **OK**.  
  
### <a name="to-protect-a-content-control-at-runtime"></a>K ochraně obsahu ovládacího prvku za běhu  
  
1.  Nastavte `LockContents` vlastnost obsahu ovládacího prvku na **true** zabránit uživatelům v úpravách ovládací prvek a nastavit `LockContentControl` vlastnost **true** uživatelům zabránit v odstranění ovládacího prvku.  
  
     Následující příklad kódu ukazuje použití <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> a <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> dva různé vlastnosti <xref:Microsoft.Office.Tools.Word.RichTextContentControl> objekty v projektu úrovni dokumentu. Tento kód spustit, přidejte kód, který `ThisDocument` třídu v projektu a volejte `AddProtectedContentControls` metodu z `ThisDocument_Startup` obslužné rutiny události.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]  
  
     Následující příklad kódu ukazuje použití <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> a <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> dva různé vlastnosti <xref:Microsoft.Office.Tools.Word.RichTextContentControl> objekty v projektu doplňku VSTO. Tento kód spustit, přidejte kód, který `ThisAddIn` třídu v projektu a volejte `AddProtectedContentControls` metodu z `ThisAddIn_Startup` obslužné rutiny události.  
  
     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]  
  
## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Ochrana část dokumentu, který není v ovládacím prvku obsahu  
 Můžete zabránit uživatelům možnost měnit oblast v dokumentu tak, že vložíte oblasti <xref:Microsoft.Office.Tools.Word.GroupContentControl>. To je užitečné v následujících scénářích:  
  
-   Chcete chránit prostor, který obsahuje ovládací prvky obsahu.  
  
-   Chcete chránit prostor, který již obsahuje ovládací prvky obsahu, ale text nebo jiné položky, které chcete chránit, nejsou v ovládacích prvcích obsahu.  
  
> [!NOTE]  
>  Pokud jste vytvořili <xref:Microsoft.Office.Tools.Word.GroupContentControl> , která obsahuje vložené ovládací prvky obsahu, embedded ovládacích prvků obsahu nejsou chráněné automaticky. Pokud chcete zabránit uživatelům v úpravách vložené ovládací prvek obsahu, použijte **LockContents** vlastnost ovládacího prvku.  
  
### <a name="to-protect-an-area-of-a-document-at-design-time"></a>K ochraně oblast dokumentu v době návrhu  
  
1.  V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrhář, vyberte oblast, která chcete chránit.  
  
2.  Na pásu karet klikněte na tlačítko **Developer** kartu.  
  
    > [!NOTE]  
    >  Pokud **Developer** karta není zobrazena, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  V **ovládací prvky** klikněte na položku **skupiny** tlačítko rozevíracího seznamu a pak klikněte na tlačítko **skupiny**.  
  
     A <xref:Microsoft.Office.Tools.Word.GroupContentControl> , který obsahuje chráněnou oblast není automaticky vygenerován v `ThisDocument` třídu ve vašem projektu. Ohraničení, která představuje ovládacího prvku skupiny je viditelný v době návrhu, ale neexistuje žádná viditelná ohraničení za běhu.  
  
### <a name="to-protect-an-area-of-a-document-at-runtime"></a>K ochraně oblast v dokumentu za běhu  
  
1.  Prostřednictvím kódu programu vyberte oblast, kterou chcete chránit a poté zavolejte <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> metodu pro vytvoření <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
     Následující příklad kódu na úrovni dokumentu projekt přidá text do prvního odstavce v dokumentu, vybere prvního odstavce a poté vytvoří instanci <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Tento kód spustit, přidejte kód, který `ThisDocument` třídu v projektu a volejte `ProtectFirstParagraph` metodu z `ThisDocument_Startup` obslužné rutiny události.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]  
  
     Následující příklad kódu pro projekt doplňku VSTO přidá text do prvního odstavce v aktivním dokumentu, vybere prvního odstavce a poté vytvoří instanci <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Tento kód spustit, přidejte kód, který `ThisAddIn` třídu v projektu a volejte `ProtectFirstParagraph` metodu z `ThisAddIn_Startup` obslužné rutiny události.  
  
     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Ovládací prvky obsahu](../vsto/content-controls.md)   
 [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)  
   