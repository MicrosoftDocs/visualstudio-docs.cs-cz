---
title: Vytvoření vazby ovládacích prvků WPF k datové sadě
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8de276bfb6d7ec8bc36380ee41d86de07fc8dd74
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586975"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Vytvoření vazby ovládacích prvků WPF k datové sadě

V tomto návodu vytvoříte aplikaci WPF, která obsahuje ovládací prvky vázané na data. Ovládací prvky jsou vázány na záznamy produktu, které jsou zapouzdřeny v datové sadě. Můžete také přidat tlačítka pro procházení produktů a uložení změn záznamů produktu.

Tento návod znázorňuje následující úlohy:

- Vytvoření aplikace WPF a datové sady, která je generována z dat v ukázkové databázi AdventureWorksLT.

- Vytvoření sady ovládacích prvků vázaných na data přetažením tabulky dat z okna **zdroje dat** do okna v Návrháři WPF.

- Vytváření tlačítek, která pohybují vpřed a zpět záznamy produktů.

- Vytvořením tlačítka, které ukládá změny provedené uživateli na záznamy produktu, do tabulky dat a podkladového zdroje dat.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio

- Přístup ke spuštěné instanci SQL Server nebo SQL Server Express s připojenou ukázkovou databází AdventureWorks Light (AdventureWorksLT). Databázi AdventureWorksLT si můžete stáhnout z [archivu CodePlex](https://archive.codeplex.com/?p=awlt2008dbscript).

Předchozí znalosti následujících konceptů jsou také užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Datové sady a objekty TableAdapter. Další informace najdete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) a [objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

- Datová vazba WPF Další informace najdete v tématu [Přehled datových vazeb](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Vytvoření projektu

Vytvořte nový projekt WPF pro zobrazení záznamů produktu.

::: moniker range="vs-2017"

1. Otevřít Visual Studio.

2. V nabídce **soubor** vyberte **Nový** > **projekt**.

3. Rozbalte položku **Visual Basic** nebo **vizuál C#** a pak vyberte možnost **Windows**.

4. Vyberte šablonu projektu **aplikace WPF** .

5. Do pole **název** zadejte **AdventureWorksProductsEditor** a pak vyberte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřít Visual Studio.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. C# Vyhledejte šablonu projektu **aplikace WPF** a postupujte podle pokynů pro vytvoření projektu a pojmenování projektu **AdventureWorksProductsEditor**.

::: moniker-end

   Visual Studio vytvoří projekt AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Vytvoření datové sady pro aplikaci

Předtím, než můžete vytvořit ovládací prvky vázané na data, je nutné pro svou aplikaci definovat datový model a přidat je do okna **zdroje dat** . V tomto návodu vytvoříte datovou sadu, která bude použita jako datový model.

1. Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

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

8. Klikněte na **Dokončit**.

   Visual Studio přidá nový soubor `AdventureWorksLTDataSet.xsd` do projektu a přidá odpovídající položku **AdventureWorksLTDataSet** do okna **zdroje dat** . `AdventureWorksLTDataSet.xsd` soubor definuje typovou datovou sadu s názvem `AdventureWorksLTDataSet` a TableAdapter s názvem `ProductTableAdapter`. Později v tomto návodu použijete `ProductTableAdapter` k vyplnění datové sady daty a k uložení změn zpět do databáze.

9. Sestavte projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Upravit výchozí metodu Fill pro TableAdapter

Chcete-li datovou sadu vyplnit daty, použijte metodu `Fill` `ProductTableAdapter`. Ve výchozím nastavení metoda `Fill` vyplní `ProductDataTable` ve `AdventureWorksLTDataSet` všechny řádky dat z tabulky Product. Tuto metodu lze upravit tak, aby vracela pouze podmnožinu řádků. V tomto návodu upravte metodu `Fill` tak, aby vracela pouze řádky pro produkty, které mají fotografie.

1. V **Průzkumník řešení**dvakrát klikněte na soubor *AdventureWorksLTDataSet. xsd* .

     Otevře se Návrhář DataSet.

2. V návrháři klikněte pravým tlačítkem myši na příkaz **Fill**, **GetData ()** a vyberte možnost **Konfigurovat**.

     Otevře se průvodce **konfigurací TableAdapter** .

3. Na stránce **Zadejte příkaz SQL** přidejte následující klauzuli WHERE za příkaz `SELECT` v textovém poli.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Klikněte na **Dokončit**.

## <a name="define-the-user-interface"></a>Definování uživatelského rozhraní

Do okna přidejte několik tlačítek úpravou XAML v Návrháři WPF. Později v tomto návodu přidáte kód, který umožňuje uživatelům procházet a ukládat změny záznamů produktů pomocí těchto tlačítek.

1. V **Průzkumník řešení**dvakrát klikněte na *MainWindow. XAML*.

    Okno se otevře v **Návrháři WPF**.

2. V zobrazení [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] návrháře přidejte následující kód mezi značky `<Grid>`:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Sestavte projekt.

## <a name="create-data-bound-controls"></a>Vytváření ovládacích prvků vázaných na data

Vytvořte ovládací prvky, které zobrazují záznamy o zákaznících, přetažením tabulky `Product` z okna **zdroje dat** do návrháře WPF.

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

     Sada Visual Studio generuje kód XAML, který definuje sadu ovládacích prvků, které jsou vázány na data v tabulce **Products** . Také generuje kód, který načte data. Další informace o vygenerovaném kódu XAML a kódu naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. V návrháři klikněte na textové pole vedle popisku **ID produktu** .

7. V okně **vlastnosti** zaškrtněte políčko vedle vlastnosti **IsReadOnly** .

## <a name="navigate-product-records"></a>Navigace v záznamech produktů

Přidejte kód, který umožňuje uživatelům procházet záznamy produktů pomocí tlačítek **\<** a **>** .

1. V Návrháři poklikejte na tlačítko **<** na povrchu okna.

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `backButton_Click` obslužnou rutinu události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Upravte obslužnou rutinu události `Window_Loaded`, aby `ProductViewSource`, `AdventureWorksLTDataSet`a `AdventureWorksLTDataSetProductTableAdapter` byly mimo metodu a přístupná k celému formuláři. Deklarujete pouze ty, které mají být globální pro formulář, a přiřaďte je v rámci obslužné rutiny `Window_Loaded` události podobné následujícímu:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3. Do obslužné rutiny události `backButton_Click` přidejte následující kód:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4. Vraťte se do návrháře a dvakrát klikněte na tlačítko **>** .

5. Do obslužné rutiny události `nextButton_Click` přidejte následující kód:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Uložení změn záznamů produktu

Přidejte kód, který umožňuje uživatelům ukládat změny do záznamů produktů pomocí tlačítka **Uložit změny** .

1. V Návrháři dvakrát klikněte na tlačítko **Uložit změny** .

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `saveButton_Click` obslužnou rutinu události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Do obslužné rutiny události `saveButton_Click` přidejte následující kód:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > Tento příklad používá metodu `Save` `TableAdapter` k uložení změn. To je vhodné v tomto návodu, protože se mění jenom jedna datová tabulka. Pokud potřebujete uložit změny do více datových tabulek, můžete alternativně použít metodu `UpdateAll` `TableAdapterManager`, kterou sada Visual Studio generuje s datovou sadou. Další informace najdete v tématu [objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testování aplikace

Sestavte a spusťte aplikaci. Ověřte, zda můžete zobrazit a aktualizovat záznamy produktů.

1. Stiskněte klávesu **F5**.

     Aplikace se vytvoří a spustí. Zkontrolujte:

    - Textová pole zobrazují data z prvního záznamu produktu, který obsahuje fotografii. V tomto produktu je produkt s ID 713 a názvem **dlouhé logo Jersey, S**.

    - Kliknutím na tlačítko **>** nebo **<** můžete procházet dalšími záznamy produktů.

2. V jednom ze záznamů produktu změňte hodnotu **velikosti** a pak klikněte na **Uložit změny**.

3. Ukončete aplikaci a pak restartujte aplikaci stisknutím klávesy **F5** v aplikaci Visual Studio.

4. Přejděte na záznam produktu, který jste změnili, a ověřte, zda je změna trvalá.

5. Zavřete aplikaci.

## <a name="next-steps"></a>Další kroky

Po dokončení tohoto postupu můžete vyzkoušet následující související úlohy:

- Naučte se, jak pomocí okna **zdroje dat** v aplikaci Visual Studio navazovat ovládací prvky WPF na jiné typy zdrojů dat. Další informace najdete v tématu [vázání ovládacích prvků WPF na datovou službu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Naučte se používat okno **zdroje dat** v aplikaci Visual Studio k zobrazení souvisejících dat (tj. data v relaci nadřazený-podřízený) v ovládacích prvcích WPF. Další informace najdete v tématu [Návod: zobrazení souvisejících dat v aplikaci WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Přehled datových vazeb](/dotnet/desktop-wpf/data/data-binding-overview)
