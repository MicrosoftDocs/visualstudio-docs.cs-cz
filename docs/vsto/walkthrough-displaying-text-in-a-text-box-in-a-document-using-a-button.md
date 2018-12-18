---
title: 'Návod: Zobrazení textu v textovém poli v dokumentu s použitím tlačítka'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 132a94b6e91148d943d998ab7e4aab96d0d74960
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822556"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Návod: Zobrazení textu v textovém poli v dokumentu s použitím tlačítka
  Tento návod ukazuje, jak pomocí tlačítka a textová pole v přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
- Přidání ovládacích prvků do dokumentu aplikace Word v projektu úrovni dokumentu v době návrhu.  
  
- Naplnění textové pole, když dojde ke kliknutí na tlačítko.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu dokumentu aplikace Word.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření projektu Wordového dokumentu s názvem **tlačítko Moje slovo**. V průvodci vyberte **vytvoříte nový textový dokument**.  
  
     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový Wordový dokument v návrháři a přidá **tlačítko Moje slovo** projektu **Průzkumníka řešení**.  
  
## <a name="add-controls-to-the-word-document"></a>Přidání ovládacích prvků do dokumentu aplikace Word  
 Ovládací prvky uživatelského rozhraní se skládají z tlačítko a textové pole pro Wordový dokument.  
  
### <a name="to-add-a-button-and-a-text-box"></a>Chcete-li přidat tlačítko a textové pole  
  
1. Ověřte, že dokument je otevřen v návrháři aplikace Visual Studio.  
  
2. Z **běžné ovládací prvky** karty **nástrojů**, přetáhněte <xref:Microsoft.Office.Tools.Word.Controls.TextBox> ovládací prvek v dokumentu.  
  
   > [!NOTE]  
   >  V aplikaci Word, se zahodí ovládacích prvků v řádku s textem ve výchozím nastavení. Můžete upravit způsob, jak ovládací prvky a shape – objekty jsou vloženy tak, že změníte výchozí na **upravit** karty **možnosti** dialogové okno v aplikaci Word.  
  
3. Na **zobrazení** nabídky, klikněte na tlačítko **okno vlastností**.  
  
4. Najít **TextBox1** v **vlastnosti** okno rozevíracího seznamu a změnit **název** vlastnosti textového pole na **ZobrazenýText**.  
  
5. Přetáhněte **tlačítko** ovládací prvek v dokumentu a změnit následující vlastnosti.  
  
   |Vlastnost|Hodnota|  
   |--------------|-----------|  
   |**Jméno**|**insertText**|  
   |**Text**|**Vložit Text**|  
  
   Teď můžete napsat kód, který se spustí po kliknutí na tlačítko.  
  
## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Rozbalte textové pole, když dojde ke kliknutí na tlačítko  
 Pokaždé, když uživatel klikne na tlačítko **Hello World!** je přidán do textového pole.  
  
### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Po kliknutí na tlačítko zapsat do textového pole  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ThisDocument**a potom klikněte na tlačítko **zobrazit kód** v místní nabídce.  
  
2.  Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události tlačítka.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  V C#, je nutné přidat obslužnou rutinu události pro tlačítko <xref:Microsoft.Office.Tools.Word.Document.Startup> událostí. Informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Teď můžete otestovat váš dokument, abyste měli jistotu, že zpráva **Hello World!** v textovém poli se zobrazí, když kliknete na tlačítko.  
  
### <a name="to-test-your-document"></a>K otestování vašeho dokumentu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Klikněte na tlačítko.  
  
3.  Ujistěte se, že **Hello World!** Zobrazí se v textovém poli.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základy používání tlačítka a textová pole v dokumentech aplikace Word. Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Chcete-li změnit formátování pomocí pole se seznamem. Další informace najdete v tématu [návod: Změna formátování dokumentů s použitím ovládacích prvků CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Pomocí přepínačů vyberte styly grafu. Další informace najdete v tématu [návod: aktualizace grafu v dokumentu s použitím přepínačů](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvky Windows Forms na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Návody pro aplikaci Word](../vsto/walkthroughs-using-word.md)   
 [Ukázky vývoje pro Office a názorné postupy](../vsto/office-development-samples-and-walkthroughs.md)   
 [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)  
  
  