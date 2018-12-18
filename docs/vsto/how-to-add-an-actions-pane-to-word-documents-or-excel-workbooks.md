---
title: 'Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f70511d0490032204789dc037a13847a10b5cbe6
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948358"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel
  K přidání podokna akcí do dokumentů aplikace Microsoft Office Word nebo sešitu aplikace Microsoft Excel, vytvoření uživatelského ovládacího prvku Windows Forms. Pak přidejte uživatelský ovládací prvek <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> vlastnost `ThisDocument.ActionsPane` pole (slova) nebo `ThisWorkbook.ActionsPane` pole (Excel) ve vašem projektu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Vytvoření uživatelského ovládacího prvku  
 Následující postup ukazuje, jak vytvořit uživatelský ovládací prvek aplikace Word nebo Excel projektu. Také přidá tlačítko do uživatelského ovládacího prvku, který zapíše text do dokumentem nebo sešitem, když dojde ke kliknutí na.  
  
#### <a name="to-create-the-user-control"></a>Chcete-li vytvořit uživatelský ovládací prvek  
  
1.  V sadě Visual Studio otevřete projekt úrovni dokumentu aplikace Word nebo Excel.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
3.  V **přidat novou položku** dialogu **ovládacího prvku podokna akcí**, pojmenujte ho **HelloControl**a klikněte na tlačítko **přidat**.  
  
    > [!NOTE]  
    >  Můžete také přidat **uživatelský ovládací prvek** položky do projektu. Třídy generované **ovládacího prvku podokna akcí** a **uživatelský ovládací prvek** položky jsou funkčně ekvivalentní.  
  
4.  Z **Windows Forms** karty **nástrojů** přetáhněte **tlačítko** ovládacího prvku do ovládacího prvku.  
  
    > [!NOTE]  
    >  Pokud ovládací prvek není viditelný v návrháři, dvakrát klikněte na tlačítko **HelloControl** v **Průzkumníka řešení**.  
  
5.  Přidejte kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události tlačítka. Následující příklad ukazuje kód pro dokument aplikace Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  V jazyce C# je nutné přidat obslužnou rutinu události pro kliknutí na tlačítko. Tento kód v můžete umístit `HelloControl` konstruktor po volání `InitializeComponent`.  
  
     Informace o tom, jak vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Přidat uživatelský ovládací prvek do podokna akcí  
 Pokud chcete zobrazit podokno akcí, přidejte uživatelský ovládací prvek <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> vlastnost `ThisDocument.ActionsPane` pole (slova) nebo `ThisWorkbook.ActionsPane` pole (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Chcete-li přidat uživatelský ovládací prvek do podokna akcí  
  
1.  Přidejte následující kód, který `ThisDocument` nebo `ThisWorkbook` třídu jako deklaraci třídy úrovni (nepřidávejte tento kód do metody).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Přidejte následující kód, který `ThisDocument_Startup` obslužná rutina události `ThisDocument` třídy nebo `ThisWorkbook_Startup` obslužná rutina události `ThisWorkbook` třídy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Viz také:  
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)   
 [Návod: Vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Návod: Vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  