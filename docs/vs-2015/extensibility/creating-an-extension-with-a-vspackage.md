---
title: Vytváření rozšíření pomocí VSPackage | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 945ae5b3cf6cd8769795c31a10a4f51e1f7eccb6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773298"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Vytváření rozšíření pomocí VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit projekt VSIX a přidejte položku projektu VSPackage. Použijeme sady VSPackage se získat službu uživatelského prostředí. Chcete-li zobrazit okno se zprávou.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Vytváření VSPackage  
  
1.  Vytvořte projekt VSIX s názvem **FirstPackage**. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C# / rozšíření**.  
  
2.  Po otevření projektu přidat šablonu položky balíčku sady Visual Studio s názvem **FirstPackage**. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. V **přidat novou položku** dialogové okno, přejděte na **Visual C# / rozšíření** a vyberte **balíček Visual Studio**. V **název** pole v dolní části okna, změňte název souboru příkazu **FirstPackage.cs**.  
  
3.  Sestavte projekt a spusťte ladění.  
  
     Experimentální instanci sady Visual Studio se zobrazí. Další informace o experimentální instanci najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
4.  V experimentální instanci aplikace, otevřete **nástrojů / rozšíření a aktualizace** okna. Měli byste vidět **FirstPackage** rozšíření tady. (Pokud otevřete **rozšíření a aktualizace** v instanci pracovního sadě Visual Studio, neuvidíte **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Načítání sady VSPackage  
 V tuto chvíli rozšíření nepodaří načíst, protože není nic, která způsobí, že ho pro načtení. Rozšíření můžete načíst obecně při interakci s jeho uživatelské rozhraní (kliknutím na příkaz nabídky, otevřete okno nástroje), nebo tak, že určíte, že by se měly načíst sady VSPackage v určitém kontextu uživatelského rozhraní. Další informace o načítání rozšíření VSPackages a uživatelské rozhraní kontextech najdete v tématu [načítání rozšíření VSPackages](../extensibility/loading-vspackages.md). V tomto postupu vám ukážeme, jak načíst VSPackage při otevření řešení.  
  
1.  Otevřete soubor FirstPackage.cs. Deklarace třídy FirstPackage hledejte. Nahraďte existující atributy následující:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Přidejme zpráva, že získáme tak jistotu, že byl načten sady VSPackage. Metodu Initialize() sady VSPackage používáme k tomu, protože služby Visual Studio můžete získat až poté, co byly umístěny balíčku VSPackage. (Další informace o tom, jak služby najdete v tématu [postupy: získání služby](../extensibility/how-to-get-a-service.md).) Nahraďte metodu Initialize() FirstPackage kód, který získá <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> služby, získá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> rozhraní a volání jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metoda.  
  
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
  
3.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.  
  
4.  Otevřete řešení v experimentální instanci aplikace. Měli byste vidět okno se zprávou, že **první balíček uvnitř Initialize()**.

