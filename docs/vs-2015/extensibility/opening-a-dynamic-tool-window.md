---
title: Otevření dynamického panelu nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 073e8a2e7ff13dad0e413aa47b7875260f612cd2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773792"
---
# <a name="opening-a-dynamic-tool-window"></a>Otevření dynamického panelu nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okna nástrojů jsou obvykle otevřené z příkazu nabídky nebo ekvivalentní klávesové zkratky. V některých případech však může být zapotřebí panelu nástrojů, které se otevře vždy, když konkrétní kontextu uživatelského rozhraní použije a zavře, když už neplatí kontextu uživatelského rozhraní. Okna nástrojů, jako jsou tyto se nazývají *dynamické* nebo *automaticky viditelná*.  
  
> [!NOTE]
>  Seznam předdefinovaných kontexty uživatelského rozhraní najdete v tématu <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Pro  
  
 Pokud chcete otevřít dynamického panelu nástrojů při spuštění a je možné k vytvoření selhání, je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> rozhraní a podmínky selhání v testu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metody. Aby prostředí vědět, že máte dynamického panelu nástrojů, který by měl být otevřen při spuštění, je nutné přidat `SupportsDynamicToolOwner` (nastaveno na hodnotu 1) k registraci balíčku. Tato hodnota není součástí standardu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, proto je nutné vytvořit vlastní atribut a přidejte ji. Další informace o uživatelských atributů, které najdete v tématu [pomocí vlastního atributu registrace k registraci rozšíření](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Použití <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> otevřete panel nástrojů. Panel nástrojů se vytvoří podle potřeby.  
  
> [!NOTE]
>  Dynamického panelu nástrojů můžete zavřít uživatel. Pokud chcete vytvořit příkaz nabídky, takže uživatel může znovu otevřít okno nástroje, musí být ve stejném kontextu uživatelského rozhraní, které se otevře okno nástroje a zakázána, jinak aktivována příkazu nabídky.  
  
### <a name="to-open-a-dynamic-tool-window"></a>K otevření dynamického panelu nástrojů  
  
1.  Vytvořte projekt VSIX s názvem **DynamicToolWindow** a přidat šablonu položky okna nástroje s názvem **DynamicWindowPane.cs**. Další informace najdete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  V souboru DynamicWindowPanePackage.cs najdete DynamicWindowPanePackage deklarace. Přidat <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> a T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute atributy registrace panel nástrojů.  
  
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
  
     Tento registr – okno nástroje s názvem DynamicWindowPane jako přechodné okna, která není zachována, když je aplikace Visual Studio zavřít a znovu otevřít. Otevřít DynamicWindowPane pokaždé, když <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> platí a uzavřených jinak.  
  
3.  Sestavte projekt a spusťte ladění. Experimentální instanci aplikace by se zobrazit. Panel nástrojů byste neměli vidět.  
  
4.  Otevřete projekt v experimentální instanci aplikace. By se zobrazit panel nástrojů.

