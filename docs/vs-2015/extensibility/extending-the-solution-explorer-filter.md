---
title: Rozšíření filtru Průzkumník řešení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 687663a79ea5dca75da68013519f4652fa71460c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204393"
---
# <a name="extending-the-solution-explorer-filter"></a>Rozšíření filtru Průzkumníka řešení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete roztáhnout funkce filtru **Průzkumník řešení** a zobrazit nebo skrýt jiné soubory. Můžete například vytvořit filtr, který v **Průzkumník řešení**zobrazí pouze soubory továrny tříd C#, jak ukazuje tento návod.  
  
## <a name="prerequisites"></a>Požadavky  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="create-a-visual-studio-package-project"></a>Vytvoření projektu balíčku sady Visual Studio  
  
1. Vytvořte projekt VSIX s názvem `FileFilter` . Přidejte šablonu vlastní položky příkazu s názvem **Filter**. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Přidejte odkaz na `System.ComponentModel.Composition` a `Microsoft.VisualStudio.Utilities` .  
  
3. Příkaz nabídky se zobrazí na panelu nástrojů **Průzkumník řešení** . Otevřete soubor FileFilterPackage. vsct.  
  
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
  
1. V souboru source. extension. vsixmanifest přidejte Asset, který je součástí rozhraní MEF.  
  
2. Na kartě **assets (prostředky** ) klikněte na tlačítko **Nový** .  
  
3. V poli **typ** vyberte **Microsoft. VisualStudio. MefComponent**.  
  
4. V poli **zdroj** vyberte **projekt v aktuálním řešení**.  
  
5. V poli **projekt** zvolte možnost **Filtr**a pak klikněte na tlačítko **OK** .  
  
### <a name="add-the-filter-code"></a>Přidat kód filtru  
  
1. Do souboru FileFilterPackageGuids.cs přidejte nějaké identifikátory GUID:  
  
    ```csharp  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2. Přidejte soubor třídy do projektu filtru souborů s názvem FileNameFilter.cs.  
  
3. Nahraďte prázdný obor názvů a prázdnou třídu níže uvedeným kódem.  
  
     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`Metoda vezme kolekci, která obsahuje kořen řešení ( `rootItems` ) a vrátí kolekci položek, které mají být zahrnuty do filtru.  
  
     `ShouldIncludeInFilter`Metoda filtruje položky v hierarchii **Průzkumník řešení** na základě zadané podmínky.  
  
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
  
4. V FileFilter.cs odeberte umístění příkazů a kód pro zpracování z konstruktoru filtru souborů. Výsledek by měl vypadat takto:  
  
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
  
     Odeberte také metodu ShowMessageBox ().  
  
5. V FileFilterPackage cs nahraďte kód v metodě Initialize () následujícím způsobem:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### <a name="test-your-code"></a>Testování kódu  
  
1. Sestavte a spusťte projekt. Zobrazí se druhá instance aplikace Visual Studio. To se označuje jako experimentální instance.  
  
2. V experimentální instanci aplikace Visual Studio otevřete projekt C#.  
  
3. Vyhledejte tlačítko, které jste přidali na panelu nástrojů Průzkumník řešení. Mělo by se jednat o čtvrté tlačítko zleva.  
  
4. Po kliknutí na toto tlačítko by se měly odfiltrovat všechny soubory a měla by se zobrazit zpráva "všechny položky byly vyfiltrovány ze zobrazení". v Průzkumník řešení.
