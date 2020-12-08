---
title: 'Postupy: Správa rozložení ovládacích prvků v podoknech akcí'
description: Zjistěte, jak můžete spravovat rozložení ovládacích prvků v podoknech akcí psaním kódu pro správné skládání uživatelských ovládacích prvků.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbee49a97ab6cb3e6084950e53f30b3cb6ce1b7c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848245"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Postupy: Správa rozložení ovládacích prvků v podoknech akcí
  Podokno akce je ukotveno napravo od dokumentu nebo listu ve výchozím nastavení. dá se ale ukotvit vlevo, nahoře nebo dole. Pokud používáte více uživatelských ovládacích prvků, můžete napsat kód pro správné vytvoření zásobníku uživatelských ovládacích prvků v podokně akce. Další informace najdete v tématu [Přehled podokna akcí](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Pořadí zásobníku ovládacích prvků závisí na tom, zda je podokno akce ukotveno svisle nebo vodorovně.

> [!NOTE]
> Pokud uživatel změní velikost podokna akce v době běhu, můžete nastavit ovládací prvky pro změnu velikosti pomocí podokna akce. Můžete použít <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost ovládacího prvku model Windows Forms k ukotvení ovládacích prvků do podokna akce. Další informace naleznete v tématu [How to: Anchor Controls on model Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Nastavení pořadí zásobníku pro ovládací prvky podokna akce

1. Otevřete projekt na úrovni dokumentu pro systém Microsoft Office Word, který obsahuje podokno akce s několika uživatelskými ovládacími prvky nebo vnořenými ovládacími prvky podokna akcí. Další informace najdete v tématu [Postup: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

2. Pravým tlačítkem myši klikněte na **ThisDocument.cs** nebo **ThisDocument. vb** v **Průzkumník řešení** a pak klikněte na **Zobrazit kód**.

3. V <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> obslužné rutině události podokna akce ověřte, zda je orientace podokna akce vodorovná.

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. Pokud je orientace vodorovná, navrstvení ovládacího prvku podokno akcí vlevo; v opačném případě je naskládat z horní části.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. V jazyce C# je nutné přidat obslužnou rutinu události pro do `ActionsPane` <xref:Microsoft.Office.Tools.Word.Document.Startup> obslužné rutiny události. Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. Spusťte projekt a ověřte, zda jsou ovládací prvky podokna akce umístěny vlevo a vpravo v případě, že je podokno akce ukotveno v horní části dokumentu, a ovládací prvky jsou vrstveny shora dolů, je-li podokno akce ukotveno na pravé straně dokumentu.

## <a name="example"></a>Příklad
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad vyžaduje:

- Projekt na úrovni dokumentu aplikace Word s podoknem akcí, které obsahuje více uživatelských ovládacích prvků nebo vnořených ovládacích prvků podokna akcí.

## <a name="see-also"></a>Viz také
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Návod: vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Návod: vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
