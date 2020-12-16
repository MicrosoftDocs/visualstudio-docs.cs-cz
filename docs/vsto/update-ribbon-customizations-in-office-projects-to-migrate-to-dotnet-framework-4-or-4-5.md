---
title: Aktualizace přizpůsobení pásu karet migrovány na .NET Framework 4,5
description: Přečtěte si, že je nutné provést změny kódu projektu, pokud je cílová verze rozhraní změněna na .NET Framework 4 nebo novější.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a831bced793f13394a89d278a6be1cda959c775a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527930"
---
# <a name="update-ribbon-customizations-migrated-to-net-framework-45"></a>Aktualizace přizpůsobení pásu karet migrovány na .NET Framework 4,5

  Pokud projekt obsahuje přizpůsobení pásu karet, které bylo vytvořeno pomocí položky projektu **pás karet (vizuální Návrhář)** , je nutné provést následující změny kódu projektu, pokud je cílová architektura změněna na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo vyšší.

- Upravte vygenerovaný kód pásu karet.

- Upravte jakýkoliv kód, který vytvoří instanci ovládacích prvků pásu karet za běhu, zpracovává události pásu karet nebo nastavuje polohu komponenty pásu karet programově.

## <a name="update-the-generated-ribbon-code"></a>Aktualizace generovaného kódu pásu karet
 Pokud je cílová architektura projektu změněna na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné změnit vygenerovaný kód pro položku pásu karet provedením následujících kroků. Soubory kódu, které potřebujete aktualizovat, závisí na programovacím jazyku a způsobu, jakým jste projekt vytvořili:

- V Visual Basic projekty nebo v projektech Visual C#, které jste vytvořili v [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] nebo [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] proveďte všechny kroky v souboru s kódem na pozadí pásu karet (*YourRibbonItem*). Designer.cs nebo *YourRibbonItem*. Designer. vb). Pokud chcete zobrazit soubor kódu na pozadí v Visual Basic projekty, klikněte na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení**.

- V projektech Visual C#, které jste vytvořili v aplikaci Visual Studio 2008 a potom upgradovali na [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , proveďte první dva kroky v souboru kódu pásu karet (*YourRibbonItem*. cs nebo *YourRibbonItem*. vb) a proveďte zbývající kroky v souboru s kódem na pozadí pásu karet.

### <a name="to-change-the-generated-ribbon-code"></a>Změna generovaného kódu pásu karet

1. Upravte deklaraci třídy pásu karet tak, aby byla odvozena z <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> místo `Microsoft.Office.Tools.Ribbon.OfficeRibbon` .

2. Upravte konstruktor třídy pásu karet, jak je znázorněno níže. Pokud jste do konstruktoru přidali libovolný vlastní kód, neměňte kód. V Visual Basic projekty upravte pouze konstruktor bez parametrů. Ignorujte druhý konstruktor.

     Následující příklad kódu ukazuje výchozí konstruktor třídy pásu karet v projektu, který cílí na .NET Framework 3,5.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     Následující příklad kódu ukazuje výchozí konstruktor třídy pásu karet v projektu, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo vyšší.

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3. V `InitializeComponent` metodě upravte libovolný kód, který vytvoří ovládací prvek pásu karet tak, aby kód místo toho používal jednu z pomocných metod <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu.

    > [!NOTE]
    > V projektech v jazyce Visual C# je nutné rozšířit oblast, která je pojmenována `Component Designer generated code` k zobrazení `InitializeComponent` metody.

     Předpokládejme například, že soubor obsahuje následující řádek kódu, který vytváří instanci <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> pojmenované `button1` v projektu, který cílí na .NET Framework 3,5.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     V projektu, který se zaměřuje na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, musíte místo toho použít následující kód.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Úplný seznam pomocných metod pro ovládací prvky pásu karet najdete v tématu věnovaném [vytvoření instance ovládacích prvků pásu karet](#ribboncontrols).

4. V projektech v jazyce Visual C# upravte libovolný řádek kódu v `InitializeComponent` metodě, která používá <xref:System.EventHandler%601> delegáta pro místo toho použití konkrétního delegáta pásu karet.

     Předpokládejme například, že soubor obsahuje následující řádek kódu, který zpracovává <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> událost v projektu, který cílí na .NET Framework 3,5.

    \<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> v projektu, který se zaměřuje na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, musíte místo toho použít následující kód.

    \<CodeContentPlaceHolder>9 </CodeContentPlaceHolder> úplný seznam delegátů pásu karet najdete v tématu [zpracování událostí pásu karet](#ribbonevents).

5. V Visual Basic projekty vyhledejte `ThisRibbonCollection` třídu na konci souboru. Upravte deklaraci této třídy tak, aby již nedědila z `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection` .

## <a name="instantiate-ribbon-controls"></a><a name="ribboncontrols"></a> Vytvoření instance ovládacích prvků pásu karet
 Je nutné upravit jakýkoli kód, který dynamicky konkretizuje ovládací prvky pásu karet. V projektech, které cílí na .NET Framework 3,5, jsou ovládací prvky pásu karet třídy, které lze vytvořit přímo v určitých scénářích. V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, jsou tyto ovládací prvky rozhraní, které nelze vytvořit přímo. Ovládací prvky je nutné vytvořit pomocí metod, které jsou k dispozici v <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu.

 Existují dva způsoby, jak získat přístup k <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu:

- Pomocí vlastnosti factory třídy pásu karet. Použijte tento přístup z kódu ve své třídě pásu karet.

- Pomocí `Globals.Factory.GetRibbonFactory` metody. Použijte tento přístup z kódu mimo svou třídu pásu karet. Další informace o třídě Globals naleznete v tématu [globální přístup k objektům v projektech systému Office](../vsto/global-access-to-objects-in-office-projects.md).

  Následující příklad kódu ukazuje, jak vytvořit <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> ve třídě pásu karet v projektu, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.

\<CodeContentPlaceHolder>10 </CodeContentPlaceHolder> 
 \<CodeContentPlaceHolder> 11 </CodeContentPlaceHolder> v následující tabulce jsou uvedeny ovládací prvky, které můžete vytvořit programově a metodu, která slouží k vytvoření ovládacích prvků v projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.

|Řízení|Metoda RibbonFactory pro použití v [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a novějších projektech|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

## <a name="handle-ribbon-events"></a><a name="ribbonevents"></a> Zpracování událostí pásu karet
 Je nutné upravit jakýkoli kód, který zpracovává události ovládacích prvků pásu karet. V projektech, které cílí na .NET Framework 3,5, jsou tyto události zpracovávány pomocí obecného <xref:System.EventHandler%601> delegáta. V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, jsou nyní tyto události zpracovávány jinými delegáty.

 V následující tabulce jsou uvedeny události pásu karet a delegáti, kteří jsou k nim přidruženi v projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.

|Událost|Delegát pro použití v [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a novějších projektech|
|-----------| - |
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> událost ve vygenerované třídě pásu karet|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Nastavení pozice komponenty pásu karet prostřednictvím kódu programu
 Je třeba upravit jakýkoli kód, který nastaví umístění skupin pásu karet, karet nebo ovládacích prvků. V projektech, které cílí na .NET Framework 3,5, můžete použít `AfterOfficeId` metody a `BeforeOfficeId` statické `Microsoft.Office.Tools.Ribbon.RibbonPosition` třídy k přiřazení `Position` Vlastnosti skupiny, karty nebo ovládacího prvku. V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, musíte přistupovat k těmto metodám pomocí <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> vlastnosti poskytované <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektem.

 Existují dva způsoby, jak získat přístup k <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu:

- Pomocí `Factory` vlastnosti třídy pásu karet. Použijte tento přístup z kódu ve své třídě pásu karet.

- Pomocí `Globals.Factory.GetRibbonFactory` metody. Použijte tento přístup z kódu mimo svou třídu pásu karet. Další informace o třídě Globals naleznete v tématu [globální přístup k objektům v projektech systému Office](../vsto/global-access-to-objects-in-office-projects.md).

  Následující příklad kódu ukazuje, jak nastavit `Position` vlastnost karty ve třídě pásu karet v projektu, který cílí na .NET Framework 3,5.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 Následující příklad kódu ukazuje stejný úkol v projektu, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>Viz také
- [Migrace řešení Office na .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Návrhář pásu karet](../vsto/ribbon-designer.md)
