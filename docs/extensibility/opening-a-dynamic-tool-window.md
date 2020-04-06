---
title: Otevření okna dynamického nástroje | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702261"
---
# <a name="open-a-dynamic-tool-window"></a>Otevření okna dynamického nástroje
Okna nástrojů se obvykle otevírají z příkazu v nabídce nebo z ekvivalentní klávesové zkratky. Někdy však budete potřebovat okno nástroje, které se otevře vždy, když se použije konkrétní kontext ui a zavře, když kontext ui již neplatí. Tyto typy oken nástrojů se nazývají *dynamické* nebo *automaticky viditelné*.

> [!NOTE]
> Seznam předdefinovaných kontextů nového <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>ui naleznete v tématu .

 Pokud chcete otevřít okno dynamického nástroje při spuštění a je možné, že <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> se vytvoření nezdaří, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> je nutné implementovat rozhraní a otestovat podmínky selhání v metodě. Aby prostředí vědět, že máte dynamické okno nástroje, které by měly `SupportsDynamicToolOwner` být otevřeny při spuštění, je nutné přidat hodnotu (nastavenou na 1) k registraci balíčku. Tato hodnota není součástí <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>standardu , takže je nutné vytvořit vlastní atribut přidat. Další informace o vlastních atributech naleznete [v tématu Použití vlastního atributu registrace k registraci rozšíření](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Slouží <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> k otevření okna nástroje. Okno nástroje je vytvořeno podle potřeby.

> [!NOTE]
> Okno dynamického nástroje může uživatel zavřít. Pokud chcete vytvořit příkaz nabídky, aby uživatel mohl znovu otevřít okno nástroje, příkaz nabídky by měl být povolen ve stejném kontextu uživatelského rozhraní, který otevře okno nástroje, a jinak je zakázán.

## <a name="to-open-a-dynamic-tool-window"></a>Otevření okna dynamického nástroje

1. Vytvořte projekt VSIX s názvem **DynamicToolWindow** a přidejte šablonu položky okna nástroje s názvem *DynamicWindowPane.cs*. Další informace naleznete [v tématu Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

2. V *souboru DynamicWindowPanePackage.cs* vyhledejte deklaraci DynamicWindowPanePackage. Přidejte <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> atributy a pro registraci okna nástroje.

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

     Výše uvedené atributy zaregistrovat okno nástroje s názvem DynamicWindowPane jako přechodné okno, které není trvalé při zavření a znovu otevření sady Visual Studio. DynamicWindowPane je <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> otevřen vždy, když platí, a jinak uzavřen.

3. Sestavení projektu a začít ladění. Experimentální instance by se měla zobrazit. Neměli byste vidět okno nástroje.

4. Otevřete projekt v experimentální instanci. Mělo by se zobrazit okno nástroje.
