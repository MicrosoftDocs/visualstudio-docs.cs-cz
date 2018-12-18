---
title: 'Postupy: Správa rozložení ovládacích prvků v podoknech akcí'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f523d56b189fb1517df7e22d18cd689e9300eff3
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255912"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Postupy: Správa rozložení ovládacích prvků v podoknech akcí
  Podokna akcí ukotven napravo od dokumentu nebo sešitu ve výchozím nastavení; Můžete však být ukotven na levé straně, horní nebo dolní. Pokud používáte více uživatelských ovládacích prvků, můžete napsat kód pro správně zásobníku uživatelské ovládací prvky v podokně Akce. Další informace najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Zásobník pořadí ovládacích prvků závisí na tom, jestli je v podokně Akce ukotven vodorovně nebo svisle.  
  
> [!NOTE]  
>  Když uživatel změní velikost podokna akce za běhu, můžete nastavit ovládací prvky ke změně velikosti se v podokně Akce. Můžete použít <xref:System.Windows.Forms.Control.Anchor%2A> vlastností ovládacího prvku Windows Forms do ovládacích prvků ukotvení do podokna akce. Další informace najdete v tématu [postupy: Ukotvování ovládacích prvků ve Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení prostředí Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Nastavení pořadí zásobníku ovládací prvky pro podokno akcí  
  
1.  Otevřete projekt na úrovni dokumentu a pro aplikace Microsoft Office Word, která zahrnuje podokna akcí s více uživatelských ovládacích prvků nebo ovládací prvky podokna akce vnořené. Další informace najdete v tématu [postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  Klikněte pravým tlačítkem na **ThisDocument.cs** nebo **ThisDocument.vb** v **Průzkumníku řešení** a pak klikněte na **kód zobrazení**.  
  
3.  V <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> obslužné rutiny události podokna akcí, zkontrolujte, zda je vodorovné orientaci v podokně Akce.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]  
  
4.  Pokud je vodorovné orientaci, ovládací prvky zásobníku v podokně Akce zleva; v opačném z horní části zásobníku je.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]  
  
5.  V jazyce C#, je nutné přidat obslužné rutiny události pro `ActionsPane` k <xref:Microsoft.Office.Tools.Word.Document.Startup> obslužné rutiny události. Informace o vytváření obslužných rutin událostí najdete v tématu [postupy: vytváření obslužných rutin událostí v projektech Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]  
  
6.  Spusťte projekt a ověřte, že ovládací prvky podokna akce přibývají zprava doleva když v podokně Akce ukotven v horní části dokumentu a ovládací prvky jsou skládaný shora dolů, pokud je ukotvena podokna akce na pravé straně dokumentu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Určuje projekt na úrovni dokumentu aplikace Word s vnořené akce podokna nebo podokna akcí, která obsahuje více uživatelských ovládacích prvků.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)   
 [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Postupy: Přidání podokně akcí do dokumentů aplikace Word nebo v aplikaci Excel sešitů](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Návod: Vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Návod: Vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  