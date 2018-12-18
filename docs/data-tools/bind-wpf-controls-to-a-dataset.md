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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 43b262344965091cf7599a9e1b2c43d6bcdb94f2
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305725"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Vytvoření vazby ovládacích prvků WPF k datové sadě

V tomto návodu vytvoříte aplikaci WPF, která obsahuje ovládací prvky vázané na data. Ovládací prvky jsou vázány na záznamy produktů, které jsou zapouzdřeny v datové sadě. Je také přidat tlačítka Procházet produkty a uložit změny do produktu záznamy.

Tento návod znázorňuje následující úlohy:

- Vytvoření aplikace WPF a datové sady, který je generován z dat z ukázkové databáze AdventureWorksLT.

- Vytvoření sady ovládacích prvků vázaných na data přetažením tabulku dat z **zdroje dat** okna do okna Návrháře WPF.

- Vytváření tlačítek, procházet záznamy produktů vpřed a zpět.

- Vytvoření tlačítka, který uloží změny, které uživatelé provádět na záznamy produktu do tabulky dat a podkladový zdroj dat.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio

- Přístup ke spuštěné instanci systému SQL Server nebo SQL Server Express, která obsahuje ukázkovou databázi AdventureWorks Light (AdventureWorksLT) k němu připojená. Můžete stáhnout z databáze AdventureWorksLT [CodePlex archivu](https://archive.codeplex.com/?p=awlt2008dbscript).

Předchozí znalosti následujících konceptů je také užitečné, ale nejsou vyžadovány k dokončení návodu:

- Datových sad a TableAdapters. Další informace najdete v tématu [datovou sadu nástrojů v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) a [objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

- Datové vazby WPF. Další informace najdete v tématu [přehled datových vazeb](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Vytvoření projektu

Vytvořte nový projekt WPF pro zobrazení záznamů produktu.

1. Spusťte sadu Visual Studio.

2. Na **souboru** nabídce vyberte možnost **nový** > **projektu**.

3. Rozbalte **jazyka Visual Basic** nebo **Visual C#** a pak vyberte **Windows**.

4. Vyberte **aplikace WPF** šablony projektu.

5. V **název** zadejte **AdventureWorksProductsEditor** a pak vyberte **OK**.

   Visual Studio vytvoří projekt AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Vytvoření datové sady pro aplikaci

Předtím, než budete moct vytvořit ovládací prvky vázané na data, musíte definovat datový model pro vaši aplikaci a přidejte ji tak **zdroje dat** okna. V tomto návodu vytvoříte datovou sadu pro použití jako datového modelu.

1. Na **Data** nabídky, klikněte na tlačítko **zobrazit zdroje dat**.

   **Zdroje dat** otevře se okno.

2. V **zdroje dat** okna, klikněte na tlačítko **přidat nový zdroj dat**.

   **Konfigurace zdroje dat** otevře se průvodce.

3. Na **zvolte typ zdroje dat** stránce **databáze**a potom klikněte na tlačítko **Další**.

4. Na **vyberte databázový Model** stránce **datovou sadu**a potom klikněte na tlačítko **Další**.

5. Na **vyberte datové připojení** stránky, vyberte jednu z následujících možností:

   - Pokud připojení dat k ukázkové databáze AdventureWorksLT je k dispozici v rozevíracím seznamu, vyberte ji a pak klikněte na tlačítko **Další**.

   - Klikněte na tlačítko **nové připojení**a vytvořte připojení k databázi AdventureWorksLT.

6. Na **uložit připojovací řetězec do souboru konfigurace aplikace** stránky, vyberte **Ano, uložit připojení jako** zaškrtněte políčko a potom klikněte na tlačítko **Další**.

7. Na **zvolte vaše databázové objekty** stránce, rozbalte **tabulky**a pak vyberte **produkt (SalesLT)** tabulky.

8. Klikněte na tlačítko **Dokončit**.

   Visual Studio přidá nový `AdventureWorksLTDataSet.xsd` soubor do projektu a přidá odpovídající **AdventureWorksLTDataSet** položkou **zdroje dat** okna. `AdventureWorksLTDataSet.xsd` Soubor definuje typové datové sady s názvem `AdventureWorksLTDataSet` a s názvem objektu typu TableAdapter `ProductTableAdapter`. Dále v tomto názorném postupu použijete `ProductTableAdapter` naplnění dataset s daty a uložte změny zpět do databáze.

9. Sestavte projekt.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Upravit výchozí metoda výplň TableAdapter

Chcete-li datovou sadu naplnit data, použijte `Fill` metodu `ProductTableAdapter`. Ve výchozím nastavení `Fill` metoda výplně `ProductDataTable` v `AdventureWorksLTDataSet` se všechny řádky dat z tabulky Product. Můžete upravit tuto metodu za účelem vrátí pouze podmnožinu řádků. V tomto návodu, změnit `Fill` metoda vrátí pouze řádky pro produkty, které mají fotografie.

1. V **Průzkumníka řešení**, dvakrát klikněte *AdventureWorksLTDataSet.xsd* souboru.

     Otevře se Návrhář datových sad.

2. V návrháři, klikněte pravým tlačítkem myši **vyplnit**, **GetData()** dotazu a vyberte **konfigurovat**.

     **Konfigurace TableAdapter** otevře se průvodce.

3. V **zadejte příkaz SQL** stránce, přidejte následující klauzule WHERE po `SELECT` příkaz v textovém poli.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Klikněte na tlačítko **Dokončit**.

## <a name="define-the-user-interface"></a>Definování uživatelského rozhraní

Přidání několika tlačítek do okna tak, že upravíte XAML ve WPF Designer. Dále v tomto názorném postupu přidáte kód, který umožňuje uživatelům posouvat prostřednictvím a uložte změny záznamů produkty pomocí těchto tlačítek.

1. V **Průzkumníka řešení**, dvakrát klikněte na panel *souboru MainWindow.xaml*.

    Otevře se okno v **Návrhář WPF**.

2. V [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] návrháře, přidejte následující kód mezi `<Grid>` značky:

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

## <a name="create-data-bound-controls"></a>Vytvoření ovládacích prvků vázaných na data

Vytvořte ovládací prvky zobrazující záznamy o zákaznících přetažením `Product` tabulce **zdroje dat** okno do Návrháře WPF.

1. V **zdroje dat** okna, klikněte na rozevírací nabídku **produktu** uzel a vyberte možnost **podrobnosti**.

2. Rozbalte **produktu** uzlu.

3. V tomto příkladu některá pole se nezobrazí, takže klikněte na rozevírací nabídku vedle následujících uzlů a vyberte **žádný**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - ROWGUID

    - ModifiedDate

4. Klikněte na rozevírací nabídku vedle položky **thumbnailphoto nastavuje** uzel a vyberte možnost **Image**.

    > [!NOTE]
    > Ve výchozím nastavení, položky v **zdroje dat** okno, které představují obrázky mají jejich výchozího ovládacího prvku nastavte na **žádný**. Je to proto, že obrázky jsou uloženy jako pole bajtů v databázích a pole bajtů může obsahovat cokoli od jednoduchých pole bajtů na spustitelný soubor velké aplikace.

5. Z **zdroje dat** okno, přetáhněte **produktu** uzlů na řádek mřížky pod řádkem, který obsahuje tlačítka.

     Generuje XAML, který definuje sadu ovládacích prvků, které jsou vázány na data v sadě Visual Studio **produkty** tabulky. Také generuje kód, který načte data. Další informace o vygenerovaný XAML a kódu, naleznete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. V návrháři, klepněte na textové pole vedle položky **ID produktu** popisek.

7. V **vlastnosti** okna, vyberte zaškrtávací políčko vedle položky **IsReadOnly** vlastnost.

## <a name="navigate-product-records"></a>Přejděte záznamy produktů

Přidejte kód, který umožňuje uživatelům procházet záznamy produktu s použitím **\<** a **>** tlačítka.

1. V Návrháři dvakrát klikněte **<** tlačítko na plochu okna.

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `backButton_Click` obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.

2. Upravit `Window_Loaded` obslužná rutina události, takže `ProductViewSource`, `AdventureWorksLTDataSet`, a `AdventureWorksLTDataSetProductTableAdapter` jsou mimo metodu a dostupné pro celý formulář. Deklarovat pouze tyto globální do formuláře a přiřaďte je v rámci `Window_Loaded` obslužná rutina události je podobný následujícímu:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3. Přidejte následující kód, který `backButton_Click` obslužné rutiny události:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4. Vraťte se do návrháře a dvojím kliknutím **>** tlačítko.

5. Přidejte následující kód, který `nextButton_Click` obslužné rutiny události:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Uložit změny do produktu záznamů

Přidejte kód, který umožňuje uživatelům ukládat změny produktu záznamů pomocí **uložit změny** tlačítko.

1. V Návrháři dvakrát klikněte **uložit změny** tlačítko.

     Visual Studio otevře soubor kódu na pozadí a vytvoří novou `saveButton_Click` obslužné rutiny události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí.

2. Přidejte následující kód, který `saveButton_Click` obslužné rutiny události:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > V tomto příkladu `Save` metodu `TableAdapter` a uložte změny. To je vhodné v tomto názorném postupu, protože mění jenom jednu datovou tabulku. Pokud je potřeba uložit změny do několika tabulek dat, případně můžete použít `UpdateAll` metodu `TableAdapterManager` , který generuje sada Visual Studio s vaší datové sadě. Další informace najdete v tématu [objekty TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testování aplikace

Sestavte a spusťte aplikaci. Ověřte, že můžete zobrazit a aktualizovat záznamy produktů.

1. Stisknutím klávesy **F5**.

     Aplikace vytvoří a spustí. Ověřte následující:

    - Do textových polí zobrazit data z první položky produktu, který má fotografii. Tento produkt obsahuje produkt ID 713 a název **Jersey Logo obal dlouho, S**.

    - Můžete kliknout **>** nebo **<** tlačítka Procházet další záznamy produktu.

2. V jednom produktu záznamy, změnit **velikost** hodnotu a potom klikněte na tlačítko **uložit změny**.

3. Ukončete aplikaci a restartujte aplikaci stisknutím klávesy **F5** v sadě Visual Studio.

4. Přejděte k záznamu produktu, který jste změnili a ověřte, že změny trvalý.

5. Ukončete aplikaci.

## <a name="next-steps"></a>Další kroky

Po dokončení tohoto návodu, můžete vyzkoušet následující související úlohy:

- Další informace o použití **zdroje dat** okna v sadě Visual Studio k vytvoření vazby WPF ovládací prvky na jiné typy datových zdrojů. Další informace najdete v tématu [WPF vytvoření vazby ovládacích prvků do datové služby WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Další informace o použití **zdroje dat** okna v sadě Visual Studio pro zobrazení souvisejících dat (tj. data ve vztahu nadřazený podřízený) v ovládacích prvcích WPF. Další informace najdete v tématu [návod: zobrazení souvisejících dat v aplikaci WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Přehled datových vazeb](/dotnet/framework/wpf/data/data-binding-overview)
