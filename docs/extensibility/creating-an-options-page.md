---
title: Vytvoření stránky možností | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739512"
---
# <a name="create-an-options-page"></a>Vytvoření stránky možností

Tento návod vytvoří jednoduchou stránku Nástroje/možnosti, která používá mřížku vlastností ke kontrole a nastavení vlastností.

 Chcete-li tyto vlastnosti uložit do souboru nastavení a obnovit je ze souboru nastavení, postupujte takto a potom v [tématu Vytvoření kategorie nastavení](../extensibility/creating-a-settings-category.md).

 MPF poskytuje dvě třídy, které vám <xref:Microsoft.VisualStudio.Shell.Package> pomohou <xref:Microsoft.VisualStudio.Shell.DialogPage> vytvořit tools možnosti stránky, třídy a třídy. Vytvoření MAJek, který poskytne kontejner pro tyto `Package` stránky podřadnou třídou. Každou stránku možností nástrojů vytvoříte odvozením `DialogPage` z třídy.

## <a name="prerequisites"></a>Požadavky

 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Vytvořit stránku mřížky Možnosti nástroje

 V této části vytvoříte jednoduchou mřížku vlastností Možnosti nástroje. Tato mřížka slouží k zobrazení a změně hodnoty vlastnosti.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Chcete-li vytvořit projekt VSIX a přidat VSPackage

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `MyToolsOptionsExtension`. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Přidejte balíček VSPackage přidáním šablony `MyToolsOptionsPackage`položky balíčku sady Visual Studio s názvem . V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V **dialogovém okně Přidat novou položku**přejděte na položku > **Rozšiřitelnost** **položek visual c#** a vyberte **balíček sady Visual Studio**. V poli **Název** v dolní části dialogového okna `MyToolsOptionsPackage.cs`změňte název souboru na . Další informace o tom, jak vytvořit VSPackage, naleznete v [tématu Vytvoření rozšíření s VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Vytvoření mřížky vlastností Možnosti nástroje

1. Otevřete soubor *MyToolsOptionsPackage* v editoru kódu.

2. Přidejte následující příkaz using.

   ```csharp
   using System.ComponentModel;
   ```

3. Deklarovat `OptionPageGrid` třídu <xref:Microsoft.VisualStudio.Shell.DialogPage>a odvodit ji z .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Použijte <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> a `VSPackage` pro třídu, chcete-li třídě přiřadit kategorii možností a název stránky možností pro OptionPageGrid. Výsledek by měl vypadat takto:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Přidejte `OptionInteger` vlastnost `OptionPageGrid` do třídy.

    - Použijte <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> vlastnost přiřadit k vlastnosti kategorii mřížky vlastností.

    - Použijte <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> a přiřaďte vlastnosti název.

    - Použijte <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> k přiřazení popisu k vlastnosti.

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
    > Výchozí implementace <xref:Microsoft.VisualStudio.Shell.DialogPage> podporuje vlastnosti, které mají příslušné převaděče nebo které jsou struktury nebo pole, které lze rozbalit do vlastností, které mají příslušné převaděče. Seznam převaděčů naleznete <xref:System.ComponentModel> v oboru názvů.

6. Sestavení projektu a začít ladění.

7. V experimentální instanci sady Visual Studio klepněte v nabídce **Nástroje** na **položku Možnosti**.

     V levém podokně by se měla zobrazit **moje kategorie**. (Kategorie možností jsou uvedeny v abecedním pořadí, takže by se měly objevit asi v polovině seznamu.) Otevřete **Moje kategorie** a klikněte na **Stránka mřížky**. Mřížka voleb se zobrazí v pravém podokně. Kategorie vlastností je **Moje možnosti**a název vlastnosti je **Možnost celého čísla**. Popis vlastnosti **Moje celé číslo – možnost**se zobrazí v dolní části podokna. Změňte hodnotu z počáteční hodnoty 256 na něco jiného. Klepněte na tlačítko **OK**a znovu **otevřete stránku Mřížka**. Můžete vidět, že nová hodnota přetrvává.

     Stránka možností je k dispozici také prostřednictvím vyhledávacího pole sady Visual Studio. Do vyhledávacího pole v horní části ide zadejte **Moje kategorie** a ve výsledcích se zobrazí moje **kategorie -> Moje stránka mřížky.**

## <a name="create-a-tools-options-custom-page"></a>Vytvořit vlastní stránku Možnosti nástrojů

 V této části vytvoříte stránku Možnosti nástrojů s vlastním uzem. Tato stránka slouží k zobrazení a změně hodnoty vlastnosti.

1. Otevřete soubor *MyToolsOptionsPackage* v editoru kódu.

2. Přidejte následující příkaz using.

    ```csharp
    using System.Windows.Forms;
    ```

3. Přidejte `OptionPageCustom` třídu těsně `OptionPageGrid` před třídu. Odvodit `DialogPage`novou třídu z .

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

4. Přidejte atribut GUID. Přidejte vlastnost OptionString:

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

5. Použijte sekundu <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> na třídu VSPackage. Tento atribut přiřadí třídě kategorii možností a název stránky možností.

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

     V okně **Vlastnosti** klikněte na panelu nástrojů na tlačítko **Události** a potom poklepejte na událost **Leave.** Nová obslužná rutina události se zobrazí v *kódu MyUserControl.cs.*

8. Přidejte `OptionsPage` veřejné pole, metodu `Initialize` do třídy ovládacího prvku a aktualizujte obslužnou rutinu události a nastavte hodnotu možnosti pro obsah textového pole:

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

     Pole `optionsPage` obsahuje odkaz na `OptionPageCustom` nadřazenou instanci. Metoda `Initialize` se `OptionString` zobrazí v **textovém poli**. Obslužná rutina události zapíše `OptionString` aktuální hodnotu **textboxu** do pole, ve které fokus opustí **textbox**.

9. V souboru kódu balíčku přidejte `OptionPageCustom.Window` do `OptionPageCustom` třídy přepsání vlastnosti, chcete-li `MyUserControl`vytvořit, inicializovat a vrátit instanci aplikace . Třída by nyní měla vypadat takto:

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

10. Sestavení a spuštění projektu.

11. V experimentální instanci klepněte na **položku Možnosti nástrojů** > **Options**.

12. Najít **kategorii** moje a pak **moje vlastní stránka**.

13. Změňte hodnotu **OptionString**. Klepněte na tlačítko **OK**a znovu **otevřete moji vlastní stránku**. Můžete vidět, že nová hodnota přetrvává.

## <a name="access-options"></a>Možnosti přístupu

 V této části získáte hodnotu možnosti z Balíčku VSPackage, který je hostitelem přidružené stránky Možnosti nástrojů. Stejnou techniku lze použít k získání hodnoty jakéhokoli veřejného majetku.

1. V souboru kódu balíčku přidejte do třídy **MyToolsOptionsPackage** veřejnou vlastnost nazvanou **OptionInteger.**

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

     Tento kód <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> volá k `OptionPageGrid` vytvoření nebo načtení instance. `OptionPageGrid`volá <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> načíst jeho možnosti, které jsou veřejné vlastnosti.

2. Nyní přidejte vlastní šablonu položky příkazu s názvem **MyToolsOptionsCommand** pro zobrazení hodnoty. V dialogovém okně **Přidat novou položku** přejděte na položku**Rozšiřitelnost** **jazyka Visual C#** > a vyberte **vlastní příkaz**. V poli **Název** v dolní části okna změňte název příkazového souboru na *MyToolsOptionsCommand.cs*.

3. V souboru *MyToolsOptionsCommand* nahraďte tělo `ShowMessageBox` metody příkazu následujícím:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Sestavení projektu a začít ladění.

5. V experimentální instanci klepněte v nabídce **Nástroje** na **příkaz Invoke MyToolsOptionsCommand**.

     Okno se zprávou zobrazuje `OptionInteger`aktuální hodnotu .

## <a name="see-also"></a>Viz také

- [Stránky možností a možností](../extensibility/internals/options-and-options-pages.md)
