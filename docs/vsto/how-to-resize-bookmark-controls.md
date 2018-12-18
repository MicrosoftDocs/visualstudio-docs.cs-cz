---
title: 'Postupy: Změna velikosti ovládacích prvků záložek'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 57b6d6a089570c52607cf73eeed4fc00978ab251
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924834"
---
# <a name="how-to-resize-bookmark-controls"></a>Postupy: Změna velikosti ovládacích prvků záložek
  Nastavte velikost <xref:Microsoft.Office.Tools.Word.Bookmark> řídit, kdy je přidat do dokumentu aplikace Microsoft Office Word. Můžete také změnit velikost ji později.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Existují tři způsoby, jak změnit velikost záložky:  
  
- Přidání nebo odstranění textu v <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku.  
  
   Pokaždé, když přidáte záložku text, velikost záložky se automaticky zvětší tak, aby obsahovala nového textu. Když odstraníte text, velikost záložky automaticky sníží.  
  
- Změnit <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> a <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> vlastnosti <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku.  
  
   To je užitečné, pokud chcete změnit velikost podle jenom několik znaků.  
  
- Znovu vytvořit <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku.  
  
   To je užitečné, pokud je zásadní změnu velikosti či umístění záložku.  
  
  Projekty na úrovni dokumentu, můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků do dokumentu v projektu v době návrhu nebo v době běhu. Projekty doplňků VSTO, můžete přidat <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacích prvků do libovolného otevřeného dokumentu za běhu. Další informace najdete v tématu [postupy: Přidání Záložka ovládacích prvků do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="change-the-start-and-end-properties"></a>Změnit vlastnosti počáteční a koncové  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Změnit velikost záložky v projektu úrovni dokumentu v době návrhu  
  
1.  Vyberte záložku v **vlastnosti** okna.  
  
2.  Zvýšení nebo snížení hodnoty <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> vlastnost.  
  
3.  Zvýšení nebo snížení hodnoty <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> vlastnost.  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-runtime"></a>Změnit velikost záložky v projektu úrovni dokumentu za běhu  
  
1.  Upravit <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> a <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> vlastnosti <xref:Microsoft.Office.Tools.Word.Bookmark> vytvoří za běhu nebo v době návrhu.  
  
     Následující příklad kódu přidá na začátek Záložka s názvem pět znaků `SampleBookmark`. Tento kód předpokládá, že existují alespoň 5 znaků textu před záložkou.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     Následující příklad kódu přidá pět znaků na konec stejné záložku. Tento kód předpokládá, že existují alespoň 5 znaků textu po záložky.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-runtime"></a>Změnit velikost záložky v projektu doplňku VSTO za běhu  
  
1.  Upravit <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> a <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> vlastnosti <xref:Microsoft.Office.Tools.Word.Bookmark> vytvoří za běhu.  
  
     Následující příklad kódu vytvoří <xref:Microsoft.Office.Tools.Word.Bookmark> , který obsahuje text v prvním odstavci aktivního dokumentu a pak taky odebere pět znaků od začátku a konce <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreate-the-bookmark"></a>Znovu vytvořte záložku  
 Můžete změnit velikost záložky v úrovni dokumentu projektu tak, že přidáte novou záložku, která má stejný název jako existující záložku, ale s jinou velikostí.  
  
### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Znovu vytvořte záložku v projektu úrovni dokumentu v době návrhu  
  
1.  Vyberte text, který má být zahrnuté v novém <xref:Microsoft.Office.Tools.Word.Bookmark> ovládacího prvku.  
  
2.  Na **vložit** nabídky, klikněte na tlačítko **záložku**.  
  
3.  V **záložku** dialogového okna, vyberte název záložky, který chcete změnit velikost a klikněte na tlačítko **přidat**.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Postupy: Změna velikosti ovládacích prvků ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  