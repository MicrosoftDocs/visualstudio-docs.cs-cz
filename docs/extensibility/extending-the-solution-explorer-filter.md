---
title: Rozšíření filtru Průzkumníka řešení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711562"
---
# <a name="extend-the-solution-explorer-filter"></a>Rozšíření filtru Průzkumníka řešení
Můžete rozšířit funkci filtru **Průzkumníka řešení** a zobrazit nebo skrýt různé soubory. Můžete například vytvořit filtr, který zobrazuje pouze soubory factory třídy C# v **Průzkumníku řešení**, jak ukazuje tento návod.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Vytvoření projektu balíčku sady Visual Studio

1. Vytvořte projekt VSIX s názvem `FileFilter`. Přidejte vlastní šablonu položky příkazu s názvem **FileFilter**. Další informace naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Přidejte odkaz `System.ComponentModel.Composition` `Microsoft.VisualStudio.Utilities`na a .

3. Zobrazil se příkaz nabídky na panelu nástrojů **Průzkumník a řešení.** Otevřete soubor *FileFilterPackage.vsct.*

4. Změňte `<Button>` blok na následující:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Aktualizace souboru manifestu

1. V souboru *source.extension.vsixmanifest* přidejte datový zdroj, který je součástí MEF.

2. Na kartě **Datové zdroje** zvolte **tlačítko Nový.**

3. V poli **Typ** zvolte **Microsoft.VisualStudio.MefComponent**.

4. V poli **Zdroj** zvolte **Projekt A v aktuálním řešení**.

5. V poli **Projekt** zvolte **FileFilter**a pak zvolte tlačítko **OK.**

### <a name="add-the-filter-code"></a>Přidání kódu filtru

1. Do souboru *FileFilterPackageGuids.cs* přidejte některé identifikátory GUID:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Přidejte soubor třídy do projektu FileFilter s názvem *FileNameFilter.cs*.

3. Nahraďte prázdný obor názvů a prázdnou třídu níže uvedenou kódovou třídou.

     Metoda `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` přebírá kolekci, která obsahuje kořen`rootItems`řešení ( ) a vrátí kolekci položek, které mají být zahrnuty do filtru.

     Metoda `ShouldIncludeInFilter` filtruje položky v hierarchii **Průzkumníka řešení** na základě zadané podmínky.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. V *FileFilter.cs*odeberte příkaz umístění a zpracování kódu z FileFilter konstruktoru. Výsledek by měl vypadat takto:

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     Odstraňte `ShowMessageBox()` také metodu.

5. V *FileFilterPackage.cs*nahraďte `Initialize()` kód v metodě tímto:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Testování kódu

1. Sestavení a spuštění projektu. Zobrazí se druhá instance sady Visual Studio. Tomu se říká experimentální instance.

2. V experimentální instanci sady Visual Studio otevřete projekt Jazyka C#.

3. Vyhledejte tlačítko, které jste přidali na panelu nástrojů **Průzkumník a řešení.** Mělo by to být čtvrté tlačítko zleva.

4. Po klepnutí na tlačítko by měly být odfiltrovány všechny soubory a měli byste vidět, že **všechny položky byly filtrovány ze zobrazení.** v **Průzkumníku řešení**.
