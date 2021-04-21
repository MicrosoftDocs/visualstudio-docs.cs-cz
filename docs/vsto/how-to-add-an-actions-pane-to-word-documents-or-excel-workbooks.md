---
title: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel
description: Přečtěte si, že pokud chcete přidat podokno akcí systém Microsoft Office do dokumentu aplikace Word nebo do sešitu aplikace Microsoft Excel, je třeba nejprve vytvořit model Windows Forms uživatelský ovládací prvek.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9cf079727581b9cec4b6cb77a0a0c3f0b503b3a0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825521"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel
  Chcete-li přidat podokno akcí do aplikace systém Microsoft Office wordový dokument nebo do sešitu aplikace Microsoft Excel, nejprve vytvořte model Windows Forms uživatelský ovládací prvek. Pak přidejte uživatelský ovládací prvek do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> vlastnosti `ThisDocument.ActionsPane` pole (Word) nebo `ThisWorkbook.ActionsPane` pole (Excel) v projektu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Vytvoření uživatelského ovládacího prvku
 Následující postup ukazuje, jak vytvořit uživatelský ovládací prvek v projektu aplikace Word nebo Excel. Přidá také tlačítko k uživatelskému ovládacímu prvku, který při kliknutí zapisuje text do dokumentu nebo na sešit.

#### <a name="to-create-the-user-control"></a>Vytvoření uživatelského ovládacího prvku

1. Otevřete projekt na úrovni dokumentu aplikace Word nebo Excelu v aplikaci Visual Studio.

2. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

3. V dialogovém okně **Přidat novou položku** vyberte možnost **ovládací prvek podokno akce**, pojmenujte ji **HelloControl** a klikněte na tlačítko **Přidat**.

    > [!NOTE]
    > Můžete alternativně přidat položku **uživatelského ovládacího prvku** do projektu. Třídy generované **ovládacími prvky podokna akce** a položkami **uživatelského ovládacího prvku** jsou funkčně ekvivalentní.

4. Na kartě **model Windows Forms** panelu **nástrojů** přetáhněte ovládací prvek **tlačítko** na ovládací prvek.

    > [!NOTE]
    > Pokud ovládací prvek není viditelný v návrháři, poklikejte na **HelloControl** v **Průzkumník řešení**.

5. Přidejte kód do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události tlačítka. Následující příklad ukazuje kód pro systém Microsoft Office wordový dokument.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb" id="Snippet12":::

6. V jazyce C# je nutné přidat obslužnou rutinu události pro kliknutí na tlačítko. Tento kód lze umístit do `HelloControl` konstruktoru po volání `InitializeComponent` .

     Informace o tom, jak vytvořit obslužné rutiny událostí, naleznete v tématu [How to: Create event handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet13":::

## <a name="add-the-user-control-to-the-actions-pane"></a>Přidání uživatelského ovládacího prvku do podokna akce
 Chcete-li zobrazit podokno akcí, přidejte uživatelský ovládací prvek do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> vlastnosti `ThisDocument.ActionsPane` pole (Word) nebo `ThisWorkbook.ActionsPane` pole (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Přidání uživatelského ovládacího prvku do podokna akce

1. Přidejte následující kód do `ThisDocument` `ThisWorkbook` třídy nebo jako deklaraci na úrovni třídy (Nepřidávat tento kód do metody).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet14":::

2. Přidejte následující kód do `ThisDocument_Startup` obslužné rutiny události `ThisDocument` třídy nebo `ThisWorkbook_Startup` obslužné rutiny události `ThisWorkbook` třídy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet15":::

## <a name="see-also"></a>Viz také
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Návod: vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Návod: vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
