---
title: 'Průvodce: Vytvoření grafického doplňku zobrazení, příkazů a nastavení (vodítka sloupců) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 501d5c9991aaef090c061e396eaa147dba1f53f1
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348533"
---
# <a name="walkthrough-creating-a-view-adornment-commands-and-settings-column-guides"></a>Průvodce: Vytvoření grafického doplňku zobrazení, příkazů a nastavení (vodítka sloupců)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete rozšířit editoru textu nebo kódu sady Visual Studio s příkazy a zobrazit důsledky. V tomto tématu se dozvíte, jak začít pracovat s funkcí oblíbené rozšíření, vodítka sloupců. Vodítka sloupců jsou vizuálně světla čáry dekorace pro zobrazení textového editoru vám pomohou při správě kód do určitého sloupce šířky. Speciálně formátovaného kódu může být důležité pro ukázky zahrnout do dokumentů, blogy, nebo zpráv o chybách.

V tomto návodu provedete následující:

- Vytvořte projekt VSIX
- Přidat grafického doplňku zobrazení editoru
- Přidání podpory pro ukládání a načítání nastavení (Pokud k vodítka sloupců příkazu pro vykreslení a jejich barva)
- Přidání příkazů (Přidání nebo odebrání vodítka sloupců, změna jejich barvy)
- Umístit příkazy na textový dokument kontextové nabídky a nabídky Upravit
- Přidání podpory pro vyvolávání příkazů v příkazovém okně Visual Studio  
  
  Budete moct vyzkoušet verzi funkce vodítka sloupců s této galerie sady Visual Studio[rozšíření](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).  
  
  **Poznámka:**: v tomto názorném postupu vložte velké množství kódu do několika soubory generované záznamem šablony pro rozšíření sady visual studio, ale brzy bude odkazovat Tento názorný postup dokončené řešení na Githubu s příklady dalších rozšíření. Dokončený kód se mírně liší v tom, že má skutečné příkaz ikony namísto použití generictemplate ikony.

## <a name="getting-started"></a>Začínáme
Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="setting-up-the-solution"></a>Nastavení řešení
Nejprve vytvořte projekt VSIX, přidáte grafického doplňku zobrazení editoru a pak přidejte příkaz (který přidá VSPackage vlastnit příkaz). Základní architektura vypadá takto:

- Máte textové zobrazení vytvořit naslouchací proces, který vytvoří `ColumnGuideAdornment` objektu na zobrazení. Tento objekt naslouchá událostem o změně zobrazení nebo změna nastavení, aktualizace nebo překreslování sloupec provede podle potřeby.
- Je `GuidesSettingsManager` , která zpracovává čtení a zápis z úložiště nastavení sady Visual Studio. Správce nastavení také obsahuje operace pro aktualizaci nastavení, které podporují uživatelských příkazů (Přidat sloupec, odeberte sloupce, změňte barvu).
- Je VSIP balíček, který je nutné v případě, že máte uživatelské příkazy, ale je stejně často používaný kód, který inicializuje objekt implementace příkazy.
- Je `ColumnGuideCommands` deklarovat objekt, který implementuje uživatelských příkazů a připojí do obslužné rutiny příkazů pro příkazy v souboru .vsct.
  
  **VSIX**. Použití **souboru &#124; nové...** příkaz pro vytvoření projektu. V levém navigačním podokně zvolte uzel rozšiřitelnosti v rámci jazyka C# a zvolte **projekt VSIX** v pravém podokně. Zadejte název ColumnGuides a zvolte **OK** pro vytvoření projektu.
  
  **Zobrazení dalších úprav**. Stisknutím tlačítka správný ukazatel myši na uzel projektu v Průzkumníku řešení. Zvolte **přidat &#124; novou položku...** příkaz pro přidání nové položky grafického doplňku zobrazení. Zvolte **rozšiřitelnost &#124; Editor** v levém navigačním podokně a zvolte **grafického doplňku zobrazení editoru** v pravém podokně. Zadejte název ColumnGuideAdornment jako položka název a zvolte **přidat** a přidejte ji.
  
  Uvidíte, že tato šablona položky přidány dva soubory do projektu (stejně jako odkazy a tak dále): ColumnGuideAdornment.cs a ColumnGuideAdornmentTextViewCreationListener.cs. Šablony jenom vykreslení obdélníku fialové pro zobrazení. Níže se změnit několik řádků v naslouchacím procesu vytváření zobrazení a nahraďte jeho obsah ColumnGuideAdornment.cs.
  
  **Příkazy**. Stisknutím tlačítka správný ukazatel myši na uzel projektu v Průzkumníku řešení. Zvolte **přidat &#124; novou položku...** příkaz pro přidání nové položky grafického doplňku zobrazení. Zvolte **rozšiřitelnost &#124; VSPackage** v levém navigačním podokně a zvolte **vlastního příkazu** v pravém podokně. Zadejte název ColumnGuideCommands jako položka název a zvolte **přidat** a přidejte ji. Přidávání příkazů a balíček kromě několik odkazů, přidá ColumnGuideCommands.cs ColumnGuideCommandsPackage.cs a ColumnGuideCommandsPackage.vsct. Níže najdete nahradíte obsah první a poslední soubory musel definovat a implementovat příkazy.

## <a name="setting-up-the-text-view-creation-listener"></a>Nastavení naslouchacího procesu vytváření zobrazení textu
ColumnGuideAdornmentTextViewCreationListener.cs otevře v editoru. Tento kód implementuje obslužné rutiny pro vždy, když sada Visual Studio vytvoří zobrazení textu. Existují atributy, které řídí, kdy je volána obslužnou rutinu v závislosti na charakteristikách zobrazení.

Kód také musí deklarovat vrstvu dalších úprav. Při zobrazení aktualizací editoru, získá vrstvy grafického doplňku zobrazení a z té získá prvky dalších úprav. Je možné deklarovat řazení vrstvě relativně k ostatním s atributy. Nahraďte následující řádek:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

 s těmito dvěma řádky:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Řádek, který jste nahradili nachází v jiné skupině atributů, které deklarují vrstvu dalších úprav.  První řádek jste změnili pouze změny, kde se zobrazí sloupec vodicí čáry. Kreslení čar "před" textem v zobrazení znamená, že se zobrazují před nebo za pod textem. Druhý řádek deklaruje, že vylepšení Průvodce sloupce se vztahují na entity text, odpovídající vaší pojem dokumentu, ale můžete deklarovat dalších úprav, například k fungovat pouze pro upravitelný text. Další informace naleznete v [služba jazyka a editoru Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implementing-the-settings-manager"></a>Implementace nastavení správce
Obsah GuidesSettingsManager.cs nahraďte následujícím kódem (vysvětleno níže):

```csharp
using Microsoft.VisualStudio.Settings;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Settings;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows.Media;

namespace ColumnGuides
{
    internal static class GuidesSettingsManager
    {
        // Because my code is always called from the UI thred, this succeeds.
        internal static SettingsManager VsManagedSettingsManager =
            new ShellSettingsManager(ServiceProvider.GlobalProvider);

        private const int _maxGuides = 5;
        private const string _collectionSettingsName = "Text Editor";
        private const string _settingName = "Guides";
        // 1000 seems reasonable since primary scenario is long lines of code
        private const int _maxColumn = 1000;

        static internal bool AddGuideline(int column)
        {
            if (! IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column",
                    "The paramenter must be between 1 and " + _maxGuides.ToString());
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            if (offsets.Count() >= _maxGuides)
                return false;
            // Check for duplicates
            if (offsets.Contains(column))
                return false;
            offsets.Add(column);
            WriteSettings(GuidesSettingsManager.GuidelinesColor, offsets);
            return true;
        }

        static internal bool RemoveGuideline(int column)
        {
            if (!IsValidColumn(column))
                throw new ArgumentOutOfRangeException(
                    "column", "The paramenter must be between 1 and 10,000");
            var columns = GuidesSettingsManager.GetColumnOffsets();
            if (! columns.Remove(column))
            {
                // Not present. Allow user to remove the last column 
                // even if they're not on the right column.
                if (columns.Count != 1)
                    return false;

                columns.Clear();
            }
            WriteSettings(GuidesSettingsManager.GuidelinesColor, columns);
            return true;
        }

        static internal bool CanAddGuideline(int column)
        {
            if (!IsValidColumn(column))
                return false;
            var offsets = GetColumnOffsets();
            if (offsets.Count >= _maxGuides)
                return false;
            return ! offsets.Contains(column);
        }

        static internal bool CanRemoveGuideline(int column)
        {
            if (! IsValidColumn(column))
                return false;
            // Allow user to remove the last guideline regardless of the column.
            // Okay to call count, we limit the number of guides.
            var offsets = GuidesSettingsManager.GetColumnOffsets();
            return offsets.Contains(column) || offsets.Count() == 1;
        }

        static internal void RemoveAllGuidelines()
        {
            WriteSettings(GuidesSettingsManager.GuidelinesColor, new int[0]);
        }

        private static bool IsValidColumn(int column)
        {
            // zero is allowed (per user request)
            return 0 <= column && column <= _maxColumn;
        }

        // This has format "RGB(<int>, <int>, <int>) <int> <int>...".
        // There can be any number of ints following the RGB part,
        // and each int is a column (char offset into line) where to draw.
        static private string _guidelinesConfiguration;
        static private string GuidelinesConfiguration
        {
            get
            {
                if (_guidelinesConfiguration == null)
                {
                    _guidelinesConfiguration =
                        GetUserSettingsString(
                            GuidesSettingsManager._collectionSettingsName,
                            GuidesSettingsManager._settingName)
                        .Trim();
                }
                return _guidelinesConfiguration;
            }

            set
            {
                if (value != _guidelinesConfiguration)
                {
                    _guidelinesConfiguration = value;
                    WriteUserSettingsString(
                        GuidesSettingsManager._collectionSettingsName,
                        GuidesSettingsManager._settingName, value);
                    // Notify ColumnGuideAdornments to update adornments in views.
                    var handler = GuidesSettingsManager.SettingsChanged;
                    if (handler != null)
                        handler();
                }
            }
        }

        internal static string GetUserSettingsString(string collection, string setting)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetReadOnlySettingsStore(SettingsScope.UserSettings);
            return store.GetString(collection, setting, "RGB(255,0,0) 80");
        }

        internal static void WriteUserSettingsString(string key, string propertyName,
                                                     string value)
        {
            var store = GuidesSettingsManager
                            .VsManagedSettingsManager
                            .GetWritableSettingsStore(SettingsScope.UserSettings);
            store.CreateCollection(key);
            store.SetString(key, propertyName, value);
        }

        // Persists settings and sets property with side effect of signaling
        // ColumnGuideAdornments to update.
        static private void WriteSettings(Color color, IEnumerable<int> columns)
        {
            string value = ComposeSettingsString(color, columns);
            GuidelinesConfiguration = value;
        }

        private static string ComposeSettingsString(Color color,
                                                    IEnumerable<int> columns)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendFormat("RGB({0},{1},{2})", color.R, color.G, color.B);
            IEnumerator<int> columnsEnumerator = columns.GetEnumerator();
            if (columnsEnumerator.MoveNext())
            {
                sb.AppendFormat(" {0}", columnsEnumerator.Current);
                while (columnsEnumerator.MoveNext())
                {
                    sb.AppendFormat(", {0}", columnsEnumerator.Current);
                }
            }
            return sb.ToString();
        }

        // Parse a color out of a string that begins like "RGB(255,0,0)"
        static internal Color GuidelinesColor
        {
            get
            {
                string config = GuidelinesConfiguration;
                if (!String.IsNullOrEmpty(config) && config.StartsWith("RGB("))
                {
                    int lastParen = config.IndexOf(')');
                    if (lastParen > 4)
                    {
                        string[] rgbs = config.Substring(4, lastParen - 4).Split(',');

                        if (rgbs.Length >= 3)
                        {
                            byte r, g, b;
                            if (byte.TryParse(rgbs[0], out r) &&
                                byte.TryParse(rgbs[1], out g) &&
                                byte.TryParse(rgbs[2], out b))
                            {
                                return Color.FromRgb(r, g, b);
                            }
                        }
                    }
                }
                return Colors.DarkRed;
            }

            set
            {
                WriteSettings(value, GetColumnOffsets());
            }
        }

        // Parse a list of integer values out of a string that looks like
        // "RGB(255,0,0) 1, 5, 10, 80"
        static internal List<int> GetColumnOffsets()
        {
            var result = new List<int>();
            string settings = GuidesSettingsManager.GuidelinesConfiguration;
            if (String.IsNullOrEmpty(settings))
                return new List<int>();

            if (!settings.StartsWith("RGB("))
                return new List<int>();

            int lastParen = settings.IndexOf(')');
            if (lastParen <= 4)
                return new List<int>();

            string[] columns = settings.Substring(lastParen + 1).Split(',');

            int columnCount = 0;
            foreach (string columnText in columns)
            {
                int column = -1;
                // VS 2008 gallery extension didn't allow zero, so per user request ...
                if (int.TryParse(columnText, out column) && column >= 0)
                {
                    columnCount++;
                    result.Add(column);
                    if (columnCount >= _maxGuides)
                        break;
                }
            }
            return result;
        }

        // Delegate and Event to fire when settings change so that ColumnGuideAdornments
        // can update. We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

Většina tento kód jenom vytvoří a analyzuje formát nastavení: "RGB (\<int >,\<int >,\<int >) \<int >, \<int >;...". Celých čísel na konci je založen na jedničce sloupce, ve kterém chcete vodítka sloupců. Rozšíření vodítka sloupců zachytí všechna nastavení v řetězci hodnotu jedno nastavení.

Existují některé části kódu, které stojí za to, zvýraznění. Následující řádek kódu získá spravovaná obálka sady Visual Studio pro nastavení úložiště. Ve většině případů to abstrahuje přes registru Windows, ale toto rozhraní API je nezávislý na mechanismus úložiště.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

 Nastavení úložiště Visual Studio používá identifikátor kategorie a identifikátor nastavení k jednoznačné identifikaci všechna nastavení:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Není nutné používat `“Text Editor”` kategorii název a můžete si vybrat jakkoli chcete.

První několik funkcí jsou vstupními body k nastavení změnit. Přihlášením ke vysoké úrovně omezení jako maximální počet povolený vodítka. Potom volají `WriteSettings` který lze kombinovat nastavení řetězec a nastaví vlastnost `GuideLinesConfiguration`. Nastavení této vlastnosti uloží hodnotu nastavení úložiště nastavení sady Visual Studio a aktivuje se `SettingsChanged` události a aktualizovat všechny `ColumnGuideAdornment` objekty, každý přidružené k zobrazení textu.

Existuje několik funkcí vstupního bodu, jako například `CanAddGuideline`, které se používají k implementaci příkazy, které mění nastavení. Když sada Visual Studio zobrazí nabídky, vyžádá si implementace příkazu zobrazíte, pokud příkaz je zapnut, co je jeho název, atd. Níže se zobrazí postup připojení těchto vstupních bodů pro implementace příkazu. Zobrazit [rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md) Další informace o příkazech.

## <a name="implementing-the-columnguideadornment-class"></a>Implementující třída ColumnGuideAdornment
`ColumnGuideAdornment` Pro každé zobrazení textu, který může mít vylepšení je vytvořena instance třídy. Tato třída naslouchá událostem o změně zobrazení nebo změna nastavení, aktualizace nebo překreslování sloupec provede podle potřeby.

Obsah ColumnGuideAdornment.cs nahraďte následujícím kódem (vysvětleno níže):

```csharp
using System;
using System.Windows.Media;
using Microsoft.VisualStudio.Text.Editor;
using System.Collections.Generic;
using System.Windows.Shapes;
using Microsoft.VisualStudio.Text.Formatting;
using System.Windows;

namespace ColumnGuides
{
    /// <summary>
    /// Adornment class, one instance per text view that draws a guides on the viewport
    /// </summary>
    internal sealed class ColumnGuideAdornment
    {
        private const double _lineThickness = 1.0;
        private IList<Line> _guidelines;
        private IWpfTextView _view;
        private double _baseIndentation;
        private double _columnWidth;

        /// <summary>
        /// Creates editor column guidelines
        /// </summary>
        /// <param name="view">The <see cref="IWpfTextView"/> upon
        /// which the adornment will be drawn</param>
        public ColumnGuideAdornment(IWpfTextView view)
        {
            _view = view;
            _guidelines = CreateGuidelines();
            GuidesSettingsManager.SettingsChanged +=
                new GuidesSettingsManager.SettingsChangedHandler(SettingsChanged);
            view.LayoutChanged +=
                new EventHandler<TextViewLayoutChangedEventArgs>(OnViewLayoutChanged);
            _view.Closed += new EventHandler(OnViewClosed);
        }

        void SettingsChanged()
        {
            _guidelines = CreateGuidelines();
            UpdatePositions();
            AddGuidelinesToAdornmentLayer();
        }

        void OnViewClosed(object sender, EventArgs e)
        {
            _view.LayoutChanged -= OnViewLayoutChanged;
            _view.Closed -= OnViewClosed;
            GuidesSettingsManager.SettingsChanged -= SettingsChanged;
        }

        private bool _firstLayoutDone;

        void OnViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
        {
            bool fUpdatePositions = false;

            IFormattedLineSource lineSource = _view.FormattedLineSource;
            if (lineSource == null)
            {
                return;
            }
            if (_columnWidth != lineSource.ColumnWidth)
            {
                _columnWidth = lineSource.ColumnWidth;
                fUpdatePositions = true;
            }
            if (_baseIndentation != lineSource.BaseIndentation)
            {
                _baseIndentation = lineSource.BaseIndentation;
                fUpdatePositions = true;
            }
            if (fUpdatePositions ||
                e.VerticalTranslation ||
                e.NewViewState.ViewportTop != e.OldViewState.ViewportTop ||
                e.NewViewState.ViewportBottom != e.OldViewState.ViewportBottom)
            {
                UpdatePositions();
            }
            if (!_firstLayoutDone)
            {
                AddGuidelinesToAdornmentLayer();
                _firstLayoutDone = true;
            }
        }

        private static IList<Line> CreateGuidelines()
        {
            Brush lineBrush = new SolidColorBrush(GuidesSettingsManager.GuidelinesColor);
            DoubleCollection dashArray = new DoubleCollection(new double[] { 1.0, 3.0 });
            IList<Line> result = new List<Line>();
            foreach (int column in GuidesSettingsManager.GetColumnOffsets())
            {
                Line line = new Line()
                {
                    // Use the DataContext slot as a cookie to hold the column
                    DataContext = column,
                    Stroke = lineBrush,
                    StrokeThickness = _lineThickness,
                    StrokeDashArray = dashArray
                };
                result.Add(line);
            }
            return result;
        }

        void UpdatePositions()
        {
            foreach (Line line in _guidelines)
            {
                int column = (int)line.DataContext;
                line.X2 = _baseIndentation + 0.5 + column * _columnWidth;
                line.X1 = line.X2;
                line.Y1 = _view.ViewportTop;
                line.Y2 = _view.ViewportBottom;
            }
        }

        void AddGuidelinesToAdornmentLayer()
        {
            // Grab a reference to the adornment layer that this adornment
            // should be added to
            // Must match exported name in ColumnGuideAdornmentTextViewCreationListener
            IAdornmentLayer adornmentLayer =
                _view.GetAdornmentLayer("ColumnGuideAdornment");
            if (adornmentLayer == null)
                return;
            adornmentLayer.RemoveAllAdornments();
            // Add the guidelines to the adornment layer and make them relative
            // to the viewport
            foreach (UIElement element in _guidelines)
                adornmentLayer.AddAdornment(AdornmentPositioningBehavior.OwnerControlled,
                                            null, null, element, null);
        }
    }

}
```

Instance této třídy opřete se o přidruženého <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> a seznam `Line` objekty v zobrazení.

Konstruktor (volat z `ColumnGuideAdornmentTextViewCreationListener` když Visual Studio vytvoří nová zobrazení) vytvoří Průvodce sloupec `Line` objekty. Konstruktor také přidá obslužné rutiny pro `SettingsChanged` událostí (podle `GuidesSettingsManager`) a zobrazení událostí `LayoutChanged` a `Closed`.

`LayoutChanged` Dojde k aktivaci události z důvodu několik druhů změny v zobrazení, včetně toho, když sada Visual Studio vytvoří zobrazení. `OnViewLayoutChanged` Volání obsluhy `AddGuidelinesToAdornmentLayer` ke spuštění. Kód v `OnViewLayoutChanged` Určuje, jestli je potřeba aktualizovat pozice řádku na základě změn, jako je například změní velikost písma, zobrazení mezery, vodorovné posouvání a tak dále. Kód v `UpdatePositions` způsobí, že vodicí čáry mezi znaky nebo bezprostředně po sloupci text, který je zadaný znak posun řádku text nakreslit.

Vždy, když se nastavení změní `SettingsChanged` obnoví všechny funkce jenom `Line` objekty se bez ohledu nové nastavení. Po nastavení pozice řádků, odebere všechny předchozí kód `Line` objekty z `ColumnGuideAdornment` dalších úprav vrstvy a přidá nové značky.

## <a name="defining-the-commands-menus-and-menu-placements"></a>Definování příkazy, nabídky a nabídky umístění
Může být mnohem deklarace příkazů a nabídek, umístění skupiny příkazů nebo nabídek na různých jiných nabídek a zapojování obslužné rutiny příkazů. Tento návod zabývá fungování příkazy v tomto rozšíření, ale podrobnější informace najdete v tématu [rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Úvod do kódu
Rozšíření vodítka sloupců ukazuje deklarace skupiny příkazů, které patří k sobě (Přidat sloupec, odeberte sloupce, změňte barvu čáry) a potom uvedení této skupiny na podnabídka z místní nabídky editoru. Rozšíření vodítka sloupců také přidá příkazy do hlavní **upravit** nabídky ale zůstanou skryté, popsané jako běžný vzor níže.

Existují tři části implementace příkazů: ColumnGuideCommandsPackage.cs ColumnGuideCommandsPackage.vsct a ColumnGuideCommands.cs. Kód vygenerovaný šablony umístí příkaz **nástroje** nabídky, která otevře dialogové okno jako implementace. Můžete si prohlédnout jak, která je implementovaná v souborech ColumnGuideCommands.cs a .vsct vzhledem k tomu, že je poměrně jednoduchý. Bude nahraďte kód v těchto souborech níže.

Balíček kódu je často používaný text deklarace, které jsou požadovány pro Visual Studio ke zjištění, že toto rozšíření nabízí příkazy a kam umístit příkazy. Když balíček inicializuje, vytvořit instanci třídy implementace příkazy. Podívejte se na příkazy nad odkaz Další informace o balíčcích týkající se příkazy.

### <a name="a-common-commands-pattern"></a>Běžným vzorem příkazy
Příkazy v vodítka sloupců rozšíření představují velmi běžným postupem v sadě Visual Studio. Zadejte související příkazy do skupiny, a vložíte skupiny v hlavní nabídce často s "`<CommandFlag>CommandWellOnly</CommandFlag>`" nastavena na skrytí příkazu. Přepnutím příkazy do hlavní nabídky (jako **upravit**) tímto způsobem nabízí, je dobré názvy (například **Edit.AddColumnGuide**) které jsou užitečné pro vyhledání příkazy pro opětovné přiřazení klávesové zkratky v  **Možnosti nástrojů** a získání dokončení při vyvolávání příkazů z **příkazové okno**.

Přidejte skupinu příkazů do místních nabídek nebo dílčí nabídky kde očekáváte, že uživatel používat příkazy. Visual Studio zpracuje `CommandWellOnly` jako neviditelnosti příznak pro pouze hlavní nabídky. Při umístění stejnou skupinu příkazů v Kontextová nabídka nebo podnabídka příkazy jsou viditelné.

Jako součást běžný vzor rozšíření vodítka sloupců vytvoří druhé skupině, která obsahuje jeden podnabídka. V nabídce sub zase obsahuje první skupinu pomocí Průvodce příkazů čtyři sloupce. Druhé skupině, která obsahuje dílčí nabídky je opakovaně použitelné asset, který můžete umístit na různé kontextové nabídky, které umístí dílčí nabídky na tyto kontextové nabídky.

### <a name="the-vsct-file"></a>Souboru .vsct
Souboru .vsct deklaruje, že příkazy a kam se obrátit, spolu s ikonami a tak dále. Nahraďte obsah souboru .vsct následujícím kódem (vysvětleno níže):

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <!--  This is the file that defines the actual layout and type of the commands.
        It is divided in different sections (e.g. command definition, command
        placement, ...), with each defining a specific set of properties.
        See the comment before each section for more details about how to
        use it. -->

  <!--  The VSCT compiler (the tool that translates this file into the binary
        format that VisualStudio will consume) has the ability to run a preprocessor
        on the vsct file; this preprocessor is (usually) the C++ preprocessor, so
        it is possible to define includes and macros with the same syntax used
        in C++ files. Using this ability of the compiler here, we include some files
        defining some of the constants that we will use inside the file. -->

  <!--This is the file that defines the IDs for all the commands exposed by
      VisualStudio. -->
  <Extern href="stdidcmd.h"/>

  <!--This header contains the command ids for the menus provided by the shell. -->
  <Extern href="vsshlids.h"/>

  <!--The Commands section is where commands, menus, and menu groups are defined.
      This section uses a Guid to identify the package that provides the command
      defined inside it. -->
  <Commands package="guidColumnGuideCommandsPkg">
    <!-- Inside this section we have different sub-sections: one for the menus, another
    for the menu groups, one for the buttons (the actual commands), one for the combos
    and the last one for the bitmaps used. Each element is identified by a command id
    that is a unique pair of guid and numeric identifier; the guid part of the identifier
    is usually called "command set" and is used to group different command inside a
    logically related group; your package should define its own command set in order to
    avoid collisions with command ids defined by other packages. -->

    <!-- In this section you can define new menu groups. A menu group is a container for
         other menus or buttons (commands); from a visual point of view you can see the
         group as the part of a menu contained between two lines. The parent of a group
         must be a menu. -->
    <Groups>

      <!-- The main group is parented to the edit menu. All the buttons within the group
           have the "CommandWellOnly" flag, so they're actually invisible, but it means
           they get canonical names that begin with "Edit". Using placements, the group
           is also placed in the GuidesSubMenu group. -->
      <!-- The priority 0xB801 is chosen so it goes just after
           IDG_VS_EDIT_COMMANDWELL -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

      <!-- Group for holding the "Guidelines" sub-menu anchor (the item on the menu that
           drops the sub menu). The group is parented to
           the context menu for code windows. That takes care of most editors, but it's
           also placed in a couple of other windows using Placements -->
      <Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_CODEWIN" />
      </Group>

    </Groups>

    <Menus>
      <Menu guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" priority="0x1000"
            type="Menu">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup" />
        <Strings>
          <ButtonText>&Column Guides</ButtonText>
        </Strings>
      </Menu>
    </Menus>

    <!--Buttons section. -->
    <!--This section defines the elements the user can interact with, like a menu command or a button
        or combo box in a toolbar. -->
    <Buttons>
      <!--To define a menu group you have to specify its ID, the parent menu and its
          display priority.
          The command is visible and enabled by default. If you need to change the
          visibility, status, etc, you can use the CommandFlag node.
          You can add more than one CommandFlag node e.g.:
              <CommandFlag>DefaultInvisible</CommandFlag>
              <CommandFlag>DynamicVisibility</CommandFlag>
          If you do not want an image next to your command, remove the Icon node or
          set it to <Icon guid="guidOfficeIcon" id="msotcidNoIcon" /> -->

      <Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
              priority="0x0100" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicAddGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Add Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveColumnGuide"
              priority="0x0101" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicRemoveGuide" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>AllowParams</CommandFlag>
        <Strings>
          <ButtonText>&Remove Column Guide</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidChooseGuideColor"
              priority="0x0103" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <Icon guid="guidImages" id="bmpPicChooseColor" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Column Guide &Color...</ButtonText>
        </Strings>
      </Button>

      <Button guid="guidColumnGuidesCommandSet" id="cmdidRemoveAllColumnGuides"
              priority="0x0102" type="Button">
        <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
        <CommandFlag>CommandWellOnly</CommandFlag>
        <Strings>
          <ButtonText>Remove A&ll Columns</ButtonText>
        </Strings>
      </Button>
    </Buttons>

    <!--The bitmaps section is used to define the bitmaps that are used for the
        commands.-->
    <Bitmaps>
      <!--  The bitmap id is defined in a way that is a little bit different from the
            others:
            the declaration starts with a guid for the bitmap strip, then there is the
            resource id of the bitmap strip containing the bitmaps and then there are
            the numeric ids of the elements used inside a button definition. An important
            aspect of this declaration is that the element id
            must be the actual index (1-based) of the bitmap inside the bitmap strip. -->
      <Bitmap guid="guidImages" href="Resources\ColumnGuideCommands.png"
              usedList="bmpPicAddGuide, bmpPicRemoveGuide, bmpPicChooseColor" />
    </Bitmaps>

  </Commands>

  <CommandPlacements>

    <!-- Define secondary placements for our groups -->

    <!-- Place the group containing the three commands in the sub-menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                      priority="0x0100">
      <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
    </CommandPlacement>

    <!-- The HTML editor context menu, for some reason, redefines its own groups
         so we need to place a copy of our context menu there too. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_HTML" />
    </CommandPlacement>

    <!-- The HTML context menu in Dev12 changed. -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp_Dev12" id="IDMX_HTM_SOURCE_HTML_Dev12" />
    </CommandPlacement>

    <!-- Similarly for Script -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_SCRIPT" />
    </CommandPlacement>

    <!-- Similarly for ASPX  -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x1001">
      <Parent guid="CMDSETID_HtmEdGrp" id="IDMX_HTM_SOURCE_ASPX" />
    </CommandPlacement>

    <!-- Similarly for the XAML editor context menu -->
    <CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
                      priority="0x0600">
      <Parent guid="guidXamlUiCmds" id="IDM_XAML_EDITOR" />
    </CommandPlacement>

  </CommandPlacements>

  <!-- This defines the identifiers and their values used above to index resources
       and specify commands. -->
  <Symbols>
    <!-- This is the package guid. -->
    <GuidSymbol name="guidColumnGuideCommandsPkg"
                value="{e914e5de-0851-4904-b361-1a3a9d449704}" />

    <!-- This is the guid used to group the menu commands together -->
    <GuidSymbol name="guidColumnGuidesCommandSet"
                value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
      <IDSymbol name="GuidesContextMenuGroup" value="0x1020" />
      <IDSymbol name="GuidesMenuItemsGroup" value="0x1021" />
      <IDSymbol name="GuidesSubMenu" value="0x1022" />
      <IDSymbol name="cmdidAddColumnGuide" value="0x0100" />
      <IDSymbol name="cmdidRemoveColumnGuide" value="0x0101" />
      <IDSymbol name="cmdidChooseGuideColor" value="0x0102" />
      <IDSymbol name="cmdidRemoveAllColumnGuides" value="0x0103" />
    </GuidSymbol>

    <GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
      <IDSymbol name="bmpPicAddGuide" value="1" />
      <IDSymbol name="bmpPicRemoveGuide" value="2" />
      <IDSymbol name="bmpPicChooseColor" value="3" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp_Dev12"
                value="{78F03954-2FB8-4087-8CE7-59D71710B3BB}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML_Dev12" value="0x1" />
    </GuidSymbol>

    <GuidSymbol name="CMDSETID_HtmEdGrp" value="{d7e8c5e1-bdb8-11d0-9c88-0000f8040a53}">
      <IDSymbol name="IDMX_HTM_SOURCE_HTML" value="0x33" />
      <IDSymbol name="IDMX_HTM_SOURCE_SCRIPT" value="0x34" />
      <IDSymbol name="IDMX_HTM_SOURCE_ASPX" value="0x35" />
    </GuidSymbol>

    <GuidSymbol name="guidXamlUiCmds" value="{4c87b692-1202-46aa-b64c-ef01faec53da}">
      <IDSymbol name="IDM_XAML_EDITOR" value="0x103" />
    </GuidSymbol>
  </Symbols>

</CommandTable>

```

**IDENTIFIKÁTORY GUID**. Pro Visual Studio můžete najít vaší obslužné rutiny příkazů a je vyvolat je potřeba zajistit, že balíček, který GUID deklarované v souboru ColumnGuideCommandsPackage.cs (generován ze šablony položky projektu) odpovídá balíček, který GUID deklarované v souboru .vsct (zkopírováno z výše ). Pokud znovu použijete ukázkový kód, by měl se ujistěte, že máte jiný identifikátor GUID tak, aby vám nejsou v konfliktu se všichni ostatní, kteří mohou mít zkopírovat tento kód.

Vyhledejte tento řádek v ColumnGuideCommandsPackage.cs a zkopírujte identifikátor GUID mezi uvozovky:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Vložte identifikátor GUID v souboru .vsct tak, abyste měli následující řádek vaší `Symbols` deklarace:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg" 
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Identifikátory GUID pro příkaz nastavit a rastrového obrázku musí být jedinečná pro rozšíření příliš:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Není však nutné změnit sadu příkazů a rastrový obrázek GUID v tomto názorném postupu získat kód pro práci. Příkaz nastavit GUID musí odpovídat deklarace v souboru ColumnGuideCommands.cs, ale nahradí obsah tohoto souboru příliš; proto bude odpovídat identifikátory GUID.

Jiné identifikátory GUID v souboru .vsct identifikovat předem stávající nabídky, ke kterým se přidají příkazy Průvodce sloupce, takže nikdy nezmění.

**Soubor oddíly**. .vsct má tři části vnější: příkazy, umístění a symboly. Příkazy oddíl definuje skupinu příkazů, nabídek, tlačítek nebo položky nabídky a rastrových obrázků pro ikony. V části umístění deklaruje, kde skupin přejděte v nabídkách nebo další umístění do existující nabídky. V části symboly deklaruje identifikátory použitými jinde v souboru .vsct díky .vsct kód čitelnější než všude s identifikátory GUID a šestnáctkových číslic.

**Příkazy části, seskupuje definice**. V části příkazy nejdřív definuje skupinu příkazů. Příkazy, které vidíte v nabídkách s mírné šedou řádky oddělení skupin jsou skupiny příkazů. Skupina může rovněž zadat celou dílčí nabídka, jako v následujícím příkladu a se nezobrazí na šedý symbol v tomto případě oddělení řádků. Soubory .vsct deklaruje dvě skupiny `GuidesMenuItemsGroup` , který je prvek `IDM_VS_MENU_EDIT` (hlavní **upravit** nabídky) a `GuidesContextMenuGroup` , který je prvek `IDM_VS_CTXT_CODEWIN` (kontextová nabídka editor kódu).

Druhý deklarace skupiny `0x0600` priority:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Cílem je, Vložit sloupec provede podnabídka na konci z jakékoliv místní nabídky, ke kterému můžeme přidat skupinu nabídek sub. Ale by neměly předpokládají nejlíp vědět a vynutit podnabídka vždy být poslední pomocí prioritu `0xFFFF`. Budete muset pohrát si s tímto číslem, které chcete zobrazit, pokud dílčí nabídka spočívá v kontextové nabídky, které umístíte. V tomto případě `0x0600` je dostatečně vysoká, aby umístil na konci nabídky nejdál, co můžeme vidět, ale ponechává místo pro někoho jiného návrhu svého rozšíření bude nižší než rozšíření vodítka sloupců, pokud je to žádoucí.

**Příkazy části definice nabídky**. Další příkaz oddíl definuje dílčí nabídky `GuidesSubMenu`, k nadřazeným prvkem `GuidesContextMenuGroup`. `GuidesContextMenuGroup` Je skupina přidáme na všechny příslušné místní nabídky. V části umístění kód umístí skupiny s příkazy Průvodce čtyři sloupce v této nabídce sub.

**Příkazy části, tlačítka definice**. Část příkazy pak definuje položky nabídky nebo tlačítka, která jsou čtyři sloupce provede příkazy. `CommandWellOnly`, bylo uvedeno výše, znamená, že příkazy nejsou viditelná, když umístění v hlavní nabídce. Dvě položky nabídky tlačítka deklarace (Průvodce přidat a odebrat průvodce) je navíc `AllowParams` příznak:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Tento příznak povolí spolu s s hlavní nabídky umístění příkazu přijímat argumenty, když Visual Studio vyvolá obslužnou rutinu příkazu. Pokud uživatel vyvolá příkaz z příkazového okna, argument bude předána do obslužná rutina příkazu události argumenty.

**Příkaz oddíly, bitmap definice**. Nakonec v části příkazy deklaruje rastrové obrázky a ikony používané pro příkazy. Toto je jednoduché deklarace, která identifikuje prostředek projektů a seznam založen na jedničce indexy používaných ikon. Symboly část souboru .vsct deklaruje hodnoty identifikátory používané jako indexy. Tento návod používá pruhu rastrový obrázek poskytovány se šablonou vlastního příkazu položky přidány do projektu.

**Oddíl umístění**. Po příkazech, které je část oddílu umístění. První z nich je, pokud kód přidá první skupiny bylo uvedeno výše, který obsahuje čtyři sloupce Průvodce příkazy do dílčí nabídky kde se zobrazí příkazy:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Přidejte všechny další umístění `GuidesContextMenuGroup` (obsahující `GuidesSubMenu`) pro ostatní kontextové nabídky editoru. Když kód deklarované `GuidesContextMenuGroup`, byl prvek místní nabídky editoru kódu. To je důvod, proč nevidíte umístění pro místní nabídka editoru kódu.

**Symboly části**. Jak je uvedeno výše, deklaruje části symboly identifikátory použitými jinde v souboru .vsct díky .vsct kód čitelnější než všude s identifikátory GUID a šestnáctkové číslice. Důležitých bodů v této části se, že identifikátor GUID balíčku musíte souhlasit s deklarací ve třídě balíčku a sadu příkazů, že identifikátor GUID musíte souhlasit s deklarací ve třídě implementace příkazu.

## <a name="implementing-the-commands"></a>Provádění příkazů
Soubor ColumnGuideCommands.cs implementuje příkazy a připojí do obslužné rutiny. Když Visual Studio načte balíček a inicializuje ji, balíček pak volá `Initialize` v implementační třídě příkazy. Příkazy inicializace jednoduše vytvoří instanci třídy a konstruktoru připojí se všechny obslužné rutiny příkazu.

Nahraďte obsah souboru ColumnGuideCommands.cs následující kód (vysvětleno níže):

```csharp
using System;
using System.ComponentModel.Design;
using System.Globalization;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;
using Microsoft.VisualStudio.TextManager.Interop;
using Microsoft.VisualStudio.Text.Editor;
using Microsoft.VisualStudio;

namespace ColumnGuides
{
    /// <summary>
    /// Command handler
    /// </summary>
    internal sealed class ColumnGuideCommands
    {

        const int cmdidAddColumnGuide = 0x0100;
        const int cmdidRemoveColumnGuide = 0x0101;
        const int cmdidChooseGuideColor = 0x0102;
        const int cmdidRemoveAllColumnGuides = 0x0103;

        /// <summary>
        /// Command menu group (command set GUID).
        /// </summary>
        static readonly Guid CommandSet =
            new Guid("c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e");

        /// <summary>
        /// VS Package that provides this command, not null.
        /// </summary>
        private readonly Package package;

        OleMenuCommand _addGuidelineCommand;
        OleMenuCommand _removeGuidelineCommand;

        /// <summary>
        /// Initializes the singleton instance of the command.
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        public static void Initialize(Package package)
        {
            Instance = new ColumnGuideCommands(package);
        }

        /// <summary>
        /// Gets the instance of the command.
        /// </summary>
        public static ColumnGuideCommands Instance
        {
            get;
            private set;
        }

        /// <summary>
        /// Initializes a new instance of the <see cref="ColumnGuideCommands"/> class.
        /// Adds our command handlers for menu (commands must exist in the command
        /// table file)
        /// </summary>
        /// <param name="package">Owner package, not null.</param>
        private ColumnGuideCommands(Package package)
        {
            if (package == null)
            {
                throw new ArgumentNullException("package");
            }

            this.package = package;

            // Add our command handlers for menu (commands must exist in the .vsct file)

            OleMenuCommandService commandService =
                this.ServiceProvider.GetService(typeof(IMenuCommandService))
                    as OleMenuCommandService;
            if (commandService != null)
            {
                // Add guide
                _addGuidelineCommand =
                    new OleMenuCommand(AddColumnGuideExecuted, null,
                                       AddColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidAddColumnGuide));
                _addGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_addGuidelineCommand);
                // Remove guide
                _removeGuidelineCommand =
                    new OleMenuCommand(RemoveColumnGuideExecuted, null,
                                       RemoveColumnGuideBeforeQueryStatus,
                                       new CommandID(ColumnGuideCommands.CommandSet,
                                                     cmdidRemoveColumnGuide));
                _removeGuidelineCommand.ParametersDescription = "<column>";
                commandService.AddCommand(_removeGuidelineCommand);
                // Choose color
                commandService.AddCommand(
                    new MenuCommand(ChooseGuideColorExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidChooseGuideColor)));
                // Remove all
                commandService.AddCommand(
                    new MenuCommand(RemoveAllGuidelinesExecuted,
                                    new CommandID(ColumnGuideCommands.CommandSet,
                                                  cmdidRemoveAllColumnGuides)));
            }
        }

        /// <summary>
        /// Gets the service provider from the owner package.
        /// </summary>
        private IServiceProvider ServiceProvider
        {
            get
            {
                return this.package;
            }
        }

        private void AddColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _addGuidelineCommand.Enabled =
                GuidesSettingsManager.CanAddGuideline(currentColumn);
        }

        private void RemoveColumnGuideBeforeQueryStatus(object sender, EventArgs e)
        {
            int currentColumn = GetCurrentEditorColumn();
            _removeGuidelineCommand.Enabled =
                GuidesSettingsManager.CanRemoveGuideline(currentColumn);
        }

        private int GetCurrentEditorColumn()
        {
            IVsTextView view = GetActiveTextView();
            if (view == null)
            {
                return -1;
            }

            try
            {
                IWpfTextView textView = GetTextViewFromVsTextView(view);
                int column = GetCaretColumn(textView);

                // Note: GetCaretColumn returns 0-based positions. Guidelines are 1-based
                // positions.
                // However, do not subtract one here since the caret is positioned to the
                // left of
                // the given column and the guidelines are positioned to the right. We
                // want the
                // guideline to line up with the current caret position. e.g. When the
                // caret is
                // at position 1 (zero-based), the status bar says column 2. We want to
                // add a
                // guideline for column 1 since that will place the guideline where the
                // caret is.
                return column;
            }
            catch (InvalidOperationException)
            {
                return -1;
            }
        }

        /// <summary>
        /// Find the active text view (if any) in the active document.
        /// </summary>
        /// <returns>The IVsTextView of the active view, or null if there is no active
        /// document or the
        /// active view in the active document is not a text view.</returns>
        private IVsTextView GetActiveTextView()
        {
            IVsMonitorSelection selection =
                this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
                                                    as IVsMonitorSelection;
            object frameObj = null;
            ErrorHandler.ThrowOnFailure(
                selection.GetCurrentElementValue(
                    (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame, out frameObj));

            IVsWindowFrame frame = frameObj as IVsWindowFrame;
            if (frame == null)
            {
                return null;
            }

            return GetActiveView(frame);
        }

        private static IVsTextView GetActiveView(IVsWindowFrame windowFrame)
        {
            if (windowFrame == null)
            {
                throw new ArgumentException("windowFrame");
            }

            object pvar;
            ErrorHandler.ThrowOnFailure(
                windowFrame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView, out pvar));

            IVsTextView textView = pvar as IVsTextView;
            if (textView == null)
            {
                IVsCodeWindow codeWin = pvar as IVsCodeWindow;
                if (codeWin != null)
                {
                    ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
                }
            }
            return textView;
        }

        private static IWpfTextView GetTextViewFromVsTextView(IVsTextView view)
        {

            if (view == null)
            {
                throw new ArgumentNullException("view");
            }

            IVsUserData userData = view as IVsUserData;
            if (userData == null)
            {
                throw new InvalidOperationException();
            }

            object objTextViewHost;
            if (VSConstants.S_OK
                   != userData.GetData(Microsoft.VisualStudio
                                                .Editor
                                                .DefGuidList.guidIWpfTextViewHost,
                                       out objTextViewHost))
            {
                throw new InvalidOperationException();
            }

            IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
            if (textViewHost == null)
            {
                throw new InvalidOperationException();
            }

            return textViewHost.TextView;
        }

        /// <summary>
        /// Given an IWpfTextView, find the position of the caret and report its column
        /// number. The column number is 0-based
        /// </summary>
        /// <param name="textView">The text view containing the caret</param>
        /// <returns>The column number of the caret's position. When the caret is at the
        /// leftmost column, the return value is zero.</returns>
        private static int GetCaretColumn(IWpfTextView textView)
        {
            // This is the code the editor uses to populate the status bar.
            Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
                textView.Caret.ContainingTextViewLine;
            double columnWidth = textView.FormattedLineSource.ColumnWidth;
            return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                       / columnWidth));
        }

        /// <summary>
        /// Determine the applicable column number for an add or remove command.
        /// The column is parsed from command arguments, if present. Otherwise
        /// the current position of the caret is used to determine the column.
        /// </summary>
        /// <param name="e">Event args passed to the command handler.</param>
        /// <returns>The column number. May be negative to indicate the column number is
        /// unavailable.</returns>
        /// <exception cref="ArgumentException">The column number parsed from event args
        /// was not a valid integer.</exception>
        private int GetApplicableColumn(EventArgs e)
        {
            var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
            if (!string.IsNullOrEmpty(inValue))
            {
                int column;
                if (!int.TryParse(inValue, out column) || column < 0)
                    throw new ArgumentException("Invalid column");
                return column;
            }

            return GetCurrentEditorColumn();
        }

        /// <summary>
        /// This function is the callback used to execute a command when the a menu item
        /// is clicked. See the Initialize method to see how the menu item is associated
        /// to this function using the OleMenuCommandService service and the MenuCommand
        /// class.
        /// </summary>
        private void AddColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.AddGuideline(column);
            }
        }

        private void RemoveColumnGuideExecuted(object sender, EventArgs e)
        {
            int column = GetApplicableColumn(e);
            if (column >= 0)
            {
                GuidesSettingsManager.RemoveGuideline(column);
            }
        }

        private void RemoveAllGuidelinesExecuted(object sender, EventArgs e)
        {
            GuidesSettingsManager.RemoveAllGuidelines();
        }

        private void ChooseGuideColorExecuted(object sender, EventArgs e)
        {
            System.Windows.Media.Color color = GuidesSettingsManager.GuidelinesColor;

            using (System.Windows.Forms.ColorDialog picker =
                new System.Windows.Forms.ColorDialog())
            {
                picker.Color = System.Drawing.Color.FromArgb(255, color.R, color.G,
                                                             color.B);
                if (picker.ShowDialog() == System.Windows.Forms.DialogResult.OK)
                {
                    GuidesSettingsManager.GuidelinesColor =
                        System.Windows.Media.Color.FromRgb(picker.Color.R,
                                                           picker.Color.G,
                                                           picker.Color.B);
                }
            }
        }

    }
}

```

**Opravit odkazy**. V tomto okamžiku jsou nechybí odkaz. Stisknutím tlačítka správný ukazatel myši na uzel odkazy v Průzkumníku řešení. Zvolte **přidat...** příkaz. **Přidat odkaz** dialogové okno obsahuje vyhledávací pole v pravém horním rohu. Zadejte "editor" (bez dvojitých uvozovek). Zvolte **Microsoft.VisualStudio.Editor** položky (musí zaškrtnete políčko nalevo od položky, stačí vybrat položky) a zvolte **OK** přidat odkaz.

**Inicializace**. Inicializuje třídu balíček volá `Initialize` v implementační třídě příkazy. `ColumnGuideCommands` Inicializace vytvoří instanci třídy a členy třídy ukládá instance třídy a odkaz na balíček.

Podívejme se na jednu z ups hook obslužná rutina příkazu z konstruktoru třídy:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Vytvoření `OleMenuCommand`. Visual Studio používá příkaz systém Microsoft Office. Klíče argumenty při vytvoření instance OleMenuCommand je funkce, která implementuje příkazu (`AddColumnGuideExecuted`), funkce, která má být volána při sada Visual Studio zobrazí nabídku pomocí příkazu (`AddColumnGuideBeforeQueryStatus`) a ID příkazu. Visual studio volá funkci stav dotazu před zobrazením příkaz v nabídce, aby příkaz můžete provést samotný neviditelný nebo vyšedlá pro konkrétní zobrazení nabídky (třeba zakázání **kopírování** Pokud nebyla vybrána žádná položka), změnit ikonu, nebo dokonce i změnit jeho název (například z přidat něco, co můžete odebrat něco) a tak dále. ID příkazu, který musí odpovídat ID příkazu deklarované v souboru .vsct. Nastavte řetězce pro příkaz a vodítka sloupců přidejte příkaz musí odpovídat mezi souboru .vsct a ColumnGuideCommands.cs.

Následující řádek představuje pomoc v případě, když uživatelé vyvolání příkazu via příkazové okno (vysvětleno níže):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

**Dotaz stav**. Funkce dotazování na stav `AddColumnGuideBeforeQueryStatus` a `RemoveColumnGuideBeforeQueryStatus` zkontrolujte některá nastavení (například maximální počet příruček a maximální počet sloupců) nebo pokud je sloupec vodítko k odebrání. Pokud jsou podmínky vpravo umožňují příkazy. Funkce dotazování na stav musí být velmi efektivní, protože se spustí pokaždé, když sada Visual Studio zobrazí nabídku, pro každý příkaz v nabídce.

**Funkce AddColumnGuideExecuted**. Zajímavé části Průvodce přidáním je zjištění aktuálního umístění zobrazení a blikající kurzor editoru. Nejprve tuto funkci volá `GetApplicableColumn` která zkontroluje, jestli je argumentem uživatelem zadané v argumentech události obslužná rutina příkazu, a pokud neexistuje žádný, pak funkce zkontroluje zobrazení editoru:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

    return GetCurrentEditorColumn();
}

```

`GetCurrentEditorColumn` má se do toho nepomáhají dostat se <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> zobrazení kódu. Pokud je trasování prostřednictvím `GetActiveTextView`, `GetActiveView`, a `GetTextViewFromVsTextView`, můžete zjistit, jak to udělat. Tady je příslušný kód abstrakci, od aktuální výběr a získávání rámce výběr a potom vyberte získávání rámce DocView jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, potom <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> z IVsTextView a získávání zobrazení hostitele, a Nakonec IWpfTextView:

```csharp
   IVsMonitorSelection selection =
       this.ServiceProvider.GetService(typeof(IVsMonitorSelection))
           as IVsMonitorSelection;
   object frameObj = null;

ErrorHandler.ThrowOnFailure(selection.GetCurrentElementValue(
                                (uint)VSConstants.VSSELELEMID.SEID_DocumentFrame,
                                out frameObj));

   IVsWindowFrame frame = frameObj as IVsWindowFrame;
   if (frame == null)
       <<do nothing>>;

...
   object pvar;
   ErrorHandler.ThrowOnFailure(frame.GetProperty((int)__VSFPROPID.VSFPROPID_DocView,
                                                  out pvar));

   IVsTextView textView = pvar as IVsTextView;
   if (textView == null)
   {
       IVsCodeWindow codeWin = pvar as IVsCodeWindow;
       if (codeWin != null)
       {
           ErrorHandler.ThrowOnFailure(codeWin.GetLastActiveView(out textView));
       }
   }

...
   if (textView == null)
       <<do nothing>>

   IVsUserData userData = textView as IVsUserData;
   if (userData == null)
       <<do nothing>>

   object objTextViewHost;
   if (VSConstants.S_OK
           != userData.GetData(Microsoft.VisualStudio.Editor.DefGuidList
                                                            .guidIWpfTextViewHost,
                                out objTextViewHost))
   {
       <<do nothing>>
   }

   IWpfTextViewHost textViewHost = objTextViewHost as IWpfTextViewHost;
   if (textViewHost == null)
       <<do nothing>>

   IWpfTextView textView = textViewHost.TextView;

```

Jakmile budete mít IWpfTextView, získáte sloupec, kde je umístěná stříška:

```csharp
private static int GetCaretColumn(IWpfTextView textView)
{
    // This is the code the editor uses to populate the status bar.
    Microsoft.VisualStudio.Text.Formatting.ITextViewLine caretViewLine =
        textView.Caret.ContainingTextViewLine;
    double columnWidth = textView.FormattedLineSource.ColumnWidth;
    return (int)(Math.Round((textView.Caret.Left - caretViewLine.Left)
                                / columnWidth));
}

```

Aktuální sloupec spolupráce tam, kde uživatel kliknul, kód jen volá správce nastavení přidat nebo odebrat sloupce. Správce nastavení aktivuje událost, na kterém jsou všechny `ColumnGuideAdornment` naslouchání objekty. Když se aktivuje událost, aktualizujte tyto objekty své názory přidružený text s novými sloupci průvodce nastaveními.

## <a name="invoking-command-from-the-command-window"></a>Vyvolání příkazu z příkazového okna
Ukázka vodítka sloupců umožňuje uživatelům umožnit vyvolání dva příkazy z příkazového okna ve formě rozšíření. Pokud používáte **zobrazení &#124; ostatní Windows &#124; příkazové okno** příkaz, může se zobrazit příkazové okno. Můžete pracovat pomocí příkazového okna tak, že zadáte "upravit" a název dokončení příkazu a zadávání argumentu 120, máte následující:

```
> Edit.AddColumnGuide 120
>
```

Části Ukázky, které jsou v deklaracích souboru .vsct, `ColumnGuideCommands` konstruktoru třídy při jeho zavěšení obslužné rutiny příkazů a implementace obslužné rutiny příkazu, které kontrolují argumenty události.

Jste viděli "`<CommandFlag>CommandWellOnly</CommandFlag>`" v souboru .vsct, stejně jako umístění v hlavní nabídce Úpravy i když jsme nezobrazovat příkazy **upravit** nabídce uživatelského rozhraní. Máte v hlavní nabídce Úpravy jim umožňuje názvy jako **Edit.AddColumnGuide**. Příkazy skupiny deklarace, která obsahuje že čtyři příkazy umístěné skupině v nabídce upravit přímo:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Oddíl tlačítka později deklarovat příkazy `CommandWellOnly` Novoroční viditelná v hlavní nabídce a je deklarován `AllowParams`:

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide" 
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Jste viděli obslužná rutina příkazu propojení kódu v `ColumnGuideCommands` konstruktoru třídy uvedete popis parametru povolené:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Jste viděli `GetApplicableColumn` funkci kontroly `OleMenuCmdEventArgs` hodnoty před vrácením zobrazení editoru pro aktuální sloupec:

```csharp
private int GetApplicableColumn(EventArgs e)
{
    var inValue = ((OleMenuCmdEventArgs)e).InValue as string;
    if (!string.IsNullOrEmpty(inValue))
    {
        int column;
        if (!int.TryParse(inValue, out column) || column < 0)
            throw new ArgumentException("Invalid column");
        return column;
    }

```

## <a name="trying-your-extension"></a>Při operaci rozšíření
Nyní můžete stisknout **F5** ke spuštění rozšíření vodítka sloupců. Otevřete textový soubor a pomocí místní nabídky editoru přidat vodítka řádků, je odebrat a změnit jeho barvu. Budete muset kliknout na text (mezera není dosaženo konce řádku) Chcete-li přidat sloupec průvodce nebo editoru přidá jej do posledního sloupce v řádku. Pokud používáte příkazové okno a vyvolání příkazů s argumentem, můžete přidat kamkoli vodítka sloupců.

Pokud chcete zkuste jiný příkaz umístění, změňte názvy, změnit ikony a tak dále, a máte potíže s pomocí sady Visual Studio zobrazí nejnovější kód v nabídkách, můžete resetovat experimentální hive, který ladíte. Vyvolali **nabídce Windows Start** a zadejte "obnovit". Vyhledejte a vyvolat příkaz **obnovit na další experimentální Instance sady Visual Studio**. Tím vyčistíte experimentální podregistru všech součástí rozšíření. Ne čištění si nastavení z komponent, tak žádné vodítka při vypnutí experimentální hive v sadě Visual Studio bude stále existovat při váš kód načítá úložiště nastavení při dalším spuštění.

## <a name="finished-code-project"></a>Dokončený kód projektu
Brzy bude projekt Githubu ukázky rozšiřitelnosti sady Visual Studio a dokončený projekt bude existuje. Aktualizujeme Toto téma tak, aby odkazoval došlo, pokud k tomu dojde. Dokončený ukázkový projekt může mít různé identifikátory GUID a bude mít různými bitmapami vymazat u ikon příkazu.

Budete moct vyzkoušet verzi funkce vodítka sloupců s této galerie sady Visual Studio[rozšíření](https://visualstudiogallery.msdn.microsoft.com/da227a0b-0e31-4a11-8f6b-3a149cf2e459?SRC=Home).

## <a name="see-also"></a>Viz také
[V editoru](../extensibility/inside-the-editor.md)
[rozšíření pro Editor a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md)
[služba jazyka a editoru Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md) 
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
[přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md)
[vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)

