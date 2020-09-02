---
title: Vytvoření rozšíření pomocí sady VSPackage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68ade2f8d334c1f93349e396d910fa300f6b5417
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903858"
---
# <a name="create-an-extension-with-a-vspackage"></a>Vytvoření rozšíření pomocí VSPackage

Tento návod ukazuje, jak vytvořit projekt VSIX a přidat položku projektu VSPackage. Pomocí VSPackage získáme službu prostředí uživatelského rozhraní, aby se zobrazilo okno se zprávou.

## <a name="prerequisites"></a>Předpoklady

Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Vytvoření balíčku VSPackage

1. Vytvořte projekt VSIX s názvem **FirstPackage**. Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** hledáním "VSIX".

2. Po otevření projektu přidejte šablonu položky balíčku sady Visual Studio s názvem **FirstPackage**. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V dialogovém okně **Přidat novou položku** přejít na rozšiřitelnost **Visual C#**  >  **Extensibility** a vybrat **balíček sady Visual Studio**. V poli **název** v dolní části okna změňte název souboru příkazů na *FirstPackage.cs*.

3. Sestavte projekt a spusťte ladění.

    Zobrazí se experimentální instance aplikace Visual Studio. Další informace o experimentální instanci naleznete v [experimentální instanci](../extensibility/the-experimental-instance.md).

4. V experimentální instanci otevřete **Tools**  >  okno**rozšíření a aktualizace** nástrojů. Tady byste měli vidět rozšíření **FirstPackage** . (Pokud v pracovní instanci sady Visual Studio otevřete **rozšíření a aktualizace** , neuvidíte **FirstPackage**).

## <a name="load-the-vspackage"></a>Načíst VSPackage

V tomto okamžiku se rozšíření nenačte, protože není nic, co způsobuje načtení. Při interakci s uživatelským rozhraním (kliknutím na příkaz nabídky, otevřením okna nástroje) nebo určením, že VSPackage by mělo být načteno do konkrétního kontextu uživatelského rozhraní, lze obecně načíst rozšíření. Další informace o načítání VSPackage a kontextů uživatelského rozhraní najdete v tématu [načítání VSPackage](../extensibility/loading-vspackages.md). Pro tento postup vám ukážeme, jak po otevření řešení načíst VSPackage.

1. Otevřete soubor *FirstPackage.cs* . Vyhledejte deklaraci `FirstPackage` třídy. Nahraďte stávající atributy následujícími atributy:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Pojďme přidat zprávu, která nám umožní zjistit, že se VSPackage načetl. `Initialize()`K tomu slouží metoda VSPackage, protože můžete získat služby sady Visual Studio až po umístění balíčku VSPackage. (Další informace o tom, jak získat služby, najdete v tématu [Postupy: získání služby](../extensibility/how-to-get-a-service.md).) Nahraďte `Initialize()` metodu `FirstPackage` kódem, který načte <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> službu, získá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní a zavolá jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metodu.

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

3. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.

4. Otevřete řešení v experimentální instanci. Mělo by se zobrazit okno se zprávou, které říká **první balíček uvnitř inicializace ()**.
