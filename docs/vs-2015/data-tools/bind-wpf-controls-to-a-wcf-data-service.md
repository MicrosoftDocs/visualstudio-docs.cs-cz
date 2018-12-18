---
title: Vytvoření vazby ovládacích prvků WPF k datové služby WCF | Dokumentace Microsoftu
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4f3dbfad8655b8594301b8da7ce1dda050119206
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220375"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Vytvoření vazby ovládacích prvků WPF k datové službě WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V tomto návodu vytvoříte aplikaci WPF, která obsahuje ovládací prvky vázané na data. Ovládací prvky, které jsou vázány na záznamy o zákaznících, které jsou zapouzdřeny v [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]. Pokud přidáte tlačítka, která zákazníkům umožňuje zobrazit a aktualizovat záznamy.  
  
 Tento návod znázorňuje následující úlohy:  
  
- Vytvoření modelu Entity Data Model, který se vygeneruje z dat z ukázkové databáze AdventureWorksLT.  
  
- Vytváření [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] , která zveřejňuje data v modelu Entity Data Model do aplikace WPF.  
  
- Vytvoření sady ovládacích prvků vázaných na data přetažením položek z **zdroje dat** okno do Návrháře WPF.  
  
- Vytváření tlačítek, přejděte vpřed a zpět prostřednictvím záznamy o zákaznících.  
  
- Vytvoření tlačítka, který ukládá data v ovládacích prvcích pro změny [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] a podkladový zdroj dat.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Přístup ke spuštěné instanci systému SQL Server nebo SQL Server Express, který má k němu připojené ukázkové databáze AdventureWorksLT. Můžete stáhnout z databáze AdventureWorksLT [webových stránkách CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Předchozí znalosti následujících konceptů je také užitečné, ale nejsou vyžadovány k dokončení návodu:  
  
- Služby WCF Data Services. Další informace najdete v tématu [přehled](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
- Modely dat v [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)].  
  
- Datových modelech entity a ADO.NET Entity Framework. Další informace najdete v tématu [přehled Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- Práce s WPF designer. Další informace najdete v tématu [WPF a Silverlight Návrhář přehled](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Datové vazby WPF. Další informace najdete v tématu [přehled datových vazeb](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-service-project"></a>Vytvořte projekt služby  
 Spuštěním tohoto průvodce vytvořením projektu [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
#### <a name="to-create-the-service-project"></a>Chcete-li vytvořit projekt služby  
  
1.  Spusťte sadu Visual Studio.  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  Rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **webové**.  
  
4.  Vyberte **webová aplikace ASP.NET** šablony projektu.  
  
5.  V **název** zadejte `AdventureWorksService` a klikněte na tlačítko **OK**.  
  
     Visual Studio vytvoří `AdventureWorksService` projektu.  
  
6.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Default.aspx** a vyberte **odstranit**. Tento soubor není nutné v tomto názorném postupu.  
  
## <a name="create-an-entity-data-model-for-the-service"></a>Vytvoření datového modelu Entity pro službu  
 Ke zveřejňování dat pro aplikace s využitím [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], je nutné definovat datový model pro službu. [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] Podporuje dva typy datových modelů: datových modelech Entity a vlastní datové modely, které jsou definovány pomocí běžné language runtime (CLR) objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní. V tomto návodu vytvoříte pro datový model Entity Data Model.  
  
#### <a name="to-create-an-entity-data-model"></a>Chcete-li vytvořit Entity Data Model  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2.  V seznamu nainstalovaných šablonách klikněte na tlačítko **Data**a pak vyberte **datový Model Entity ADO.NET** položky projektu.  
  
3.  Změňte název na `AdventureWorksModel.edmx`a klikněte na tlačítko **přidat**.  
  
     **Modelu Entity Data Model** otevře se průvodce.  
  
4.  Na **výběr obsahu modelu** klikněte na **Generovat z databáze**a klikněte na tlačítko **Další**.  
  
5.  Na **vyberte datové připojení** stránky, vyberte jednu z následujících možností:  
  
    -   Pokud připojení dat k ukázkové databáze AdventureWorksLT k dispozici v rozevíracím seznamu, vyberte ji.  
  
    -   Klikněte na tlačítko **nové připojení**a vytvořte připojení k databázi AdventureWorksLT.  
  
6.  Na **vyberte datové připojení** stránky, ujistěte se, že **uložit nastavení připojení v souboru App.Config jako entity** možnost je vybrána a potom klikněte na **Další**.  
  
7.  Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky**a pak vyberte **SalesOrderHeader** tabulky.  
  
8.  Klikněte na tlačítko **Dokončit**.  
  
## <a name="create-the-service"></a>Vytvoření služby  
 Vytvoření [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] ke zveřejňování dat v datovém modelu Entity do aplikace WPF.  
  
#### <a name="to-create-the-service"></a>Vytvoření služby  
  
1.  Na **projektu** nabídce vyberte možnost **přidat novou položku**.  
  
2.  V seznamu nainstalovaných šablonách klikněte na tlačítko **webové**a pak vyberte **službu WCF Data Service** položky projektu.  
  
3.  V **název** zadejte `AdventureWorksService.svc`a klikněte na tlačítko **přidat**.  
  
     Visual Studio přidá `AdventureWorksService.svc` do projektu.  
  
## <a name="configure-the-service"></a>Konfigurace služby  
 Musíte nakonfigurovat službu pro provoz na modelu Entity Data Model, který jste vytvořili.  
  
#### <a name="to-configure-the-service"></a>Postup konfigurace služby  
  
1.  V `AdventureWorks.svc` soubor kódu, nahraďte `AdventureWorksService` třídy deklarace s následujícím kódem.  
  
     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]  
  
     Aktualizuje tento kód `AdventureWorksService` , takže je odvozena z třídy <xref:System.Data.Services.DataService%601> , který pracuje `AdventureWorksLTEntities` objektu context – třída v modelu Entity Data Model. Aktualizuje také `InitializeService` metoda můžete umožnit klientům přístup k službě Úplné čtení a zápis do `SalesOrderHeader` entity.  
  
2.  Sestavte projekt a ověřte, že sestaví bez chyb.  
  
## <a name="create-the-wpf-client-application"></a>Vytvořit klientskou aplikaci WPF  
 Pro zobrazení dat z [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], vytvořte novou aplikaci WPF se zdrojem dat, která je založená na službě. Dále v tomto názorném postupu přidáte ovládací prvky vázané na data do aplikace.  
  
#### <a name="to-create-the-wpf-client-application"></a>Vytvoření klientské aplikace WPF  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení, klikněte na tlačítko **přidat**a vyberte **nový projekt**.  
  
2.  V **nový projekt** dialogového okna, rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **Windows**.  
  
3.  Vyberte **aplikace WPF** šablony projektu.  
  
4.  V **název** zadejte `AdventureWorksSalesEditor`a klikněte na tlačítko **OK**.  
  
     Visual Studio přidá `AdventureWorksSalesEditor` projektu do řešení.  
  
5.  Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.  
  
     **Zdroje dat** otevře se okno.  
  
6.  V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.  
  
     **Konfigurace zdroje dat** otevře se průvodce.  
  
7.  V **zvolte typ zdroje dat** stránky v průvodci vyberte **služby**a potom klikněte na tlačítko **Další**.  
  
8.  V **přidat odkaz na službu** dialogové okno, klikněte na tlačítko **Discover**.  
  
     Visual Studio vyhledá aktuální řešení dostupných služeb a přidá `AdventureWorksService.svc` do seznamu dostupných služeb v **služby** pole.  
  
9. V **Namespace** zadejte `AdventureWorksService`.  
  
10. V **služby** klikněte **AdventureWorksService.svc**a potom klikněte na tlačítko **OK**.  
  
     Visual Studio stáhne informace o službě a potom vrátí **konfigurace zdroje dat** průvodce.  
  
11. V **přidat odkaz na službu** klikněte na **Dokončit**.  
  
     Visual Studio přidá uzly, které představují data vrácená služba **zdroje dat** okna.  
  
## <a name="define-the-user-interface-of-the-window"></a>Definování uživatelského rozhraní okna  
 Přidání několika tlačítek do okna tak, že upravíte XAML ve WPF designer. Dále v tomto názorném postupu přidáte kód, který umožňuje uživatelům zobrazit a aktualizovat prodejní záznamů pomocí těchto tlačítek.  
  
#### <a name="to-create-the-window-layout"></a>Chcete-li vytvořit rozložení oken  
  
1.  V **Průzkumníka řešení**, poklikejte na soubor MainWindow.xaml.  
  
     V okně se otevře v Návrháři WPF.  
  
2.  V [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] návrháře, přidejte následující kód mezi `<Grid>` značky:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Sestavte projekt.  
  
## <a name="create-the-data-bound-controls"></a>Vytvoření ovládacích prvků vázaných na data  
 Vytvořte ovládací prvky zobrazující záznamy o zákaznících přetažením `SalesOrderHeaders` uzlu z **zdroje dat** do okna návrháře.  
  
#### <a name="to-create-the-data-bound-controls"></a>Chcete-li vytvořit ovládací prvky vázané daty  
  
1. V **zdroje dat** okna, klikněte na rozevírací nabídku **SalesOrderHeaders** uzel a vyberte možnost **podrobnosti**.  
  
2. Rozbalte **SalesOrderHeaders** uzlu.  
  
3. V tomto příkladu některá pole se nezobrazí, takže klikněte na rozevírací nabídku vedle následujících uzlů a vyberte **žádný**:  
  
   - **CreditCardApprovalCode**  
  
   - **ModifiedDate**  
  
   - **OnlineOrderFlag**  
  
   - **RevisionNumber**  
  
   - **ROWGUID**  
  
     Tato akce zabraňuje vytváření ovládacích prvků vázaných na data pro tyto uzly v dalším kroku sady Visual Studio. V tomto návodu se předpokládá, že koncový uživatel nemusí zobrazit tato data.  
  
4. Z **zdroje dat** okno, přetáhněte **SalesOrderHeaders** uzlů na řádek mřížky pod řádkem, který obsahuje tlačítka.  
  
    Visual Studio generuje XAML a kód, který vytvoří sadu ovládacích prvků, které jsou vázány na data v **produktu** tabulky. Další informace o vygenerovaný XAML a kódu, naleznete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5. V návrháři, klepněte na textové pole vedle položky **ID zákazníka** popisek.  
  
6. V **vlastnosti** okna, vyberte zaškrtávací políčko vedle položky **IsReadOnly** vlastnost.  
  
7. Nastavte **IsReadOnly** vlastnost pro každý z následujících polí:  
  
   -   **Čísla nákupních objednávek**  
  
   -   **ID prodejní objednávky**  
  
   -   **Číslo prodejní objednávky**  
  
## <a name="load-the-data-from-the-service"></a>Načtení dat ze služby  
 Pomocí objektu proxy služby můžete načíst prodejní data ze služby. Pak přiřaďte zdroje dat pro vrácená data <xref:System.Windows.Data.CollectionViewSource> v okně WPF.  
  
#### <a name="to-load-the-data-from-the-service"></a>K načtení dat ze služby  
  
1.  V návrháři, chcete-li vytvořit `Window_Loaded` obslužná rutina události, klikněte dvakrát na text, který čte: **hlavního okna MainWindow**.  
  
2.  Obslužná rutina události nahraďte následujícím kódem. Ujistěte se, že nahradíte *localhost* adresy v tomto kódu s adresou místního hostitele ve svém vývojovém počítači.  
  
     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]  
  
## <a name="navigatesales-records"></a>Navigatesales záznamů  
 Přidejte kód, který umožňuje uživatelům procházet prodejní záznamy s použitím **\<** a **>** tlačítka.  
  
#### <a name="to-enable-users-to-navigate-sales-records"></a>Povolit uživatelům procházet prodejní záznamů  
  
1.  V Návrháři dvakrát klikněte **<** tlačítko na plochu okna.  
  
     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `backButton_Click` obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
2.  Přidejte následující kód vygenerovaný `backButton_Click` obslužné rutiny události:  
  
     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]  
  
3.  Vraťte se do návrháře a dvakrát klikněte **>** tlačítko.  
  
     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `nextButton_Click` obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
4.  Přidejte následující kód vygenerovaný `nextButton_Click` obslužné rutiny události:  
  
     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]  
  
## <a name="saving-changes-to-sales-records"></a>Ukládají se změny záznamů o prodeji  
 Přidejte kód, který umožňuje uživatelům zobrazit i uložit změny do prodeje záznamů pomocí **uložit změny** tlačítko.  
  
#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Chcete-li přidat možnost uložit změny do prodeje záznamů  
  
1.  V Návrháři dvakrát klikněte **uložit změny** tlačítko.  
  
     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `saveButton_Click` obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.  
  
2.  Přidejte následující kód, který `saveButton_Click` obslužné rutiny události.  
  
     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]  
  
## <a name="testing-the-application"></a>Testování aplikace  
 Sestavení a spuštění aplikace k ověření, že můžete zobrazit a aktualizovat záznamy o zákaznících.  
  
#### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Ověřte, že řešení sestaví bez chyb.  
  
2.  Stisknutím klávesy **Ctrl + F5**.  
  
     Spustí aplikace Visual Studio **AdventureWorksService** projektu bez ladění.  
  
3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **AdventureWorksSalesEditor** projektu.  
  
4.  V místní nabídce v části **ladění**, klikněte na tlačítko **zahájit novou instanci**.  
  
     Spuštění aplikace. Ověřte následující:  
  
    -   Do textových polí zobrazit různých polí dat. z první prodejní záznam, který má ID prodejní objednávky **71774**.  
  
    -   Můžete kliknout **>** nebo **<** tlačítka Procházet další prodejní záznamy.  
  
5.  Jedním ze záznamů o prodeji, zadejte nějaký text v **komentář** pole a potom klikněte na tlačítko **uložit změny**.  
  
6.  Ukončete aplikaci a pak znovu spusťte aplikaci ze sady Visual Studio.  
  
7.  Přejděte na prodejní záznam, který jste změnili a ověřte, že tato změna bude zachován po zavřete a znovu otevřete aplikaci.  
  
8.  Ukončete aplikaci.  
  
## <a name="next-steps"></a>Další kroky  
 Po dokončení tohoto návodu, můžete provádět následující úlohy související:  
  
-   Další informace o použití **zdroje dat** okna v sadě Visual Studio k vytvoření vazby WPF ovládací prvky na jiné typy datových zdrojů. Další informace najdete v tématu [WPF vytvoření vazby ovládacích prvků do datové sady](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Další informace o použití **zdroje dat** okna v sadě Visual Studio pro zobrazení souvisejících dat (tj. data ve vztahu nadřazený podřízený) v ovládacích prvcích WPF. Další informace najdete v tématu [návod: zobrazování souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Vytvoření vazby ovládacích prvků WPF k datové sadě](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Přehled](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)   
 [Přehled Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)   
 [WPF a Silverlight Návrhář – přehled](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Přehled datových vazeb](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)

