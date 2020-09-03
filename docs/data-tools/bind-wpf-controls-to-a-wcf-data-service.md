---
title: Vytvoření vazby ovládacích prvků WPF k datové službě WCF
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7371e08925ad9227cf15a93a339e6e0ed36d11db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282849"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Vytvoření vazby ovládacích prvků WPF k datové službě WCF

V tomto návodu vytvoříte aplikaci WPF, která obsahuje ovládací prvky vázané na data. Ovládací prvky jsou svázány se záznamy zákazníků, které jsou zapouzdřeny ve službě WCF Data Service. Můžete také přidat tlačítka, která mohou zákazníci použít k zobrazení a aktualizaci záznamů.

Tento návod znázorňuje následující úlohy:

- Vytváření model EDM (Entity Data Model) generovaných z dat v ukázkové databázi AdventureWorksLT.

- Vytvoření datové služby WCF, která zpřístupňuje data v model EDM (Entity Data Model) k aplikaci WPF.

- Vytvoření sady ovládacích prvků vázaných na data přetažením položek z okna **zdroje dat** do návrháře WPF.

- Vytváření tlačítek, která pohybují vpřed a zpět záznamy zákazníků.

- Vytvoření tlačítka, které ukládá změny dat v ovládacích prvcích do datové služby WCF a podkladového zdroje dat.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio

- Přístup ke spuštěné instanci SQL Server nebo SQL Server Express, ke které je připojena ukázková databáze AdventureWorksLT. Databázi AdventureWorksLT si můžete stáhnout z [webu CodePlex](https://archive.codeplex.com/?p=SqlServerSamples).

Předchozí znalosti následujících konceptů jsou také užitečné, ale nevyžadují se k dokončení tohoto postupu:

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Datové modely v [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] .

- Entity data Models a ADO.NET Entity Framework. Další informace najdete v tématu [přehled Entity Framework](/dotnet/framework/data/adonet/ef/overview).

- Datová vazba WPF Další informace najdete v tématu [Přehled datových vazeb](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Vytvoření projektu služby

1. Spusťte tento návod vytvořením projektu **webové aplikace** v jazyce C# nebo Visual Basic ASP.NET. Pojmenujte projekt **AdventureWorksService**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **Default. aspx** a vyberte **Odstranit**. Tento soubor není pro návod nutný.

## <a name="create-an-entity-data-model-for-the-service"></a>Vytvoření model EDM (Entity Data Model) pro službu

Aby bylo možné vystavit data pro aplikaci pomocí datové služby WCF, je nutné pro tuto službu definovat datový model. Datová služba WCF podporuje dva typy datových modelů: datové modely entit a vlastní datové modely, které jsou definovány pomocí objektů CLR (Common Language Runtime), které implementují <xref:System.Linq.IQueryable%601> rozhraní. V tomto návodu vytvoříte model EDM (Entity Data Model) pro datový model.

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V seznamu nainstalované šablony klikněte na **data**a pak vyberte položku **ADO.NET model EDM (Entity Data Model)** projektu.

3. Změňte název na `AdventureWorksModel.edmx` a klikněte na **Přidat**.

     Otevře se průvodce **model EDM (Entity Data Model)** .

4. Na stránce **Vybrat obsah modelu** klikněte na **Generovat z databáze**a pak klikněte na **Další**.

5. Na stránce **Vyberte datové připojení** vyberte jednu z následujících možností:

    - Pokud je datové připojení k ukázkové databázi AdventureWorksLT dostupné v rozevíracím seznamu, vyberte je.

    - Klikněte na **nové připojení**a vytvořte připojení k databázi AdventureWorksLT.

6. Na stránce **Vyberte datové připojení** se ujistěte, že je vybraná možnost **Uložit nastavení připojení entity v App.Config jako** , a pak klikněte na **Další**.

7. Na stránce **Zvolte vaše databázové objekty** rozbalte **tabulky**a potom vyberte tabulku **SalesOrderHeader** .

8. Klikněte na **Finish** (Dokončit).

## <a name="create-the-service"></a>Vytvoření služby

Vytvoření datové služby WCF pro zpřístupnění dat v model EDM (Entity Data Model) k aplikaci WPF:

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

2. V seznamu **Nainstalované šablony** klikněte na možnost **Web**a poté vyberte položku projektu **WCF Data Service** .

3. Do pole **název** zadejte `AdventureWorksService.svc` a klikněte na **Přidat**.

     Visual Studio přidá `AdventureWorksService.svc` do projektu.

## <a name="configure-the-service"></a>Konfigurace služby

Službu musíte nakonfigurovat tak, aby fungovala s model EDM (Entity Data Model), kterou jste vytvořili:

1. V `AdventureWorks.svc` souboru kódu nahraďte deklaraci třídy **AdventureWorksService** následujícím kódem.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Tento kód aktualizuje třídu **AdventureWorksService** tak, aby byla odvozena z typu <xref:System.Data.Services.DataService%601> , který pracuje ve `AdventureWorksLTEntities` třídě kontextu objektu v model EDM (Entity Data Model). Také aktualizuje `InitializeService` metodu tak, aby umožňovala klientům úplný přístup pro čtení a zápis k `SalesOrderHeader` entitě.

2. Sestavte projekt a ověřte, zda se jedná o sestavení bez chyb.

## <a name="create-the-wpf-client-application"></a>Vytvoření klientské aplikace WPF

Chcete-li zobrazit data z datové služby WCF, vytvořte novou aplikaci WPF se zdrojem dat, který je založen na službě. Později v tomto návodu přidáte ovládací prvky vázané na data do aplikace.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení, klikněte na položku **Přidat**a vyberte možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte položku **Visual C#** nebo **Visual Basic**a pak vyberte možnost **Windows**.

3. Vyberte šablonu projektu **aplikace WPF** .

4. Do pole **název** zadejte `AdventureWorksSalesEditor` a klikněte na **OK**.

   Visual Studio přidá `AdventureWorksSalesEditor` projekt do řešení.

5. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

   Otevře se okno **zdroje dat** .

6. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

   Otevře se průvodce **konfigurací zdroje dat** .

7. Na stránce **Vybrat typ zdroje dat** v průvodci vyberte možnost **Služba**a potom klikněte na tlačítko **Další**.

8. V dialogovém okně **Přidat odkaz na službu** klikněte na možnost **zjistit**.

   Visual Studio hledá v aktuálním řešení dostupné služby a přidá je `AdventureWorksService.svc` do seznamu dostupných služeb v poli **služby** .

9. Do pole **obor názvů** zadejte **AdventureWorksService**.

10. V poli **služby** klikněte na **AdventureWorksService. svc**a pak klikněte na **OK**.

    Visual Studio stáhne informace o službě a pak se vrátí do průvodce **konfigurací zdroje dat** .

11. Na stránce **Přidat odkaz na službu** klikněte na **Dokončit**.

    Visual Studio přidá uzly, které reprezentují data vrácená službou do okna **zdroje dat** .

## <a name="define-the-user-interface"></a>Definování uživatelského rozhraní

Do okna přidejte několik tlačítek úpravou XAML v Návrháři WPF. Později v tomto návodu přidáte kód, který umožňuje uživatelům zobrazit a aktualizovat záznamy prodeje pomocí těchto tlačítek.

1. V **Průzkumník řešení**dvakrát klikněte na **MainWindow. XAML**.

   Okno se otevře v Návrháři WPF.

2. V [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] zobrazení návrháře přidejte následující kód mezi `<Grid>` značky:

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

Vytvořte ovládací prvky, které zobrazují záznamy o zákaznících přetažením `SalesOrderHeaders` uzlu z okna **zdroje dat** do návrháře.

1. V okně **zdroje dat** klikněte na rozevírací nabídku uzlu **SalesOrderHeaders** a vyberte **Podrobnosti**.

2. Rozbalte uzel **SalesOrderHeaders** .

3. V tomto příkladu se některá pole nezobrazují, takže klikněte na rozevírací nabídku vedle následujících uzlů a vyberte **žádná**:

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **ROWGUID**

    Tato akce zabrání aplikaci Visual Studio v vytváření ovládacích prvků vázaných na data pro tyto uzly v dalším kroku. Pro účely tohoto Názorného postupu Předpokládejme, že koncový uživatel nemusí tato data zobrazovat.

4. V okně **zdroje dat** Přetáhněte uzel **SalesOrderHeaders** do řádku mřížky pod řádkem, který obsahuje tlačítka.

     Sada Visual Studio generuje XAML a kód, který vytvoří sadu ovládacích prvků, které jsou vázány na data v tabulce **Product** . Další informace o vygenerovaném kódu XAML a kódu naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. V návrháři klikněte na textové pole vedle popisku **ID zákazníka** .

6. V okně **vlastnosti** zaškrtněte políčko vedle vlastnosti **IsReadOnly** .

7. Pro každé z následujících textových polí nastavte vlastnost **IsReadOnly** :

    - **Číslo nákupní objednávky**

    - **ID prodejní objednávky**

    - **Číslo nákupní objednávky**

## <a name="load-the-data-from-the-service"></a>Načtení dat ze služby

Pomocí objektu proxy služby načtěte data z prodeje ze služby. Pak přiřaďte vrácená data ke zdroji dat <xref:System.Windows.Data.CollectionViewSource> v okně WPF.

1. V Návrháři vytvořte `Window_Loaded` obslužnou rutinu události dvojitým kliknutím na text, který přečte: **MainWindow**.

2. Proměnnou obslužné rutiny události nahraďte následujícím kódem. Ujistěte se, že v tomto kódu nahradíte adresu *localhost* adresou místního hostitele na vašem vývojovém počítači.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Přejít k prodejním záznamům

Přidejte kód, který umožňuje uživatelům procházet záznamy prodeje pomocí **\<** and **>** tlačítek.

1. V Návrháři poklikejte na **<** tlačítko na ploše okna.

     Visual Studio otevře soubor kódu na pozadí a vytvoří `backButton_Click` pro událost novou obslužnou rutinu události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Do generované `backButton_Click` obslužné rutiny události přidejte následující kód:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Vraťte se do návrháře a dvakrát klikněte na **>** tlačítko.

     Visual Studio otevře soubor kódu na pozadí a vytvoří `nextButton_Click` pro událost novou obslužnou rutinu události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

4. Do generované `nextButton_Click` obslužné rutiny události přidejte následující kód:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Uložení změn prodejních záznamů

Přidejte kód, který umožňuje uživatelům zobrazit a uložit změny v záznamech prodeje pomocí tlačítka **Uložit změny** :

1. V Návrháři dvakrát klikněte na tlačítko **Uložit změny** .

     Visual Studio otevře soubor kódu na pozadí a vytvoří `saveButton_Click` pro událost novou obslužnou rutinu události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Přidejte následující kód do `saveButton_Click` obslužné rutiny události.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Testování aplikace

Sestavte a spusťte aplikaci, abyste ověřili, že můžete zobrazit a aktualizovat záznamy zákazníků:

1. V nabídce **sestavení** klikněte na **Sestavit řešení**. Ověřte, že řešení je sestavení bez chyb.

2. Stiskněte klávesu **CTRL** + **F5**.

     Visual Studio spustí projekt **AdventureWorksService** bez ladění.

3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **AdventureWorksSalesEditor** .

4. V nabídce kliknutím pravým tlačítkem (kontextová nabídka) v části **ladění**klikněte na **spustit novou instanci**.

     Aplikace se spustí. Zkontrolujte:

    - Textová pole zobrazují různá pole dat z prvního záznamu prodeje, který má ID prodejní objednávky **71774**.

    - Kliknutím na **>** tlačítka nebo můžete **<** Procházet dalšími záznamy prodeje.

5. V jednom ze záznamů prodejů zadejte do pole **Komentář** nějaký text a pak klikněte na **Uložit změny**.

6. Ukončete aplikaci a pak znovu spusťte aplikaci ze sady Visual Studio.

7. Přejděte k záznamu prodeje, který jste změnili, a ověřte, že tato změna bude trvat i po zavření a opětovném otevření aplikace.

8. Zavřete aplikaci.

## <a name="next-steps"></a>Další kroky

Po dokončení tohoto návodu můžete provádět následující související úlohy:

- Naučte se, jak pomocí okna **zdroje dat** v aplikaci Visual Studio navazovat ovládací prvky WPF na jiné typy zdrojů dat. Další informace naleznete v tématu [Svázání ovládacích prvků WPF s datovou sadou](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Naučte se používat okno **zdroje dat** v aplikaci Visual Studio k zobrazení souvisejících dat (tj. data v relaci nadřazený-podřízený) v ovládacích prvcích WPF. Další informace naleznete v tématu [Návod: zobrazení souvisejících dat v aplikaci WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Viz také

- [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Svázání ovládacích prvků WPF s datovou sadou](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [Přehled služby WCF (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Přehled Entity Framework (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Přehled datové vazby (.NET Framework)](/dotnet/desktop-wpf/data/data-binding-overview)
