---
title: Vytvoření vztahu hlavní podrobnosti pomocí datové sady uložených v mezipaměti
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0acf84dd983a8c10f2af526ae0bb904eaa90a360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328356"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Návod: Vytvoření vztahu hlavní podrobnosti pomocí datové sady uložené v mezipaměti
  Tento návod ukazuje vytvoření vztahu hlavní/podrobnosti na listu a ukládání dat do mezipaměti, aby bylo možné řešení použít offline.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 V tomto návodu se naučíte:

- Přidejte ovládací prvky do listu.

- Nastavte datovou sadu pro ukládání do mezipaměti v listu.

- Přidejte kód, který umožní procházení záznamů.

- Otestujte svůj projekt.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]:

- Přístup k ukázkové databázi Northwind SQL Server. Databáze může být na vašem vývojovém počítači nebo na serveru.

- Oprávnění ke čtení a zápisu do databáze SQL Server.

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 V tomto kroku vytvoříte projekt sešitu aplikace Excel.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Vytvořte projekt sešitu aplikace Excel s názvem **Moje hlavní-podrobnosti**pomocí Visual Basic nebo C#. Ujistěte se, že je vybraná možnost **vytvořit nový dokument** . Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio otevře nový excelový sešit v návrháři a přidá **můj hlavní projekt s podrobnostmi** do **Průzkumník řešení**.

## <a name="create-the-data-source"></a>Vytvoření zdroje dat
 Pomocí okna **zdroje dat** přidejte do projektu typovou datovou sadu.

### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat

1. Pokud není okno **zdroje dat** viditelné, zobrazte ho tak, že v řádku nabídek vyberete možnost **Zobrazit**  >  **ostatní**  >  **zdroje dat**Windows.

2. Zvolením možnosti **Přidat nový zdroj dat** spusťte **Průvodce konfigurací zdroje dat**.

3. Vyberte **databáze** a pak klikněte na **Další**.

4. Vyberte datové připojení k ukázce databáze Northwind SQL Server databázi nebo přidejte nové připojení pomocí tlačítka **nové připojení** .

5. Po výběru nebo vytvoření připojení klikněte na **Další**.

6. Zrušte zaškrtnutí políčka Uložit připojení, pokud je vybráno, a poté klikněte na tlačítko **Další**.

7. Rozbalte uzel **tabulky** v okně **objekty databáze** .

8. Vyberte tabulku **Orders (objednávky** ) a tabulku **Podrobnosti objednávky** .

9. Klikněte na **Finish** (Dokončit).

   Průvodce přidá tyto dvě tabulky do okna **zdroje dat** . Také přidá do projektu typovou datovou sadu, která je viditelná v **Průzkumník řešení**.

## <a name="add-controls-to-the-worksheet"></a>Přidat ovládací prvky do listu
 V tomto kroku přidáte pojmenovaný rozsah, objekt seznamu a dvě tlačítka na první list. Nejprve přidejte pojmenovaný rozsah a objekt list z okna **zdroje dat** tak, aby byly automaticky svázány se zdrojem dat. Dále přidejte tlačítka ze **sady nástrojů**.

### <a name="to-add-a-named-range-and-a-list-object"></a>Přidání pojmenovaného rozsahu a objektu seznamu

1. Ověřte, že je sešit **moje Master-Detail.xlsx** otevřený v návrháři sady Visual Studio a zobrazí se **List1** .

2. Otevřete okno **zdroje dat** a rozbalte uzel **objednávky** .

3. Vyberte sloupec **ČísloObjednávky** a potom klikněte na šipku rozevíracího seznamu, která se zobrazí.

4. V rozevíracím seznamu klikněte na **NamedRange** a potom přetáhněte sloupec **ČísloObjednávky** do buňky **a2**.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Ovládací prvek s názvem `OrderIDNamedRange` je vytvořen v buňce **a2**. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> `OrdersBindingSource` <xref:System.Data.DataSet> se do projektu přidají pouze pojmenované, adaptér s tabulkou a instance. Ovládací prvek je vázán na <xref:System.Windows.Forms.BindingSource> , který je zase svázán s <xref:System.Data.DataSet> instancí.

5. Posuňte se dolů za sloupce, které jsou pod tabulkou **Orders** . V dolní části seznamu je tabulka **Podrobnosti objednávky** ; je zde, protože je podřízenou položkou tabulky **Orders** . Vyberte tuto tabulku **podrobností objednávky** , nikoli tu, která je na stejné úrovni jako tabulka **Orders** , a potom klikněte na šipku rozevíracího seznamu, která se zobrazí.

6. V rozevíracím seznamu klikněte na **ListObject** a pak přetáhněte tabulku **OrderDetails** na buňku **a6**.

7. <xref:Microsoft.Office.Tools.Excel.ListObject>Ovládací prvek s názvem **Order_DetailsListObject** je vytvořen v buňce **a6**a svázán s objektem <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>Přidání dvou tlačítek

1. Na kartě **běžné ovládací prvky** **panelu nástrojů**přidejte <xref:System.Windows.Forms.Button> ovládací prvek do buňky **a3** listu.

    Toto tlačítko má název `Button1` .

2. <xref:System.Windows.Forms.Button>Do buňky **B3** listu přidejte jiný ovládací prvek.

    Toto tlačítko má název `Button2` .

   Potom označte datovou sadu, která se uloží do mezipaměti v dokumentu.

## <a name="cache-the-dataset"></a>Ukládat datovou sadu do mezipaměti
 Označte datovou sadu, která se uloží do mezipaměti v dokumentu tak, že ji nastavíte jako veřejnou a nastavíte vlastnost **CacheInDocument** .

### <a name="to-cache-the-dataset"></a>Ukládání datové sady do mezipaměti

1. V části přihrádka součásti vyberte **NorthwindDataSet** .

2. V okně **vlastnosti** změňte vlastnost **modifikátory** na hodnotu **Public**.

    Než bude ukládání do mezipaměti povoleno, musí být datové sady veřejné.

3. Změňte vlastnost **CacheInDocument** na **hodnotu true**.

   Dalším krokem je přidání textu do tlačítek a v C# přidat kód pro zapojení obslužných rutin událostí.

## <a name="initialize-the-controls"></a>Inicializovat ovládací prvky
 Nastavte text tlačítka a přidejte obslužné rutiny události během <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> události.

### <a name="to-initialize-the-data-and-the-controls"></a>Inicializace dat a ovládacích prvků

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **List1. vb** nebo **Sheet1.cs**a pak klikněte na **Zobrazit kód** v místní nabídce.

2. Přidejte následující kód do `Sheet1_Startup` metody pro nastavení textu pro tlačítka.

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. Pouze pro C# přidejte obslužné rutiny události pro události kliknutí na tlačítko do `Sheet1_Startup` metody.

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Přidejte kód, který umožní procházení záznamů.
 Přidejte kód do <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro každé tlačítko pro přesun záznamů.

### <a name="to-scroll-through-the-records"></a>Procházení záznamů

1. Přidejte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost objektu `Button1` a přidejte následující kód pro přesun zpět prostřednictvím záznamů:

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. Přidejte obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button2` a přidejte následující kód, který bude pokračovat v záznamech:

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>Testování aplikace
 Nyní můžete testovat sešit, abyste se ujistili, že se data zobrazují podle očekávání a že je možné použít řešení offline.

### <a name="to-test-the-data-caching"></a>Testování ukládání dat do mezipaměti

1. Stiskněte klávesu **F5**.

2. Ověřte, že pojmenovaný rozsah a objekt list jsou vyplněny daty ze zdroje dat.

3. Posuňte se na některé záznamy kliknutím na tlačítka.

4. Uložte sešit a pak zavřete sešit a Visual Studio.

5. Zakažte připojení k databázi. Odpojte síťový kabel od počítače, pokud je databáze umístěna na serveru, nebo zastavte službu SQL Server, pokud se databáze nachází na vašem vývojovém počítači.

6. Otevřete aplikaci Excel a otevřete **složku moje Master-Detail.xlsx** z adresáře *\Bin* (*\My Master-Detail\bin* v Visual Basic nebo *\My Master-Detail\bin\debug* v jazyce C#).

7. Procházejte částmi záznamů a podívejte se, že list funguje normálně po odpojení.

8. Znovu se připojte k databázi. Připojte počítač k síti znovu, pokud je databáze umístěna na serveru, nebo spusťte službu SQL Server, pokud se databáze nachází na vašem vývojovém počítači.

## <a name="next-steps"></a>Další kroky
 V tomto návodu se dozvíte základy vytvoření vztahu hlavních a podrobných dat na listu a ukládání datové sady do mezipaměti. Tady jsou některé úkoly, které mohou být další:

- Nasaďte řešení. Další informace najdete v tématu [nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md) .

## <a name="see-also"></a>Viz také
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)
- [Data mezipaměti](../vsto/caching-data.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
