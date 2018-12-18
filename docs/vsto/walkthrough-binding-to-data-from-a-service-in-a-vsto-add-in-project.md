---
title: 'Návod: Vytvoření vazby k datům ze služby v projektu doplňku VSTO'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4ebf998dc7c278fda1e605d18198945958a7fed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933180"
---
# <a name="walkthrough-bind-to-data-from-a-service-in-a-vsto-add-in-project"></a>Návod: Vytvoření vazby k datům ze služby v projektu doplňku VSTO
  Vytvoření vazby dat k ovládacím prvkům hostitele v projekty doplňku VSTO. Tento návod ukazuje, jak přidat ovládací prvky do dokumentu aplikace Microsoft Office Word, svázat ovládací prvky dat načtených z obsahu služby MSDN a reagovat na události v době běhu.  
  
 **Platí pro:** informace v tomto tématu se vztahují na projekty na úrovni aplikace pro Word 2010. Další informace najdete v tématu [Dostupné funkce podle aplikace Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Tento návod znázorňuje následující úlohy:  
  
- Přidání <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ovládacího prvku do dokumentu za běhu.  
  
- Vytvoření vazby <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ovládacího prvku k datům z webové služby.  
  
- Reakce na <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> události <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ovládacího prvku.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] nebo [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-a-new-project"></a>Vytvoření nového projektu  
 Prvním krokem je vytvoření projektu doplňku VSTO pro Word.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření projektu doplňku VSTO pro Word s názvem **služba obsah MTPS**, pomocí jazyka Visual Basic nebo C#.  
  
     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře `ThisAddIn.vb` nebo `ThisAddIn.cs` soubor a přidá projekt do **Průzkumníka řešení**.  
  
## <a name="add-a-web-service"></a>Přidat odkaz webové služby  
 V tomto návodu pomocí webové služby názvem MTPS obsahu služby. Tato webová služba vrátí informace ze zadané článku na webu MSDN v podobě prostého textu nebo řetězec XML. Později ukazuje, jak zobrazení vrácených informacích v obsahu prvku.  
  
### <a name="to-add-the-mtps-content-service-to-the-project"></a>Postup přidání služby content MTPS do projektu  
  
1.  Na **Data** nabídky, klikněte na tlačítko **přidat nový zdroj dat**.  
  
2.  V **Průvodce konfigurací zdroje dat**, klikněte na tlačítko **služby**a potom klikněte na tlačítko **Další**.  
  
3.  V **adresu** pole, zadejte následující adresu URL:  
  
     **http://services.msdn.microsoft.com/ContentServices/ContentService.asmx**  
  
4.  Klikněte na tlačítko **Přejít**.  
  
5.  V **Namespace** zadejte **ContentService**a klikněte na tlačítko **OK**.  
  
6.  V **Průvodce přidáním odkazu** dialogové okno, klikněte na tlačítko **Dokončit**.  
  
## <a name="add-a-content-control-and-bind-to-data-at-runtime"></a>Přidání ovládacího prvku obsahu a vytvoření vazby k datům za běhu  
 V doplňku VSTO projektů přidání a vytvoření vazby ovládacích prvků za běhu. V tomto návodu nakonfigurujte ovládací prvek obsahu k načtení dat z webové služby, když uživatel klikne v ovládacím prvku.  
  
### <a name="to-add-a-content-control-and-bind-to-data"></a>Přidání ovládacího prvku obsahu a vytvořit vazbu na data  
  
1.  V `ThisAddIn` třídy, deklarujte proměnné MTPS obsah služby, ovládací prvek obsahu a datové vazby.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#2)]  
  
2.  Přidejte následující metodu do `ThisAddIn` třídy. Tato metoda vytvoří ovládací prvek obsahu na začátku aktivní dokument.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#4)]  
  
3.  Přidejte následující metodu do `ThisAddIn` třídy. Tato metoda inicializuje objekty, které jsou potřebné k vytvoření a odeslat požadavek na webovou službu.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#6)]  
  
4.  Vytvořte obslužnou rutinu události pro načtení dokumentu knihovny MSDN o obsahu ovládací prvky, pokud uživatel klikne v obsahu, řízení a svázat data do ovládacího prvku obsahu.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#5)]  
  
5.  Volání `AddRichTextControlAtRange` a `InitializeServiceObjects` metody ze `ThisAddIn_Startup` metody. Programátoři v C# přidejte obslužnou rutinu události.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/CSharp/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_bindingdatatocontentcontrol/ThisAddIn.vb#3)]  
  
## <a name="test-the-add-in"></a>Testování v aplikaci  
 Při otevření aplikace <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ovládací prvek se zobrazí. Text v řízení změn, když kliknete dovnitř.  
  
### <a name="to-test-the-vsto-add-in"></a>K otestování doplňku VSTO  
  
1.  Stisknutím klávesy **F5**.  
  
2.  Klikněte na tlačítko uvnitř obsahu ovládacího prvku.  
  
     Informace ze služby MTPS obsah stáhli a zobrazit uvnitř ovládacího prvku obsahu.  
  
## <a name="see-also"></a>Viz také:  
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  