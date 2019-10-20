---
title: Svázání ovládacích prvků WPF s datovou službou WCF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 421bd778b86aa223e1e7b3a96aa3943a86588174
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662514"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Vytvoření vazby ovládacích prvků WPF k datové službě WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu vytvoříte aplikaci WPF, která obsahuje ovládací prvky vázané na data. Ovládací prvky jsou svázány se záznamy zákazníků, které jsou zapouzdřeny v [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]. Můžete také přidat tlačítka, která mohou zákazníci použít k zobrazení a aktualizaci záznamů.

 Tento návod znázorňuje následující úlohy:

- Vytváření model EDM (Entity Data Model) generovaných z dat v ukázkové databázi AdventureWorksLT.

- Vytvoření [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], které zpřístupňuje data v model EDM (Entity Data Model) aplikace WPF.

- Vytvoření sady ovládacích prvků vázaných na data přetažením položek z okna **zdroje dat** do návrháře WPF.

- Vytváření tlačítek, která pohybují vpřed a zpět záznamy zákazníků.

- Vytvoření tlačítka, které ukládá změny dat v ovládacích prvcích do [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] a podkladového zdroje dat.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Přístup ke spuštěné instanci SQL Server nebo SQL Server Express, ke které je připojena ukázková databáze AdventureWorksLT. Databázi AdventureWorksLT si můžete stáhnout z webu [CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).

  Předchozí znalosti následujících konceptů jsou také užitečné, ale nevyžadují se k dokončení tohoto postupu:

- WCF Data Services. Další informace najdete v tématu [Přehled](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- Datové modely v [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)].

- Entity data Models a ADO.NET Entity Framework. Další informace najdete v tématu [přehled Entity Framework](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Práce s návrhářem WPF. Další informace naleznete v tématu [Přehled Návrháře WPF a Silverlight](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Datová vazba WPF Další informace najdete v tématu [Přehled datových vazeb](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-service-project"></a>Vytvoření projektu služby
 Spusťte tento návod vytvořením projektu pro [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

#### <a name="to-create-the-service-project"></a>Vytvoření projektu služby

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. Rozbalte **položku C# vizuál** nebo **Visual Basic**a pak vyberte možnost **Web**.

4. Vyberte šablonu projektu **webové aplikace ASP.NET** .

5. Do pole **název** zadejte `AdventureWorksService` a klikněte na **OK**.

     Visual Studio vytvoří projekt `AdventureWorksService`.

6. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **Default. aspx** a vyberte **Odstranit**. Tento soubor není v tomto návodu nutný.

## <a name="create-an-entity-data-model-for-the-service"></a>Vytvoření model EDM (Entity Data Model) pro službu
 Aby bylo možné vystavit data pro aplikaci pomocí [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], je nutné pro tuto službu definovat datový model. @No__t_0 podporuje dva typy datových modelů: entity data Models a vlastní datové modely, které jsou definovány pomocí objektů modulu CLR (Common Language Runtime), které implementují rozhraní <xref:System.Linq.IQueryable%601>. V tomto návodu vytvoříte model EDM (Entity Data Model) pro datový model.

#### <a name="to-create-an-entity-data-model"></a>Vytvoření model EDM (Entity Data Model)

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V seznamu nainstalované šablony klikněte na **data**a pak vyberte položku **ADO.NET model EDM (Entity Data Model)** projektu.

3. Změňte název na `AdventureWorksModel.edmx` a klikněte na **Přidat**.

     Otevře se průvodce **model EDM (Entity Data Model)** .

4. Na stránce **Vybrat obsah modelu** klikněte na **Generovat z databáze**a pak klikněte na **Další**.

5. Na stránce **Vyberte datové připojení** vyberte jednu z následujících možností:

    - Pokud je datové připojení k ukázkové databázi AdventureWorksLT dostupné v rozevíracím seznamu, vyberte je.

    - Klikněte na **nové připojení**a vytvořte připojení k databázi AdventureWorksLT.

6. Na stránce **Vyberte datové připojení** se ujistěte, že je vybraná možnost **Uložit nastavení připojení entity v App. config jako** , a pak klikněte na **Další**.

7. Na stránce **Zvolte vaše databázové objekty** rozbalte **tabulky**a potom vyberte tabulku **SalesOrderHeader** .

8. Klikněte na tlačítko **Dokončit**.

## <a name="create-the-service"></a>Vytvoření služby
 Vytvořte [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] k vystavení dat v model EDM (Entity Data Model) do aplikace WPF.

#### <a name="to-create-the-service"></a>Vytvoření služby

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

2. V seznamu nainstalované šablony klikněte na možnost **Web**a poté vyberte položku projektu **WCF Data Service** .

3. Do pole **název** zadejte `AdventureWorksService.svc` a klikněte na **Přidat**.

     Visual Studio přidá `AdventureWorksService.svc` do projektu.

## <a name="configure-the-service"></a>Konfigurace služby
 Službu musíte nakonfigurovat tak, aby fungovala na model EDM (Entity Data Model), kterou jste vytvořili.

#### <a name="to-configure-the-service"></a>Konfigurace služby

1. V souboru kódu `AdventureWorks.svc` nahraďte deklaraci `AdventureWorksService` třídy následujícím kódem.

     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]

     Tento kód aktualizuje třídu `AdventureWorksService` tak, aby byla odvozena z <xref:System.Data.Services.DataService%601>, která ve vaší model EDM (Entity Data Model) pracuje se třídou kontextu objektu `AdventureWorksLTEntities`. Také aktualizuje metodu `InitializeService`, aby klientům umožnil plný přístup pro čtení a zápis k entitě `SalesOrderHeader`.

2. Sestavte projekt a ověřte, zda se jedná o sestavení bez chyb.

## <a name="create-the-wpf-client-application"></a>Vytvoření klientské aplikace WPF
 Chcete-li zobrazit data z [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], vytvořte novou aplikaci WPF se zdrojem dat, který je založen na službě. Později v tomto návodu přidáte ovládací prvky vázané na data do aplikace.

#### <a name="to-create-the-wpf-client-application"></a>Vytvoření klientské aplikace WPF

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení, klikněte na položku **Přidat**a vyberte možnost **Nový projekt**.

2. V dialogovém okně **Nový projekt** rozbalte položku **Visual C#**  nebo **Visual Basic**a pak vyberte možnost **Windows**.

3. Vyberte šablonu projektu **aplikace WPF** .

4. Do pole **název** zadejte `AdventureWorksSalesEditor` a klikněte na **OK**.

     Visual Studio přidá do řešení `AdventureWorksSalesEditor` projekt.

5. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

     Otevře se okno **zdroje dat** .

6. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

     Otevře se průvodce **konfigurací zdroje dat** .

7. Na stránce **Vybrat typ zdroje dat** v průvodci vyberte možnost **Služba**a potom klikněte na tlačítko **Další**.

8. V dialogovém okně **Přidat odkaz na službu** klikněte na možnost **zjistit**.

     Visual Studio hledá v aktuálním řešení dostupné služby a přidá `AdventureWorksService.svc` do seznamu dostupných služeb v poli **služby** .

9. Do pole **obor názvů** zadejte `AdventureWorksService`.

10. V poli **služby** klikněte na **AdventureWorksService. svc**a pak klikněte na **OK**.

     Visual Studio stáhne informace o službě a pak se vrátí do průvodce **konfigurací zdroje dat** .

11. Na stránce **Přidat odkaz na službu** klikněte na **Dokončit**.

     Visual Studio přidá uzly, které reprezentují data vrácená službou do okna **zdroje dat** .

## <a name="define-the-user-interface-of-the-window"></a>Definice uživatelského rozhraní okna
 Do okna přidejte několik tlačítek úpravou XAML v Návrháři WPF. Později v tomto návodu přidáte kód, který umožňuje uživatelům zobrazit a aktualizovat záznamy prodeje pomocí těchto tlačítek.

#### <a name="to-create-the-window-layout"></a>Vytvoření rozložení okna

1. V **Průzkumník řešení**dvakrát klikněte na MainWindow. XAML.

     Okno se otevře v Návrháři WPF.

2. V zobrazení [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] návrháře přidejte následující kód mezi značky `<Grid>`:

    ```
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
 Vytvořte ovládací prvky, které zobrazují záznamy o zákaznících, přetažením uzlu `SalesOrderHeaders` z okna **zdroje dat** do návrháře.

#### <a name="to-create-the-data-bound-controls"></a>Vytvoření ovládacích prvků vázaných na data

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

    Sada Visual Studio generuje XAML a kód, který vytvoří sadu ovládacích prvků, které jsou vázány na data v tabulce **Product** . Další informace o vygenerovaném kódu XAML a kódu naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

5. V návrháři klikněte na textové pole vedle popisku **ID zákazníka** .

6. V okně **vlastnosti** zaškrtněte políčko vedle vlastnosti **IsReadOnly** .

7. Pro každé z následujících textových polí nastavte vlastnost **IsReadOnly** :

   - **Číslo nákupní objednávky**

   - **ID prodejní objednávky**

   - **Číslo prodejní objednávky**

## <a name="load-the-data-from-the-service"></a>Načtení dat ze služby
 Pomocí objektu proxy služby načtěte data z prodeje ze služby. Pak přiřaďte vracená data ke zdroji dat pro <xref:System.Windows.Data.CollectionViewSource> v okně WPF.

#### <a name="to-load-the-data-from-the-service"></a>Načtení dat ze služby

1. V Návrháři vytvořte obslužnou rutinu události `Window_Loaded` dvojitým kliknutím na text, který přečte: **MainWindow**.

2. Proměnnou obslužné rutiny události nahraďte následujícím kódem. Ujistěte se, že v tomto kódu nahradíte adresu *localhost* adresou místního hostitele na vašem vývojovém počítači.

     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]

## <a name="navigatesales-records"></a>Záznamy Navigatesales
 Přidejte kód, který umožňuje uživatelům procházet záznamy prodeje pomocí tlačítek **\<** a **>** .

#### <a name="to-enable-users-to-navigate-sales-records"></a>Umožnění uživatelům přejít k prodejním záznamům

1. V Návrháři poklikejte na tlačítko **<** na povrchu okna.

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `backButton_Click` obslužnou rutinu události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Do generované `backButton_Click` obslužné rutiny události přidejte následující kód:

     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]

3. Vraťte se do návrháře a dvakrát klikněte na tlačítko **>** .

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `nextButton_Click` obslužnou rutinu události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

4. Do generované `nextButton_Click` obslužné rutiny události přidejte následující kód:

     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]

## <a name="saving-changes-to-sales-records"></a>Ukládání změn prodejních záznamů
 Přidejte kód, který umožňuje uživatelům zobrazit a uložit změny v záznamech prodeje pomocí tlačítka **Uložit změny** .

#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Přidání možnosti ukládat změny do záznamů prodeje

1. V Návrháři dvakrát klikněte na tlačítko **Uložit změny** .

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `saveButton_Click` obslužnou rutinu události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Do obslužné rutiny události `saveButton_Click` přidejte následující kód.

     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]

## <a name="testing-the-application"></a>Testování aplikace
 Sestavte a spusťte aplikaci, abyste ověřili, že můžete zobrazit a aktualizovat záznamy zákazníků.

#### <a name="to-test-the-application"></a>Testování aplikace

1. V nabídce **sestavení** klikněte na **Sestavit řešení**. Ověřte, že řešení je sestavení bez chyb.

2. Stiskněte klávesy **CTRL + F5**.

     Visual Studio spustí projekt **AdventureWorksService** bez ladění.

3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **AdventureWorksSalesEditor** .

4. V místní nabídce v části **ladění**klikněte na **spustit novou instanci**.

     Aplikace se spustí. Ověřte následující:

    - Textová pole zobrazují různá pole dat z prvního záznamu prodeje, který má ID prodejní objednávky **71774**.

    - Kliknutím na tlačítko **>** nebo **<** můžete procházet dalšími záznamy prodeje.

5. V jednom ze záznamů prodejů zadejte do pole **Komentář** nějaký text a pak klikněte na **Uložit změny**.

6. Ukončete aplikaci a pak znovu spusťte aplikaci ze sady Visual Studio.

7. Přejděte k záznamu prodeje, který jste změnili, a ověřte, že tato změna bude trvat i po zavření a opětovném otevření aplikace.

8. Zavřete aplikaci.

## <a name="next-steps"></a>Další kroky
 Po dokončení tohoto návodu můžete provádět následující související úlohy:

- Naučte se, jak pomocí okna **zdroje dat** v aplikaci Visual Studio navazovat ovládací prvky WPF na jiné typy zdrojů dat. Další informace naleznete v tématu [Svázání ovládacích prvků WPF s datovou sadou](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Naučte se používat okno **zdroje dat** v aplikaci Visual Studio k zobrazení souvisejících dat (tj. data v relaci nadřazený-podřízený) v ovládacích prvcích WPF. Další informace naleznete v tématu [Návod: zobrazení souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>Viz také
 [Vázání ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [vázání ovládacích prvků WPF na data v nástroji Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [BIND WPF controls to](../data-tools/bind-wpf-controls-to-a-dataset.md) [–](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb) přehled [Entity Framework přehled](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0) [WPF and Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) [data Overview Přehled vazeb](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
