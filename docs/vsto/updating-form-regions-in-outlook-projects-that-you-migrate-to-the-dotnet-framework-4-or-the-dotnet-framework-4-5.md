---
title: Aktualizace oblastí formuláře Outlooku při migraci na .NET Framework 4,5
description: Pokud je cílová architektura projektu doplňku VSTO aplikace Outlook s oblastmi formuláře změněna na .NET Framework 4 nebo novější, je nutné upravit kód.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 15b212a8b7dde85e66b18b78d356bdb31c62836a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921886"
---
# <a name="update-outlook-form-regions-when-migrated-to-net-framework-45"></a>Aktualizace oblastí formuláře Outlooku při migraci na .NET Framework 4,5

  Pokud je cílová architektura projektu doplňku aplikace Outlook VSTO s oblastí formuláře změněna na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo vyšší, je nutné provést některé změny v kódu vygenerované oblasti formuláře a v jakémkoli kódu, který vytváří instance určitých tříd oblastí formuláře za běhu.

## <a name="update-the-generated-form-region-code"></a>Aktualizace kódu vygenerované oblasti formuláře
 Pokud je cílová architektura projektu změněna na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné změnit kód oblasti vygenerovaného formuláře. Změny, které provedete, se liší pro oblasti formulářů, které jste navrhli v aplikaci Visual Studio a oblasti formulářů, které jste importovali z Outlooku. Další informace o rozdílech mezi těmito typy oblastí formuláře najdete v tématu věnovaném [vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Chcete-li aktualizovat generovaný kód pro oblast formuláře, kterou jste navrhli v aplikaci Visual Studio

1. V editoru kódu otevřete soubor kódu na pozadí oblasti formuláře. Tento soubor má název *YourFormRegion*. Designer.cs nebo *YourFormRegion*. Designer. vb. Pokud chcete tento soubor zobrazit v Visual Basic projekty, klikněte na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení**.

2. Upravte deklaraci třídy region formuláře tak, aby byla odvozena z <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> místo `Microsoft.Office.Tools.Outlook.FormRegionControl` .

3. Upravte konstruktor třídy region formuláře, jak je znázorněno v následujících příkladech kódu.

     Následující příklad kódu ukazuje konstruktor třídy region formuláře v projektu, který cílí na .NET Framework 3,5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.InitializeComponent();
    }
    ```

     Následující příklad kódu ukazuje konstruktor třídy region formuláře v projektu, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.InitializeComponent();
    }
    ```

4. Upravte podpis `InitializeManifest` metody, jak je znázorněno níže. Ujistěte se, že kód v metodě neupravujete. Tento kód představuje nastavení oblasti formuláře, které jste použili v návrháři. V projektech v jazyce Visual C# je nutné rozšířit oblast, která je pojmenována `Form Region Designer generated code` k zobrazení této metody.

     Následující příklad kódu ukazuje podpis `InitializeManifest` metody v projektu, který cílí na .NET Framework 3,5.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)
    {
        // Do not change code in this method.
    }
    ```

     Následující příklad kódu ukazuje `InitializeManifest` metodu podpisu v projektu, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,
        Microsoft.Office.Tools.Outlook.Factory factory)
    {
        // Do not change code in this method.
    }
    ```

5. Přidejte do projektu novou položku oblasti formuláře Outlooku. Otevřete soubor kódu na pozadí pro novou oblast formuláře, vyhledejte *YourNewFormRegion* `Factory` a `WindowFormRegionCollection` třídy v souboru a zkopírujte tyto třídy do schránky.

6. Odstraňte novou oblast formuláře, kterou jste přidali do projektu.

7. V souboru kódu na pozadí oblasti formuláře, kterou aktualizujete, aby fungovala v přecíleném projektu, vyhledejte *YourOriginalFormRegion* `Factory` a `WindowFormRegionCollection` třídy a nahraďte je kódem, který jste zkopírovali z nové oblasti formuláře.

8. V *YourNewFormRegion* `Factory` a `WindowFormRegionCollection` třídách vyhledejte všechny odkazy na třídu *YourNewFormRegion* a místo toho změňte každý odkaz na třídu *YourOriginalFormRegion* . Pokud je například oblast formuláře, kterou aktualizujete, pojmenována `SalesDataFormRegion` a nová oblast formuláře, kterou jste vytvořili v kroku 5, je pojmenována `FormRegion1` , změňte všechny odkazy `FormRegion1` na `SalesDataFormRegion` .

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Aktualizace generovaného kódu pro oblast formuláře, kterou jste importovali z Outlooku

1. V editoru kódu otevřete soubor kódu na pozadí oblasti formuláře. Tento soubor má název *YourFormRegion*. Designer.cs nebo *YourFormRegion*. Designer. vb. Pokud chcete tento soubor zobrazit v Visual Basic projekty, klikněte na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení**.

2. Upravte deklaraci třídy region formuláře tak, aby byla odvozena z <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> místo `Microsoft.Office.Tools.Outlook.ImportedFormRegion` .

3. Upravte konstruktor třídy region formuláře, jak je znázorněno v následujících příkladech kódu.

     Následující příklad kódu ukazuje konstruktor třídy region formuláře v projektu, který cílí na .NET Framework 3,5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

     Následující příklad kódu ukazuje signaturu konstruktoru třídy oblasti formuláře v projektu, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

4. Pro každý řádek kódu v `InitializeControls` metodě, která inicializuje ovládací prvek ve třídě region formuláře, upravte kód, jak je znázorněno níže.

     Následující příklad kódu ukazuje, jak inicializovat ovládací prvek v projektu, který cílí na .NET Framework 3,5. V tomto kódu `GetFormRegionControl` má metoda parametr typu, který určuje typ vráceného ovládacího prvku.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     Následující příklad kódu ukazuje, jak inicializovat ovládací prvek v projektu, který cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . V tomto kódu metoda nemá <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> parametr typu. Vrácenou hodnotu je nutné přetypovat na typ ovládacího prvku, který inicializujete.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Přidejte do projektu novou položku oblasti formuláře Outlooku. Otevřete soubor kódu na pozadí pro novou oblast formuláře, vyhledejte *YourNewFormRegion* `Factory` a `WindowFormRegionCollection` třídy v souboru a zkopírujte tyto třídy do schránky.

6. Odstraňte novou oblast formuláře, kterou jste přidali do projektu.

7. V souboru kódu na pozadí oblasti formuláře, kterou aktualizujete, aby fungovala v přecíleném projektu, vyhledejte *YourOriginalFormRegion* `Factory` a `WindowFormRegionCollection` třídy a nahraďte je kódem, který jste zkopírovali z nové oblasti formuláře.

8. V *YourNewFormRegion* `Factory` a `WindowFormRegionCollection` třídách vyhledejte všechny odkazy na třídu *YourNewFormRegion* a místo toho změňte každý odkaz na třídu *YourOriginalFormRegion* . Pokud je například oblast formuláře, kterou aktualizujete, pojmenována `SalesDataFormRegion` a nová oblast formuláře, kterou jste vytvořili v kroku 5, je pojmenována `FormRegion1` , změňte všechny odkazy `FormRegion1` na `SalesDataFormRegion` .

## <a name="instantiate-form-region-classes"></a>Instance tříd oblastí formuláře
 Je nutné upravit kód, který dynamicky vytváří instance určitých tříd oblastí formuláře. V projektech, které cílí na .NET Framework 3,5, můžete vytvářet instance tříd oblastí formuláře, například `Microsoft.Office.Tools.Outlook.FormRegionManifest` přímo. V projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, jsou tyto třídy rozhraní, které nelze vytvořit přímo.

 Pokud je cílová architektura projektu změněna na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné vytvořit instanci rozhraní pomocí metod, které jsou poskytnuty `Globals.Factory` vlastností. Další informace o této `Globals.Factory` vlastnosti najdete v tématu [globální přístup k objektům v projektech Office](../vsto/global-access-to-objects-in-office-projects.md).

 V následující tabulce jsou uvedeny typy oblastí formuláře a metoda, která má být použita k vytvoření instance typů v projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.

|Typ|Metoda továrního použití|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Viz také
- [Migrace řešení Office na .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
