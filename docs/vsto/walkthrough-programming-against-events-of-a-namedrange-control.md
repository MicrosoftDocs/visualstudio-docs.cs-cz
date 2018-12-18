---
title: 'Návod: Program ošetření událostí ovládacího prvku NamedRange'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3f8b55cda9576a0203857b3fdaeccbb205b42168
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812515"
---
# <a name="walkthrough-program-against-events-of-a-namedrange-control"></a>Návod: Program ošetření událostí ovládacího prvku NamedRange
  Tento návod ukazuje, jak přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku na list aplikace Microsoft Office Excel a program před jeho událostmi s využitím vývojových nástrojů Office v sadě Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 V tomto návodu se dozvíte, jak:  
  
-   Přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do listu.  
  
-   Programovat proti <xref:Microsoft.Office.Tools.Excel.NamedRange> řídit události.  
  
-   Otestování vašeho projektu.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 V tomto kroku vytvoříte pomocí sady Visual Studio projektu sešitu aplikace Excel.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvořte projekt sešitu aplikace Excel s názvem **Moje události s názvem rozsah**. Ujistěte se, že **vytvoříte nový textový dokument** zaškrtnuto. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **Moje události s názvem rozsah** projektu **Průzkumníka řešení**.  
  
## <a name="add-text-and-named-ranges-to-the-worksheet"></a>Přidání textu a pojmenované oblasti do listu  
 Protože hostitelské ovládací prvky jsou rozšířených objektů Office, můžete je přidat do dokumentu stejným způsobem by přidat nativní objekt. Například můžete přidat aplikace Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do listu tak, že otevřete **vložit** nabídky, přejdete na **název**a zvolíte **definovat**. Můžete také přidat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku z jeho přetažením **nástrojů** do listu.  
  
 V tomto kroku přidáte ovládací prvky dvou pojmenované oblasti do listu pomocí **nástrojů**a pak přidejte text do listu.  
  
### <a name="to-add-a-range-to-your-worksheet"></a>Chcete-li přidat rozsah list  
  
1.  Ověřte, že *Moje Events.xlsx oblast s názvem* sešitu je otevřen v návrháři aplikace Visual Studio s `Sheet1` zobrazí.  
  
2.  Z **ovládací prvky Excelu** kartu na panelu nástrojů přetáhněte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do buňky **A1** v `Sheet1`.  
  
     **Přidat ovládací prvek NamedRange** zobrazí se dialogové okno.  
  
3.  Ověřte, že **$A$ 1** se zobrazí v upravitelné textové pole a buňka **A1** zaškrtnuto. Pokud není, klikněte na buňku **A1** ji vyberte.  
  
4.  Klikněte na tlačítko **OK**.  
  
     Buňka **A1** stane oblast s názvem `namedRange1`. Není by na listu, ale `namedRange1` se zobrazí v **název** políčka (přímo nad listu na levé straně) při buňky **A1** zaškrtnuto.  
  
5.  Přidejte další <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku do buňky **B3**.  
  
6.  Ověřte, že **$B$ 3** se zobrazí v upravitelné textové pole a buňka **B3** zaškrtnuto. Pokud není, klikněte na buňku **B3** ji vyberte.  
  
7.  Klikněte na tlačítko **OK**.  
  
     Buňka **B3** stane oblast s názvem `namedRange2`.  
  
### <a name="to-add-text-to-your-worksheet"></a>Chcete-li přidat text do listu  
  
1. V buňce **A1**, zadejte následující text:  
  
    **Toto je příklad namedrange – ovládací prvek.**  
  
2. V buňce **A3** (nalevo od `namedRange2`), zadejte následující text:  
  
    **Události:**  
  
   V následujících částech můžete psát kód, který vloží text do `namedRange2` a upraví vlastnosti `namedRange2` ovládacího prvku v reakci <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, a <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> události `namedRange1`.  
  
## <a name="add-code-to-respond-to-the-beforedoubleclick-event"></a>Přidejte kód pro reakce na událost BeforeDoubleClick  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-beforedoubleclick-event"></a>Pro vložení textu na NamedRange2 na základě BeforeDoubleClick události  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Sheet1.vb** nebo **Sheet1.cs** a vyberte **zobrazit kód**.  
  
2.  Přidejte kód proto `namedRange1_BeforeDoubleClick` obslužná rutina události vypadat takhle:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  V jazyce C#, musíte přidat obslužné rutiny událostí pro pojmenované oblasti, jak je znázorněno <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> následující událost. Informace o vytváření obslužných rutin událostí, naleznete v tématu [postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## <a name="add-code-to-respond-to-the-change-event"></a>Přidejte kód pro reakce na událost změny  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-change-event"></a>Vložit text do namedRange2 založené na události změny  
  
1.  Přidejte kód proto `NamedRange1_Change` obslužná rutina události vypadat takhle:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Vzhledem k tomu, že poklikáte na buňku v oblasti aplikace Excel přejde do režimu úprav <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> události dojde, když se výběr je přesunut mimo rozsah, i v případě, že nedošlo k žádným změnám na text.  
  
## <a name="add-code-to-respond-to-the-selectionchange-event"></a>Přidejte kód pro reakce na SelectionChange – událost  
  
### <a name="to-insert-text-into-namedrange2-based-on-the-selectionchange-event"></a>Pro vložení textu na namedRange2 podle SelectionChange – událost  
  
1.  Přidejte kód, tak na **NamedRange1_SelectionChange** obslužnou rutinu události vypadá následovně:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Vzhledem k tomu, že poklikáte na buňku v oblasti aplikace Excel způsobí, že přesunutí do rozsahu, <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> před dojde k události <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> dojde k události.  
  
## <a name="test-the-application"></a>Testování aplikace  
 Teď můžete otestovat sešit ověřit tento text popisující událostí <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek je vložen do jiné oblasti s názvem při události jsou vyvolány.  
  
### <a name="to-test-your-document"></a>K otestování vašeho dokumentu  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Umístěte ukazatel myši v `namedRange1`a ověřte, zda text týkající <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> událostí je vložen a komentář se vloží do listu.  
  
3.  Poklikejte na uvnitř `namedRange1`a ověřte, zda text ohledně <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> události se vloží s červený text kurzívou v `namedRange2`.  
  
4.  Klikněte na tlačítko mimo `namedRange1` a Všimněte si, že dojde k události změny při ukončení režimu úprav, přestože se neprovedly žádné změny textu.  
  
5.  Změní celý text v rámci `namedRange1`.  
  
6.  Klikněte na tlačítko mimo `namedRange1`a ověřte, zda text ohledně <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> vložena událost s modrý text do `namedRange2`.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základy programování v události <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku. Tady je úkol, který by mohl pocházet Další:  
  
-   Nasazení projektu. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Namedrange – ovládací prvek](../vsto/namedrange-control.md)   
 [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Postupy: vytváření obslužných rutin událostí v projektech pro systém Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  