---
title: Aktualizace vlastních nastavení pásu karet v projektech Office při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4cfd5fb259db7903541e0a86f16c720c9ff9c4d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937418"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizace vlastních nastavení pásu karet v projektech Office při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5
  Pokud váš projekt obsahuje vlastní nastavení pásu karet, který byl vytvořen pomocí **pás karet (vizuální návrhář)** položku projektu, musíte proveďte následující změny do projektu kódu, pokud Cílová architektura, která se změní na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později.  
  
-   Upravte vygenerovaný kód pásu karet.  
  
-   Upravte veškerý kód, který vytvoří instanci ovládacích prvků pásu karet za běhu, zpracovává události pásu karet nebo nastavuje pozici komponentu pásu karet prostřednictvím kódu programu.  
  
## <a name="update-the-generated-ribbon-code"></a>Aktualizace generovaného kódu pásu karet  
 Pokud cílové rozhraní projektu se změní na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné změnit generovaného kódu pro položku pásu karet provedením následujících kroků. Soubory kódu, které je potřeba aktualizovat v závislosti na programovacím jazyce a jak vytvořit projekt:  
  
-   V projektech Visual Basicu nebo v projektech Visual C#, které jste vytvořili v některém [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] nebo [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] všechny následující kroky proveďte v soubor kódu pásu karet (*YourRibbonItem*. Designer.cs nebo *YourRibbonItem*. Designer.vb). Soubor kódu na pozadí v projektech Visual Basicu zobrazíte kliknutím **zobrazit všechny soubory** tlačítko **Průzkumníku řešení**.  
  
-   V projektech Visual C#, které jste vytvořili v sadě Visual Studio 2008 a potom upgradovali na [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], proveďte první dva kroky v soubor kódu pásu karet (*YourRibbonItem*.cs nebo *YourRibbonItem*.vb), a Proveďte zbývající kroky v soubor kódu pásu karet.  
  
### <a name="to-change-the-generated-ribbon-code"></a>Chcete-li změnit generovaného kódu pásu karet  
  
1.  Upravit deklarace třídy pásu karet, takže je odvozena z <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> místo `Microsoft.Office.Tools.Ribbon.OfficeRibbon`.  
  
2.  Upravte konstruktor třídy pásu karet, jak je znázorněno níže. Pokud jste přidali vlastní kód do konstruktoru, neměňte váš kód. V projektech Visual Basicu upravte pouze konstruktor bez parametrů. Ignorujte jiných konstruktoru.  
  
     Následující příklad kódu ukazuje výchozí konstruktor třídy pásu karet v projektu, který cílí rozhraní .NET Framework 3.5.  
  
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
  
     Následující příklad kódu ukazuje výchozí konstruktor třídy pásu karet v projektu, který cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.  
  
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
  
3.  V `InitializeComponent` metody upravit veškerý kód, který vytvoří ovládací prvek pásu karet tak, aby kód místo toho používá jednu z metod helper <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu.  
  
    > [!NOTE]  
    >  V projektech Visual C#, je třeba rozbalit oblast s názvem `Component Designer generated code` zobrazíte `InitializeComponent` metody.  
  
     Předpokládejme například, že soubor obsahuje následující řádek kódu, který vytvoří instanci <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> s názvem `button1` v projektu, který cílí na rozhraní .NET Framework 3.5.  
  
    ```vb  
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();  
    ```  
  
     V projektu, který se zaměřuje [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné použít následující kód místo.  
  
    ```vb  
    Me.button1 = Me.Factory.CreateRibbonButton()  
    ```  
  
    ```csharp  
    this.button1 = this.Factory.CreateRibbonButton();  
    ```  
  
     Úplný seznam pomocné metody pro ovládací prvky pásu karet, najdete v části [ovládací prvky pásu karet vytvořit instanci](#ribboncontrols).  
  
4.  V projektech Visual C#, upravte libovolném řádku kódu v `InitializeComponent` metodu, která se používá <xref:System.EventHandler%601> delegáta místo toho použít konkrétní delegáta pásu karet.  
  
     Předpokládejme například, že soubor obsahuje následující řádek kódu, který zpracovává <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> události v projektu, který cílí na rozhraní .NET Framework 3.5.  
  
    <CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
     V projektu, který se zaměřuje [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné použít následující kód místo.  
  
    <CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
     Úplný seznam delegátů pásu karet najdete v tématu [zpracování pás karet událostí](#ribbonevents).  
  
5.  V projektech Visual Basicu, vyhledejte `ThisRibbonCollection` třídy na konci souboru. Upravte deklaraci této třídy, aby už nebude dědit z `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`.  
  
##  <a name="ribboncontrols"></a> Vytvoření instance ovládacích prvků pásu karet  
 Je třeba upravit jakýkoli kód, který dynamicky vytvoří instanci ovládacích prvků pásu karet. V projektech, které se zaměřují rozhraní .NET Framework 3.5, ovládací prvky pásu karet jsou třídy, které lze vytvořit instanci přímo v některých scénářích. V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, jsou tyto ovládací prvky rozhraní, které nelze přímo vytvořit instanci. Musíte vytvořit ovládací prvky pomocí metod, které jsou poskytovány <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu.  
  
 Existují dva způsoby přístupu k <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu:  
  
- Pomocí vlastnosti objekt pro vytváření třídy pásu karet. Použijte tento přístup z kódu ve své třídě pásu karet.  
  
- S použitím `Globals.Factory.GetRibbonFactory` metody. Použijte tento přístup z kódu mimo svou třídu pásu karet. Další informace o třídě Globals, naleznete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
  Následující příklad kódu ukazuje, jak vytvořit <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> ve třídě pásu karet v projektu, který se zaměřuje [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 Následující tabulka uvádí můžete programově vytvořit ovládací prvky a metody pro použití k vytvoření ovládacích prvků v projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.  
  
|Ovládací prvek|Metoda RibbonFactory pro použití v [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a novější projekty|  
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
  
##  <a name="ribbonevents"></a> Zpracování události pásu karet  
 Je třeba upravit jakýkoli kód, který zpracovává události ovládacích prvků pásu karet. V projektech cílených rozhraní .NET Framework 3.5, jsou tyto události zpracovat Obecné <xref:System.EventHandler%601> delegovat. V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později, jsou tyto události nyní zpracovat jiných delegátů.  
  
 Následující tabulka uvádí události pásu karet a delegáty, které jsou spojeny s nimi v projektech cílených [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.  
  
|Událost|Delegát pro použití v [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a novější projekty|  
|-----------| - |  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> událost v generované třídě pásu karet|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Nastavíte pozici komponentu pásu karet prostřednictvím kódu programu  
 Je třeba upravit jakýkoli kód, který nastavuje pozici skupin, karty nebo ovládací prvky pásu karet. V projektech cílených rozhraní .NET Framework 3.5, můžete použít `AfterOfficeId` a `BeforeOfficeId` metody statické `Microsoft.Office.Tools.Ribbon.RibbonPosition` třídy přiřazení `Position` vlastnosti skupiny, karta nebo ovládací prvek. V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později, musíte tyto metody přístup s použitím <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> vlastnost poskytované <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu.  
  
 Existují dva způsoby přístupu k <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objektu:  
  
- S použitím `Factory` vlastnosti třídy pásu karet. Použijte tento přístup z kódu ve své třídě pásu karet.  
  
- S použitím `Globals.Factory.GetRibbonFactory` metody. Použijte tento přístup z kódu mimo svou třídu pásu karet. Další informace o třídě Globals, naleznete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
  Následující příklad kódu ukazuje, jak nastavit `Position` vlastnosti karty ve třídě pásu karet v projektu, který cílí na rozhraní .NET Framework 3.5.  
  
```vb  
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");  
```  
  
 Následující příklad kódu ukazuje stejný úkol v projektu, který se zaměřuje [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  
  
```vb  
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")  
```  
  
```csharp  
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");  
```  
  
## <a name="see-also"></a>Viz také:  
 [Migrace řešení Office na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)  
  
  