---
title: 'Návod: zobrazení souvisejících dat v aplikaci WPF | Microsoft Docs'
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
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 8116d4ab4a2f20f79f3849ae7f8b324af9832dd5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850244"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Návod: Zobrazování souvisejících dat v aplikaci WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto návodu vytvoříte aplikaci WPF, která bude zobrazovat data z databázových tabulek, které mají relaci nadřazený-podřízený. Data jsou zapouzdřena v entitách v model EDM (Entity Data Model). Nadřazená entita obsahuje informace o přehledu pro sadu objednávek. Každá vlastnost této entity je vázána na jiný ovládací prvek v aplikaci. Podřízená entita obsahuje podrobnosti o jednotlivých objednávkách. Tato sada dat je svázána s ovládacím prvkem <xref:System.Windows.Controls.DataGrid>.

 Tento návod znázorňuje následující úlohy:

- Vytvoření aplikace WPF a model EDM (Entity Data Model), která je generována z dat v ukázkové databázi AdventureWorksLT.

- Vytvoření sady ovládacích prvků vázaných na data, které zobrazují informace o přehledu pro sadu objednávek. Ovládací prvky lze vytvořit přetažením nadřazené entity z okna **zdroje dat** do **Návrháře WPF**.

- Vytvoření ovládacího prvku <xref:System.Windows.Controls.DataGrid>, který zobrazí související podrobnosti pro každou vybranou objednávku. Ovládací prvky lze vytvořit přetažením podřízené entity z okna **zdroje dat** do okna v **Návrháři WPF**.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

- Přístup ke spuštěné instanci SQL Server nebo SQL Server Express, ke které je připojena ukázková databáze AdventureWorksLT. Databázi AdventureWorksLT si můžete stáhnout z webu [CodePlex](https://codeplex.com/SqlServerSamples).

  Předchozí znalosti následujících konceptů jsou také užitečné, ale nevyžadují se k dokončení tohoto postupu:

- Entity data Models a ADO.NET Entity Framework. Další informace najdete v tématu [přehled Entity Framework](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Práce s návrhářem WPF. Další informace naleznete v tématu [Přehled Návrháře WPF a Silverlight](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Datová vazba WPF Další informace najdete v tématu [Přehled datových vazeb](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="creating-the-project"></a>Vytvoření projektu
 Vytvořte nový projekt WPF pro zobrazení záznamů objednávek.

#### <a name="to-create-a-new-wpf-project"></a>Vytvoření nového projektu WPF

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. Rozbalte **položku C# Visual** nebo **Visual Basic**a pak vyberte možnost **Windows**.

4. Ujistěte se, že je vybrána možnost **.NET Framework 4** v poli se seznamem v horní části dialogového okna. <xref:System.Windows.Controls.DataGrid> ovládací prvek, který používáte v tomto návodu, je k dispozici pouze v .NET Framework 4.

5. Vyberte šablonu projektu **aplikace WPF** .

6. Do pole **Název** zadejte `AdventureWorksOrdersViewer`.

7. Klikněte na tlačítko **OK**.

     Visual Studio vytvoří projekt `AdventureWorksOrdersViewer`.

## <a name="creating-an-entity-data-model-for-the-application"></a>Vytvoření model EDM (Entity Data Model) pro aplikaci
 Předtím, než můžete vytvořit ovládací prvky vázané na data, je nutné pro svou aplikaci definovat datový model a přidat je do okna **zdroje dat** . V tomto návodu je datovým modelem model EDM (Entity Data Model).

#### <a name="to-create-an-entity-data-model"></a>Vytvoření model EDM (Entity Data Model)

1. V nabídce **data** klikněte na tlačítko **Přidat nový zdroj dat** . tím otevřete **Průvodce konfigurací zdroje dat**.

2. Na stránce **Vybrat typ zdroje dat** klikněte na možnost **databáze**a poté klikněte na tlačítko **Další**.

3. Na stránce **Vyberte databázový model** klikněte na **model EDM (Entity Data Model)** a potom klikněte na **Další**.

4. Na stránce **Vybrat obsah modelu** klikněte na **vygenerovat z databáze**a pak klikněte na **Další**.

5. Na stránce **Vyberte datové připojení** proveďte jednu z následujících akcí:

   - Pokud je datové připojení k ukázkové databázi AdventureWorksLT dostupné v rozevíracím seznamu, vyberte je.

      -nebo-

   - Klikněte na **nové připojení** a vytvořte připojení k databázi AdventureWorksLT.

     Ujistěte se, že je zaškrtnuté políčko **Uložit nastavení připojení entity v App. config jako** možnost a potom klikněte na tlačítko **Další**.

6. Na stránce **Zvolte vaše databázové objekty** rozbalte **tabulky**a potom vyberte následující tabulky:

   - **Prodejní**

   - **SalesOrderHeader**

7. Klikněte na **Dokončit**.

8. Sestavte projekt.

## <a name="creating-data-bound-controls-that-display-the-orders"></a>Vytváření ovládacích prvků vázaných na data, které zobrazují objednávky
 Vytvořte ovládací prvky, které zobrazují záznamy objednávky přetažením entity `SalesOrderHeaders` z okna **zdroje dat** do návrháře WPF.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Vytvoření ovládacích prvků vázaných na data, které zobrazují záznamy objednávky

1. V **Průzkumník řešení**dvakrát klikněte na MainWindow. XAML.

    Okno se otevře v Návrháři WPF.

2. Upravte kód XAML tak, aby se vlastnosti **Height** a **Width** nastavily na 800.

3. V okně **zdroje dat** klikněte na rozevírací nabídku uzlu **SalesOrderHeaders** a vyberte **Podrobnosti**.

4. Rozbalte uzel **SalesOrderHeaders** .

5. Klikněte na rozevírací nabídku vedle **SalesOrderID** a vyberte položku **ComboBox**.

6. Pro každý z následujících podřízených uzlů uzlu **SalesOrderHeader** klikněte na rozevírací nabídku vedle uzlu a vyberte **žádné**:

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **ShipToAddressID**

   - **BillToAddressID**

   - **CreditCardApprovalCode**

   - **Jedna**

   - **TaxAmt**

   - **Odbaven**

   - **ROWGUID**

   - **ModifiedDate**

     Tato akce zabrání aplikaci Visual Studio v vytváření ovládacích prvků vázaných na data pro tyto uzly v dalším kroku. V tomto návodu se předpokládá, že koncový uživatel nepotřebuje tato data zobrazit.

7. V okně **zdroje dat** Přetáhněte uzel **SalesOrderHeaders** do okna v **Návrháři WPF**.

    Sada Visual Studio generuje XAML, která vytvoří sadu ovládacích prvků, které jsou vázány na data v entitě **SalesOrderHeaders** a kód, který načte data. Další informace o vygenerovaném kódu XAML a kódu naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

8. V návrháři klikněte na pole se seznamem vedle popisku **ID prodejní objednávky** .

9. V okně **vlastnosti** zaškrtněte políčko vedle vlastnosti **IsReadOnly** .

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Vytvoření prvku DataGrid, který zobrazí podrobnosti objednávky
 Vytvořte <xref:System.Windows.Controls.DataGrid> ovládací prvek, který zobrazí podrobnosti o objednávce přetažením entity `SalesOrderDetails` z okna **zdroje dat** do návrháře WPF.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Vytvoření prvku DataGrid, který zobrazí podrobnosti objednávky

1. V okně **zdroje dat** vyhledejte uzel **SalesOrderDetails** , který je podřízenou položkou uzlu **SalesOrderHeaders** .

   > [!NOTE]
   > K dispozici je také uzel **SalesOrderDetails** , který je partnerským uzlem uzlu **SalesOrderHeaders** . Ujistěte se, že jste vybrali podřízený uzel uzlu **SalesOrderHeaders** .

2. Rozbalte uzel podřízené uzly **SalesOrderDetails** .

3. Pro každý z následujících podřízených uzlů uzlu **SalesOrderDetails** klikněte na rozevírací nabídku vedle uzlu a vyberte **žádné**:

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **ROWGUID**

   - **ModifiedDate**

     Tato akce zabrání aplikaci Visual Studio v zahrnutí těchto dat do ovládacího prvku <xref:System.Windows.Controls.DataGrid>, který vytvoříte v následujícím kroku. V tomto návodu se předpokládá, že koncový uživatel nepotřebuje tato data zobrazit.

4. V okně **zdroje dat** přetáhněte podřízený uzel **SalesOrderDetails** do okna v **Návrháři WPF**.

    Visual Studio generuje XAML pro definování nového ovládacího prvku <xref:System.Windows.Controls.DataGrid> vázaného na data a ovládací prvek se zobrazí v návrháři. Visual Studio také aktualizuje generovanou metodu `GetSalesOrderHeadersQuery` v souboru kódu na pozadí, aby zahrnovala data v entitě **SalesOrderDetails** .

## <a name="testing-the-application"></a>Testování aplikace
 Sestavte a spusťte aplikaci, abyste ověřili, že zobrazuje záznamy objednávky.

#### <a name="to-test-the-application"></a>Testování aplikace

1. Stiskněte klávesu **F5**.

     Aplikace se vytvoří a spustí. Zkontrolujte:

    - V poli se seznamem **ID prodejní objednávky** se zobrazí **71774**. Toto je první ID objednávky v entitě.

    - Pro každé pořadí, které vyberete v poli se seznamem **ID prodejní objednávky** , se zobrazí podrobné informace o objednávce v <xref:System.Windows.Controls.DataGrid>.

2. Zavřete aplikaci.

## <a name="next-steps"></a>Další kroky
 Po dokončení tohoto Názorného postupu se naučíte, jak pomocí okna **zdroje dat** v aplikaci Visual Studio navazovat ovládací prvky WPF na jiné typy zdrojů dat. Další informace najdete v tématu [vázání ovládacích prvků WPF na datovou službu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) a [vázání ovládacích prvků WPF na datovou sadu](../data-tools/bind-wpf-controls-to-a-dataset.md).

## <a name="see-also"></a>Viz také
 [Vázání ovládacích prvků WPF k datům v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [zobrazení souvisejících dat v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md)
