---
title: Vytvoření vazby ovládacích prvků WPF k datové službě WCF
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3330c86c84318be68619a8d031a034b33faa7fd1
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305660"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Vytvoření vazby ovládacích prvků WPF k datové službě WCF

V tomto návodu vytvoříte aplikaci WPF, která obsahuje ovládací prvky vázané na data. Ovládací prvky jsou vázány na záznamy o zákaznících, které jsou zapouzdřeny v WCF Data Service. Pokud přidáte tlačítka, která zákazníkům umožňuje zobrazit a aktualizovat záznamy.

Tento návod znázorňuje následující úlohy:

- Vytvoření modelu Entity Data Model, který se vygeneruje z dat z ukázkové databáze AdventureWorksLT.

- Vytvoření datové služby WCF, která zveřejňuje data v modelu Entity Data Model do aplikace WPF.

- Vytvoření sady ovládacích prvků vázaných na data přetažením položek z **zdroje dat** okno do Návrháře WPF.

- Vytváření tlačítek, přejděte vpřed a zpět prostřednictvím záznamy o zákaznících.

- Vytvoření tlačítka, který ukládá data v ovládacích prvcích na službu WCF Data Service a podkladový zdroj dat změny.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio

- Přístup ke spuštěné instanci systému SQL Server nebo SQL Server Express, který má k němu připojené ukázkové databáze AdventureWorksLT. Můžete stáhnout z databáze AdventureWorksLT [webu CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).

Předchozí znalosti následujících konceptů je také užitečné, ale nejsou vyžadovány k dokončení návodu:

- Služby WCF Data Services. Další informace najdete v tématu [přehled](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Modely dat v [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

- Datových modelech entity a ADO.NET Entity Framework. Další informace najdete v tématu [přehled Entity Framework](/dotnet/framework/data/adonet/ef/overview).

- Datové vazby WPF. Další informace najdete v tématu [přehled datové vazby](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Vytvořte projekt služby

Spuštěním tohoto průvodce vytvořením projektu pro službu WCF Data Service:

1. Spusťte sadu Visual Studio.

2. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

3. Rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **webové**.

4. Vyberte **webová aplikace ASP.NET** šablony projektu.

5. V **název** zadejte **AdventureWorksService** a klikněte na tlačítko **OK**.

     Visual Studio vytvoří **AdventureWorksService** projektu.

6. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Default.aspx** a vyberte **odstranit**. Tento soubor není nutné v tomto názorném postupu.

## <a name="create-an-entity-data-model-for-the-service"></a>Vytvoření datového modelu Entity pro službu

Ke zveřejňování dat pro aplikace s použitím službu WCF Data Service, je nutné definovat datový model pro službu. Službu WCF Data Service podporuje dva typy datových modelů: datových modelech Entity a vlastní datové modely, které jsou definovány pomocí běžné language runtime (CLR) objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní. V tomto návodu vytvoříte pro datový model Entity Data Model.

1. Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.

2. V seznamu nainstalovaných šablonách klikněte na tlačítko **Data**a pak vyberte **datový Model Entity ADO.NET** položky projektu.

3. Změňte název na `AdventureWorksModel.edmx`a klikněte na tlačítko **přidat**.

     **Modelu Entity Data Model** otevře se průvodce.

4. Na **výběr obsahu modelu** klikněte na **Generovat z databáze**a klikněte na tlačítko **Další**.

5. Na **vyberte datové připojení** stránky, vyberte jednu z následujících možností:

    - Pokud připojení dat k ukázkové databáze AdventureWorksLT k dispozici v rozevíracím seznamu, vyberte ji.

    - Klikněte na tlačítko **nové připojení**a vytvořte připojení k databázi AdventureWorksLT.

6. Na **vyberte datové připojení** stránky, ujistěte se, že **uložit nastavení připojení v souboru App.Config jako entity** možnost je vybrána a potom klikněte na **Další**.

7. Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky**a pak vyberte **SalesOrderHeader** tabulky.

8. Klikněte na tlačítko **Dokončit**.

## <a name="create-the-service"></a>Vytvoření služby

Vytvoření datové služby WCF ke zveřejňování dat v datovém modelu Entity do aplikace WPF:

1. Na **projektu** nabídce vyberte možnost **přidat novou položku**.

2. V **nainstalované šablony** klikněte na možnost **webové**a pak vyberte **službu WCF Data Service** položky projektu.

3. V **název** zadejte `AdventureWorksService.svc`a klikněte na tlačítko **přidat**.

     Visual Studio přidá `AdventureWorksService.svc` do projektu.

## <a name="configure-the-service"></a>Konfigurace služby

Musíte nakonfigurovat službu pro provoz na modelu Entity Data Model, který jste vytvořili:

1. V `AdventureWorks.svc` soubor kódu, nahraďte **AdventureWorksService** třídy deklarace s následujícím kódem.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Aktualizuje tento kód **AdventureWorksService** , takže je odvozena z třídy <xref:System.Data.Services.DataService%601> , který pracuje `AdventureWorksLTEntities` objektu context – třída v modelu Entity Data Model. Aktualizuje také `InitializeService` metoda můžete umožnit klientům přístup k službě Úplné čtení a zápis do `SalesOrderHeader` entity.

2. Sestavte projekt a ověřte, že sestaví bez chyb.

## <a name="create-the-wpf-client-application"></a>Vytvořit klientskou aplikaci WPF

Chcete-li zobrazit data ze služby WCF Data Service, vytvořte novou aplikaci WPF se zdrojem dat, která je založená na službě. Dále v tomto názorném postupu přidáte ovládací prvky vázané na data do aplikace.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení, klikněte na tlačítko **přidat**a vyberte **nový projekt**.

2. V **nový projekt** dialogového okna, rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **Windows**.

3. Vyberte **aplikace WPF** šablony projektu.

4. V **název** zadejte `AdventureWorksSalesEditor`a klikněte na tlačítko **OK**.

   Visual Studio přidá `AdventureWorksSalesEditor` projektu do řešení.

5. Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

   **Zdroje dat** otevře se okno.

6. V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.

   **Konfigurace zdroje dat** otevře se průvodce.

7. V **zvolte typ zdroje dat** stránky v průvodci vyberte **služby**a potom klikněte na tlačítko **Další**.

8. V **přidat odkaz na službu** dialogové okno, klikněte na tlačítko **Discover**.

   Visual Studio vyhledá aktuální řešení dostupných služeb a přidá `AdventureWorksService.svc` do seznamu dostupných služeb v **služby** pole.

9. V **Namespace** zadejte **AdventureWorksService**.

10. V **služby** klikněte **AdventureWorksService.svc**a potom klikněte na tlačítko **OK**.

    Visual Studio stáhne informace o službě a potom vrátí **konfigurace zdroje dat** průvodce.

11. V **přidat odkaz na službu** klikněte na **Dokončit**.

    Visual Studio přidá uzly, které představují data vrácená služba **zdroje dat** okna.

## <a name="define-the-user-interface"></a>Definování uživatelského rozhraní

Přidání několika tlačítek do okna tak, že upravíte XAML ve WPF designer. Dále v tomto názorném postupu přidáte kód, který umožňuje uživatelům zobrazit a aktualizovat prodejní záznamů pomocí těchto tlačítek.

1. V **Průzkumníka řešení**, dvakrát klikněte na panel **souboru MainWindow.xaml**.

   V okně se otevře v Návrháři WPF.

2. V [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] návrháře, přidejte následující kód mezi `<Grid>` značky:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Sestavte projekt.

## <a name="create-the-data-bound-controls"></a>Vytvoření ovládacích prvků vázaných na data

Vytvořte ovládací prvky zobrazující záznamy o zákaznících přetažením `SalesOrderHeaders` uzlu z **zdroje dat** do okna návrháře.

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

     Visual Studio generuje XAML a kód, který vytvoří sadu ovládacích prvků, které jsou vázány na data v **produktu** tabulky. Další informace o vygenerovaný XAML a kódu, naleznete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. V návrháři, klepněte na textové pole vedle položky **ID zákazníka** popisek.

6. V **vlastnosti** okna, vyberte zaškrtávací políčko vedle položky **IsReadOnly** vlastnost.

7. Nastavte **IsReadOnly** vlastnost pro každý z následujících polí:

    - **Čísla nákupních objednávek**

    - **ID prodejní objednávky**

    - **Číslo prodejní objednávky**

## <a name="load-the-data-from-the-service"></a>Načtení dat ze služby

Pomocí objektu proxy služby můžete načíst prodejní data ze služby. Pak přiřaďte zdroje dat pro vrácená data <xref:System.Windows.Data.CollectionViewSource> v okně WPF.

1. V návrháři, chcete-li vytvořit `Window_Loaded` obslužná rutina události, klikněte dvakrát na text, který čte: **hlavního okna MainWindow**.

2. Obslužná rutina události nahraďte následujícím kódem. Ujistěte se, že nahradíte *localhost* adresy v tomto kódu s adresou místního hostitele ve svém vývojovém počítači.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Procházení záznamů o prodeji

Přidejte kód, který umožňuje uživatelům procházet prodejní záznamy s použitím **\<** a **>** tlačítka.

1. V Návrháři dvakrát klikněte **<** tlačítko na plochu okna.

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `backButton_Click` obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.

2. Přidejte následující kód vygenerovaný `backButton_Click` obslužné rutiny události:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Vraťte se do návrháře a dvakrát klikněte **>** tlačítko.

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `nextButton_Click` obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.

4. Přidejte následující kód vygenerovaný `nextButton_Click` obslužné rutiny události:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Uložit změny do prodeje záznamů

Přidejte kód, který umožňuje uživatelům zobrazit i uložit změny do prodeje záznamů pomocí **uložit změny** tlačítka:

1. V Návrháři dvakrát klikněte **uložit změny** tlačítko.

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `saveButton_Click` obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.

2. Přidejte následující kód, který `saveButton_Click` obslužné rutiny události.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Testování aplikace

Sestavení a spuštění aplikace k ověření, že můžete zobrazit a aktualizovat záznamy o zákaznících:

1. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Ověřte, že řešení sestaví bez chyb.

2. Stisknutím klávesy **Ctrl**+**F5**.

     Spustí aplikace Visual Studio **AdventureWorksService** projektu bez ladění.

3. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **AdventureWorksSalesEditor** projektu.

4. V místní nabídce v části **ladění**, klikněte na tlačítko **zahájit novou instanci**.

     Spuštění aplikace. Ověřte následující:

    - Do textových polí zobrazit různých polí dat. z první prodejní záznam, který má ID prodejní objednávky **71774**.

    - Můžete kliknout **>** nebo **<** tlačítka Procházet další prodejní záznamy.

5. Jedním ze záznamů o prodeji, zadejte nějaký text v **komentář** pole a potom klikněte na tlačítko **uložit změny**.

6. Ukončete aplikaci a pak znovu spusťte aplikaci ze sady Visual Studio.

7. Přejděte na prodejní záznam, který jste změnili a ověřte, že tato změna bude zachován po zavřete a znovu otevřete aplikaci.

8. Ukončete aplikaci.

## <a name="next-steps"></a>Další kroky

Po dokončení tohoto návodu, můžete provádět následující úlohy související:

- Další informace o použití **zdroje dat** okna v sadě Visual Studio k vytvoření vazby WPF ovládací prvky na jiné typy datových zdrojů. Další informace najdete v tématu [WPF vytvoření vazby ovládacích prvků do datové sady](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Další informace o použití **zdroje dat** okna v sadě Visual Studio pro zobrazení souvisejících dat (tj. data ve vztahu nadřazený podřízený) v ovládacích prvcích WPF. Další informace najdete v tématu [návod: zobrazování souvisejících dat v aplikaci WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Vytvoření vazby ovládacích prvků WPF k datové sadě](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Přehled WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Přehled Entity Framework (rozhraní .NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Datové vazby (rozhraní .NET Framework) – přehled](/dotnet/framework/wpf/data/data-binding-overview)