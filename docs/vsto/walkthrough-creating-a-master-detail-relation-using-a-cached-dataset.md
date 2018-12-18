---
title: 'Návod: Vytvoření hlavního podrobný vztah pomocí datové sady v mezipaměti'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d877eae119c922939ea61007a845e5bd7049076
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933154"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Návod: Vytvoření hlavního podrobný vztah pomocí datové sady v mezipaměti
  Tento názorný postup ukazuje vytvoření vztah záznamů master/detail v listu a dat do mezipaměti, takže toto řešení je možné do offline režimu.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 V tomto návodu se dozvíte, jak:  
  
-   Přidání ovládacích prvků na list.  
  
-   Nastavení datové sady do mezipaměti v listu.  
  
-   Přidejte kód pro povolení přecházení mezi záznamy.  
  
-   Otestování vašeho projektu.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] nebo [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Přístup k ukázkové databázi Northwind SQL Server. Databáze může být na vašem vývojovém počítači nebo na serveru.  
  
-   Oprávnění ke čtení a zápis do databáze serveru SQL Server.  
  
## <a name="create-a-new-project"></a>Vytvoření nového projektu  
 V tomto kroku vytvoříte projekt sešitu aplikace Excel.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1. Vytvořte projekt sešitu aplikace Excel s názvem **Moje hlavní-podrobnosti**, pomocí jazyka Visual Basic nebo C#. Ujistěte se, že **vytvoříte nový textový dokument** zaškrtnuto. Další informace najdete v tématu [postupy: vytváření projektů pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio otevře nový sešit aplikace Excel v návrháři a přidá **Moje hlavní-podrobnosti** projektu **Průzkumníka řešení**.  
  
## <a name="create-the-data-source"></a>Vytvoření zdroje dat  
 Použití **zdroje dat** okno pro přidání typové datové sady do projektu.  
  
### <a name="to-create-the-data-source"></a>Vytvoření zdroje dat  
  
1. Pokud **zdroje dat** okno se nezobrazuje, zobrazit ho tím, na panelu nabídek, výběrem **zobrazení** > **ostatní Windows**  >   **Zdroje dat**.  
  
2. Zvolte **přidat nový zdroj dat** spustit **Průvodce konfigurací zdroje dat**.  
  
3. Vyberte **databáze** a potom klikněte na tlačítko **Další**.  
  
4. Vyberte datové připojení k ukázkové databázi Northwind systému SQL Server, nebo přidejte nové připojení s použitím **nové připojení** tlačítko.  
  
5. Po výběru nebo vytvoření připojení, klikněte na tlačítko **Další**.  
  
6. Uložit připojení, pokud je zaškrtnuto a pak klikněte na tlačítko Vymazat **Další**.  
  
7. Rozbalte **tabulky** uzlu **databázové objekty** okna.  
  
8. Vyberte **objednávky** tabulky a **OrderDetails** tabulky.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
   Průvodce přidá do obou tabulek **zdroje dat** okna. Také přidá typové datové sady do projektu, který se zobrazuje **Průzkumníka řešení**.  
  
## <a name="add-controls-to-the-worksheet"></a>Přidání ovládacích prvků na list  
 V tomto kroku přidáte pojmenované oblasti, objekt seznamu a dvě tlačítka na první sešit. Nejprve přidejte pojmenovaném rozsahu a objekt v seznamu **zdroje dat** okna tak, aby se automaticky vázán na zdroj dat. V dalším kroku přidejte tlačítka z **nástrojů**.  
  
### <a name="to-add-a-named-range-and-a-list-object"></a>Chcete-li přidat pojmenované oblasti a objekt seznamu  
  
1.  Ověřte, že **Moje hlavní Detail.xlsx** sešitu je otevřen v návrháři aplikace Visual Studio s **List1** zobrazí.  
  
2.  Otevřít **zdroje dat** okno a rozbalte **objednávky** uzlu.  
  
3.  Vyberte **OrderID** sloupce a potom klikněte na šipku rozevíracího seznamu, který se zobrazí.  
  
4.  Klikněte na tlačítko **NamedRange** v rozevíracím seznamu a pak přetáhněte **OrderID** sloupce do buňky **A2**.  
  
     A <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `OrderIDNamedRange` se vytvoří v buňce **A2**. Ve stejnou dobu <xref:System.Windows.Forms.BindingSource> s názvem `OrdersBindingSource`, tabulka adaptéru a <xref:System.Data.DataSet> instance jsou přidány do projektu. Ovládací prvek vázaný <xref:System.Windows.Forms.BindingSource>, která je dále vázán na <xref:System.Data.DataSet> instance.  
  
5.  Posuňte se dolů sloupce, které jsou pod správou **objednávky** tabulky. V dolní části seznamu je **OrderDetails** tabulky; je zde, protože je podřízeným prvkem **objednávky** tabulky. Tuto možnost vyberte, **OrderDetails** tabulky není ten, který je na stejné úrovni jako **objednávky** tabulku a pak klikněte na šipku rozevíracího seznamu, který se zobrazí.  
  
6.  Klikněte na tlačítko **ListObject** v rozevíracím seznamu a pak přetáhněte **OrderDetails** tabulky do buňky **A6**.  
  
7.  A <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek s názvem **Order_DetailsListObject** se vytvoří v buňce **A6**a vázán <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-two-buttons"></a>Chcete-li přidat dvě tlačítka  
  
1. Z **běžné ovládací prvky** karty **nástrojů**, přidat <xref:System.Windows.Forms.Button> ovládacího prvku do buňky **A3** listu.  
  
    Toto tlačítko nazývalo `Button1`.  
  
2. Přidejte další <xref:System.Windows.Forms.Button> ovládacího prvku do buňky **B3** listu.  
  
    Toto tlačítko nazývalo `Button2`.  
  
   V dalším kroku označte datovou sadu do mezipaměti v dokumentu.  
  
## <a name="cache-the-dataset"></a>Datovou sadu do mezipaměti  
 Označit datovou sadu do mezipaměti v dokumentu tak, že datovou sadu, veřejné a nastavení **CacheInDocument** vlastnost.  
  
### <a name="to-cache-the-dataset"></a>Chcete-li datovou sadu do mezipaměti  
  
1. Vyberte **NorthwindDataSet** v panelu komponent.  
  
2. V **vlastnosti** okno Změnit **modifikátory** vlastnost **veřejné**.  
  
    Předtím, než je povoleno ukládání do mezipaměti, musí být veřejné datové sady.  
  
3. Změnit **CacheInDocument** vlastnost **True**.  
  
   Dalším krokem je přidání textu tlačítka a v jazyce C# přidejte kód k připojení obslužných rutin událostí.  
  
## <a name="initialize-the-controls"></a>Inicializovat ovládací prvky  
 Nastavení textu tlačítka a přidejte obslužné rutiny událostí během <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> událostí.  
  
### <a name="to-initialize-the-data-and-the-controls"></a>Inicializace dat a ovládací prvky  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Sheet1.vb** nebo **Sheet1.cs**a potom klikněte na tlačítko **zobrazit kód** v místní nabídce.  
  
2.  Přidejte následující kód, který `Sheet1_Startup` metody nastavte text tlačítka.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Jenom v C#, přidejte obslužné rutiny události pro tlačítko klikněte na události `Sheet1_Startup` metody.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Přidejte kód umožňující posouvání záznamů  
 Přidejte kód, který <xref:System.Windows.Forms.Control.Click> obslužná rutina události z každé tlačítko pro procházení záznamů.  
  
### <a name="to-scroll-through-the-records"></a>Procházet záznamy  
  
1.  Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button1`a přidejte následující kód pro přechod zpět každý pomocí záznamů:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.Control.Click> událost `Button2`a přidejte následující kód, který postupoval záznamy:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="test-the-application"></a>Testování aplikace  
 Nyní můžete otestovat sešitu, abyste měli jistotu, že se zobrazí data podle očekávání a, které můžete použít řešení v režimu offline.  
  
### <a name="to-test-the-data-caching"></a>K otestování dat, ukládání do mezipaměti  
  
1.  Stisknutím klávesy **F5**.  
  
2.  Ověřte, že pojmenované oblasti a objekt seznamu jsou vyplněny hodnotou data ze zdroje dat.  
  
3.  Projděte si některé záznamy pomocí tlačítek.  
  
4.  Uložte sešit a poté zavřete sešit a sady Visual Studio.  
  
5.  Zakážete připojení k databázi. Odpojit síťový kabel z vašeho počítače, pokud se databáze nachází na serveru nebo zastavit službu systému SQL Server, pokud se databáze nachází na vašem vývojovém počítači.  
  
6.  Otevřete aplikaci Excel a pak otevřete **Moje hlavní Detail.xlsx** z *\bin* adresáře (*\My Master-Detail\bin* v jazyce Visual Basic nebo *\My Master-Detail\bin\ ladění* v jazyce C#).  
  
7.  Projděte si některé záznamy zobrazit, že do listu funguje normálně při odpojení.  
  
8.  Znovu připojte k databázi. Připojení počítače k síti znovu Pokud se databáze nachází na serveru nebo spustit službu systému SQL Server, pokud se databáze nachází na vašem vývojovém počítači.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod ukazuje základy vytváření relací dat záznamů master/detail v listu a ukládání do mezipaměti datové sady. Tady jsou některé úlohy, které by mohl pocházet Další:  
  
-   Nasazení řešení. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Viz také:  
 [Vytvoření vazby dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Data v řešeních pro systém Office](../vsto/data-in-office-solutions.md)   
 [Data v mezipaměti](../vsto/caching-data.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)  
  
  