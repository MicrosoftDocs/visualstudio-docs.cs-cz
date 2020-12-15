---
title: Zobrazit text v textovém poli v dokumentu pomocí tlačítka
description: Přečtěte si, jak můžete používat tlačítka a textová pole v přizpůsobení na úrovni dokumentu pro Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1cda1fe3e7430ff30dcc3b3921eb2bcd4d31b699
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522753"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Návod: zobrazení textu v textovém poli v dokumentu s použitím tlačítka
  Tento návod ukazuje, jak používat tlačítka a textová pole v přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Tento návod znázorňuje následující úlohy:

- Přidávání ovládacích prvků do dokumentu aplikace Word v projektu na úrovni dokumentu v době návrhu.

- Vyplnění textového pole při kliknutí na tlačítko.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Vytvoření projektu
 Prvním krokem je vytvoření projektu wordového dokumentu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt wordového dokumentu s tlačítkem název **Moje slovo**. V průvodci vyberte možnost **vytvořit nový dokument**.

     Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový wordový dokument v návrháři a přidá projekt **tlačítka moje slovo** do **Průzkumník řešení**.

## <a name="add-controls-to-the-word-document"></a>Přidání ovládacích prvků do dokumentu aplikace Word
 Ovládací prvky uživatelského rozhraní se skládají z tlačítka a textového pole v dokumentu aplikace Word.

### <a name="to-add-a-button-and-a-text-box"></a>Přidání tlačítka a textového pole

1. Ověřte, že je dokument otevřený v návrháři sady Visual Studio.

2. Na kartě **běžné ovládací prvky** **panelu nástrojů** přetáhněte <xref:Microsoft.Office.Tools.Word.Controls.TextBox> ovládací prvek do dokumentu.

   > [!NOTE]
   > V aplikaci Word jsou ovládací prvky ve výchozím nastavení zavěšeny textem. Můžete upravit způsob, jakým jsou ovládací prvky a objekty tvarů vloženy, změnou výchozí hodnoty na kartě **Upravit** v dialogovém okně **Možnosti** ve Wordu.

3. V nabídce **zobrazení** klikněte na položku **Vlastnosti okno**.

4. V rozevíracím seznamu okno **vlastností** Najděte text **TextBox1** a změňte vlastnost **název** textového pole na **zobrazenýtext**.

5. Přetáhněte ovládací prvek **tlačítko** do dokumentu a změňte následující vlastnosti.

   |Vlastnost|Hodnota|
   |--------------|-----------|
   |**Název**|**insertText**|
   |**Text**|**Vložit text**|

   Nyní můžete napsat kód, který se spustí po kliknutí na tlačítko.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Naplnit textové pole při kliknutí na tlačítko
 Pokaždé, když uživatel klikne na tlačítko, **Hello World!** je přidáno do textového pole.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Zápis do textového pole při kliknutí na tlačítko

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **ThisDocument** a potom klikněte na **Zobrazit kód** v místní nabídce.

2. Přidejte následující kód do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události tlačítka.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. V jazyce C# je nutné přidat obslužnou rutinu události pro tlačítko do <xref:Microsoft.Office.Tools.Word.Document.Startup> události. Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete dokument otestovat, abyste se ujistili, že zpráva **Hello World!** se zobrazí v textovém poli po kliknutí na tlačítko.

### <a name="to-test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Klikněte na tlačítko.

3. Potvrďte, že **Hello World!** zobrazí se v textovém poli.

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy používání tlačítek a textových polí v dokumentech aplikace Word. Tady jsou některé úkoly, které mohou být další:

- Změna formátování pomocí pole se seznamem. Další informace naleznete v tématu [Návod: Změna formátování dokumentu pomocí ovládacích prvků CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Výběr stylů grafu pomocí přepínačů Další informace najdete v tématu [Návod: aktualizace grafu v dokumentu pomocí přepínačů](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Viz také
- [Přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Návody pomocí aplikace Word](../vsto/walkthroughs-using-word.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
