---
title: Rozšíření filtru Průzkumníka řešení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf43243abc361df6c5b32b0e71e966c61a501b52
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498785"
---
# <a name="extend-the-solution-explorer-filter"></a>Rozšíření filtru Průzkumníka řešení
Můžete rozšířit **Průzkumníka řešení** filtrování funkce, které umožňuje zobrazit nebo skrýt různé soubory. Například můžete vytvořit filtr zobrazující jenom soubory jazyka C# třída továrny v **Průzkumníka řešení**, jak Tento názorný postup ukazuje.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-visual-studio-package-project"></a>Vytvořte projekt balíčku Visual Studio  
  
1.  Vytvořte projekt VSIX s názvem `FileFilter`. Přidat vlastní příkaz šablonu položky s názvem **FileFilter**. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Přidejte odkaz na `System.ComponentModel.Composition` a `Microsoft.VisualStudio.Utilities`.  
  
3.  Vytvořit příkaz nabídky zobrazí na **Průzkumníka řešení** nástrojů. Otevřít *FileFilterPackage.vsct* souboru.  
  
4.  Změnit `<Button>` bloku pro následující:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### <a name="update-the-manifest-file"></a>Aktualizujte soubor manifestu  
  
1.  V *source.extension.vsixmanifest* přidejte asset, který je součástí MEF.  
  
2.  Na **prostředky** , vyberte **nový** tlačítko.  
  
3.  V **typ** zvolte **Microsoft.VisualStudio.MefComponent**.  
  
4.  V **zdroj** zvolte **projekt v aktuálním řešení**.  
  
5.  V **projektu** zvolte **FileFilter**a klikněte na tlačítko **OK** tlačítko.  
  
### <a name="add-the-filter-code"></a>Přidejte kód filtru  
  
1.  Některé identifikátory GUID pro přidání *FileFilterPackageGuids.cs* souboru:  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Přidejte soubor třídy do projektu FileFilter s názvem *FileNameFilter.cs*.  
  
3.  Prázdný obor názvů a prázdné třídy nahraďte následujícím kódem.  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` Metoda přijímá kolekce, která obsahuje kořenovou složku řešení (`rootItems`) a vrátí kolekci položek, které chcete zahrnout do filtru.  
  
     `ShouldIncludeInFilter` Metoda filtruje položky v **Průzkumníka řešení** hierarchii na základě za předpokladu, že zadáte.  
  
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
  
4.  V *FileFilter.cs*, odeberte umístění příkazu a kód z konstruktoru FileFilter pro zpracování. Výsledek by měl vypadat nějak takto:  
  
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
  
     Odeberte `ShowMessageBox()` také metody.  
  
5.  V *FileFilterPackage.cs*, nahraďte kód v `Initialize()` metoda následujícím kódem:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>Testování kódu  
  
1.  Sestavte a spusťte projekt. Zobrazí se druhé instanci aplikace Visual Studio. Tomu se říká experimentální instanci aplikace.  
  
2.  V experimentální instanci sady Visual Studio otevřete projekt C#.  
  
3.  Najděte tlačítko jste přidali na **Průzkumníka řešení** nástrojů. Měla by být čtvrté tlačítko z levé strany.  
  
4.  Když kliknete na tlačítko, by měl být odfiltrovány všechny soubory a byste měli vidět **všechny položky byly filtrovány ze zobrazení.** v **Průzkumníka řešení**.