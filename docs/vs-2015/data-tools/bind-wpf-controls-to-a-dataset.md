---
title: Svázání ovládacích prvků WPF s datovou sadou | Microsoft Docs
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
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 937e28e923c26a72940b0181da16cf34199bb9aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852160"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Vytvoření vazby ovládacích prvků WPF k datové sadě
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu vytvoříte aplikaci WPF, která obsahuje ovládací prvky vázané na data. Ovládací prvky jsou vázány na záznamy produktu, které jsou zapouzdřeny v datové sadě. Přidáte také tlačítka pro procházení produktů a uložení změn záznamů produktu.

 Tento návod znázorňuje následující úlohy:

- Vytvoření aplikace WPF a datové sady, která je generována z dat v ukázkové databázi AdventureWorksLT.

- Vytvoření sady ovládacích prvků vázaných na data přetažením tabulky dat z okna **zdroje dat** do okna v Návrháři WPF.

- Vytváření tlačítek, která pohybují vpřed a zpět záznamy produktů.

- Vytvořením tlačítka, které ukládá změny provedené uživateli na záznamy produktu, do tabulky dat a podkladového zdroje dat.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Předpoklady
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Přístup ke spuštěné instanci SQL Server nebo SQL Server Express, ke které je připojena ukázková databáze AdventureWorksLT. Databázi AdventureWorksLT si můžete stáhnout z webu [CodePlex](https://codeplex.com/SqlServerSamples).

  Předchozí znalosti následujících konceptů jsou také užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Datové sady a objekty TableAdapter. Další informace najdete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- Práce s návrhářem WPF. Další informace naleznete v tématu [Přehled Návrháře WPF a Silverlight](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Datová vazba WPF Další informace najdete v tématu [Přehled datových vazeb](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-project"></a>Vytvoření projektu
 Vytvořte nový projekt WPF. Projekt zobrazí záznamy produktů.

#### <a name="to-create-the-project"></a>Vytvoření projektu

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. Rozbalte položku **Visual Basic** nebo **Visual C#** a pak vyberte možnost **Windows**.

4. Vyberte šablonu projektu **aplikace WPF** .

5. Do pole **název** zadejte `AdventureWorksProductsEditor` a klikněte na **OK**.

     Visual Studio vytvoří `AdventureWorksProductsEditor` projekt.

## <a name="create-a-dataset-for-the-application"></a>Vytvoření datové sady pro aplikaci
 Předtím, než můžete vytvořit ovládací prvky vázané na data, je nutné pro svou aplikaci definovat datový model a přidat je do okna **zdroje dat** . V tomto návodu vytvoříte datovou sadu, která bude použita jako datový model.

#### <a name="to-create-a-dataset"></a>Vytvoření datové sady

1. V nabídce **data** klikněte na možnost **Zobrazit zdroje dat**.

     Otevře se okno **zdroje dat** .

2. V okně **zdroje dat** klikněte na tlačítko **Přidat nový zdroj dat**.

     Otevře se průvodce **konfigurací zdroje dat** .

3. Na stránce **Zvolte typ zdroje dat** vyberte možnost **databáze**a poté klikněte na tlačítko **Další**.

4. Na stránce **Vyberte databázový model** vyberte **datová sada**a potom klikněte na **Další**.

5. Na stránce **Vyberte datové připojení** vyberte jednu z následujících možností:

    - Pokud je v rozevíracím seznamu k dispozici datové připojení k ukázkové databázi AdventureWorksLT, vyberte je a klikněte na tlačítko **Další**.

    - Klikněte na **nové připojení**a vytvořte připojení k databázi AdventureWorksLT.

6. Na stránce **Uložit připojovací řetězec do souboru konfigurace aplikace** zaškrtněte políčko **Ano, uložit připojení jako** zaškrtávací políčko a potom klikněte na tlačítko **Další**.

7. Na stránce **Zvolte vaše databázové objekty** rozbalte **tabulky**a pak vyberte tabulku **Product (tabulky SalesLT)** .

8. Klikněte na **Finish** (Dokončit).

     Visual Studio přidá do projektu nový soubor AdventureWorksLTDataSet. xsd a přidá odpovídající položku **AdventureWorksLTDataSet** do okna **zdroje dat** . Soubor AdventureWorksLTDataSet. xsd definuje typovou datovou sadu s názvem `AdventureWorksLTDataSet` a TableAdapter s názvem `ProductTableAdapter` . Později v tomto návodu použijete `ProductTableAdapter` k vyplnění datové sady daty a uložíte změny zpátky do databáze.

9. Sestavte projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Upravit výchozí metodu Fill pro TableAdapter
 Chcete-li datovou sadu vyplnit daty, použijte `Fill` metodu `ProductTableAdapter` . Ve výchozím nastavení `Fill` Metoda vyplní do `ProductDataTable` `AdventureWorksLTDataSet` všechny řádky dat z tabulky Product. Tuto metodu lze upravit tak, aby vracela pouze podmnožinu řádků. Pro tento návod upravte `Fill` metodu tak, aby vracela pouze řádky pro produkty, které mají fotografie.

#### <a name="to-load-product-rows-that-have-photos"></a>Načtení řádků produktu, které mají fotky

1. V **Průzkumník řešení**dvakrát klikněte na soubor AdventureWorksLTDataSet. xsd.

     Otevře se Návrhář DataSet.

2. V návrháři klikněte pravým tlačítkem myši na příkaz **Fill, GetData ()** a vyberte možnost **Konfigurovat**.

     Otevře se průvodce **konfigurací TableAdapter** .

3. Na stránce **Zadejte příkaz SQL** přidejte následující klauzuli WHERE za `SELECT` příkaz v textovém poli.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Klikněte na **Finish** (Dokončit).

## <a name="define-the-user-interface"></a>Definování uživatelského rozhraní
 Do okna přidejte několik tlačítek úpravou XAML v Návrháři WPF. Později v tomto návodu přidáte kód, který umožňuje uživatelům procházet a ukládat změny záznamů produktů pomocí těchto tlačítek.

#### <a name="to-define-the-user-interface-of-the-window"></a>Definování uživatelského rozhraní okna

1. V **Průzkumník řešení**dvakrát klikněte na MainWindow. XAML.

     Okno se otevře v Návrháři WPF.

2. V [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] zobrazení návrháře přidejte následující kód mezi `<Grid>` značky:

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. Sestavte projekt.

## <a name="createdata-bound-controls"></a>Ovládací prvky vázané na Createdata
 Vytvořte ovládací prvky, které zobrazují záznamy o zákaznících, přetažením `Product` tabulky z okna **zdroje dat** do návrháře WPF.

#### <a name="to-create-data-bound-controls"></a>Vytvoření ovládacích prvků vázaných na data

1. V okně **zdroje dat** klikněte na rozevírací nabídku uzlu **produkt** a vyberte **Podrobnosti**.

2. Rozbalte uzel **produkt** .

3. V tomto příkladu se některá pole nezobrazují, takže klikněte na rozevírací nabídku vedle následujících uzlů a vyberte **žádná**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - ROWGUID

    - ModifiedDate

4. Klikněte na rozevírací nabídku vedle uzlu **ThumbNailPhoto** a vyberte **Obrázek**.

    > [!NOTE]
    > Ve výchozím nastavení mají položky v okně **zdroje dat** , které reprezentují obrázky výchozí ovládací prvek nastaven na **možnost žádné**. Je to proto, že obrázky jsou uloženy jako pole bajtů v databázích a pole bajtů může obsahovat cokoli od jednoduchého pole bajtů ke spustitelnému souboru velké aplikace.

5. V okně **zdroje dat** Přetáhněte uzel **produkt** do řádku mřížky pod řádkem, který obsahuje tlačítka.

     Sada Visual Studio generuje kód XAML, který definuje sadu ovládacích prvků, které jsou vázány na data v tabulce **Products** . Také generuje kód, který načte data. Další informace o vygenerovaném kódu XAML a kódu naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. V návrháři klikněte na textové pole vedle popisku **ID produktu** .

7. V okně **vlastnosti** zaškrtněte políčko vedle vlastnosti **IsReadOnly** .

## <a name="navigating-product-records"></a>Navigace v záznamech produktů
 Přidejte kód, který umožňuje uživatelům procházet záznamy produktů pomocí **\<** and **>** tlačítek.

#### <a name="to-enable-users-to-navigate-product-records"></a>Umožnění uživatelům navigovat záznamy produktů

1. V Návrháři poklikejte na **<** tlačítko na ploše okna.

     Visual Studio otevře soubor kódu na pozadí a vytvoří `backButton_Click` pro událost novou obslužnou rutinu události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Upravte `Window_Loaded` obslužnou rutinu události, a to tak, aby byla `ProductViewSource` `AdventureWorksLTDataSet` `AdventureWorksLTDataSetProductTableAdapter` mimo metodu a přístupná k celému formuláři. Deklarujete pouze ty, které mají být z formuláře globální, a přiřaďte je v rámci `Window_Loaded` obslužné rutiny události podobné následujícímu:

     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]

3. Do `backButton_Click` obslužné rutiny události přidejte následující kód:

     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]

4. Vraťte se do návrháře a dvakrát klikněte na **>** tlačítko.

5. Do `nextButton_Click` obslužné rutiny události přidejte následující kód:

     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]

## <a name="savechanges-to-product-records"></a>SaveChanges na záznamy produktů
 Přidejte kód, který umožňuje uživatelům ukládat změny do záznamů produktů pomocí tlačítka **Uložit změny** .

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Přidání možnosti ukládat změny do záznamů produktů

1. V Návrháři dvakrát klikněte na tlačítko **Uložit změny** .

     Visual Studio otevře soubor kódu na pozadí a vytvoří `saveButton_Click` pro událost novou obslužnou rutinu události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Do `saveButton_Click` obslužné rutiny události přidejte následující kód:

     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]

    > [!NOTE]
    > Tento příklad používá `Save` metodu `TableAdapter` pro uložení změn. To je vhodné v tomto návodu, protože se mění jenom jedna datová tabulka. Pokud potřebujete uložit změny do více tabulek dat, můžete alternativně použít `UpdateAll` metodu `TableAdapterManager` , kterou sada Visual Studio generuje s datovou sadou. Další informace najdete v tématu [TableAdapterManager Overview](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

## <a name="test-the-application"></a>Testování aplikace
 Sestavte a spusťte aplikaci. Ověřte, zda můžete zobrazit a aktualizovat záznamy produktů.

#### <a name="to-test-the-application"></a>Testování aplikace

1. Stiskněte klávesu **F5**.

     Aplikace se vytvoří a spustí. Zkontrolujte:

    - Textová pole zobrazují data z prvního záznamu produktu, který obsahuje fotografii. V tomto produktu je produkt s ID 713 a názvem **dlouhé logo Jersey, S**.

    - Kliknutím na **>** tlačítka nebo můžete procházet **<** dalšími záznamy produktů.

2. V jednom ze záznamů produktu změňte hodnotu **velikosti** a pak klikněte na **Uložit změny**.

3. Ukončete aplikaci a pak restartujte aplikaci stisknutím klávesy **F5** v aplikaci Visual Studio.

4. Přejděte na záznam produktu, který jste změnili, a ověřte, zda je změna trvalá.

5. Zavřete aplikaci.

## <a name="next-steps"></a>Další kroky
 Po dokončení tohoto návodu můžete provádět následující související úlohy:

- Naučte se, jak pomocí okna **zdroje dat** v aplikaci Visual Studio navazovat ovládací prvky WPF na jiné typy zdrojů dat. Další informace najdete v tématu [vázání ovládacích prvků WPF na datovou službu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Naučte se používat okno **zdroje dat** v aplikaci Visual Studio k zobrazení souvisejících dat (tj. data v relaci nadřazený-podřízený) v ovládacích prvcích WPF. Další informace naleznete v tématu [Návod: zobrazení souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků WPF k datům v](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) sadě Visual Studio [vázání ovládacích prvků WPF na data v](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [nástrojích datové sady sady Visual Studio v nástroji Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [WPF a v Návrháři Silverlight](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) přehled [vazby dat](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
