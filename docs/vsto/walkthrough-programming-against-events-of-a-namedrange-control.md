---
title: 'Návod: program na události ovládacího prvku NamedRange'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, programming against events
- worksheets, changing cell values
- NamedRange control, events
- worksheets, events
- worksheets, automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2e5ce12e2de8274afd2c27d4ece36529563a6386
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584934"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Návod: program na události ovládacího prvku NamedRange
  Tento návod ukazuje, jak přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do listu aplikace systém Microsoft Office Excel a program na jeho události pomocí nástrojů pro vývoj pro Office v sadě Visual Studio.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 V tomto návodu se naučíte:

- Přidejte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do listu.

- Program pro <xref:Microsoft.Office.Tools.Excel.NamedRange> události řízení.

- Otestujte svůj projekt.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

## <a name="create-the-project"></a>Vytvoření projektu
 V tomto kroku vytvoříte projekt sešitu aplikace Excel pomocí sady Visual Studio.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel s názvem **Moje události s názvem "moje pojmenované rozsahy**". Ujistěte se, že je vybraná možnost **vytvořit nový dokument** . Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otevře nový excelový sešit v návrháři a přidá projekt **události moje pojmenované oblasti** do **Průzkumník řešení**.

## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Přidat text a pojmenované rozsahy do listu
 Vzhledem k tomu, že ovládací prvky hostitele jsou rozšířené objekty Office, můžete je přidat do dokumentu stejným způsobem jako při přidávání nativního objektu. Například můžete přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek aplikace Excel do listu otevřením nabídky **Vložit** , přechodem na položku **název**a volbou možnosti **definovat**. Ovládací prvek lze také přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> přetažením z **panelu nástrojů** na list.

 V tomto kroku přidáte do listu dva pojmenované ovládací prvky rozsahu pomocí **sady nástrojů**a následně do listu přidáte text.

### <a name="to-add-a-range-to-your-worksheet"></a>Přidání rozsahu do listu

1. Ověřte, že je *Events.xlsx* sešit otevřený v návrháři sady Visual Studio se `Sheet1` zobrazeným názvem.

2. Z karty **ovládací prvky aplikace Excel** v panelu nástrojů přetáhněte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do buňky **a1** v `Sheet1` .

     Zobrazí se dialogové okno **Přidat ovládací prvek NamedRange** .

3. Ověřte, zda se **$A $1** zobrazí v upravitelném textovém poli a zda je vybrána buňka **a1** . Pokud ne, klikněte na buňku **a1** a vyberte ji.

4. Klikněte na **OK**.

     Buňka **a1** se zobrazí v rozsahu s názvem `namedRange1` . V listu není žádné viditelné označení, ale zobrazí se `namedRange1` v poli **název** (umístěný hned nad listem na levé straně), když je vybraná buňka **a1** .

5. <xref:Microsoft.Office.Tools.Excel.NamedRange>Do buňky **B3**přidejte další ovládací prvek.

6. Ověřte, zda se **$B $3** zobrazí v upravitelném textovém poli a zda je vybrána buňka **B3** . Pokud ne, klikněte na buňku **B3** a vyberte ji.

7. Klikněte na **OK**.

     Buňka **B3** se zobrazí v rozsahu s názvem `namedRange2` .

### <a name="to-add-text-to-your-worksheet"></a>Přidání textu do listu

1. Do buňky **a1**zadejte následující text:

    **Toto je příklad ovládacího prvku NamedRange.**

2. Do buňky **a3** (vlevo od `namedRange2` ) zadejte následující text:

    **Událost**

   V následujících částech budete psát kód, který vloží text do `namedRange2` a upraví vlastnosti `namedRange2` ovládacího prvku v reakci na <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> události, a <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> `namedRange1` .

## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Přidejte kód, který bude reagovat na událost BeforeDoubleClick

### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Vložení textu do NamedRange2 založeného na události BeforeDoubleClick

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **List1. vb** nebo **Sheet1.cs** a vyberte **Zobrazit kód**.

2. Přidejte kód, aby `namedRange1_BeforeDoubleClick` obslužná rutina události vypadala takto:

     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]

3. V jazyce C# je nutné přidat obslužné rutiny události pro pojmenovaný rozsah, jak je znázorněno v <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> události níže. Informace o vytváření obslužných rutin událostí najdete v tématu [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]

## <a name="add-code-to-respond-to-the-change-event"></a>Přidat kód, který reaguje na událost změny

### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Vložení textu do namedRange2 na základě události Change

1. Přidejte kód, aby `NamedRange1_Change` obslužná rutina události vypadala takto:

     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]

    > [!NOTE]
    > Vzhledem k tomu, že Poklikáním na buňku v oblasti aplikace Excel přejdete do režimu úprav, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> dojde k události, když je výběr přesunut mimo rozsah, a to i v případě, že nedošlo k žádným změnám textu.

## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Přidejte kód, který bude reagovat na událost SelectionChange

### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Vložení textu do namedRange2 založeného na události SelectionChange

1. Přidejte kód, aby **NamedRange1_SelectionChange** obslužná rutina události vypadala takto:

     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]

    > [!NOTE]
    > Vzhledem k tomu, že dvojitým kliknutím na buňku v oblasti aplikace Excel dojde k přesunutí výběru do rozsahu, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> dojde k události před <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> výskytem události.

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete testovat sešit a ověřit, zda text popisující události <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku je vložen do jiného pojmenovaného rozsahu, když jsou události vyvolány.

### <a name="to-test-your-document"></a>Testování dokumentu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Umístěte kurzor do umístění `namedRange1` a ověřte, zda je vložen text týkající se <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> události a zda je do listu vložen komentář.

3. Dvakrát klikněte na tlačítko uvnitř `namedRange1` a ověřte, zda je text týkající se <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> událostí vložen pomocí červeného textu s kurzívou v `namedRange2` .

4. Klikněte mimo `namedRange1` a Všimněte si, že událost změny nastane při opuštění režimu úprav, i když se neudělala žádná změna textu.

5. Změňte text v rámci `namedRange1` .

6. Klikněte na tlačítko mimo `namedRange1` a ověřte, zda je text týkající se <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> události vložen do pole modrý text `namedRange2` .

## <a name="next-steps"></a>Další kroky
 Tento názorný postup ukazuje základy programování před událostmi <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku. Tady je úkol, který může být další:

- Nasazení projektu. Další informace najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Viz také
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ovládací prvek NamedRange](../vsto/namedrange-control.md)
- [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
