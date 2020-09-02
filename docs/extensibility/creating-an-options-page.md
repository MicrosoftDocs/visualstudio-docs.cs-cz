---
title: Vytváření stránky možností | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be826b73e28a73216ea88ceba8e23eb1e9ea457b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903819"
---
# <a name="create-an-options-page"></a>Vytvoření stránky možnosti

Tento návod vytvoří jednoduchou stránku nástrojů/možností, která používá mřížku vlastností k prohlédnutí a nastavení vlastností.

 Pokud chcete tyto vlastnosti Uložit do souboru nastavení a obnovit je, postupujte podle těchto kroků a pak se podívejte na téma [Vytvoření kategorie nastavení](../extensibility/creating-a-settings-category.md).

 Parametr MPF poskytuje dvě třídy, které vám pomůžou vytvořit stránky možností nástrojů, <xref:Microsoft.VisualStudio.Shell.Package> třídu a <xref:Microsoft.VisualStudio.Shell.DialogPage> třídu. Vytvoříte VSPackage pro poskytnutí kontejneru pro tyto stránky podtřídou `Package` třídy. Můžete vytvořit každou stránku možností nástrojů odvozením z `DialogPage` třídy.

## <a name="prerequisites"></a>Předpoklady

 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Vytvoření stránky s mřížkou možností nástrojů

 V této části vytvoříte jednoduchou mřížku vlastností možností nástroje. Tuto mřížku použijete k zobrazení a změně hodnoty vlastnosti.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Chcete-li vytvořit projekt VSIX a přidat VSPackage

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `MyToolsOptionsExtension` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** hledáním "VSIX".

2. Přidejte VSPackage přidáním šablony položky balíčku sady Visual Studio s názvem `MyToolsOptionsPackage` . V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V **dialogovém okně Přidat novou položku**přejít na rozšiřitelnost **položek Visual C#**  >  **Extensibility** a vybrat **balíček sady Visual Studio**. V poli **název** v dolní části dialogového okna změňte název souboru na `MyToolsOptionsPackage.cs` . Další informace o tom, jak vytvořit VSPackage, najdete v tématu [Vytvoření rozšíření pomocí sady VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Vytvoření tabulky vlastností možnosti nástrojů

1. Otevřete soubor *MyToolsOptionsPackage* v editoru kódu.

2. Přidejte následující příkaz using.

   ```csharp
   using System.ComponentModel;
   ```

3. Deklarovat `OptionPageGrid` třídu a odvodit z ní <xref:Microsoft.VisualStudio.Shell.DialogPage>

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Použijte <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pro třídu, `VSPackage` která se přiřadí ke třídě a kategorii možností a název stránky možností pro OptionPageGrid. Výsledek by měl vypadat takto:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Přidejte `OptionInteger` vlastnost do `OptionPageGrid` třídy.

    - Použijte <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> pro přiřazení k vlastnosti kategorie mřížky vlastností.

    - Použijte <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> pro přiřazení k vlastnosti název.

    - Použijte <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> pro přiřazení k vlastnosti Popis.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > Výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage> podporuje vlastnosti, které mají odpovídající převaděče nebo jsou struktury nebo pole, která lze rozšířit na vlastnosti, které mají odpovídající převaděče. Seznam převaděčů naleznete v tématu <xref:System.ComponentModel> obor názvů.

6. Sestavte projekt a spusťte ladění.

7. V experimentální instanci aplikace Visual Studio klikněte v nabídce **nástroje** na **Možnosti**.

     V levém podokně byste měli vidět **Moje kategorie**. (Kategorie možností jsou uvedeny v abecedním pořadí, takže by se měla objevit přibližně uprostřed seznamu.) Otevřete **kategorii Moje kategorie** a potom klikněte na možnost **Stránka mřížka**. V pravém podokně se zobrazí mřížka možnosti. Kategorie vlastností je **Moje možnosti**a název vlastnosti je **Moje celočíselná možnost**. Popis vlastnosti, **možnost mé celé číslo**, se zobrazí v dolní části podokna. Změňte hodnotu z počáteční hodnoty 256 na něco jiného. Klikněte na tlačítko **OK**a potom znovu otevřete **stránku mřížka**. Uvidíte, že nová hodnota přetrvává.

     Vaše stránka možnosti je také k dispozici prostřednictvím vyhledávacího pole sady Visual Studio. Do vyhledávacího pole v horní části rozhraní IDE zadejte **Moje kategorie** a zobrazí se **Stránka moje kategorie – > mřížka** uvedená ve výsledcích.

## <a name="create-a-tools-options-custom-page"></a>Vytvoření vlastní stránky možností nástrojů

 V této části vytvoříte stránku možností nástroje s vlastním uživatelským rozhraním. Tato stránka slouží k zobrazení a změně hodnoty vlastnosti.

1. Otevřete soubor *MyToolsOptionsPackage* v editoru kódu.

2. Přidejte následující příkaz using.

    ```csharp
    using System.Windows.Forms;
    ```

3. Přidejte `OptionPageCustom` třídu těsně před `OptionPageGrid` třídu. Odvodit novou třídu z `DialogPage` .

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. Přidejte atribut GUID. Přidat vlastnost OptionString:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. Použijte sekundu <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> pro třídu VSPackage. Tento atribut přiřadí třídu a možnosti kategorie a možnosti název stránky.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Přidejte do projektu nový **uživatelský ovládací prvek** s názvem MyUserControl.

7. Přidejte ovládací prvek **TextBox** do uživatelského ovládacího prvku.

     V okně **vlastnosti** klikněte na panelu nástrojů na tlačítko **události** a potom poklikejte na událost **opuštění** . Nová obslužná rutina události se zobrazí v kódu *MyUserControl.cs* .

8. Přidejte veřejné `OptionsPage` pole, `Initialize` metodu do třídy ovládacího prvku a aktualizujte obslužnou rutinu události tak, aby se hodnota možnosti nastavila na obsah textového pole:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     `optionsPage`Pole obsahuje odkaz na nadřazenou `OptionPageCustom` instanci. `Initialize`Metoda se zobrazí `OptionString` v **textovém**poli. Obslužná rutina události zapíše aktuální hodnotu **textového pole** do pole `OptionString` když fokus opustí **textové pole**.

9. V souboru s kódem balíčku přidejte přepsání pro `OptionPageCustom.Window` vlastnost do `OptionPageCustom` třídy pro vytvoření, inicializaci a vrácení instance `MyUserControl` . Třída by teď měla vypadat takto:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Sestavte a spusťte projekt.

11. V experimentální instanci klikněte na možnost **nástroje**  >  **Options**.

12. Najde **moji kategorii** a pak **moji vlastní stránku**.

13. Změňte hodnotu **OptionString**. Klikněte na **OK**a pak znovu otevřete **moji vlastní stránku**. Můžete vidět, že nová hodnota je trvalá.

## <a name="access-options"></a>Možnosti přístupu

 V této části získáte hodnotu možnosti ze sady VSPackage, která je hostitelem stránky možnosti přidružených nástrojů. Stejnou techniku lze použít k získání hodnoty libovolné veřejné vlastnosti.

1. V souboru s kódem balíčku přidejte veřejnou vlastnost s názvem **OptionInteger** do třídy **MyToolsOptionsPackage** .

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Tento kód volá <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Vytvoření nebo načtení `OptionPageGrid` instance. `OptionPageGrid` volá <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> načtení jeho možností, což jsou veřejné vlastnosti.

2. Nyní k zobrazení hodnoty přidejte šablonu vlastní položky příkazu s názvem **MyToolsOptionsCommand** . V dialogovém okně **Přidat novou položku** , přejít na rozšiřitelnost v **jazyce Visual C#**  >  **Extensibility** a vybrat **vlastní příkaz**. V poli **název** v dolní části okna změňte název souboru příkazů na *MyToolsOptionsCommand.cs*.

3. V souboru *MyToolsOptionsCommand* nahraďte tělo `ShowMessageBox` metody příkazu následujícím způsobem:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Sestavte projekt a spusťte ladění.

5. V experimentální instanci v nabídce **nástroje** klikněte na **vyvolat MyToolsOptionsCommand**.

     V okně se zprávou se zobrazuje aktuální hodnota `OptionInteger` .

## <a name="see-also"></a>Viz také

- [Stránky možností a možností](../extensibility/internals/options-and-options-pages.md)
