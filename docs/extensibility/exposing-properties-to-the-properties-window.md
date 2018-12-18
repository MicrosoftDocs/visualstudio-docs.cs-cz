---
title: Vystavení vlastností v okně Vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a37dcac9d75cbd773894b3d708dd4931f77b4ce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888408"
---
# <a name="expose-properties-to-the-properties-window"></a>Vystavení vlastností v okně Vlastnosti
Tento návod poskytuje veřejné vlastnosti objektu **vlastnosti** okna. Změny provedené pro tyto vlastnosti se projeví v **vlastnosti** okna.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="expose-properties-to-the-properties-window"></a>Vystavení vlastností v okně Vlastnosti  
 V této části vytvoříte vlastního okna nástroje a veřejné vlastnosti objektu podokno související okna v zobrazení **vlastnosti** okna.  
  
### <a name="to-expose-properties-to-the-properties-window"></a>K vystavení vlastností v okně Vlastnosti  
  
1. Každé rozšíření sady Visual Studio spustí nasazení projektu VSIX, který bude obsahovat rozšíření prostředků. Vytvoření [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projekt s názvem `MyObjectPropertiesExtension`. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C#** > **rozšiřitelnost**.  
  
2. Přidání panelu nástrojů přidejte šablonu vlastního panelu nástrojů položku s názvem `MyToolWindow`. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka**. V **dialogového okna Přidat novou položku**, přejděte na stránku **položky Visual C#** > **rozšiřitelnost** a vyberte **vlastního panelu nástrojů**. V **název** pole v dolní části dialogového okna, změňte název souboru, aby *MyToolWindow.cs*. Další informace o tom, jak vytvořit vlastního okna nástroje najdete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Otevřít *MyToolWindow.cs* a přidejte následující příkaz using:  
  
   ```csharp  
   using System.Collections;  
   using System.ComponentModel;  
   using Microsoft.VisualStudio.Shell.Interop;  
   ```  
  
4. Nyní přidejte následující pole na `MyToolWindow` třídy.  
  
   ```csharp  
   private ITrackSelection trackSel;  
   private SelectionContainer selContainer;  
  
   ```  
  
5. Přidejte následující kód, který `MyToolWindow` třídy.  
  
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
  
    `TrackSelection` Používá vlastnost `GetService` získat `STrackSelection` službu, která poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> rozhraní. `OnToolWindowCreated` Obslužné rutiny události a `SelectList` metoda společně vytvoření seznamu vybrané objekty, který obsahuje pouze nástroj okno podokna samotného objektu. `UpdateSelection` Metoda říká **vlastnosti** okno k zobrazení veřejné vlastnosti podokno okna nástrojů.  
  
6. Sestavte projekt a spusťte ladění. Experimentální instanci sady Visual Studio by se zobrazit.  
  
7. Pokud **vlastnosti** okno se nezobrazuje, otevřete ho stisknutím kombinace kláves **F4**.  
  
8. Otevřít **MyToolWindow** okna. Najdete ho v **zobrazení** > **ostatní Windows**.  
  
    Otevře se okno a veřejné vlastnosti podokno okna se zobrazí v **vlastnosti** okna.  
  
9. Změnit **titulek** vlastnost v **vlastnosti** okno **vlastnosti mého objekt**.  
  
     Titulek okna MyToolWindow příslušným způsobem mění.  
  
## <a name="expose-tool-window-properties"></a>Vystavení vlastností okna nástroje  
 V této části přidáte panelu nástrojů a zobrazit její vlastnosti. Změny provedené na vlastnosti se projeví v **vlastnosti** okna.  
  
### <a name="to-expose-tool-window-properties"></a>Vystavení vlastností okna nástroje  
  
1.  Otevřít *MyToolWindow.cs*, a přidejte veřejnou logickou vlastnost IsChecked k `MyToolWindow` třídy.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Tato vlastnost získá stavu od zaškrtávacího políčka WPF, kterou vytvoříte později.  
  
2.  Otevřít *MyToolWindowControl.xaml.cs* a konstruktoru MyToolWindowControl nahraďte následujícím kódem.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Díky tomu `MyToolWindowControl` přístup k `MyToolWindow` podokně.  
  
3.  V *MyToolWindow.cs*, změnit `MyToolWindow` konstruktor následujícím způsobem:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Přejděte do zobrazení návrhu MyToolWindowControl.  
  
5.  Tlačítko Odstranit a přidáte zaškrtávací políčko z **nástrojů** do levého horního rohu.  
  
6.  Přidání událostí zaškrtnuto a nezaškrtnuto. Zaškrtněte políčko v návrhovém zobrazení. V **vlastnosti** okna, klikněte na tlačítko obslužné rutiny události (v horní části vpravo **vlastnosti** okno). Najít **Checked** a typ **checkbox_Checked** v textovém poli vyhledejte **Unchecked** a typ **checkbox_Unchecked** v textovém poli.  
  
7.  Přidejte obslužné rutiny událostí zaškrtávací políčko:  
  
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
  
8.  Sestavte projekt a spusťte ladění.  
  
9. V experimentální instanci aplikace, otevřete **MyToolWindow** okna.  
  
     Hledat v okně Vlastnosti **vlastnosti** okna. **IsChecked** vlastnost se zobrazí v dolní části okna, v části **vlastnosti mého** kategorie.  
  
10. Zaškrtněte políčko **MyToolWindow** okna. **IsChecked** v **vlastnosti** okno se změní na **True**. Zrušte zaškrtnutí políčka v **MyToolWindow** okna. **IsChecked** v **vlastnosti** okno se změní na **False**. Změňte hodnotu vlastnosti **IsChecked** v **vlastnosti** okna. Zaškrtněte políčko v **MyToolWindow** okna změny tak, aby odpovídala nové hodnoty.  
  
    > [!NOTE]
    >  Pokud musíte uvolnění objektu, který se zobrazí v **vlastnosti** okna, volání `OnSelectChange` s `null` zásobník pro výběr první. Po uvolnění vlastnost nebo objekt, můžete změnit na zásobník pro výběr, která se aktualizovala <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> a <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> seznamy.  
  
## <a name="change-selection-lists"></a>Změnit seznamy výběru  
 V této části můžete přidat seznam výběru pro vlastnost základní třídy a používat rozhraní okna nástroje rozhodnout, které seznamu výběru zobrazit.  
  
### <a name="to-change-selection-lists"></a>Chcete-li změnit seznam výběru  
  
1.  Otevřít *MyToolWindow.cs* a přidejte veřejnou třídu s názvem `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
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
  
2.  Přidat `SimpleObject` vlastnost `MyToolWindow` třídy. navíc dvě metody pro přepnutí **vlastnosti** okno Výběr mezi podokno okna a `Simple` objektu.  
  
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
  
3.  V *MyToolWindowControl.cs*, nahraďte tyto řádky kódu obslužné rutiny zaškrtávací políčko:  
  
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
  
4.  Sestavte projekt a spusťte ladění.  
  
5.  V experimentální instanci aplikace, otevřete **MyToolWindow** okna.  
  
6.  Zaškrtněte políčko v **MyToolWindow** okna. **Vlastnosti** v okně se zobrazí `Simple` vlastnosti, objektu **SomeText** a **jen pro čtení**. Zrušte zaškrtnutí políčka. Veřejné vlastnosti v okně se zobrazí v **vlastnosti** okna.  
  
    > [!NOTE]
    >  Zobrazovaný název **SomeText** je **tento Text**.  
  
## <a name="best-practice"></a>Osvědčený postup  
 V tomto názorném postupu <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> je implementováno tak, že kolekce volitelných objektu a kolekce vybraných objektů jsou stejné kolekce. V prohlížeči vlastností seznamu se zobrazí pouze vybraný objekt. Úplnější ISelectionContainer implementaci najdete v ukázkách Reference.ToolWindow.  
  
 Okna nástrojů Visual Studio zachována i mezi relacemi aplikace Visual Studio. Další informace o zachování stav okna nástroje, najdete v části <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Viz také:  
 [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)