---
title: Vytvoření zobrazení vylepšení, příkazy a nastavení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aab9e0ede95eebe6f8f54cc3f01e7e7d5f98d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697649"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Návod: Vytvoření vylepšení zobrazení, příkazů a nastavení (vodítka sloupců)
Editor textu a kódu sady Visual Studio můžete rozšířit o příkazy a efekty zobrazení. Tento článek vám ukáže, jak začít s populární funkcí rozšíření, sloupcovými průvodci. Vodítka sloupců jsou vizuálně světelné čáry nakreslené v zobrazení textového editoru, které vám pomohou spravovat kód na konkrétní šířky sloupců. Konkrétně formátovaný kód může být důležitý pro ukázky, které zahrnete do dokumentů, příspěvků blogu nebo hlášení chyb.

V tomto návodu:
- Vytvoření projektu VSIX
- Přidání vylepšení zobrazení editoru
- Přidat podporu pro ukládání a získávání nastavení (kde kreslit vodítka sloupců a jejich barvu)
- Přidání příkazů (přidání/odebrání vodítek sloupců, změna jejich barvy)
- Umístění příkazů do kontextových nabídek Úpravy a textových dokumentů
- Přidání podpory pro vyvolání příkazů z okna příkazu sady Visual Studio

  Můžete vyzkoušet verzi funkce průvodce sloupci s tímto[rozšířením](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)Galerie sady Visual Studio .

  > [!NOTE]
  > V tomto návodu vložíte velké množství kódu do několika souborů generovaných šablonami rozšíření sady Visual Studio. Ale brzy tento návod bude odkazovat na dokončené řešení na GitHubu s dalšími příklady rozšíření. Vyplněný kód se mírně liší v tom, že má skutečné ikony příkazů namísto použití obecných ikon šablon.

## <a name="get-started"></a>Začínáme
Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Nastavení řešení
Nejprve vytvoříte projekt VSIX, přidáte vylepšení zobrazení editoru a pak přidáte příkaz (který přidá VSPackage vlastní příkaz). Základní architektura je následující:
- Máte naslouchací proces `ColumnGuideAdornment` vytvoření zobrazení textu, který vytvoří objekt na zobrazení. Tento objekt naslouchá událostem o změně zobrazení nebo změně nastavení, aktualizaci nebo překreslování vodítek sloupců podle potřeby.
- `GuidesSettingsManager` Je, který zpracovává čtení a zápis z úložiště nastavení sady Visual Studio. Správce nastavení má také operace pro aktualizaci nastavení, která podporují uživatelské příkazy (přidat sloupec, odstranit sloupec, změnit barvu).
- Je tu balíček VSIP, který je nezbytný, pokud máte uživatelské příkazy, ale je to jen standardní kód, který inicializuje objekt implementace příkazů.
- Je objekt, `ColumnGuideCommands` který spouští uživatelské příkazy a zapojí obslužné rutiny příkazů pro příkazy deklarované v souboru *.vsct.*

  **VSIX**. K vytvoření projektu použijte příkaz **Nový &#124; soubor ...** . V levém navigačním podokně zvolte uzel **rozšiřitelnostpod** **c#** a v pravém podokně zvolte **Projekt VSIX.** Zadejte název **SloupciPrůvodci** a pro vytvoření projektu zvolte **OK.**

  **Zobrazit ozdobu**. Stiskněte pravé tlačítko ukazatele na uzlu projektu v Průzkumníku řešení. Chcete-li přidat novou položku zobrazení, zvolte příkaz **Přidat &#124; novou položku ...** V levém navigačním podokně zvolte **Rozšiřitelnost &#124; Editor** a v pravém podokně zvolte **Vylepšení výřezu editoru.** Zadejte název **ColumnGuideAdornment** jako název položky a zvolte **Přidat,** chcete-li přidat.

  Tato šablona položky byla přidána dva soubory do projektu (stejně jako odkazy a tak dále): **ColumnGuideAdornment.cs** a **ColumnGuideAdornmentTextViewCreationListener.cs**. Šablony nakreslí v zobrazení fialový obdélník. V následující části změníte několik řádků v naslouchací proces vytvoření zobrazení a nahradit obsah **ColumnGuideAdornment.cs**.

  **Příkazy**. V **Průzkumníku řešení**stiskněte pravé tlačítko ukazatele na uzlu projektu. Chcete-li přidat novou položku zobrazení, zvolte příkaz **Přidat &#124; novou položku ...** V levém navigačním podokně zvolte **Rozšiřitelnost &#124; VSPackage** a v pravém podokně zvolte **Vlastní příkaz.** Zadejte název **ColumnGuideCommands** jako název položky a zvolte **Přidat**. Kromě několika odkazů přidání příkazů a balíčku také **přidalo ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**a **ColumnGuideCommandsPackage.vsct**. V následující části nahradíte obsah prvního a posledního souboru a definujte a implementujete příkazy.

## <a name="set-up-the-text-view-creation-listener"></a>Nastavení naslouchací proces vytvoření zobrazení textu
Otevřete *ColumnGuideAdornmentTextViewCreationListener.cs* v editoru. Tento kód implementuje obslužnou rutinu pro vždy, když Visual Studio vytvoří zobrazení textu. Existují atributy, které řídí, když je volána obslužná rutina v závislosti na charakteristikách zobrazení.

Kód také musí deklarovat vrstvu vylepšení. Když editor aktualizuje zobrazení, získá vrstvy vylepšení pro zobrazení a z toho získá prvky vylepšení. Můžete deklarovat pořadí vrstvy vzhledem k ostatním s atributy. Nahraďte následující řádek:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

s těmito dvěma řádky:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Řádek, který jste nahradili, je ve skupině atributů, které deklarují vrstvu vylepšení. První řádek, který jste změnili, se změní pouze tam, kde se zobrazí vodicí čáry sloupců. Kreslení řádků "před" text v zobrazení znamená, že se zobrazí za nebo pod textem. Druhý řádek deklaruje, že vylepšení průvodce sloupci jsou použitelné pro textové entity, které odpovídají vaší pojetí dokumentu, ale můžete deklarovat vylepšení, například pracovat pouze pro upravitelný text. Další informace naleznete v [jazykových službách a doplňkových bodech editoru](../extensibility/language-service-and-editor-extension-points.md)

## <a name="implement-the-settings-manager"></a>Implementace správce nastavení
Obsah *GuidesSettingsManager.cs* se nahradí následujícím kódem (vysvětleno níže):

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
                // Not present.  Allow user to remove the last column
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
        // can update.  We need nothing special in this event since the settings manager
        // is statically available.
        //
        internal delegate void SettingsChangedHandler();
        static internal event SettingsChangedHandler SettingsChanged;

    }
}

```

Většina tohoto kódu vytvoří a analyzuje formát nastavení:\<"RGB( int\<>, int>,\<int>) \<int>, \<int>, ...".  Celá čísla na konci jsou sloupce s jedním souborem, ve kterých chcete vodítka sloupců. Rozšíření vodítka sloupců zachycuje všechna jeho nastavení v jednom řetězci hodnot nastavení.

Existují některé části kódu stojí za zvýraznění. Následující řádek kódu získá obálku spravované houštinou sady Visual Studio pro úložiště nastavení. Z větší části to abstrahuje přes registr systému Windows, ale toto rozhraní API je nezávislé na mechanismu úložiště.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Úložiště nastavení sady Visual Studio používá identifikátor kategorie a identifikátor nastavení k jednoznačné identifikaci všech nastavení:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Není třeba použít `"Text Editor"` jako název kategorie. Můžeš si vybrat, co chceš.

Prvních několik funkcí jsou vstupní body pro změnu nastavení. Kontrolují omezení na vysoké úrovni, jako je maximální povolený počet vodítek.  Pak volají `WriteSettings`, který skládá řetězec nastavení a `GuideLinesConfiguration`nastaví vlastnost . Nastavení této vlastnosti uloží hodnotu nastavení do úložiště `SettingsChanged` nastavení sady `ColumnGuideAdornment` Visual Studio a spustí událost aktualizovat všechny objekty, každý přidružený k textovému zobrazení.

Existuje několik funkcí vstupního bodu, `CanAddGuideline`například , které se používají k implementaci příkazů, které mění nastavení. Když Visual Studio zobrazuje nabídky, dotazuje se implementace příkazů, aby zjistil, zda je příkaz aktuálně povolen, jaký je jeho název a tak dále.  Níže vidíte, jak připojit tyto vstupní body pro implementace příkazu. Další informace o příkazech naleznete v tématu [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementace třídy ColumnGuideAdornment
Třída `ColumnGuideAdornment` je vytvořena instance pro každé zobrazení textu, které může mít vylepšení. Tato třída naslouchá událostem o změně zobrazení nebo změně nastavení a aktualizaci nebo překreslování sloupcových vodítek podle potřeby.

Obsah *ColumnGuideAdornment.cs* nahraďte následujícím kódem (vysvětleno níže):

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

Instance této třídy se drží <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> přidružené a `Line` seznam objektů nakreslených v zobrazení.

Konstruktor (volaný z `ColumnGuideAdornmentTextViewCreationListener` doby, kdy Visual `Line` Studio vytvoří nová zobrazení) vytvoří objekty vodítka sloupců.  Konstruktor také přidá `SettingsChanged` obslužné `GuidesSettingsManager`rutiny pro `LayoutChanged` událost `Closed`(definované v ) a události zobrazení a .

Událost `LayoutChanged` je vyvolána z důvodu několika druhů změn v zobrazení, včetně při visual studio vytvoří zobrazení. Obslužná rutina `OnViewLayoutChanged` volá `AddGuidelinesToAdornmentLayer` ke spuštění. Kód v `OnViewLayoutChanged` aplikaci určuje, zda je třeba aktualizovat umístění řádků na základě změn, jako jsou změny velikosti písma, zobrazení okapů, vodorovné posouvání a tak dále. Kód v `UpdatePositions` způsobí, že vodicí čáry kreslit mezi znaky nebo těsně za sloupce textu, který je v zadaném znaku posun v řádku textu.

Kdykoli nastavení `SettingsChanged` změnit funkci jen `Line` obnoví všechny objekty s bez ohledu na nové nastavení jsou. Po nastavení polohy řádku kód odstraní `Line` všechny předchozí `ColumnGuideAdornment` objekty z vrstvy vylepšení a přidá nové.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definování příkazů, nabídek a umístění nabídek
Může být hodně deklarování příkazů a nabídek, umístění skupin příkazů nebo nabídek na různé jiné nabídky a zapisování obslužných rutin příkazů. Tento návod zvýrazní, jak příkazy fungují v tomto rozšíření, ale hlubší informace naleznete v [tématu Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Úvod do kódu
Rozšíření Vodítka sloupců zobrazuje deklarování skupiny příkazů, které patří k sobě (přidání sloupce, odebrání sloupce, změna barvy čáry) a následné umístění této skupiny do dílčí nabídky kontextové nabídky editoru.  Rozšíření Vodítka sloupců také přidá příkazy do hlavní nabídky **Úpravy,** ale udržuje je neviditelné, popisované jako společný vzor níže.

Implementace příkazů má tři části: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage.vsct a ColumnGuideCommands.cs. Kód generovaný šablonami umístí příkaz do nabídky **Nástroje,** který jako implementaci zobrazí dialogové okno. Můžete se podívat na to, jak je implementována v *.vsct* a *ColumnGuideCommands.cs* soubory, protože je jednoduché. Můžete nahradit kód v těchto souborech níže.

Kód balíčku obsahuje často používané deklarace požadované pro Visual Studio zjistit, že rozšíření nabízí příkazy a zjistit, kam umístit příkazy. Když se balíček inicializuje, vytvoří instance třídy implementace příkazů. Další informace o balíčcích týkajících se příkazů naleznete v [tématu Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Vzor běžných příkazů
Příkazy v rozšíření Vodítka sloupců jsou příkladem velmi běžného vzoru v sadě Visual Studio. Vložíte související příkazy do skupiny a vložíte ji do`<CommandFlag>CommandWellOnly</CommandFlag>`hlavní nabídky, často s " " nastaveným tak, aby byl příkaz neviditelný.  Umístění příkazů do hlavních nabídek (například **Upravit)** jim dává pěkné názvy (například **Edit.AddColumnGuide),** které jsou užitečné pro hledání příkazů při opětovném přiřazení klíčů v opcích **nástroje**. Je také užitečné pro získání dokončení při vyvolání příkazů z **příkazového okna**.

Potom přidáte skupinu příkazů do kontextových nabídek nebo dílčích nabídek, kde očekáváte, že uživatel bude používat příkazy. Visual Studio `CommandWellOnly` považuje příznak neviditelnosti pouze pro hlavní nabídky. Pokud umístíte stejnou skupinu příkazů do kontextové nabídky nebo dílčí nabídky, příkazy jsou viditelné.

Jako součást společného vzoru vytvoří rozšíření Vodítka sloupců druhou skupinu, která obsahuje jednu dílčí nabídku. Dílčí nabídka zase obsahuje první skupinu s příkazy průvodce čtyřmi sloupci. Druhá skupina, která obsahuje dílčí nabídku, je opakovaně použitelný datový zdroj, který umístíte do různých kontextových nabídek, které umístí dílčí nabídku do těchto kontextových nabídek.

### <a name="the-vsct-file"></a>Soubor .vsct
Soubor *.vsct* deklaruje příkazy a kam jdou, spolu s ikonami a tak dále. Nahraďte obsah souboru *.vsct* následujícím kódem (vysvětleno níže):

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

**Identifikátory GUID**. Pro Visual Studio najít obslužné rutiny příkazů a vyvolat je, je třeba zajistit, aby identifikátor GUID balíčku deklarovaný v *souboru ColumnGuideCommandsPackage.cs* (generovanéze šablony položky projektu) odpovídá identifikátoru GUID balíčku deklarovanému v souboru *.vsct* (zkopírovaný shora). Pokud znovu použijete tento ukázkový kód, měli byste se ujistit, že máte jiný identifikátor GUID, abyste nebyli v konfliktu s nikým jiným, kdo mohl tento kód zkopírovat.

Vyhledejte tento řádek v *ColumnGuideCommandsPackage.cs* a zkopírujte identifikátor GUID z mezi uvozovkami:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Potom vložte identifikátor GUID do souboru *.vsct,* abyste `Symbols` měli v deklaracích následující řádek:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Identifikátory GUID pro sadu příkazů a soubor bitmapového obrazu by měly být jedinečné i pro vaše rozšíření:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

Ale není nutné měnit sadu příkazů a bitmapové image GUID v tomto návodu získat kód do práce. Příkaz nastavit GUID musí odpovídat prohlášení v *souboru ColumnGuideCommands.cs,* ale nahradit obsah tohoto souboru, taky; proto se budou odpovídat identifikátorům GUID.

Jiné identifikátory GUID v souboru *.vsct* identifikují již existující nabídky, do kterých jsou přidány příkazy průvodce sloupcem, takže se nikdy nezmění.

**Oddíly souborů**. *.vsct* má tři vnější oddíly: příkazy, umístění a symboly. Oddíl příkazů definuje skupiny příkazů, nabídky, tlačítka nebo položky nabídky a bitmapy pro ikony. Sekce Umístění deklaruje, kam skupiny přejdou v nabídkách nebo dalších umístěních do již existujících nabídek. Sekce symbolů deklaruje identifikátory používané jinde v souboru *.vsct,* což činí kód *.vsct* čitelnější než identifikátory GUID a šestnáctková čísla všude.

**Sekce Příkazy, definice skupin**. Oddíl příkazů nejprve definuje skupiny příkazů. Skupiny příkazů jsou příkazy, které vidíte v nabídkách s mírnými šedými čarami oddělujícími skupiny. Skupina může také vyplnit celou dílčí nabídku, jako v tomto příkladu, a v tomto případě nevidíte šedé oddělující čáry. *Soubory .vsct* `GuidesMenuItemsGroup` deklarují dvě skupiny, které jsou nadřazené `IDM_VS_MENU_EDIT` (hlavní nabídka **upravit)** a `GuidesContextMenuGroup` které jsou nadřazené `IDM_VS_CTXT_CODEWIN` (kontextová nabídka editoru kódu).

Druhé skupinové prohlášení `0x0600` má prioritu:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Cílem je umístit dílčí nabídku sloupcových průvodců na konec libovolné kontextové nabídky, do které přidáte skupinu dílčích nabídek. Ale neměli byste předpokládat, že víte nejlépe a vynutit dílčí `0xFFFF`menu, aby bylo vždy poslední pomocí priority . Musíte experimentovat s číslem, abyste zjistili, kde se vaše dílčí nabídka nachází v kontextových nabídkách, kam ji umístíte. V tomto `0x0600` případě je dostatečně vysoká, aby ji na konci menu, pokud můžete vidět, ale ponechává prostor pro někoho jiného navrhnout jejich rozšíření být nižší než rozšíření vodítka sloupců, pokud je to žádoucí.

**Oddíl Příkazy, definice nabídky**. Dále příkazový oddíl definuje dílčí `GuidesSubMenu`nabídku , `GuidesContextMenuGroup`nadřazenou na . Jedná `GuidesContextMenuGroup` se o skupinu, kterou přidáte do všech relevantních kontextových nabídek. V části Umístění kód umístí skupinu pomocí příkazů průvodce čtyřmi sloupci v této dílčí nabídce.

**Sekce Příkazy, definice tlačítek**. Oddíl příkazy pak definuje položky nabídky nebo tlačítka, které jsou příkazy čtyřsloupcových průvodců. `CommandWellOnly`, popsané výše, znamená, že příkazy jsou neviditelné, když jsou umístěny v hlavní nabídce. Dvě deklarace tlačítek položky nabídky (přidat průvodce a `AllowParams` odebrat průvodce) mají také příznak:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Tento příznak umožňuje, spolu s umístění hlavní nabídky, příkaz přijímat argumenty při Visual Studio vyvolá obslužnou rutinu příkazu.  Pokud uživatel spustí příkaz z příkazového okna, argument je předán obslužné rutině příkazu v argumentech události.

**Příkazové sekce, definice bitmap**. Nakonec sekce příkazů deklaruje bitmapy nebo ikony použité pro příkazy. Tato část je jednoduché prohlášení, které identifikuje zdroj projektu a uvádí jeden založený indexy použitých ikon. Sekce symboly souboru *.vsct* deklaruje hodnoty identifikátorů používaných jako indexy. Tento návod používá bitmapový proužek dodaný s vlastní šablonou příkazové položky přidané do projektu.

**Sekce Umístění**. Po příkazy sekce je umístění sekce. První z nich je místo, kde kód přidá první skupinu popsané výše, která obsahuje příkazy průvodce čtyřmi sloupci do podnabídky, kde se příkazy zobrazují:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Všechna ostatní umístění přidat `GuidesContextMenuGroup` (který obsahuje `GuidesSubMenu`) do jiných kontextových nabídek editoru. Když kód deklaroval `GuidesContextMenuGroup`, byl nadřazený do kontextové nabídky editoru kódu. To je důvod, proč nevidíte umístění pro kontextové nabídky editoru kódu.

**Sekce symbolů**. Jak je uvedeno výše, symboly sekce deklaruje identifikátory používané jinde v souboru *.vsct,* což činí *.vsct* kód čitelnější než s GUID a šestnáctková čísla všude. Důležité body v této části jsou, že guid balíčku musí souhlasit s deklarací ve třídě balíčku. A guid sady příkazů musí souhlasit s deklarací ve třídě implementace příkazu.

## <a name="implement-the-commands"></a>Implementace příkazů
Soubor *ColumnGuideCommands.cs* implementuje příkazy a zapojí obslužné rutiny. Když Visual Studio načte balíček a inicializuje `Initialize` jej, balíček zase volá na příkazy implementace třídy. Inicializace příkazů jednoduše konkretizovat třídy a konstruktor zapojuje všechny obslužné rutiny příkazu.

Nahraďte obsah *souboru ColumnGuideCommands.cs* následujícím kódem (vysvětleno níže):

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

**Opravte odkazy**. V tuto chvíli vám chybí odkaz. Stiskněte pravé tlačítko ukazatele v uzlu Reference v Průzkumníku řešení. Zvolte příkaz **Přidat ...** . Dialogové okno **Přidat odkaz** má v pravém horním rohu vyhledávací pole. Zadejte "editor" (bez dvojitých uvozovek). Zvolte položku **Microsoft.VisualStudio.Editor** (musíte zaškrtnout políčko nalevo od položky, ne jen vybrat položku) a zvolte **OK** pro přidání odkazu.

**Inicializace**.  Když se inicializuje třída `Initialize` balíčku, volá na třídu implementace příkazů. Inicializace `ColumnGuideCommands` instanci třídy a uloží instance třídy a odkaz na balíček v členy třídy.

Podívejme se na jeden z příkazu obslužné připojení z konstruktoru třídy:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Vytvoření . `OleMenuCommand` Visual Studio používá příkazový systém Microsoft Office. Klíčové argumenty při vytváření instancí `OleMenuCommand` a je funkce,`AddColumnGuideExecuted`která implementuje příkaz ( ), funkce`AddColumnGuideBeforeQueryStatus`volat při Visual Studio zobrazuje nabídku s příkazem ( ) a ID příkazu. Visual Studio volá funkci stavu dotazu před zobrazením příkazu v nabídce tak, aby příkaz může být sám neviditelný nebo šedě pro konkrétní zobrazení nabídky (například zakázání **Copy,** pokud není žádný výběr), změnit jeho ikonu nebo dokonce změnit jeho název (například z Přidat něco odebrat něco) a tak dále. ID příkazu se musí shodovat s ID příkazu deklarovaným v souboru *.vsct.* Řetězce pro sadu příkazů a příkazy pro přidání sloupců se musí shodovat mezi souborem *.vsct* a *ColumnGuideCommands.cs*.

Následující řádek poskytuje pomoc při vyvolání příkazu uživateli prostřednictvím příkazového okna (vysvětleno níže):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Stav dotazu**. Funkce stavu `AddColumnGuideBeforeQueryStatus` dotazu a `RemoveColumnGuideBeforeQueryStatus` zkontrolujte některá nastavení (například maximální počet vodítek nebo sloupec max) nebo pokud existuje průvodce sloupcem, který chcete odebrat. Povolují příkazy, pokud jsou podmínky správné.  Funkce stavu dotazu musí být efektivní, protože jsou spuštěny pokaždé, když Visual Studio zobrazí nabídku a pro každý příkaz v nabídce.

 **Funkce AddColumnGuideExecuted**. Zajímavou součástí přidání průvodce je zjištění aktuálního zobrazení editoru a umístění stříšky.  Nejprve tato `GetApplicableColumn`funkce volá , která zkontroluje, zda je v argumentech události obslužné rutiny příkazu argument uživatelem, a pokud žádná neexistuje, funkce zkontroluje zobrazení editoru:

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

`GetCurrentEditorColumn`musí trochu kopat, aby <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> získal přehled o kódu.  Pokud trasujete přes `GetActiveTextView`, `GetActiveView`a `GetTextViewFromVsTextView`, můžete vidět, jak to udělat. Následující kód je příslušný kód abstrahované, počínaje aktuální výběr, pak získání výběru rámce, pak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>získání rámce <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> DocView jako , pak dostat z IVsTextView, pak získání zobrazení hostitele, a nakonec IWpfTextView:

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

Jakmile budete mít IWpfTextView, můžete získat sloupec, kde se nachází stříška:

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

S aktuálním sloupcem v ruce, kde uživatel kliknul, kód pouze volá správce nastavení přidat nebo odebrat sloupec. Správce nastavení spustí událost, `ColumnGuideAdornment` které všechny objekty poslouchat. Když se událost spustí, tyto objekty aktualizují jejich přidružená zobrazení textu pomocí nového nastavení průvodce sloupci.

## <a name="invoke-command-from-the-command-window"></a>Příkaz Vyvolat z příkazového okna
Ukázka vodítek sloupců umožňuje uživatelům vyvolat dva příkazy z příkazového okna jako formu rozšiřitelnosti. Pokud používáte příkaz **Zobrazit &#124; jiné příkazové okno &#124; systému Windows,** zobrazí se příkazové okno. S příkazovým oknem můžete pracovat zadáním příkazu "edit", a s dokončením názvu příkazu a zadáním argumentu 120 máte následující výsledek:

```csharp
> Edit.AddColumnGuide 120
>
```

Části ukázky, které umožňují toto chování jsou v *.vsct* deklarace souboru, konstruktor `ColumnGuideCommands` třídy při zapisování příkazobslužné rutiny a implementace obslužné rutiny příkazu, které kontrolují argumenty události.

V souboru`<CommandFlag>CommandWellOnly</CommandFlag>` *.vsct* i umístěních v hlavní nabídce **Upravit** jste viděli " ", i když příkazy nejsou zobrazeny v uzdu v nabídce **Úpravy.** Mít je v hlavní nabídce **Upravit** jim dává názvy jako **Edit.AddColumnGuide**. Deklarace skupiny příkazů, která obsahuje čtyři příkazy, umístila skupinu přímo do nabídky **Úpravy:**

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Sekce tlačítek později deklarovala příkazy, `CommandWellOnly` aby byly `AllowParams`v hlavním menu neviditelné, a deklarovala je pomocí :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Viděli jste kód připojení obslužné rutiny příkazu v konstruktoru `ColumnGuideCommands` třídy, který poskytl popis povoleného parametru:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Viděli jste `GetApplicableColumn` funkci `OleMenuCmdEventArgs` kontroly hodnoty před kontrolou zobrazení editoru pro aktuální sloupec:

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

## <a name="try-your-extension"></a>Vyzkoušejte rozšíření
Nyní můžete stisknout **klávesu F5** a provést rozšíření Vodítka sloupců. Otevřete textový soubor a pomocí kontextové nabídky editoru přidejte vodicí čáry, odeberte je a změňte jejich barvu. Klepnutím do textu (ne do mezery předaný na konci řádku) přidáte vodítko sloupce nebo jej editor přidá do posledního sloupce na řádku. Pokud použijete příkazové okno a vyvoláte příkazy s argumentem, můžete vodítka sloupců přidat kamkoli.

Pokud chcete vyzkoušet různá umístění příkazů, změnit názvy, změnit ikony a tak dále a máte nějaké problémy s visual studio zobrazující nejnovější kód v nabídkách, můžete obnovit experimentální podregistr, ve kterém ladíte. Vydejte **nabídku Start systému Windows** a zadejte "reset". Vyhledejte a spusťte příkaz **Obnovit další experimentální instance sady Visual Studio**. Tento příkaz vyčistí podregistr experimentálníregistru všech součástí rozšíření. Nečistí nastavení z komponent, takže všechny průvodce, které jste měli při vypnutí experimentální podregistr visual studio jsou stále k dispozici při kódu čte úložiště nastavení při příštím spuštění.

## <a name="finished-code-project"></a>Dokončený projekt kódu
Brzy bude projekt GitHub ukázky rozšiřitelnosti sady Visual Studio a dokončený projekt bude tam. Tento článek bude aktualizován tak, aby tam, když se to stane. Dokončený ukázkový projekt může mít různé identifikátory GUID a bude mít pro ikony příkazů jiný rastrový proužek.

Můžete vyzkoušet verzi funkce průvodce sloupci s tímto[rozšířením](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)Galerie sady Visual Studio .

## <a name="see-also"></a>Viz také
- [Uvnitř editoru](../extensibility/inside-the-editor.md)
- [Rozšíření editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md)
- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
- [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md)
- [Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)
