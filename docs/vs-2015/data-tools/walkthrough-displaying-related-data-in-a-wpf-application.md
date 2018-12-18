---
title: 'Návod: Zobrazování souvisejících dat v aplikaci WPF | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1fc90acf94fde0ef815fc3a487412bba8e8257ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913134"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Návod: Zobrazování souvisejících dat v aplikaci WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu vytvoříte aplikaci WPF, která zobrazí data z tabulek databáze, které mají vztah nadřízenosti /. Data zapouzdřena v entitách v modelu Entity Data Model. Nadřazená entita obsahuje přehled informací o sadu objednávky. Tato entita se jednotlivé vlastnosti je vázána na jiný ovládací prvek v aplikaci. Podřízené entity obsahuje podrobnosti pro jednotlivé objednávky. Tuto sadu dat je vázán na <xref:System.Windows.Controls.DataGrid> ovládacího prvku.  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření aplikace WPF a Entity Data Model, který je generován z dat z ukázkové databáze AdventureWorksLT.  
  
- Vytvoření sady ovládacích prvků vázaných na data, které zobrazují přehled informací o sadu objednávky. Vytvoříte přetažením nadřazená entita z ovládacích prvků **zdroje dat** okno **Návrhář WPF**.  
  
- Vytváření <xref:System.Windows.Controls.DataGrid> ovládací prvek, který zobrazí související podrobnosti pro jednotlivé vybrané pořadí. Vytvoříte přetažením podřízené entity z ovládacích prvků **zdroje dat** okna do okna v **Návrhář WPF**.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Přístup ke spuštěné instanci systému SQL Server nebo SQL Server Express, který má k němu připojené ukázkové databáze AdventureWorksLT. Můžete stáhnout z databáze AdventureWorksLT [webových stránkách CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Předchozí znalosti následujících konceptů je také užitečné, ale nejsou vyžadovány k dokončení návodu:  
  
- Datových modelech entity a ADO.NET Entity Framework. Další informace najdete v tématu [přehled Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- Práce s WPF Designer. Další informace najdete v tématu [WPF a Silverlight Návrhář přehled](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Datové vazby WPF. Další informace najdete v tématu [přehled datových vazeb](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Vytvořte nový projekt WPF, chcete-li zobrazit pořadí záznamů.  
  
#### <a name="to-create-a-new-wpf-project"></a>Chcete-li vytvořit nový projekt WPF  
  
1.  Spusťte sadu Visual Studio.  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  Rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **Windows**.  
  
4.  Ujistěte se, že **rozhraní .NET Framework 4** výběru v poli se seznamem v horní části dialogového okna. <xref:System.Windows.Controls.DataGrid> Ovládací prvek, který můžete použít v tomto průvodci je dostupná jenom v rozhraní .NET Framework 4.  
  
5.  Vyberte **aplikace WPF** šablony projektu.  
  
6.  V **název** zadejte `AdventureWorksOrdersViewer`.  
  
7.  Klikněte na tlačítko **OK**.  
  
     Visual Studio vytvoří `AdventureWorksOrdersViewer` projektu.  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>Vytvoření datového modelu Entity pro aplikaci  
 Předtím, než budete moct vytvořit ovládací prvky vázané na data, musíte definovat datový model pro vaši aplikaci a přidejte ji tak **zdroje dat** okna. V tomto návodu je datový model Entity Data Model.  
  
#### <a name="to-create-an-entity-data-model"></a>Chcete-li vytvořit Entity Data Model  
  
1. Na **Data** nabídky, klikněte na tlačítko **přidat nový zdroj dat** otevřít **Průvodce konfigurací zdroje dat**.  
  
2. Na **zvolte typ zdroje dat** klikněte na **databáze**a potom klikněte na tlačítko **Další**.  
  
3. Na **vyberte databázový Model** klikněte na **modelu Entity Data Model**a potom klikněte na tlačítko **Další**.  
  
4. Na **výběr obsahu modelu** klikněte na **Generovat z databáze**a potom klikněte na tlačítko **Další**.  
  
5. Na **vyberte datové připojení** stránce, proveďte jednu z následujících akcí:  
  
   - Pokud připojení dat k ukázkové databáze AdventureWorksLT k dispozici v rozevíracím seznamu, vyberte ji.  
  
      -nebo-  
  
   - Klikněte na tlačítko **nové připojení** a vytvoření připojení k databázi AdventureWorksLT.  
  
     Ujistěte se, že **uložit nastavení připojení v souboru App.Config jako entity** možnost je vybrána a potom klikněte na **Další**.  
  
6. Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky**a pak vyberte následující tabulky:  
  
   -   **Podrobnosti prodejní objednávky**  
  
   -   **SalesOrderHeader**  
  
7. Klikněte na tlačítko **Dokončit**.  
  
8. Sestavte projekt.  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>Vytvoření datově – zobrazované ovládací prvky objednávky  
 Vytvořte ovládací prvky zobrazující pořadí záznamů přetažením `SalesOrderHeaders` entity z **zdroje dat** okno do Návrháře WPF.  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Chcete-li vytvořit ovládací prvky vázané na data, které zobrazují pořadí záznamů  
  
1. V **Průzkumníka řešení**, poklikejte na soubor MainWindow.xaml.  
  
    V okně se otevře v Návrháři WPF.  
  
2. Upravit XAML proto **výška** a **šířka** 800 nastavené vlastnosti  
  
3. V **zdroje dat** okna, klikněte na rozevírací nabídku **SalesOrderHeaders** uzel a vyberte možnost **podrobnosti**.  
  
4. Rozbalte **SalesOrderHeaders** uzlu.  
  
5. Klikněte na rozevírací nabídku vedle **SalesOrderID** a vyberte **– pole se seznamem**.  
  
6. Pro každou z následující podřízené uzly **SalesOrderHeaders** uzel, klikněte na rozevírací nabídku vedle uzlu a vyberte **žádný**:  
  
   - **RevisionNumber**  
  
   - **OnlineOrderFlag**  
  
   - **ShipToAddressID**  
  
   - **BillToAddressID**  
  
   - **CreditCardApprovalCode**  
  
   - **Souhrn**  
  
   - **TaxAmt**  
  
   - **Dopravné**  
  
   - **ROWGUID**  
  
   - **ModifiedDate**  
  
     Tato akce zabraňuje vytváření ovládacích prvků vázaných na data pro tyto uzly v dalším kroku sady Visual Studio. V tomto návodu předpokládá se, že koncový uživatel nemusí zobrazit tato data.  
  
7. Z **zdroje dat** okno, přetáhněte **SalesOrderHeaders** uzlu na okno **Návrhář WPF**.  
  
    Generuje XAML, který vytvoří sadu ovládacích prvků, které jsou vázány na data v sadě Visual Studio **SalesOrderHeaders** entity a kód, který načte data. Další informace o vygenerovaný XAML a kódu, naleznete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8. V Návrháři klikněte vedle pole se seznamem **ID prodejní objednávky** popisek.  
  
9. V **vlastnosti** okna, vyberte zaškrtávací políčko vedle položky **IsReadOnly** vlastnost.  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Vytvoření ovládacího prvku DataGrid, která zobrazuje podrobnosti objednávky  
 Vytvoření <xref:System.Windows.Controls.DataGrid> ovládací prvek, který se zobrazí podrobnosti objednávky přetažením `SalesOrderDetails` entity z **zdroje dat** okno do Návrháře WPF.  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Vytvoření ovládacího prvku DataGrid, který zobrazí podrobnosti objednávky  
  
1. V **zdroje dat** okna, vyhledejte **SalesOrderDetails** uzel, který je podřízeným prvkem **SalesOrderHeaders** uzlu.  
  
   > [!NOTE]
   >  K dispozici je také **SalesOrderDetails** uzel, který je partnerské zařízení **SalesOrderHeaders** uzlu. Ujistěte se, že jste vybrali podřízený uzel **SalesOrderHeaders** uzlu.  
  
2. Rozbalit podřízené **SalesOrderDetails** uzlu.  
  
3. Pro každou z následující podřízené uzly **SalesOrderDetails** uzel, klikněte na rozevírací nabídku vedle uzlu a vyberte **žádný**:  
  
   - **SalesOrderID**  
  
   - **SalesOrderDetailID**  
  
   - **ROWGUID**  
  
   - **ModifiedDate**  
  
     Tato akce zabraňuje včetně těchto dat v sadě Visual Studio <xref:System.Windows.Controls.DataGrid> ovládacího prvku v dalším kroku vytvoříte. V tomto návodu předpokládá se, že koncový uživatel nemusí zobrazit tato data.  
  
4. Z **zdroje dat** okno, přetáhněte podřízený **SalesOrderDetails** uzlu na okno **Návrhář WPF**.  
  
    Sada Visual Studio generuje XAML k definování nového datově <xref:System.Windows.Controls.DataGrid> ovládacího prvku a ovládací prvek se zobrazí v návrháři. Aktualizace nástroje Visual Studio také generované `GetSalesOrderHeadersQuery` metoda ve data v souboru kódu na pozadí **SalesOrderDetails** entity.  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Sestavení a spuštění aplikace k ověření, že zobrazuje pořadí záznamů.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Stisknutím klávesy **F5**.  
  
     Aplikace vytvoří a spustí. Ověřte následující:  
  
    -   **ID prodejní objednávky** zobrazí pole se seznamem **71774**. Toto je první ID objednávky v dané entitě.  
  
    -   Pro jednotlivé objednávky v vyberete **ID prodejní objednávky** – pole se seznamem, pořadí podrobné informace se zobrazí v <xref:System.Windows.Controls.DataGrid>.  
  
2.  Ukončete aplikaci.  
  
## <a name="next-steps"></a>Další kroky  
 Po dokončení tohoto návodu, přečtěte si, jak používat **zdroje dat** okna v sadě Visual Studio k vytvoření vazby WPF ovládací prvky na jiné typy datových zdrojů. Další informace najdete v tématu [WPF vytvoření vazby ovládacích prvků do datové služby WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) a [WPF vytvoření vazby ovládacích prvků do datové sady](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Zobrazení souvisejících dat v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md)