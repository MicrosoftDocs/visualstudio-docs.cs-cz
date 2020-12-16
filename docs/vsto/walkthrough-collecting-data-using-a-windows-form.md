---
title: 'Návod: shromáždění dat pomocí formuláře Windows'
description: Otevřete formulář Windows z přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Excel, shromážděte informace od uživatele a zapište tyto informace do buňky listu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], Windows Forms
- Windows Forms [Office development in Visual Studio], collecting data
- forms [Office development in Visual Studio], walkthroughs
- worksheets [Office development in Visual Studio], collecting data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58d6f58f732d4a52aade6ff3678842900f1c29cd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527167"
---
# <a name="walkthrough-collect-data-by-using-a-windows-form"></a>Návod: shromáždění dat pomocí formuláře Windows
  Tento návod ukazuje, jak otevřít formulář Windows z přizpůsobení na úrovni dokumentu pro systém Microsoft Office Excel, shromažďovat informace od uživatele a zapisovat tyto informace do buňky listu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 I když tento návod používá pro Excel konkrétně projekt na úrovni dokumentu, koncepce znázorněné v tomto návodu se vztahují na jiné projekty Office.

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 Prvním krokem je vytvoření projektu excelového sešitu.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel s názvem **WinFormInput** a vyberte možnost **vytvořit nový dokument** v průvodci. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový excelový sešit v návrháři a přidá projekt **WinFormInput** do **Průzkumník řešení**.

## <a name="add-a-namedrange-control-to-the-worksheet"></a>Přidání ovládacího prvku NamedRange do listu

### <a name="to-add-a-named-range-to-sheet1"></a>Postup přidání pojmenovaného rozsahu do List1

1. Vyberte buňku **a1** na `Sheet1` .

2. Do pole **název** zadejte **formInput**.

     Pole **název** je umístěno nalevo od řádku vzorců, a to těsně nad sloupcem **A** listu.

3.  Stiskněte **Enter**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Ovládací prvek je přidán do buňky **a1**. List neobsahuje žádné viditelné údaje, ale **formInput** se zobrazí v poli **název** (hned nad listem na levé straně) a v okně **vlastnosti** , když je vybrána buňka **a1** .

## <a name="add-a-windows-form-to-the-project"></a>Přidat formulář Windows do projektu
 Vytvoří formulář Windows, který uživateli vyzve k zadání informací.

### <a name="to-add-a-windows-form"></a>Přidání formuláře Windows

1. Vyberte projekt **WinFormInput** v **Průzkumník řešení**.

2. V nabídce **projekt** klikněte na tlačítko **Přidat formulář systému Windows**.

3. Pojmenujte formulář **GetInputString. vb** nebo **GetInputString.cs** a pak klikněte na **Přidat**.

    Nový formulář se otevře v návrháři.

4. Přidejte <xref:System.Windows.Forms.TextBox> a <xref:System.Windows.Forms.Button> do formuláře.

5. Vyberte tlačítko, v okně **vlastnosti** vyhledejte **text** vlastnosti a změňte text na **OK**.

   Dále přidejte kód do `ThisWorkbook.vb` nebo `ThisWorkbook.cs` ke shromáždění informací o uživateli.

## <a name="display-the-windows-form-and-collecting-information"></a>Zobrazení formuláře Windows a shromažďování informací
 Vytvořte instanci `GetInputString` formuláře Windows a zobrazte ho a pak zapište informace o uživateli do buňky v listu.

#### <a name="to-display-the-form-and-collect-information"></a>Zobrazení formuláře a shromažďování informací

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **ThisWorkbook. vb** nebo **ThisWorkbook.cs** a pak klikněte na **Zobrazit kód**.

2. V <xref:Microsoft.Office.Tools.Excel.Workbook.Open> obslužné rutině události pro `ThisWorkbook` přidejte následující kód, který deklaruje proměnnou pro formulář `GetInputString` a pak zobrazí formulář.

   > [!NOTE]
   > V jazyce C# je nutné přidat obslužnou rutinu události, jak je znázorněno v <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> události níže. Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#1)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#1)]

3. Vytvořte metodu nazvanou `WriteStringToCell` , která zapíše text do pojmenovaného rozsahu. Tato metoda se volá z formuláře a vstup uživatele se předává <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacímu prvku, `formInput` na buňce **a1**.

    [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/CSharp/WinFormInputCS/ThisWorkbook.cs#2)]
    [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../vsto/codesnippet/VisualBasic/WinFormInput/ThisWorkbook.vb#2)]

   Potom do formuláře přidejte kód pro zpracování události kliknutí na tlačítko.

## <a name="send-information-to-the-worksheet"></a>Odeslat informace do listu

### <a name="to-send-information-to-the-worksheet"></a>Odeslání informací do listu

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **GetInputString** a potom klikněte na **Návrhář zobrazení**.

2. Dvojím kliknutím na tlačítko otevřete soubor kódu s <xref:System.Windows.Forms.Control.Click> přidaným obslužnou rutinou události tlačítka.

3. Přidejte kód do obslužné rutiny události, abyste převzali vstup z textového pole, odešlete ho do funkce `WriteStringToCell` a pak zavřete formulář.

     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/CSharp/WinFormInputCS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../vsto/codesnippet/VisualBasic/WinFormInput/GetInputString.vb#3)]

## <a name="test"></a>Test
 Nyní můžete spustit projekt. Zobrazí se formulář Windows a váš vstup se zobrazí v listu.

### <a name="to-test-your-workbook"></a>Test sešitu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Potvrďte, že se zobrazí formulář Windows.

3. Do textového pole zadejte **Hello World** a pak klikněte na **OK**.

4. Potvrďte, že **Hello World** se zobrazí v buňce **a1** listu.

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy zobrazování formuláře Windows a předávání dat do listu. Mezi další úlohy, které můžete chtít provést, patří:

- Použijte ovládací prvky model Windows Forms v excelovém sešitě nebo v dokumentu aplikace Word. Další informace najdete v tématu [přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

- Upravte uživatelské rozhraní aplikace systém Microsoft Office z přizpůsobení na úrovni dokumentu nebo doplňku VSTO. Další informace najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Viz také
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Návody pomocí aplikace Word](../vsto/walkthroughs-using-word.md)
- [Návody pomocí Excelu](../vsto/walkthroughs-using-excel.md)
