---
title: Otevření dynamického okna nástroje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09b81294abc708cf7616dad03b5dd7333d6a1719
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816858"
---
# <a name="opening-a-dynamic-tool-window"></a>Otevření dynamického panelu nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okna nástrojů se obvykle otevírají z příkazu v nabídce nebo ekvivalentní klávesové zkratky. V některých případech však můžete potřebovat okno nástroje, které se otevře vždy, když se použije konkrétní kontext uživatelského rozhraní, a ukončí se, když se kontext uživatelského rozhraní již nepoužívá. Okna nástrojů, jako jsou tato, se nazývají *Dynamická* nebo *automaticky viditelná*.  
  
> [!NOTE]
> Seznam předdefinovaných kontextů uživatelského rozhraní naleznete v tématu <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> . Jako  
  
 Chcete-li otevřít dynamické okno nástroje při spuštění a je možné, že vytvoření selže, je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> rozhraní a otestovat podmínky selhání v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metodě. Aby prostředí věděli, že máte dynamické okno nástrojů, které by se mělo otevřít při spuštění, musíte `SupportsDynamicToolOwner` do registrace balíčku přidat hodnotu (nastavenou na 1). Tato hodnota není součástí standardu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , takže musíte vytvořit vlastní atribut pro jeho přidání. Další informace o vlastních atributech naleznete v tématu [použití vlastního registračního atributu k registraci rozšíření](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Použijte <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> k otevření okna nástroje. V případě potřeby se vytvoří okno nástroje.  
  
> [!NOTE]
> Dynamické okno nástroje může být zavřeno uživatelem. Pokud chcete vytvořit příkaz nabídky, aby uživatel mohl znovu otevřít okno nástroje, měl by být příkaz nabídky povolen ve stejném kontextu uživatelského rozhraní, který otevírá okno nástroje, a v opačném případě zakázaný.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Otevření dynamického okna nástrojů  
  
1. Vytvořte projekt VSIX s názvem **DynamicToolWindow** a přidejte šablonu položky okna nástroje s názvem **DynamicWindowPane.cs**. Další informace naleznete v tématu [Vytvoření rozšíření pomocí okna nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2. V souboru DynamicWindowPanePackage.cs Najděte deklaraci DynamicWindowPanePackage. Přidejte <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atributy a T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute pro registraci okna nástroje.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Tím se registruje okno nástroje s názvem DynamicWindowPane jako přechodné okno, které není trvalé při zavření a opětovném otevření aplikace Visual Studio. DynamicWindowPane se otevře vždy <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> , když se použije, a v opačném případě zavře.  
  
3. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance. Okno nástroje byste neměli vidět.  
  
4. Otevřete projekt v experimentální instanci. Měl by se zobrazit okno nástroje.
