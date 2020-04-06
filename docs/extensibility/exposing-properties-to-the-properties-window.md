---
title: Vystavení vlastností oknu Vlastnosti | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711831"
---
# <a name="expose-properties-to-the-properties-window"></a>Vystavit vlastnosti oknu Vlastnosti

Tento návod zpřístupňuje veřejné vlastnosti objektu do okna **Vlastnosti.** Změny provedené v těchto vlastnostech se projeví v okně **Vlastnosti.**

## <a name="prerequisites"></a>Požadavky

Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Vystavit vlastnosti oknu Vlastnosti

V této části vytvoříte vlastní okno nástroje a zobrazíte veřejné vlastnosti přidruženého objektu podokna okna v okně **Vlastnosti.**

### <a name="to-expose-properties-to-the-properties-window"></a>Zpřístupnění vlastností oknu Vlastnosti

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `MyObjectPropertiesExtension`. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Přidejte okno nástroje přidáním vlastní šablony `MyToolWindow`položky okna nástroje s názvem . V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V **dialogovém okně Přidat novou položku**přejděte do části**Rozšiřitelnost** **položek** > Visual C# a vyberte vlastní okno **nástroje**. V poli **Název** v dolní části dialogového okna změňte název souboru na *MyToolWindow.cs*. Další informace o vytvoření vlastního okna nástroje naleznete v [tématu Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Otevřete *MyToolWindow.cs* a přidejte následující příkaz using:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Nyní přidejte do `MyToolWindow` třídy následující pole.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Přidejte následující kód `MyToolWindow` do třídy.

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

    Vlastnost `TrackSelection` používá `GetService` k `STrackSelection` získání služby, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> která poskytuje rozhraní. Obslužná rutina `OnToolWindowCreated` události a `SelectList` metoda společně vytvářejí seznam vybraných objektů, který obsahuje pouze samotný objekt panelu okna nástroje. Metoda `UpdateSelection` říká **okno Vlastnosti** k zobrazení veřejných vlastností podokna okna nástroje.

6. Sestavení projektu a začít ladění. Experimentální instance sady Visual Studio by se měla zobrazit.

7. Pokud okno **Vlastnosti** není viditelné, otevřete ho stisknutím **klávesy F4**.

8. Otevřete okno **MyToolWindow.** Najdete ji v **zobrazit** > **další windows**.

    Otevře se okno a veřejné vlastnosti podokna okna se zobrazí v okně **Vlastnosti.**

9. Změňte vlastnost **Caption** v okně **Vlastnosti** na **Vlastnosti objektu**.

     MyToolWindow okno titulek změní odpovídajícím způsobem.

## <a name="expose-tool-window-properties"></a>Vystavit vlastnosti okna nástroje

V této části přidáte okno nástroje a vystavit jeho vlastnosti. Změny, které provedete ve vlastnostech, se projeví v okně **Vlastnosti.**

### <a name="to-expose-tool-window-properties"></a>Vystavení vlastností okna nástroje

1. Otevřete *MyToolWindow.cs*a přidejte veřejnou logickou `MyToolWindow` vlastnost IsChecked do třídy.

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

     Tato vlastnost získá svůj stav ze zaškrtávacího políčka WPF, které vytvoříte později.

2. Otevřete *MyToolWindowControl.xaml.cs* a nahraďte konstruktor MyToolWindowControl následujícím kódem.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     To `MyToolWindowControl` umožňuje přístup `MyToolWindow` k podokně.

3. V *MyToolWindow.cs*změňte `MyToolWindow` konstruktor takto:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Změňte na zobrazení návrhu MyToolWindowControl.

5. Odstraňte tlačítko a přidejte zaškrtávací políčko z **panelu nástrojů** do levého horního rohu.

6. Přidejte zaškrtnuté a nezaškrtnuté události. Zaškrtněte políčko v návrhovém zobrazení. V okně **Vlastnosti** klikněte na tlačítko obslužné rutiny události (v pravém horním rohu okna **Vlastnosti).** Najděte **Zaškrtnuto** a zadejte **checkbox_Checked** do textového pole, pak najděte **Nezaškrtnuté** a zadejte **checkbox_Unchecked** do textového pole.

7. Přidejte obslužné rutiny událostí zaškrtávacího políčka:

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

8. Sestavení projektu a začít ladění.

9. V experimentální instanci otevřete okno **MyToolWindow.**

     Vyhledejte vlastnosti okna v okně **Vlastnosti.** Vlastnost **IsChecked** se zobrazí v dolní části okna v kategorii **Moje vlastnosti.**

10. Zaškrtněte políčko v okně **MyToolWindow.** **IsChecked** v okně **Vlastnosti** se změní na **True**. Zrušte zaškrtnutí políčka v okně **MyToolWindow.** **IsChecked** v okně **Vlastnosti** se změní na **False**. Změňte hodnotu **IsChecked** v okně **Vlastnosti.** Zaškrtávací políčko v okně **MyToolWindow** se změní tak, aby odpovídalo nové hodnotě.

    > [!NOTE]
    > Pokud je nutné vyřadit objekt, který je `OnSelectChange` zobrazen `null` v okně **Vlastnosti,** nejprve volejte s kontejnerem výběru. Po likvidaci vlastnosti nebo objektu můžete změnit na <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> kontejner <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> výběru, který byl aktualizován a seznamy.

## <a name="change-selection-lists"></a>Změna výběrových seznamů

 V této části přidáte seznam výběru pro základní třídu vlastností a pomocí rozhraní okna nástroje zvolte, který seznam výběru se má zobrazit.

### <a name="to-change-selection-lists"></a>Změna výběrových seznamů

1. Otevřete *MyToolWindow.cs* a přidejte veřejnou třídu s názvem `Simple`.

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

2. Přidejte `SimpleObject` vlastnost `MyToolWindow` do třídy a dvě metody pro přepnutí `Simple` výběru okna **Vlastnosti** mezi podoknem okna a objektem.

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

4. Sestavení projektu a začít ladění.

5. V experimentální instanci otevřete okno **MyToolWindow.**

6. Zaškrtněte políčko v okně **MyToolWindow.** V okně **Vlastnosti** se zobrazí vlastnosti objektu `Simple` **SomeText** a **ReadOnly**. Zrušte zaškrtnutí políčka. Veřejné vlastnosti okna se zobrazí v okně **Vlastnosti.**

    > [!NOTE]
    > Zobrazovaný název **SomeText** je **Můj text**.

## <a name="best-practice"></a>Osvědčený postup

V tomto návodu je implementována tak, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> aby kolekce volitelných objektů a kolekce vybraných objektů byly stejné kolekce. V seznamu Prohlížeče vlastností se zobrazí pouze vybraný objekt. Pro úplnější implementaci ISelectionContainer, naleznete reference.ToolWindow ukázky.

Okna nástrojů sady Visual Studio přetrvávají mezi relacemi sady Visual Studio. Další informace o zachování stavu okna <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>nástroje naleznete v tématu .

## <a name="see-also"></a>Viz také

- [Rozšířit vlastnosti a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)
