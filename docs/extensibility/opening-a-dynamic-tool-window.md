---
title: Otevření dynamického panelu nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d37a72629dfb7c10eeb51bcd2317151447e9edd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636643"
---
# <a name="open-a-dynamic-tool-window"></a>Otevření dynamického panelu nástrojů
Okna nástrojů jsou obvykle otevřené z příkazu nabídky nebo ekvivalentní klávesové zkratky. V některých případech však může být zapotřebí panelu nástrojů, které se otevře vždy, když konkrétní kontextu uživatelského rozhraní použije a zavře, když už neplatí kontextu uživatelského rozhraní. Tyto druhy oken nástrojů se nazývají *dynamické* nebo *automaticky viditelná*.  
  
> [!NOTE]
>  Seznam předdefinovaných kontexty uživatelského rozhraní najdete v tématu <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>.  
  
 Pokud chcete otevřít dynamického panelu nástrojů při spuštění a je možné k vytvoření selhání, je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> rozhraní a podmínky selhání v testu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metody. Aby prostředí vědět, že máte dynamického panelu nástrojů, který by měl být otevřen při spuštění, je nutné přidat `SupportsDynamicToolOwner` (nastaveno na hodnotu 1) k registraci balíčku. Tato hodnota není součástí standardu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, proto je nutné vytvořit vlastní atribut a přidejte ji. Další informace o uživatelských atributů, které najdete v tématu [použijte atribut vlastní registrace k registraci rozšíření](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Použití <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> otevřete panel nástrojů. Panel nástrojů se vytvoří podle potřeby.  
  
> [!NOTE]
>  Dynamického panelu nástrojů můžete zavřít uživatel. Pokud chcete vytvořit příkaz nabídky, takže uživatel může znovu otevřít okno nástroje, musí být ve stejném kontextu uživatelského rozhraní, které se otevře okno nástroje a zakázána, jinak aktivována příkazu nabídky.  
  
## <a name="to-open-a-dynamic-tool-window"></a>K otevření dynamického panelu nástrojů  
  
1.  Vytvořte projekt VSIX s názvem **DynamicToolWindow** a přidat šablonu položky okna nástroje s názvem *DynamicWindowPane.cs*. Další informace najdete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  V *DynamicWindowPanePackage.cs* souboru, najít DynamicWindowPanePackage deklarace. Přidat <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> a <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> atributy registrace panel nástrojů.  
  
    ```vb  
    [ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackage.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Výše uvedené atributy registrace s názvem DynamicWindowPane jako přechodné okna, která není zachována, když je aplikace Visual Studio zavřít a znovu otevřít okno nástroje. Otevřít DynamicWindowPane pokaždé, když <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> platí a uzavřených jinak.  
  
3.  Sestavte projekt a spusťte ladění. Experimentální instanci aplikace by se zobrazit. Panel nástrojů byste neměli vidět.  
  
4.  Otevřete projekt v experimentální instanci aplikace. By se zobrazit panel nástrojů.