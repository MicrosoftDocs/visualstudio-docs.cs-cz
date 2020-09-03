---
title: Vystavení vlastností oknu vlastností | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711831"
---
# <a name="expose-properties-to-the-properties-window"></a>Vystavení vlastností okno Vlastnosti

Tento návod zveřejňuje veřejné vlastnosti objektu v okně **vlastnosti** . Změny, které provedete u těchto vlastností, se projeví v okně **vlastnosti** .

## <a name="prerequisites"></a>Předpoklady

Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Vystavení vlastností okno Vlastnosti

V této části vytvoříte vlastní okno nástrojů a zobrazíte veřejné vlastnosti objektu přidruženého podokna okna v okně **vlastnosti** .

### <a name="to-expose-properties-to-the-properties-window"></a>Vystavení vlastností okno Vlastnosti

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `MyObjectPropertiesExtension` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** hledáním "VSIX".

2. Přidejte okno nástroje přidáním vlastní šablony položky okna nástroje s názvem `MyToolWindow` . V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V **dialogovém okně Přidat novou položku**, přejít na rozšiřitelnost **položek Visual C#**  >  **Extensibility** a vybrat **vlastní panel nástrojů**. V poli **název** v dolní části dialogového okna změňte název souboru na *MyToolWindow.cs*. Další informace o tom, jak vytvořit vlastní panel nástrojů, najdete v tématu [Vytvoření rozšíření s oknem nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Otevřete *MyToolWindow.cs* a přidejte následující příkaz using:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Nyní do třídy přidejte následující pole `MyToolWindow` .

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Do třídy přidejte následující kód `MyToolWindow` .

   ```csharp
   private ITrackSelection TrackSelection
   {
       get
       {
           if (trackSel == null)
               trackSel =
                  GetService(typeof(STrackSelection)) as ITrackSelection;
           return trackSel;
       }
   }

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    Tato `TrackSelection` vlastnost používá `GetService` k získání `STrackSelection` služby, která poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> rozhraní. `OnToolWindowCreated`Obslužná rutina a `SelectList` Metoda události společně vytvoří seznam vybraných objektů, které obsahují pouze samotný objekt podokna nástrojů. `UpdateSelection`Metoda instruuje okno **vlastnosti** , aby zobrazil veřejné vlastnosti podokna okna nástroje.

6. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance sady Visual Studio.

7. Pokud se okno **vlastnosti** nezobrazí, otevřete ho stisknutím klávesy **F4**.

8. Otevřete okno **MyToolWindow** . Můžete ji najít v **zobrazení**  >  **jiných oken**.

    Otevře se okno a zobrazí se veřejné vlastnosti podokna okna v okně **vlastnosti** .

9. V okně **vlastnosti** změňte vlastnost **Titulek** na **Moje vlastnosti objektu**.

     Titulek okna MyToolWindow se odpovídajícím způsobem změní.

## <a name="expose-tool-window-properties"></a>Vystavení vlastností okna nástroje

V této části přidáte okno nástroje a zpřístupníte jeho vlastnosti. Změny, které provedete ve vlastnostech, se projeví v okně **vlastnosti** .

### <a name="to-expose-tool-window-properties"></a>Vystavení vlastností okna nástroje

1. Otevřete *MyToolWindow.cs*a přidejte vlastnost Public Boolean-Checked do `MyToolWindow` třídy.

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     Tato vlastnost získá svůj stav z zaškrtávacího políčka WPF, které budete vytvářet později.

2. Otevřete *MyToolWindowControl.XAML.cs* a nahraďte konstruktor MyToolWindowControl následujícím kódem.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Tím získáte `MyToolWindowControl` přístup k `MyToolWindow` podoknu.

3. V *MyToolWindow.cs*změňte `MyToolWindow` konstruktor následujícím způsobem:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Přejděte do návrhového zobrazení MyToolWindowControl.

5. Odstraňte tlačítko a přidejte zaškrtávací políčko ze **sady nástrojů** do levého horního rohu.

6. Přidejte kontrolované a nezaškrtnuté události. Zaškrtněte políčko v návrhovém zobrazení. V okně **vlastnosti** klikněte na tlačítko obslužné rutiny události (v pravém horním rohu okna **vlastnosti** ). V textovém poli vyhledejte **zaškrtnuté** políčko a zadejte **checkbox_Checked** a potom v textovém poli Najděte **checkbox_Unchecked** typu bez **zaškrtnutí** .

7. Přidejte obslužné rutiny události zaškrtávacího políčka:

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = true;
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.UpdateSelection();
    }
    ```

8. Sestavte projekt a spusťte ladění.

9. V experimentální instanci otevřete okno **MyToolWindow** .

     V okně **vlastnosti** vyhledejte vlastnosti okna. Vlastnost **nezaškrtnutou** se zobrazí v dolní části okna v kategorii **Moje vlastnosti** .

10. Zaškrtněte políčko v okně **MyToolWindow** . **V okně** **vlastnosti** se změní na **true**. Zrušte zaškrtnutí políčka v okně **MyToolWindow** . **V okně** **vlastnosti** se změní na **false**. V okně **vlastnosti** změňte hodnotu je **zaškrtnuto** . Zaškrtávací políčko v okně **MyToolWindow** se změní tak, aby odpovídalo nové hodnotě.

    > [!NOTE]
    > Pokud je nutné uvolnit objekt, který je zobrazen v okně **vlastnosti** , zavolejte `OnSelectChange` `null` nejprve pomocí kontejneru výběru. Po likvidaci vlastnosti nebo objektu můžete přejít na kontejner výběru, který obsahuje seznam aktualizovaných <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> a <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> seznamů.

## <a name="change-selection-lists"></a>Změnit seznamy pro výběr

 V této části přidáte seznam výběru pro základní třídu vlastností a pomocí rozhraní okna nástroje vyberete seznam výběru, který chcete zobrazit.

### <a name="to-change-selection-lists"></a>Změna seznamů pro výběr

1. Otevřete *MyToolWindow.cs* a přidejte veřejnou třídu s názvem `Simple` .

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
        {
            get { return someText; }
            set { someText = value; }
        }

        [Category("My Properties")]
        [Description("Read-only property")]
        public bool ReadOnly
        {
            get { return false; }
        }
    }
    ```

2. Přidejte `SimpleObject` vlastnost do třídy a `MyToolWindow` dvě metody pro přepnutí výběru okna **vlastností** mezi oknem okna a `Simple` objektem.

    ```csharp
    private Simple simpleObject = null;
    public Simple SimpleObject
    {
        get
        {
            if (simpleObject == null) simpleObject = new Simple();
            return simpleObject;
        }
    }

    public void SelectSimpleList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(SimpleObject);
        SelectList(listObjects);
    }

    public void SelectThisList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(this);
        SelectList(listObjects);
    }
    ```

3. V *MyToolWindowControl.cs*nahraďte obslužné rutiny zaškrtávacího políčka těmito řádky kódu:

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
     {
        pane.IsChecked = true;
        pane.SelectSimpleList();
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.SelectThisList();
        pane.UpdateSelection();
    }
    ```

4. Sestavte projekt a spusťte ladění.

5. V experimentální instanci otevřete okno **MyToolWindow** .

6. Zaškrtněte políčko v okně **MyToolWindow** . V okně **vlastnosti** se zobrazí `Simple` vlastnosti objektu **SomeText** a **ReadOnly**. Zrušte zaškrtnutí tohoto políčka. Veřejné vlastnosti okna se zobrazí v okně **vlastnosti** .

    > [!NOTE]
    > Zobrazovaný název **SomeText** je **můj text**.

## <a name="best-practice"></a>Osvědčený postup

V tomto návodu <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> je implementováno, aby kolekce volitelných objektů a vybraná kolekce objektů byly stejné kolekce. V seznamu prohlížeče vlastností se zobrazí pouze vybraný objekt. Úplnější implementaci ISelectionContainer naleznete v tématu Reference. panelu Samples.

Mezi relacemi sady Visual Studio se chovají i okna nástrojů sady Visual Studio. Další informace o zachování stavu okna nástroje naleznete v tématu <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .

## <a name="see-also"></a>Viz také

- [Rozšířené vlastnosti a okno vlastností](../extensibility/extending-properties-and-the-property-window.md)
