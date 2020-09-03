---
title: Vytváření doplňků, příkazů a nastavení zobrazení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a2df0a3-42da-4f7b-996f-ee16a35ac922
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c4be60f2285edb986d5ca7a1cf4a2202e03c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905041"
---
# <a name="walkthrough-create-a-view-adornment-commands-and-settings-column-guides"></a>Návod: vytvoření vylepšení zobrazení, příkazů a nastavení (vodítka sloupců)
Můžete roztáhnout text nebo Editor kódu sady Visual Studio pomocí příkazů a zobrazení efektů. V tomto článku se dozvíte, jak začít s oblíbenými funkcemi rozšíření, vodítky sloupců. Vodítka sloupců jsou vizuálně světlé čáry vykreslené v zobrazení textový editor, které vám pomohou spravovat kód pro konkrétní šířku sloupců. Konkrétně formátovaný kód může být důležitý pro ukázky, které zahrnete do dokumentů, příspěvků na blogu nebo hlášení o chybách.

V tomto návodu:
- Vytvoření projektu VSIX
- Přidat vylepšení zobrazení editoru
- Přidání podpory pro ukládání a získávání nastavení (kde nakreslit vodítka sloupců a jejich barvu)
- Přidat příkazy (přidat/odebrat vodítka sloupců, změnit jejich barvu)
- Umístit příkazy do nabídky upravit a do kontextových nabídek textového dokumentu
- Přidání podpory pro vyvolání příkazů z příkazového okna sady Visual Studio

  Pomocí tohoto[rozšíření](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)galerie sady Visual Studio můžete vyzkoušet verzi funkcí vodítek sloupců.

  > [!NOTE]
  > V tomto návodu vložíte Skvělé množství kódu do několika souborů generovaných šablonami rozšíření sady Visual Studio. Ale brzo tento návod bude odkazovat na dokončené řešení na GitHubu s dalšími příklady rozšíření. Dokončený kód se mírně liší v tom, že má ikony reálného příkazu namísto použití ikon generictemplate.

## <a name="get-started"></a>Začínáme
Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="set-up-the-solution"></a>Nastavení řešení
Nejprve vytvoříte projekt VSIX, přidáte doplňky zobrazení editoru a potom přidáte příkaz (který přidá VSPackage do vlastního příkazu). Základní architektura je následující:
- Máte naslouchací proces vytváření zobrazení textu, který vytváří `ColumnGuideAdornment` objekt pro zobrazení. Tento objekt čeká na události týkající se změny zobrazení nebo změny nastavení, aktualizace a vykreslení vodítek sloupců podle potřeby.
- K dispozici je modul `GuidesSettingsManager` , který zpracovává čtení a zápis z úložiště nastavení sady Visual Studio. Správce nastavení také obsahuje operace pro aktualizaci nastavení podporujících příkazy uživatele (přidat sloupec, odebrat sloupec, změnit barvu).
- K dispozici je balíček VSIP, který je nezbytný, pokud máte uživatelské příkazy, ale právě se jedná o často používaný kód, který inicializuje objekt implementace příkazů.
- Existuje `ColumnGuideCommands` objekt, který spouští uživatelské příkazy a zavěsí obslužné rutiny příkazů pro příkazy deklarované v souboru *. vsct* .

  **VSIX**. K vytvoření projektu použijte **soubor &#124; New...** Command. V levém navigačním podokně vyberte uzel **rozšiřitelnost** v **C#** a v pravém podokně vyberte **projekt VSIX** . Zadejte název **ColumnGuides** a kliknutím na **tlačítko OK** vytvořte projekt.

  **Zobrazit doplňky** Stiskněte pravé tlačítko ukazatel na uzlu projektu v Průzkumník řešení. Vyberte příkaz **přidat &#124; novou položku...** a přidejte tak novou položku zobrazení. V levém navigačním podokně vyberte **rozšíření &#124; Editor** a v pravém podokně vyberte **Doplňky zobrazení editoru** . Jako název položky zadejte název **ColumnGuideAdornment** a kliknutím na **Přidat** ho přidejte.

  Můžete vidět, že tato šablona položky přidala do projektu dva soubory (stejně jako odkazy atd.): **ColumnGuideAdornment.cs** a **ColumnGuideAdornmentTextViewCreationListener.cs**. Šablony nakreslí fialový obdélník na zobrazení. V následující části změníte několik řádků v naslouchací službě vytváření zobrazení a nahradíte obsah **ColumnGuideAdornment.cs**.

  **Příkazy**. V **Průzkumník řešení**stiskněte pravé tlačítko ukazatel na uzlu projektu. Vyberte příkaz **přidat &#124; novou položku...** a přidejte tak novou položku zobrazení. V levém navigačním podokně vyberte **rozšiřitelnost &#124; VSPackage** a v pravém podokně vyberte **vlastní příkaz** . Jako název položky zadejte název **ColumnGuideCommands** a klikněte na **Přidat**. Kromě několika odkazů přidávání příkazů a balíčků Přidal také **ColumnGuideCommands.cs**, **ColumnGuideCommandsPackage.cs**a **ColumnGuideCommandsPackage. vsct**. V následující části nahradíte obsah prvních a posledních souborů pro definování a implementaci příkazů.

## <a name="set-up-the-text-view-creation-listener"></a>Nastavení naslouchacího procesu pro vytváření zobrazení textu
Otevřete *ColumnGuideAdornmentTextViewCreationListener.cs* v editoru. Tento kód implementuje obslužnou rutinu pro každé, když aplikace Visual Studio vytvoří zobrazení textu. Existují atributy, které řídí, kdy je obslužná rutina volána v závislosti na vlastnostech zobrazení.

Kód musí také deklarovat vrstvu doplňku. Když editor aktualizuje zobrazení, získá vrstvy přípravcích pro zobrazení a z, které získá prvky Doplňky. Pořadí vrstev můžete deklarovat relativně k ostatním atributům. Nahraďte následující řádek:

```csharp
[Order(After = PredefinedAdornmentLayers.Caret)]
```

s těmito dvěma řádky:

```csharp
[Order(Before = PredefinedAdornmentLayers.Text)]
[TextViewRole(PredefinedTextViewRoles.Document)]
```

Řádek, který jste nahradili, je ve skupině atributů, které deklaruje vrstvu doplňku. První řádek, který jste změnili, se změní pouze v případě, že se zobrazí čáry vodítka sloupce. Kreslení čar "před" textem v zobrazení znamená, že se zobrazí za textem nebo pod ním. Druhý řádek deklaruje, že doplňky sloupců jsou použitelné pro textové entity, které odpovídají vašemu pojmu dokumentu, ale je možné deklarovat například doplňky, aby fungovala pouze pro upravitelný text. V [jazykových službách a rozšiřovacích bodech editoru](../extensibility/language-service-and-editor-extension-points.md) jsou další informace.

## <a name="implement-the-settings-manager"></a>Implementace správce nastavení
Nahraďte obsah *GuidesSettingsManager.cs* následujícím kódem (vysvětleno níže):

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

Většina tohoto kódu vytváří a analyzuje formát nastavení: "RGB ( \<int> , \<int> , \<int> ) \<int> , \<int> ,...".  Celá čísla na konci jsou sloupce založené na jednom, kde chcete mít vodítka sloupců. Rozšíření pro vodítka sloupců zachycuje všechna jeho nastavení v jednom řetězci hodnot nastavení.

Jsou zde zvýrazněny některé části kódu. Následující řádek kódu získá spravovanou obálku sady Visual Studio pro úložiště nastavení. Ve většině případů tato abstrakce v registru systému Windows, ale toto rozhraní API je nezávislé na mechanismu úložiště.

```csharp
internal static SettingsManager VsManagedSettingsManager =
    new ShellSettingsManager(ServiceProvider.GlobalProvider);
```

Úložiště nastavení sady Visual Studio používá identifikátor kategorie a identifikátor nastavení k jedinečné identifikaci všech nastavení:

```csharp
private const string _collectionSettingsName = "Text Editor";
private const string _settingName = "Guides";
```

Nemusíte používat `"Text Editor"` jako název kategorie. Můžete si vybrat cokoli, co chcete.

První pár funkcí je vstupním bodem pro změnu nastavení. Kontrolují omezení vysoké úrovně, jako je povolený maximální počet průvodců.  Potom volají `WriteSettings` , který vytvoří řetězec nastavení a nastaví vlastnost `GuideLinesConfiguration` . Nastavením této vlastnosti se uloží hodnota nastavení do úložiště nastavení sady Visual Studio a aktivuje `SettingsChanged` událost pro aktualizaci všech `ColumnGuideAdornment` objektů, z nichž každá je přidružena k textovému zobrazení.

Existuje několik funkcí vstupního bodu, například `CanAddGuideline` , které slouží k implementaci příkazů, které mění nastavení. Když aplikace Visual Studio zobrazuje nabídky, dotazuje se na příkazy pro zjištění, zda je příkaz aktuálně povolen, jaký je jeho název a tak dále.  Níže vidíte, jak připojit tyto vstupní body pro implementace příkazů. Další informace o příkazech naleznete v tématu [rozšiřuje nabídky a příkazy](../extensibility/extending-menus-and-commands.md).

## <a name="implement-the-columnguideadornment-class"></a>Implementace třídy ColumnGuideAdornment
`ColumnGuideAdornment`Třída je vytvořena pro každé textové zobrazení, které může mít doplňky. Tato třída poslouchá události týkající se změny zobrazení nebo změny nastavení a v případě potřeby aktualizuje nebo překreslí vodítka sloupců.

Nahraďte obsah *ColumnGuideAdornment.cs* následujícím kódem (vysvětleno níže):

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

Instance této třídy jsou podrženy na přidruženém <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> a seznamu `Line` objektů vykreslených v zobrazení.

Konstruktor (volá se, `ColumnGuideAdornmentTextViewCreationListener` když aplikace Visual Studio vytvoří nová zobrazení) vytvoří objekty vodítka sloupců `Line` .  Konstruktor také přidává obslužné rutiny pro `SettingsChanged` událost (definovaná v `GuidesSettingsManager` ) a události zobrazení `LayoutChanged` a `Closed` .

`LayoutChanged`Událost je aktivována v důsledku několika druhů změn v zobrazení, včetně toho, kdy aplikace Visual Studio vytvoří zobrazení. `OnViewLayoutChanged`Obslužná rutina volá metodu `AddGuidelinesToAdornmentLayer` Execute. Kód v `OnViewLayoutChanged` Určuje, zda musí aktualizovat pozice řádků na základě změn, jako jsou změny velikosti písma, zobrazení hřbetů, horizontální posouvání atd. Kód v nástroji `UpdatePositions` způsobuje, že čáry Průvodce kreslí mezi znaky nebo těsně za sloupcem textu, který je v zadaném posunu znaku v řádku textu.

Vždy, když se změní nastavení `SettingsChanged` funkce, znovu vytvoří všechny `Line` objekty bez ohledu na to, jaká jsou nová nastavení. Po nastavení pozice řádků kód odstraní všechny předchozí `Line` objekty z `ColumnGuideAdornment` vrstvy úprav a přidá nové.

## <a name="define-the-commands-menus-and-menu-placements"></a>Definice příkazů, nabídek a míst pro nabídky
K deklarování příkazů a nabídek, umístění skupin příkazů nebo nabídek do různých nabídek a k zapojení obslužných rutin příkazů se může nacházet hodně. Tento názorný postup popisuje, jak fungují příkazy v tomto rozšíření, ale pro hlubší informace viz téma [rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md).

### <a name="introduction-to-the-code"></a>Úvod do kódu
Přípona vodítek sloupců znázorňuje deklaraci skupiny příkazů, které patří dohromady (přidání sloupce, odebrání sloupce, změna barvy čáry) a následné umístění této skupiny do podnabídky místní nabídky editoru.  Rozšíření vodítek sloupců také přidá příkazy do hlavní nabídky pro **Úpravy** , ale ponechá je neviditelná, popsané jako společný vzor.

Existují tři části pro implementaci příkazů: ColumnGuideCommandsPackage.cs, ColumnGuideCommandsPackage. vsct a ColumnGuideCommands.cs. Kód vygenerovaný šablonami Vloží příkaz v nabídce **nástroje** , který jako implementaci vyvolá dialogové okno. Můžete se podívat na to, jak je implementováno v souborech *. vsct* a *ColumnGuideCommands.cs* , protože je jednoduché. Nahraďte kód v těchto souborech níže.

Kód balíčku obsahuje často používané deklarace, které se vyžadují pro Visual Studio, aby se zjistilo, že rozšíření nabízí příkazy a hledá, kam se mají příkazy umístit. Po inicializaci balíčku se vytvoří instance třídy implementace příkazů. Další informace o balíčcích, které se týkají příkazů, najdete v tématu věnovaném [rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md).

### <a name="a-common-commands-pattern"></a>Vzor běžných příkazů
Příkazy v rozšíření vodítek sloupců jsou příkladem velmi společného vzoru v aplikaci Visual Studio. Do skupiny vložíte související příkazy a tuto skupinu vložíte do hlavní nabídky, často pomocí příkazu " `<CommandFlag>CommandWellOnly</CommandFlag>` " nastavené tak, aby příkaz nebyl neviditelný.  Vložení příkazů do hlavních nabídek (například **Upravit**) dává smysluplné názvy (například **Edit. AddColumnGuide**), které jsou užitečné při hledání příkazů při opětovném přiřazování klíčových vazeb v **možnostech nástrojů**. Je také užitečné při vyvolání příkazů z **příkazového okna**.

Pak přidáte skupinu příkazů do kontextových nabídek nebo dílčích nabídek, ve kterých očekáváte, že uživatel bude používat příkazy. Visual Studio se považuje `CommandWellOnly` za příznak inviditelnosti jenom pro hlavní nabídky. Když umístíte stejnou skupinu příkazů do kontextové nabídky nebo podnabídky, budou tyto příkazy viditelné.

Jako součást společného vzoru přípona sloupců vytvoří druhou skupinu, která obsahuje jednu dílčí nabídku. Podnabídka zase obsahuje první skupinu s příkazy Průvodce čtyřmi sloupci. Druhá skupina, která obsahuje podnabídku, je opakovaně použitelný prostředek, který umístíte do různých kontextových nabídek, který do těchto kontextových nabídek umístí podnabídku.

### <a name="the-vsct-file"></a>Soubor. vsct
Soubor *. vsct* deklaruje příkazy a tam, kde jsou, spolu s ikonami a tak dále. Obsah souboru *. vsct* nahraďte následujícím kódem (vysvětleno níže):

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

**Identifikátory GUID**. Aby sada Visual Studio mohla najít obslužné rutiny příkazů a vyvolat je, je nutné zajistit, aby byl identifikátor GUID balíčku deklarovaný v souboru *ColumnGuideCommandsPackage.cs* (vygenerovaný ze šablony položky projektu) SHODNÝ s identifikátorem GUID balíčku deklarovaným v souboru *. vsct* (zkopírovaným z výše). Pokud tento vzorový kód znovu použijete, měli byste se ujistit, že máte jiný identifikátor GUID, aby nedošlo ke konfliktu s kýmkoli, kdo mohl tento kód zkopírovat.

Najde tento řádek v *ColumnGuideCommandsPackage.cs* a kopíruje GUID mezi uvozovky:

```csharp
public const string PackageGuidString = "ef726849-5447-4f73-8de5-01b9e930f7cd";
```

Pak vložte identifikátor GUID do souboru *. vsct* , abyste měli v `Symbols` deklaracích následující řádek:

```xml
<GuidSymbol name="guidColumnGuideCommandsPkg"
            value="{ef726849-5447-4f73-8de5-01b9e930f7cd}" />
```

Identifikátory GUID pro sadu příkazů a soubor rastrového obrázku by měly být pro vaše rozšíření jedinečné:

```xml
<GuidSymbol name="guidColumnGuidesCommandSet"
            value="{c2bc0047-8bfa-4e5a-b5dc-45af8c274d8e}">
<GuidSymbol name="guidImages" value="{2C99F852-587C-43AF-AA2D-F605DE2E46EF}">
```

V tomto návodu ale nemusíte měnit sadu příkazů a identifikátory GUID rastrových obrázků, abyste mohli kód pracovat. Identifikátor GUID sady příkazů musí odpovídat deklaraci v souboru *ColumnGuideCommands.cs* , ale obsah tohoto souboru můžete také nahradit. identifikátory GUID se proto shodují.

Jiné identifikátory GUID v souboru *. vsct* identifikují již existující nabídky, do kterých jsou přidány příkazy Průvodce sloupcem, takže se nikdy nezmění.

**Oddíly souborů**. *Přípona. vsct* má tři vnější části: příkazy, umístění a symboly. Oddíl Commands definuje skupiny příkazů, nabídky, tlačítka nebo položky nabídky a rastrové obrázky pro ikony. Oddíl místa deklaruje, kde skupiny přecházejí do nabídek nebo dalších míst do již existujících nabídek. Oddíl symboly deklaruje identifikátory používané jinde v souboru *. vsct* , což umožňuje, aby byl kód *. vsct* čitelnější než identifikátory GUID a hexadecimální čísla všude.

**Oddíl Commands, definice skupin**. Oddíl Commands nejprve definuje skupiny příkazů. Skupiny příkazů jsou příkazy, které vidíte v nabídkách s drobnými šedými čarami, které odděluje skupiny. Skupina může také vyplnit celou dílčí nabídku, jak je uvedeno v tomto příkladu, a v tomto případě se nezobrazuje šedé oddělující čáry. Soubory *. vsct* deklaruje dvě skupiny, `GuidesMenuItemsGroup` které jsou nadřazené do `IDM_VS_MENU_EDIT` (hlavní nabídka **Upravit** ) a `GuidesContextMenuGroup` které jsou nadřazené do `IDM_VS_CTXT_CODEWIN` (kontextová nabídka editoru kódu).

Druhá deklarace skupiny má `0x0600` prioritu:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesContextMenuGroup"
             priority="0x0600">
```

Nápadem je umístit podnabídku vodítek sloupců na konec libovolné kontextové nabídky, do které přidáte skupinu podnabídek. Ale neměli byste předpokládat, že byste měli v podnabídce co nejvýhodnější a vynutit, aby se podnabídka vždy naposledy používala s prioritou `0xFFFF` . Chcete-li zjistit, kde je vaše podnabídka v místních nabídkách umístění, je nutné experimentovat s tímto číslem. V tomto případě `0x0600` je dostatečně vysoko umístit na konec nabídek, jak vidíte, ale opustí místo pro někoho jiného, aby navrhli rozšíření, aby bylo nižší než rozšíření vodítek sloupců, pokud je to žádoucí.

**Oddíl Commands, definice nabídky**. Dále oddíl příkazu definuje podnabídku podřízenou `GuidesSubMenu` položce `GuidesContextMenuGroup` . `GuidesContextMenuGroup`Je skupina, kterou přidáte do všech relevantních kontextových nabídek. V části místa, kód umístí skupinu pomocí příkazů Průvodce čtyřmi sloupci v této podnabídce.

**Oddíly příkazů, definice tlačítek**. Oddíl Commands (příkazy) potom definuje položky nabídky nebo tlačítka, která jsou příkazy pro vodítka se čtyřmi sloupci. `CommandWellOnly`, popsané výše, znamená, že příkazy jsou při umístění do hlavní nabídky neviditelné. Dvě deklarace tlačítek položky nabídky (přidat průvodce a odebrat průvodce) mají také `AllowParams` příznak:

```xml
<CommandFlag>AllowParams</CommandFlag>
```

Tento příznak umožňuje společně s umístěními hlavní nabídky, příkazem, který přijímá argumenty při vyvolání obslužné rutiny příkazu v aplikaci Visual Studio.  Pokud uživatel spustí příkaz z příkazového řádku, argument je předán obslužné rutině příkazu v argumentech události.

**Oddíly příkazů, rastry a definice**. Nakonec oddíl Commands deklaruje rastrové obrázky nebo ikony používané pro příkazy. Tato část je jednoduchá deklarace, která identifikuje prostředek projektu a zobrazuje seznam indexů použitých ikon. Oddíl symboly v souboru *. vsct* deklaruje hodnoty identifikátorů používaných jako indexy. V tomto návodu se používá rastrový pruh, který je k dispozici v šabloně položky vlastního příkazu přidané do projektu.

**Část místa**. Po části s příkazy se nachází oddíl místa. První z nich je místo, kde kód přidá první skupinu popsanou výše, která obsahuje příkazy se čtyřmi sloupci, do dílčí nabídky, kde se zobrazují příkazy:

```xml
<CommandPlacement guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
                  priority="0x0100">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesSubMenu" />
</CommandPlacement>
```

Všechna ostatní místa přidávají do `GuidesContextMenuGroup` `GuidesSubMenu` jiných kontextových nabídek editoru (které obsahuje). V případě, že kód `GuidesContextMenuGroup` byl deklarován, byl vytvořen jako nadřazený v místní nabídce editoru kódu. To je důvod, proč nevidíte umístění pro kontextovou nabídku editoru kódu.

**Oddíl symboly**. Jak je uvedeno výše, oddíl symboly deklaruje identifikátory používané jinde v souboru *. vsct* , což usnadňuje čtení kódu *. vsct* , než identifikátory GUID a hexadecimální čísla všude. Důležité body v této části jsou v tom, že GUID balíčku musí souhlasit s deklarací ve třídě Package. A GUID sady příkazů musí souhlasit s deklarací ve třídě implementace příkazu.

## <a name="implement-the-commands"></a>Implementace příkazů
Soubor *ColumnGuideCommands.cs* implementuje příkazy a zavěsí obslužné rutiny. Když aplikace Visual Studio načte balíček a inicializuje jej, balíček v systému zavolá `Initialize` třídu implementující příkazy. Inicializace příkazů jednoduše vytvoří instanci třídy a konstruktor Zapojte všechny obslužné rutiny příkazů.

Obsah souboru *ColumnGuideCommands.cs* nahraďte následujícím kódem (vysvětleno níže):

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

**Opravte odkazy**. V tuto chvíli nechybí odkaz. Stiskněte pravé tlačítko ukazatel na uzlu odkazy v Průzkumník řešení. Klikněte na příkaz **Přidat...** . Dialogové okno **Přidat odkaz** obsahuje vyhledávací pole v pravém horním rohu. Zadejte "Editor" (bez dvojitých uvozovek). Zvolte položku **Microsoft. VisualStudio. Editor** (je nutné zaškrtnout políčko nalevo od položky, ne pouze vybrat položku) a přidat odkaz kliknutím na **tlačítko OK** .

**Inicializace**.  Při inicializaci třídy balíčku volá `Initialize` třídu implementující příkazy. `ColumnGuideCommands`Inicializace vytvoří instanci třídy a uloží instanci třídy a odkaz na balíček do členů třídy.

Pojďme se podívat na jeden z příkazů obsluhy obslužné rutiny z konstruktoru třídy:

```csharp
_addGuidelineCommand =
    new OleMenuCommand(AddColumnGuideExecuted, null,
                       AddColumnGuideBeforeQueryStatus,
                       new CommandID(ColumnGuideCommands.CommandSet,
                                     cmdidAddColumnGuide));

```

Vytvoříte `OleMenuCommand` . Visual Studio používá systém systém Microsoft Officeových příkazů. Klíčové argumenty při vytváření instance `OleMenuCommand` je funkce, která implementuje příkaz ( `AddColumnGuideExecuted` ), funkce, která má být volána, když Visual Studio zobrazí nabídku pomocí příkazu ( `AddColumnGuideBeforeQueryStatus` ) a ID příkazu. Visual Studio volá funkci stavu dotazu před zobrazením příkazu v nabídce tak, že příkaz může být pro konkrétní zobrazení nabídky sám neviditelný nebo šedý (například zakázání **kopírování** , pokud není nic vybráno), změnit jeho ikonu nebo dokonce změnit jeho název (například ze seznamu přidat něco pro odebrání nějakého) a tak dále. ID příkazu musí odpovídat ID příkazu deklarovanému v souboru *. vsct* . Řetězce pro sadu příkazů a vodítka sloupců příkaz Přidat se musí shodovat mezi souborem *. vsct* a *ColumnGuideCommands.cs*.

Následující řádek poskytuje pomoc pro uživatele, kteří vyvolávají příkaz prostřednictvím příkazového okna (vysvětleno níže):

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";
```

 **Dotaz na stav**. Funkce stavu dotazu `AddColumnGuideBeforeQueryStatus` a `RemoveColumnGuideBeforeQueryStatus` zkontroluje některá nastavení (například maximální počet příruček nebo max. sloupec), nebo pokud je k dispozici průvodce sloupcem, který chcete odebrat. Povolují příkazy, pokud jsou podmínky správné.  Funkce stavu dotazu musí být efektivní, protože se spouštějí pokaždé, když Visual Studio zobrazuje nabídku a pro každý příkaz v nabídce.

 **Funkce AddColumnGuideExecuted** Zajímavá část Přidání příručky slouží ke zjištění aktuálního zobrazení editoru a umístění blikajícího kurzoru.  Za prvé tato funkce volá `GetApplicableColumn` , která kontroluje, jestli je v argumentech události obslužné rutiny příkazu zadaný uživatelem, a pokud není žádná, funkce zkontroluje zobrazení editoru:

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

`GetCurrentEditorColumn` pro získání zobrazení kódu je potřeba dig trochu <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .  Pokud provedete trasování `GetActiveTextView` , `GetActiveView` a `GetTextViewFromVsTextView` , můžete vidět, jak to provést. Následující kód je relevantní kód, který je abstraktní, počínaje aktuálním výběrem, poté získá rámec výběru a pak získá objekt DocView snímku jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a pak získá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> z IVsTextView, pak získá z a pak získá hostitele zobrazení a nakonec IWpfTextView:

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

Jakmile budete mít IWpfTextView, můžete získat sloupec, kde se nachází blikající kurzor:

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

S aktuálním sloupcem na místě, kde uživatel kliknul, kód pouze volá správce nastavení, aby mohl sloupec přidat nebo odebrat. Správce nastavení aktivuje událost, na kterou všechny `ColumnGuideAdornment` objekty naslouchají. Když událost aktivuje, tyto objekty aktualizují svoje přidružená textová zobrazení pomocí nového nastavení Průvodce sloupcem.

## <a name="invoke-command-from-the-command-window"></a>Vyvolat příkaz z příkazového okna
Ukázka vodítka sloupců umožňuje uživatelům vyvolat dva příkazy z příkazového okna jako formu rozšiřitelnosti. Pokud použijete příkaz **zobrazit &#124; jiné okno příkazového okna &#124; systému Windows** , můžete zobrazit okno příkazového řádku. S příkazovým oknem můžete pracovat pomocí příkazu "Upravit" a zadáním příkazu "Upravit" a zadáním argumentu 120, máte následující výsledek:

```csharp
> Edit.AddColumnGuide 120
>
```

Části ukázky, které umožňují toto chování, jsou v deklaracích souborů *. vsct* , `ColumnGuideCommands` konstruktoru třídy při zapojení obslužných rutin příkazů a implementace obslužné rutiny příkazu, který kontroluje argumenty události.

V `<CommandFlag>CommandWellOnly</CommandFlag>` souboru *. vsct* jste viděli "", stejně jako místo v nabídce **Upravit** hlavní nabídku, i když příkazy nejsou zobrazeny v uživatelském rozhraní nabídky pro **Úpravy** . Pokud máte v hlavní nabídce pro **Úpravy** názvy, jako je **Edit. AddColumnGuide**. Deklarace skupiny příkazů, která obsahuje čtyři příkazy, které jsou umístěny do skupiny v nabídce **Upravit** přímo:

```xml
<Group guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup"
             priority="0xB801">
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_EDIT" />
      </Group>

```

Oddíl tlačítka později deklaruje příkazy, `CommandWellOnly` aby je zůstaly neviditelné v hlavní nabídce a deklarovaly pomocí `AllowParams` :

```xml
<Button guid="guidColumnGuidesCommandSet" id="cmdidAddColumnGuide"
        priority="0x0100" type="Button">
  <Parent guid="guidColumnGuidesCommandSet" id="GuidesMenuItemsGroup" />
  <Icon guid="guidImages" id="bmpPicAddGuide" />
  <CommandFlag>CommandWellOnly</CommandFlag>
  <CommandFlag>AllowParams</CommandFlag>

```

Zjistili jste, že obslužná rutina příkazu zaznamenala kód v `ColumnGuideCommands` konstruktoru třídy, který poskytuje popis povoleného parametru:

```csharp
_addGuidelineCommand.ParametersDescription = "<column>";

```

Zjistili jste, že `GetApplicableColumn` funkce kontroluje `OleMenuCmdEventArgs` hodnotu před kontrolou zobrazení editoru pro aktuální sloupec:

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

## <a name="try-your-extension"></a>Vyzkoušejte si rozšíření
Stisknutím klávesy **F5** teď můžete spustit rozšíření pro vodítka sloupců. Otevřete textový soubor a pomocí kontextové nabídky editoru přidejte vodicí čáry, odeberte je a změňte jejich barvu. Kliknutím na text (ne mezeru před koncem řádku) přidejte vodítko sloupce nebo ho Editor přidá do posledního sloupce na řádku. Pokud použijete příkazové okno a vyvoláte příkazy s argumentem, můžete přidat vodítka sloupců kdekoli.

Pokud chcete vyzkoušet jiné umístění příkazů, změnit názvy, změnit ikony a tak dále, a máte nějaké problémy se sadou Visual Studio, které vám zobrazí nejnovější kód v nabídkách, můžete obnovit experimentální podregistr, ve kterém provádíte ladění. Otevřete **nabídku Start systému Windows** a zadejte "Reset". Vyhledejte a spusťte příkaz, **resetujte další experimentální instanci sady Visual Studio**. Tento příkaz vyčistí experimentální podregistr registru všech součástí rozšíření. Nečistí nastavení z komponent, takže všechny příručky, které jste měli po vypnutí experimentálního podregistru sady Visual Studio, jsou pořád tam, kde při dalším spuštění přečte váš kód úložiště nastavení.

## <a name="finished-code-project"></a>Dokončený kód projektu
Brzy bude projekt GitHub ukázek rozšiřitelnosti sady Visual Studio a dokončený projekt bude. Tento článek se aktualizuje, aby odkazoval na to, kdy k tomu dojde. Dokončený vzorový projekt může mít odlišné identifikátory GUID a bude mít pro ikony příkazu jiný rastrový obrázek.

Pomocí tohoto[rozšíření](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.EditorGuidelines)galerie sady Visual Studio můžete vyzkoušet verzi funkcí vodítek sloupců.

## <a name="see-also"></a>Viz také
- [Uvnitř editoru](../extensibility/inside-the-editor.md)
- [Rozšiřování editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md)
- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
- [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Přidání podnabídky do nabídky](../extensibility/adding-a-submenu-to-a-menu.md)
- [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)
