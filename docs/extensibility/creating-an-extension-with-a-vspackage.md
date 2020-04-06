---
title: Vytvoření rozšíření s balíčkem VSPackage | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739537"
---
# <a name="create-an-extension-with-a-vspackage"></a>Vytvoření rozšíření pomocí balíčku VSPackage

Tento návod ukazuje, jak vytvořit projekt VSIX a přidat položku projektu VSPackage. Použijeme VSPackage získat službu prostředí ui, aby se zobrazilo okno se zprávou.

## <a name="prerequisites"></a>Požadavky

Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Vytvoření balíčku VSPackage

1. Vytvořte projekt VSIX s názvem **FirstPackage**. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Při otevření projektu přidejte šablonu položky balíčku sady Visual Studio s názvem **FirstPackage**. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** přejděte na **visual c#** > **rozšiřitelnost** a vyberte **balíček sady Visual Studio**. V poli **Název** v dolní části okna změňte název příkazového souboru na *FirstPackage.cs*.

3. Sestavení projektu a začít ladění.

    Zobrazí se experimentální instance sady Visual Studio. Další informace o experimentální instanci naleznete [v tématu Experimentální instance](../extensibility/the-experimental-instance.md).

4. V experimentální instanci otevřete okno Rozšíření a aktualizace **nástrojů.** > **Extensions and Updates** Měli byste vidět **FirstPackage** rozšíření zde. (Pokud otevřete **rozšíření a aktualizace** v pracovní instanci sady Visual Studio, neuvidíte **FirstPackage).**

## <a name="load-the-vspackage"></a>Načíst balíček VSPackage

V tomto okamžiku rozšíření nenačte, protože není nic, co způsobí, že k načtení. Obecně můžete načíst rozšíření při interakci s jeho uzly (klepnutím na příkaz nabídky, otevření okna nástroje) nebo zadáním, že VSPackage by se měla načíst v určitém kontextu ui. Další informace o načítání kontextů VSPackages a UI naleznete v [tématu Loading VSPackages](../extensibility/loading-vspackages.md). V tomto postupu vám ukážeme, jak načíst VSPackage při otevření řešení.

1. Otevřete *soubor FirstPackage.cs.* Podívejte se na `FirstPackage` prohlášení třídy. Nahraďte existující atributy následujícími atributy:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Přidáme zprávu, která nám umožní vědět, že VSPackage má načten. K tomu používáme `Initialize()` metodu VSPackage, protože služby sady Visual Studio můžete získat pouze po umístění balíčku VSPackage. (Další informace o získávání služeb najdete v [tématu How to: Get a service](../extensibility/how-to-get-a-service.md).) Nahraďte `Initialize()` `FirstPackage` metodu s <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> kódem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> který získá službu, získá rozhraní a volá jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metodu.

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

4. Otevřete řešení v experimentální instanci. Měli byste vidět okno se zprávou, která říká, že **první balíček uvnitř Initialize()**.
