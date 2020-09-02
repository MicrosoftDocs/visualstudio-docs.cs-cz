---
title: Vytvoření rozšíření pomocí sady VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddad7149db75aa662f9427a301c04eaf925146f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197419"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Vytváření rozšíření pomocí VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit projekt VSIX a přidat položku projektu VSPackage. Pomocí VSPackage získáme službu prostředí uživatelského rozhraní, aby se zobrazilo okno se zprávou.  
  
## <a name="prerequisites"></a>Požadavky  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Vytvoření balíčku VSPackage  
  
1. Vytvořte projekt VSIX s názvem **FirstPackage**. Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** v části **Visual C#/rozšiřitelnost**.  
  
2. Po otevření projektu přidejte šablonu položky balíčku sady Visual Studio s názvem **FirstPackage**. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat/nová položka**. V dialogovém okně **Přidat novou položku** přejít na **Visual C#/rozšiřitelnost** a vyberte **balíček Visual Studio**. V poli **název** v dolní části okna změňte název souboru příkazů na **FirstPackage.cs**.  
  
3. Sestavte projekt a spusťte ladění.  
  
     Zobrazí se experimentální instance aplikace Visual Studio. Další informace o experimentální instanci naleznete v [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
4. V experimentální instanci otevřete okno **Nástroje/rozšíření a aktualizace** . Tady byste měli vidět rozšíření **FirstPackage** . (Pokud v pracovní instanci sady Visual Studio otevřete **rozšíření a aktualizace** , neuvidíte **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Načítání VSPackage  
 V tomto okamžiku se rozšíření nenačte, protože není nic, co způsobuje načtení. Při interakci s uživatelským rozhraním (kliknutím na příkaz nabídky, otevřením okna nástroje) nebo určením, že VSPackage by mělo být načteno do konkrétního kontextu uživatelského rozhraní, lze obecně načíst rozšíření. Další informace o načítání VSPackage a kontextů uživatelského rozhraní najdete v tématu [načítání VSPackage](../extensibility/loading-vspackages.md). Pro tento postup vám ukážeme, jak po otevření řešení načíst VSPackage.  
  
1. Otevřete soubor FirstPackage.cs. Vyhledejte deklaraci třídy FirstPackage. Nahraďte stávající atributy následujícím způsobem:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2. Pojďme přidat zprávu, která nám umožní zjistit, že se VSPackage načetl. K tomuto účelu používáme metodu Initialize () VSPackage, protože můžete získat služby sady Visual Studio až po umístění balíčku VSPackage. (Další informace o tom, jak získat služby, najdete v tématu [Postupy: získání služby](../extensibility/how-to-get-a-service.md).) Nahraďte metodu Initialize () pro FirstPackage kódem, který získá <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> službu, získá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní a zavolá jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metodu.  
  
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
